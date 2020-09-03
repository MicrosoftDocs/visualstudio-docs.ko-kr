---
title: 데이터 집합의 관계 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eb13ad7db9a4f13ce9bf983ce6327045f885f4d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652880"
---
# <a name="relationships-in-datasets"></a>데이터 세트에서의 관계
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관련 데이터 테이블이 포함 된 데이터 집합 <xref:System.Data.DataRelation> 은 개체를 사용 하 여 테이블 간의 부모/자식 관계를 나타내고 서로 관련 된 레코드를 반환 합니다. **데이터 소스 구성 마법사**를 사용 하 여 데이터 집합에 관련 테이블을 추가 하거나 **데이터 세트 디자이너**를 사용 하 여 개체를 만들고 구성 <xref:System.Data.DataRelation> 합니다.

 <xref:System.Data.DataRelation>개체는 다음 두 가지 함수를 수행 합니다.

- 작업 중인 레코드와 관련 된 레코드를 사용할 수 있게 만들 수 있습니다. 부모 레코드 ()에 있는 경우 자식 레코드를 제공 하 <xref:System.Data.DataRow.GetChildRows%2A> 고, 자식 레코드 ()로 작업 하는 경우 부모 레코드를 제공 <xref:System.Data.DataRow.GetParentRow%2A> 합니다.

- 부모 레코드를 삭제할 때 관련 자식 레코드를 삭제 하는 등의 참조 무결성에 대 한 제약 조건을 적용할 수 있습니다.

  개체의 실제 조인과 함수 간의 차이점을 이해 하는 것이 중요 합니다 <xref:System.Data.DataRelation> . 진정한 조인에서 레코드는 부모 및 자식 테이블에서 가져오며 단일 플랫 레코드 집합에 배치 됩니다. 개체를 사용 하는 경우 <xref:System.Data.DataRelation> 새 레코드 집합을 만들 수 없습니다. 대신 DataRelation은 테이블 간의 관계를 추적 하 고 부모 및 자식 레코드를 동기화 된 상태로 유지 합니다.

## <a name="datarelation-objects-and-constraints"></a>DataRelation 개체 및 제약 조건
 <xref:System.Data.DataRelation>개체는 다음과 같은 제약 조건을 만들고 적용 하는 데도 사용 됩니다.

- 테이블의 열에 중복 항목이 포함 되지 않도록 보장 하는 unique 제약 조건입니다.

- 데이터 집합의 부모 및 자식 테이블 간에 참조 무결성을 유지 하는 데 사용할 수 있는 외래 키 제약 조건입니다.

  개체에서 지정 하는 제약 조건은 <xref:System.Data.DataRelation> 자동으로 적절 한 개체를 만들거나 속성을 설정 하 여 구현 됩니다. 개체를 사용 하 여 외래 키 제약 조건을 만드는 경우 <xref:System.Data.DataRelation> 클래스의 인스턴스 <xref:System.Data.ForeignKeyConstraint> 는 <xref:System.Data.DataRelation> 개체의 속성에 추가 됩니다 <xref:System.Data.DataRelation.ChildKeyConstraint%2A> .

  Unique 제약 조건은 <xref:System.Data.DataColumn.Unique%2A> 데이터 열의 속성을로 설정 `true` 하거나 클래스의 인스턴스를 <xref:System.Data.UniqueConstraint> <xref:System.Data.DataRelation> 개체의 속성에 추가 <xref:System.Data.DataRelation.ParentKeyConstraint%2A> 하 여 구현 됩니다. 데이터 집합의 제약 조건 일시 중단에 대 한 자세한 내용은 [데이터 집합을 채우는 동안 제약 조건](../data-tools/turn-off-constraints-while-filling-a-dataset.md)해제를 참조 하세요.

### <a name="referential-integrity-rules"></a>참조 무결성 규칙
 외래 키 제약 조건의 일부로 세 지점에서 적용 되는 참조 무결성 규칙을 지정할 수 있습니다.

- 부모 레코드가 업데이트 되는 경우

- 부모 레코드가 삭제 되는 경우

- 변경 내용이 수락 되거나 거부 되는 경우

  지정할 수 있는 규칙은 열거형에 지정 되어 있으며 <xref:System.Data.Rule> 다음 표에 나와 있습니다.

|외래 키 제약 조건 규칙|작업|
|----------------------------------|------------|
|<xref:System.Data.Rule>|부모 레코드에 대 한 변경 (업데이트 또는 삭제)은 자식 테이블의 관련 레코드에도 적용 됩니다.|
|<xref:System.Data.Rule>|자식 레코드는 삭제 되지 않지만 자식 레코드의 외래 키는로 설정 됩니다 <xref:System.DBNull> . 이 설정을 사용 하면 자식 레코드를 "고아"로 남겨둘 수 있습니다. 즉, 부모 레코드와 관계가 없습니다. **참고:**  이 규칙을 사용 하면 자식 테이블에 잘못 된 데이터가 생성 될 수 있습니다.|
|<xref:System.Data.Rule>|관련 자식 레코드의 외래 키는 열의 속성에 설정 된 대로 기본값으로 설정 됩니다 <xref:System.Data.DataColumn.DefaultValue%2A> .|
|<xref:System.Data.Rule>|관련 자식 레코드는 변경 되지 않습니다. 이 설정을 사용 하면 자식 레코드에 잘못 된 부모 레코드에 대 한 참조가 포함 될 수 있습니다.|

 데이터 집합 테이블의 업데이트에 대 한 자세한 내용은 [데이터를 데이터베이스에 다시 저장](../data-tools/save-data-back-to-the-database.md)을 참조 하세요.

