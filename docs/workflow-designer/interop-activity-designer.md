---
title: 워크플로 디자이너-Interop 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650206"
---
# <a name="interop-activity-designer"></a>Interop 활동 디자이너

**Interop** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Interop> .

## <a name="the-interop-activity"></a>Interop 활동

<xref:System.Activities.Statements.Interop> 활동은 워크플로의 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>에서 파생되는 형식의 실행을 관리합니다.

### <a name="use-the-interop-activity-designer"></a>Interop 활동 디자이너 사용

**Interop** 활동 디자이너 **는 도구 상자**의 **마이그레이션** 범주에 있습니다 .이 범주에 액세스 하려면 **도구 상자** 탭을 클릭 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** + **Alt** + **X**를 누릅니다.

작업을 포함 하는 [마이그레이션](../workflow-designer/migration-activity-designers.md) 범주는 <xref:System.Activities.Statements.Interop> 프로젝트가 4 (전체) 이상 버전을 .NET Framework 대상으로 하는 경우에만 **도구 상자** 에 표시 됩니다. 필요한 경우 프로젝트의 대상 프레임 워크 버전을 변경할 수 있습니다.

**Interop** 활동 디자이너를 **도구 상자** 에서 끌어와 같이 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . **Interop** 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.Interop> 기본 **DisplayName** 이 interop 인 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Interop** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서을 편집할 수 있습니다.

**Interop** 활동 디자이너 또는 속성 표에서 **ActivityType** 상자의 텍스트를 **찾아보려면 클릭** 하 여 **.net 유형 찾아보기 및 선택** 대화 상자를 엽니다. 워크플로 3.0 또는 워크플로 3.5 활동에 대 한 유형만 표시 됩니다. 즉,에서 파생 된 유형만 <xref:System.Workflow.ComponentModel.Activity> 표시 됩니다. 이 상자를 사용 하 여 형식을 지정 하는 방법에 대 한 자세한 내용은 [.Net 형식 찾아보기 및 선택 대화 상자](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)를 참조 하세요.

### <a name="the-interop-properties"></a>Interop 속성

다음 표에서는 <xref:System.Activities.Statements.Interop> 속성을 보여 주고 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다. 이러한 속성은 속성 표 또는 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 활동의 이름입니다. 기본값은 **Interop**입니다. 표시 이름은 필수는 아니지만 하나를 제공 하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> 활동에 포함된 활동의 형식을 지정합니다. 지정된 이 형식은 <xref:System.Workflow.ComponentModel.Activity>에서 파생된 것이어야 합니다.|

## <a name="see-also"></a>추가 정보

- [마이그레이션](../workflow-designer/migration-activity-designers.md)