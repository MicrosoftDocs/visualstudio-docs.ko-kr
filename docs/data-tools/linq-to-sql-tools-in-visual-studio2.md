---
title: LINQ to SQL O/R 디자이너 개요
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 55f6fa2ad9eda2d701563d1fa99c76f5cd5c7c1d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282009"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Visual Studio의 LINQ to SQL 도구

LINQ to SQL은 Microsoft에서 릴리스된 최초의 개체 관계형 매핑 기술입니다. 이는 기본 시나리오에서 잘 작동 하며 Visual Studio에서 계속 지원 되지만 더 이상 개발 되지 않습니다. 이미 사용 하 고 있는 레거시 응용 프로그램을 유지 관리 하거나 SQL Server를 사용 하는 간단한 응용 프로그램에서 LINQ to SQL를 사용 하 고 다중 테이블 매핑이 필요 하지 않습니다. 일반적으로 개체 관계형 매퍼 계층이 필요한 경우 새 응용 프로그램은 Entity Framework를 사용 해야 합니다.

## <a name="install-the-linq-to-sql-tools"></a>LINQ to SQL 도구 설치

Visual Studio에서 **개체 관계형 디자이너** (**O/R 디자이너**)를 사용 하 여 SQL 테이블을 나타내는 LINQ to SQL 클래스를 만듭니다. O/R 디자이너는 .dbml 파일을 편집 하기 위한 UI입니다. 디자이너 화면을 사용 하 여 .dbml 파일을 편집 하려면 Visual Studio 작업의 일부로 기본적으로 설치 되지 않는 LINQ to SQL 도구가 필요 합니다.

LINQ to SQL 도구를 설치 하려면 Visual Studio 설치 관리자를 시작 하 고, **수정**을 선택 하 고, **개별 구성 요소** 탭을 선택한 다음, **코드 도구** 범주 아래에서 **LINQ to SQL 도구** 를 선택 합니다.

## <a name="what-is-the-or-designer"></a>O/R 디자이너 란?

**O/R 디자이너** 의 디자인 화면에는 왼쪽에 있는 엔터티 창과 오른쪽에 있는 메서드 창이 있습니다. 엔터티 창은 엔터티 클래스, 연결 및 상속 계층을 표시하는 기본 디자인 화면입니다. 메서드 창은 저장 프로시저와 함수에 매핑되는 <xref:System.Data.Linq.DataContext> 메서드를 표시하는 디자인 화면입니다.

**O/R 디자이너** 는 데이터베이스의 개체를 기반으로 하는 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) 엔터티 클래스 및 연결 (관계)을 만들기 위한 시각적 디자인 화면을 제공 합니다. 즉, **O/R 디자이너** 는 데이터베이스의 개체에 매핑되는 응용 프로그램에 개체 모델을 만듭니다. 또한 <xref:System.Data.Linq.DataContext> 엔터티 클래스와 데이터베이스 간에 데이터를 보내고 받는 강력한 형식의을 생성 합니다. 또한 **O/R 디자이너** 는 <xref:System.Data.Linq.DataContext> 데이터를 반환 하 고 엔터티 클래스를 채우기 위해 저장 프로시저 및 함수를 메서드에 매핑하는 기능을 제공 합니다. 마지막으로 **O/R 디자이너** 는 엔터티 클래스 간에 상속 관계를 디자인 하는 기능을 제공 합니다.

## <a name="open-the-or-designer"></a>O/R 디자이너 열기

LINQ to SQL 엔터티 모델을 프로젝트에 추가 **하려면 프로젝트**  >  **새 항목 추가**를 선택 하 고 프로젝트 항목 목록에서 **LINQ to SQL 클래스** 를 선택 합니다.

