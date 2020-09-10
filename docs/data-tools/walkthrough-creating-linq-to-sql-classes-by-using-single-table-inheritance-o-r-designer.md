---
title: 단일 테이블 상속을 사용 하는 LINQ to SQL 클래스
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0c76818f7cd70077996370cf5ffe930ef78f9acb
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741828"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>연습: 단일 테이블 상속을 사용 하 여 LINQ to SQL 클래스 만들기 (O/R 디자이너)
[Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 는 일반적으로 관계형 시스템에서 구현 되는 단일 테이블 상속을 지원 합니다. 이 연습은 [방법: O/R 디자이너를 사용 하 여 상속 구성](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) 항목에서 제공 하는 일반 단계를 확장 하 고에서 상속 사용을 보여 주는 몇 가지 실제 데이터를 제공 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] 합니다.

이 연습에서는 다음 작업을 수행 합니다.

- 데이터베이스 테이블을 만들고 그 안에 데이터를 추가합니다.

- Windows Forms 애플리케이션을 만듭니다.

- [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] 파일을 프로젝트에 추가합니다.

- 새 엔터티 클래스를 만듭니다.

- 상속을 사용하도록 엔터티 클래스를 구성합니다.

- 상속된 클래스를 쿼리합니다.

- Windows Form에 데이터를 표시합니다.

## <a name="create-a-table-to-inherit-from"></a>상속에 사용될 테이블 만들기
상속이 어떻게 작동 하는지 확인 하려면 작은 테이블을 만들고 `Person` 기본 클래스로 사용한 다음 `Employee` 이를 상속 하는 개체를 만듭니다.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>상속을 보여 주기 위한 기본 테이블을 만들려면

1. **서버 탐색기** 또는 **데이터베이스 탐색기**에서 **테이블** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새 테이블 추가**를 클릭 합니다.

    > [!NOTE]
    > Northwind 데이터베이스 또는 테이블을 추가할 수 있는 기타 데이터베이스를 사용할 수 있습니다.

2. **테이블 디자이너**에서 테이블에 다음 열을 추가 합니다.

    |열 이름|데이터 형식|Null 허용|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**형식**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**관리자**|**int**|**True**|

3. ID 열을 기본 키로 설정합니다.

4. 테이블을 저장하고 이름을 **Person**으로 지정합니다.

## <a name="add-data-to-the-table"></a>테이블에 데이터 추가
속성이 올바르게 구성되었는지 확인하기 위해서는 단일 테이블 상속에서 각 클래스에 대한 몇 가지 데이터가 테이블에 필요합니다.

### <a name="to-add-data-to-the-table"></a>테이블에 데이터를 추가하려면

1. 데이터 뷰에서 테이블을 엽니다. **서버 탐색기** 또는 **데이터베이스 탐색기** 에서 **Person** 테이블을 마우스 오른쪽 단추로 클릭 하 고 **테이블 데이터 표시**를 클릭 합니다.

2. 다음 데이터를 테이블로 복사합니다. ( **결과** 창에서 전체 행을 선택 하 여 복사 하 고 테이블에 붙여넣을 수 있습니다.)

    |**ID**|**형식**|**FirstName**|**LastName**|**관리자**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>새 프로젝트 만들기
테이블을 만든 후에는 상속 구성을 보여 주기 위한 새 프로젝트를 만듭니다.

### <a name="to-create-the-new-windows-forms-application"></a>새 Windows Forms 응용 프로그램을 만들려면

1. Visual Studio의 **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

2. 왼쪽 창에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **Windows 데스크톱**을 선택 합니다.

3. 가운데 창에서 **Windows Forms 앱** 프로젝트 형식을 선택 합니다.

4. 프로젝트 이름을 **InheritanceWalkthrough**로 지정한 다음 **확인**을 선택 합니다.

     **InheritanceWalkthrough** 프로젝트가 만들어지고 **솔루션 탐색기**에 추가됩니다.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>프로젝트에 LINQ to SQL 클래스 파일 추가

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>프로젝트에 LINQ to SQL 파일을 추가하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **LINQ to SQL 클래스** 템플릿을 클릭한 다음, **추가**를 클릭합니다.

     *.Dbml* 파일이 프로젝트에 추가 되 고 **O/R 디자이너가** 열립니다.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>O/R 디자이너를 사용하여 상속 만들기
**상속** 개체를 **도구 상자**에서 디자인 화면으로 끌어 와서 상속을 구성합니다.

### <a name="to-create-the-inheritance"></a>상속을 만들려면

1. **서버 탐색기** 또는 **데이터베이스 탐색기**에서 이전에 만든 **Person** 테이블로 이동 합니다.

2. **Person** 테이블을 **O/R 디자이너** 디자인 화면으로 끌어 놓습니다.

3. 두 번째 **Person** 테이블을 **O/R 디자이너로** 끌어 오고 이름을 **Employee**로 변경 합니다.

4. **Person** 개체에서 **Manager** 속성을 삭제합니다.

5. **Employee** 개체에서 **Type**, **ID**, **FirstName** 및 **LastName** 속성을 삭제합니다. 즉, **Manager**를 제외한 모든 속성을 삭제합니다.

6. **도구 상자**의 **개체 관계형 디자이너** 탭에서 **Person** 및 **Employee** 개체 사이에 **상속**을 만듭니다. 이렇게 하려면 **도구 상자**에서 **상속** 항목을 클릭하고 마우스 단추를 놓으세요. 그런 다음, **Employee** 개체를 클릭 하 고 **O/R 디자이너**에서 **Person** 개체를 클릭 합니다. 그러면 상속 선의 화살표가 **Person** 개체를 가리킵니다.

7. 디자인 화면에서 **상속** 선을 클릭합니다.

8. **Discriminator Property** 속성을 **Type**으로 설정합니다.

9. **Derived Class Discriminator Value** 속성을 **2**로 설정합니다.

10. **Base Class Discriminator Value** 속성을 **1**로 설정합니다.

11. **Inheritance Default** 속성을 **Person**으로 설정합니다.

12. 프로젝트를 빌드합니다.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>상속된 클래스 쿼리 및 폼에 데이터 표시
이제 개체 모델에서 특정 클래스에 대해 쿼리 하는 일부 코드를 폼에 추가 합니다.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>LINQ 쿼리를 만들고 폼에 결과를 표시하려면

1. **ListBox**를 **Form1**으로 끌어서 놓습니다.

2. 폼을 두 번 클릭하여 `Form1_Load` 이벤트 처리기를 만듭니다.

3. 다음 코드를 `Form1_Load` 이벤트 처리기에 추가합니다.

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>애플리케이션 테스트
응용 프로그램을 실행 하 고 목록 상자에 표시 된 레코드가 모두 직원 (해당 **유형의** 열에 값이 2 인 레코드) 인지 확인 합니다.

### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. **F5**키를 누릅니다.

2. **Type** 열의 값이 2인 레코드만 표시되는지 확인합니다.

3. 폼을 닫아 디버깅을 **디버그** 메뉴에서 **디버깅 중지**를 클릭 합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [연습: LINQ to SQL 클래스 만들기(O-R 디자이너)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O/R 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [방법: Visual Basic 또는 C에서 개체 모델 생성 #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
