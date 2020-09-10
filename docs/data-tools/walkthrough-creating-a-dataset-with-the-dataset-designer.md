---
title: 데이터 세트 디자이너를 사용 하 여 데이터 집합 만들기
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 07d61ec32d48e5cb9b5421e397d743cd8c95b523
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742929"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>연습: 데이터 세트 디자이너을 사용 하 여 데이터 집합 만들기

이 연습에서는 **데이터 세트 디자이너**를 사용 하 여 데이터 집합을 만듭니다. 이 문서에서는 새 프로젝트를 만들고 새 프로젝트에 새 **데이터 집합** 항목을 추가 하는 과정을 안내 합니다. 마법사를 사용 하지 않고 데이터베이스의 테이블을 기반으로 테이블을 만드는 방법을 배웁니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다.

1. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 **Visual Studio 설치 관리자**를 통해 설치 합니다. Visual Studio 설치 관리자에서 SQL Server Express LocalDB는 **데이터 저장소 및 처리** 워크 로드의 일부로 설치 되거나 개별 구성 요소로 설치 될 수 있습니다.

2. 다음 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 **SQL Server 개체 탐색기** 창을 엽니다. SQL Server 개체 탐색기는 **데이터 저장소 및 처리** 워크 로드의 일부로 Visual Studio 설치 관리자에 설치 됩니다. **SQL Server** 노드를 확장 합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 선택 합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 를 클립보드에 복사 합니다. 이 T-sql 스크립트는 Northwind 데이터베이스를 처음부터 만들어 데이터로 채웁니다.

    3. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

       잠시 후 쿼리 실행이 완료 되 고 Northwind 데이터베이스가 만들어집니다.

## <a name="create-a-new-windows-forms-application-project"></a>새 Windows Forms 애플리케이션 프로젝트 만들기

1. Visual Studio의 **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

2. 왼쪽 창에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **Windows 데스크톱**을 선택 합니다.

3. 가운데 창에서 **Windows Forms 앱** 프로젝트 형식을 선택 합니다.

4. 프로젝트 이름을 **Datasetdesignerwalkthrough**로 지정한 다음 **확인**을 선택 합니다.

     Visual Studio는 **솔루션 탐색기** 에 프로젝트를 추가 하 고 디자이너에서 새 폼을 표시 합니다.

## <a name="add-a-new-dataset-to-the-application"></a>응용 프로그램에 새 데이터 집합 추가

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. 왼쪽 창에서 **데이터**를 선택한 다음 가운데 창에서 데이터 **집합** 을 선택 합니다.

3. 데이터 집합의 이름을 **NorthwindDataset**로 지정한 다음 **추가**를 선택 합니다.

     Visual Studio에서 **NorthwindDataset** 라는 파일을 프로젝트에 추가 하 고 **데이터 세트 디자이너**에서 엽니다.

## <a name="create-a-data-connection-in-server-explorer"></a>서버 탐색기에서 데이터 연결 만들기

1. **보기** 메뉴에서 **서버 탐색기**를 클릭합니다.

2. **서버 탐색기**에서 **데이터베이스에 연결** 단추를 클릭 합니다.

3. Northwind 샘플 데이터베이스에 대 한 연결을 만듭니다.

## <a name="create-the-tables-in-the-dataset"></a>데이터 집합에 테이블 만들기

이 섹션에서는 데이터 집합에 테이블을 추가 하는 방법에 대해 설명 합니다.

### <a name="to-create-the-customers-table"></a>Customers 테이블을 만들려면

1. **서버 탐색기**에서 만든 데이터 연결을 확장 한 다음 **테이블** 노드를 확장 합니다.

2. **서버 탐색기** 에서 **데이터 세트 디자이너**로 **Customers** 테이블을 끕니다.

     **Customers** 데이터 테이블과 **Customerstableadapter** 가 데이터 집합에 추가 됩니다.

### <a name="to-create-the-orders-table"></a>Orders 테이블을 만들려면

- **서버 탐색기** 에서 **데이터 세트 디자이너**로 **Orders** 테이블을 끌어 옵니다.

     **Customers** 테이블과 **Orders** 테이블 간의 **주문** 데이터 테이블, **orderstableadapter**및 데이터 관계가 데이터 집합에 추가 됩니다.

### <a name="to-create-the-orderdetails-table"></a>OrderDetails 테이블을 만들려면

- **서버 탐색기** 에서 **데이터 세트 디자이너**로 **주문 정보** 테이블을 끕니다.

     **Order Details** 데이터 테이블, **OrderDetailsTableAdapter**및 **Orders** 테이블과 **OrderDetails** 테이블 간의 데이터 관계가 데이터 집합에 추가 됩니다.

## <a name="next-steps"></a>다음 단계

- 데이터 집합을 저장 합니다.

- **데이터 소스** 창에서 항목을 선택 하 고 폼으로 끌어 놓습니다. 자세한 내용은 [Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)을 참조 하세요.

- Tableadapter에 쿼리를 추가 합니다.

- <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 데이터 집합에 있는 데이터 테이블의 또는 이벤트에 유효성 검사 논리를 추가 합니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [데이터의 유효성 검사](../data-tools/validate-data-in-datasets.md)
