---
title: 워크플로 디자이너를 사용 하 여 응용 프로그램 개발 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656819"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Workflow Designer로 애플리케이션 개발
[!INCLUDE[wfd1](../includes/wfd1-md.md)]는 [!INCLUDE[wf](../includes/wf-md.md)] 개발 환경에 호스트되는 [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)]에서 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 애플리케이션을 디버깅하고 그래픽을 생성하는 비주얼 디자이너 겸 디버거입니다. 여기서 템플릿 및 활동 디자이너를 사용하여 복합 워크플로 애플리케이션, 활동 라이브러리 또는 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 서비스를 생성할 수 있습니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 워크플로 [Windows Workflow Foundation &#91; .NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66)를 참조 하세요.

 새 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 버전에서 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 이전 버전과 달라진 몇 가지 디자인 기능은 다음과 같습니다.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[avalon1](../includes/avalon1-md.md)]로 제작되었습니다. 따라서 활동 디자이너의 사용 경험과 대형 복합 워크플로에 대한 성능이 향상되었습니다.

- 이제 XAML을 사용하여 [!INCLUDE[avalon2](../includes/avalon2-md.md)]로 사용자 지정 활동을 설계할 수 있으며 활동 디자이너를 생성하는 프로그래밍 모델이 간소화되었습니다.

- 익숙한 순서도 모델링 스타일을 사용하여 프로그램 흐름을 시각화할 수 있도록 순서도 활동을 구현했습니다.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)]에는 워크플로 내에서 변수를 선언하고 범위를 지정하여 활동에 바인딩할 수 있도록 하는 새로운 변수 디자이너가 있습니다.

- [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 워크플로 내에 Visual Basic 식을 작성할 때 완전한 IntelliSense 기능을 제공합니다.

- 이제 디버깅 환경이 XAML까지 확장되어 XAML 워크플로 정의에 중단점을 설정하고 런타임 시 XAML 코드를 한 단계씩 실행할 수 있으므로 관리 코드와 비슷한 사용 경험을 얻을 수 있습니다.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] 외부에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 재호스트하는 작업이 이전 버전과 비교할 때 훨씬 간소화되어 이제는 코드 몇 줄만 있으면 됩니다.

- 새 <xref:System.Activities.Statements.Flowchart> 작업 및 해당 [순서도](../workflow-designer/flowchart-activity-designer.md) 를 사용 하면 익숙한 순서도 모델링 스타일을 사용 하 여 프로그램 흐름을 시각화할 수 있습니다.

- 메시징 활동도 향상되어 완전 선언적(코드 없음) [!INCLUDE[indigo1](../includes/indigo1-md.md)] 서비스를 작성할 수 있습니다.

- **서비스 참조 추가** ... 기능을 사용 하면 웹 서비스에 액세스 하는 작업을 자동으로 생성할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
 [워크플로 디자이너 사용](../workflow-designer/using-the-workflow-designer.md) 기본 제공 디자이너를 사용 하 여 새 작업 및 워크플로 프로젝트를 만드는 방법과 디자이너에서 제공 하는 다른 도구를 사용 하 여 인수, 변수, 식, 가져오기 및 이동 경로 탐색을 처리 하는 방법을 보여 줍니다.

 [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md) 시스템에서 제공 하는 작업 및 템플릿 및 디자이너의 범주에 대해 설명 합니다.

 [워크플로 디자이너를 사용 하 여 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) 기존 디버깅 절차를 수행 하는 방법과 XAML 및 식 디버깅을 수행 하는 방법을 설명 합니다.

 [워크플로 디자이너 UI 도움말](../workflow-designer/workflow-designer-ui-help.md) 에서 제공 하는 대화 상자에 대 한 상황에 맞는 도움말 항목 뿐만 아니라 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 디자이너 셸 기능, 바로 가기 키 및 오류 메시지에 대 한 지침을 제공 합니다.

 [.Net 3.0 또는 .net 3.5 프레임 워크를 대상으로 하는 워크플로 응용 프로그램 개발](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) 또는를 대상으로 하는 레거시 디자이너를 사용 하는 방법에 대 한 지침을 포함 합니다 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [Designer 재호스팅 &#91;WF 샘플&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) 이 샘플에서는 디자이너를 포함 하는 WPF 레이아웃을 만드는 방법을 보여 줍니다.

 [사용자 지정 활동 디자이너](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) 이 섹션에는 workflow designer에 표시할 사용자 지정 디자이너를 사용 하는 활동 샘플이 포함 되어 있습니다.