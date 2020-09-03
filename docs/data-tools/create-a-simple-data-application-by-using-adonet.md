---
title: ADO.NET을 사용하여 간단한 데이터 애플리케이션 만들기
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8f35173ded1ba4d52e0c5a9800fa228a7f93b981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586876"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET을 사용하여 간단한 데이터 애플리케이션 만들기

데이터베이스의 데이터를 조작하는 애플리케이션을 만들면 연결 문자열 정의, 데이터 삽입 및 저장 프로시저 실행과 같은 기본 작업을 수행합니다. 이 항목의 내용에 따라 Visual c # 또는 Visual Basic 및 ADO.NET를 사용 하 여 간단한 Windows Forms "데이터 폼" 응용 프로그램 내에서 데이터베이스와 상호 작용 하는 방법을 알아볼 수 있습니다.  데이터 집합, LINQ to SQL 및 Entity Framework를 비롯 한 모든 .NET 데이터 기술은 궁극적으로이 문서에 표시 된 것과 매우 유사한 단계를 수행 합니다.

이 문서에서는 빠른 방법으로 데이터베이스에서 데이터를 가져오는 간단한 방법을 보여 줍니다. 응용 프로그램에서 중요 하지 않은 방법으로 데이터를 수정 하 고 데이터베이스를 업데이트 해야 하는 경우 Entity Framework 사용을 고려 하 고 데이터 바인딩을 사용 하 여 사용자 인터페이스 컨트롤을 기본 데이터의 변경 내용에 자동으로 동기화 해야 합니다.

> [!IMPORTANT]
> 코드를 간단히 유지하기 위해 프로덕션에 사용하는 예외 처리는 포함되어 있지 않습니다.

## <a name="prerequisites"></a>필수 구성 요소

애플리케이션을 만들려면 다음이 필요 합니다.

- Visual Studio.

- SQL Server Express LocalDB. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 설치할 수 있습니다.

