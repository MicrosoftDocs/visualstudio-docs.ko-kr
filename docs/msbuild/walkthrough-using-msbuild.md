---
title: '연습: MSBuild 사용 | Microsoft Docs'
ms.date: 03/20/2019
ms.topic: conceptual
ms.custom: contperfq1
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c04344e361bea15c39b092c59e76d1853e3969e2
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89738313"
---
# <a name="walkthrough-use-msbuild"></a>연습: MSBuild 사용

MSBuild는 Microsoft 및 Visual Studio용 빌드 플랫폼입니다. 이 연습에서는 MSBuild의 구성 요소를 소개하고 MSBuild 프로젝트를 작성, 조작 및 디버깅하는 방법을 보여 줍니다. 학습 내용은 다음과 같습니다.

- 프로젝트 파일 만들기 및 조작

- 빌드 속성을 사용하는 방법

- 빌드 항목을 사용하는 방법

Visual Studio 또는 **명령 창**에서 MSBuild를 실행할 수 있습니다. 이 연습에서는 Visual Studio를 사용하여 MSBuild 프로젝트 파일을 만듭니다. Visual Studio에서 프로젝트 파일을 편집한 다음, **명령 창**을 사용하여 프로젝트를 빌드하고 결과를 검사할 수 있습니다.

## <a name="create-an-msbuild-project"></a>MSBuild 프로젝트 만들기

 Visual Studio 프로젝트 시스템은 MSBuild를 기반으로 합니다. 따라서 Visual Studio를 사용하여 새 프로젝트 파일을 쉽게 만들 수 있습니다. 이 섹션에서는 Visual C# 프로젝트 파일을 만듭니다. 대신 Visual Basic 프로젝트 파일을 만들도록 선택할 수도 있습니다. 이 연습의 컨텍스트에서 두 프로젝트 파일에는 큰 차이가 없습니다.

**프로젝트 파일을 만들려면**

1. Visual Studio를 열고 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl+Q**를 입력하여 검색 상자를 열고, **winforms**를 입력한 다음, **새 Windows Forms 앱(.NET Framework) 만들기**를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.

    **이름** 상자에 `BuildApp`을 입력합니다. 솔루션의 **위치**를 *D:\\* 와 같이 입력합니다. **솔루션**, **솔루션 이름**(**BuildApp**) 및 **프레임워크**의 기본값을 적용합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#**  > **Windows Desktop**을 확장한 다음, **Windows Forms 앱(.NET Framework)** 을 선택합니다. 그런 다음, **확인**을 선택합니다.

    **이름** 상자에 `BuildApp`을 입력합니다. 솔루션의 **위치**를 *D:\\* 와 같이 입력합니다. **솔루션용 디렉터리 만들기**의 기본값(선택된 상태), **소스 제어에 추가**의 기본값(선택되지 않은 상태) 및 **솔루션 이름**의 기본값(**BuildApp**)을 적용합니다.
    ::: moniker-end

1. **확인** 또는 **만들기**를 클릭하여 프로젝트 파일을 만듭니다.

## <a name="examine-the-project-file"></a>프로젝트 파일 검사

 이전 섹션에서는 Visual Studio를 사용하여 Visual C# 프로젝트 파일을 만들었습니다. 프로젝트 파일은 BuildApp이라는 프로젝트 노드로 **솔루션 탐색기**에 표시됩니다. Visual Studio 코드 편집기를 사용하여 프로젝트 파일을 검사할 수 있습니다.

**프로젝트 파일을 검사하려면**

1. **솔루션 탐색기**에서 프로젝트 노드 **BuildApp**을 클릭합니다.

1. **속성** 브라우저에서 **프로젝트 파일** 속성이 *BuildApp.csproj*인지 확인합니다. 모든 프로젝트 파일 이름에는 접미사 *proj*가 추가됩니다. Visual Basic 프로젝트를 만든 경우 프로젝트 파일 이름은 *BuildApp.vbproj*가 됩니다.

