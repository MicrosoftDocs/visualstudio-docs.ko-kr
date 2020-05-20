---
title: '연습: 처음부터 새로 MSBuild 프로젝트 파일 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe9f052c10f31c4db0f8bf09f273be5814ff732
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263138"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>연습: 처음부터 새로 MSBuild 프로젝트 파일 만들기

.NET Framework를 대상으로 하는 프로그래밍 언어는 MSBuild 프로젝트 파일을 사용하여 애플리케이션 빌드 프로세스를 설명하고 제어합니다. Visual Studio를 사용하여 MSBuild 프로젝트 파일을 만들 때 적절한 XML이 파일에 자동으로 추가됩니다. 그러나 XML이 구성되는 방식과 이러한 방식을 변경하여 빌드를 제어할 수 있는 방법을 이해하는 것이 좋습니다.

 C++ 프로젝트용 프로젝트 파일을 만드는 방법에 대한 자세한 내용은 [MSBuild(C++)](/cpp/build/msbuild-visual-cpp)를 참조하세요.

 이 연습에서는 텍스트 편집기만을 사용하여 기본 프로젝트 파일을 증분 방식으로 만드는 방법을 보여 줍니다. 이 연습에서는 다음과 같은 단계를 따릅니다.

1. 최소 애플리케이션 소스 파일을 만듭니다.

2. 최소 MSBuild 프로젝트 파일을 만듭니다.

3. MSBuild를 포함하도록 PATH 환경 변수를 확장합니다.

4. 프로젝트 파일을 사용하여 애플리케이션을 빌드합니다.

5. 빌드를 제어하기 위한 속성을 추가합니다.

6. 속성 값을 변경하여 빌드를 제어합니다.

7. 빌드에 대상을 추가합니다.

8. 대상을 지정하여 빌드를 제어합니다.

9. 증분 방식으로 빌드합니다.

이 연습에서는 명령 프롬프트에서 프로젝트를 빌드하고 결과를 검토하는 방법을 보여 줍니다. MSBuild 및 명령 프롬프트에서 MSBuild를 실행하는 방법에 대한 자세한 내용은 [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md)을 참조하세요.

연습을 완료하려면 .NET Framework(버전 2.0, 3.5, 4.0, 4.5 또는 그 이상)가 설치되어 있어야 합니다. .NET Framework에 연습에 필요한 MSBuild 및 Visual C# 컴파일러가 포함되어 있기 때문입니다.

## <a name="create-a-minimal-application"></a>최소 애플리케이션 만들기

 이 섹션에서는 텍스트 편집기를 사용하여 최소 C# 애플리케이션 소스 파일을 만드는 방법을 보여 줍니다.

1. 명령 프롬프트에서 애플리케이션을 만들려는 폴더로 이동합니다(예: ‘\내 문서\\’ 또는 ‘\바탕 화면\\’).

2. **md HelloWorld**를 입력하여 *\HelloWorld\\* 라는 하위 폴더를 만듭니다.

3. **cd HelloWorld**를 입력하여 새 폴더로 변경합니다.

4. 메모장이나 다른 텍스트 편집기를 시작한 후 다음 코드를 입력합니다.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. 이 소스 코드 파일을 저장하고 이름을 *Helloworld.cs*로 지정합니다.

6. 명령 프롬프트에서 **csc helloworld.cs**를 입력하여 애플리케이션을 빌드합니다.

7. 명령 프롬프트에서 **helloworld**를 입력하여 애플리케이션을 테스트합니다.

     **Hello, world!** 메시지가 표시됩니다.

8. 명령 프롬프트에서 **del helloworld.exe**를 입력하여 애플리케이션을 삭제합니다.

## <a name="create-a-minimal-msbuild-project-file"></a>최소 MSBuild 프로젝트 파일 만들기

 최소 애플리케이션 소스 파일이 있으므로 이제 최소 프로젝트 파일을 만들어 애플리케이션을 빌드할 수 있습니다. 이 프로젝트 파일에는 다음 요소가 포함되어 있습니다.

- 필수 루트 `Project` 노드

- 항목 요소를 포함할 `ItemGroup` 노드

- 애플리케이션 소스 파일을 참조하는 항목 요소

