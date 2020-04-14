---
title: C++ 개체의 사용자 지정 뷰 만들기
description: Natvis 프레임워크를 사용하여 Visual Studio에서 디버거에서 네이티브 형식을 표시하는 방법을 사용자 지정합니다.
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224513"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis 프레임워크를 사용하여 디버거에서 C++ 개체의 사용자 지정 보기 만들기

Visual Studio *Natvis* 프레임워크는 네이티브 형식이 **로컬** 및 **보기** 창 및 **DataTips와**같은 디버거 변수 창에 표시되는 방식을 사용자 지정합니다. Natvis 시각화를 사용하면 디버깅 중에 만든 형식을 더 잘 볼 수 있습니다.

Natvis는 이전 버전의 Visual Studio의 *autoexp.dat* 파일을 XML 구문, 더 나은 진단, 버전 전환 및 여러 파일 지원으로 대체합니다.

> [!NOTE]
> Natvis 사용자 지정은 클래스및 구조체와 함께 작동하지만 형식은 사용하지 않습니다.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>낫비스 비주얼라이제이서

Natvis 프레임워크를 사용하여 개발자가 디버깅 중에 더 쉽게 볼 수 있도록 만드는 형식에 대한 시각화 규칙을 만듭니다.

예를 들어 다음 그림에서는 사용자 지정 시각화가 적용되지 않고 디버거 창에서 [Windows::UI:Xaml::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) 형식의 변수를 보여 옵니다.

![TextBox 기본 시각화](../debugger/media/dbg_natvis_textbox_default.png "TextBox 기본 시각화")

강조 표시된 행은 `Text` 클래스의 `TextBox` 속성을 보여 줍니다. 복잡한 클래스 계층 구조로 인해 이 속성을 찾기가 어렵습니다. 디버거는 사용자 지정 문자열 형식을 해석하는 방법을 모르므로 텍스트 상자 안에 있는 문자열을 볼 수 없습니다.

Natvis `TextBox` 사용자 지정 시각화 도우미 규칙이 적용될 때 변수 창에서도 동일하게 훨씬 간단해 보입니다. 클래스의 중요한 멤버가 함께 표시되고 디버거는 사용자 지정 문자열 형식의 기본 문자열 값을 표시합니다.

![시각화 도우미를 사용하는 TextBox 데이터](../debugger/media/dbg_natvis_textbox_visualizer.png "시각화 도우미를 사용하는 TextBox 데이터")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ 프로젝트에서 .natvis 파일 사용

Natvis는 *.natvis* 파일을 사용하여 시각화 규칙을 지정합니다. *.natvis* 파일은 *.natvis* 확장이 있는 XML 파일입니다. Natvis 스키마는 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd로*정의됩니다.

*.natvis* 파일의 기본 구조는 시각화 `Type` 항목을 나타내는 하나 이상의 요소입니다. 각 `Type` 요소의 정규화된 이름은 해당 `Name` 특성에 지정됩니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

비주얼 *스튜디오는 %VSINSTALLDIR%\Common7\패키지\디버거\시각화* 도우미 폴더에 있는 일부 *.natvis* 파일을 제공합니다. 이러한 파일에는 여러 일반적인 형식에 대한 시각화 규칙이 있으며 새 형식에 대한 시각화를 작성하는 예제로 사용할 수 있습니다.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ 프로젝트에 .natvis 파일 추가

모든 C++ 프로젝트에 *.natvis* 파일을 추가할 수 있습니다.

**새 *.natvis* 파일을 추가하려면 다음을 수행하십시오.**

1. **솔루션 탐색기에서**C++ 프로젝트 노드를 선택하고 **프로젝트** > **새 항목 추가를**선택하거나 프로젝트를 마우스 오른쪽 단추로 클릭하고 새**항목** **추가를** > 선택합니다.

1. 새 **항목 추가** 대화 상자에서 **Visual C++** > **유틸리티** > **디버거 시각화 파일(.natvis)을**선택합니다.

1. 파일 이름을 지정하고 **에 추가를**선택합니다.

   새 파일이 **솔루션 탐색기에**추가되고 Visual Studio 문서 창에서 열립니다.

