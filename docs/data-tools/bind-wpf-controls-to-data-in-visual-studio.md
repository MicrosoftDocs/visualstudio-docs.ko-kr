---
title: 데이터에 WPF 컨트롤 바인딩-1 부
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 27d0c14bcf09a3b0d30cd23dea0f8348c45fcab7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282883"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio에서 데이터에 WPF 컨트롤 바인딩

데이터를 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 컨트롤에 바인딩하여 애플리케이션 사용자에게 데이터를 표시할 수 있습니다. 이러한 데이터 바인딩된 컨트롤을 만들려면 **데이터 소스** 창에서 Visual Studio의로 항목을 끌어 옵니다 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] . 이 항목에서는 데이터 바인딩된 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] 애플리케이션을 만드는 데 사용할 수 있는 가장 일반적인 몇 가지 작업, 도구 및 클래스에 대해 설명합니다.

Visual Studio에서 데이터 바인딩된 컨트롤을 만드는 방법에 대 한 일반적인 내용은 [Visual studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요. 데이터 바인딩에 대 한 자세한 내용은 [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] [데이터 바인딩 개요](/dotnet/desktop-wpf/data/data-binding-overview)를 참조 하세요.

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>WPF 컨트롤을 데이터에 바인딩하는 것과 관련된 작업

다음 표에서는 **데이터 원본** 창에서 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]로 항목을 끌어서 수행할 수 있는 작업을 보여 줍니다.

|Task|자세한 정보|
|----------| - |
|새 데이터 바인딩된 컨트롤을 만듭니다.<br /><br /> 기존 컨트롤을 데이터에 바인딩합니다.|[데이터 집합에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|부모-자식 관계로 관련 데이터를 표시하는 컨트롤을 만듭니다. 그러면 사용자가 어느 한 컨트롤에서 부모 데이터 레코드를 선택하면 선택한 부모 레코드의 관련 자식 데이터가 다른 한 컨트롤에 표시됩니다.|[WPF 애플리케이션에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md)|
|한 테이블의 정보를 다른 테이블의 외래 키 필드 값을 기반으로 표시하는 *조회 테이블*을 만듭니다.|[WPF 애플리케이션에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|데이터베이스의 이미지에 컨트롤을 바인딩합니다.|[데이터베이스의 그림에 컨트롤 바인딩](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>유효한 놓기 대상

**데이터 원본** 창의 항목을 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]의 유효한 놓기 대상으로 끌어 올 수 있습니다. 유효한 놓기 대상에는 크게 두 가지 종류 즉, 컨테이너와 컨트롤이 있습니다. 컨테이너는 일반적으로 컨트롤을 포함하는 사용자 인터페이스 요소입니다. 예를 들어, 표는 컨테이너이므로 창입니다.

## <a name="generated-xaml-and-code"></a>생성된 XAML 및 코드

**데이터 소스** 창에서로 항목을 끌어 오면 [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 새 데이터 바인딩된 컨트롤을 정의 하거나 기존 컨트롤을 데이터 소스에 바인딩하는을 생성 합니다. 일부 데이터 원본의 경우에는 데이터 소스를 데이터로 채우는 코드에 코드를 생성 하는 코드도 생성 됩니다.

다음 표에서는 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] **데이터 소스** 창에서 각 데이터 소스 형식에 대해 Visual Studio에서 생성 하는 및 코드를 보여 줍니다.

| 데이터 원본 | 데이터 소스에 컨트롤을 바인딩하는 XAML을 생성합니다. | 데이터 소스를 데이터로 채우는 코드를 생성합니다. |
| - | - | - |
| 데이터 세트 | 예 | 예 |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | 예 | 예 |
| 서비스 | 예 | 아니요 |
| Object | 예 | 아니요 |

### <a name="datasets"></a>데이터 세트

**데이터 소스** 창에서 디자이너로 테이블이 나 열을 끌어 오면 Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 다음을 수행 하는을 생성 합니다.

- 항목을 끌어 온 컨테이너의 리소스에 데이터 세트과 새 <xref:System.Windows.Data.CollectionViewSource>를 추가합니다. <xref:System.Windows.Data.CollectionViewSource>는 데이터 세트에 있는 데이터를 탐색하고 표시하는 데 사용할 수 있는 개체입니다.

- 컨트롤에 대한 데이터 바인딩을 만듭니다. 디자이너의 기존 컨트롤로 항목을 끌면 XAML이 컨트롤을 항목에 바인딩합니다. 항목을 컨테이너로 끌어 오면 XAML은 끌어 온 항목에 대해 선택한 컨트롤을 만들고 컨트롤을 항목에 바인딩합니다. 이 컨트롤은 새로운 <xref:System.Windows.Controls.Grid> 내에 만들어집니다.

또한 Visual Studio에서는 코드 숨김 파일에 대해 다음과 같은 변경 작업도 수행합니다.

- 이 컨트롤이 들어 있는 <xref:System.Windows.FrameworkElement.Loaded> 요소에 대한 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 이벤트 처리기를 만듭니다. 이 이벤트 처리기는 테이블을 데이터로 채우고 컨테이너의 리소스에서 <xref:System.Windows.Data.CollectionViewSource>를 검색한 다음 첫 번째 데이터 항목을 현재 항목으로 설정합니다. <xref:System.Windows.FrameworkElement.Loaded>이벤트 처리기가 이미 있는 경우 Visual Studio는 기존 이벤트 처리기에이 코드를 추가 합니다.

### <a name="entity-data-models"></a>엔터티 데이터 모델

**데이터 소스** 창에서 디자이너로 엔터티 또는 엔터티 속성을 끌어 오면 Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 다음을 수행 하는을 생성 합니다.

- 항목을 끌어 온 컨테이너의 리소스에 새 <xref:System.Windows.Data.CollectionViewSource>를 추가합니다. <xref:System.Windows.Data.CollectionViewSource>는 엔터티에 있는 데이터를 탐색하고 표시하는 데 사용할 수 있는 개체입니다.

- 컨트롤에 대한 데이터 바인딩을 만듭니다. 디자이너의 기존 컨트롤로 항목을 끌면 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]이 컨트롤을 항목에 바인딩합니다. 항목을 컨테이너로 끌어 오면는 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 끌어 온 항목에 대해 선택한 컨트롤을 만들고 컨트롤을 항목에 바인딩합니다. 이 컨트롤은 새로운 <xref:System.Windows.Controls.Grid> 내에 만들어집니다.

또한 Visual Studio에서는 코드 숨김 파일에 대해 다음과 같은 변경 작업도 수행합니다.

- 디자이너로 끌어 온 엔터티(또는 디자이너로 끌어 온 속성이 들어 있는 엔터티)에 대한 쿼리를 반환하는 새 메서드를 추가합니다. 새 메서드에는 이름이 있습니다 `Get<EntityName>Query` `\<EntityName>` . 여기서은 엔터티의 이름입니다.

- 이 컨트롤이 들어 있는 <xref:System.Windows.FrameworkElement.Loaded> 요소에 대한 [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] 이벤트 처리기를 만듭니다. 이벤트 처리기는 메서드를 호출 `Get<EntityName>Query` 하 여 엔터티를 데이터로 채우고 <xref:System.Windows.Data.CollectionViewSource> 컨테이너의 리소스에서를 검색 한 다음 첫 번째 데이터 항목을 현재 항목으로 만듭니다. <xref:System.Windows.FrameworkElement.Loaded>이벤트 처리기가 이미 있는 경우 Visual Studio는 기존 이벤트 처리기에이 코드를 추가 합니다.

### <a name="services"></a>서비스

**데이터 소스** 창에서 디자이너로 서비스 개체 또는 속성을 끌어 오면 Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 데이터 바인딩된 컨트롤을 만들거나 기존 컨트롤을 개체나 속성에 바인딩하는을 생성 합니다. 그러나 Visual Studio는 프록시 서비스 개체를 데이터로 채우는 코드를 생성 하지 않습니다. 이 코드를 직접 작성해야 합니다. 이 작업을 수행 하는 방법을 보여 주는 예제는 [WCF 데이터 서비스에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)을 참조 하세요.

Visual Studio에서는 다음을 수행하는 XAML을 생성합니다.

- 항목을 끌어 온 컨테이너의 리소스에 새 <xref:System.Windows.Data.CollectionViewSource>를 추가합니다. <xref:System.Windows.Data.CollectionViewSource>는 서비스에서 반환하는 개체에 있는 데이터를 탐색하고 표시하는 데 사용할 수 있는 개체입니다.

- 컨트롤에 대한 데이터 바인딩을 만듭니다. 디자이너의 기존 컨트롤로 항목을 끌면 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)]이 컨트롤을 항목에 바인딩합니다. 항목을 컨테이너로 끌어 오면는 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 끌어 온 항목에 대해 선택한 컨트롤을 만들고 컨트롤을 항목에 바인딩합니다. 이 컨트롤은 새로운 <xref:System.Windows.Controls.Grid> 내에 만들어집니다.

