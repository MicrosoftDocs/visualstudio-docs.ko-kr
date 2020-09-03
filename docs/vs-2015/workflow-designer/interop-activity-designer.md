---
title: Interop 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659031"
---
# <a name="interop-activity-designer"></a>Interop 활동 디자이너
**Interop** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Interop> .

## <a name="the-interop-activity"></a>Interop 활동
 <xref:System.Activities.Statements.Interop> 활동은 워크플로의 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>에서 파생되는 형식의 실행을 관리합니다.

### <a name="using-the-interop-activity-designer"></a>Interop 활동 디자이너 사용
 **Interop** 활동 디자이너 **는 도구 상자**의 **마이그레이션** 범주에 있습니다 .이 범주에 액세스 하려면 **도구 상자** 탭을 클릭 하거나, **보기** 메뉴에서 **도구 상자** 를 선택 하거나, CTRL + ALT + X를 선택 합니다.

 작업을 포함 하는 [마이그레이션](../workflow-designer/migration-activity-designers.md) 범주는 <xref:System.Activities.Statements.Interop> 프로젝트가 전체를 대상으로 하는 경우에만 **도구 상자** 에 표시 됩니다 [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 C # 프로젝트의 경우 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 하 여 전체를 사용 하도록 프로젝트 대상을 다시 지정할 수 있습니다. **응용 프로그램** 탭에서 **대상 프레임 워크**의 **.net framework 4** 옵션을 선택 합니다. 이 변경 내용을 확인 하 라는 메시지가 표시 되는 **대상 프레임 워크 변경** 대화 상자에서 **예** 단추를 선택 합니다.

 VB 프로젝트의 경우 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 하 여 전체를 사용 하도록 프로젝트 대상을 다시 지정할 수 있습니다. **컴파일** 탭에서 **고급 컴파일 옵션** 단추를 클릭 합니다. **대상 프레임 워크 목록** 에서 **.net Framework 4** 를 선택한 다음 **확인을**클릭 합니다. **대상 프레임 워크 변경** 대화 상자에서 **예** 단추를 클릭 하 여이 변경 내용을 확인 하는 메시지를 표시 합니다.

 **Interop** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 놓을 수 있습니다 [!INCLUDE[wfd2](../includes/wfd2-md.md)] <xref:System.Activities.Statements.Sequence> . 이렇게 하면 <xref:System.Activities.Statements.Interop> 기본 **DisplayName** 이 Interop 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Interop** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

 **찾아보려면 클릭** ... **.Net 형식 찾아보기 및 선택** 대화 상자를 표시 하는 **Interop** 활동 디자이너나 속성 표에 있는 **ActivityType** 상자의 텍스트입니다. 워크플로 3.0 또는 워크플로 3.5 활동의 형식(<xref:System.Workflow.ComponentModel.Activity>에서 파생된 형식)만 표시됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하 여 형식을 지정 하려면 [.Net 형식 찾아보기 및 선택 대화 상자](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) 항목을 참조 하세요.

### <a name="the-interop-properties"></a>Interop 속성
 다음 표에서는 <xref:System.Activities.Statements.Interop> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 활동의 이름입니다. 기본값은 Interop입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> 활동에 포함된 활동의 형식을 지정합니다. 지정된 이 형식은 <xref:System.Workflow.ComponentModel.Activity>에서 파생된 것이어야 합니다.|

## <a name="see-also"></a>관련 항목
 [마이그레이션](../workflow-designer/migration-activity-designers.md)