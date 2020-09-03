---
title: '연습: WPF 응용 프로그램에서 관련 데이터 표시 | Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8116d4ab4a2f20f79f3849ae7f8b324af9832dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850247"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>연습: WPF 애플리케이션에서 관련 데이터 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 부모/자식 관계가 있는 데이터베이스 테이블의 데이터를 표시 하는 WPF 응용 프로그램을 만듭니다. 데이터는 엔터티 데이터 모델 엔터티에 캡슐화 됩니다. 부모 엔터티는 일련의 주문에 대 한 개요 정보를 포함 합니다. 이 엔터티의 각 속성은 응용 프로그램의 다른 컨트롤에 바인딩됩니다. 자식 엔터티에는 각 주문에 대 한 세부 정보가 포함 됩니다. 이 데이터 집합은 컨트롤에 바인딩됩니다 <xref:System.Windows.Controls.DataGrid> .

 이 연습에서는 다음 작업을 수행합니다.

- AdventureWorksLT 샘플 데이터베이스의 데이터에서 생성 되는 WPF 응용 프로그램 및 엔터티 데이터 모델를 만듭니다.

- 일련의 주문에 대 한 개요 정보를 표시 하는 데이터 바인딩된 컨트롤 집합을 만듭니다. **데이터 소스** 창에서 **WPF 디자이너로**부모 엔터티를 끌어서 컨트롤을 만듭니다.