1. 프로젝트 노드를 다시 마우스 오른쪽 단추로 클릭하고 **BuildApp.csproj 편집**을 클릭합니다. 

     프로젝트 파일이 코드 편집기에 나타납니다.

>[!NOTE]
> C++ 같은 일부 프로젝트 형식의 경우 프로젝트 파일을 열고 편집하려면 프로젝트를 언로드해야 합니다(프로젝트 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트**언로드 선택).

## <a name="targets-and-tasks"></a>대상 및 작업

프로젝트 파일은 루트 노드 [프로젝트](../msbuild/project-element-msbuild.md)를 포함하는 XML 형식의 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

최신 .NET Core(SDK 스타일) 프로젝트에는 `Sdk` 특성이 있습니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

SDK 스타일 프로젝트가 아닌 경우에는 프로젝트 요소에 xmlns 네임스페이스를 지정해야 합니다. `ToolsVersion`이 새 프로젝트에 존재하는 경우 "15.0"이어야 합니다.

애플리케이션 빌드 작업에서는 [대상](../msbuild/target-element-msbuild.md) 및 [작업](../msbuild/task-element-msbuild.md) 요소를 사용합니다.

- 작업(task)은 작업(work)의 최소 단위(빌드의 "구성 요소")이며, 입력과 출력을 포함할 수 있는 독립적인 실행 가능 구성 요소입니다. 현재 프로젝트 파일에는 참조되거나 정의된 작업(task)이 없습니다. 아래 섹션에서 프로젝트 파일에 작업(task)을 추가합니다. 자세한 내용은 [작업](../msbuild/msbuild-tasks.md) 항목을 참조하세요.

- 대상은 작업의 명명된 순서입니다. 자세한 내용은 [대상](../msbuild/msbuild-targets.md) 항목을 참조하세요.
- [작업의 명명된 순서일 수 있지만 빌드하거나 수행할 항목을 나타내므로 목표 중심으로 정의하는 것이 중요합니다.]

기본 대상은 프로젝트 파일에 정의되어 있지 않으며 대신에 가져오는 프로젝트에 지정됩니다. [가져오기](../msbuild/import-element-msbuild.md) 요소는 가져오는 프로젝트를 지정합니다. 예를 들어 C# 프로젝트에서 기본 대상은 *Microsoft.CSharp.targets* 파일에서 가져옵니다.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

가져온 파일은 참조될 때마다 프로젝트 파일에 실제로 삽입됩니다.

SDK 스타일 프로젝트에서는 SDK 특성으로 인해 이 파일을 암시적으로 가져오므로 이 가져오기 요소가 표시되지 않습니다.

MSBuild는 빌드의 대상을 추적하며 각 대상이 여러 번 빌드되지 않음을 보장합니다.

## <a name="add-a-target-and-a-task"></a>대상 및 작업 추가

 이 섹션에서는 프로젝트 파일에 대상을 추가합니다. 그리고 메시지를 인쇄하는 작업을 대상에 추가합니다.

**대상 및 작업을 추가하려면**

1. 프로젝트 파일에서 Import 문 바로 뒤에 다음 줄을 추가합니다.

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    그러면 HelloWorld라는 대상이 생성됩니다. 프로젝트 파일을 편집하는 동안에는 IntelliSense가 지원됩니다.

2. 결과 섹션이 다음과 같아지도록 HelloWorld 대상에 줄을 추가합니다.

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. 프로젝트 파일을 저장합니다.

메시지 작업은 MSBuild와 함께 제공되는 여러 작업 중 하나입니다. 사용 가능한 작업 및 사용법 정보의 전체 목록은 [작업 참조](../msbuild/msbuild-task-reference.md)를 참조하세요.

메시지 작업에서는 Text 특성의 문자열 값을 입력으로 사용하며 출력 디바이스에 해당 값을 표시하거나 해당되는 경우 하나 이상의 로그에 기록합니다. HelloWorld 대상은 메시지 작업을 "Hello"와 "World"를 표시하는 데 각각 한 번씩 두 번 실행합니다.

## <a name="build-the-target"></a>대상 빌드

