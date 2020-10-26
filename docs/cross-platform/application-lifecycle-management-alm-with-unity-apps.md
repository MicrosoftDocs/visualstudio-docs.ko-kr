---
title: ALM(Application Lifecycle Management) 및 Unity 앱 | Microsoft 문서
description: ALM(애플리케이션 수명 주기 관리) 및 Unity 앱을 이해합니다. Agile 도구, 모델, 코드, 빌드, 테스트를 검토하고 코드 품질을 향상합니다.
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 17cfe2dd0a1ba25eeab6b0bb31ad849303207a02
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039926"
---
# <a name="devops-with-unity-apps"></a>Unity 앱을 사용한 DevOps

최신 플랫폼용 앱을 개발하려면 코드 작성 이외에도 많은 작업을 수행해야 합니다. DevOps(개발+운영)라는 이러한 작업은 앱의 전체 수명 주기에 걸쳐 있으며, 작업 계획 및 추적, 코드 디자인 및 구현, 소스 코드 리포지토리 관리, 빌드 실행, 연속 통합 및 배포 관리, 테스트(단위 테스트 및 UI 테스트 포함), 개발 및 프로덕션 환경에서 다양한 형태의 진단 실행, 원격 분석 및 분석을 통해 실시간으로 앱 성능과 사용자 동작 모니터링하는 작업을 포함합니다.

Visual Studio는 Azure DevOps Services 및 Team Foundation Server와 함께 다양한 DevOps 기능을 제공합니다. 이러한 기능은 특히 스크립트 언어로 C#을 사용하는 경우 Unity&mdash;로 만든 게임 및 몰입형 그래픽 앱을 포함하여 플랫폼 간 프로젝트에 대부분 적용할 수 있습니다. 그러나 Unity에는 자체 개발 환경과 런타임 엔진이 있기 때문에 많은 DevOps 기능은 Visual Studio에 빌드된 다른 종류의 프로젝트에 적용되는 것과 같이 적용되지 않습니다.

다음 표에서는 Unity를 사용할 때 Visual Studio의 DevOps 기능을 적용하거나 적용하지 않는 방법을 식별합니다. 기능 자체에 대한 자세한 내용은 연결된 설명서를 참조하세요.

## <a name="agile-tools"></a>Agile 도구

참조 링크: [Agile 도구 및 Agile 프로젝트 관리 정보](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)(Azure Boards 또는 TFS 사용, Team Explorer Everywhere 포함)

일반 설명: 모든 계획 및 추적 기능은 프로젝트 형식 및 코딩 언어와 독립적입니다.

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|백로그 및 스프린트 관리|yes||
|작업 추적|yes||
|단체 방 협업|yes||
|Kanban 보드|yes||
|보고 및 진행률 시각화|예||

## <a name="modeling"></a>모델링

참조 링크: **[분석 및 모델 아키텍처](../modeling/analyze-and-model-your-architecture.md)**

일반 설명: 이러한 디자인 기능은 코딩 언어에 독립적이거나 C#과 같은 .NET 언어로 작동하지만 개체 계층 구조 및 클래스 관계를 포함하는 기존 애플리케이션 패러다임에서 작동합니다. Unity 내에서 게임을 디자인하는 경우 완전히 다른 패러다임, 즉 그래픽 개체, 소리, 셰이더, 스크립트 등의 관계가 필요합니다. 이러한 이유로 Visual Studio 모델링 다이어그램 도구는 Unity 프로젝트 전체와 특별한 관련이 없습니다. C# 스크립트 내에서 관계를 관리하는 데 사용될 수 있지만 전체의 일부일 뿐입니다.

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|시퀀스 다이어그램|예||
|종속성 그래프|예||
|호출 계층 구조|예||
|클래스 디자이너|예||
|아키텍처 탐색기|예||
|UML 다이어그램(사용 사례, 활동, 클래스, 구성 요소, 시퀀스 및 DSL)|예||
|레이어 다이어그램|예||
|레이어 유효성 검사|예||

## <a name="code"></a>코드

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|[TFVC(Team Foundation 버전 제어)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true) 또는 Azure Repos 사용|예|Unity 프로젝트는 단순히 다른 프로젝트와 마찬가지로 버전 제어 시스템에 배치할 수 있는 파일 모음이지만, 특별히 고려해야 하는 몇 가지 사항을 뒤에서 설명합니다.|
|[Azure Repos에서 Git 시작하기](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio&preserve-view=true)|예|표 뒤에 나오는 설명을 참조하세요.|
|[코드 품질 향상](../test/improve-code-quality.md)|yes||
|[코드 변경 내용 및 기타 기록 찾기](../ide/find-code-changes-and-other-history-with-codelens.md)|yes||
|[코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)|예||

