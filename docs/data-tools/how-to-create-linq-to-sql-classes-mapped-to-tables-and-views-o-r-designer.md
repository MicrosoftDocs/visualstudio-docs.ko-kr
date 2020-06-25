---
title: 테이블/뷰에 LINQ to SQL 클래스 매핑 (O-R 디자이너)
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 19b634973e555fd037d20c3ad359ccbb1465c894
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282126"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>방법: 테이블 및 뷰에 매핑된 LINQ to SQL 클래스 만들기(O/R 디자이너)

[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]데이터베이스 테이블 및 뷰에 매핑된 클래스를 *엔터티 클래스*라고 합니다. 엔터티 클래스는 레코드에 매핑되고 엔터티 클래스의 개별 속성은 레코드를 구성 하는 개별 열에 매핑됩니다. **서버 탐색기** 또는 **데이터베이스 탐색기** 의 테이블이 나 뷰를 [Visual Studio의 LINQ to SQL 도구로](../data-tools/linq-to-sql-tools-in-visual-studio2.md)끌어 데이터베이스 테이블 또는 뷰를 기반으로 하는 엔터티 클래스를 만듭니다. **O/R 디자이너** 는 클래스를 생성 하 고 특정 특성을 적용 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 하 여 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 기능 (의 데이터 통신 및 편집 기능)을 사용 하도록 설정 합니다 <xref:System.Data.Linq.DataContext> . 클래스에 대 한 자세한 내용은 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] [LINQ to SQL 개체 모델](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)을 참조 하세요.

> [!NOTE]
> **O/R 디자이너** 는 1:1 매핑 관계만 지 원하는 단순 개체 관계형 매퍼입니다. 즉, 엔터티 클래스는 데이터베이스 테이블 또는 뷰와 1:1 매핑 관계만 갖습니다. 엔터티 클래스를 여러 테이블에 매핑하는 복잡한 매핑은 지원되지 않습니다. 그러나 엔터티 클래스를 여러 관련 테이블을 연결하는 뷰에 매핑할 수 있습니다.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>데이터베이스 테이블 또는 보기에 매핑된 LINQ to SQL 클래스 만들기

**서버 탐색기** 또는 **데이터베이스 탐색기** 에서 **O/R Designer** 로 테이블 또는 뷰를 끌어 오면 업데이트를 수행 하는 데 사용 되는 메서드와 함께 엔터티 클래스가 만들어집니다 <xref:System.Data.Linq.DataContext> .

기본적으로 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 런타임에서는 업데이트 가능한 엔터티 클래스의 변경 내용을 데이터베이스에 다시 저장하는 논리를 만듭니다. 이 논리는 열 정의 및 기본 키 정보와 같은 테이블 스키마를 기반으로 합니다. 이 동작을 원하지 않는 경우에는 기본 런타임 동작을 사용 하는 대신 저장 프로시저를 사용 하 여 삽입, 업데이트 및 삭제를 수행 하도록 엔터티 클래스를 구성할 수 있습니다 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] . 자세한 내용은 [방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O/R 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)을 참조 하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>데이터베이스 테이블 또는 뷰에 매핑된 LINQ to SQL 클래스를 만들려면

1. **서버** 또는 **데이터베이스 탐색기**에서 **테이블** 또는 **보기**를 확장하여 사용자 애플리케이션에 사용할 데이터베이스 테이블 또는 보기를 찾습니다.

2. 테이블이 나 뷰를 **O/R 디자이너로**끌어 옵니다.

     엔터티 클래스가 만들어져 디자인 화면에 표시됩니다. 엔터티 클래스에는 선택한 테이블 또는 뷰의 열에 매핑되는 속성이 있습니다.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>개체 데이터 원본을 만들어 폼에 데이터 표시

**O/R 디자이너**를 사용 하 여 엔터티 클래스를 만든 후에는 개체 데이터 소스를 만들고 엔터티 클래스를 사용 하 여 [데이터 소스 창을](add-new-data-sources.md#data-sources-window) 채울 수 있습니다.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>LINQ to SQL 엔터티 클래스 기반의 개체 데이터 소스를 만들려면

1. **빌드** 메뉴에서 **솔루션 빌드**를 클릭하여 프로젝트를 빌드합니다.

2. 데이터 **소스** 창을 열려면 **데이터** 메뉴에서 **데이터 소스 표시**를 클릭 합니다.

3. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

4. **데이터 원본 형식 선택** 페이지에서 **개체**를 클릭한 후, **다음**을 클릭합니다.

5. 노드를 확장하여 클래스를 찾아 선택합니다.

    > [!NOTE]
    > **Customer** 클래스를 사용할 수 없는 경우에는 마법사를 취소하고, 프로젝트를 빌드하고, 마법사를 다시 실행합니다.

6. **마침**을 클릭하여 데이터 원본을 만들고 **데이터 원본** 창에 **Customer** 엔터티 클래스를 추가합니다.

7. 항목을 **데이터 원본** 창에서 폼으로 끌어 옵니다.

## <a name="see-also"></a>참조

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습: LINQ to SQL 클래스 만들기(O-R 디자이너)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [DataContext 메서드(O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)
- [방법: 저장 프로시저 및 함수에 매핑된 DataContext 메서드 만들기(O/R 디자이너)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ to SQL 개체 모델](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작을 사용자 지정](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [방법: LINQ to SQL 클래스 사이에 연결(관계) 만들기(O/R 디자이너)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