Visual Studio 디버거는 C++ 프로젝트에서 *.natvis* 파일을 자동으로 로드하며 기본적으로 프로젝트가 빌드될 때 *.pdb* 파일에도 포함됩니다. 빌드된 앱을 디버깅하는 경우 프로젝트를 열지 않은 경우에도 디버거는 *.pdb* 파일에서 *.natvis* 파일을 로드합니다. *.pdb에*포함 되는 *.natvis* 파일을 원하지 않는 경우 기본 *.pdb* 파일에서 제외할 수 있습니다.

**.pdb에서 *.natvis* 파일을 제외하려면 *다음을 수행합니다.***

1. **솔루션 탐색기에서** *.natvis* 파일을 선택하고 **속성** 아이콘을 선택하거나 파일을 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다.

1. **빌드에서 제외** 옆의 화살표를 드롭다운하고 **예**를 선택한 다음 **확인을**선택합니다.

>[!NOTE]
>실행 파일 프로젝트를 디버깅하려면 C++ 프로젝트를 사용할 수 없으므로 솔루션 항목을 사용하여 *.pdb에*없는 *.natvis* 파일을 추가합니다.

>[!NOTE]
>*.pdb에서* 로드된 Natvis 규칙은 *.pdb가* 참조하는 모듈의 형식에만 적용됩니다. 예를 들어 *Module1.pdb라는* 형식에 `Test`대한 Natvis 항목이 있는 `Test` 경우 *Module1.dll*의 클래스에만 적용됩니다. 다른 모듈이 명명된 `Test`클래스를 정의하는 경우 *Module1.pdb* Natvis 항목은 적용되지 않습니다.

**VSIX 패키지를 통해 *.natvis* 파일을 설치하고 등록하려면 다음을 수행하십시오.**

VSIX 패키지는 *.natvis* 파일을 설치하고 등록할 수 있습니다. 어디에 설치하든 등록된 모든 *.natvis* 파일은 디버깅 중에 자동으로 선택됩니다.

1. VSIX 패키지에 *.natvis* 파일을 포함합니다. 예를 들어 다음 프로젝트 파일의 경우:
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. *source.extension.vsixmanifest* 파일에 *.natvis* 파일을 등록합니다.
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>낫비스 파일 위치

여러 프로젝트에 적용하려는 경우 *.natvis* 파일을 사용자 디렉토리 또는 시스템 디렉토리에 추가할 수 있습니다.

*.natvis* 파일은 다음 순서로 평가됩니다.

1. 로드된 프로젝트에 동일한 이름의 파일이 없는 한 *.pdb에* 포함된 모든 *.natvis* 파일입니다.

2. 로드된 C++ 프로젝트 또는 최상위 솔루션에 있는 *모든 .natvis* 파일입니다. 이 그룹에는 클래스 라이브러리를 포함하여 로드된 모든 C++ 프로젝트가 포함되지만 다른 언어로 된 프로젝트는 포함되지 않습니다.

3. VSIX 패키지를 통해 설치 및 등록된 *모든 .natvis* 파일입니다.

::: moniker range="vs-2017"

4. 사용자 별 Natvis 디렉토리(예: *%USERPROFILE%\문서\비주얼 스튜디오 2017\비주얼라이저).*

::: moniker-end

::: moniker range=">= vs-2019"

4. 사용자 별 Natvis 디렉토리(예: *%USERPROFILE%\문서\비주얼 스튜디오 2019\비주얼라이저).*

::: moniker-end

5. 시스템 차원 Natvis 디렉터리(*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). 이 디렉토리에는 Visual Studio에 설치된 *.natvis* 파일이 있습니다. 관리자 권한이 있는 경우 이 디렉터리에 파일을 추가할 수 있습니다.

## <a name="modify-natvis-files-while-debugging"></a>디버깅하는 동안 .natvis 파일 수정

프로젝트를 디버깅하는 동안 IDE에서 *.natvis* 파일을 수정할 수 있습니다. 디버깅하는 Visual Studio의 동일한 인스턴스에서 파일을 열고 수정한 다음 저장합니다. 파일이 저장되는 즉시 **Watch** 및 **Locals** 창이 변경 을 반영하도록 업데이트됩니다.

또한 디버깅하는 솔루션에 *.natvis* 파일을 추가하거나 삭제할 수 있으며 Visual Studio에서 관련 시각화를 추가하거나 제거할 수 있습니다.

디버깅하는 동안 *.pdb* 파일에 포함된 *.natvis* 파일은 업데이트할 수 없습니다.

