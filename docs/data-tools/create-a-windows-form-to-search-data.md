---
title: 데이터 검색을 위한 Windows Form 만들기
description: Windows Form을 만들어 데이터를 검색하는 방법의 예제를 읽어보십시오. Windows Form 애플리케이션, 데이터 원본 및 양식을 만듭니다. 매개 변수화를 추가합니다. 앱을 테스트합니다.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ce9d3eeebf42855ad69f02b2d72330190a2b390
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761097"
---
# <a name="create-a-windows-form-to-search-data"></a>데이터 검색을 위한 Windows Form 만들기

일반적인 애플리케이션 시나리오에서는 선택한 데이터를 폼에 표시합니다. 특정 고객의 주문이나 특정 주문의 정보를 표시하려는 경우를 예로 들 수 있습니다. 이 시나리오에서는 사용자가 폼에 정보를 입력하면 해당 사용자의 입력을 매개 변수로 사용하여 쿼리가 실행됩니다. 즉 매개 변수가 있는 쿼리를 기준으로 데이터가 선택됩니다. 쿼리는 사용자가 입력한 기준을 만족하는 데이터만 반환합니다. 이 연습에서는 특정 구/군/시의 고객을 반환하는 쿼리를 만들고 사용자 인터페이스를 수정하여, 사용자가 구/군/시 이름을 입력한 후 단추를 눌러 쿼리를 실행할 수 있도록 하는 방법을 보여줍니다.

매개 변수가 있는 쿼리를 사용하면 데이터베이스가 레코드를 빠르게 필터링하도록 함으로써 애플리케이션의 효율성을 높일 수 있습니다. 반면 전체 데이터베이스 테이블을 요청하여 네트워크를 통해 전송한 다음, 애플리케이션 논리를 사용하여 원하는 레코드를 찾는 경우 애플리케이션의 속도와 효율성이 떨어질 수 있습니다.

**검색 조건 작성기** 대화 상자를 사용하여 매개 변수가 있는 쿼리를 모든 TableAdapter(및 컨트롤에 추가하여 매개 변수 값을 수락하고 쿼리를 실행할 수 있음)할 수 있습니다. **데이터** 메뉴 또는 TableAdapter 스마트 태그에서 **쿼리 추가** 명령을 선택하여 대화 상자를 엽니다.

이 연습에서 설명하는 작업은 다음과 같습니다.

- 데이터 원본 구성 마법사를 통해 애플리케이션에서 **데이터 원본** 만들기 및 구성

- **데이터 원본** 창에서 항목의 놓기 유형 설정

- **데이터 원본** 창에서 양식으로 항목을 끌어 데이터를 표시하는 컨트롤을 만듭니다.

- 폼에 데이터를 표시하기 위한 컨트롤을 추가합니다.

- **검색 조건 작성기** 대화 상자를 완료합니다.

- 폼에 매개 변수를 입력하고 매개 변수가 있는 쿼리를 실행합니다.

> [!NOTE]
> 이 문서의 절차는 .NET Core Windows Forms 프로젝트가 아닌 .NET Framework Windows Forms 프로젝트에만 적용됩니다.

## <a name="prerequisites"></a>필수 구성 요소

데이터 스토리지 **및 처리** 워크로드가 설치되어 있어야 합니다. [Visual Studio 수정](../install/modify-visual-studio.md)을 참조하세요.

이 연습에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용합니다.

