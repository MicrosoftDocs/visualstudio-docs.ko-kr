---
title: '연습: 런타임에 리본 메뉴의 컨트롤 업데이트'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 425918ea32c14e6ba905d6b32864a2844d2b5a90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255342"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>연습: 런타임에 리본 메뉴의 컨트롤 업데이트

이 연습에서는 리본이 Office 응용 프로그램에 로드 된 후 리본 개체 모델을 사용 하 여 리본 메뉴의 컨트롤을 업데이트 하는 방법을 보여 줍니다.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

이 예제에서는 Northwind 샘플 데이터베이스에서 데이터를 끌어와 Microsoft Office Outlook의 콤보 상자 및 메뉴를 채웁니다. 이러한 컨트롤에서 선택 하는 항목은 전자 메일 메시지의 **받는 사람** 및 **제목** 등의 필드를 자동으로 채웁니다.

이 연습에서는 다음 작업을 수행합니다.

- 새 Outlook VSTO 추가 기능 프로젝트를 만듭니다.

- 사용자 지정 리본 그룹을 디자인 합니다.

- 기본 제공 탭에 사용자 지정 그룹을 추가 합니다.

- 런타임에 리본 메뉴의 컨트롤을 업데이트 합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>새 Outlook VSTO 추가 기능 프로젝트 만들기

먼저 Outlook VSTO 추가 기능 프로젝트를 만듭니다.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>새 Outlook VSTO 추가 기능 프로젝트를 만들려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Ribbon_Update_At_Runtime**이름으로 Outlook VSTO 추가 기능 프로젝트를 만듭니다.

2. **새 프로젝트** 대화 상자에서 **솔루션용 디렉터리 만들기**를 선택합니다.

3. 기본 프로젝트 디렉터리에 프로젝트를 저장합니다.

     자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

## <a name="design-a-custom-ribbon-group"></a>사용자 지정 리본 그룹 디자인

사용자가 새 메일 메시지를 작성할 때이 예제의 리본이 표시 됩니다. 리본에 대 한 사용자 지정 그룹을 만들려면 먼저 프로젝트에 리본 항목을 추가한 다음 리본 디자이너에서 그룹을 디자인 합니다. 이 사용자 지정 그룹을 통해 데이터베이스에서 이름 및 주문 기록을 끌어 고객에 게 추가 작업 메일 메시지를 생성할 수 있습니다.

### <a name="to-design-a-custom-group"></a>사용자 지정 그룹을 디자인하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. **새 항목 추가** 대화 상자에서 **리본(비주얼 디자이너)** 을 선택합니다.

3. 새 리본의 이름을 **Customerribbon**로 변경한 다음 **추가**를 클릭 합니다.

     *CustomerRibbon.cs* 또는 *customerribbon .Vb* 파일이 리본 디자이너에서 열리고 기본 탭 및 그룹이 표시 됩니다.

4. 리본 디자이너를 클릭하여 선택합니다.

5. **속성** 창에서 RibbonType 속성 옆에 있는 드롭다운 화살표를 클릭 한 다음 **RibbonType** **를 클릭 합니다.**

     이렇게 하면 사용자가 Outlook에서 새 메일 메시지를 작성할 때 리본이 표시 됩니다.

6. 리본 디자이너에서 **Group1** 을 클릭 하 여 선택 합니다.

7. **속성** 창에서 **레이블** 을 **고객 구매**로 설정 합니다.

8. **도구 상자**의 **Office 리본 컨트롤** 탭에서 **ComboBox** 를 **Customer 구매** 그룹으로 끌어 놓습니다.

9. **ComboBox1** 을 클릭 하 여 선택 합니다.

10. **속성** 창에서 **레이블** 을 **고객**으로 설정 합니다.

11. **도구 상자**의 **Office 리본 컨트롤** 탭에서 **메뉴** 를 **Customer 구매** 그룹으로 끌어 놓습니다.

12. **속성** 창에서 **레이블** 을 **구매한 제품**으로 설정 합니다.

13. **동적** 을 **true**로 설정 합니다.

     이렇게 하면 리본이 Office 응용 프로그램에 로드 된 후 런타임에 메뉴에 컨트롤을 추가 하 고 제거할 수 있습니다.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>기본 제공 탭에 사용자 지정 그룹 추가

기본 제공 탭은 Outlook 탐색기 또는 검사기의 리본에 이미 있는 탭입니다. 이 절차에서는 기본 제공 탭에 사용자 지정 그룹을 추가하고 탭에서 사용자 지정 그룹의 위치를 지정합니다.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>기본 제공 탭에 사용자 지정 그룹을 추가하려면

1. **Tabaddins (기본 제공)** 탭을 클릭 하 여 선택 합니다.

