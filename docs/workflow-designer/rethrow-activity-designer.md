---
title: 워크플로 디자이너-다시 Throw 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114755"
---
# <a name="rethrow-activity-designer"></a>Rethrow 활동 디자이너

다시 **throw** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Rethrow> .

## <a name="the-rethrow-activity"></a>다시 Throw 작업

<xref:System.Activities.Statements.Rethrow> 활동은 이전에 throw된 예외를 throw합니다. 이 활동은 <xref:System.Activities.Statements.Catch> 활동의 <xref:System.Activities.Statements.TryCatch> 처리기에서만 사용할 수 있습니다.

### <a name="use-the-rethrow-activity-designer"></a>다시 Throw 활동 디자이너 사용

**도구 상자**의 **오류 처리** 범주에 있는 다시 **throw** 활동 디자이너에 액세스 합니다. 다시 **throw** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 활동 디자이너를 삭제 하면 <xref:System.Activities.Statements.Rethrow> 기본 **DisplayName** 인 Throw를 사용 하 여 활동이 만들어집니다. 다시 <xref:System.Activities.Activity.DisplayName%2A> **throw** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다.

### <a name="the-rethrow-properties"></a>다시 Throw 속성

다음 표에서는 <xref:System.Activities.Statements.Rethrow> 속성을 보여 주고 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> 활동의 선택적 이름을 지정합니다. 기본값은 Rethrow입니다.|

## <a name="see-also"></a>추가 정보

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [반환할](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
