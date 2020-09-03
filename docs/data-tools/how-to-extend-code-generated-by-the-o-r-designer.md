---
title: '방법: O-R 디자이너에서 생성된 코드 확장'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b4c0ac8cff82250169171e1d842e64a34a4523ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282113"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>방법: O/R 디자이너에서 생성된 코드 확장
**O/R 디자이너** 에서 생성 한 코드는 디자이너 화면에서 엔터티 클래스 및 기타 개체가 변경 될 때 다시 생성 됩니다. 이러한 코드의 다시 생성으로 인해 일반적으로 디자이너에서 코드를 다시 생성하면 생성된 코드에 추가한 모든 코드를 덮어씁니다. **O/R 디자이너** 는 덮어쓰지 않는 코드를 추가할 수 있는 partial 클래스 파일을 생성 하는 기능을 제공 합니다. **O/R 디자이너** 에서 생성 된 코드에 사용자 고유의 코드를 추가 하는 한 가지 예는 LINQ to SQL (엔터티) 클래스에 데이터 유효성 검사를 추가 하는 것입니다. 자세한 내용은 [방법: 엔터티 클래스에 유효성 검사 추가](../data-tools/how-to-add-validation-to-entity-classes.md)를 참조 하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>엔터티 클래스에 코드 추가

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Partial 클래스를 만들고 엔터티 클래스에 코드를 추가하려면

1. **O/R 디자이너**에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다. **솔루션 탐색기** 또는 **데이터베이스 탐색기**에서 **.dbml** 파일을 두 번 클릭 합니다.

2. **O/R 디자이너**에서 유효성 검사를 추가할 클래스를 마우스 오른쪽 단추로 클릭한 다음, **코드 보기**를 클릭합니다.

     선택한 엔터티 클래스의 partial 클래스와 함께 코드 편집기가 열립니다.

3. 엔터티 클래스의 partial 클래스 선언에 사용자 코드를 추가합니다.

## <a name="add-code-to-a-datacontext"></a>DataContext에 코드 추가

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Partial 클래스를 만들고 DataContext에 코드를 추가하려면

1. **O/R 디자이너**에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다. **솔루션 탐색기** 또는 **데이터베이스 탐색기**에서 **.dbml** 파일을 두 번 클릭 합니다.

2. **O/R 디자이너**의 디자이너에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

     DataContext의 partial 클래스와 함께 코드 편집기가 열립니다.

3. DataContext의 partial 클래스 선언에 사용자 코드를 추가합니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습: LINQ to SQL 클래스 만들기(O-R 디자이너)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