- <xref:System.Windows.Controls.DataGrid>선택한 각 주문에 대 한 관련 세부 정보를 표시 하는 컨트롤을 만듭니다. 컨트롤은 **데이터 소스** 창에서 **WPF 디자이너**의 창으로 자식 엔터티를 끌어서 만듭니다.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- AdventureWorksLT 샘플 데이터베이스가 연결된 SQL Server 또는 SQL Server Express의 실행 중인 인스턴스 액세스 권한. [CodePlex 웹 사이트](https://codeplex.com/SqlServerSamples)에서 AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다.

  또한 다음 개념에 대한 지식은 연습을 완료하는 데 반드시 필요하지는 않지만 사전에 파악해 두면 유용할 수 있습니다.

- 엔터티 데이터 모델 및 ADO.NET Entity Framework 자세한 내용은 [Entity Framework 개요](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)를 참조 하세요.

- WPF 디자이너 사용법. 자세한 내용은 [WPF 및 Silverlight 디자이너 개요](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)를 참조 하세요.

- WPF 데이터 바인딩. 자세한 내용은 [데이터 바인딩 개요](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)를 참조 하세요.

## <a name="creating-the-project"></a>프로젝트 만들기
 주문 레코드를 표시할 새 WPF 프로젝트를 만듭니다.

#### <a name="to-create-a-new-wpf-project"></a>새 WPF 프로젝트를 만들려면

1. Visual Studio를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. **Visual c #** 또는 **Visual Basic**을 확장 한 다음 **Windows**를 선택 합니다.

4. 대화 상자 위쪽에 있는 콤보 상자에서 **.NET Framework 4** 가 선택 되어 있는지 확인 합니다. <xref:System.Windows.Controls.DataGrid>이 연습에서 사용 하는 컨트롤은 .NET Framework 4 에서만 사용할 수 있습니다.

5. **WPF 애플리케이션** 프로젝트 템플릿을 선택합니다.

6. **이름** 상자에 `AdventureWorksOrdersViewer`을 입력합니다.

7. **확인**을 클릭합니다.

     Visual Studio에서 프로젝트를 만듭니다 `AdventureWorksOrdersViewer` .

## <a name="creating-an-entity-data-model-for-the-application"></a>응용 프로그램에 대 한 엔터티 데이터 모델 만들기
 데이터 바인딩된 컨트롤을 만들려면 먼저 애플리케이션의 데이터 모델을 정의하고 **데이터 원본** 창에 추가해야 합니다. 이 연습에서 데이터 모델은 엔터티 데이터 모델입니다.

#### <a name="to-create-an-entity-data-model"></a>엔터티 데이터 모델을 만들려면

1. **데이터** 메뉴에서 **새 데이터 소스 추가** 를 클릭 하 여 **데이터 소스 구성 마법사**를 엽니다.

2. **데이터 소스 형식 선택** 페이지에서 **데이터베이스**를 클릭 한 후 **다음**을 클릭 합니다.

3. **데이터베이스 모델 선택** 페이지에서 **엔터티 데이터 모델**를 클릭 한 후 **다음**을 클릭 합니다.

4. **모델 콘텐츠 선택** 페이지에서 **데이터베이스에서 생성**을 클릭 하 고 **다음**을 클릭 합니다.

5. **데이터 연결 선택** 페이지에서 다음 중 하나를 수행 합니다.

   - AdventureWorksLT 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

      또는

   - **새 연결** 을 클릭 하 고 AdventureWorksLT 데이터베이스에 대 한 연결을 만듭니다.

     **App.Config로 엔터티 연결 설정 저장** 옵션이 선택 되어 있는지 확인 하 고 **다음**을 클릭 합니다.

6. **데이터베이스 개체 선택** 페이지에서 **테이블**을 확장 하 고 다음 테이블을 선택 합니다.

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. **마침**을 클릭합니다.

8. 프로젝트를 빌드합니다.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>주문을 표시 하는 데이터 바인딩된 컨트롤 만들기
 `SalesOrderHeaders` **데이터 소스** 창에서 WPF 디자이너로 엔터티를 끌어 주문 레코드를 표시 하는 컨트롤을 만듭니다.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>주문 레코드를 표시 하는 데이터 바인딩된 컨트롤을 만들려면

1. **솔루션 탐색기**에서 mainwindow.xaml를 두 번 클릭 합니다.

    WPF 디자이너에서 창이 열립니다.

2. **Height** 및 **Width** 속성이 800로 설정 되도록 XAML을 편집 합니다.

3. **데이터 소스** 창에서 **SalesOrderHeaders** 노드에 대 한 드롭다운 메뉴를 클릭 하 고 **세부 정보**를 선택 합니다.

4. **SalesOrderHeaders** 노드를 확장합니다.

5. **SalesOrderID** 옆의 드롭다운 메뉴를 클릭 하 고 **ComboBox**를 선택 합니다.

6. **SalesOrderHeaders** 노드의 다음 자식 노드 각각에 대해 노드 옆의 드롭다운 메뉴를 클릭 하 고 **없음**을 선택 합니다.

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **부분합**

   - **TaxAmt**

   - **Freight**

   - **rowguid**

   - **ModifiedDate**

     이 작업을 수행하면 다음 단계에서 이러한 노드에 대해 데이터 바인딩된 컨트롤이 작성되지 않습니다. 이 연습에서는 최종 사용자가 이 데이터를 확인하지 않아도 된다고 가정합니다.

7. **데이터 소스** 창에서 **SALESORDERHEADERS** 노드를 **WPF 디자이너**의 창으로 끌어 옵니다.

    Visual Studio는 **SalesOrderHeaders** 엔터티의 데이터에 바인딩되는 컨트롤 집합을 만들고 데이터를 로드 하는 코드를 생성 하는 XAML을 생성 합니다. 생성 된 XAML 및 코드에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

8. 디자이너에서 **판매 주문 ID** 레이블 옆에 있는 콤보 상자를 클릭 합니다.

9. **속성** 창에서 **IsReadOnly** 속성 옆의 확인란을 선택합니다.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>주문 세부 정보를 표시 하는 DataGrid 만들기
 <xref:System.Windows.Controls.DataGrid> `SalesOrderDetails` **데이터 소스** 창에서 WPF designer로 엔터티를 끌어 주문 정보를 표시 하는 컨트롤을 만듭니다.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>주문 정보를 표시 하는 DataGrid를 만들려면

1. **데이터 소스** 창에서 **SalesOrderHeaders** 노드의 자식인 **SalesOrderDetails** 노드를 찾습니다.

   > [!NOTE]
   > **SalesOrderHeaders** 노드의 피어 인 **SalesOrderDetails** 노드도 있습니다. **SalesOrderHeaders** 노드의 자식 노드를 선택 했는지 확인 합니다.

2. 자식 **SalesOrderDetails** 노드를 확장 합니다.

3. **SalesOrderDetails** 노드의 다음 자식 노드 각각에 대해 노드 옆의 드롭다운 메뉴를 클릭 하 고 **없음**을 선택 합니다.

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **rowguid**

   - **ModifiedDate**

     이 작업을 수행 하면 Visual Studio에서 <xref:System.Windows.Controls.DataGrid> 다음 단계에서 만든 컨트롤에이 데이터를 포함 하지 않습니다. 이 연습에서는 최종 사용자가 이 데이터를 확인하지 않아도 된다고 가정합니다.

4. **데이터 소스** 창에서 **WPF 디자이너**의 창으로 자식 **SalesOrderDetails** 노드를 끌어 옵니다.

    Visual Studio는 새 데이터 바인딩된 컨트롤을 정의 하는 XAML을 생성 하 <xref:System.Windows.Controls.DataGrid> 고 디자이너에 컨트롤을 표시 합니다. 또한 Visual Studio는 `GetSalesOrderHeadersQuery` **SalesOrderDetails** 엔터티에 데이터를 포함 하도록 코드 숨김으로 생성 된 메서드를 업데이트 합니다.

## <a name="testing-the-application"></a>애플리케이션 테스트
 응용 프로그램을 빌드하고 실행 하 여 주문 레코드를 표시 하는지 확인 합니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. **F5**키를 누릅니다.

     애플리케이션이 빌드되고 실행됩니다. 다음을 확인합니다.

    - **판매 주문 ID** 콤보 상자에 **71774**이 표시 됩니다. 이는 엔터티의 첫 번째 주문 ID입니다.

    - **판매 주문 ID** 콤보 상자에서 선택한 각 주문에 대해 자세한 주문 정보가에 표시 됩니다 <xref:System.Windows.Controls.DataGrid> .

2. 애플리케이션을 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료 한 후 Visual Studio에서 **데이터 소스** 창을 사용 하 여 WPF 컨트롤을 다른 형식의 데이터 소스에 바인딩하는 방법에 대해 알아봅니다. 자세한 내용은 [WCF 데이터 서비스에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) 및 [데이터 집합에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-dataset.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 Wpf [응용 프로그램에서 관련 데이터를 표시](../data-tools/display-related-data-in-wpf-applications.md) [하는 Visual Studio의 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
