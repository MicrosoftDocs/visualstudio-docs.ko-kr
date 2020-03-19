---
title: '방법: 플랫폼을 대상으로 한 프로젝트 구성'
ms.date: 08/16/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cbe4bc3f982ae18b9f85fe8bf5c21495c98beee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76112544"
---
# <a name="how-to-configure-projects-to-target-platforms"></a>방법: 플랫폼을 대상으로 한 프로젝트 구성

Visual Studio를 사용하면 64비트 플랫폼을 비롯하여 다양한 플랫폼을 대상으로 하는 애플리케이션을 설정할 수 있습니다. Visual Studio의 64비트 플랫폼 지원에 대한 자세한 내용은 [64비트 애플리케이션](/dotnet/framework/64-bit-apps)을 참조하세요.

## <a name="target-platforms-with-the-configuration-manager"></a>구성 관리자에서 대상 플랫폼 지정

**구성 관리자**는 프로젝트의 대상이 될 새 플랫폼을 신속하게 추가할 수 있는 방법을 제공합니다. Visual Studio에 포함되어 있는 플랫폼 중 하나를 선택하면 프로젝트의 속성이 선택된 플랫폼에 맞는 프로젝트를 빌드하도록 수정됩니다.

### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>64비트 플랫폼을 대상으로 하는 프로젝트를 구성하려면

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다.

2. **활성 솔루션 플랫폼** 목록에서 대상으로 지정할 솔루션으로 64비트 플랫폼을 선택한 다음 **닫기** 단추를 선택합니다.

    1. **활성 솔루션 플랫폼** 목록에 원하는 플랫폼이 없는 경우 **새로 만들기**를 선택합니다.

         **새 솔루션 플랫폼** 대화 상자가 나타납니다.

    2. **새 플랫폼 입력 또는 선택** 목록에서 **x64**를 선택합니다.

        > [!NOTE]
        > 구성의 새 이름을 지정한 경우 **프로젝트 디자이너**에서 설정을 수정하여 올바른 플랫폼을 대상으로 지정해야 합니다.

    3. 현재 플랫폼 구성에서 설정을 복사하려면 해당 설정을 선택한 다음 **확인** 단추를 선택합니다.

64비트 플랫폼을 대상으로 하는 모든 프로젝트의 속성이 업데이트되고 프로젝트의 다음 빌드가 64비트 플랫폼에 최적화됩니다.

## <a name="target-platforms-in-the-project-designer"></a>프로젝트 디자이너에서 대상 플랫폼 지정

**프로젝트 디자이너**에서도 프로젝트에 대해 여러 플랫폼을 대상으로 지정하는 방법을 제공합니다. 사용자의 솔루션에 대해 **새 솔루션 플랫폼** 대화 상자의 목록에 있는 플랫폼 중 하나를 선택할 수 없는 경우, 사용자 지정 구성 이름을 만들고 **프로젝트 디자이너**에서 원하는 플랫폼을 대상으로 하도록 설정을 수정할 수 있습니다.

사용하고 있는 프로그래밍 언어에 따라 이 작업이 다르게 수행됩니다. 자세한 내용은 다음 링크를 참조하세요.

- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 프로젝트의 경우 [/platform(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)을 참조하세요.

- [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 프로젝트의 경우 [빌드 페이지, 프로젝트 디자이너(C#)](../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

- [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 프로젝트의 경우 [/clr(공용 언어 런타임 컴파일)](/cpp/build/reference/clr-common-language-runtime-compilation)을 참조하세요.

## <a name="manually-editing-the-project-file"></a>수동으로 프로젝트 파일 편집

일부 사용자 지정 구성에 대한 프로젝트 파일을 수동으로 편집해야 하는 경우가 있습니다. 예를 들어 다음 예제와 같이 두 가지 플랫폼에 대해 서로 다른 참조와 같이 IDE에서 조건을 지정할 수 없는 경우를 들 수 있습니다.

### <a name="example-referencing-x86-and-x64-assemblies-and-dlls"></a>예: x86 및 x64 어셈블리 및 DLL 참조

x86 및 x64 버전이 모두 포함된 .NET 어셈블리 또는 DLL이 있을 수 있습니다. 이러한 참조를 사용하도록 프로젝트를 설정하려면 먼저 참조를 추가한 다음 프로젝트 파일을 열고 편집하여 구성 및 대상 플랫폼을 모두 참조하는 조건을 포함하는 `ItemGroup`을 추가합니다.  예를 들어 참조하는 이진이 ClassLibrary1이고 디버그 및 릴리스 구성에 대한 경로와 x86 및 x64 버전이 서로 다른 경우를 가정합니다.  그러면 다음과 같이 모든 설정 조합이 포함된 네 개의 `ItemGroup` 요소를 사용합니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <Platforms>AnyCPU;x64;x86</Platforms>
  </PropertyGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x64'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x64\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>

  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Debug\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
  
  <ItemGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|x86'">
    <Reference Include="ClassLibrary1">
      <HintPath>..\..\ClassLibrary1\ClassLibrary1\bin\x86\Release\netstandard2.0\ClassLibrary1.dll</HintPath>
    </Reference>
  </ItemGroup>
</Project>
```

::: moniker range="vs-2017"
> [!NOTE]
> Visual Studio 2017에서 프로젝트 파일을 편집하려면 먼저 프로젝트를 언로드해야 합니다. 프로젝트를 언로드하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택합니다. 편집을 완료한 후 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 다시 로드**를 선택하여 변경 내용을 저장하고 프로젝트를 다시 로드합니다.
::: moniker-end

프로젝트 파일에 대한 자세한 내용은 [MSBuild 프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)를 참조하세요.

## <a name="see-also"></a>참조

- [빌드 플랫폼 이해](../ide/understanding-build-platforms.md)
- [/platform(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)
- [64비트 애플리케이션](/dotnet/framework/64-bit-apps)
- [Visual Studio IDE 64비트 지원](../ide/visual-studio-ide-64-bit-support.md)
- [프로젝트 파일 이해](/aspnet/web-forms/overview/deployment/web-deployment-in-the-enterprise/understanding-the-project-file)
