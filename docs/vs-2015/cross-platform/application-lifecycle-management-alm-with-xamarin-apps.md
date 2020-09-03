---
title: ALM(Application Lifecycle Management) 및 Xamarin 앱 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 37c855f7940cbed847dcb7d5c6414be436cee993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918369"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>ALM(Application Lifecycle Management) 및 Xamarin 앱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin을 통해 C#, .NET 및 Visual Studio를 사용하여 Android, iOS 및 Windows를 대상으로 하는 플랫폼 간 모바일 앱을 빌드할 수 있습니다. Xamarin을 통해 많은 양의 코드를 플랫폼 간에 공유할 수 있으므로 일부 코드만 플랫폼별로 작성하면 됩니다. Xamarin 자체에 대한 자세한 내용은 [Visual Studio 및 Xamarin](../cross-platform/visual-studio-and-xamarin.md)을 참조하세요.  
  
 최신 플랫폼용 앱을 개발하려면 코드 작성 이외에도 많은 작업을 수행해야 합니다. DevOps(개발+운영)라는 이러한 활동은 앱의 전체 수명 주기에 걸쳐 있으며 민첩한 작업 계획 및 추적, 코드 디자인 및 구현, 소스 코드 리포지토리 관리, 빌드 실행, 연속 통합 및 배포 관리, 테스트(유닛 테스트 및 UI 테스트 포함), 개발 및 프로덕션 환경에서 다양한 형태의 진단 실행, 원격 분석 및 분석을 통해 실시간으로 앱 성능과 사용자 동작 모니터링을 포함합니다.  
  
 Visual Studio Team Services 및 Team Foundation Server와 더불어 Visual Studio는 다양한 DevOps 기능(애플리케이션 수명 주기 관리 또는 ALM이라고도 함)을 제공합니다. 이 중에서 많은 기능을 플랫폼 간 프로젝트에 전체적으로 적용할 수 있습니다.  
  
 Xamarin 앱은 일부 ALM 도구를 빌드하는 C# 및 .NET으로 빌드되기 때문에 특히 그렇습니다. 기타 도구는 빌드 및 런타임 환경과 긴밀히 통합되어야 합니다. Xamarin 앱은 Windows 이외의 플랫폼에서 실행되며 .NET의 모노 구현을 사용하기 때문에 Xamarin은 특정 요구를 충족하는 특수 도구를 제공합니다.  
  
 아래 표에서는 Xamarin 프로젝트에서 제대로 작동하는 Visual Studio ALM 기능 및 제한 사항이 있는 Visual Studio ALM 기능을 식별합니다. 기능 자체에 대한 자세한 내용은 연결된 설명서를 참조하세요.  
  
## <a name="agile-tools"></a>Agile 도구  
 참조 링크: **[작업](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)**(Visual Studio Team Services 또는 TFS 사용, Team Explorer Everywhere 포함)  
  
 일반 설명: 모든 계획 및 추적 기능은 프로젝트 형식 및 코딩 언어와 독립적입니다.  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|백로그 및 스프린트 관리|예||  
|작업 추적|예||  
|단체 방 협업|예||  
|Kanban 보드|예||  
|보고 및 진행률 시각화|예||  
  
## <a name="modeling"></a>모델링  
 참조 링크: **[아키텍처 분석 및 모델링](../modeling/analyze-and-model-your-architecture.md)**  
  
 디자인 기능은 코딩 언어에 독립적이며 C#과 같은 .NET 언어에서 작동합니다. 코드와 관련 된 측면은 [소프트웨어 개발에서 아키텍처 및 모델링 다이어그램의 역할](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) 을 참조 하세요.  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|시퀀스 다이어그램|예||  
|종속성 그래프|예||  
|호출 계층 구조|예||  
|클래스 디자이너|예||  
|아키텍처 탐색기|예||  
|UML 다이어그램(사용 사례, 활동, 클래스, 구성 요소, 시퀀스 및 DSL)|예||  
|레이어 다이어그램|예||  
|레이어 유효성 검사|예||  
  