Visual Studio에서 이 프로젝트를 빌드하려고 하면 정의한 대상이 빌드되지 않습니다. Visual Studio에서는 가져온 *.targets* 파일에 아직 있는 기본 대상을 선택하기 때문입니다.

Visual Studio용 **개발자 명령 프롬프트**에서 MSBuild를 실행하여 위에 정의되어 있는 HelloWorld 대상을 빌드합니다. -target 또는 -t 명령줄 스위치를 사용하여 대상을 선택합니다.

> [!NOTE]
> 아래 섹션에서 **개발자 명령 프롬프트**를 **명령 창**으로 지칭하겠습니다.

**대상을 빌드하려면**

1. **명령 창**을 엽니다.

   (Windows 10) 작업 표시줄의 검색 상자에 `dev` 또는 `developer command prompt`와 같은 도구 이름을 입력합니다. 그러면 검색 패턴과 일치하는 설치된 앱의 목록이 표시됩니다.

   수동으로 찾아야 하는 경우 파일은 *<visualstudio 설치 폴더\>\<version>\Common7\Tools* 폴더의 *LaunchDevCmd.bat*입니다.

2. 명령 창에서 프로젝트 파일을 포함하는 폴더(이 연습의 경우 *D:\BuildApp\BuildApp*)로 이동합니다.

3. 명령 스위치 `-t:HelloWorld`를 사용하여 msbuild를 실행합니다. 그러면 HelloWorld 대상이 선택 및 빌드됩니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. **명령 창**에서 출력을 검사합니다. "Hello" 및 "World"의 두 줄이 표시됩니다.

    ```output
    Hello
    World
    ```

> [!NOTE]
> 이 두 줄 대신 `The target "HelloWorld" does not exist in the project`가 표시되는 경우에는 코드 편집기에서 프로젝트 파일을 저장하지 않은 것일 수 있습니다. 파일을 저장하고 다시 시도합니다.

 코드 편집기와 명령 창을 오가면서 프로젝트 파일을 변경하고 결과를 빠르게 확인할 수 있습니다.

## <a name="build-properties"></a>빌드 속성

 빌드 속성은 빌드를 안내하는 이름-값 쌍입니다. 여러 빌드 속성이 프로젝트 파일의 위쪽에 이미 정의되어 있습니다.

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 모든 속성은 PropertyGroup 요소의 자식 요소입니다. 속성의 이름은 자식 요소의 이름이며 속성값은 자식 요소의 텍스트 요소입니다. 예를 들면 다음과 같습니다.

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 위의 코드는 TargetFrameworkVersion이라는 속성을 정의하고 해당 속성에 문자열 값 “v4.5”를 제공합니다.

 빌드 속성은 언제든지 다시 정의할 수 있습니다. 조건

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 위의 코드가 프로젝트 파일 뒷부분이나 프로젝트 파일에서 나중에 가져온 파일에 나오는 경우 TargetFrameworkVersion은 새 값인 "v3.5"를 사용합니다.

## <a name="examine-a-property-value"></a>속성 값 검사

 속성값을 가져오려면 다음 구문을 사용합니다. 여기서 `PropertyName`은 속성의 이름입니다.

```xml
$(PropertyName)
```

이 구문을 사용하여 프로젝트 파일의 일부 속성을 검사합니다.

**속성 값을 검사하려면**

1. 코드 편집기에서 HelloWorld 대상을 다음 코드로 바꿉니다.

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. 프로젝트 파일을 저장합니다.

1. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. 출력을 검사합니다. 다음과 같은 두 줄이 표시됩니다. 사용 중인 .NET Framework 버전은 이 줄과 다를 수 있습니다.

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>조건부 속성

`Configuration`과 같은 대다수 속성은 조건부로 정의됩니다. 즉, 속성 요소에 `Condition` 특성이 나타납니다. 조건부 속성은 조건이 "true"로 확인되는 경우에만 정의되거나 다시 정의됩니다. 정의되지 않은 속성에는 기본값(빈 문자열)이 제공됩니다. 예를 들면 다음과 같습니다.

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