- 애플리케이션을 빌드하는 데 필요한 작업을 포함할 `Target` 노드

- 애플리케이션을 빌드하기 위해 Visual C# 컴파일러를 시작하는 `Task` 요소

### <a name="to-create-a-minimal-msbuild-project-file"></a>최소 MSBuild 프로젝트 파일을 만들려면

1. 텍스트 편집기에서 기존 텍스트를 다음 두 줄을 사용하여 바꿉니다.

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. 이 `ItemGroup` 노드를 `Project` 노드의 자식 요소로 삽입합니다.

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     이 `ItemGroup`은 이미 항목 요소를 포함하고 있습니다.

3. `Target` 노드를 `Project` 노드의 자식 요소로 추가합니다. 노드의 이름을 `Build`로 지정합니다.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. 이 작업 요소를 `Target` 노드의 자식 요소로 삽입합니다.

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. 이 프로젝트 파일을 저장하고 이름을 *Helloworld.csproj*로 지정합니다.

최소 프로젝트 파일은 다음 코드와 유사합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Build 대상의 작업은 순차적으로 실행됩니다. 이 경우 Visual C# 컴파일러 `Csc` 작업이 유일한 작업입니다. 이 작업에는 컴파일할 소스 파일 목록이 필요하며, 이는 `Compile` 항목 값으로 제공됩니다. `Compile` 항목은 하나의 소스 파일 *Helloworld.cs*만 참조합니다.

> [!NOTE]
> 다음과 같이 항목 요소에 별표 와일드카드 문자(\*)를 사용하여 파일 이름 확장명이 *.cs*인 모든 파일을 참조할 수 있습니다.
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="extend-the-path-to-include-msbuild"></a>MSBuild를 포함하도록 경로 확장

MSBuild에 액세스하려면 먼저 .NET Framework 폴더를 포함하도록 PATH 환경 변수를 확장해야 합니다.

Visual Studio 2013부터 MSBuild 폴더(32비트 운영 체제의 경우 *%ProgramFiles%\MSBuild* 또는 64비트 운영 체제의 경우 *%ProgramFiles(x86)%\MSBuild*)에서 *MSBuild.exe*를 찾을 수 있습니다.

명령 프롬프트에 **set PATH=%PATH%;%ProgramFiles%\MSBuild** 또는 **set PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**를 입력합니다.

또는 Visual Studio가 설치되어 있는 경우 *MSBuild* 폴더를 포함하는 경로가 있는 **Visual Studio용 개발자 명령 프롬프트**를 사용할 수 있습니다.

## <a name="build-the-application"></a>애플리케이션 빌드

 이제 애플리케이션을 빌드하기 위해 방금 만든 프로젝트 파일을 사용합니다.

1. 명령 프롬프트에 **msbuild helloworld.csproj -t:Build**를 입력합니다.

     그러면 Helloworld 애플리케이션을 만들기 위해 Visual C# 컴파일러를 호출하여 Helloworld 프로젝트 파일의 Build 대상이 빌드됩니다.

2. **helloworld**를 입력하여 애플리케이션을 테스트합니다.

     **Hello, world!** 메시지가 표시됩니다.

> [!NOTE]
> 자세한 정도를 높여 빌드에 대한 자세한 정보를 볼 수 있습니다. 세부 정보 표시 수준을 “자세히”로 설정하려면 명령 프롬프트에서 다음 명령 중 하나를 입력합니다.
>
> **msbuild helloworld.csproj -t:Build -verbosity:detailed**

## <a name="add-build-properties"></a>빌드 속성 추가

 프로젝트 파일에 빌드 속성을 추가하여 빌드에 대한 제어를 강화할 수 있습니다. 이제 다음 속성을 추가합니다.

- 애플리케이션의 이름을 지정하기 위한 `AssemblyName` 속성

- 애플리케이션을 포함할 폴더를 지정하기 위한 `OutputPath` 속성

### <a name="to-add-build-properties"></a>빌드 속성을 추가하려면

1. 명령 프롬프트에서 **del helloworld.exe**를 입력하여 기존 애플리케이션을 삭제합니다.

