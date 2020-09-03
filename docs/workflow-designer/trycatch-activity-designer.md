---
title: 워크플로 디자이너 TryCatch 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b70f1d3174990ec12c621dff4a45ce4d899ceb4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593072"
---
# <a name="trycatch-activity-designer"></a>TryCatch 활동 디자이너

**TryCatch** 활동 디자이너는 활동을 만들고 구성 하는 데 사용 됩니다 <xref:System.Activities.Statements.TryCatch> .

## <a name="the-trycatch-activity"></a>TryCatch 활동
 활동에는 <xref:System.Activities.Statements.TryCatch> <xref:System.Activities.Statements.TryCatch.Try%2A> 활동, ** \<TException> Catch** 컬렉션 및 활동이 포함 <xref:System.Activities.Statements.TryCatch.Finally%2A> 됩니다. <xref:System.Activities.Statements.Catch%601> **Texception** 형식의에는 및가 포함 되어 있습니다 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> <xref:System.Activities.Statements.Catch%601.Action%2A> . 둘 다 일반적인 예외 기반의 오류 처리 메커니즘을 구현하는 데 사용됩니다. <xref:System.Activities.Statements.TryCatch> 활동은 <xref:System.Activities.Statements.TryCatch.Try%2A> 활동을 실행하려고 합니다. 활동에서 <xref:System.Activities.Statements.TryCatch.Try%2A> 예외를 throw 하는 경우 <xref:System.Activities.Statements.TryCatch> 활동은 해당 **Catch<texception \> ** 컬렉션을 사용 하 여 예외를 일치 시킵니다. 일치 하는 항목이 있는 경우 <xref:System.Activities.Statements.Catch%601.Action%2A> 예외에 대 한 오류 처리 논리로 제공 되는 해당 **Catch \<TException> ** 의이 실행 됩니다. <xref:System.Activities.Statements.TryCatch.Try%2A> 섹션의 활동이 성공적으로 완료되었거나 <xref:System.Activities.Statements.TryCatch.Catches%2A>의 활동이 성공적으로 완료된 경우 <xref:System.Activities.Statements.TryCatch> 활동은 해당 <xref:System.Activities.Statements.TryCatch.Finally%2A> 활동을 실행합니다. 자세한 내용은 [Windows 워크플로 예외](/dotnet/framework/windows-workflow-foundation/exceptions)를 참조 하세요.

### <a name="using-the-trycatch-activity-designer"></a>TryCatch 활동 디자이너 사용

**도구 상자**의 **오류 처리** 범주에 있는 **TryCatch** activity 디자이너에 액세스 합니다.

**TryCatch** 활동 디자이너를 **도구 상자** 에서 끌어다가 등 일반적으로 활동을 배치 하는 워크플로 디자이너 화면에 놓을 수 있습니다 <xref:System.Activities.Statements.Sequence> . 이렇게 하면 기본 <xref:System.Activities.Statements.TryCatch>인 TryCatch라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> **TryCatch** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 값을 편집할 수 있습니다. **TryCatch** 활동 디자이너의 화면에서 다른 속성을 편집 해야 합니다.

**TryCatch** 디자이너의 오른쪽 위 모퉁이에 있는 확장 단추를 클릭 하 여 확장 된 보기에 **Try**, **catch**및 **Finally** 상자를 표시 합니다. Catch를 추가 하려면 **TryCatch** 디자이너의 **새 catch 추가** 단추를 클릭 합니다. 단추가 형식 콤보 상자로 바뀝니다. 예외 형식을 선택하고 &lt;ENTER&gt; 키를 눌러 Catch를 추가합니다. **Catch를**추가한 후에는 catch 영역이 확장 되 고 catch에 활동을 끌어 catch에 대 한 실행 논리를 정의할 수 있습니다. 확장된 Catch 영역 오른쪽에는 텍스트 상자가 있습니다. 이 텍스트 상자를 사용하여 예외 변수의 이름을 지정할 수 있습니다. 예외 변수는 동일한 **Catch**내의 활동에만 사용할 수 있습니다.

**TryCatch** 디자이너는 **Catch**편집을 지원 하지 않습니다. 예외 유형을 변경 하려면 Catch를 삭제 하 고 새 **Catch** 를 추가 해야 합니다. **Catch** 를 선택 하 고 삭제 하거나 마우스 오른쪽 단추를 클릭 하 여 액세스 하는 상황에 맞는 메뉴에서 **삭제** 를 선택 하 여 삭제할 수 있습니다.

### <a name="the-trycatch-properties"></a>TryCatch 속성

다음 표에서는 속성을 보여 주고 <xref:System.Activities.Statements.TryCatch> 디자이너에서 이러한 속성을 사용 하는 방법을 설명 합니다.

|속성 이름|필수|사용량|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TryCatch> 활동의 선택적 이름을 지정합니다. 기본 TryCatch입니다.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|<xref:System.Activities.Statements.TryCatch>가 실행될 때 처음으로 실행되는 동작입니다.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|활동에서 예외를 throw 할 때 확인할 **Catch** 요소의 컬렉션입니다 <xref:System.Activities.Statements.TryCatch.Try%2A> .<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A>에 하나 이상의 활동을 추가하거나 <xref:System.Activities.Statements.TryCatch.Finally%2A> 블록에 활동을 추가해야 합니다.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> 및 <xref:System.Activities.Statements.TryCatch.Catches%2A> 컬렉션의 필요한 모든 활동이 실행 완료될 때 실행할 작업입니다.<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A>에 하나 이상의 활동을 추가하거나 <xref:System.Activities.Statements.TryCatch.Finally%2A> 블록에 활동을 추가해야 합니다.|

## <a name="see-also"></a>추가 정보

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [반환할](../workflow-designer/throw-activity-designer.md)