### <a name="constraint-only-relations"></a>제약 조건 전용 관계
 개체를 만들 때 <xref:System.Data.DataRelation> 제약 조건을 적용 하는 경우에만 관계를 사용 하도록 지정할 수 있습니다. 즉, 관련 레코드에 액세스 하는 데에도 사용 되지 않습니다. 이 옵션을 사용 하 여 약간 더 효율적이 고 관련 레코드 기능을 사용 하는 것 보다 더 작은 메서드를 포함 하는 데이터 집합을 생성할 수 있습니다. 그러나 관련 레코드에는 액세스할 수 없습니다. 예를 들어 제약 조건 전용 관계로 인해 자식 레코드가 아직 있는 부모 레코드를 삭제할 수 없으며, 부모를 통해 자식 레코드에 액세스할 수 없습니다.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>데이터 세트 디자이너에서 수동으로 데이터 관계 만들기
 Visual Studio에서 데이터 디자인 도구를 사용 하 여 데이터 테이블을 만들 때 데이터 원본에서 정보를 수집할 수 있는 경우 자동으로 관계가 만들어집니다. **도구 상자**의 데이터 **집합** 탭에서 수동으로 데이터 테이블을 추가 하는 경우 관계를 수동으로 만들어야 할 수 있습니다. 프로그래밍 방식으로 개체를 만드는 방법에 대 한 자세한 내용은 <xref:System.Data.DataRelation> [Datarelations 추가](https://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4)를 참조 하세요.

 데이터 테이블 간의 관계는 관계의 일 대 다 측면을 보여 주는 키와 무한대 문자를 사용 하 여 **데이터 세트 디자이너**의 선으로 나타납니다. 기본적으로 relationshipCommentEnd Id = ' 1c8c78e19b7fa441 '의 이름은 디자인 화면에 표시 되지 않습니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>두 데이터 테이블 간에 관계를 만들려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [방법: 데이터 세트 디자이너에서 데이터 집합 열기](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)를 참조 하세요.

2. **관계 개체를** **데이터 집합** 도구 상자에서 관계의 자식 데이터 테이블로 끌어 놓습니다.

     관계 **대화 상자가** 열리고 **관계** 개체를 끌어온 테이블로 **자식 테이블** 상자를 채웁니다.

3. **부모 테이블** 상자에서 부모 테이블을 선택 합니다. 부모 테이블은 일 대 다 관계의 "일" 쪽에 있는 레코드를 포함 합니다.

4. **자식 테이블** 상자에 올바른 자식 테이블이 표시 되는지 확인 합니다. 자식 테이블에는 일 대 다 관계의 "다" 쪽에 있는 레코드가 포함 되어 있습니다.

5. **이름** 상자에 관계 이름을 입력 하거나 선택한 테이블을 기반으로 기본 이름을 그대로 둡니다. <xref:System.Data.DataRelation>코드의 실제 개체 이름입니다.

6. **키 열** 과 **외래 키 열** 목록에서 테이블을 조인 하는 열을 선택 합니다.

7. 관계, 제약 조건 또는 둘 다를 만들지 여부를 선택 합니다. 자세한 내용은 [DataRelation 개체 소개](https://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)를 참조 하세요.

8. **중첩 관계** 상자를 선택 하거나 선택 취소 합니다. 이 옵션을 선택 하면 <xref:System.Data.DataRelation.Nested%2A> 속성이로 설정 `true` 되 고, 해당 행이 XML 데이터로 작성 되거나와 동기화 될 때 관계의 자식 행이 부모 열 내에 중첩 됩니다 <xref:System.Xml.XmlDataDocument> . 자세한 내용은 [DataRelations 중첩](https://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab)을 참조 하세요.

9. 이러한 테이블의 레코드를 변경 하는 경우 적용 되는 규칙을 설정 합니다. 자세한 내용은 <xref:System.Data.Rule>를 참조하세요.

10. **확인** 을 클릭 하 여 관계를 만듭니다. 두 테이블 사이에 관계 선이 디자이너에 나타납니다.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>데이터 세트 디자이너에 관계 이름을 표시 하려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다. 자세한 내용은 [방법: 데이터 세트 디자이너에서 데이터 집합 열기](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)를 참조 하세요.

2. **데이터** 메뉴에서 **관계 레이블 표시** 명령을 선택 하 여 관계 이름을 표시 합니다. 이 명령을 지워 관계 이름을 숨깁니다.
