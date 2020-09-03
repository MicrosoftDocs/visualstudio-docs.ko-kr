---
title: 데이터 클래스 상속(O-R 디자이너)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462397"
---
# <a name="data-class-inheritance-or-designer"></a>데이터 클래스 상속(O/R 디자이너)

다른 개체와 마찬가지로 LINQ to SQL 클래스는 상속을 사용할 수 있고 다른 클래스에서 파생 될 수 있습니다. 코드에서 클래스 하나가 다른 클래스에서 상속되도록 선언하여 개체 간의 상속 관계를 지정할 수 있습니다. 데이터베이스에서 상속 관계는 여러 가지 방법으로 만들어집니다. **개체 관계형 디자이너** (**O/R 디자이너**)는 관계형 시스템에서 주로 구현 되는 단일 테이블 상속 개념을 지원 합니다.

단일 테이블 상속에서는 기본 클래스와 파생 클래스의 열을 모두 포함하는 데이터베이스 테이블이 하나 있습니다. 관계형 데이터의 경우 판별자 열에는 해당 레코드가 어느 클래스에 속해 있는지를 판별하는 값이 포함됩니다. 예를 `Persons` 들어 회사에서 사용 하는 모든 사용자를 포함 하는 테이블이 있다고 가정 합니다. 어떤 사람들은 사원이고 어떤 사람들은 관리자입니다. `Persons`이 테이블에는 `Type` 관리자의 경우 값이 1이 고 직원의 값은 2 인 열이 포함 되어 있습니다. `Type`열이 판별자 열입니다. 이 시나리오에서는 직원의 서브 클래스를 만들고 값이 2 인 레코드로만 클래스를 채울 수 있습니다 `Type` .

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]를 사용하여 엔터티 클래스에서 상속을 구성하려면 상속 데이터가 들어 있는 단일 테이블을 디자이너에 두 번, 즉 상속 계층 구조의 각 클래스에 대해 테이블을 한 번씩 끌어 와야 합니다. 디자이너에 테이블을 추가한 후에는 **개체 관계형 디자이너** 도구 상자의 상속 항목을 사용하여 두 테이블을 연결한 다음, **속성** 창에서 네 가지 상속 속성을 설정합니다.

## <a name="inheritance-properties"></a>상속 속성

다음 표에는 상속 속성과 해당 설명이 나와 있습니다.

|속성|설명|
|--------------|-----------------|
|**Discriminator Property**|현재 레코드가 속해 있는 클래스를 결정하는 속성이며 열에 매핑됩니다.|
|**Base Class Discriminator Value**|**판별자 속성**으로 지정 된 열에서 레코드가 기본 클래스 임을 확인 하는 값입니다.|
|**Derived Class Discriminator Value**|**판별자 속성**으로 지정 된 속성에서 레코드가 파생 클래스 임을 확인 하는 값입니다.|
|**Inheritance Default**|**판별자 속성** 으로 지정 된 속성의 값이 **기본 클래스 판별자 값** 또는 **파생 클래스 판별자 값**과 일치 하지 않을 때 채워지는 클래스입니다.|

상속을 사용하고 관계형 데이터에 대응하는 개체 모델을 만드는 것은 다소 복잡할 수 있습니다. 이 항목에서는 상속을 구성하는 데 필요한 기본 개념과 개별 속성에 대한 정보를 제공합니다. 다음 항목에는 **O/R 디자이너**를 사용 하 여 상속을 구성 하는 방법에 대 한 자세한 설명이 나와 있습니다.

|항목|설명|
|-----------|-----------------|
|[방법: O/R 디자이너를 사용하여 상속 구성](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|**O/R 디자이너**를 사용 하 여 단일 테이블 상속을 사용 하는 엔터티 클래스를 구성 하는 방법을 설명 합니다.|
|[연습: 단일 테이블 상속을 사용하여 LINQ to SQL 클래스 만들기(O/R 디자이너)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|**O/R 디자이너**를 사용 하 여 단일 테이블 상속을 사용 하는 엔터티 클래스를 구성 하는 방법에 대 한 단계별 지침을 제공 합니다.|

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습: LINQ to SQL 클래스 만들기(O-R 디자이너)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [연습: 단일 테이블 상속을 사용하여 LINQ to SQL 클래스 만들기(O/R 디자이너)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [시작](/dotnet/framework/data/adonet/sql/linq/getting-started)