2. **속성** 창에서 **ControlId** 속성을 확장 한 다음 **TabNewMailMessage** **로 설정 합니다** .

     그러면 새 메일 메시지에 표시 되는 리본의 **메시지** 탭에 **고객 구매** 그룹이 추가 됩니다.

3. **고객 구매** 그룹을 클릭 하 여 선택 합니다.

4. **속성** 창에서 **Position** 속성을 확장 하 고 **PositionType** 속성 옆에 있는 드롭다운 화살표를 클릭 한 다음 **BeforeOfficeId**를 클릭 합니다.

5. 개인 **id** 속성을 **groupclipboard**로 설정 합니다.

     이렇게 하면 **고객 구매** 그룹이 **메시지** 탭의 **클립보드** 그룹 앞에 배치 됩니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기

**데이터 원본** 창을 사용하여 형식화된 데이터 세트를 프로젝트에 추가합니다.

### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터** 메뉴에서 **새 데이터 소스 추가**를 클릭합니다.

     이렇게 하면 **데이터 소스 구성 마법사**가 시작 됩니다.

2. **데이터베이스**를 선택 하 고 **다음**을 클릭 합니다.

3. **데이터 집합**을 선택 하 고 **다음**을 클릭 합니다.

4. Northwind 샘플 Microsoft SQL Server Compact 4.0 데이터베이스에 대 한 데이터 연결을 선택 하거나 **새 연결** 단추를 사용 하 여 새 연결을 추가 합니다.

5. 연결을 선택 하거나 만든 후 **다음**을 클릭 합니다.

6. **다음** 을 클릭 하 여 연결 문자열을 저장 합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블**을 확장 합니다.

8. 다음 표의 옆에 있는 확인란을 각각 선택합니다.

    1. **고객**

    2. **주문 정보**

    3. **Orders**

    4. **제품**

9. **마침**을 클릭합니다.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>런타임에 사용자 지정 그룹의 컨트롤 업데이트

리본 개체 모델을 사용하여 다음 작업을 수행합니다.

- **Customers** 콤보 상자에 고객 이름을 추가 합니다.

- 판매 주문 및 판매 된 제품을 나타내는 메뉴 및 단추 컨트롤을 **구매한 제품** 메뉴에 추가 합니다.

- **Customers** 콤보 상자 및 **제품 구매한** 메뉴의 데이터를 사용 하 여 새 메일 메시지의 받는 사람, 제목 및 본문 필드를 채웁니다.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>리본 개체 모델을 사용하여 사용자 지정 그룹의 컨트롤을 업데이트하려면

1. **프로젝트** 메뉴에서 **참조 추가**를 클릭합니다.

2. **참조 추가** 대화 상자에서 **.net** 탭을 클릭 **하 고, System.xml 어셈블리를** 선택한 후 **확인**을 클릭 합니다.

    이 어셈블리에는 LINQ(Language-Integrated Queries)를 사용하기 위한 클래스가 포함되어 있습니다. LINQ를 사용하여 Northwind 데이터베이스의 데이터로 사용자 지정 그룹의 컨트롤을 채웁니다.

3. **솔루션 탐색기**에서 **CustomerRibbon.cs** 또는 **customerribbon .vb** 를 클릭 하 여 선택 합니다.

4. **보기** 메뉴에서 **코드**를 클릭합니다.

    코드 편집기에서 리본 코드 파일이 열립니다.

5. 리본 코드 파일 맨 위에 다음 문을 추가합니다. 이러한 문을 통해 Outlook PIA(주 interop 어셈블리)의 네임스페이스 및 LINQ 네임스페이스에 쉽게 액세스할 수 있습니다.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. 클래스 내에 다음 코드를 추가 `CustomerRibbon` 합니다. 이 코드는 Northwind 데이터베이스의 Customer, Orders, Order Details 및 Product 테이블 정보를 저장하는 데 사용할 데이터 테이블 및 테이블 어댑터를 선언합니다.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. `CustomerRibbon` 클래스에 다음 코드 블록을 추가합니다. 이 코드는 런타임에 리본 메뉴에 대 한 컨트롤을 만드는 세 가지 도우미 메서드를 추가 합니다.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. `CustomerRibbon_Load` 이벤트 처리기 메서드를 다음 코드로 바꿉니다. 이 코드는 LINQ 쿼리를 사용하여 다음 작업을 수행합니다.

   - Northwind 데이터베이스에 있는 20 명의 고객에 대 한 ID 및 이름을 사용 하 여 **customers** 콤보 상자를 채웁니다.

   - `PopulateSalesOrderInfo` 도우미 메서드를 호출합니다. 이 메서드는 현재 선택 된 고객과 관련 된 판매 주문 번호를 사용 하 여 **ProductsPurchased** 메뉴를 업데이트 합니다.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. `CustomerRibbon` 클래스에 다음 코드를 추가합니다. 이 코드는 LINQ 쿼리를 사용하여 다음 작업을 수행합니다.

   - 선택한 고객과 관련 된 각 판매 주문의 **ProductsPurchased** 메뉴에 하위 메뉴를 추가 합니다.

   - 판매 주문과 관련된 제품에 대한 단추를 각 하위 메뉴에 추가합니다.

   - 각 단추에 이벤트 처리기를 추가합니다.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. **솔루션 탐색기**에서 리본 코드 파일을 두 번 클릭 합니다.

     리본 디자이너가 열립니다.