2. 프로젝트 파일에서 여는 `PropertyGroup` 요소 바로 뒤에 이 `Project` 요소를 삽입합니다.

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. 이 작업을 `Csc` 작업 바로 앞의 Build 대상에 추가합니다.

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir` 작업이 `OutputPath` 속성에 의해 이름이 지정된 폴더를 만듭니다(현재 해당 이름의 폴더가 없는 경우).

4. 이 `OutputAssembly` 특성을 `Csc` 작업에 추가합니다.

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     그러면 `AssemblyName` 속성에 의해 이름이 지정된 어셈블리를 생성하여 `OutputPath` 속성에 의해 이름이 지정된 폴더에 배치하라는 지시가 Visual C# 컴파일러에 전달됩니다.

5. 변경 내용을 저장합니다.

이제 프로젝트 파일은 다음 코드와 유사합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> `OutputPath` 요소에 백슬래시(\\) 경로 구분 기호를 지정할 때는 `Csc` 작업의 `OutputAssembly` 특성에 해당 기호를 추가하는 대신 폴더 이름의 끝에 기호를 추가하는 것이 좋습니다. 따라서
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> 가 아래보다 좋습니다.
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>빌드 속성 테스트

 이제 출력 폴더 및 애플리케이션 이름을 지정하기 위해 빌드 속성을 사용한 프로젝트 파일을 사용하여 애플리케이션을 빌드할 수 있습니다.

1. 명령 프롬프트에 **msbuild helloworld.csproj -t:Build**를 입력합니다.

     그러면 *\Bin\\* 폴더가 만들어진 다음, Visual C# 컴파일러가 호출되어 *MSBuildSample* 애플리케이션이 만들어져 *\Bin\\* 폴더에 배치됩니다.

2. *\Bin\\* 폴더가 만들어져 *MSBuildSample* 애플리케이션을 포함하고 있는지 확인하려면 **dir Bin**을 입력합니다.

3. **Bin\MSBuildSample**을 입력하여 애플리케이션을 테스트합니다.

     **Hello, world!** 메시지가 표시됩니다.

## <a name="add-build-targets"></a>빌드 대상 추가

 이제 다음과 같이 프로젝트 파일에 대상을 두 개 더 추가합니다.

- 이전 파일을 삭제하는 Clean 대상

- `DependsOnTargets` 특성을 사용하여 Clean 작업이 Build 작업보다 먼저 실행되도록 하는 Rebuild 대상

대상이 여러 개이므로 이제 Build 대상을 기본 대상으로 설정할 수 있습니다.

### <a name="to-add-build-targets"></a>빌드 대상을 추가하려면

1. 프로젝트 파일에서 이러한 두 대상을 Build 대상 바로 뒤에 추가합니다.

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Clean 대상은 Delete 작업을 호출하여 애플리케이션을 삭제합니다. Rebuild 대상은 Clean 대상과 Build 대상이 둘 다 실행될 때까지 실행되지 않습니다. Rebuild 대상에 작업이 없더라도 Rebuild 대상은 Clean 대상이 Build 대상보다 먼저 실행되도록 합니다.

2. 이 `DefaultTargets` 특성을 여는 `Project` 요소에 추가합니다.

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     그러면 Build 대상이 기본 대상으로 설정됩니다.

이제 프로젝트 파일은 다음 코드와 유사합니다.

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>빌드 대상 테스트

 새 빌드 대상을 실행하여 프로젝트 파일의 이러한 기능을 테스트할 수 있습니다.

- 기본 빌드를 바인딩합니다.

- 명령 프롬프트에서 애플리케이션 이름을 설정합니다.

- 다른 애플리케이션이 빌드되기 전에 애플리케이션을 삭제합니다.

- 다른 애플리케이션을 빌드하지 않고 애플리케이션을 삭제합니다.

### <a name="to-test-the-build-targets"></a>빌드 대상을 테스트하려면

1. 명령 프롬프트에 **msbuild helloworld.csproj -p:AssemblyName=Greetings**를 입력합니다.

     **-t** 스위치를 사용하여 대상을 명시적으로 설정하지 않았으므로 MSBuild가 기본 Build 대상을 실행합니다. **-p** 스위치는 `AssemblyName` 속성을 재정의하고 이 속성에 새 값 `Greetings`를 제공합니다. 따라서 새 애플리케이션 *Greetings.exe*가 *\Bin\\* 폴더에 만들어집니다.

2. *\Bin\\* 폴더에 *MSBuildSample* 애플리케이션과 새 *Greetings* 애플리케이션이 둘 다 포함되어 있는지 확인하려면 **dir Bin**을 입력합니다.

3. **Bin\Greetings**를 입력하여 Greetings 애플리케이션을 테스트합니다.

     **Hello, world!** 메시지가 표시됩니다.

4. **msbuild helloworld.csproj -t:clean**을 입력하여 MSBuildSample 애플리케이션을 삭제합니다.

     그러면 Clean 작업이 실행되어 기본 `AssemblyName` 속성값 `MSBuildSample`이 포함되어 있는 애플리케이션이 제거됩니다.

5. **msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings**를 입력하여 Greetings 애플리케이션을 삭제합니다.

     그러면 Clean 작업이 실행되어 지정된 **AssemblyName** 속성값 `Greetings`가 포함되어 있는 애플리케이션이 제거됩니다.

6. 이제 *\Bin\\* 폴더가 비어 있는지 확인하려면 **dir Bin**을 입력합니다.

7. **msbuild**를 입력합니다.

     프로젝트 파일이 지정되어 있지 않더라도 현재 폴더에 프로젝트 파일이 하나뿐이므로 MSBuild는 *helloworld.csproj* 파일을 빌드합니다. 따라서 *MSBuildSample* 애플리케이션이 *\Bin\\* 폴더에 만들어집니다.

     *\Bin\\* 폴더에 *MSBuildSample* 애플리케이션이 포함되어 있는지 확인하려면 **dir Bin**을 입력합니다.

## <a name="build-incrementally"></a>증분 방식으로 빌드

 대상이 의존하는 소스 파일 또는 대상 파일이 변경된 경우에만 대상을 빌드하라고 MSBuild에 지시할 수 있습니다. MSBuild는 파일의 타임스탬프를 사용하여 파일이 변경되었는지 여부를 확인합니다.

### <a name="to-build-incrementally"></a>증분 방식으로 빌드하려면

1. 프로젝트 파일에서 다음 특성을 여는 Build 대상에 추가합니다.

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     그러면 Build 대상이 `Compile` 항목 그룹에 지정된 입력 파일에 의존하고, 출력 대상이 애플리케이션 파일이도록 지정됩니다.

     결과 Build 대상은 다음 코드와 유사합니다.

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. 명령 프롬프트에서 **msbuild -v:d**를 입력하여 Build 대상을 테스트합니다.

     *helloworld.csproj*는 기본 프로젝트 파일이고, 해당 Build는 기본 대상이라는 사실을 기억하세요.

     **-v:d** 스위치는 빌드 프로세스에 대한 자세한 설명을 지정합니다.

     다음과 같은 줄이 표시됩니다.

     **해당 입력 파일과 비교하여 출력 파일이 모두 최신 파일이므로 "Build" 대상을 건너뜁니다.**

     **입력 파일: HelloWorld.cs**

     **출력 파일: BinMSBuildSample.exe**

     MSBuild는 애플리케이션이 마지막으로 빌드된 이후로 변경된 소스 파일이 없으므로 Build 대상을 건너뜁니다.

## <a name="c-example"></a>C# 예제

다음 예제에서는 C# 애플리케이션을 컴파일하고 출력 파일 이름이 포함된 메시지를 기록하는 프로젝트 파일을 보여 줍니다.

### <a name="code"></a>코드

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Visual Basic 예제

다음 예제에서는 Visual Basic 애플리케이션을 컴파일하고 출력 파일 이름이 포함된 메시지를 기록하는 프로젝트 파일을 보여 줍니다.

### <a name="code"></a>코드

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>다음 단계

 Visual Studio는 이 연습에 표시된 작업의 많은 부분을 자동으로 수행할 수 있습니다. Visual Studio를 사용하여 MSBuild 프로젝트 파일을 만들고, 편집하고, 빌드하고, 테스트하는 방법에 대한 자세한 내용은 [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [MSBuild 개요](../msbuild/msbuild.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
