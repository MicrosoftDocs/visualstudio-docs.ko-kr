---
title: '연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작 사용자 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9901d917de2babf4992519ffe6b360454542aad1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72602566"
---
# <a name="walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes"></a>연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 는 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 데이터베이스의 개체를 기반으로 하는 클래스 (엔터티 클래스)를 만들고 편집 하는 시각적 디자인 화면을 제공 합니다. [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)를 사용 하 여 LINQ 기술을 사용 하 여 SQL database에 액세스할 수 있습니다. 자세한 내용은 [LINQ(Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)를 참조하세요.

 기본적으로 업데이트를 수행하는 논리는 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 런타임에서 제공합니다. 런타임에서는 열 정의 및 기본 키 정보와 같은 테이블 스키마를 기반으로 기본 Insert, Update 및 Delete 문을 만듭니다. 기본 동작을 사용하지 않으려면 업데이트 동작을 구성하고 데이터베이스의 데이터 작업에 필요한 삽입, 업데이트 및 삭제를 수행하기 위한 특정 저장 프로시저를 지정할 수 있습니다. 엔터티 클래스가 뷰에 매핑되는 때와 같이 기본 동작이 생성되지 않은 경우에도 이렇게 할 수 있습니다. 또한 저장 프로시저를 통해 데이터베이스의 테이블에 액세스해야 하는 경우에 기본 업데이트 동작을 재정의할 수 있습니다. 자세한 내용은 [저장 프로시저를 사용 하 여 작업 사용자 지정](https://msdn.microsoft.com/library/aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a)을 참조 하세요.

> [!NOTE]
> 이 연습을 수행하려면 Northwind 데이터베이스의 **InsertCustomer**, **UpdateCustomer** 및 **DeleteCustomer** 저장 프로시저를 사용할 수 있어야 합니다.

 이 연습에서는 저장 프로시저를 사용하여 데이터를 데이터베이스에 다시 저장하기 위한 기본 LINQ to SQL 런타임 동작을 재정의하는 단계에 대해 설명합니다.

 이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 새 Windows Forms 애플리케이션을 만들고 여기에 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 파일을 추가합니다.

- Northwind Customers 테이블에 매핑되는 엔터티 클래스를 만듭니다.

- LINQ to SQL Customer 클래스를 참조하는 개체 데이터 소스를 만듭니다.

- Customer 클래스에 바인딩된 <xref:System.Windows.Forms.DataGridView>를 포함하는 Windows Form을 만듭니다.

- 폼의 저장 기능을 구현합니다.

- <xref:System.Data.Linq.DataContext>에 저장 프로시저를 추가하여 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 메서드를 만듭니다.

- 저장 프로시저를 사용하여 삽입, 업데이트 및 삭제를 수행하도록 Customer 클래스를 구성합니다.

## <a name="prerequisites"></a>사전 준비 사항
 이 연습을 완료하려면 다음이 필요합니다.

- Northwind 샘플 데이터베이스의 SQL Server 버전 액세스 권한.

- Northwind 데이터베이스에 대 한 **Insertcustomer**, **UpdateCustomer**및 **DeleteCustomer** 저장 프로시저입니다.

## <a name="creating-an-application-and-adding-linq-to-sql-classes"></a>애플리케이션 만들기 및 LINQ to SQL 클래스 추가
 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 클래스로 작업하고 데이터를 Windows Form에 표시하므로 새 Windows Forms 애플리케이션을 만들고 LINQ to SQL 클래스 파일을 추가합니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-a-new-windows-application-project-that-contains-linq-to-sql-classes"></a>LINQ to SQL 클래스를 포함하는 새 Windows 애플리케이션을 만들려면

1. **파일** 메뉴에서 새 프로젝트를 만듭니다.

2. 프로젝트 이름을 **UpdatingwithSProcsWalkthrough**로 합니다.

    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 및 C# 프로젝트에서 지원됩니다. 따라서 이러한 언어 중 하나로 새 프로젝트를 만듭니다.

3. **Windows Forms 응용 프로그램** 템플릿을 클릭 하 고 **확인을**클릭 합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)을 참조 하세요.

     UpdatingwithSProcsWalkthrough 프로젝트가 만들어지고 **솔루션 탐색기**에 추가 됩니다.

4. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

5. **LINQ to SQL 클래스** 템플릿을 클릭하고 **이름** 상자에 **Northwind.dbml**을 입력합니다.

6. **추가**를 클릭합니다.

     빈 LINQ to SQL 클래스 파일(Northwind.dbml)이 프로젝트에 추가되고 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]가 열립니다.

## <a name="creating-the-customer-entity-class-and-object-data-source"></a>Customer 엔터티 클래스 및 개체 데이터 소스 만들기
 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] **서버 탐색기**데이터베이스 탐색기에서로 테이블을 끌어 데이터베이스 테이블에 매핑된 클래스를 만듭니다 / **Database Explorer** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . 그러면 데이터베이스의 테이블에 매핑되는 LINQ to SQL 엔터티 클래스가 생성됩니다. 엔터티 클래스를 만든 후 이 클래스를 공용 속성이 있는 다른 클래스처럼 개체 데이터 소스로 사용할 수 있습니다.

#### <a name="to-create-a-customer-entity-class-and-configure-a-data-source-with-it"></a>Customer 엔터티 클래스를 만들고 이 클래스를 사용하여 데이터 소스를 구성하려면

1. **서버 탐색기** / **데이터베이스 탐색기**에서 Northwind 샘플 데이터베이스 SQL Server 버전의 Customer 테이블을 찾습니다.

2. **Customers** 노드를 **서버 탐색기** / **데이터베이스 탐색기** 화면으로 끌어다 놓습니다 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

     **Customer**라는 엔터티 클래스를 만듭니다. 이 클래스에는 Customers 테이블의 열에 해당하는 속성이 있습니다. 이 엔터티 클래스는 Customers 테이블의 단일 고객을 나타내므로 이름이 **Customers**가 아닌 **Customer**로 지정됩니다.

    > [!NOTE]
    > 이러한 이름 바꾸기 동작을 *복수 적용*이라고 합니다. [옵션 대화 상자](../ide/reference/options-dialog-box-visual-studio.md)에서 설정 하거나 해제할 수 있습니다. 자세한 내용은 [방법: 복수화 설정 및 해제 (O/R 디자이너)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)를 참조 하세요.

3. **빌드** 메뉴에서 **UpdatingwithSProcsWalkthrough 빌드**를 클릭하여 프로젝트를 빌드합니다.

4. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

5. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

6. **데이터 원본 형식 선택** 페이지에서 **개체**를 클릭한 후, **다음**을 클릭합니다.

7. **UpdatingwithSProcsWalkthrough** 노드를 확장하고 **Customer** 클래스를 찾아 선택합니다.

    > [!NOTE]
    > **Customer** 클래스를 사용할 수 없는 경우에는 마법사를 취소하고, 프로젝트를 빌드하고, 마법사를 다시 실행합니다.

8. **마침**을 클릭하여 데이터 원본을 만들고 **데이터 원본** 창에 **Customer** 엔터티 클래스를 추가합니다.

## <a name="creating-a-datagridview-to-display-the-customer-data-on-a-windows-form"></a>Windows Form에 고객 데이터를 표시하기 위해 DataGridView 만들기
 데이터 소스 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 창에서 Windows Form으로 데이터 소스 항목을 끌어와 서 엔터티 **Data Sources** 클래스에 바인딩된 컨트롤을 만듭니다.

#### <a name="to-add-controls-that-are-bound-to-the-entity-classes"></a>엔터티 클래스에 바인딩된 컨트롤을 추가하려면

1. 디자인 뷰에서 Form1을 엽니다.

2. **데이터 소스** 창에서 **Customer** 노드를 Form1로 끌어 옵니다.

    > [!NOTE]
    > **데이터 원본** 창을 표시하려면 **데이터** 메뉴에서 **데이터 원본 표시**를 클릭합니다.

3. 코드 편집기에서 Form1을 엽니다.

4. 폼에서 특정 메서드의 외부이지만 Form1 클래스의 내부인 위치에 다음 코드를 폼에 대해 전역적으로 추가합니다.

    ```vb
    Private NorthwindDataContext1 As New NorthwindDataContext
    ```

    ```csharp
    private NorthwindDataContext northwindDataContext1
        = new NorthwindDataContext();

    ```

