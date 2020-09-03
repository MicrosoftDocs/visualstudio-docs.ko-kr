---
title: 워크플로 디자이너-Throw 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 650082ab0e4f8576b7028b8011c88bf5d93b2afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593098"
---
# <a name="throw-activity-designer"></a>Throw 활동 디자이너

**Throw** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.Throw> .

## <a name="the-throw-activity"></a>Throw 활동

<xref:System.Activities.Statements.Throw> 활동은 예외를 throw합니다.

### <a name="using-the-throw-activity-designer"></a>Throw 활동 디자이너 사용

**도구 상자**의 **오류 처리** 범주에서 **Throw** 활동 디자이너에 액세스 합니다.

**Throw** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 아무 곳에 나 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 그러면 <xref:System.Activities.Statements.Throw> 기본 **DisplayName** 인 Throw를 사용 하 여 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **Throw** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다. <xref:System.Activities.Statements.Throw.Exception%2A> 속성은 속성 표에서 편집해야 합니다.

### <a name="the-throw-properties"></a>Throw 속성

다음 표에서는 <xref:System.Activities.Statements.Throw> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Throw> 활동의 선택적 이름을 지정합니다. 기본값은 Throw입니다.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|throw할 예외입니다. 이 예외는 <xref:System.Exception>에서 파생되어야 합니다. 이 예외를 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|

## <a name="see-also"></a>추가 정보

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw 활동 디자이너](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