## <a name="code"></a>코드  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|[Team Foundation 버전 제어](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) 또는 Visual Studio Team Services 사용|예||  
|[Team Services에서 Git 시작하기](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|예||  
|[코드 분석/코드 품질 향상(참조, 제안된 변경 내용 등)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|예||  
|[코드 변경 내용 및 기타 기록 찾기](../ide/find-code-changes-and-other-history-with-codelens.md)|예|런타임까지 구현이 확인되지 않는 플랫폼 특정 경계를 넘는 경우는 제외됩니다.|  
|[코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)|예||  
  
## <a name="build"></a>빌드  
 참조 링크: **[빌드](/azure/devops/pipelines/index)**  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|온-프레미스 TFS 서버|예|빌드 컴퓨터에 Xamarin이 설치되어 있어야 하며, iOS용 빌드를 위해 OSX 컴퓨터에 연결할 수 있습니다. [Xamarin에 대 한 TFS 구성](/azure/devops/repos/tfvc/overview?view=azure-devops) (xamarin 웹 사이트)을 참조 하세요.|  
|Visual Studio Team Services에 연결된 온-프레미스 빌드 서버|예|자세한 내용은 [빌드 서버](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c)를 참조하세요.|  
|Visual Studio Team Services의 호스트된 컨트롤러 서비스|예|[Xamarin 앱 빌드](https://www.visualstudio.com/docs/build/apps/mobile/xamarin)를 참조하세요.|  
|사전 및 사후 스크립트로 정의 작성|예||  
|제어된 체크 인을 포함하는 연속 통합|예|Git는 체크 인이 아니라 끌어오기 요청 모델로 작동하므로 TFVC에 대한 제어된 체크 인에만 해당|  
  
## <a name="testing"></a>테스트  
 참조 링크: **[애플리케이션 테스트](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|테스트 계획, 테스트 사례 만들기 및 테스트 도구 모음 구성|예||  
|수동 테스트|예||  
|테스트 관리자(테스트 기록 및 재생)|예|Visual Studio에서만 제공하는 Windows 디바이스 및 Android 에뮬레이터. [Xamarin 테스트 레코더](https://www.xamarin.com/test-cloud/recorder)를 사용하면 모든 디바이스에 대한 기록이 가능합니다.|  
|코드 검사|해당 없음||  
|[코드 단위 테스트](../test/unit-test-your-code.md)|예|Windows 및 Android 대상의 경우 기본 제공 MSTest 도구를 사용할 수 있습니다. Windows, Android 및 iOS에서 단위 테스트를 실행하려면 NUnit를 사용하는 것이 좋습니다. [Xamarin용 TFS 구성](/azure/devops/repos/tfvc/overview?view=azure-devops) (Xamarin 웹 사이트)을 참조하세요.|  
|[UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)|Windows만|Visual Studio의 UI 테스트 레코더는 Windows 전용입니다. 모든 플랫폼에 대해서는 [Xamarin 테스트 레코더](https://www.xamarin.com/test-cloud/recorder)를 참조하세요.|  
  
## <a name="improve-code-quality"></a>코드 품질 향상  
 참조 링크: **[코드 품질 향상](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|[관리 코드 품질 분석](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|예||  
|[코드 복제본 검색을 사용하여 중복 코드 찾기](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|예||  
|[관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|예||  
|[성능 탐색기](../profiling/performance-explorer.md)|예|대신 Xamarin Studio를 통해 [Xamarin 프로파일러](/xamarin/cross-platform/deploy-test/) 를 사용합니다. Xamarin 프로파일러는 현재 미리 보기로 제공되며 아직 Windows 대상에서 작동하지 않습니다.|  
|[.NET Framework 메모리 문제 분석](../misc/analyze-dotnet-framework-memory-issues.md)|예|Visual Studio 도구에는 프로파일링을 위한 모노 프레임워크에 대한 후크가 없습니다.|  
  
## <a name="release-management"></a>릴리스 관리  
 참조 링크: **[릴리스 관리로 배포 자동화](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|릴리스 프로세스 관리|예||  
|스크립트를 통한 테스트용 로드를 위해 서버에 배포|예||  
|앱 스토어에 업로드|Partial|일부 앱 스토어의 경우 이 프로세스를 자동화할 수 있는 확장을 사용할 수 있습니다.  [Visual Studio Team Services용 확장](https://marketplace.visualstudio.com/VSTS)(예: [Google Play용 확장](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play))을 참조하세요.|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp으로 모니터링  
 참조 링크: **[HockeyApp으로 모니터링](https://www.hockeyapp.net/features/)**  
  
|기능|Xamarin에서 지원 여부|추가 설명|  
|-------------|----------------------------|-------------------------|  
|충돌 분석, 원격 분석 및 베타 분포|예||
