---
title: DataContext 메서드를 sprocs 및 함수에 매핑
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6926631cfd9d04992d92553a346348ea18af847
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038337"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>방법: 저장 프로시저 및 함수에 매핑된 DataContext 메서드 만들기(O/R 디자이너)

저장 프로시저 및 함수를 **O/R 디자이너** 에 메서드로 추가할 수 있습니다 <xref:System.Data.Linq.DataContext> . 메서드를 호출하여 필요한 매개 변수에 전달하면 데이터베이스의 저장 프로시저 또는 함수가 실행되어 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식으로 데이터를 반환합니다. 메서드에 대 한 자세한 내용은 <xref:System.Data.Linq.DataContext> [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

> [!NOTE]
> 저장 프로시저를 사용 하 여 [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 엔터티 클래스의 변경 내용이 데이터베이스에 저장 될 때 삽입, 업데이트 및 삭제를 수행 하는 기본 런타임 동작을 재정의할 수도 있습니다. 자세한 내용은 [방법: 저장 프로시저를 할당하여 업데이트, 삽입 및 삭제 수행(O/R 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)을 참조하세요.

## <a name="create-datacontext-methods"></a>DataContext 메서드 만들기

<xref:System.Data.Linq.DataContext> <strong>서버 탐색기 또는 * * 데이터베이스 탐색기</strong> 의 저장 프로시저 또는 함수를 **O/R 디자이너로**끌어 메서드를 만들 수 있습니다.

> [!NOTE]
> 생성 된 메서드의 반환 형식은 <xref:System.Data.Linq.DataContext> **O/R 디자이너**에서 저장 프로시저 또는 함수를 놓는 위치에 따라 달라 집니다. drop항목을 기존 엔터티 클래스에 직접 드롭하면 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. **O/R 디자이너** 의 빈 영역에 항목을 놓으면 <xref:System.Data.Linq.DataContext> 자동으로 생성 된 형식을 반환 하는 메서드가 만들어집니다. **Methods** 창에 추가한 후 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 변경할 수 있습니다. <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 검사하거나 변경하려면 해당 메서드를 선택하고 **속성** 창에서 **반환 형식** 속성을 검사합니다. 자세한 내용은 [방법: DataContext 메서드의 반환 형식 변경 (O/R 디자이너)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)을 참조 하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>자동으로 생성된 형식을 반환하는 DataContext 메서드를 만들려면

1. **서버 탐색기** 또는 **데이터베이스 탐색기**에서 작업 하 고 있는 데이터베이스의 **저장 프로시저** 노드를 확장 합니다.

2. 원하는 저장 프로시저를 찾아 **O/R 디자이너**의 빈 영역으로 끕니다.

     자동으로 생성된 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어지고 **메서드** 창에 나타납니다.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>엔터티 클래스의 반환 형식을 갖는 DataContext 메서드를 만들려면

1. **서버 탐색기** 또는 **데이터베이스 탐색기**에서 작업 하 고 있는 데이터베이스의 **저장 프로시저** 노드를 확장 합니다.

2. 원하는 저장 프로시저를 찾아 **O/R 디자이너**의 기존 엔터티 클래스로 끌어 놓습니다.

     선택한 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어지고 **메서드** 창에 나타납니다.

> [!NOTE]
> 기존 반환 형식을 변경 하는 방법은 <xref:System.Data.Linq.DataContext> 메서드 참조 [방법: DataContext 메서드의 반환 형식 변경(O/R 디자이너)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)
- [연습: LINQ to SQL 클래스 만들기](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Basic의 LINQ 소개](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [C#의 LINQ](/dotnet/csharp/linq/linq-in-csharp)