위의 코드는 "Configuration 속성이 아직 정의되지 않은 경우 정의하고 값으로 'Debug'를 지정한다"는 의미입니다.

거의 모든 MSBuild 요소는 Condition 특성을 포함할 수 있습니다. Condition 특성을 사용하는 방법에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.

### <a name="reserved-properties"></a>예약된 속성

MSBuild는 몇 개의 속성 이름을 예약하여 프로젝트 파일과 MSBuild 이진 파일에 대한 정보를 저장합니다. MSBuildToolsPath는 예약된 속성의 한 예입니다. 예약된 속성은 다른 속성과 마찬가지로 $ 표기법을 사용하여 참조됩니다. 자세한 내용은 [방법: 프로젝트 파일의 이름 또는 위치 참조](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) 및 [MSBuild의 예약된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)을 참조하세요.

### <a name="environment-variables"></a>환경 변수

프로젝트 파일의 환경 변수는 빌드 속성과 같은 방식으로 참조할 수 있습니다. 예를 들어 프로젝트 파일에서 PATH 환경 변수를 사용하려면 $(Path)를 사용합니다. 프로젝트에 환경 변수와 이름이 같은 속성 정의가 포함되어 있으면 프로젝트의 속성이 환경 변수의 값을 재정의합니다. 자세한 내용은 [방법: 빌드 시 환경 변수 사용](../msbuild/how-to-use-environment-variables-in-a-build.md)을 참조하세요.

## <a name="set-properties-from-the-command-line"></a>명령줄에서 속성 설정

-property 또는 -p 명령줄 스위치를 사용하여 명령줄에서 속성을 정의할 수 있습니다. 명령줄에서 수신된 속성값은 프로젝트 파일 및 환경 변수에 설정되어 있는 속성값을 재정의합니다.

**명령줄에서 속성 값을 설정하려면**

1. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```output
    Configuration is Release.
    ```

MSBuild는 Configuration 속성을 생성하고 "Release" 값을 지정합니다.

## <a name="special-characters"></a>특수 문자

MSBuild 프로젝트 파일에서 특정 문자는 특수한 의미로 사용됩니다. 이러한 문자의 예로는 세미콜론(;) 및 별표(*)를 들 수 있습니다. 프로젝트 파일에서 해당 특수 문자를 리터럴로 사용하려면 %\<xx> 구문을 사용하여 해당 문자를 지정해야 합니다. 여기서 \<xx>는 문자의 ASCII 16진수 값을 나타냅니다.

특수 문자를 사용해 Configuration 속성값을 표시하도록 메시지 작업을 변경하면 해당 작업을 보다 쉽게 읽을 수 있습니다.

**메시지 작업에 특수 문자를 사용하려면**

1. 코드 편집기에서 두 메시지 작업을 모두 다음 줄로 바꿉니다.

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. 프로젝트 파일을 저장합니다.

1. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```output
    $(Configuration) is "Debug"
    ```

자세한 내용은 [MSBuild 특수 문자](../msbuild/msbuild-special-characters.md)를 참조하세요.

## <a name="build-items"></a>항목 빌드

항목은 빌드 시스템에 대한 입력으로 사용되는 정보 부분(일반적으로는 파일 이름)입니다. 예를 들어 소스 파일을 나타내는 항목 컬렉션을 Compile이라는 작업으로 전달하여 해당 항목을 어셈블리로 컴파일할 수 있습니다.

모든 항목은 ItemGroup 요소의 자식 요소입니다. 항목 이름은 자식 요소의 이름이고 항목 값은 자식 요소의 Include 특성 값입니다. 이름이 같은 항목의 값은 해당 이름의 항목 종류로 수집됩니다.  예를 들면 다음과 같습니다.

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

위의 코드는 두 항목이 포함된 항목 그룹을 정의합니다. 항목 종류 컴파일에는 다음 두 가지 값이 있습니다. *Program.cs* 및 *Properties\AssemblyInfo.cs*.

