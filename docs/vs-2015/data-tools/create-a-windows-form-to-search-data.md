---
title: 데이터 검색을 위한 Windows Form 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670059"
---
# <a name="create-a-windows-form-to-search-data"></a>데이터 검색을 위한 Windows Form 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적인 애플리케이션 시나리오에서는 선택한 데이터를 폼에 표시합니다. 특정 고객의 주문이나 특정 주문의 정보를 표시하려는 경우를 예로 들 수 있습니다. 이 시나리오에서는 사용자가 폼에 정보를 입력하면 해당 사용자의 입력을 매개 변수로 사용하여 쿼리가 실행됩니다. 즉 매개 변수가 있는 쿼리를 기준으로 데이터가 선택됩니다. 쿼리는 사용자가 입력한 기준을 만족하는 데이터만 반환합니다. 이 연습에서는 특정 구/군/시의 고객을 반환하는 쿼리를 만들고 사용자 인터페이스를 수정하여, 사용자가 구/군/시 이름을 입력한 후 단추를 눌러 쿼리를 실행할 수 있도록 하는 방법을 보여줍니다.

 매개 변수가 있는 쿼리를 사용하면 데이터베이스가 레코드를 빠르게 필터링하도록 함으로써 애플리케이션의 효율성을 높일 수 있습니다. 반면 전체 데이터베이스 테이블을 요청하여 네트워크를 통해 전송한 다음, 애플리케이션 논리를 사용하여 원하는 레코드를 찾는 경우 애플리케이션의 속도와 효율성이 떨어질 수 있습니다.

 **검색 조건 작성기** 대화 상자를 사용 하 여 매개 변수가 있는 쿼리를 TableAdapter에 추가 하 고 매개 변수 값을 허용 하 고 쿼리를 실행 하는 컨트롤을 제어할 수 있습니다. **데이터** 메뉴 또는 TableAdapter 스마트 태그에서 **쿼리 추가** 명령을 선택하여 대화 상자를 엽니다.

 이 연습에서 설명하는 작업은 다음과 같습니다.

- 새 Windows Forms 응용 프로그램 프로젝트를 만듭니다.

- **데이터 소스 구성** 마법사를 사용 하 여 응용 프로그램에서 데이터 소스를 만들고 구성 합니다.

- **데이터 소스** 창에서 항목의 놓기 형식을 설정 합니다.

- **데이터 원본** 창에서 양식으로 항목을 끌어 데이터를 표시하는 컨트롤을 만듭니다.

- 폼에 데이터를 표시하기 위한 컨트롤을 추가합니다.

- **검색 조건 작성기** 대화 상자를 완료 합니다.

- 매개 변수를 폼에 입력 하 고 매개 변수가 있는 쿼리를 실행 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음 사항이 필요합니다.

- Northwind 샘플 데이터베이스에 대한 액세스.

## <a name="create-the-windows-application"></a>Windows 응용 프로그램 만들기
 첫 번째 단계는 **Windows 응용 프로그램**을 만드는 것입니다. 이 단계에서는 프로젝트에 이름을 지정할 수 있지만 나중에 저장할 수 있으므로 이름을 지정 합니다.

#### <a name="to-create-the-new-windows-application-project"></a>새 Windows 애플리케이션 프로젝트를 만들려면

1. **파일** 메뉴에서 새 프로젝트를 만듭니다.

2. 프로젝트 이름을 `WindowsSearchForm`로 지정합니다.

3. **Windows 응용 프로그램** 을 선택 하 고 **확인을**클릭 합니다.

     **WindowsSearchForm** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 이 단계에서는 **데이터 소스 구성** 마법사를 사용 하 여 데이터베이스에서 데이터 소스를 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다. Northwind 샘플 데이터베이스를 설정 하는 방법에 대 한 자세한 내용은 [Install SQL Server sample](../data-tools/install-sql-server-sample-databases.md)database을 참조 하세요.

#### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성** 마법사를 시작합니다.

3. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택하고 **다음**을 클릭합니다.

4. **데이터 연결 선택** 페이지에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

5. 데이터베이스에 암호가 필요하면 중요한 데이터를 포함하는 옵션을 선택한 후, **다음**을 클릭합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭 합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

8. **고객** 테이블을 선택한 다음, **마침**을 클릭합니다.

     **NorthwindDataSet**가 프로젝트에 추가되면 **고객** 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="create-the-form"></a> 폼 만들기
 **데이터 소스** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

#### <a name="to-create-data-bound-controls-on-the-form"></a>폼에서 데이터 바인딩된 컨트롤을 만들려면

1. **데이터 원본** 창에서 **Customers** 노드를 확장합니다.

2. **고객** 노드를 **데이터 원본** 창에서 양식으로 끌어옵니다.

     <xref:System.Windows.Forms.DataGridView>와 레코드 탐색에 사용되는 도구 스트립(<xref:System.Windows.Forms.BindingNavigator>)이 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.

## <a name="addparameterization-search-functionality-to-the-query"></a>쿼리에 addparameterization 변수화 (검색 기능)
 **검색 조건 작성기** 대화 상자를 사용 하 여 원래 쿼리에 WHERE 절을 추가할 수 있습니다.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>매개 변수가 있는 쿼리와 컨트롤을 만들어 매개 변수를 입력하려면

1. <xref:System.Windows.Forms.DataGridView> 컨트롤을 선택한 다음, **데이터** 메뉴에서 **쿼리 추가**를 선택합니다.

2. `FillByCity` **검색 조건 작성기** 대화 상자에서 **새 쿼리 이름** 영역을 입력 합니다.

3. 쿼리의 **쿼리 텍스트** 영역에 `WHERE City = @City`를 추가합니다.

     이 쿼리는 다음과 같아야 합니다.

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Access 및 OLE DB 데이터 원본은 물음표 ('? ')를 사용 하 여 매개 변수를 표시 하므로 WHERE 절은와 `WHERE City = ?` 같습니다.

4. **확인**을 클릭하여 **검색 조건 작성기** 대화 상자를 닫습니다.

     **FillByCityToolStrip**이 양식에 추가됩니다.

## <a name="testing-the-application"></a>애플리케이션 테스트
 애플리케이션을 실행하면 매개 변수를 입력으로 사용할 수 있는 폼이 열립니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. F5 키를 눌러 애플리케이션을 실행합니다.

2. **도시** 텍스트 상자에 **런던**을 입력한 다음, **FillByCity**를 클릭합니다.

     데이터 표는 조건을 충족 하는 고객으로 채워집니다. 이 예제의 데이터 표에는 **도시** 열의 값이 **런던**인 고객만 표시됩니다.

## <a name="next-steps"></a>다음 단계
 애플리케이션 요구 사항에 따라 매개 변수가 있는 폼을 만든 후 몇 단계를 더 수행해야 할 수도 있습니다. 이 연습에서 보완할 수 있는 사항은 다음과 같습니다.

- 관련 데이터를 표시하는 컨트롤을 추가합니다.

- 데이터 세트을 편집하여 데이터베이스 개체를 추가하거나 편집합니다. 자세한 내용은 [데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
