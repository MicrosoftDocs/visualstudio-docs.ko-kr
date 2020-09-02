---
title: WPF 응용 프로그램에서 조회 테이블 만들기 | Microsoft Docs
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657419"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF 애플리케이션에서 조회 테이블 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

용어 *조회 테이블* ( *조회 바인딩*이라고 함)은 다른 테이블의 외래 키 필드 값을 기반으로 한 데이터 테이블의 정보를 표시 하는 컨트롤을 설명 합니다. **데이터 소스** 창에서 부모 테이블 또는 개체의 주 노드를 관련 자식 테이블의 열 또는 속성에 이미 바인딩된 컨트롤로 끌어 조회 테이블을 만들 수 있습니다.

 예를 들어 sales 데이터베이스의 테이블을 생각해 보겠습니다 `Orders` . 테이블의 각 레코드에 `Orders` 는 `CustomerID` 주문에 배치 된 고객을 나타내는가 포함 됩니다. 는 `CustomerID` 테이블의 고객 레코드를 가리키는 외래 키입니다 `Customers` . 테이블의 주문 목록을 표시 하는 경우 `Orders` 대신 실제 고객 이름을 표시 하는 것이 좋습니다 `CustomerID` . 고객 이름이 테이블에 있으므로 `Customers` 고객 이름을 표시 하는 조회 테이블을 만들어야 합니다. 조회 테이블은 레코드의 값을 사용 하 여 `CustomerID` `Orders` 관계를 탐색 하 고 고객 이름을 반환 합니다.

## <a name="to-create-a-lookup-table"></a>조회 테이블을 만들려면

1. 관련 데이터가 포함 된 다음 데이터 원본 중 하나를 프로젝트에 추가 합니다.

    - 데이터 집합 또는 엔터티 데이터 모델입니다.

    - WCF 데이터 서비스, WCF 서비스 또는 웹 서비스입니다. 자세한 내용은 [방법: 서비스의 데이터에 연결](../data-tools/how-to-connect-to-data-in-a-service.md)을 참조 하세요.

    - 개체. 자세한 내용은 [방법: 개체의 데이터에 연결](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b)을 참조 하세요.

    > [!NOTE]
    > 조회 테이블을 만들려면 먼저 두 개의 관련 테이블이 나 개체가 프로젝트의 데이터 원본으로 존재 해야 합니다.

2. **WPF 디자이너**를 열고 디자이너에 **데이터 소스** 창의 항목에 대 한 유효한 놓기 대상인 컨테이너가 포함 되어 있는지 확인 합니다.

     유효한 놓기 대상에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

3. **데이터** 메뉴에서 **데이터 원본 표시**를 클릭하여 **데이터 원본** 창을 엽니다.

4. 부모 테이블이 나 개체 및 관련 자식 테이블이 나 개체를 볼 수 있을 때까지 **데이터 소스** 창에서 노드를 확장 합니다.

    > [!NOTE]
    > 관련 자식 테이블이 나 개체는 부모 테이블이 나 개체 아래에 확장 가능한 자식 노드로 표시 되는 노드입니다.

5. 자식 노드에 대 한 드롭다운 메뉴를 클릭 하 고 **세부 정보**를 선택 합니다.

6. 자식 노드를 확장 합니다.

7. 자식 노드 아래에서 자식 및 부모 데이터와 관련 된 항목에 대 한 드롭다운 메뉴를 클릭 합니다. 앞의 예제에서이는 **CustomerID** 노드입니다. 조회 바인딩을 지 원하는 다음 형식의 컨트롤 중 하나를 선택 합니다.

    - **ComboBox**

    - **상자가**

    - **ListView**

        > [!NOTE]
        > 목록에 **ListBox** 또는 **ListView** 컨트롤이 표시 되지 않는 경우 목록에 이러한 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

    - 에서 파생 되는 모든 사용자 지정 컨트롤 <xref:System.Windows.Controls.Primitives.Selector> 입니다.

        > [!NOTE]
        > **데이터 소스** 창에서 항목에 대해 선택할 수 있는 컨트롤 목록에 사용자 지정 컨트롤을 추가 하는 방법에 대 한 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤 추가](../data-tools/add-custom-controls-to-the-data-sources-window.md)를 참조 하세요.

8. 자식 노드를 **데이터 소스** 창에서 WPF 디자이너의 컨테이너로 끌어 옵니다. 앞의 예제에서 자식 노드는 **Orders** 노드입니다.

     Visual Studio는 끌어 온 각 항목에 대해 새로운 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. 또한 XAML은 <xref:System.Windows.Data.CollectionViewSource> 자식 테이블이 나 개체에 대 한 새를 놓기 대상의 리소스에 추가 합니다. 일부 데이터 원본의 경우에는 Visual Studio에서 테이블 또는 개체에 데이터를 로드 하는 코드도 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

9. **데이터 소스** 창에서 이전에 만든 조회 바인딩 컨트롤로 부모 노드를 끌어 옵니다. 앞의 예제에서 부모 노드는 **Customers** 노드입니다.

     Visual Studio는 컨트롤의 일부 속성을 설정 하 여 조회 바인딩을 구성 합니다. 다음 표에서는 Visual Studio에서 수정 하는 속성을 보여 줍니다. 필요한 경우 XAML 또는 **속성** 창에서 이러한 속성을 변경할 수 있습니다.

    |속성|설정 설명|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|이 속성은 컨트롤에 표시 되는 데이터를 가져오는 데 사용 되는 컬렉션 또는 바인딩을 지정 합니다. Visual Studio는 <xref:System.Windows.Data.CollectionViewSource> 컨트롤로 끌어 온 부모 데이터의로이 속성을 설정 합니다.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|이 속성은 컨트롤에 표시 되는 데이터 항목의 경로를 지정 합니다. Visual Studio는 기본 키 뒤에 문자열 데이터 형식이 있는 부모 데이터의 첫 번째 열 또는 속성으로이 속성을 설정 합니다.<br /><br /> 부모 데이터에 다른 열 이나 속성을 표시 하려는 경우이 속성을 다른 속성의 경로로 변경 합니다.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio는이 속성을 디자이너로 끌어 온 자식 데이터의 열 또는 속성에 바인딩합니다. 부모 데이터의 외래 키입니다.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio는 부모 데이터의 외래 키인 자식 데이터의 열 또는 속성 경로에이 속성을 설정 합니다.|

## <a name="see-also"></a>관련 항목
 [Visual studio에서 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) visual [studio에서 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) wpf [응용 프로그램에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md) [연습: wpf 응용 프로그램에서 관련 데이터 표시](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