다음 코드는 이 두 파일을 모두 세미콜론으로 구분하여 Include 특성 하나에 선언하는 방식으로 같은 항목 종류를 만듭니다.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

> [!NOTE]
> 파일 경로는 프로젝트 파일이 가져온 프로젝트 파일이더라도 MSBuild 프로젝트 파일이 포함된 폴더를 기준으로 합니다. 여기에는 몇 가지 예외가 있습니다. [Import](import-element-msbuild.md) 및 [UsingTask](usingtask-element-msbuild.md) 요소를 사용할 경우를 예로 들 수 있습니다.

## <a name="examine-item-type-values"></a>항목 종류 값 검사

 항목 종류의 값을 가져오려면 다음 구문을 사용합니다. 여기서 ItemType은 항목 종류의 이름입니다.

```xml
@(ItemType)
```

이 구문을 사용하여 프로젝트 파일에서 Compile 항목 종류를 검사합니다.

**항목 종류 값을 검사하려면**

1. 코드 편집기에서 HelloWorld 대상 작업을 다음 코드로 바꿉니다.

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. 프로젝트 파일을 저장합니다.

1. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. 출력을 검사합니다. 다음과 같은 긴 줄이 표시됩니다.

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

기본적으로 항목 종류의 값은 세미콜론으로 구분됩니다.

항목 종류의 구분 기호를 변경하려면 다음 구문을 사용합니다. 여기서 ItemType은 항목 종류이고 Separator는 하나 이상의 구분 문자를 포함하는 문자열입니다.

```xml
@(ItemType, Separator)
```

캐리지 리턴과 줄 바꿈(%0A%0D)을 사용하여 Compile 항목을 한 줄에 하나씩 표시하도록 메시지 작업을 변경합니다.

**항목 종류 값을 한 줄에 하나씩 표시하려면**

1. 코드 편집기에서 메시지 작업을 다음 줄로 바꿉니다.

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. 프로젝트 파일을 저장합니다.

3. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>포함, 제외 및 와일드카드

 Include 특성에서 와일드카드 "*", "\*\*" 및 "?"를 사용하여 항목 종류에 항목을 추가할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<Photos Include="images\*.jpeg" />
