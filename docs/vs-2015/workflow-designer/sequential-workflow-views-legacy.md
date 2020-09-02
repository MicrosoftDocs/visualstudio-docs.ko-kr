---
title: 순차 워크플로 뷰 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846209"
---
# <a name="sequential-workflow-views-legacy"></a>순차 워크플로 뷰(레거시)
[!INCLUDE[vs2010](../includes/vs2010-md.md)][!INCLUDE[wfd1](../includes/wfd1-md.md)]또는를 대상으로 하는 데 사용할 수 있는 레거시를 제공 합니다 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]에서는 친숙한 [!INCLUDE[wf](../includes/wf-md.md)] 사용자 인터페이스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 애플리케이션을 시각적으로 만들 수 있습니다. [!INCLUDE[wf](../includes/wf-md.md)] 애플리케이션은 활동이라고 하는 워크플로 프로세스 단계로 구성됩니다. 워크플로를 만들려면 **도구 상자** 에서 해당 활동 디자이너를 디자인 화면으로 끌어서 디자인 화면에서 활동을 작성 합니다.

 [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)순차 워크플로를 만드는 경우에는 세 가지 워크플로의 뷰를 사용할 수 있습니다. 이러한 보기는 **워크플로** 메뉴와 디자인 화면의 상황에 맞는 메뉴에서 액세스할 수 있습니다.

 다음 표에서는 각 뷰의 이름과 설명을 보여 줍니다.

|메뉴/탭 옵션|설명|
|----------------------|-----------------|
|**순차 워크플로 보기**|디자인 화면을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **SequentialWorkflow 보기** 옵션을 선택 하 **여 순차 워크플로 뷰를** 표시 합니다 .이 뷰에는 순차 워크플로의 활동 기반 그래픽 표현이 표시 됩니다. 또는 **워크플로** 메뉴에서 **SequentialWorkflow 보기** 를 선택 합니다.|
|**취소 처리기 보기**|디자인 화면을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **취소 처리기 보기** 옵션을 선택 하 여 워크플로에 연결 된 [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) 활동을 보여 주는 **순차 워크플로** 뷰를 표시 합니다. 또는 **워크플로** 메뉴에서 **취소 처리기 보기** 를 선택 합니다.|
|**오류 처리기 보기**|디자인 화면을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **오류 처리기 보기** 옵션을 선택 하 여 **오류** 뷰를 표시 합니다 .이 뷰는 워크플로와 연결 된 [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) 활동을 보여 줍니다. 또는 **워크플로** 메뉴에서 **오류 처리기 보기** 를 선택 합니다.|

 유사한 뷰에 대 한 자세한 내용은 [활동 뷰 (레거시)](../workflow-designer/activity-views-legacy.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [활동 뷰 (레거시)](../workflow-designer/activity-views-legacy.md) [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md) [워크플로 제작 모드](https://msdn2.microsoft.com/library/bb628440.aspx)