5. `Form_Load` 이벤트에 대한 이벤트 처리기를 만들고 다음 코드를 처리기에 추가합니다.

    ```vb
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers
    ```

    ```csharp
    customerBindingSource.DataSource
        = northwindDataContext1.Customers;

    ```

## <a name="implementing-save-functionality"></a>저장 기능 구현
 기본적으로 저장 단추를 사용할 수 없으며 저장 기능이 구현되지 않습니다. 또한 개체 데이터 소스에 대해 데이터 바인딩된 컨트롤을 만들 때 변경된 데이터를 데이터베이스에 저장하는 코드가 자동으로 추가되지 않습니다. 이 단원에서는 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 개체에서 저장 단추를 사용하고 저장 기능을 구현하는 방법에 대해 설명합니다.

#### <a name="to-implement-save-functionality"></a>저장 기능을 구현하려면

1. 디자인 뷰에서 Form1을 엽니다.

2. **CustomerBindingNavigator**에서 저장 단추(플로피 디스크 아이콘이 있는 단추)를 선택합니다.

3. **속성**창에서 **Enabled** 속성을 **True**로 설정합니다.

4. 저장 단추를 두 번 클릭하여 이벤트 처리기를 만들고 코드 편집기로 전환합니다.

5. 저장 단추 이벤트 처리기에 다음 코드를 추가합니다.

    ```vb
    NorthwindDataContext1.SubmitChanges()
    ```

    ```csharp
    northwindDataContext1.SubmitChanges();
    ```

## <a name="overriding-the-default-behavior-for-performing-updates-inserts-updates-and-deletes"></a>업데이트(삽입, 업데이트 및 삭제)를 수행하기 위한 기본 동작 재정의

#### <a name="to-override-the-default-update-behavior"></a>기본 업데이트 동작을 재정의하려면

1. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 LINQ to SQL 파일을 엽니다. (**솔루션 탐색기**에서 **Northwind.dbml** 파일을 두 번 클릭합니다.)

2. **서버 탐색기** / **데이터베이스 탐색기**에서 Northwind 데이터베이스 **저장 프로시저** 노드를 확장 하 고 **insertcustomers**, **UpdateCustomers**및 **DeleteCustomers** 저장 프로시저를 찾습니다.

3. 세 개의 저장 프로시저를 모두 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]로 끌어 옵니다.

     이러한 저장 프로시저가 메서드 창에 <xref:System.Data.Linq.DataContext> 메서드로 추가됩니다. 자세한 내용은 [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

4. 에서 **Customer** 엔터티 클래스를 선택 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 합니다.

5. **속성** 창에서 **삽입** 속성을 선택합니다.

6. **런타임 사용** 옆의 줄임표(...) 를 클릭하여 **동작 구성** 대화 상자를 엽니다.

7. **사용자 지정**을 선택합니다.

8. **사용자 지정** 목록에서 **InsertCustomers** 메서드를 선택합니다.

9. **적용**을 클릭하여 선택한 클래스 및 동작에 대한 구성을 저장합니다.

    > [!NOTE]
    > 계속해서 클래스/동작 조합을 변경한 후 **적용**을 클릭하여 해당하는 각 조합에 대한 동작을 구성할 수 있습니다. **적용**을 클릭 하기 전에 클래스 또는 동작을 변경한 경우 변경 내용을 적용할 수 있는 경고 대화 상자가 표시 됩니다.

10. **동작** 목록에서 **업데이트**를 선택합니다.

11. **사용자 지정**을 선택합니다.

12. **사용자 지정** 목록에서 **UpdateCustomers** 메서드를 선택합니다.

     **메서드 인수** 및 **클래스 속성** 목록을 살펴보면 테이블의 일부 열에 두 개의 **메서드 인수**와 두 개의 **클래스 속성**이 있습니다. 이를 사용하면 손쉽게 변경 내용을 추적하고 동시성 위반을 확인하는 문을 만들 수 있습니다.

13. **Original_CustomerID** 메서드 인수를 **CustomerID(Original)** 클래스 속성에 매핑합니다.

    > [!NOTE]
    > 기본적으로 메서드 인수는 이름이 일치하는 경우 클래스 속성에 매핑됩니다. 속성 이름이 변경되거나 더 이상 테이블 및 엔터티 클래스 간에 일치하지 않아 O/R 디자이너에서 올바른 매핑을 결정할 수 없는 경우에는 매핑할 해당하는 클래스 속성을 선택해야 합니다. 또한 메서드 인수를 매핑할 올바른 클래스 속성이 없는 경우 **클래스 속성** 값을 **(없음)** 으로 설정할 수 있습니다.

14. **적용**을 클릭하여 선택한 클래스 및 동작에 대한 구성을 저장합니다.

15. **목록** 목록에서 **삭제**를 선택합니다.

16. **사용자 지정**을 선택합니다.

17. **사용자 지정** 목록에서 **DeleteCustomers** 메서드를 선택합니다.

18. **Original_CustomerID** 메서드 인수를 **CustomerID(Original)** 클래스 속성에 매핑합니다.

19. **확인**을 클릭합니다.

> [!NOTE]
> 이 연습에서는 문제가 되지 않지만 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]은 삽입 및 업데이트 과정에서 identity(자동 증분), rowguidcol(데이터베이스에서 생성된 GUID) 및 timestamp 열에 대해 데이터베이스에서 생성된 값을 자동으로 처리한다는 점을 기억할 필요가 있습니다. 데이터베이스에서 생성된 값이 다른 형식의 열에 있으면 null 값이라는 예기치 않은 결과가 발생합니다. 데이터베이스에서 생성된 값을 반환하려면 수동으로 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>를 `true`로 설정하고 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>를 <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> 또는 <xref:System.Data.Linq.Mapping.AutoSync> 중 하나로 설정해야 합니다.