```

 위의 코드는 *images* 폴더에 있는 파일 확장명이 *.jpeg*인 모든 파일을 Photos 항목 종류에 추가합니다. 반면

```xml
<Photos Include="images\**\*.jpeg" />
```

 위의 코드는 *images* 폴더 및 모든 하위 폴더에 있는 파일 확장명이 *.jpeg*인 모든 파일을 Photos 항목 종류에 추가합니다. 추가 예제는 [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)을 참조하세요.

 선언하는 항목은 항목 종류에 추가됩니다. 예를 들면 다음과 같습니다.

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 위의 코드는 파일 확장명이  ‘.jpeg’ 또는  ‘.gif’인  ‘images’ 폴더의 모든 파일을 포함하는 Photo라는 항목 종류를 만듭니다. 이 코드는 다음 줄과 동일합니다.

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Exclude 특성을 사용하면 항목 종류에서 특정 항목을 제외할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 위의 코드는 이름에 *Designer*라는 문자열이 포함된 파일을 제외하고 파일 확장명이 *.cs*인 모든 파일을 Compile 항목 종류에 추가합니다. 추가 예제는 [방법: 빌드에서 파일 제외](../msbuild/how-to-exclude-files-from-the-build.md)를 참조하세요.

Exclude 특성은 Include 특성과 Exclude 특성을 모두 포함하는 항목 요소에서 Include 특성에 의해 추가된 항목에만 영향을 줍니다. 예를 들면 다음과 같습니다.

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

위의 코드를 실행해도 이전 항목 요소에서 추가된 *Form1.cs* 파일은 제외되지 않습니다.

**항목을 포함 및 제외하려면**

1. 코드 편집기에서 메시지 작업을 다음 줄로 바꿉니다.

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Import 요소 바로 뒤에 다음 항목 그룹을 추가합니다.

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. 프로젝트 파일을 저장합니다.

4. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>항목 메타데이터

 항목은 Include 및 Exclude 특성에서 수집된 정보 외에 메타데이터를 포함할 수 있습니다. 이 메타데이터는 항목 값뿐만이 아니라 항목에 대한 추가 정보를 필요로 하는 작업에서 사용할 수 있습니다.

 메타데이터의 이름을 항목 자식 요소로 사용하여 요소를 만드는 방법으로 프로젝트 파일에서 항목 메타데이터를 선언합니다. 항목은 메타데이터 값을 포함하지 않을 수도 있고 하나 이상 포함할 수도 있습니다. 예를 들어 다음 CSFile 항목에는 값이 "Fr"인 Culture 메타데이터가 있습니다.

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 항목 종류의 메타데이터 값을 가져오려면 다음 구문을 사용합니다. 여기서 ItemType은 항목 종류의 이름이고 MetaDataName은 메타데이터의 이름입니다.

```xml
%(ItemType.MetaDataName)
```

**항목 메타데이터를 검사하려면**

1. 코드 편집기에서 메시지 작업을 다음 줄로 바꿉니다.

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. 프로젝트 파일을 저장합니다.

3. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

위 코드에 나와 있는 것처럼 "Compile.DependentUpon" 구가 여러 번 나타납니다. 대상 내에서 이 구문이 포함된 메타데이터를 사용하면 "일괄 처리"가 수행됩니다. 일괄 처리란 대상 내의 작업이 각각의 고유 메타데이터 값에 대해 한 번씩 실행된다는 의미입니다. 이 코드는 일반적인 "for loop" 프로그래밍 구문과 동일한 MSBuild 스크립트입니다. 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.

### <a name="well-known-metadata"></a>잘 알려진 메타데이터

 항목 목록에 항목을 추가할 때마다 해당 항목에는 몇 가지 잘 알려진 메타데이터가 할당됩니다. 예를 들어 %(Filename)은 모든 항목의 파일 이름을 반환합니다. 잘 알려진 메타데이터의 전체 목록은 [잘 알려진 항목 메타데이터](../msbuild/msbuild-well-known-item-metadata.md)를 참조하세요.

**잘 알려진 메타데이터를 검사하려면**

1. 코드 편집기에서 메시지 작업을 다음 줄로 바꿉니다.

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. 프로젝트 파일을 저장합니다.

3. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

위의 두 예를 비교하면 Compile 항목 종류에서 DependentUpon 메타데이터는 일부 항목에만 포함되어 있지만 잘 알려진 Filename 메타데이터는 모든 항목에 포함되어 있음을 확인할 수 있습니다.

### <a name="metadata-transformations"></a>메타데이터 변환

 항목 목록을 새 항목 목록으로 변환할 수 있습니다. 항목 목록을 변환하려면 다음 구문을 사용합니다. 여기서 \<ItemType>은 항목 종류의 이름이고 \<MetadataName>은 메타데이터의 이름입니다.

```xml
@(ItemType -> '%(MetadataName)')
```

예를 들어 `@(SourceFiles -> '%(Filename).obj')`와 같은 식을 사용하여 소스 파일의 항목 목록을 개체 파일 컬렉션으로 변환할 수 있습니다. 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요.

**메타데이터를 사용하여 항목을 변환하려면**

1. 코드 편집기에서 메시지 작업을 다음 줄로 바꿉니다.

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. 프로젝트 파일을 저장합니다.

3. **명령 창**에서 다음 줄을 입력하고 실행합니다.

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. 출력을 검사합니다. 다음 줄이 표시됩니다.

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

이 구문으로 표현되는 메타데이터로 인해 일괄 처리가 수행되지는 않습니다.

## <a name="next-steps"></a>다음 단계

 간단한 프로젝트 파일을 단계별로 만드는 방법을 알아보려면 [연습: 처음부터 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)를 진행해 보세요.

## <a name="see-also"></a>참조

- [MSBuild 개요](../msbuild/msbuild.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