### <a name="objects"></a>개체

**데이터 소스** 창에서 디자이너로 개체 또는 속성을 끌어 오면 Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 데이터 바인딩된 컨트롤을 만들거나 기존 컨트롤을 개체나 속성에 바인딩하는을 생성 합니다. 그러나 Visual Studio에서는 데이터를 사용 하 여 개체를 채우는 코드를 생성 하지 않습니다. 이 코드를 직접 작성해야 합니다.

> [!NOTE]
> 사용자 지정 클래스는 public 이어야 하며 기본적으로 매개 변수가 없는 생성자가 있어야 합니다. 구문에서 "점"을 포함 하는 중첩 된 클래스 일 수 없습니다. 자세한 내용은 [WPF에 대 한 XAML 및 사용자 지정 클래스](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf)를 참조 하세요.

Visual Studio에서 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 다음을 수행 하는을 생성 합니다.

- 항목을 끌어 온 컨테이너의 리소스에 새 <xref:System.Windows.Data.CollectionViewSource>를 추가합니다. <xref:System.Windows.Data.CollectionViewSource>는 개체에 있는 데이터를 탐색하고 표시하는 데 사용할 수 있는 개체입니다.

- 컨트롤에 대한 데이터 바인딩을 만듭니다. 디자이너의 기존 컨트롤로 항목을 끌면 XAML이 컨트롤을 항목에 바인딩합니다. 항목을 컨테이너로 끌어 오면 XAML은 끌어 온 항목에 대해 선택한 컨트롤을 만들고 컨트롤을 항목에 바인딩합니다. 이 컨트롤은 새로운 <xref:System.Windows.Controls.Grid> 내에 만들어집니다.

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