## <a name="testing-the-application"></a>애플리케이션 테스트
 애플리케이션을 다시 실행하여 **UpdateCustomers** 저장 프로시저가 데이터베이스에서 고객 레코드를 올바로 업데이트하는지 확인합니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. F5 키를 누릅니다.

2. 표에서 레코드를 수정하여 업데이트 동작을 테스트합니다.

3. 새 레코드를 추가하여 삽입 동작을 테스트합니다.

4. 저장 단추를 클릭하여 변경 내용을 데이터베이스에 다시 저장합니다.

5. 폼을 닫아 디버깅을

6. F5 키를 눌러 업데이트된 레코드와 새로 삽입한 레코드가 있는지 확인합니다.

7. 3단계에서 만든 새 레코드를 삭제하여 삭제 동작을 테스트합니다.

8. 저장 단추를 클릭하여 변경 내용을 전송하고 데이터베이스에서 삭제한 레코드를 제거합니다.

9. 폼을 닫아 디버깅을

10. F5 키를 눌러 삭제한 레코드가 데이터베이스에서 제거되었는지 확인합니다.

    > [!NOTE]
    > 애플리케이션에서 SQL Server Express 버전을 사용하는 경우 데이터베이스 파일의 **출력 디렉터리로 복사** 속성 값에 따라 10단계에서 F5 키를 누를 때 변경 내용이 표시되지 않을 수 있습니다.

## <a name="next-steps"></a>다음 단계
 애플리케이션 요구 사항에 따라 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 엔터티 클래스를 만든 후 몇 단계를 더 수행할 수도 있습니다. 이 애플리케이션에서 개선할 수 있는 몇 가지 사항은 다음과 같습니다.

- 업데이트 동안 동시성 검사를 구현합니다. 자세한 내용은 [낙관적 동시성: 개요](https://msdn.microsoft.com/library/c2e38512-d0c8-4807-b30a-cb7e30338694)를 참조 하세요.

- LINQ 쿼리를 추가하여 데이터를 필터링합니다. 자세한 내용은 [LINQ 쿼리 소개 (c #)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Visual studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [LINQ to SQL 쿼리](https://msdn.microsoft.com/library/f4897aaa-7f44-4c20-a471-b948c2971aae) [DataContext 메서드 (o/r 디자이너)](../data-tools/datacontext-methods-o-r-designer.md) [방법: 업데이트, 삽입 및 삭제를 수행 하는 저장 프로시저 할당 (o/r 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [PAVE Visual Studio 2012에서 데이터 응용 프로그램 개발에 대 한 새로운 기능](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1)