![LINQ to SQL 클래스](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio는 *.dbml* 파일을 만들어 솔루션에 추가 합니다. XML 매핑 파일 및 관련 코드 파일입니다.

![솔루션 탐색기의 LINQ to SQL 클래스](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

*.Dbml* 파일을 선택 하면 Visual Studio에서 모델을 시각적으로 만들 수 있도록 하는 **O/R 디자이너** 화면을 표시 합니다. 다음 그림에서는 Northwind `Customers` 및 `Orders` 테이블이 **서버 탐색기**에서 끌어온 후의 디자이너를 보여 줍니다. 테이블 간의 관계를 확인 합니다.

![LINQ to SQL 디자이너](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R 디자이너** 는 1:1 매핑 관계만 지 원하는 단순 개체 관계형 매퍼입니다. 즉, 엔터티 클래스는 데이터베이스 테이블 또는 뷰와 1:1 매핑 관계만 갖습니다. 엔터티 클래스를 조인 된 테이블에 매핑하는 등의 복잡 한 매핑은 지원 되지 않습니다. 복합 매핑에 Entity Framework를 사용 합니다. 또한 이 디자이너는 단방향 코드 생성기입니다. 이는 디자이너 화면에서 변경한 내용만이 코드 파일에 반영된다는 의미입니다. 코드 파일을 수동으로 변경 해도 **O/R 디자이너**에는 반영 되지 않습니다. 코드 파일에서 수동으로 변경한 모든 내용은 디자이너를 저장하고 코드를 다시 생성할 때 덮어쓰여집니다. 사용자 코드를 추가 하 여 생성 된 클래스를 확장 하는 방법에 대 한 자세한 합니다 **O/R 디자이너**를 참조 하세요 [방법: O/R 디자이너에서 생성한 코드 확장](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>DataContext 만들기 및 구성

프로젝트에 **LINQ to SQL 클래스** 항목을 추가 하 고 **O/R 디자이너**를 연 후 빈 디자인 화면은 구성할 준비가 된 빈를 나타냅니다 <xref:System.Data.Linq.DataContext> . 따라서 <xref:System.Data.Linq.DataContext>는 디자인 화면에 놓여진 첫째 항목에서 제공된 연결 정보를 사용하여 구성됩니다. 따라서 <xref:System.Data.Linq.DataContext>는 디자인 화면에 놓여진 첫째 항목의 연결 정보를 사용하여 구성됩니다. 클래스에 대 한 자세한 내용은 <xref:System.Data.Linq.DataContext> [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>데이터베이스 테이블 및 뷰에 매핑되는 엔터티 클래스 만들기

**서버 탐색기** 또는 **데이터베이스 탐색기** 의 데이터베이스 테이블 및 뷰를 **O/R 디자이너로**끌어와 테이블 및 뷰에 매핑되는 엔터티 클래스를 만들 수 있습니다. 이전 섹션에서 설명한 것처럼 <xref:System.Data.Linq.DataContext>는 디자인 화면으로 끌어온 첫 번째 항목에서 제공된 연결 정보를 사용하여 구성됩니다. 다른 연결을 사용 하는 후속 항목이 **O/R 디자이너**에 추가 된 경우에 대 한 연결을 변경할 수 있습니다 <xref:System.Data.Linq.DataContext> . 자세한 내용은 [방법: 테이블 및 뷰에 매핑된 LINQ to SQL 클래스 만들기 (O/R 디자이너)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)를 참조 하세요.

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>저장 프로시저 및 함수를 호출 하는 DataContext 메서드 만들기

<xref:System.Data.Linq.DataContext> **서버 탐색기** 또는 **데이터베이스 탐색기** 에서 **O/R 디자이너로**끌어 저장 프로시저 및 함수를 호출 하는 메서드를 만들 수 있습니다. 저장 프로시저 및 함수는 **O/R 디자이너** 에의 메서드로 추가 됩니다 <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> **서버 탐색기** 또는 **데이터베이스 탐색기** 의 저장 프로시저 및 함수를 **O/R 디자이너로**끌어 오면 생성 된 메서드의 반환 형식은 <xref:System.Data.Linq.DataContext> 항목을 끌어 놓은 위치에 따라 달라 집니다. 자세한 내용은 [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>저장 프로시저를 사용 하 여 엔터티 클래스와 데이터베이스 간에 데이터를 저장 하도록 DataContext 구성

앞에서 설명한 대로 저장 프로시저 및 함수를 호출하는 <xref:System.Data.Linq.DataContext> 메서드를 만들 수 있습니다. 또한 기본 LINQ to SQL 런타임 동작에 사용 되는 저장 프로시저를 할당 하 여 삽입, 업데이트 및 삭제를 수행할 수 있습니다. 자세한 내용은 [방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O/R 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)을 참조 하세요.

## <a name="inheritance-and-the-or-designer"></a>상속 및 O/R 디자이너

다른 개체와 마찬가지로 LINQ to SQL 클래스는 상속을 사용할 수 있고 다른 클래스에서 파생 될 수 있습니다. 데이터베이스에서 상속 관계는 여러 가지 방법으로 만들어집니다. **O/R 디자이너** 는 관계형 시스템에서 주로 구현 되는 단일 테이블 상속 개념을 지원 합니다. 자세한 내용은 [방법: O/R 디자이너를 사용 하 여 상속 구성](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)을 참조 하세요.

## <a name="linq-to-sql-queries"></a>LINQ to SQL 쿼리

**O/R 디자이너** 에서 만든 엔터티 클래스는 [LINQ (통합 언어 쿼리)](/dotnet/csharp/linq/)와 함께 사용 하도록 설계 되었습니다. 자세한 내용은 [방법: 정보 쿼리](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)를 참조 하세요.

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>생성 된 DataContext 및 엔터티 클래스 코드를 다른 네임 스페이스로 분리

**O/R 디자이너** 는에 **컨텍스트 네임 스페이스** 및 **엔터티 네임 스페이스** 속성을 제공 합니다 <xref:System.Data.Linq.DataContext> . 이들 속성은 <xref:System.Data.Linq.DataContext> 및 엔터티 클래스 코드가 어떤 네임스페이스로 생성되는지를 결정합니다. 기본적으로 이들 속성은 비어 있으며 <xref:System.Data.Linq.DataContext> 및 엔터티 클래스는 애플리케이션의 네임스페이스로 생성됩니다. 코드를 애플리케이션의 네임스페이스가 아닌 다른 네임스페이스로 생성하려면 **컨텍스트 네임스페이스** 및/또는 **엔터티 네임스페이스** 속성에 값을 입력합니다.

## <a name="reference-content"></a>참조 콘텐츠

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>참고 항목

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Faq (질문과 대답) (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
