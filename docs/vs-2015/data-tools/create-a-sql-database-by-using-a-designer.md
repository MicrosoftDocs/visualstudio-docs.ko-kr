---
title: 디자이너를 사용 하 여 SQL 데이터베이스 만들기 | Microsoft Docs
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651053"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>디자이너를 사용하여 SQL 데이터베이스 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio를 사용 하 여 SQL Server Express LocalDB에서 로컬 데이터베이스 파일을 만들고 업데이트 하 여 테이블 추가 및 열 정의와 같은 기본적인 작업을 탐색할 수 있습니다. 이 연습을 마친 후 로컬 데이터베이스를 사용하여 고급 기능을 알아보고 다른 연습을 미리 준비할 수 있습니다.

 Visual Studio의 **SQL Server 개체 탐색기** 도구 창에서 SQL Server Management Studio (별도 다운로드) 또는 transact-sql 문을 사용 하 여 데이터베이스를 만들 수도 있습니다.

 이 연습에서는 다음 작업을 수행하는 방법을 알아봅니다.

- [프로젝트 및 로컬 데이터베이스 파일 만들기](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [테이블, 열, 기본 키 및 외래 키 만들기](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [테이블을 데이터로 채우기](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 SQL Server Data Tools 설치 되어 있는지 확인 합니다. **보기** 메뉴에 **SQL Server 개체 탐색기**표시 되어야 합니다. 표시 되지 않는 경우 **프로그램 추가/제거**로 이동 하 고, **Visual Studio 2015**을 클릭 하 고, **변경**을 선택 하 고 **SQL Server Data Tools**옆의 상자를 선택 합니다.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> 프로젝트 및 로컬 데이터베이스 파일 만들기

#### <a name="to-create-a-project-and-a-database-file"></a>프로젝트 및 데이터베이스 파일을 만들려면

1. 이라는 Windows Forms 프로젝트를 만듭니다 `SampleDatabaseWalkthrough` .

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. 항목 템플릿 목록에서 아래로 스크롤하여 **서비스 기반 데이터베이스**를 선택 합니다.

    ![항목 템플릿 대화 상자](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. 데이터베이스 이름을 **sampledatabase.mdf**로 지정한 다음 **추가** 단추를 선택 합니다.

5. **데이터 소스** 창이 열려 있지 않으면 Shift + Alt + D 키를 선택 하거나 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 소스**보기를 선택 하 여 엽니다.

6. **데이터 소스** 창에서 **새 데이터 소스 추가** 링크를 선택 합니다.

7. **데이터 소스 구성 마법사**에서 **다음** 단추를 네 번 선택 하 여 기본 설정을 적용 한 다음 **마침** 단추를 선택 합니다.

   데이터베이스의 속성 창을 열어 연결 문자열 및 기본 .mdf 파일 위치를 볼 수 있습니다. 데이터베이스 파일이 프로젝트 폴더에 있는 것을 볼 수 있습니다.

- Visual Studio에서 **View**  >  창이 아직 열려 있지 않은 경우**SQL Server 개체 탐색기** 보기를 선택 합니다. **데이터 연결** 노드를 확장 하 고 sampledatabase.mdf에 대 한 바로 가기 메뉴를 연 다음 **속성**을 선택 하 여 속성 창을 엽니다.

- 또는 **View**  >  해당 창이 아직 열려 있지 않은 경우**서버 탐색기**보기를 선택할 수 있습니다. **데이터 연결** 노드를 확장 하 여 속성 창을 엽니다. Sampledatabase.mdf에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> 테이블, 열, 기본 키 및 외래 키 만들기
 이 단원에서는 몇 가지 테이블과 각 테이블의 기본 키 그리고 몇 행의 샘플 데이터를 만들어야 합니다. 다음 연습에서는 애플리케이션에서 이 정보를 표시하는 방법을 배웁니다. 또한 외래 키를 만들어 한 테이블의 레코드가 다른 테이블의 레코드에 해당하는 방식을 지정할 수 있습니다.

#### <a name="to-create-the-customers-table"></a>Customers 테이블을 만들려면

1. **서버 탐색기** 또는 **SQL Server 개체 탐색기**에서 **데이터 연결** 노드를 확장 한 다음 **sampledatabase.mdf** 노드를 확장 합니다.

2. **테이블**에 대 한 바로 가기 메뉴를 열고 **새 테이블 추가**를 선택 합니다.

     **테이블 디자이너**가 열리고 사용자가 만드는 테이블의 단일 열을 나타내는 한 개의 기본 행이 포함된 표가 표시됩니다. 표에 행을 추가하여 테이블에 열을 추가합니다.

3. 표에서 다음 각 항목에 대한 행을 추가합니다.

    |열 이름|데이터 형식|null 허용|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False(선택 취소)|
    |`CompanyName`|`nvarchar(50)`|False(선택 취소)|
    |`ContactName`|`nvarchar (50)`|True(선택)|
    |`Phone`|`nvarchar (24)`|True(선택)|

4. 행에 대 한 바로 가기 메뉴를 열고 `CustomerID` **기본 키 설정**을 선택 합니다.

5. 기본 행에 대 한 바로 가기 메뉴를 열고 **삭제**를 선택 합니다.

6. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Customers 테이블 이름을 지정합니다.

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     다음과 비슷한 결과가 표시됩니다.

     ![테이블 디자이너](../data-tools/media/raddata-table-designer.png "raddata 테이블 디자이너")

7. **테이블 디자이너**의 왼쪽 위 모퉁이에 있는 **업데이트** 단추를 선택 합니다.

8. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트** 단추를 선택 합니다.

     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.

#### <a name="to-create-the-orders-table"></a>Orders 테이블을 만들려면

1. 다른 테이블을 추가한 다음, 다음 표의 각 항목에 대한 행을 추가합니다.

    |열 이름|데이터 형식|null 허용|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False(선택 취소)|
    |`CustomerID`|`nchar(5)`|False(선택 취소)|
    |`OrderDate`|`datetime`|True(선택)|
    |`OrderQuantity`|`int`|True(선택)|

2. **OrderID** 를 기본 키로 설정한 다음 기본 행을 삭제 합니다.

3. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Orders 테이블 이름을 지정합니다.

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. **테이블 디자이너**의 왼쪽 위 모퉁이에 있는 **업데이트** 단추를 선택 합니다.

5. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트** 단추를 선택 합니다.

     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.

#### <a name="to-create-a-foreign-key"></a>외래 키를 만들려면

1. 표 오른쪽의 컨텍스트 창에서 **외래 키**에 대 한 바로 가기 메뉴를 열고 다음 그림과 같이 **새 외래 키 추가**를 선택 합니다.

     ![테이블 디자이너에서 외래 키 추가하기](../data-tools/media/foreignkey.png "ForeignKey")

2. 표시 되는 텍스트 상자에서 **ToTable** 를로 바꿉니다 `Customers` .

3. T-sql 창에서 마지막 줄을 다음 샘플과 일치 하도록 업데이트 합니다.

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. **테이블 디자이너**의 왼쪽 위 모퉁이에 있는 **업데이트** 단추를 선택 합니다.

5. **데이터베이스 업데이트 미리 보기** 대화 상자에서 **데이터베이스 업데이트** 단추를 선택 합니다.

     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> 테이블을 데이터로 채우기

#### <a name="to-populate-the-tables-with-data"></a>테이블을 데이터로 채우려면

1. **서버 탐색기** 또는 **SQL Server 개체 탐색기**에서 예제 데이터베이스에 대 한 노드를 확장 합니다.

2. **테이블** 노드에 대 한 바로 가기 메뉴를 열고 **새로 고침**을 선택한 다음 **테이블** 노드를 확장 합니다.

3. Customers 테이블의 바로 가기 메뉴를 열고 **테이블 데이터 표시**를 선택 합니다.

4. 세 명 이상의 고객에 대해 원하는 모든 데이터를 추가합니다.

     고객 ID를 5자로 지정할 수 있지만 나중에 이 절차에서 사용할 수 있도록 기억하기 쉬운 1자 정도를 선택하면 됩니다.

5. Orders 테이블에 대 한 바로 가기 메뉴를 열고 **테이블 데이터 표시**를 선택 합니다.

6. 세 개 이상의 주문에 대한 데이터를 추가합니다.

    > [!IMPORTANT]
    > 모든 주문 ID와 주문 수량이 정수이고 각 고객 ID가 Customers 테이블의 CustomerID 열에 지정한 값과 일치하는지 확인합니다.

7. 메뉴 모음에서 **파일**  >  **모두 저장**을 선택 합니다.

8. 메뉴 모음에서 **파일**  >  **솔루션 닫기**를 선택 합니다.

    > [!NOTE]
    > 가장 좋은 방법은 만든 데이터베이스 파일을 복사한 후 복사본을 다른 위치에 붙여 넣거나 복사본에 다른 이름을 지정하여 데이터베이스 파일을 백업하는 것입니다.

## <a name="next-steps"></a>다음 단계
 이제 일부 샘플 데이터가 포함 된 로컬 데이터베이스 파일이 있으므로 데이터베이스 작업을 보여 주는 모든 연습을 완료할 수 있습니다.