Visual Studio 외부에서 *.natvis* 파일을 수정하면 변경 내용이 자동으로 적용되지 않습니다. 디버거 창을 업데이트하려면 **즉시** 창에서 **.natvisreload** 명령을 다시 평가할 수 있습니다. 그런 다음 디버깅 세션을 다시 시작하지 않고 변경 사항이 적용됩니다.

또한 **.natvisreload** 명령을 사용하여 *.natvis* 파일을 최신 버전으로 업그레이드합니다. 예를 들어 *.natvis 파일은* 소스 제어로 체크 인될 수 있으며 다른 사람이 변경한 최근 변경 사항을 선택하려고 합니다.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> 식 및 형식 지정
Natvis 시각화에서는 C++ 식을 사용하여 표시할 데이터 항목을 지정합니다. [컨텍스트 연산자(C++)에](../debugger/context-operator-cpp.md)설명되어 있는 디버거에서 C++ 식의 향상된 기능 및 제한 사항 외에도 다음 사항에 유의하십시오.

- Natvis 식은 현재 스택 프레임이 아닌 시각화되는 개체의 컨텍스트에서 평가됩니다. 예를 들어 `x` Natvis 식에서 시각화 되는 개체에서 **x라는** 필드를 참조 하 고 현재 함수에서 **x라는** 로컬 변수를 참조 합니다. 전역 변수에 액세스할 수 있지만 Natvis 표현식에서 로컬 변수에 액세스할 수는 없습니다.

