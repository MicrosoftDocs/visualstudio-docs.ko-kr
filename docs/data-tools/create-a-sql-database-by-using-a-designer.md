---
title: 데이터베이스 파일을 만들고 테이블 디자이너를 사용 합니다.
description: Visual Studio에서 테이블 디자이너를 사용 하 여 데이터베이스에 테이블 및 외래 키를 추가 하는 방법을 설명 하는 자습서입니다. 또한 그래픽 인터페이스를 통해 데이터를 추가 하는 방법을 보여 줍니다.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e31be90ff24f110fda66449187d3372976f269a7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282724"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>데이터베이스 만들기 및 Visual Studio에서 테이블 추가

Visual Studio를 사용 하 여 SQL Server Express LocalDB에서 로컬 데이터베이스 파일을 만들고 업데이트할 수 있습니다. Visual Studio의 **SQL Server 개체 탐색기** 도구 창에서 transact-sql 문을 실행 하 여 데이터베이스를 만들 수도 있습니다. 이 항목에서는 *.mdf* 파일을 만들고 테이블 디자이너를 사용 하 여 테이블 및 키를 추가 합니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료 하려면 Visual Studio에 설치 된 **.net 데스크톱 개발** 및 **데이터 저장소 및 처리** 작업을 수행 해야 합니다. 이를 설치 하려면 **Visual Studio 설치 관리자** 열고 수정 하려는 Visual Studio 버전 옆의 **수정 (또는** **추가**  >  **수정**)을 선택 합니다.

> [!NOTE]
> 이 문서의 절차는 .NET Core Windows Forms 프로젝트가 아닌 .NET Framework Windows Forms 프로젝트에만 적용 됩니다.

## <a name="create-a-project-and-a-local-database-file"></a>프로젝트 및 로컬 데이터베이스 파일 만들기

1. 새 **Windows Forms 앱 (.NET Framework)** 프로젝트를 만들고 이름을 **sampledatabasewalkthrough로**로 만듭니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. 항목 템플릿 목록에서 아래로 스크롤하여 **서비스 기반 데이터베이스**를 선택 합니다.

   ![항목 템플릿 대화 상자](../data-tools/media/raddata-vsitemtemplates.png)

4. 데이터베이스 이름을 **sampledatabase.mdf**로 지정한 다음 **추가**를 클릭 합니다.

### <a name="add-a-data-source"></a>데이터 원본 추가

1. **데이터 소스** 창이 열려 있지 않은 경우 **Shift** + **Alt** + **D** 를 누르거나 **View**  >  메뉴 모음에서**다른 창**  >  **데이터 원본** 보기를 선택 하 여 엽니다.

1. **데이터 소스** 창에서 **새 데이터 소스 추가**를 선택 합니다.

   ![Visual Studio에서 새 데이터 소스 추가](media/add-new-data-source.png)

   **데이터 원본 구성** 마법사가 열립니다.

1. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택 하 고 **다음**을 선택 합니다.

1. **데이터베이스 모델 선택** 페이지에서 **다음** 을 선택 하 여 기본값 (데이터 집합)을 적용 합니다.

1. **데이터 연결 선택** 페이지의 드롭다운 목록에서 **sampledatabase.mdf** 파일을 선택 하 고 **다음**을 선택 합니다.

1. **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 선택 합니다.

1. **데이터베이스 개체 선택** 페이지에서 데이터베이스에 개체가 포함 되어 있지 않다는 메시지가 표시 됩니다. **마침**을 선택합니다.

### <a name="view-properties-of-the-data-connection"></a>데이터 연결의 속성 보기

데이터 연결의 속성 창을 열어 *sampledatabase.mdf* 파일에 대 한 연결 문자열을 볼 수 있습니다.

- SQL Server 개체 탐색기 **보기**  >  **SQL Server Object Explorer** 를 선택 하 여 **SQL Server 개체 탐색기** 창을 엽니다. **(Localdb) \MSSQLLocalDB**  >  **데이터베이스**를 확장 한 다음 *sampledatabase.mdf* 를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

- 또는 **View**  >  해당 창이 아직 열려 있지 않은 경우**서버 탐색기**보기를 선택할 수 있습니다. **데이터 연결** 노드를 확장 하 고 *sampledatabase.mdf*를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 하 여 속성 창을 엽니다.

  > [!TIP]
  > 데이터 연결 노드를 확장할 수 없거나 Sampledatabase.mdf 연결이 목록에 없는 경우 서버 탐색기 도구 모음에서 **데이터베이스에 연결** 단추를 선택 합니다. **연결 추가** 대화 상자에서 **데이터 원본**아래에 **Microsoft SQL Server 데이터베이스 파일이** 선택 되어 있는지 확인 한 다음 sampledatabase.mdf 파일을 찾아 선택 합니다. **확인을**선택 하 여 연결 추가를 완료 합니다.

## <a name="create-tables-and-keys-by-using-table-designer"></a>테이블 디자이너를 사용 하 여 테이블 및 키 만들기

이 섹션에서는 두 개의 테이블, 각 테이블의 기본 키 및 몇 개의 샘플 데이터 행을 만듭니다. 또한 외래 키를 만들어 한 테이블의 레코드가 다른 테이블의 레코드에 해당 하는 방식을 지정 합니다.

