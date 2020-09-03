---
title: '방법: 복수형 설정 및 해제(O-R 디자이너)'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6675a136b2bbdc1ef19d90ee19ecf7497053bfe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282049"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>방법: 복수형 설정 및 해제(O/R 디자이너)
기본적으로 이름이로 끝나는 데이터베이스 개체를 **서버 탐색기** 또는 **데이터베이스 탐색기** 에서 [Visual Studio의 LINQ to SQL 도구로](../data-tools/linq-to-sql-tools-in-visual-studio2.md)끌면 생성 된 엔터티 클래스의 이름이 복수형에서 단일로 변경 됩니다. 이렇게 하면 인스턴스화된 엔터티 클래스를 데이터의 단일 레코드에 매핑하는 것을 보다 정확하게 나타낼 수 있습니다. 예를 들어 `Customers` **O/R 디자이너** 에 테이블을 추가 하면 `Customer` 클래스에서 단일 고객에 대 한 데이터만 저장 하므로 라는 엔터티 클래스가 만들어집니다.

> [!NOTE]
> 복수 적용은 기본적으로 Visual Studio 영어 버전에만 적용됩니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>복수 적용을 설정 및 해제하려면

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **옵션** 대화 상자에서 **데이터베이스 도구**를 확장합니다.

    > [!NOTE]
    > **데이터베이스 도구** 노드가 표시되지 않은 경우에는 **모든 설정 표시**를 선택합니다.

3. **O/R 디자이너**를 클릭합니다.

4. **이름 복수화** 를 **사용**  =  **False** 로 설정 하 여 클래스 이름을 변경 하지 않도록 **O/R 디자이너** 를 설정 합니다.

5. **Pluralization of names** **Enabled**  =  **O/R 디자이너**에 추가 된 개체의 클래스 이름에 복수화 규칙을 적용 하려면 이름 복수화을 Enabled**True** 로 설정 합니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
