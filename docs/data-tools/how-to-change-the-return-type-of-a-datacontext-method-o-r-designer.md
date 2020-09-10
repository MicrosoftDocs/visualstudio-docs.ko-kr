---
title: DataContext 메서드의 반환 형식 변경
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b40851323efdf3c2cbf0900ae323f3c9c0a1ec17
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89737045"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>방법: DataContext 메서드의 반환 형식 변경(O/R 디자이너)
저장 프로시저 또는 함수를 <xref:System.Data.Linq.DataContext> 기반으로 만들어진 메서드의 반환 형식은 **O/R 디자이너**에서 저장 프로시저 또는 함수를 놓는 위치에 따라 달라 집니다. 저장 프로시저 또는 함수에서 반환된 데이터의 스키마가 엔터티 클래스의 모양과 일치하는 경우 항목을 기존 엔터티 클래스에 직접 드롭하면 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. 항목을 **O/R 디자이너**의 빈 영역에 놓으면 <xref:System.Data.Linq.DataContext> 자동으로 생성 된 형식을 반환 하는 메서드가 만들어집니다. 메서드 창에 추가한 후 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 변경할 수 있습니다. <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 검사하거나 변경하려면 해당 메서드를 선택하고 **속성** 창에서 **반환 형식** 속성을 클릭합니다.

> [!NOTE]
> 반환 형식을 엔터티 클래스로 설정한 <xref:System.Data.Linq.DataContext> 메서드를 **속성** 창을 사용하여 자동 생성된 형식을 반환하도록 되돌릴 수 없습니다. <xref:System.Data.Linq.DataContext>자동 생성 된 형식을 반환 하도록 메서드를 되돌리려면 원래 데이터베이스 개체를 **O/R 디자이너로** 다시 끌어와 야 합니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>DataContext 메서드의 반환 형식을 자동으로 생성된 형식에서 엔터티 클래스로 변경하려면

1. 메서드 창에서 <xref:System.Data.Linq.DataContext> 메서드를 선택합니다.

2. **속성** 창에서 **반환 형식**을 선택한 다음, **반환 형식** 목록에서 사용 가능한 엔터티 클래스를 선택합니다. 원하는 엔터티 클래스가 목록에 없으면 **O/R 디자이너** 에서 추가 하거나 만들어 목록에 추가 합니다.

3. *.dbml* 파일을 저장합니다.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>DataContext 메서드의 반환 형식을 엔터티 클래스에서 자동으로 생성된 형식으로 다시 변경하려면

1. 메서드 <xref:System.Data.Linq.DataContext> 창에서 메서드를 **Methods** 선택 하 고 삭제 합니다.

2. **서버 탐색기** 또는 **데이터베이스 탐색기** 의 데이터베이스 개체를 **O/R 디자이너**의 빈 영역으로 끕니다.

3. *.dbml* 파일을 저장합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)
- [방법: 저장 프로시저 및 함수에 매핑된 DataContext 메서드 만들기(O/R 디자이너)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