### <a name="create-the-customers-table"></a>Customers 테이블 만들기

1. **서버 탐색기**에서 **데이터 연결** 노드를 확장 한 다음 **sampledatabase.mdf** 노드를 확장 합니다.

   데이터 연결 노드를 확장할 수 없거나 Sampledatabase.mdf 연결이 목록에 없는 경우 서버 탐색기 도구 모음에서 **데이터베이스에 연결** 단추를 선택 합니다. **연결 추가** 대화 상자에서 **데이터 원본**아래에 **Microsoft SQL Server 데이터베이스 파일이** 선택 되어 있는지 확인 한 다음 sampledatabase.mdf 파일을 찾아 선택 합니다. **확인을**선택 하 여 연결 추가를 완료 합니다.

2. **테이블** 을 마우스 오른쪽 단추로 클릭 하 고 **새 테이블 추가**를 선택 합니다.

   테이블 디자이너가 열리고 사용자가 만드는 테이블의 단일 열을 나타내는 한 개의 기본 행이 포함된 표가 표시됩니다. 표에 행을 추가하여 테이블에 열을 추가합니다.

3. 표에서 다음 각 항목에 대한 행을 추가합니다.

   |열 이름|데이터 형식|null 허용|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False(선택 취소)|
   |`CompanyName`|`nvarchar(50)`|False(선택 취소)|
   |`ContactName`|`nvarchar (50)`|True(선택)|
   |`Phone`|`nvarchar (24)`|True(선택)|

4. 행을 마우스 오른쪽 단추로 클릭 한 `CustomerID` 다음 **기본 키 설정**을 선택 합니다.

5. 기본 행 ()을 마우스 오른쪽 단추로 클릭 한 `Id` 다음 **삭제**를 선택 합니다.

6. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Customers 테이블 이름을 지정합니다.

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   다음과 유사한 결과가 표시됩니다.

   ![테이블 디자이너](../data-tools/media/table-designer.png)

7. **테이블 디자이너**의 왼쪽 위 모서리에서 **업데이트**를 선택 합니다.

8. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트**를 선택 합니다.

   Customers 테이블은 로컬 데이터베이스 파일에 생성 됩니다.

### <a name="create-the-orders-table"></a>Orders 테이블 만들기

1. 다른 테이블을 추가한 다음, 다음 표의 각 항목에 대한 행을 추가합니다.

   |열 이름|데이터 형식|null 허용|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False(선택 취소)|
   |`CustomerID`|`nchar(5)`|False(선택 취소)|
   |`OrderDate`|`datetime`|True(선택)|
   |`OrderQuantity`|`int`|True(선택)|

2. **OrderID** 를 기본 키로 설정한 다음 기본 행을 삭제 합니다.

3. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Orders 테이블 이름을 지정합니다.

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. **테이블 디자이너**의 왼쪽 위 모서리에서 **업데이트**를 선택 합니다.

5. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트**를 선택 합니다.

   Orders 테이블은 로컬 데이터베이스 파일에 생성 됩니다. 서버 탐색기의 **테이블** 노드를 확장 하면 다음 두 테이블이 표시 됩니다.

   ![테이블 노드가 서버 탐색기 확장 됨](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>외래 키 만들기

1. Orders 테이블의 테이블 디자이너 그리드 오른쪽에 있는 컨텍스트 창에서 **외래 키** 를 마우스 오른쪽 단추로 클릭 하 고 **새 외래 키 추가**를 선택 합니다.

   ![Visual Studio에서 테이블 디자이너의 외래 키 추가](../data-tools/media/add-foreign-key.png)

2. 표시 되는 텍스트 상자에서 **ToTable** 텍스트를 **고객**으로 바꿉니다.

3. T-sql 창에서 마지막 줄을 다음 샘플과 일치 하도록 업데이트 합니다.

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. **테이블 디자이너**의 왼쪽 위 모서리에서 **업데이트**를 선택 합니다.

5. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트**를 선택 합니다.

   외래 키가 생성 됩니다.

## <a name="populate-the-tables-with-data"></a>테이블을 데이터로 채우기

1. **서버 탐색기** 또는 **SQL Server 개체 탐색기**에서 예제 데이터베이스에 대 한 노드를 확장 합니다.

2. **테이블** 노드에 대 한 바로 가기 메뉴를 열고 **새로 고침**을 선택한 다음 **테이블** 노드를 확장 합니다.

3. Customers 테이블의 바로 가기 메뉴를 열고 **테이블 데이터 표시**를 선택 합니다.

4. 일부 고객에 게 필요한 모든 데이터를 추가 합니다.

    고객 ID를 5자로 지정할 수 있지만 나중에 이 절차에서 사용할 수 있도록 기억하기 쉬운 1자 정도를 선택하면 됩니다.

5. Orders 테이블에 대 한 바로 가기 메뉴를 열고 **테이블 데이터 표시**를 선택 합니다.

6. 일부 주문의 데이터를 추가 합니다.

    > [!IMPORTANT]
    > 모든 주문 ID와 주문 수량이 정수이고 각 고객 ID가 Customers 테이블의 **CustomerID** 열에 지정한 값과 일치하는지 확인합니다.

7. 메뉴 모음에서 **파일**  >  **모두 저장**을 선택 합니다.

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터 액세스](accessing-data-in-visual-studio.md)