- Natvis 식은 함수 평가 또는 부작용을 허용하지 않습니다. 함수 호출 및 할당 연산자는 무시됩니다. [디버거 내장 함수](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 는 부작용이 발생하지 않기 때문에 다른 함수 호출이 금지되어 있더라도 어떤 Natvis 식에서든 자유롭게 호출할 수 있습니다.

- 식이 표시되는 방식을 제어하려면 [C++의 형식 지정에](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)설명된 형식 지정기를 사용할 수 있습니다. `Size` [ArrayItems 확장의](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)식과 같이 Natvis에서 내부적으로 항목을 사용할 때 형식 지정자는 무시됩니다.

## <a name="natvis-views"></a>Natvis 뷰

다른 Natvis 뷰를 정의하여 다양한 방법으로 형식을 표시할 수 있습니다. 예를 들어, 다음은 .라는 `std::vector` 단순화된 뷰를 정의하는 `simple`시각화입니다. `DisplayString` `ArrayItems` 및 요소는 기본 뷰와 `simple` 뷰에 표시되지만 `[size]` 및 `[capacity]` 항목은 `simple` 뷰에 표시되지 않습니다.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

**[Watch]** 창에서 **'뷰** 형식 지정기'를 사용하여 대체 뷰를 지정합니다. 간단한 보기는 **vec,보기 (단순)로**나타납니다 .

![단순 보기의 조사식 창](../debugger/media/watch-simpleview.png "단순 보기의 조사식 창")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>낫비스 오류

디버거가 시각화 항목에서 오류가 발생하면 무시합니다. 형식을 원시 형식으로 표시하거나 다른 적합한 시각화를 선택합니다. Natvis 진단을 사용하여 디버거가 시각화 항목을 무시한 이유를 이해하고 기본 구문 및 구문 분석 오류를 확인할 수 있습니다.

**Natvis 진단을 켜려면 다음 을 수행하십시오.**

- **도구** > **옵션(또는** **디버그** > **옵션)>** **디버깅** > **출력 창을**> **Natvis 진단 메시지(C+만)를** **오류,** **경고**또는 **세부 정보로**설정한 다음 **확인을**선택합니다.

오류가 **출력** 창에 나타납니다.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis 구문 참조

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer 요소
`AutoVisualizer` 요소는 *.natvis* 파일의 루트 노드이며 네임스페이스 `xmlns:` 특성을 포함합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

요소에는 `AutoVisualizer` [유형,](#BKMK_Type) [HResult,](#BKMK_HResult) [UIVisualizer](#BKMK_UIVisualizer)및 사용자 지정 시각화 도우미 자식이 있을 수 [있습니다.](#BKMK_CustomVisualizer)

### <a name="type-element"></a><a name="BKMK_Type"></a>형식 요소

기본은 `Type` 다음과 같습니다.

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 요소는 `Type` 다음을 지정합니다.

1. 시각화를 사용해야 하는 `Name` 유형(특성)입니다.

2. 이 형식의 개체 값이 표시되는 모양( `DisplayString` 요소)

3. 사용자가 변수 `Expand` 창(노드)에서 형식을 확장할 때 형식의 멤버는 어떻게 보일지입니다.

#### <a name="templated-classes"></a>템플릿 클래스
요소의 특성은 `Name` 템플릿 클래스 이름에 `*` 사용할 수 있는 와일드카드 문자로 별표를 허용합니다. `Type`

다음 예제에서는 개체가 `CAtlArray<int>` `CAtlArray<float>`a인지 여부에 관계없이 동일한 시각화가 사용됩니다. `CAtlArray<float>`에 대한 특정 시각화 항목이 있는 경우 일반 항목보다 우선합니다.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

매크로 $T1, $T2 등을 사용하여 시각화 항목에서 템플릿 매개 변수를 참조할 수 있습니다. 이러한 매크로의 예를 살펴보려면 Visual Studio와 함께 제공되는 *.natvis* 파일을 참조하세요.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> 시각화 도우미 형식 일치
시각화 항목의 유효성을 검사하지 못하면 사용 가능한 다음 시각화가 사용됩니다.

#### <a name="inheritable-attribute"></a>상속 가능한 특성
선택적 `Inheritable` 특성은 시각화가 기본 형식또는 기본 형식 및 모든 파생 형식에만 적용되는지 여부를 지정합니다. `Inheritable`의 기본값은 `true`입니다.

다음 예제에서는 시각화형식에만 `BaseClass` 적용됩니다.

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority 특성

선택적 `Priority` 특성은 정의가 구문 분석하지 못하는 경우 대체 정의를 사용할 순서를 지정합니다. 가능한 `Priority` 값은 " `Low` `MediumLow`,`Medium` `MediumHigh`의 `High`값은 " 기본값은 `Medium`입니다. 특성은 `Priority` 동일한 *.natvis* 파일 내의 우선 순위 간에만 구분됩니다.

다음 예제는 먼저 2015 STL과 일치하는 항목을 구문 분석합니다. 구문 분석하지 못하면 STL의 2013 버전에 대한 대체 항목을 사용합니다.

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional 특성
모든 노드에 `Optional` 특성을 배치할 수 있습니다. 선택적 노드 내의 하위 표현식이 구문 분석에 실패하면 디버거는 해당 노드를 `Type` 무시하지만 나머지 규칙을 적용합니다. 다음 형식에서 `[State]` 는 필수이지만 `[Exception]` 은 선택적입니다.  `MyNamespace::MyClass` `M_exceptionHolder`_= `[State]` `[Exception]` 노드와 노드가 모두 나타나지만 필드가 없는 `_M_exceptionHolder` 경우 `[State]` 노드만 나타납니다.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> 조건 특성

선택적 `Condition` 특성은 많은 시각화 요소에 사용할 수 있으며 시각화 규칙을 사용할 시기를 지정합니다. 조건 특성 내의 식이 `false`확인되면 시각화 규칙이 적용되지 않습니다. `true`을 평가하거나 특성이 없는 `Condition` 경우 시각화가 적용됩니다. 시각화 항목에서 if-else 논리에 이 특성을 사용할 수 있습니다.

예를 들어 다음 시각화에는 `DisplayString` 스마트 포인터 유형에 대한 두 가지 요소가 있습니다. 멤버가 `_Myptr` 비어 있으면 첫 번째 `DisplayString` 요소의 조건이 `true`확인되므로 해당 양식이 표시됩니다. 멤버가 `_Myptr` 비어 있지 않은 경우 조건이 `false`을 평가하고 `DisplayString` 두 번째 요소가 표시됩니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView 및 ExcludeView 특성

및 `IncludeView` `ExcludeView` 속성은 특정 뷰에 표시하거나 표시하지 않을 요소를 지정합니다. 예를 들어 다음 Natvis 의 `std::vector`사양에서는 `simple` 뷰에 및 `[size]` `[capacity]` 항목이 표시되지 않습니다.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

형식 `IncludeView` 및 개별 `ExcludeView` 멤버에서 및 특성을 사용할 수 있습니다.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>버전 요소
`Version` 요소는 특정 모듈 및 버전에 대한 시각화 항목의 범위를 지정합니다. 이 `Version` 요소는 이름 충돌을 방지하고, 의도하지 않은 불일치를 줄이며, 다른 형식 버전에 대해 서로 다른 시각화를 허용합니다.

다른 모듈에서 사용하는 공통 헤더 파일이 형식을 정의하는 경우 버전이 지정된 시각화는 형식이 지정된 모듈 버전에 있는 경우에만 나타납니다.

다음 예제에서는 시각화버전 1.0에서 `DirectUI::Border` 1.5까지의 형식에 대해서만 시각화를 `Windows.UI.Xaml.dll` 적용할 수 있습니다.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

둘 다 `Min` 필요하지 않습니다. `Max` 선택적 특성입니다. 와일드카드 문자는 지원되지 않습니다.

속성은 `Name` *hello.exe* 또는 *some.dll*과 같은 형식 *filename.ext에*있습니다. 경로 이름은 허용되지 않습니다.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>표시문자열 요소
요소는 `DisplayString` 변수의 값으로 표시 할 문자열을 지정합니다. 또한 식과 혼합된 임의의 문자열을 허용합니다. 중괄호 내의 모든 항목은 식으로 해석됩니다. 예를 들어, `DisplayString` 다음 항목:

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

이 그림에서와 `CPoint` 같이 형식의 변수가 표시된다는 것을 의미합니다.

 ![표시 문자열 요소 사용](../debugger/media/dbg_natvis_cpoint_displaystring.png "표시 문자열 요소 사용")

의 구성원인 식에서 및 `CPoint`의 멤버는 중괄호 내부에 있으므로 해당 값이 평가됩니다. `y` `DisplayString` `x` 또한 이 예제에서는 이중 중괄호(또는 `{{` `}}` )를 사용하여 중괄호를 이스케이프하는 방법을 보여 주기도 합니다.

> [!NOTE]
> `DisplayString` 요소는 임의 문자열 및 중괄호 구문을 허용하는 유일한 요소입니다. 다른 모든 시각화 요소는 디버거가 평가할 수 있는 표현식만 허용합니다.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>문자열뷰 요소

요소는 `StringView` 디버거가 기본 제공 텍스트 시각화 도우미에 보낼 수 있는 값을 정의합니다. 예를 들어 형식에 대한 다음과 `ATL::CStringT` 같은 시각화가 제공됩니다.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

개체는 `CStringT` 다음 예제와 같은 변수 창에 표시됩니다.

![CStringT DisplayString 요소](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString 요소")

요소를 `StringView` 추가하면 디버거가 값을 텍스트 시각화로 표시할 수 있습니다.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

디버깅 하는 동안 변수 옆에 돋보기 아이콘을 선택 하 고 **텍스트 시각화 도우미를** 선택 하 여 **m_pszData** 가리키는 문자열을 표시 할 수 있습니다.

 ![StringView 시각화 도우미가 있는 CStringT 데이터](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView 시각화 도우미가 있는 CStringT 데이터")

식에는 `{m_pszData,su}` 값을 유니코드 문자열로 표시하는 C++ 형식 지정자 **su가**포함되어 있습니다. 자세한 내용은 [C++의 형식 지정자를](../debugger/format-specifiers-in-cpp.md)참조하십시오.

### <a name="expand-element"></a><a name="BKMK_Expand"></a>요소 확장

선택적 `Expand` 노드는 가변 창에서 형식을 확장할 때 시각화된 형식의 자식을 사용자 지정합니다. 노드는 `Expand` 자식 요소를 정의하는 자식 노드 목록을 허용합니다.

- 노드가 `Expand` 시각화 항목에 지정되지 않은 경우 자식은 기본 확장 규칙을 사용합니다.

- 노드가 `Expand` 하위 노드 없이 지정되면 디버거 창에서 형식을 확장할 수 없습니다.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> 항목 확장

 요소는 `Item` `Expand` 노드에서 가장 기본적이고 일반적인 요소입니다. `Item` 은 단일 자식 요소를 정의합니다. 예를 들어 `CRect` , `top`". `left` `right` `bottom` 및 다음과 같은 시각화 항목이 있는 클래스입니다.

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

디버거 창에서 형식은 `CRect` 다음과 같습니다.

![Item 요소 확장이 있는 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Item 요소 확장이 있는 CRect")

디버거는 `Width` 및 `Height` 요소에 지정된 식을 평가하고 변수 창의 **Value** 열에 값을 표시합니다.

디버거는 모든 사용자 지정 확장에 대해 **[Raw View]** 노드를 자동으로 만듭니다. 앞의 스크린샷에는 개체의 기본 원시 뷰가 Natvis 시각화와 어떻게 다른지 보여 드리기 위해 확장된 **[Raw View]** 노드가 표시됩니다. 기본 확장은 기본 클래스에 대한 하위 트리를 만들고 기본 클래스의 모든 데이터 멤버를 자식으로 나열합니다.

> [!NOTE]
> 항목 요소의 표현식이 복합 형식을 가리키는 경우 **항목** 노드 자체는 확장할 수 있습니다.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Size
`ArrayItems` 노드를 사용하면 Visual Studio 디버거가 형식을 배열로 해석하고 해당 개별 요소를 표시하도록 할 수 있습니다. `std::vector` 에 대한 시각화는 좋은 예입니다.

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` 는 변수 창에서 확장되는 경우 개별 요소를 표시합니다.

![ArrayItems 확장을 사용하는 std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "ArrayItems 확장을 사용하는 std::vector")

노드에는 `ArrayItems` 다음이 있어야 합니다.

- 디버거에서 배열의 길이를 파악하기 위한 `Size` 식(정수로 계산되어야 함)입니다.
- 첫 `ValuePointer` 번째 요소(그렇지 않은 `void*`요소 형식의 포인터여야 함을)를 가리키는 식입니다.

배열 하한의 기본값은 0입니다. 값을 재정의하려면 `LowerBound` 요소를 사용합니다. Visual Studio와 함께 제공되는 *.natvis* 파일에는 예제가 있습니다.

>[!NOTE]
>예를 `[]` `vector[i]`들어 형식 자체(예: )가 이 연산자(예:)를 사용하는 `ArrayItems`단일 `CATLArray`차원 배열 시각화와 함께 연산자(예: )를 사용할 수 없습니다.

다차원 배열을 지정할 수도 있습니다. 이 경우 디버거는 자식 요소를 제대로 표시하기 위해 약간 더 많은 정보가 필요합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`는 배열이 행 주 또는 열 주 순서인지 여부를 지정합니다.
- `Rank` 는 배열의 차수를 지정합니다.
- `Size` 요소는 해당 차원에서 배열의 길이를 확인하기 위해 차원 인덱스로 대체되는 암시적 `$i` 매개 변수를 허용합니다. 이전 예제에서 식은 `_M_extent.M_base[0]` 0차원, `_M_extent._M_base[1]` 1차원 등의 길이를 지정해야 합니다.

디버거 창에서 2차원 `Concurrency::array` 개체의 모양은 다음과 같습니다.

![ArrayItems 확장을 가진 2차원 배열](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems 확장을 가진 2차원 배열")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems 확장

배열 요소가 `ArrayItems` 메모리에 연속적으로 배치된 경우에만 확장을 사용할 수 있습니다. 디버거는 포인터를 증가시키기만 하면 다음 요소에 도착합니다. 값 노드에 대한 인덱스를 조작해야 하는 `IndexListItems` 경우 노드를 사용합니다. `IndexListItems` 노드가 있는 시각화는 다음과 같습니다.

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

유일한 `ArrayItems` 차이점은 `IndexListItems` 암시적 `ValueNode` `$i` 매개 변수가 있는 i<sup>th</sup> 요소에 대한 전체 식을 기대하는 의 입니다.

>[!NOTE]
>예를 `[]` `vector[i]`들어 형식 자체(예: )가 이 연산자(예:)를 사용하는 `IndexListItems`단일 `CATLArray`차원 배열 시각화와 함께 연산자(예: )를 사용할 수 없습니다.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 확장

시각화된 형식이 링크된 목록을 나타내는 경우 디버거에서는 `LinkedListItems` 노드를 사용하여 해당 자식을 표시할 수 있습니다. 형식에 대한 다음 `CAtlList` 시각화는 다음을 사용합니다. `LinkedListItems`

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

`Size` 요소는 목록의 길이를 참조합니다. `HeadPointer` 는 첫 번째 요소를 가리키고, `NextPointer` 는 다음 요소를 참조하며, `ValueNode` 는 항목의 값을 참조합니다.

디버거는 상위 목록 `NextPointer` `ValueNode` 유형이 아닌 `LinkedListItems` 노드 요소의 컨텍스트에서 및 식을 평가합니다. 앞의 `CAtlList` 예제에서는 연결된 `CNode` 목록의 노드인 클래스(에서 `atlcoll.h`있음)가 있습니다. `m_pNext`해당 `m_element` `CNode` 클래스의 필드가 아니라 `CAtlList` 클래스의 필드입니다.

`ValueNode`노드 자체를 참조하는 `this` `LinkedListItems` 데 사용할 수 있습니다.

#### <a name="customlistitems-expansion"></a>CustomListItems 확장

`CustomListItems` 확장을 사용하여 해시 테이블 같은 데이터 구조 전송에 대한 사용자 지정 논리를 작성할 수 있습니다. 평가해야 하는 모든 것에 C++ 식을 사용할 수 `CustomListItems` 있지만 에 `ArrayItems` `IndexListItems`대한 금형에 맞지 않는 `LinkedListItems`데이터 구조를 시각화하는 데 사용합니다.

확장에 `Exec` 정의된 변수와 개체를 `CustomListItems` 사용하여 확장 내부에서 코드를 실행하는 데 사용할 수 있습니다. `Exec`을 사용하여 논리 연산자, 산술 연산자 및 할당 연산자()를 사용할 수 있습니다. C++ 식 `Exec` 계산기에서 지원하는 [디버거 내장 함수를](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 제외하고는 함수를 평가하는 데 사용할 수 없습니다.

다음 시각화 도우미에 대 `CAtlMap` 한 `CustomListItems` 적절 한 훌륭한 예입니다.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> TreeItems 확장
 시각화된 형식이 트리를 나타내는 경우 디버거에서는 `TreeItems` 노드를 사용하여 트리를 단계별로 진행하면서 해당 자식을 표시할 수 있습니다. 노드를 사용하는 형식에 `std::map` 대한 시각화는 다음과 같습니다. `TreeItems`

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

구문은 노드와 유사합니다. `LinkedListItems` `LeftPointer`을 `RightPointer`위해 `ValueNode` 트리 노드 클래스의 컨텍스트에서 평가됩니다. `ValueNode`노드 자체를 참조하는 `this` 데 사용할 수 있습니다. `TreeItems`

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 확장
 요소는 `ExpandedItem` 시각화된 형식의 자식인 것처럼 기본 클래스 또는 데이터 멤버의 속성을 표시하여 집계된 자식 뷰를 생성합니다. 디버거는 지정된 식을 평가하고 결과의 자식 노드를 시각화된 형식의 자식 목록에 추가합니다.

예를 들어 스마트 포인터 `auto_ptr<vector<int>>` 유형은 일반적으로 다음과 같이 표시됩니다.

 ![자동&#95;ptr&#60;벡터&#60;int&#62;&#62; 기본 확장](../debugger/media/dbg_natvis_expand_expandeditem_default.png "기본 확장")

 벡터의 값을 보려면 `_Myptr` 멤버를 통과하면서 변수 창에서 두 개의 레벨을 드릴다운해야 합니다. `ExpandedItem` 요소를 추가하면 계층 구조에서 `_Myptr` 변수를 제거하고 벡터 요소를 바로 확인할 수 있습니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![자동&#95;ptr&#60;벡터&#60;int&#62;&#62; 확장항목 확장](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 확장")

다음 예제에서는 파생 된 클래스에서 기본 클래스에서 속성을 집계 하는 방법을 보여 주어 있습니다. `CPanel` 클래스가 `CFrameworkElement`에서 파생된다고 가정해 보겠습니다. 노드 시각화는 기본 `CFrameworkElement` 클래스에서 오는 속성을 반복하는 대신 해당 속성을 `CPanel` 클래스의 자식 목록에 추가합니다. `ExpandedItem`

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

파생 클래스에 대한 시각화 일치를 해제하는 **nd** 형식 지정기가 여기에 필요합니다. 그렇지 않으면 `*(CFrameworkElement*)this` 기본 시각화 `CPanel` 유형 일치 규칙이 가장 적합한 것으로 간주되므로 식이로 인해 시각화가 다시 적용됩니다. **nd** 형식 지정기를 사용하여 디버거에게 기본 클래스 시각화를 사용하거나 기본 클래스에 시각화가 없는 경우 기본 확장을 사용하도록 지시합니다.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>합성 항목 확장
 `ExpandedItem` 요소는 계층 구조를 제거하여 데이터를 보다 평면적으로 표시하지만 `Synthetic` 노드는 그 반대입니다. 식의 결과가 아닌 인공 자식 요소를 만들 수 있습니다. 인공 요소는 자체의 자식 요소를 가질 수 있습니다. 다음 예의 `Concurrency::array` 형식에 대한 시각화에서는 사용자에게 진단 메시지를 표시하기 위해 `Synthetic` 노드를 사용합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![동시성::합성 요소 확장배열](../debugger/media/dbg_natvis_expand_synthetic.png "동시성::합성 요소 확장배열")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>H결과 요소
 요소를 `HResult` 사용하면 디버거 창에서 **HRESULT에** 대해 표시된 정보를 사용자 지정할 수 있습니다. 요소에는 `HRValue` 사용자 지정할 **HRESULT의** 32비트 값이 포함되어야 합니다. 요소에는 `HRDescription` 디버거 창에 표시할 정보가 포함되어 있습니다.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>UI 비주얼라이저 요소
`UIVisualizer` 요소는 디버거에 그래픽 시각화 도우미 플러그 인을 등록합니다. 그래픽 시각화 도우미는 데이터 형식과 일치하는 방식으로 변수 또는 개체를 표시하는 대화 상자 또는 기타 인터페이스를 만듭니다. 시각화 도우미 플러그인은 [VSPackage로](../extensibility/internals/vspackages.md)작성되어야 하며 디버거가 사용할 수 있는 서비스를 노출해야 합니다. *.natvis* 파일에는 해당 이름, 노출된 서비스의 GUID 및 시각화할 수 있는 유형과 같은 플러그인에 대한 등록 정보가 포함되어 있습니다.

UIVisualizer 요소의 예는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- 특성 `ServiceId`  -  `Id` 쌍은 `UIVisualizer`을 식별합니다. 은 `ServiceId` 시각화 도우미 패키지가 노출하는 서비스의 GUID입니다. `Id`는 서비스가 두 개 이상의 서비스를 제공하는 경우 시각화 도우미를 구별하는 고유 식별자입니다. 앞의 예제에서 동일한 시각화 도우미 서비스는 두 개의 시각화 도우미를 제공합니다.

- 디버거의 `MenuName` 돋보기 아이콘 옆에 있는 드롭다운에 표시할 시각화 도우미 이름을 정의합니다. 다음은 그 예입니다.

  ![UIVisualizer 메뉴 바로 가기 메뉴](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 메뉴 바로 가기 메뉴")

*.natvis* 파일에 정의된 각 형식은 표시할 수 있는 UI 시각화 도우미를 명시적으로 나열해야 합니다. 디버거는 형식 항목의 시각화 도우미 참조를 등록된 시각화 도우미와 일치시다. 예를 들어, 참조에 `std::vector` 대한 `UIVisualizer` 다음 형식 항목은 앞의 예제에서 입니다.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 메모리 내 비트맵을 `UIVisualizer` 보는 데 사용되는 [이미지 보기](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) 확장의 예를 볼 수 있습니다.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer 요소
 `CustomVisualizer`는 Visual Studio 코드에서 시각화를 제어하기 위해 작성하는 VSIX 확장을 지정하는 확장성 지점입니다. VSIX 확장 작성에 대한 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

XML Natvis 정의보다 사용자 지정 시각화 도우미를 작성하는 것은 훨씬 더 많은 작업이지만 Natvis가 수행하거나 지원하지 않는 작업에 대한 제약 조건이 없습니다. 사용자 지정 시각화 도우미는 디버거 확장성 API의 전체 집합에 액세스할 수 있으며, 디버지 프로세스를 쿼리 및 수정하거나 Visual Studio의 다른 부분과 통신할 수 있습니다.

 요소에 `Condition`대해 에서 `IncludeView`및 `ExcludeView` 특성을 사용할 수 있습니다. `CustomVisualizer`

 ## <a name="limitations"></a>제한 사항

Natvis 사용자 지정은 클래스및 구조체와 함께 작동하지만 형식은 사용하지 않습니다.

Natvis는 기본 형식(예: `int`기본 `bool`형식) 또는 기본 형식에 대한 포인터에 대해 시각화 도우미를 지원하지 않습니다. 이 시나리오에서 한 가지 옵션은 사용 사례에 적합한 [형식 지정기를](../debugger/format-specifiers-in-cpp.md) 사용하는 것입니다. 예를 들어 코드에서 `double* mydoublearray` 사용하는 경우 처음 100개 요소를 표시하는 식과 `mydoublearray, [100]`같은 디버거의 **Watch** 창에서 배열 형식 지정기를 사용할 수 있습니다.
