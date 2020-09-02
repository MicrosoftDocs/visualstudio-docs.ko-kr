---
title: 레거시 상태 시스템 워크플로 디자이너 사용 Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 77bb2c7abb49dbf6fe973ebc80f8340000e4afbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846000"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>레거시 상태 시스템 워크플로 디자이너 사용
또는 중 하나를 대상으로 하는 새 상태 시스템 워크플로 프로젝트를 만드는 경우 [!INCLUDE[vs2010](../includes/vs2010-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] **상태 시스템 워크플로 콘솔 응용 프로그램** 또는 **상태 시스템 워크플로 라이브러리** 레거시 프로젝트 템플릿을 사용 하도록 선택할 수 있습니다. 이러한 상태 시스템 프로젝트 템플릿 중 하나를 선택하면 상태 시스템 디자이너가 레거시 Workflow Designer 사용자 인터페이스로 나타납니다. 레거시 상태 시스템 프로젝트 템플릿에 대 한 자세한 내용은 [방법: 상태 시스템 워크플로 콘솔 응용 프로그램 만들기 (레거시)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) 및 [방법: 상태 시스템 워크플로 라이브러리 만들기 (레거시)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)를 참조 하세요.

 상태 시스템 워크플로는 상태 집합으로 구성됩니다. 하나의 상태가 초기 상태로 표시됩니다. 각 상태는 특정 이벤트 집합을 받을 수 있으며 이벤트에 따라 다른 상태로 전환될 수 있습니다. 상태 시스템 워크플로는 최종 상태를 가질 수 있으며, 최종 상태로 전환되면 워크플로가 완료됩니다.

## <a name="state-machine-designer-views"></a>상태 시스템 디자이너 뷰
 상태 시스템 디자이너는 자유형 디자이너로서, 디자인 화면에서 활동을 자유롭게 이동할 수 있습니다. 상태 시스템 디자이너에는 *상태* 보기와 *이벤트 기반* 보기의 두 가지 뷰가 있습니다.

 상태 뷰에서는 상태 활동 및 상태 활동에 포함할 수 있는 이벤트 구동 활동을 표시합니다. 이 뷰에서는 상태 전환이 한 상태의 이벤트 구동 활동에서 다른 상태로 이어지는 선으로 표현됩니다. 직접 선을 그려서 전환을 만들 수도 있습니다. 전환을 그리려면 이벤트 구동 활동을 선택한 다음 해당 활동의 핸들 중 하나를 선택하여 끕니다. 그러면 선이 그려집니다. 그려진 선은 대상 상태에 연결되어 상태 전환을 나타냅니다.

 이벤트 구동 뷰에 액세스하려면 이벤트 구동 활동을 두 번 클릭합니다. 순차 워크플로 디자이너와 매우 비슷한 디자이너가 나타납니다. 디자이너 맨 위의 탐색 모음은 활동의 계층 구조를 표시하며 이 계층 구조에는 이벤트 구동 활동까지 나타납니다. 표시된 계층 구조에서 임의의 요소를 클릭하면 상태 뷰로 돌아갈 수 있습니다. 상태 뷰에서 상태 전환을 그렸고 해당 활동의 이벤트 구동 뷰를 표시하려는 경우, 설정된 상태 활동이 이벤트 구동 활동에 추가됩니다. 설정된 상태 활동의 속성을 변경하면 이는 다시 상태 뷰에 반영됩니다.

## <a name="state-machine-workflow-activities"></a>상태 시스템 워크플로 활동
 다음 표에서는 상태 시스템 Workflow Designer에서 사용되는 핵심 활동에 대해 설명합니다.

|도구 상자 이름|작업|설명|
|------------------|--------------|-----------------|
|**상태**|[StateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx)|상태 시스템의 상태를 나타냅니다. 추가 **Stateactivity** 활동을 포함할 수 있습니다. 자세한 내용은 [StateActivity 활동 사용](https://msdn2.microsoft.com/library/bb628612.aspx)을 참조 하세요.|
|**SetState**|[SetStateActivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx)|새 상태로의 전환을 지정합니다. 자세한 내용은 [SetStateActivity 활동 사용](https://msdn2.microsoft.com/library/bb628469.aspx)을 참조 하세요.|
|**StateInitialization**|[StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx)|상태가 시작되면 실행되며, 다른 활동을 포함할 수도 있습니다. 자세한 내용은 [StateInitialization 활동 사용](https://msdn2.microsoft.com/library/bb675253.aspx)을 참조 하세요.|
|**StateFinalization**|[StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)|[Stateactivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 활동을 나갈 때 포함 된 활동을 실행 합니다. 자세한 내용은 [StateFinalizationActivity 활동 사용](https://msdn2.microsoft.com/library/bb675278.aspx)을 참조 하세요.|
|**EventDriven**|[EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx)|실행 시작 여부가 외부 이벤트에 따라 달라지는 상태에 사용됩니다. **EventDrivenActivity** 활동에는 첫 번째 자식 활동으로 [ieventactivity](https://msdn2.microsoft.com/library/system.workflow.activities.ieventactivity.aspx) 인터페이스를 구현 하는 활동이 있어야 합니다. 자세한 내용은 [EventDrivenActivity 활동 사용](https://msdn2.microsoft.com/library/bb628466.aspx)을 참조 하세요.|

 상태 시스템 워크플로의 주 구성 요소는 [Stateactivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateactivity.aspx) 활동입니다. 상태 시스템 워크플로의 여러 지점에서 이벤트가 캡처되므로 이벤트와 연결된 작업을 처리하기 위해 여러 상태가 시작됩니다. 워크플로 수명 중에 워크플로가 여러 상태를 끝내고 시작할 수 있습니다. 이러한 상태는 [Setstateactivity](https://msdn2.microsoft.com/library/system.workflow.activities.setstateactivity.aspx) 활동을 사용 하 여 서로 연결 됩니다.

 새 **Stateactivity** 를 워크플로 디자인 화면으로 끌어 올 때 [EventDrivenActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventdrivenactivity.aspx), [StateInitializationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.stateinitializationactivity.aspx), [StateFinalizationActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statefinalizationactivity.aspx)또는 추가 **stateactivity** 활동을 자식 활동으로 추가할 수 있습니다.

> [!CAUTION]
> 상태 시스템 워크플로 디자이너를 사용 하 여 워크플로를 만드는 경우 **문서 개요** 뷰 창을 사용 하 여 디자인 중인 워크플로의 구조를 모니터링 해야 합니다. **문서 개요** 뷰 창에 있는 상태 시스템 워크플로의 구조 보기는 워크플로 마크업 파일의 활동에 대 한 논리적 레이아웃을 반영 합니다. 디자인 화면에 나타나는 워크플로 활동의 실제 레이아웃은 워크플로 마크업 파일의 활동에 대한 논리 레이아웃을 미러링하지 않을 수도 있습니다.
>
> **문서 개요** 창을 열려면 **보기** 메뉴에서 **다른 창**을 가리킨 다음 **문서 개요**를 선택 합니다.

## <a name="see-also"></a>관련 항목
 [방법: 상태 시스템 워크플로 콘솔 응용 프로그램 만들기 (레거시)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) 방법: [StateFinalizationActivity 활동](https://msdn2.microsoft.com/library/bb675278.aspx) 을 사용 하 여 [StateInitializationActivity 활동](https://msdn2.microsoft.com/library/bb675253.aspx) 을 사용 하 여 [상태 시스템 워크플로 라이브러리 (레거시)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [상태 시스템](https://msdn2.microsoft.com/library/bb628601.aspx) [워크플로](https://msdn2.microsoft.com/library/bb628612.aspx) 만들기 [EventDrivenActivity 활동을 사용](https://msdn2.microsoft.com/library/bb628466.aspx) 하 여 [setstateactivity](https://msdn2.microsoft.com/library/bb628469.aspx) 활동 사용
