---
title: MSBuild가 프로젝트를 빌드하는 방식
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3c1cdc4738f60301435932b3700f14377f12172
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85291013"
---
# <a name="how-msbuild-builds-projects"></a>MSBuild가 프로젝트를 빌드하는 방식

MSBuild는 실제로 어떻게 작동하나요? 이 문서에서는 Visual Studio, 명령줄 또는 스크립트에서 호출된 MSBuild가 프로젝트 파일을 처리하는 방식에 대해 알아봅니다. MSBuild 작동 방식을 알면 문제를 보다 잘 진단하고 빌드 프로세스를 보다 효율적으로 사용자 지정할 수 있습니다. 이 문서는 빌드 프로세스에 대해 설명하며 모든 프로젝트 형식에 대부분 적용됩니다.

전체 빌드 프로세스는 프로젝트를 빌드하는 대상 및 작업의 [초기 시작](#startup), [평가](#evaluation-phase) 및 [실행](#execution-phase)으로 구성됩니다. 이러한 입력 외에도 외부 가져오기가 솔루션 또는 프로젝트 수준에서 *Microsoft.Common.targets* 및 [user-configurable imports](#user-configurable-imports) 같은 두 [표준 가져오기](#standard-imports)를 모두 포함하여 빌드 프로세스의 세부 내용을 정의합니다.

## <a name="startup"></a>Startup 클래스

MSBuild는 Visual Studio에서 *Microsoft.Build.dll*의 MSBuild 개체 모델을 통해 호출하거나 명령줄에서 직접 또는 CI 시스템에서와 같이 스크립트를 통해 실행 파일을 호출하여 호출할 수 있습니다. 두 경우 모두 빌드 프로세스에 영향을 주는 입력에는 프로젝트 파일(또는 Visual Studio 내부 프로젝트 개체), 솔루션 파일, 환경 변수, 명령줄 스위치 또는 동등 개체 모델이 포함됩니다. 시작 단계에서 명령줄 옵션 또는 동등 개체 모델은 로거 구성 등의 MSBuild 설정을 구성하는 데 사용됩니다. 명령줄에서 `-property` 또는 `-p` 스위치를 사용하여 설정된 속성은 프로젝트 파일에 설정된 모든 값을 재정의하는 전역 속성으로 설정되며 나중에 프로젝트 파일을 읽는 경우에도 마찬가지입니다.

다음 섹션에서는 솔루션 파일 또는 프로젝트 파일 등의 입력 파일에 대해 설명합니다.

### <a name="solutions-and-projects"></a>솔루션 및 프로젝트

MSBuild 인스턴스는 한 프로젝트 또는 솔루션의 일부로서 여러 프로젝트로 구성될 수 있습니다. 솔루션 파일은 MSBuild XML 파일이 아니지만 MSBuild는 이 파일을 해석하여 지정된 구성 및 플랫폼 설정에 대해 빌드하는 데 필요한 모든 프로젝트를 인식합니다. MSBuild가 이 XML 입력을 처리하는 것을 솔루션 빌드라고 합니다. 여기에는 모든 솔루션 빌드에서 무언가를 실행할 수 있는 확장 가능 지점이 있습니다. 그러나 이 빌드는 개별 프로젝트 빌드와는 별도의 실행이므로 솔루션 빌드의 속성 설정 또는 대상 정의는 각 프로젝트 빌드와 관련이 없습니다.

솔루션 빌드를 확장하는 방법에 대한 자세한 내용은 [솔루션 빌드 사용자 지정](customize-your-build.md#customize-the-solution-build)에서 확인할 수 있습니다.

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Visual Studio 빌드와 MSBuild.exe 빌드

Visual Studio에서 프로젝트가 빌드되는 경우, MSBuild를 직접 호출하는 경우(MSBuild 실행 파일을 통해) 또는 MSBuild 개체 모델을 사용하여 빌드를 시작하는 경우 사이에는 몇 가지 중요한 차이점이 있습니다. Visual Studio는 Visual Studio 빌드에 대한 프로젝트 빌드 순서를 관리합니다. 개별 프로젝트 수준 에서만 MSBuild를 호출하고, 이 경우 MSBuild의 기능에 큰 영향을 주는 두 가지 부울 속성(`BuildingInsideVisualStudio`, `BuildProjectReferences`)을 설정합니다. 각 프로젝트 내에서 MSBuild를 통해 호출되는 경우와 동일하게 실행이 발생하지만 참조된 프로젝트에서 차이가 발생합니다. MSBuild에서는 참조된 프로젝트가 필요한 경우 빌드가 실제로 발생합니다. 즉, 작업 및 도구를 실행하고 출력을 생성합니다. Visual Studio 빌드가 참조된 프로젝트를 찾으면 MSBuild는 참조된 프로젝트의 예상 출력만 반환합니다. 이를 통해 Visual Studio가 다른 프로젝트의 빌드를 제어할 수 있습니다. Visual Studio는 빌드 순서를 결정하고 필요에 따라 개별적으로 MSBuild를 호출하며, 이 모두를 Visual Studio가 완벽하게 제어합니다.

솔루션 파일을 사용하여 MSBuild를 호출하는 경우 또 다른 차이점이 있습니다. MSBuild가 솔루션 파일을 구문 분석하고, 표준 XML 입력 파일을 만들고, 평가하고, 프로젝트로 실행합니다. 솔루션 빌드는 모든 프로젝트보다 먼저 실행됩니다. Visual Studio에서 빌드할 때는 이러한 상황이 발생하지 않습니다. MSBuild는 솔루션 파일을 인식하지 못합니다. 결과적으로 솔루션 빌드 사용자 지정(*before.SolutionName.sln.targets* 및 *after.SolutionName.sln.targets* 사용)은 Visual Studio 빌드가 아닌 MSbuild.exe 또는 개체 모델 기반에만 적용됩니다.

### <a name="project-sdks"></a>프로젝트 SDK

MSBuild 프로젝트 파일에 대한 SDK 기능은 비교적 새로운 기능입니다. 이러한 변경 전에 프로젝트 파일은 특정 프로젝트 형식에 대한 빌드 프로세스를 정의하는 *.targets* 및 *.props* 파일을 명시적으로 가져왔습니다.

.NET Core 프로젝트는 프로젝트에 적절한 버전의 .NET SDK를 가져옵니다. 개요, [.NET Core 프로젝트 SDK](/dotnet/core/project-sdk/overview), [속성](/dotnet/core/project-sdk/msbuild-props) 참조를 참조하세요.

## <a name="evaluation-phase"></a>평가 단계

이 섹션에서는 이러한 입력 파일을 처리하고 구문 분석하여 빌드할 항목을 결정하는 메모리 내 개체를 생성하는 방법을 설명합니다.

평가 단계의 목적은 입력 XML 파일 및 로컬 환경을 기반으로 메모리에 개체 구조를 만드는 것입니다. 평가 단계는 프로젝트 XML 파일 또는 가져온 XML 파일(기본적으로 속성을 설정하거나 빌드 대상을 정의하는지 여부에 따라 *.props* 또는 *.targets* 파일로 명명됨)과 같은 입력 파일을 처리하는 5개 패스로 구성됩니다. 각 패스는 나중에 프로젝트를 빌드하기 위해 실행 단계에서 사용되는 메모리 내 개체의 일부를 빌드하고, 평가 단계 중에는 실제 빌드 작업이 수행되지 않습니다. 각 패스 내에서 요소는 표시된 순서대로 처리됩니다.

평가 단계의 패스는 다음과 같습니다.

- 환경 변수 평가
- 가져오기 및 속성 평가
- 항목 정의 평가
- 항목 평가
- [UsingTask](usingtask-element-msbuild.md) 요소 평가
- 대상 평가

이러한 패스의 순서는 상당한 영향을 미치므로, 프로젝트 파일을 사용자 지정할 때 이를 알아야 합니다. [속성 및 항목 평가 순서](comparing-properties-and-items.md#property-and-item-evaluation-order)를 참조하세요.

### <a name="evaluate-environment-variables"></a>환경 변수 평가

이 단계에서는 환경 변수를 사용하여 동등한 속성을 설정합니다. 예를 들어 PATH 환경 변수는 `$(PATH)` 속성으로 사용할 수 있습니다. 명령줄 또는 스크립트에서 실행하는 경우 명령 환경이 정상적으로 사용되며, Visual Studio에서 실행하는 경우 Visual Studio가 시작될 때 적용되는 환경이 사용됩니다.

### <a name="evaluate-imports-and-properties"></a>가져오기 및 속성 평가

이 단계에서는 프로젝트 파일 및 전체 가져오기 체인을 포함하여 전체 입력 XML을 읽습니다. MSBuild는 프로젝트 및 모든 가져온 파일의 XML을 나타내는 메모리 내 XML 구조를 만듭니다. 이 시점에서 대상에 없는 속성이 평가되고 설정됩니다.

MSBuild가 해당 프로세스에서 조기에 모든 XML 입력 파일을 읽기 때문에 빌드 프로세스 도중 해당 입력에 대한 변경 내용은 현재 빌드에 영향을 주지 않습니다.

대상 외부 속성은 대상 내부 속성과 다르게 처리됩니다. 이 단계에서는 대상 외부에 정의된 속성만 평가합니다.

속성은 속성 패스에서 순서대로 처리되기 때문에 입력의 특정 지점에 있는 속성은 입력에서 이전에 표시되는 속성 값에 액세스할 수 있지만 나중에 표시되는 속성에는 액세스할 수 없습니다.

항목이 평가되기 전에 속성이 처리되기 때문에 속성 패스 중에는 모든 항목의 값에 액세스할 수 없습니다. 

### <a name="evaluate-item-definitions"></a>항목 정의 평가

이 단계에서는 [항목 정의](item-definitions.md)를 해석하고 이러한 정의에 대한 메모리 내 표현을 만듭니다.

### <a name="evaluate-items"></a>항목 평가

대상 내부에 정의된 항목은 대상 외부의 항목과 다르게 처리됩니다. 이 단계에서는 대상 외부의 항목과 관련 메타데이터를 처리합니다.  항목 정의에서 설정된 메타데이터는 항목에 대한 메타데이터 설정에 의해 재정의됩니다. 항목은 표시되는 순서대로 처리되기 때문에 이전에 정의된 항목을 참조할 수 있지만 나중에 표시되는 항목은 참조할 수 없습니다. 항목 패스는 속성 패스 후에 발생하므로 속성 정의가 나중에 표시되는지 여부에 관계없이 대상 외부에 정의된 경우에는 항목에 액세스할 수 있습니다.

### <a name="evaluate-usingtask-elements"></a>`UsingTask` 요소 평가

이 단계에서는 [UsingTask](usingtask-element-msbuild.md) 요소를 읽고 나중에 실행 단계에서 사용할 수 있도록 작업을 선언합니다.

### <a name="evaluate-targets"></a>대상 평가

이 단계에서는 실행을 준비하기 위해 모든 대상 개체 구조가 메모리에 생성됩니다. 실제 실행은 발생하지 않습니다. 

## <a name="execution-phase"></a>실행 단계

실행 단계에서는 대상을 정렬 및 실행하고 모든 작업을 실행합니다. 그러나 먼저 대상 내부에 정의된 속성 및 항목이 표시되는 순서대로 단일 단계에서 함께 평가됩니다. 처리 순서는 특히 대상에 없는 속성 및 항목을 처리하는 방법과 현저히 다릅니다. 즉, 모든 속성을 먼저 처리한 다음 별도의 패스에서 모든 항목을 처리합니다. 대상 내부의 속성 및 항목에 대한 변경 내용은 해당 변경이 발생한 대상 후에 관찰될 수 있습니다.

### <a name="target-build-order"></a>대상 빌드 순서

단일 프로젝트에서 대상은 순차적으로 실행됩니다. 중요한 문제는 종속성을 사용하여 올바른 순서로 대상을 빌드하도록 모든 항목을 빌드할 순서를 결정하는 방법입니다.  

대상 빌드 순서는 각 대상에서 `BeforeTargets`, `DependsOnTargets` 및 `AfterTargets` 특성을 사용하여 결정됩니다. 이전 대상이 이러한 특성에서 참조되는 속성을 수정하는 경우에는 이전 대상을 실행하는 동안 이후 대상의 순서가 영향을 받을 수 있습니다.

순서 지정 규칙은 [대상 빌드 순서 결정](target-build-order.md#determine-the-target-build-order)에 설명되어 있습니다. 프로세스는 빌드할 대상이 포함된 스택 구조에 의해 결정됩니다. 이 작업의 맨 위에 있는 대상이 실행을 시작하고, 해당 대상이 다른 대상에 종속되는 경우, 이러한 대상이 스택의 맨 위에 푸시되어 실행을 시작합니다.  종속성이 없는 대상은 실행이 완료되고 해당 부모 대상이 다시 시작됩니다.

### <a name="project-references"></a>프로젝트 참조

MSBuild가 수행할 수 있는 두 가지 코드 경로가 있습니다. 하나는 여기 설명된 일반 코드 경로이고 다른 하나는 다음 섹션에서 설명하는 그래프 옵션입니다.

개별 프로젝트는 `ProjectReference` 항목을 통해 다른 프로젝트에 대한 종속성을 지정합니다. 스택의 맨 위에 있는 프로젝트가 빌드를 시작하면 공통 대상 파일에 정의된 표준 대상인 `ResolveProjectReferences` 대상이 실행되는 지점에 도달합니다.

`ResolveProjectReferences`는 출력을 가져오기 위해 `ProjectReference` 항목의 입력을 사용하여 MSBuild 작업을 호출합니다. `ProjectReference` 항목은 `Reference`와 같은 로컬 항목으로 변환됩니다. 실행 단계에서 참조된 프로젝트를 처리하기 시작하는 동안 현재 프로젝트에 대한 MSBuild 실행 단계가 일시 중지됩니다(평가 단계는 필요한 경우 먼저 수행됨). 참조된 프로젝트는 종속 프로젝트 빌드를 시작한 후에만 빌드되며 이로 인해 빌드하는 프로젝트의 트리가 만들어집니다.

Visual Studio에서는 솔루션(.sln) 파일에 프로젝트 종속성을 만들 수 있습니다. 종속성은 솔루션 파일에 지정되며 솔루션을 빌드하거나 Visual Studio 내부에서 빌드할 때만 적용됩니다. 단일 프로젝트를 빌드하는 경우 이 유형의 종속성은 무시됩니다. 솔루션 참조는 MSBuild에서 `ProjectReference` 항목으로 변환된 후 동일한 방식으로 처리됩니다.

### <a name="graph-option"></a>그래프 옵션

그래프 빌드 스위치(`-graphBuild` 또는 `-graph`)를 지정하는 경우 `ProjectReference`는 MSBuild에서 사용하는 최고 수준 개념이 됩니다. MSBuild는 모든 프로젝트를 구문 분석하고 프로젝트의 실제 종속성 그래프인 빌드 순서 그래프를 생성합니다. 그런 다음 빌드 순서를 결정하기 이 그래프가 트래버스됩니다. MSBuild는 개별 프로젝트의 대상과 마찬가지로 참조된 프로젝트가 종속된 프로젝트 이후에 빌드됩니다.

## <a name="parallel-execution"></a>병렬 실행

다중 프로세서 지원(`-maxCpuCount` 또는 `-m` 스위치)을 사용하는 경우 MSBuild는 사용 가능한 CPU 코어를 사용하는 MSBuild 프로세스인 노드를 만듭니다. 각 프로젝트는 사용 가능한 노드로 전송됩니다. 노드 내에서 개별 프로젝트 빌드가 순차적으로 실행됩니다.

MSBuild에서 `$(BuildInParallel)` 속성의 값에 따라 설정되는 부울 변수 <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A>를 설정하여 작업에 병렬 실행을 사용할 수 있습니다. 병렬 실행을 사용하도록 설정된 작업의 경우 작업 스케줄러가 노드를 관리하고 노드에 작업을 할당합니다.

[MSBuild를 사용하여 병렬로 여러 프로젝트 빌드](building-multiple-projects-in-parallel-with-msbuild.md)를 참조하세요.

## <a name="standard-imports"></a>표준 가져오기

*Microsoft.Common.props* 및 *Microsoft.Common.targets*는 모두 .NET 프로젝트 파일이 가져오며(SDK 스타일 프로젝트에서 명시적으로 또는 암시적으로) Visual Studio 설치의 *MSBuild\Current\bin* 폴더에 있습니다. C++ 프로젝트에는 자체 가져오기 계층 구조가 있습니다. [C++ 프로젝트용 MSBuild 내부 항목](/cpp/build/reference/msbuild-visual-cpp-overview)을 참조하세요.

*Microsoft.Common.props* 파일은 사용자가 재정의할 수 있는 기본값을 설정합니다. 이 파일은 프로젝트 파일의 시작 부분에서 (명시적으로 또는 암시적으로) 가져옵니다. 이렇게 하면 프로젝트의 설정이 기본값 이후에 나타나므로 재정의됩니다.

*Microsoft.Common.targets* 파일 및 이 파일이 가져오는 대상 파일은 .NET 프로젝트의 표준 빌드 프로세스를 정의합니다. 또한 빌드를 사용자 지정하는 데 사용할 수 있는 확장 지점도 제공합니다.

구현에서 *Microsoft.Common.targets*는 *Microsoft.Common.CurrentVersion.targets*를 가져오는 씬 래퍼입니다. 이 파일은 표준 속성에 대한 설정을 포함하며, 빌드 프로세스를 정의하는 실제 대상을 정의합니다. `Build` 대상은 여기에서 정의되지만 실제로는 비어 있습니다. 그러나 `Build` 대상은 실제 빌드 단계를 구성하는 개별 대상을 지정하는 `DependsOn` 특성(`BeforeBuild`, `CoreBuild` 및 `AfterBuild`)을 포함합니다. `Build` 대상은 다음과 같이 정의됩니다.

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild` 및 `AfterBuild`는 확장 지점입니다. 이들은 *Microsoft.Common.CurrentVersion.targets* 파일에서 비어 있지만, 프로젝트는 자체 `BeforeBuild` 및 `AfterBuild` 대상에 기본 빌드 프로세스 전후에 수행해야 하는 작업을 제공할 수 있습니다. `AfterBuild`는 no-op 대상인 `Build` 이전에 실행됩니다. `AfterBuild`가 `Build` 대상의 `DependsOn` 특성에 표시되지만 `CoreBuild` 이후에 발생하기 때문입니다.

`CoreBuild` 대상은 다음과 같이 빌드 도구에 대한 호출을 포함합니다.

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

다음 표에서는 이러한 대상에 대해 설명합니다. 일부 대상은 특정 프로젝트 형식에만 적용할 수 있습니다.

| Target | 설명 |
|--------|-------------|
| BuildOnlySettings | Visual Studio가 프로젝트 로드에서 MSBuild를 호출하는 경우가 아닌 실제 빌드에 대한 설정입니다. |
| PrepareForBuild | 빌드를 위한 필수 구성 요소를 준비합니다. |
| PreBuildEvent | 빌드 전에 실행할 작업을 정의하는 프로젝트의 확장 지점입니다. |
| ResolveProjectReferences | 프로젝트 종속성을 분석하고 참조된 프로젝트를 빌드합니다. |
| ResolveAssemblyReferences| 참조된 어셈블리를 찾습니다. |
| ResolveReferences | 모든 종속성을 찾기 위한 `ResolveProjectReferences` 및 `ResolveAssemblyReferences`로 구성됩니다. |
| PrepareResources | 리소스 파일을 처리합니다. |
| ResolveKeySource| 어셈블리에 서명하는 데 사용되는 강력한 이름 키와 [ClickOnce](../deployment/clickonce-security-and-deployment.md) 매니페스트에 서명하는 데 사용되는 인증서를 확인합니다. |
| Compile | 컴파일러를 호출합니다. |
| ExportWindowsMDFile | 컴파일러에 의해 생성된 WinMDModule 파일에서 [WinMD](/uwp/winrt-cref/winmd-files) 파일을 생성합니다. |
| UnmanagedUnregistration | 이전 빌드에서 [COM Interop](/dotnet/standard/native-interop/cominterop) 레지스트리 항목을 제거/정리합니다. |
| GenerateSerializationAssemblies | [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe)를 사용하여 XML serialization 어셈블리를 생성합니다.|
| CreateSatelliteAssemblies | 리소스의 모든 고유 문화권에 대해 하나의 위성 어셈블리를 만듭니다. |
| GenerateManifests | [ClickOnce](../deployment/clickonce-security-and-deployment.md) 애플리케이션과 배포 매니페스트 또는 네이티브 매니페스트를 생성합니다. |
| GetTargetPath | 메타데이터를 사용하여 이 프로젝트에 대한 빌드 제품(실행 파일 또는 어셈블리)이 포함된 항목을 반환합니다. |
| PrepareForRun | 변경된 경우 빌드 출력을 최종 디렉터리에 복사합니다. |
| UnmanagedRegistration | [COM Interop](/dotnet/standard/native-interop/cominterop)에 대한 레지스트리 항목을 설정합니다. |
| IncrementalClean | 이전 빌드에서 생성되었지만 현재 빌드에서 생성되지 않은 파일을 제거합니다. 이 작업은 증분 빌드에서 `Clean` 작업을 수행하는 데 필요합니다. |
| PostBuildEvent | 빌드 후 실행할 작업을 정의하는 프로젝트의 확장 지점입니다. |

위의 표에 나와 있는 대상은 대부분 *Microsoft.CSharp.targets*와 같은 언어별 가져오기에 있습니다. 이 파일은 C# .NET 프로젝트에 고유한 표준 빌드 프로세스의 단계를 정의합니다. 예를 들어 실제로 C# 컴파일러를 호출하는 `Compile` 대상이 포함되어 있습니다.

## <a name="user-configurable-imports"></a>사용자 구성 가능 가져오기

표준 가져오기 외에도 몇 가지 가져오기를 추가하여 빌드 프로세스를 사용자 지정할 수 있습니다.

- *Directory.Build.props*
- *Directory.Build.targets*

이러한 파일은 해당 하위 폴더의 모든 프로젝트에 대한 표준 가져오기에서 읽습니다. 이는 일반적으로 솔루션의 모든 프로젝트를 제어하는 설정에 대한 솔루션 수준이지만 드라이브의 루트까지 파일 시스템에서 더 높은 수준일 수도 있습니다.

*Directory.Build.props* 파일은 *Microsoft.Common.props*가 가져오므로 여기에 정의된 속성은 프로젝트 파일에서 사용할 수 있습니다. 이들 속성을 프로젝트 파일에서 재정의하여 프로젝트 단위로 값을 사용자 지정할 수 있습니다. *Directory.Build.targets* 파일은 프로젝트 파일 이후에 읽습니다. 일반적으로 대상이 포함되지만 여기에서 개별 프로젝트가 다시 정의하지 않게 하려는 속성을 정의할 수도 있습니다.

## <a name="customizations-in-a-project-file"></a>프로젝트 파일의 사용자 지정

Visual Studio는 **솔루션 탐색기**, **속성** 창 또는 **프로젝트 속성**에서 변경하는 경우 프로젝트 파일을 업데이트하지만, 프로젝트 파일을 직접 편집하여 변경할 수도 있습니다.

많은 빌드 동작은 프로젝트 파일에서 프로젝트에 대한 로컬 설정에 대해 MSBuild 속성을 설정하거나 이전 섹션에서 설명한 대로 *Directory.Build.props* 파일을 만들어 프로젝트 및 솔루션의 전체 폴더에 대해 전역적으로 MSBuild 속성을 설정하여 구성할 수 있습니다. 명령줄 또는 스크립트에 대한 임시 빌드의 경우 명령줄에서 `/p` 옵션을 사용하여 MSBuild의 특정 호출에 대한 속성을 설정할 수도 있습니다. 설정할 수 있는 속성에 대한 자세한 내용은 [일반적인 MSBuild 프로젝트 속성](common-msbuild-project-properties.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

MSBuild 프로세스에는 여기에 설명된 것 외에 다른 여러 확장 지점이 있습니다. [빌드 사용자 지정](customize-your-build.md) 및 [방법: Visual Studio 빌드 프로세스 확장](how-to-extend-the-visual-studio-build-process.md)을 참조하세요.

## <a name="see-also"></a>참조

[MSBuild](msbuild.md)