11. 리본 디자이너에서 **Customers** 콤보 상자를 두 번 클릭 합니다.

     리본 코드 파일이 코드 편집기에서 열리고 `ComboBox1_TextChanged` 이벤트 처리기가 나타납니다.

12. `ComboBox1_TextChanged` 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

    - `PopulateSalesOrderInfo` 도우미 메서드를 호출합니다. 이 메서드는 선택한 고객과 관련 된 판매 주문으로 **구매한 제품** 메뉴를 업데이트 합니다.

    - `PopulateMailItem` 도우미 메서드를 호출하고 선택한 고객 이름인 현재 텍스트를 전달합니다. 이 메서드는 새 메일 메시지의 받는 사람, 제목 및 본문 필드를 채웁니다.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. `Click` 클래스에 다음 `CustomerRibbon` 이벤트 처리기를 추가합니다. 이 코드는 새 메일 메시지의 Body 필드에 선택한 제품의 이름을 추가 합니다.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. `CustomerRibbon` 클래스에 다음 코드를 추가합니다. 이 코드는 다음 작업을 수행합니다.

    - 현재 선택 된 고객의 전자 메일 주소를 사용 하 여 새 메일 메시지의 줄에를 채웁니다.

    - 새 메일 메시지의 제목 및 본문 필드에 텍스트를 추가 합니다.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>사용자 지정 그룹의 컨트롤 테스트

Outlook에서 새 메일 양식을 열면 리본 메뉴의 **메시지** 탭에 **고객 구매** 라는 사용자 지정 그룹이 표시 됩니다.

고객 추가 작업 전자 메일 메시지를 만들려면 고객을 선택한 다음 고객이 구매한 제품을 선택 합니다. **고객 구매** 그룹의 컨트롤은 런타임에 Northwind 데이터베이스의 데이터로 업데이트 됩니다.

### <a name="to-test-the-controls-in-the-custom-group"></a>사용자 지정 그룹의 컨트롤을 테스트하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

     Outlook이 시작됩니다.

2. Outlook의 **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **메일 메시지**를 클릭 합니다.

     다음 작업이 수행됩니다.

    - 새 메일 메시지 검사기 창이 나타납니다.

    - 리본의 **메시지** 탭에서 **고객 구매** 그룹이 **클립보드** 그룹 앞에 표시 됩니다.

    - 그룹의 **customers** 콤보 상자가 Northwind 데이터베이스에 있는 고객의 이름으로 업데이트 됩니다.

3. 리본 메뉴의 **메시지** 탭에 있는 **고객 구매** 그룹의 **Customers** 콤보 상자에서 고객을 선택 합니다.

     다음 작업이 수행됩니다.

    - **구매한 제품** 메뉴가 업데이트 되어 선택한 고객의 각 판매 주문이 표시 됩니다.

    - 각 판매 주문 하위 메뉴가 해당 주문에서 구매된 제품을 표시하도록 업데이트됩니다.

    - 선택한 고객의 전자 메일 주소가 메일 메시지의 **받는** 사람 줄에 추가 되 고 메일 메시지의 제목 및 본문에 텍스트가 채워집니다.

4. **제품 구매** 메뉴를 클릭 하 고 판매 주문을 가리킨 다음 판매 주문의 제품을 클릭 합니다.

     제품 이름이 메일 메시지의 본문에 추가됩니다.

## <a name="next-steps"></a>다음 단계

다음 항목에서는 Office UI를 사용자 지정하는 방법에 대해 더 자세히 설명합니다.

- 문서 수준 사용자 지정에 컨텍스트 기반 UI를 추가합니다. 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요.

- 표준 또는 사용자 지정 Microsoft Office Outlook 양식을 확장합니다. 자세한 내용은 [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)을 참조 하세요.

- Outlook에 사용자 지정 작업창을 추가합니다. 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
- [리본 개요](../vsto/ribbon-overview.md)
- [LINQ(Language-Integrated Query)](/dotnet/csharp/linq/index)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)
- [Outlook에 대 한 리본 사용자 지정](../vsto/customizing-a-ribbon-for-outlook.md)
- [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)
- [방법: Backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [방법: 리본 디자이너에서 리본 XML로 리본 메뉴 내보내기](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [방법: 추가 기능 사용자 인터페이스 오류 표시](../vsto/how-to-show-add-in-user-interface-errors.md)