이 항목에서는 사용자가 Visual Studio IDE의 기본 기능에 대해 잘 알고 있는 것으로 가정 하 고, 프로젝트에 폼을 추가 하 고, 폼에 단추 및 기타 컨트롤을 추가 하 고, 컨트롤의 속성을 설정 하 고, 간단한 이벤트를 코딩 하 여 Windows Forms 응용 프로그램을 만듭니다. 이러한 작업에 익숙하지 않은 경우이 연습을 시작 하기 전에 [Visual c # 및 Visual Basic 시작](../ide/quickstart-visual-basic-console.md) 항목을 완료 하는 것이 좋습니다.

## <a name="set-up-the-sample-database"></a>샘플 데이터베이스 설정

다음 단계를 수행 하 여 예제 데이터베이스를 만듭니다.

1. Visual Studio에서 **서버 탐색기** 창을 엽니다.

2. **데이터 연결** 을 마우스 오른쪽 단추로 클릭 하 고 **새 SQL Server 데이터베이스 만들기**를 선택 합니다.

3. **서버 이름** 텍스트 상자에 **(localdb) \mssqllocaldb**를 입력 합니다.

4. **새 데이터베이스 이름** 텍스트 상자에 **Sales**를 입력 한 다음 **확인**을 선택 합니다.

     빈 **Sales** 데이터베이스가 만들어지고 서버 탐색기의 데이터 연결 노드에 추가 됩니다.

5. **Sales** 데이터 연결을 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 선택 합니다.

     쿼리 편집기 창이 열립니다.

6. [Sales transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) 를 클립보드에 복사 합니다.

7. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

     잠시 후 쿼리 실행이 완료 되 고 데이터베이스 개체가 만들어집니다. 데이터베이스에는 Customer와 Orders 라는 두 개의 테이블이 있습니다. 이러한 테이블은 처음에는 데이터를 포함 하지 않지만 만들 응용 프로그램을 실행할 때 데이터를 추가할 수 있습니다. 데이터베이스에는 네 개의 간단한 저장 프로시저도 있습니다.

## <a name="create-the-forms-and-add-controls"></a>폼 만들기 및 컨트롤 추가

1. Windows Forms 애플리케이션의 프로젝트를 만든 다음, 이름을 **SimpleDataApp**으로 지정합니다.

    Visual Studio에서는 프로젝트와 **Form1**이라는 빈 Windows 양식을 포함한 여러 파일을 만듭니다.

2. 프로젝트에 두 개의 Windows 양식을 추가하여 총 세 개의 양식을 만든 다음, 다음 이름을 지정합니다.

   - **탐색**

   - **NewCustomer**

   - **FillOrCancel**

3. 각 폼에 대해 다음 그림에 나오는 텍스트 상자, 단추 및 기타 컨트롤을 추가합니다. 각 컨트롤에 대해 테이블이 설명하는 속성을 설정합니다.

   > [!NOTE]
   > 그룹 상자 및 레이블 컨트롤도 선명성을 더해 주지만 코드에서는 사용하지 않습니다.

   **탐색 양식**

   ![검색 대화 상자](../data-tools/media/simpleappnav.png)

|Navigation 폼 컨트롤|속성|
| - |----------------|
|단추|Name = btnGoToAdd|
|단추|Name = btnGoToFillOrCancel|
|단추|Name = btnExit|

**NewCustomer 양식**

![새 고객을 추가하고 주문하기](../data-tools/media/simpleappnewcust.png)

|NewCustomer 폼 컨트롤|속성|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|단추|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|단추|Name = btnPlaceOrder|
|단추|Name = btnAddAnotherAccount|
|단추|Name = btnAddFinish|

**FillOrCancel 양식**

![주문 입력 또는 취소](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel 폼 컨트롤|속성|
| - |----------------|
|TextBox|Name = txtOrderID|
|단추|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|단추|Name = btnCancelOrder|
|단추|Name = btnFillOrder|
|단추|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>연결 문자열 저장
애플리케이션이 데이터베이스에 대한 연결을 열려면 애플리케이션에는 연결 문자열에 액세스할 수 있어야 합니다. 각 폼에 문자열을 수동으로 입력 하지 않도록 하려면 프로젝트의 *App.config* 파일에 문자열을 저장 하 고, 응용 프로그램의 모든 폼에서 메서드가 호출 될 때 문자열을 반환 하는 메서드를 만듭니다.

**서버 탐색기** 에서 **판매** 데이터 연결을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 하 여 연결 문자열을 찾을 수 있습니다. **ConnectionString** 속성을 찾은 다음 **ctrl** + **A**, **ctrl** + **C** 를 사용 하 여 문자열을 선택 하 고 클립보드에 복사 합니다.

1. C #을 사용 하는 경우 **솔루션 탐색기**에서 프로젝트의 **속성** 노드를 확장 한 다음 **설정** 파일을 엽니다.
    Visual Basic를 사용 하는 경우 **솔루션 탐색기**에서 **모든 파일 표시**를 클릭 하 고 **내 프로젝트** 노드를 확장 한 다음 **설정** 파일을 엽니다.

2. **이름** 열에을 입력 `connString` 합니다.

3. **유형** 목록에서 **(연결 문자열)** 을 선택 합니다.

4. **범위** 목록에서 **응용 프로그램**을 선택 합니다.

5. **값** 열에 외부 따옴표 없이 연결 문자열을 입력 한 다음 변경 내용을 저장 합니다.

> [!NOTE]
> 실제 응용 프로그램에서는 [연결 문자열 및 구성 파일](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)에 설명 된 대로 연결 문자열을 안전 하 게 저장 해야 합니다.

## <a name="write-the-code-for-the-forms"></a>폼에 대한 코드 작성

이 섹션에는 각 양식이 수행 하는 작업에 대 한 간략 한 개요가 포함 되어 있습니다. 또한 폼의 단추를 클릭할 때 기본 논리를 정의 하는 코드도 제공 합니다.

### <a name="navigation-form"></a>Navigation 폼

애플리케이션을 실행하면 Navigation 폼이 열립니다. **계정 추가** 단추는 NewCustomer 양식을 엽니다. **주문 이행 또는 취소** 단추를 누르면 FillOrCancel 양식이 열립니다. **끝내기** 단추를 클릭하면 애플리케이션이 닫힙니다.

#### <a name="make-the-navigation-form-the-startup-form"></a>Navigation 폼을 시작 폼으로 만들기

C#을 사용하는 경우 **솔루션 탐색기**에서 **Program.cs**를 연 다음, `Application.Run` 줄을 `Application.Run(new Navigation());`으로 변경합니다.

Visual Basic를 사용 하는 경우 **솔루션 탐색기**에서 **속성** 창을 열고 **응용 프로그램** 탭을 선택한 후 **시작 폼** 목록에서 **simpledataapp.navigation** 를 선택 합니다.

#### <a name="create-auto-generated-event-handlers"></a>자동 생성 된 이벤트 처리기 만들기

탐색 폼의 세 단추를 두 번 클릭 하 여 빈 이벤트 처리기 메서드를 만듭니다. 단추를 두 번 클릭 하면 단추 클릭으로 이벤트를 발생 시킬 수 있는 자동 생성 코드도 디자이너 코드 파일에 추가 됩니다.

#### <a name="add-code-for-the-navigation-form-logic"></a>탐색 폼 논리에 대 한 코드 추가

탐색 폼의 코드 페이지에서 다음 코드와 같이 세 개의 단추 클릭 이벤트 처리기에 대 한 메서드 본문을 완성 합니다.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer 폼

고객 이름을 입력 한 후 **계정 만들기** 단추를 선택 하면 newcustomer 폼은 고객 계정을 만들고 SQL SERVER는 id 값을 새 고객 id로 반환 합니다. 그런 다음 금액 및 주문 날짜를 지정 하 고 **주문** 단추를 선택 하 여 새 계정에 대 한 주문을 수행할 수 있습니다.

#### <a name="create-auto-generated-event-handlers"></a>자동 생성 된 이벤트 처리기 만들기

각각의 네 단추를 두 번 클릭 하 여 NewCustomer 폼의 각 단추에 대해 빈 Click 이벤트 처리기를 만듭니다. 단추를 두 번 클릭 하면 단추 클릭으로 이벤트를 발생 시킬 수 있는 자동 생성 코드도 디자이너 코드 파일에 추가 됩니다.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>NewCustomer 양식 논리에 대 한 코드 추가

NewCustomer 양식 논리를 완료 하려면 다음 단계를 수행 합니다.

1. `System.Data.SqlClient`해당 멤버의 이름을 정규화 할 필요가 없도록 네임 스페이스를 범위로 가져옵니다.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. 다음 코드와 같이 일부 변수와 도우미 메서드를 클래스에 추가 합니다.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. 다음 코드와 같이 4 개의 단추 클릭 이벤트 처리기에 대 한 메서드 본문을 완성 합니다.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel 폼

FillOrCancel 폼은 주문 ID를 입력 하 고 주문 **찾기** 단추를 클릭할 때 주문을 반환 하는 쿼리를 실행 합니다. 반환되는 행은 읽기 전용 데이터 표에 표시됩니다. 주문 **취소** 단추를 선택 하는 경우 주문을 취소 됨 (X)으로 표시할 수 있습니다. 또는 **주문 입력** 단추를 선택 하는 경우 순서를 채워진 (F)으로 표시할 수 있습니다. **주문 찾기** 단추를 다시 선택 하면 업데이트 된 행이 나타납니다.

#### <a name="create-auto-generated-event-handlers"></a>자동 생성 된 이벤트 처리기 만들기

단추를 두 번 클릭 하 여 FillOrCancel 폼의 네 단추에 대해 빈 Click 이벤트 처리기를 만듭니다. 단추를 두 번 클릭 하면 단추 클릭으로 이벤트를 발생 시킬 수 있는 자동 생성 코드도 디자이너 코드 파일에 추가 됩니다.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>FillOrCancel 폼 논리에 대 한 코드 추가

FillOrCancel 폼 논리를 완료 하려면 다음 단계를 수행 합니다.

1. 멤버의 이름을 정규화 할 필요가 없도록 다음 두 가지 네임 스페이스를 범위로 가져옵니다.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. 다음 코드와 같이 변수와 도우미 메서드를 클래스에 추가 합니다.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. 다음 코드와 같이 4 개의 단추 클릭 이벤트 처리기에 대 한 메서드 본문을 완성 합니다.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>애플리케이션 테스트

각 Click 이벤트 처리기를 코딩하고 코딩을 마친 후에 **F5** 키를 선택하여 애플리케이션을 빌드하고 테스트합니다.

## <a name="see-also"></a>추가 정보

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
