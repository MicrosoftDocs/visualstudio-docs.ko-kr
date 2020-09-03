---
title: Workflow Foundation 프로젝트 만들기
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8c3e4930376d2d2f9a6ee3334d8b164279d5ac2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597076"
---
# <a name="workflow-project-templates"></a>워크플로 프로젝트 템플릿

Visual Studio 프로젝트 템플릿을 사용 하 여 워크플로, Windows Communication Foundation (WCF) 워크플로 서비스, 사용자 지정 활동 및 사용자 지정 활동 디자이너를 만들 수 있습니다. 이 문서에서는 Visual Studio에서 사용할 수 있는 프로젝트 템플릿을 사용 하 여 라이브러리 및 응용 프로그램을 만드는 방법을 설명 합니다.

## <a name="create-a-workflow-project"></a>워크플로 프로젝트 만들기

Visual Studio는 다음과 같은 네 가지 워크플로 프로젝트 템플릿을 제공 합니다.

- 워크플로 콘솔 앱

- WCF workflow service 앱

- 활동 라이브러리

- 활동 디자이너 라이브러리

이러한 템플릿에 액세스 하려면 먼저 Visual Studio의 **Windows Workflow Foundation** 구성 요소를 설치 합니다. 자세한 지침은 [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)를 참조 하세요.

1. **Windows Workflow Foundation** 구성 요소를 설치한 후 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

1. 워크플로 프로젝트 템플릿 (예: **워크플로 콘솔 응용 프로그램** 템플릿)을 검색 하 고 선택 합니다.

1. 프로젝트 만들기를 계속 진행 합니다.

   > [!NOTE]
   > 기존 솔루션에 새 프로젝트를 추가 하려면 Visual Studio에서 해당 솔루션을 열고 **솔루션 탐색기**솔루션을 마우스 오른쪽 단추로 클릭 한 다음 **Add**  >  **새 프로젝트**추가를 선택 합니다.

## <a name="workflow-console-app"></a>워크플로 콘솔 앱

**워크플로 콘솔 응용 프로그램** 템플릿을 선택 하는 경우 Visual Studio에서 워크플로 정의를 XAML로 만듭니다. 워크플로 디자이너는 사용자가 만든 워크플로의 캔버스를 열고 표시 합니다. 워크플로를 작성 하려면 **도구 상자** 에서 디자인 화면으로 활동 또는 기타 워크플로 항목을 끌어 옵니다.

## <a name="wcf-workflow-service-app"></a>WCF workflow service 앱

**WCF 워크플로 서비스 응용 프로그램** 템플릿을 선택 하는 경우 Visual Studio는 서비스 정의를 XAML로 만듭니다. 워크플로 디자이너는 <xref:System.Activities.Statements.Sequence> 및 작업 집합을 포함 하는 활동을 사용 하 여 디자인 뷰로 열립니다 <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> .

## <a name="activity-library"></a>활동 라이브러리

**활동 라이브러리** 템플릿을 선택 하는 경우 Visual Studio에서 활동 정의를 XAML로 만듭니다. 워크플로 디자이너 열리고 사용자 지정 활동에 대 한 캔버스를 표시 합니다. 활동을 **도구 상자** 에서 디자인 화면으로 끌어 사용자 지정 활동에 포함 합니다.

> [!NOTE]
> 사용자 지정 활동의 본문에서 자식 활동을 하나만 사용할 수 있습니다. 그러나 해당 자식 활동은 활동 또는 활동과 같은 복합 활동 일 수 있습니다 <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Statements.Flowchart> .

## <a name="activity-designer-library"></a>활동 디자이너 라이브러리

**활동 디자이너 라이브러리** 템플릿을 선택 하는 경우 Visual Studio는 활동 디자이너 정의를 XAML 및 코드 기반 구현 파일로 만듭니다. 워크플로 디자이너는 활동 디자이너에 대 한 캔버스를 열고 표시 합니다. 사용자 지정 활동 디자이너에서 사용 하려면 **도구 상자** 에서 디자인 화면으로 WINDOWS PRESENTATION FOUNDATION (WPF) 컨트롤을 끕니다.

사용자 지정 활동 디자이너를 구현 하는 방법에 대 한 예제는 [방법: 사용자 지정 활동 디자이너 만들기](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)를 참조 하세요.

> [!NOTE]
> 사용자 지정 활동 디자이너는 사용자 지정 활동 및 기본 .NET 활동에 사용할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [Workflow Designer 사용](developing-applications-with-the-workflow-designer.md)
- [워크플로 디자인 (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