Unity로 버전 제어를 수행하기 위한 특별 고려 사항:

1. Unity는 기본적으로 숨겨져 있는 불투명 단일 라이브러리에서 게임 자산 메타데이터를 추적합니다. 파일 및 메타데이터를 동기화된 상태로 유지하려면 메타데이터를 표시하고 더 관리하기 쉬운 청크로 저장해야 합니다. 자세한 내용은 [Unity와 함께 외부 버전 제어 시스템 사용](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html)(Unity 설명서)을 참조하세요.

2. Unity 프로젝트의 일부 파일 및 폴더는 위의 링크에 설명된 것처럼 소스 제어에 적합하지 않습니다. Assets 및 ProjectSettings 폴더는 추가해야 하고 Library 및 Temp 폴더는 추가하면 안 됩니다. 소스 제어로 이동하지 않는 생성된 파일의 추가 목록에 대해서는 StackOverflow의 [Unity3D 소스 제어에 Git을 사용하는 방법](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control)을 참조하세요. 독립적으로 이 주제에 대한 블로그 게시물을 올린 개발자도 많습니다.

3. 질감 또는 오디오 파일과 같은 Unity 프로젝트의 이진 자산은 많은 스토리지 공간을 차지할 수 있습니다. Git와 같은 다양한 소스 제어 시스템은 변경 내용이 파일의 일부에만 영향을 주는 경우에도 변경될 때마다 파일의 고유 복사본을 저장합니다. 이로 인해 Git 리포지토리가 너무 커질 수 있습니다. 이 문제를 해결하기 위해 대개 Unity 개발자는 최종 자산만 리포지토리에 추가하고 OneDrive, DropBox, git-annex 등의 다른 방법으로 자산의 작업 기록을 유지합니다. 일반적으로 이러한 자산은 소스 코드 변경에 따라 버전을 관리할 필요가 없으므로 이 접근 방식은 유용합니다. 또한 개발자는 일반적으로 프로젝트 편집기의 Asset Serialization Mode를 Force Text로 설정하여 이진 형식이 아니라 텍스트에 장면 파일을 저장하므로 소스 제어에서 병합할 수 있습니다. 자세한 내용은 [편집기 설정](https://docs.unity3d.com/Manual/class-EditorManager.html)(Unity 설명서)을 참조하세요.

## <a name="build"></a>빌드

참조 링크: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|온-프레미스 TFS(Team Foundation Server)|가능|Unity 프로젝트는 Visual Studio 빌드 시스템이 아니라 Unity 환경을 통해 빌드됩니다(Visual Studio Tools for Unity 내에서 빌드하면 스크립트가 컴파일되지만 실행 파일은 생성되지 않음). [명령줄에서 Unity 프로젝트를 빌드](https://docs.unity3d.com/Manual/CommandLineArguments.html)(Unity 설명서)할 수 있으므로 Unity 자체가 해당 컴퓨터에 설치되어 있는 경우 적절한 Unity 명령을 실행하도록 TFS 서버의 MSBuild 프로세스를 구성할 수 있습니다.<br /><br /> 또한 Unity는 Git 또는 SVN 리포지토리를 모니터링하고 정기적 빌드를 실행하는 [Unity 클라우드 빌드](https://build.cloud.unity3d.com/landing/)를 제공합니다. 현재는 TFVC 또는 Azure DevOps Services에서 작동하지 않습니다.|
|Azure DevOps Services에 연결된 온-프레미스 빌드 서버|가능|위와 동일한 조건에서 Azure DevOps Services를 통해 트리거된 빌드가 온-프레미스 TFS 컴퓨터를 사용하도록 추가로 지정할 수 있습니다. 지침은 [에이전트 빌드 및 릴리스](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true)를 참조하세요.|
|Azure DevOps Services의 호스트된 컨트롤러 서비스|아니요|Unity 빌드는 현재 지원되지 않습니다.|
|사전 및 사후 스크립트로 정의 작성|예|사전 및 사후 빌드 스크립트에 대해 Unity 명령줄을 사용하여 빌드를 실행하는 사용자 지정 빌드 정의를 구성할 수도 있습니다.|
|제어된 체크 인을 포함하는 연속 통합|예|Git는 체크 인이 아니라 끌어오기 요청 모델로 작동하므로 TFVC에 대한 제어된 체크 인에만 해당|

## <a name="test"></a>테스트

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|테스트 계획, 테스트 사례 만들기 및 테스트 도구 모음 구성|yes||
|수동 테스트|예||
|테스트 관리자(테스트 기록 및 재생)|Windows 디바이스 및 Android 에뮬레이터에만 해당||
|코드 검사|해당 없음|Visual Studio가 아니라 Unity 내에서 단위 테스트가 발생하는 경우에는 해당하지 않습니다. 아래를 참조하세요.|
|[코드 단위 테스트](../test/unit-test-your-code.md)|Visual Studio가 아니라 Unity 내에서 발생|Unity는 [Unity 테스트 도구](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802)(Unity Asset Store)의 일부로 자체 단위 테스트 프레임워크를 제공합니다. 단위 테스트 결과는 Unity 내에서 보고되고 Visual Studio 내에 표시되지 않습니다.|
|[UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)|아니요|코딩된 UI 테스트는 앱 UI의 읽을 수 있는 컨트롤을 사용합니다. Unity 앱은 본질적으로 그래픽이므로 코딩된 UI 테스트 도구에서 콘텐츠를 읽을 수 없습니다.|

## <a name="improve-code-quality"></a>코드 품질 향상

참조 링크: **[코드 품질 향상](../test/improve-code-quality.md)**

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|[관리 코드 품질 분석](../code-quality/code-analysis-for-managed-code-overview.md)|예|Visual Studio 내에서 C# 스크립트 코드를 분석할 수 있습니다.|
|[코드 복제본 검색을 사용하여 중복 코드 찾기](/previous-versions/hh205279(v=vs.140))|예|Visual Studio 내에서 C# 스크립트 코드를 분석할 수 있습니다.|
|[관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/code-metrics-values.md)|예|Visual Studio 내에서 C# 스크립트 코드를 분석할 수 있습니다.|
|[성능 도구](../profiling/performance-explorer.md)|아니요|[Unity 프로파일러](https://docs.unity3d.com/Manual/Profiler.html)(Unity 웹 사이트)를 사용합니다.|
|[.NET Framework 메모리 문제 분석](../vs-2015/misc/analyze-dotnet-framework-memory-issues.md)|아니요|Visual Studio 도구에는 프로파일링을 위한 모노 프레임워크(Unity에서 사용)에 대한 후크가 없습니다. [Unity 프로파일러](http://docs.unity3d.com/Manual/Profiler.html)(Unity 설명서)를 사용합니다.|

## <a name="release-management"></a>릴리스 관리

참조 링크: [Azure Pipelines 및 TFS에서 빌드 및 릴리스](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|릴리스 프로세스 관리|yes||
|스크립트를 통한 테스트용 로드를 위해 서버에 배포|예||
|앱 스토어에 업로드|Partial|일부 앱 스토어의 경우 이 프로세스를 자동화할 수 있는 확장을 사용할 수 있습니다. [Azure DevOps Services용 확장](https://marketplace.visualstudio.com/VSTS)(예: [Google Play용 확장](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play))을 참조하세요.|

## <a name="monitor-with-hockeyapp"></a>HockeyApp으로 모니터링

참조 링크: **[HockeyApp으로 모니터링](https://www.hockeyapp.net/features/)**

|기능|Unity에서 지원 여부|추가 설명|
|-------------|--------------------------|-------------------------|
|충돌 분석, 원격 분석 및 베타 분포|예|HockeyApp은 주로 베타 분포를 처리하고 충돌 보고서를 얻는 데 유용합니다.<br /><br /> C# 스크립트에서의 원격 분석에서는 Unity가 사용하는 .NET 버전에서 실행되기만 하면 모든 분석 프레임워크를 사용할 수 있습니다. 그러나 게임 스크립트 내에서만 분석할 수 있고 Unity 엔진 내에서 보다 자세히 분석할 수는 없습니다. 현재 Application Insights에 대한 플러그 인은 없지만, [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) 및 [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity) 등 기타 분석 솔루션에 대한 플러그 인은 사용 가능합니다. 물론 Unity 프로젝트의 특성을 이해하는 Unity 분석 등의 서비스가 일반 프레임워크보다 훨씬 더 의미 있는 분석을 제공합니다.|