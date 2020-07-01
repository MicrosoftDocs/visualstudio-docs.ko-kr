---
title: 내 코드만을 사용하여 사용자 코드 디버그 | Microsoft Docs
ms.date: 02/13/2019
ms.topic: how-to
ms.assetid: 0f0df097-bbaf-46ad-9ad1-ef5f40435079
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 867477fd3e490f91e81fb91c8be267ede83c8d2c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536567"
---
# <a name="debug-only-user-code-with-just-my-code"></a>내 코드만을 사용하여 사용자 코드만 디버그

*내 코드만*은 시스템, 프레임워크 및 기타 사용자 코드가 아닌 코드에 대한 호출을 자동으로 프로시저 단위로 실행하는 Visual Studio 디버깅 기능입니다. **호출 스택** 창에서 내 코드만은 이러한 호출을 **[외부 코드]** 프레임으로 축소합니다.

내 코드만은 .NET, C++ 및 JavaScript 프로젝트에서 다르게 작동합니다.

## <a name="enable-or-disable-just-my-code"></a><a name="BKMK_Enable_or_disable_Just_My_Code"></a> 내 코드만 사용 또는 사용 안 함

대부분의 프로그래밍 언어에서 내 코드만은 기본적으로 사용하도록 설정되어 있습니다.

- Visual Studio에서 내 코드만을 사용하거나 사용하지 않도록 설정하려면 **도구** > **옵션**(또는 **디버그** > **옵션**) > **디버깅** > **일반**에서 **내 코드만 사용**을 선택하거나 선택 취소합니다.

![옵션 대화 상자의 내 코드만 사용](../debugger/media/dbg_justmycode_options.png "내 코드만 사용")

> [!NOTE]
> **내 코드만 사용**은 모든 언어의 모든 Visual Studio 프로젝트에 적용되는 전역 설정입니다.

## <a name="just-my-code-debugging"></a>내 코드만 디버깅

