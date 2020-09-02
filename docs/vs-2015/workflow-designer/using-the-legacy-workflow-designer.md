---
title: 레거시 워크플로 디자이너 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c92b4431c21c27bc1fe2ff86b24c850cc34694
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846089"
---
# <a name="using-the-legacy-workflow-designer"></a>레거시 Workflow Designer 사용
[!INCLUDE[wfd2](../includes/wfd2-md.md)] 또는 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 대상으로 하려는 경우 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]에서 제공하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용할 수 있습니다.

 **새 프로젝트** 창의 맨 위에 있는 드롭다운 목록에서 **.NET Framework 3.0** 옵션 또는 **.NET Framework 3.5** 옵션을 선택 하 여 액세스할 수 있습니다. 의 기본 옵션은를 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 대상으로 하는 응용 프로그램을 만드는 데 사용 되는 **.NET Framework 4** 입니다 [!INCLUDE[wf](../includes/wf-md.md)] [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]에서는 친숙한 [!INCLUDE[wf](../includes/wf-md.md)] 사용자 인터페이스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 애플리케이션을 시각적으로 만들 수 있습니다. [!INCLUDE[wf](../includes/wf-md.md)] 애플리케이션은 활동이라고 하는 워크플로 프로세스 단계로 구성됩니다. 워크플로를 만들려면 **도구 상자** 에서 해당 활동 디자이너를 디자인 화면으로 끌어서 디자인 화면에서 활동을 작성 합니다.

 다음 표에서는 Windows Workflow Foundation용 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 주요 기능을 보여 줍니다.

|기능|설명|
|-------------|-----------------|
|활동 끌어서 놓기|활동을 **도구 상자** 에서 디자인 화면으로 끌어 워크플로를 만듭니다.|
|속성 브라우저|의 표준 **속성** 창은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 활동의 속성을 구성 하는 데 사용 됩니다.|
|Zoom|쌍안경 **확대/축소 수준** 아이콘은 디자인 화면 오른쪽의 세로 스크롤 막대 아래에 있습니다. 쌍안경을 클릭 하 고 확대/축소 비율을 선택 하 여 워크플로 그래픽을 확대 하거나 축소 합니다. **팬** 아이콘 돋보기 커서 옵션을 사용 하 여 확대 및 축소할 수도 있습니다.|
|이동|네 방향을 가리키는 네 개의 교차 화살표를 포함 하는 원 **팬** 아이콘은 디자인 화면 오른쪽의 세로 스크롤 막대 아래에 있는 쌍안경 확대/축소 아이콘 바로 아래에 있습니다. 팬 아이콘을 클릭하면 팝업 메뉴가 나타나 다음과 같은 커서 옵션을 제공합니다.<br /><br /> -돋보기 커서를 **확대** 하 여 디자인 화면을 클릭 하 여 확대할 수 있습니다.<br />- **축소** 돋보기 커서를 사용 하 여 디자인 화면을 클릭 하면 축소할 수 있습니다.<br />- **탐색 도구** 손 모양 커서를 사용 하 여 디자인 화면에서 워크플로 뷰를 "가져오고" 이동할 수 있습니다.<br />- **기본** 화살표 커서를 사용 하면 다른 커서에서 기본 화살표 커서로 다시 전환할 수 있습니다.|
|자동 스크롤|워크플로가 큰 경우 디자인 화면의 가시 영역을 바깥으로 활동을 배치할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 활동을 배치할 위치와 가장 가까운 디자인 화면의 가장자리 쪽으로 활동을 끌 수 있습니다. 그러면 디자인 화면 뷰가 자동으로 그 방향으로 이동합니다.|
|스마트 태그|완전히 구성되지 않거나 올바르지 않게 구성된 활동은 느낌표 아이콘으로 표시됩니다. 이 아이콘을 클릭하면 해당 활동에 대한 구성 요구 사항 보여 주는 드롭다운 목록이 나타납니다. 그런 다음 **속성** 창을 사용 하 여 활동을 적절 하 게 구성할 수 있습니다. 활동의 모든 속성이 올바르게 구성되면 느낌표 아이콘이 사라집니다.|

## <a name="in-this-section"></a>섹션 내용
 [Visual Studio 워크플로 창(레거시)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)

 [순차 워크플로 뷰(레거시)](../workflow-designer/sequential-workflow-views-legacy.md)

 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)

 [워크플로에서 테마 사용(레거시)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [레거시 상태 시스템 워크플로 디자이너 사용](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [레거시 활동 디자이너 사용](../workflow-designer/using-the-legacy-activity-designer.md)

 [Windows Workflow Foundation용 레거시 디자이너 UI 도움말](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>관련 항목
 [워크플로 개발](https://msdn2.microsoft.com/library/bb628448.aspx)
