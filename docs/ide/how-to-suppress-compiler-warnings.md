---
title: 프로젝트 및 NuGet 패키지에 대한 컴파일러 경고 표시 안 함
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b604f6a1392353d304897a233b74c0d81fc258df
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114502"
---
# <a name="how-to-suppress-compiler-warnings"></a>방법: 컴파일러 경고 표시 안 함

하나 이상 종류의 컴파일러 경고를 필터링하여 빌드 로그를 정리할 수 있습니다. 예를 들어 빌드 로그 세부 정보 표시를 **일반**, **자세히** 또는 **진단**으로 설정할 때 생성되는 출력 중 일부만 검토할 수 있습니다. 세부 정보 표시에 대한 자세한 내용은 [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)을 참조하세요.

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>Visual C# 또는 F\#에 대한 특정 경고 표시 안 함

**빌드** 속성 페이지를 사용하여 C# 및 F# 프로젝트에 대한 특정 경고를 표시하지 않습니다.

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트를 선택합니다.

1. 메뉴 모음에서 **보기** > **속성 페이지**를 선택합니다.

1. **빌드** 페이지를 선택합니다.

1. **경고 표시 안 함** 상자에 표시하지 않으려는 경고의 오류 코드를 세미콜론으로 구분하여 지정합니다.

1. 솔루션을 다시 빌드합니다.

## <a name="suppress-specific-warnings-for-c"></a>C++에 대한 특정 경고 표시 안 함

**구성 속성** 속성 페이지를 사용하여 C++ 프로젝트에 대한 특정 경고를 표시하지 않습니다.

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트 또는 소스 파일을 선택합니다.

1. 메뉴 모음에서 **보기** > **속성 페이지**를 선택합니다.

1. **구성 속성** 범주를 선택하고 **C/C++** 범주를 선택한 다음 **고급** 페이지를 선택합니다.

1. 다음 단계 중 하나를 수행합니다.

    - **특정 경고 사용 안 함** 상자에 표시하지 않으려는 경고의 오류 코드를 세미콜론으로 구분하여 지정합니다.

    - **특정 경고 사용 안 함** 상자에서 **편집**을 선택하여 추가 옵션을 표시합니다.

1. **확인** 단추를 선택한 다음 솔루션을 다시 빌드합니다.

## <a name="suppress-warnings-for-visual-basic"></a>Visual Basic에 대한 경고 표시 안 함

프로젝트의 *.vbproj* 파일을 편집하여 Visual Basic에 대한 특정 컴파일러 경고를 숨길 수 있습니다. *범주*별로 경고를 표시하지 않으려면 [컴파일 속성 페이지](../ide/reference/compile-page-project-designer-visual-basic.md)를 사용합니다. 자세한 내용은 [Visual Basic에서 경고 구성](../ide/configuring-warnings-in-visual-basic.md)을 참조하세요.

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Visual Basic에 대한 특정 경고를 표시하지 않으려면

이 예제는 *.vbproj* 파일을 편집하여 특정 컴파일러 경고를 표시하지 않는 방법을 보여줍니다.

1. **솔루션 탐색기**에서 경고를 표시하지 않으려는 프로젝트를 선택합니다.

1. 메뉴 모음에서 **프로젝트** > **프로젝트 언로드**를 선택합니다.

1. **솔루션 탐색기**에서 프로젝트의 오른쪽 클릭 메뉴 또는 바로 가기 메뉴를 열고 **편집 \< ProjectName>.vbproj**를 선택합니다.

    XML 프로젝트 파일이 코드 편집기에서 열립니다.

1. 빌드 중인 빌드 구성에 대한 `<NoWarn>` 요소를 찾고 하나 이상의 경고 번호를 `<NoWarn>` 요소의 값으로 추가합니다. 여러 경고 번호를 지정하는 경우 쉼표로 구분합니다.

     다음 예제는 두 개의 컴파일러 경고가 표시되지 않는 x86 플랫폼의 *디버그* 빌드 구성에 대한 `<NoWarn>` 요소를 보여줍니다.

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
        <PlatformTarget>x86</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <ErrorReport>prompt</ErrorReport>
        <NoWarn>40059,42024</NoWarn>
        <WarningLevel>1</WarningLevel>
      </PropertyGroup>
    ```

   > [!NOTE]
   > .NET Core 프로젝트는 기본적으로 빌드 구성 속성 그룹을 포함하지 않습니다. .NET Core 프로젝트에서 경고를 표시하지 않으려면 빌드 구성 섹션을 파일에 수동으로 추가합니다. 다음은 그 예입니다.
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. 변경 내용을 *.vbproj* 파일에 저장합니다.

1. 메뉴 모음에서 **프로젝트** > **프로젝트 다시 로드**를 선택합니다.

1. 메뉴 모음에서 **빌드** > **솔루션 다시 빌드**를 선택합니다.

    지정한 경고가 **출력** 창에 더 이상 표시되지 않습니다.

자세한 내용은 Visual Basic 명령줄 컴파일러에 대한 [/nowarn 컴파일러 옵션](/dotnet/visual-basic/reference/command-line-compiler/nowarn)을 참조하세요.

## <a name="suppress-warnings-for-nuget-packages"></a>NuGet 패키지에 대한 경고 표시 안 함

경우에 따라 전체 프로젝트 대신 단일 NuGet 패키지에 대한 NuGet 컴파일러 경고를 표시하지 않을 수 있습니다. 경고는 목적이 있으므로 프로젝트 수준에서 경고를 표시하는 것이 좋습니다. 예를 들어 NuGet 경고 중 하나는 패키지가 프로젝트와 완전히 호환되지 않을 수 있음을 나타냅니다. 프로젝트 수준에서 경고를 표시하지 않고 나중에 다른 NuGet 패키지를 추가하는 경우 호환성 경고가 생성되는지 알 수 없습니다.

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>단일 NuGet 패키지에 대한 특정 경고를 표시하지 않으려면

1. **솔루션 탐색기**에서 컴파일러 경고를 표시하지 않을 NuGet 패키지를 선택합니다.

   ![솔루션 탐색기의 NuGet 패키지](media/nuget-package-with-warning.png)

1. 오른쪽 클릭 메뉴 또는 상황에 맞는 메뉴에서 **속성**을 선택합니다.

1. 패키지 속성의 **NoWarn** 상자에 이 패키지에 대해 표시하지 않을 경고 번호를 입력합니다. 둘 이상의 경고를 표시하지 않으려면 쉼표를 사용하여 경고 번호를 구분합니다.

   ![NuGet 패키지 속성](media/nuget-properties-nowarn.png)

   **솔루션 탐색기** 및 **오류 목록**에서 경고가 사라집니다.

## <a name="see-also"></a>참고 항목

- [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md)
- [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