디버깅 세션 중에 디버거가 내 코드(사용자 코드)로 간주하는 코드 모듈이 기호 로드 상태와 함께 **모듈** 창에 표시됩니다. 자세한 내용은 [디버거가 앱에 연결되는 방식 자세히 알아보기](../debugger/debugger-tips-and-tricks.md#modules_window)를 참조하세요.

![모듈 창의 사용자 코드](../debugger/media/dbg_justmycode_module.png "모듈 창의 사용자 코드")

**호출 스택** 또는 **작업** 창에서, 내 코드만은 사용자 코드가 아닌 코드를 `[External Code]` 레이블과 회색 주석이 달린 코드 프레임으로 축소합니다.

![호출 스택 창의 외부 코드 프레임](../debugger/media/dbg_justmycode_externalcode.png "외부 코드 프레임")

>[!TIP]
>**모듈**, **호출 스택**, **작업** 또는 대부분의 다른 디버깅 창을 열려면 디버깅 세션에 있어야 합니다. 디버깅하는 동안 **디버그** > **창**에서 열려는 창을 선택합니다.

<a name="BKMK_Override_call_stack_filtering"></a> 축소된 **[외부 코드]** 프레임의 코드를 보려면 **호출 스택** 또는 **작업** 창을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **외부 코드 표시**를 선택합니다. 펼쳐진 외부 코드 줄이 **[외부 코드**] 프레임을 대체합니다.

![호출 스택 창에 외부 코드 표시](../debugger/media/dbg_justmycode_showexternalcode.png "외부 코드 표시")

> [!NOTE]
> **외부 코드 표시**는 사용자가 연 모든 언어의 모든 프로젝트에 적용되는 현재 사용자 프로파일러 설정입니다.

**호출 스택** 창에서 펼쳐진 외부 코드 줄을 두 번 클릭하면 호출하는 코드 줄이 소스 코드에서 녹색으로 강조 표시됩니다. DLL 또는 찾을 수 없거나 로드되지 않는 다른 모듈의 경우, 기호 또는 소스를 찾을 수 없음 페이지가 열릴 수 있습니다.

## <a name="net-just-my-code"></a><a name="BKMK__NET_Framework_Just_My_Code"></a>.NET 내 코드만

.NET 프로젝트에서 내 코드만은 기호( *.pdb*) 파일과 프로그램 최적화를 사용하여 사용자 코드와 사용자 코드가 아닌 코드를 분류합니다. .NET 디버거는 최적화된 이진 파일과 로드되지 않은 *.pdb* 파일을 사용자 코드가 아닌 코드로 간주합니다.

세 가지 컴파일러 특성도 .NET 디버거에서 사용자 코드로 간주되는 것에 영향을 줍니다.

- <xref:System.Diagnostics.DebuggerNonUserCodeAttribute>는 적용되는 코드가 사용자 코드가 아니라고 디버거에 알려줍니다.
- <xref:System.Diagnostics.DebuggerHiddenAttribute>가 적용된 코드는 내 코드만 옵션을 해제했더라도 디버거에서 숨겨집니다.
- <xref:System.Diagnostics.DebuggerStepThroughAttribute>는 적용된 코드를 한 단계씩 실행하지 않고 단계별로 실행하도록 디버거에 알려줍니다.

.NET 디버거는 다른 모든 코드를 사용자 코드로 간주합니다.

.NET 디버깅 중에:

- 사용자 코드가 아닌 코드에서 **디버그** > **한 단계씩 코드 실행**(또는 **F11**)을 누르면 사용자 코드의 다음 줄까지 프로시저 단위로 코드가 실행됩니다.
- 사용자 코드가 아닌 코드에서 **디버그** >  **프로시저 나가기**(또는 **Shift**+**F11**)를 누르면 사용자 코드의 다음 줄까지 실행됩니다.

사용자 코드가 더 이상 없으면 끝날 때까지 디버깅이 계속되거나, 다른 중단점에 적중하거나, 오류가 발생합니다.

<a name="BKMK_NET_Breakpoint_behavior"></a> 사용자 코드가 아닌 코드에서 디버거를 중단하면(예: **디버그** > **모두 중단**을 사용하고 사용자 코드가 아닌 코드에서 일시 중지하는 경우) **소스 없음** 창이 나타납니다. 그러면 **디버그** > **단계** 명령을 사용하여 사용자 코드의 다음 줄로 이동할 수 있습니다.

사용자 코드가 아닌 코드에서 처리되지 않은 예외가 발생하면 디버거는 예외가 생성된 사용자 코드의 줄에서 중단됩니다.

예외에 대해 첫째 예외가 설정된 경우 호출하는 사용자 코드 줄이 소스 코드에서 녹색으로 강조 표시됩니다. **호출 스택** 창에 **[외부 코드]** 레이블과 주석이 달린 프레임이 표시됩니다.

## <a name="c-just-my-code"></a><a name="BKMK_C___Just_My_Code"></a> C++ 내 코드만

Visual Studio 2017 버전 15.8부터는 코드 스태핑을 위한 내 코드만 기능도 지원됩니다. 이 기능을 사용하려면 [/JMC(내 코드만 디버깅)](/cpp/build/reference/jmc) 컴파일러 스위치를 사용해야 합니다. 이 스위치는 C++ 프로젝트에서 기본적으로 사용하도록 설정되어 있습니다. 내 코드만의 **호출 스택** 창 및 호출 스택 지원에는 /JMC 스위치가 필요하지 않습니다.

<a name="BKMK_CPP_User_and_non_user_code"></a> 사용자 코드로 분류되려면 사용자 코드가 포함된 바이너리의 PDB를 디버거에서 로드해야 합니다(**모듈** 창을 사용하여 확인).

호출 스택 동작(예: **호출 스택** 창)의 경우 C++의 내 코드만 기능은 다음과 같은 함수만 사용자 코드가 아닌 코드로 간주합니다.

- 기호 파일에서 소스 정보가 제거된 함수
- 기호 파일에서 스택 프레임에 해당하는 소스 파일이 없음을 나타내는 함수
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더의 *\*.natjmc* 파일에 지정된 함수

코드 스태핑 동작의 경우 C++의 내 코드만 기능은 다음과 같은 함수만 사용자 코드가 아닌 코드로 간주합니다.

- 해당 PDB 파일이 디버거에 로드되지 않은 함수
- *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더의 *\*.natjmc* 파일에 지정된 함수

> [!NOTE]
> 내 코드만 기능이 코드 스태핑을 지원하려면 C++ 코드를 Visual Studio 15.8 Preview 3 이상에서 MSVC 컴파일러를 사용하여 컴파일하고 /JMC 컴파일러 스위치를 사용하도록 설정되어 있어야 합니다(기본적으로 사용하도록 설정됨). 자세한 내용은 [C++ 호출 스택 및 코드 스태핑 동작 사용자 지정](#BKMK_CPP_Customize_call_stack_behavior)과 이 [블로그 게시물](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/)을 참조하세요. 이전 컴파일러를 사용하여 컴파일된 코드의 경우, *.natstepfilter* 파일이 내 코드와 무관하게 코드 스태핑을 사용자 지정하는 유일한 방법입니다. [C++ 스태핑 동작 사용자 지정](#BKMK_CPP_Customize_stepping_behavior)을 참조하세요.

<a name="BKMK_CPP_Stepping_behavior"></a> C++ 디버깅 중에:

- 사용자 코드가 아닌 코드에서 **디버그** > **한 단계씩 코드 실행**(또는 **F11**)을 누르면 사용자 코드의 다음 줄까지 프로시저 단위로 코드가 실행됩니다.
- 사용자 코드가 아닌 코드에서 **디버그** >  **프로시저 나가기**(또는 **Shift**+**F11**)를 누르면 사용자 코드의 다음 줄까지 실행됩니다.

사용자 코드가 더 이상 없으면 끝날 때까지 디버깅이 계속되거나, 다른 중단점에 적중하거나, 오류가 발생합니다.

사용자 코드가 아닌 코드에서 디버거를 중단하면(예: **디버그** > **모두 중단**을 사용하고 사용자 코드가 아닌 코드에서 일시 중지하는 경우), 사용자 코드가 아닌 코드에서 스태핑이 계속됩니다.

디버거에서 예외가 발생하면 사용자 코드인지 아닌지에 관계없이 예외에서 중지됩니다. **예외 설정** 대화 상자의 **사용자가 처리하지 않음** 옵션은 무시됩니다.

### <a name="customize-c-call-stack-and-code-stepping-behavior"></a><a name="BKMK_CPP_Customize_call_stack_behavior"></a> Customize C++ 호출 스택 및 코드 스태핑 동작 사용자 지정

C++ 프로젝트의 경우 **호출 스택** 창에서 사용자 코드가 아닌 코드로 간주되는 모듈, 소스 파일 및 함수를 *\*.natjmc* 파일에 명시하여 지정할 수 있습니다. 이렇게 사용자 지정하면 최신 컴파일러를 사용하는 경우 코드 스태핑에도 적용됩니다([C++ 내 코드만](#BKMK_CPP_User_and_non_user_code) 참조).

- Visual Studio 머신의 모든 사용자에 대해 사용자 코드가 아닌 코드를 지정하려면, *.natjmc* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 추가합니다.
- 개별 사용자에 대해 사용자 코드가 아닌 코드를 지정하려면 *.natjmc* 파일을 *%USERPROFILE%\My Documents\\<Visual Studio version\>\Visualizers* 폴더에 추가합니다.

*.natjmc* 파일은 다음 구문을 사용하는 XML 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<NonUserCode xmlns="http://schemas.microsoft.com/vstudio/debugger/jmc/2015">

  <!-- Modules -->
  <Module Name="ModuleSpec" />
  <Module Name="ModuleSpec" Company="CompanyName" />

  <!-- Files -->
  <File Name="FileSpec"/>

  <!-- Functions -->
  <Function Name="FunctionSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" />
  <Function Name="FunctionSpec" Module ="ModuleSpec" ExceptionImplementation="true" />

</NonUserCode>

```

 **모듈 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 모듈의 전체 경로입니다. Windows 와일드 카드 문자 `?`(0개 또는 1개의 문자) 및 `*`(0개 이상의 문자)를 사용할 수 있습니다. 예를 들면 다음과 같습니다.<br /><br /> `<Module Name="?:\3rdParty\UtilLibs\*" />`<br /><br /> 드라이브의 *\3rdParty\UtilLibs*에 있는 모든 모듈을 외부 코드로 간주하도록 디버거에 알려줍니다.|
|`Company`|선택 사항입니다. 실행 파일에 포함된 모듈을 게시하는 회사의 이름입니다. 이 특성을 사용하여 모듈을 구분할 수 있습니다.|

 **파일 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 소스 파일의 전체 경로입니다. 경로를 지정할 때 Windows 와일드 카드 문자 `?` 및 `*`를 사용할 수 있습니다.|

 **함수 요소 특성**

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 외부 코드로 처리할 함수의 정규화된 이름입니다.|
|`Module`|선택 사항입니다. 함수를 포함하는 모듈의 이름 또는 전체 경로입니다. 이 특성을 사용하여 동일한 이름을 가진 함수를 구분할 수 있습니다.|
|`ExceptionImplementation`|`true`로 설정된 경우 이 함수 대신 예외를 발생시킨 함수가 호출 스택에 표시됩니다.|

### <a name="customize-c-stepping-behavior-independent-of-just-my-code-settings"></a><a name="BKMK_CPP_Customize_stepping_behavior"></a> 내 코드만 설정과 무관하게 Customize C++ 스태핑 동작 사용자 지정

C++ 프로젝트에서는 프로시저 단위로 실행할 함수를 *\*.natstepfilter* 파일에 사용자 코드가 아닌 코드로 나열하여 지정할 수 있습니다. *\*.natstepfilter* 파일에 나열된 함수는 내 코드만 설정에 종속되지 않습니다.

- 모든 로컬 Visual Studio 사용자에 대해 사용자 코드가 아닌 코드를 지정하려면, *.natstepfilter* 파일을 *%VsInstallDirectory%\Common7\Packages\Debugger\Visualizers* 폴더에 추가합니다.
- 개별 사용자에 대해 사용자 코드가 아닌 코드를 지정하려면 *.natstepfilter* 파일을 *%USERPROFILE%\My Documents\\<Visual Studio version\>\Visualizers* 폴더에 추가합니다.

*.natstepfilter* 파일은 다음 구문을 사용하는 XML 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<StepFilter xmlns="http://schemas.microsoft.com/vstudio/debugger/natstepfilter/2010">
    <Function>
        <Name>FunctionSpec</Name>
        <Action>StepAction</Action>
    </Function>
    <Function>
        <Name>FunctionSpec</Name>
        <Module>ModuleSpec</Module>
        <Action>StepAction</Action>
    </Function>
</StepFilter>

```

|요소|설명|
|-------------|-----------------|
|`Function`|필수 요소. 하나 이상의 함수를 사용자가 작성하지 않은 함수로 지정합니다.|
|`Name`|필수 요소. 일치시킬 전체 함수 이름을 지정하는 ECMA 262 형식의 정규식입니다. 예를 들어:<br /><br /> `<Name>MyNS::MyClass.*</Name>`<br /><br /> `MyNS::MyClass`의 모든 메서드를 사용자가 작성하지 않은 코드로 간주하도록 디버거에 지시합니다. 일치 항목 찾기에서는 대/소문자를 구분합니다.|
|`Module`|선택 사항입니다. 함수를 포함하는 모듈의 전체 경로를 지정하는 ECMA 262 형식의 정규식입니다. 일치 항목 찾기에서는 대/소문자를 구분하지 않습니다.|
|`Action`|필수 요소. 대/소문자를 구분하는 다음 값 중 하나입니다.<br /><br /> `NoStepInto`  - 함수를 프로시저 단위로 실행하도록 디버거에 알려줍니다.<br /> `StepInto`  - 함수를 한 단계씩 실행하고, 일치하는 함수에 대한 다른 `NoStepInto`를 재정의하도록 디버거에 알려줍니다.|

## <a name="javascript-just-my-code"></a><a name="BKMK_JavaScript_Just_My_Code"></a> JavaScript 내 코드만

<a name="BKMK_JS_User_and_non_user_code"></a> JavaScript 내 코드만 옵션은 다음 분류 중 하나로 코드를 분류하여 단계별 실행 및 호출 스택 표시를 제어합니다.

|분류|설명|
|-|-|
|**MyCode**|사용자가 소유하고 제어하는 사용자 코드입니다.|
|**LibraryCode**|정기적으로 사용하며 앱이 제대로 작동하는 데 필요한, 사용자가 작성하지 않은 라이브러리의 코드(예: WinJS 또는 jQuery)입니다.|
|**UnrelatedCode**|내 소유가 아니고 앱이 제대로 작동하는 데 필요하지 않은 사용자가 작성하지 않은 코드입니다. 광고를 표시하는 Advertising SDK는 UnrelatedCode의 예입니다. UWP 프로젝트에서는 HTTP 또는 HTTPS URI에서 앱으로 로드된 모든 코드도 UnrelatedCode로 간주됩니다.|

JavaScript 디버거가 코드를 사용자 코드와 그렇지 않은 코드로 분류하는 순서는 다음과 같습니다.

1. 기본 분류
   - 호스트에서 제공하는 `eval` 함수에 문자열을 전달하여 실행되는 스크립트는 **MyCode**입니다.
   - `Function` 생성자에 문자열을 전달하여 실행되는 스크립트는 **LibraryCode**입니다.
   - WinJS 또는 Azure SDK와 같은 프레임워크 참조에 포함된 스크립트는 **LibraryCode**입니다.
   - `setTimeout`, `setImmediate` 또는 `setInterval` 함수에 문자열을 전달하여 실행되는 스크립트는 **UnrelatedCode**입니다.

2. *%VSInstallDirectory%\JavaScript\JustMyCode\mycode.default.wwa.json* 파일의 모든 Visual Studio JavaScript 프로젝트에 지정된 분류

3. 현재 프로젝트의 *mycode.json* 파일에 있는 분류

각 분류 단계는 이전 단계를 재정의합니다.

기타 모든 코드는 **MyCode**로 분류됩니다.

*mycode.json*이라는 *.json* 파일을 JavaScript 프로젝트의 루트 폴더에 추가하여 기본 분류를 수정하고 특정 파일과 URL을 사용자 코드 또는 사용자 코드가 아닌 코드로 분류할 수 있습니다. [JavaScript 내 코드만 사용자 지정](#BKMK_JS_Customize_Just_My_Code)을 참조하세요.

<a name="BKMK_JS_Stepping_behavior"></a> JavaScript 디버깅 중에:

- 함수가 사용자 코드가 아닌 경우 **디버그** > **한 단계씩 코드 실행**(또는 **F11**)은 **디버그** > **프로시저 단위 실행**(또는 **F10**)과 동일하게 작동합니다.
- 사용자가 작성하지 않은(**LibraryCode** 또는 **UnrelatedCode**) 코드에서 단계가 시작되면 스태핑은 일시적으로 내 코드만 기능이 활성화되지 않는 것처럼 작동합니다. 사용자 코드로 돌아가면 내 코드만 단계별 실행이 다시 활성화됩니다.
- 사용자 코드 단계가 현재 실행 컨텍스트를 벗어나면 다음에 실행된 사용자 코드 줄에서 디버거가 중지됩니다. 예를 들어 콜백이 **LibraryCode** 코드에서 실행되는 경우 사용자 코드의 다음 줄이 실행될 때까지 디버거가 계속됩니다.
- **프로시저 나가기**(또는 **Shift**+**F11**)를 누르면 사용자 코드의 다음 줄에서 중지됩니다.

사용자 코드가 더 이상 없으면 끝날 때까지 디버깅이 계속되거나, 다른 중단점에 적중하거나, 오류가 발생합니다.

코드에 설정된 중단점은 항상 적중되지만 코드는 분류됩니다.

- `debugger` 키워드가 **LibraryCode**에서 발생하면 디버거가 항상 중단됩니다.
- `debugger` 키워드가 **UnrelatedCode**에서 발생하면 디버거가 중단되지 않습니다.

<a name="BKMK_JS_Exception_behavior"></a> **MyCode** 또는 **LibraryCode** 코드에서 처리되지 않은 예외가 발생하면 디버거가 항상 중단됩니다.

**UnrelatedCode**에서 처리되지 않은 예외가 발생하고 **MyCode** 또는 **LibraryCode**가 호출 스택에 있으면 디버거가 중단됩니다.

예외에 대해 첫째 예외가 활성화되어 있고 **LibraryCode** 또는 **UnrelatedCode**에서 예외가 발생하는 경우:

- 예외가 처리되었으면 디버거가 중단되지 않습니다.
- 예외가 처리되지 않았으면 디버거가 중단됩니다.

### <a name="customize-javascript-just-my-code"></a><a name="BKMK_JS_Customize_Just_My_Code"></a> JavaScript 내 코드만 사용자 지정

단일 JavaScript 프로젝트에 대해 사용자 코드 및 사용자가 작성하지 않은 코드를 분류하려면 프로젝트의 루트 폴더에 *mycode.json*이라는 *.json* 파일을 추가하면 됩니다.

이 파일의 사양은 기본 분류와 *mycode.default.wwa.json* 파일을 재정의합니다. *mycode.json* 파일에 모든 키 값 쌍을 나열할 필요가 없습니다. **MyCode**, **Libraries**, **Unrelated** 값은 빈 배열일 수 있습니다.

*Mycode.json* 파일은 다음 구문을 사용합니다.

```json
{
    "Eval" : "Classification",
    "Function" : "Classification",
    "ScriptBlock" : "Classification",
    "MyCode" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ],
    "Libraries" : [
        "UrlOrFileSpec",
        . .
        "UrlOrFileSpec"
    ],
    "Unrelated" : [
        "UrlOrFileSpec",
        . . .
        "UrlOrFileSpec"
    ]
}

```

**Eval, Function 및 ScriptBlock**

**Eval**, **Function** 및 **ScriptBlock** 키 값 쌍은 동적으로 생성된 코드의 분류 방법을 결정합니다.

|이름|설명|
|-|-|
|**Eval**|호스트에서 제공하는 `eval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Eval 스크립트는 **MyCode**로 분류됩니다.|
|**Function**|`Function` 생성자에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 Function 스크립트는 **LibraryCode**로 분류됩니다.|
|**ScriptBlock**|`setTimeout`, `setImmediate` 또는 `setInterval` 함수에 문자열을 전달하여 실행되는 스크립트입니다. 기본적으로 ScriptBlock 스크립트는 **UnrelatedCode**로 분류됩니다.|

다음 키워드 중 하나로 값을 변경할 수 있습니다.

- `MyCode`는 스크립트를 **MyCode**로 분류합니다.
- `Library`는 스크립트를 **LibraryCode**로 분류합니다.
- `Unrelated`는 스크립트를 **UnrelatedCode**로 분류합니다.

**MyCode, Libraries 및 Unrelated**

**MyCode**, **Libraries** 및 **Unrelated** 키 값 쌍은 분류에 포함할 URL 또는 파일을 지정합니다.

|이름|설명|
|-|-|
|**MyCode**|**MyCode**로 분류된 URL 또는 파일의 배열입니다.|
|**라이브러리**|**LibraryCode**로 분류된 URL 또는 파일의 배열입니다.|
|**Unrelated**|**UnrelatedCode**로 분류된 URL 또는 파일의 배열입니다.|

URL 또는 파일 문자열에는 0개 이상의 문자와 일치하는 `*` 문자가 하나 이상 포함될 수 있습니다. `*`는 정규식 `.*`와 동일합니다.