1. SQL Server Express LocalDB가 없는 경우 SQL Server Express 다운로드 페이지 또는 [Visual Studio 설치 관리자](https://www.microsoft.com/sql-server/sql-server-editions-express)통해 설치합니다.  **Visual Studio 설치 관리자** SQL Server Express LocalDB를 **데이터 스토리지 및 처리** 워크로드의 일부로 설치하거나 개별 구성 요소로 설치할 수 있습니다.

2. 다음 단계에 따라 Northwind 샘플 데이터베이스를 설치합니다.

    1. Visual Studio **SQL Server 개체 탐색기** 창을 엽니다. (SQL Server 개체 탐색기 Visual Studio 설치 관리자 **데이터 스토리지 및 처리** 워크로드의 일부로 설치됩니다.) **SQL Server** 노드를 확장합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭하고 **새 쿼리** 를 선택합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind Transact-SQL 스크립트를](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 복사합니다. 이 T-SQL 스크립트는 처음부터 Northwind 데이터베이스를 만들고 데이터로 채웁다.

    3. T-SQL 스크립트를 쿼리 편집기 에 붙여넣은 **다음, 실행** 단추를 선택합니다.

       잠시 후 쿼리 실행이 완료되고 Northwind 데이터베이스가 만들어집니다.

## <a name="create-the-windows-forms-application"></a>Windows Forms 애플리케이션 만들기

:::moniker range="vs-2017"

C# 또는 Visual Basic 대한 **새 Windows Forms 앱(.NET Framework)** 프로젝트를 만듭니다. 프로젝트 이름을 **WindowsSearchForm** 로 지정합니다.

## <a name="create-the-data-source"></a>데이터 원본 생성

이 단계에서는 **데이터 원본 구성** 마법사를 사용하여 데이터베이스에서 데이터 원본을 만듭니다.

1. **데이터 원본** 창을 열려면 **데이터** 메뉴에서 데이터 **원본 표시를 클릭합니다.**

2. **데이터 원본** 창에서 **새 데이터 원본 추가** 를 선택하여 **데이터 원본 구성** 마법사를 시작합니다.

3. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택하고 **다음** 을 클릭합니다.

4. 데이터 연결 선택 페이지에서 다음 중 하나를 **수행합니다.**

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결** 을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

5. 데이터베이스에 암호가 필요하면 중요한 데이터를 포함하는 옵션을 선택한 후, **다음** 을 클릭합니다.

6. 애플리케이션 **구성 파일에 연결 문자열 저장** 페이지에서 **다음을** 클릭합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

8. **고객** 테이블을 선택한 다음, **마침** 을 클릭합니다.

     **NorthwindDataSet** 가 프로젝트에 추가되면 **고객** 테이블이 **데이터 원본** 창에 나타납니다.

:::moniker-end

:::moniker range=">=vs-2019"

C# 또는 Visual Basic 대한 **새 Windows Forms 앱(.NET Framework)** 프로젝트를 만듭니다. 프로젝트 이름을 **WindowsSearchForm** 로 지정합니다.

## <a name="create-the-data-source"></a>데이터 원본 생성

이 단계에서는 **데이터 원본 구성** 마법사를 사용하여 데이터베이스에서 데이터 원본을 만듭니다.

1. **데이터 원본** 창을 열려면 빠른 검색(Ctrl Q)을 사용하고 + 데이터 원본 **을 검색합니다.**

1. **데이터 원본** 창에서 **새 데이터 원본 추가** 를 선택하여 **데이터 원본 구성** 마법사를 시작합니다.

1. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택하고 **다음** 을 클릭합니다.

1. 데이터베이스 **모델 선택** 화면에서 **데이터 세트** 를 선택한 후 **다음을** 클릭합니다.

1. 데이터 연결 선택 페이지에서 다음 중 하나를 **수행합니다.**

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결** 을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

1. 애플리케이션 **구성 파일에 연결 문자열 저장** 페이지에서 **다음을** 클릭합니다.

1. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

1. **고객** 테이블을 선택한 다음, **마침** 을 클릭합니다.

     **NorthwindDataSet** 가 프로젝트에 추가되면 **고객** 테이블이 **데이터 원본** 창에 나타납니다.

:::moniker-end

## <a name="create-the-form"></a> 폼 만들기

**데이터 원본** 창에서 양식으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

1. Windows Forms 디자이너에 활성 포커스가 있고 데이터 원본 창이 열려 있고 고정되어 있는지 **확인합니다.**

1. **데이터 원본** 창에서 **Customers** 노드를 확장합니다.

1. **고객** 노드를 **데이터 원본** 창에서 양식으로 끌어옵니다.

     <xref:System.Windows.Forms.DataGridView>와 레코드 탐색에 사용되는 도구 스트립(<xref:System.Windows.Forms.BindingNavigator>)이 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.

## <a name="add-parameterization-search-functionality-to-the-query"></a>쿼리에 매개 변수화(검색 기능) 추가

**검색 조건 작성기** 대화 상자를 사용하여 원래 쿼리에 WHERE 절을 추가할 수 있습니다.

1. 양식의 디자인 표면 바로 아래에서 **customersTableAdapter** 단추를 선택한 다음, **속성** 창에서 **쿼리 추가...** 를 선택합니다.

2. **검색 조건 작성기** 대화 상자의 **새 쿼리 이름** 영역에 **FillByCity를** 입력합니다.

3. 쿼리의 **쿼리 텍스트** 영역에 `WHERE City = @City`를 추가합니다.

     이 쿼리는 다음과 같아야 합니다.

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > 액세스 및 OLE DB 데이터 원본은 물음표('?')를 사용하여 매개 변수를 나타내므로 WHERE 절은 와 `WHERE City = ?` 같습니다.

4. **확인** 을 클릭하여 **검색 조건 작성기** 대화 상자를 닫습니다.

     **FillByCityToolStrip** 이 양식에 추가됩니다.

## <a name="test-the-application"></a>애플리케이션 테스트

애플리케이션을 실행하면 폼이 열리고 매개 변수를 입력으로 사용할 준비가 됩니다.

1. **F5** 키를 눌러 애플리케이션을 실행합니다.

2. **도시** 텍스트 상자에 **런던** 을 입력한 다음, **FillByCity** 를 클릭합니다.

     데이터 그리드는 조건을 충족하는 고객으로 채워집니다. 이 예제의 데이터 표에는 **도시** 열의 값이 **런던** 인 고객만 표시됩니다.

## <a name="next-steps"></a>다음 단계

애플리케이션 요구 사항에 따라 매개 변수가 있는 폼을 만든 후 몇 단계를 더 수행해야 할 수도 있습니다. 이 연습에서 보완할 수 있는 사항은 다음과 같습니다.

- 관련 데이터를 표시하는 컨트롤을 추가합니다. 자세한 내용은 [데이터 세트의 관계를 참조하세요.](relationships-in-datasets.md)

- 데이터 세트을 편집하여 데이터베이스 개체를 추가하거나 편집합니다. 자세한 내용은 [데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조하세요.

## <a name="see-also"></a>참조

- [Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
