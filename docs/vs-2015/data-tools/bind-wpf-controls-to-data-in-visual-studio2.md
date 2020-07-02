---
title: 데이터에 WPF 컨트롤 바인딩 (2 부) | Microsoft Docs
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540090"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Visual Studio에서 데이터에 WPF 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] **소스** 창을 사용 하 여 데이터 바인딩된 컨트롤을 만들 수 있습니다. 먼저 **데이터 소스 창에** 데이터 소스를 추가 합니다. 그런 다음 **데이터 소스** 창에서**WPF Designer**로 항목을 끌어 옵니다.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a>데이터 소스 창에 데이터 소스 추가
 데이터 바인딩된 컨트롤을 만들려면 **먼저 데이터 소스 창에** 데이터 소스를 추가 해야 합니다.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>데이터 소스 창에 데이터 소스를 추가하려면

1. **보기** 메뉴에서 **다른 창**을 가리킨 다음 **데이터 원본**을 클릭 합니다.

2. **새 데이터 원본 추가**를 클릭하고 **데이터 원본 구성 마법사** 완료합니다.

3. 다음 작업 중 하나를 수행하여 데이터 바인딩된 컨트롤을 만듭니다.

    - [단일 데이터 필드에 바인딩되는 컨트롤 만들기](#simple)

    - [여러 데이터 필드에 바인딩되는 컨트롤 만들기](#complex)

    - [여러 데이터 필드에 바인딩되는 컨트롤 집합 만들기](#details)

    - [디자이너의 기존 컨트롤에 데이터 바인딩](#existing)

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a>단일 데이터 필드에 바인딩되는 컨트롤 만들기
 **데이터 소스 창에** 데이터 소스를 추가한 후 또는와 같은 단일 데이터 필드를 표시 하는 새 데이터 바인딩된 컨트롤을 만들 수 있습니다 <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>단일 데이터 필드에 바인딩되는 컨트롤을 만들려면

1. **데이터 소스** 창에서 테이블이 나 개체를 나타내는 항목을 확장 합니다. 바인딩할 열이나 속성을 나타내는 자식 항목을 찾습니다. 시각적 예제는 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)을 참조 하세요.

2. 원하는 경우 만들 컨트롤을 선택합니다. **데이터 소스** 창의 각 항목에는 디자이너로 항목을 끌 때 생성 되는 기본 컨트롤이 있습니다. 기본 컨트롤은 항목의 기본 데이터 형식에 따라 달라집니다.

     다른 컨트롤을 선택하려면 항목 옆의 드롭다운 화살표를 클릭하고 컨트롤을 선택합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

3. 항목을 디자이너의 유효한 컨테이너로 끌어 옵니다. 유효한 컨테이너에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]컨테이너에 새 데이터 바인딩된 컨트롤과 적절 한 제목을 만듭니다 <xref:System.Windows.Controls.Label> . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]또한 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 는 컨트롤을 데이터에 바인딩하기 위한 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a>여러 데이터 필드에 바인딩되는 컨트롤 만들기
 **데이터 소스 창에** 데이터 소스를 추가한 후 또는와 같은 여러 데이터 필드를 표시 하는 새 데이터 바인딩된 컨트롤을 만들 수 있습니다 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>여러 데이터 필드에 바인딩되는 컨트롤을 만들려면

1. **데이터 소스** 창에서 테이블이 나 개체를 나타내는 항목을 선택 합니다. 시각적 예제는 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)을 참조 하세요.

2. 원하는 경우 만들 컨트롤을 선택합니다. 기본적으로 데이터 테이블이 나 개체를 나타내는 **데이터 소스** 창의 각 항목은 <xref:System.Windows.Controls.DataGrid> (프로젝트를 대상으로 하는 경우 .NET Framework 4) 또는 <xref:System.Windows.Controls.ListView> (이전 버전의 .NET Framework)를 만들기 위해 설정 됩니다.

     다른 컨트롤을 선택하려면 항목 옆의 드롭다운 화살표를 클릭하고 컨트롤을 선택합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

    > [!NOTE]
    > 특정 열이나 속성을 표시하지 않으려면 항목을 확장하여 해당 자식을 표시합니다. 표시 하지 않을 열 또는 속성 옆에 있는 드롭다운 화살표를 클릭 하 고 **없음**을 클릭 합니다.

3. <xref:System.Windows.Controls.Grid>와 같은 디자이너의 유효한 컨테이너로 항목을 끌어 옵니다. 유효한 컨테이너에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]컨테이너에 새 데이터 바인딩된 컨트롤을 만듭니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]또한 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 는 컨트롤을 데이터에 바인딩하기 위한 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a>여러 데이터 필드에 바인딩되는 컨트롤 집합 만들기
 **데이터 소스 창에** 데이터 소스를 추가한 후에는 데이터 테이블이 나 개체를 컨트롤 집합에 바인딩할 수 있습니다. 테이블이나 개체의 각 열 또는 속성에 대해 서로 다른 컨트롤이 만들어집니다.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>여러 데이터 필드에 바인딩되는 컨트롤 집합을 만들려면

1. **데이터 소스** 창에서 테이블이 나 개체를 나타내는 항목을 선택 합니다. 시각적 예제는 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)을 참조 하세요.

2. 항목 옆에 있는 드롭다운 화살표를 클릭 하 고 **세부 정보**를 선택 합니다.

    > [!NOTE]
    > 특정 열이나 속성을 표시하지 않으려면 항목을 확장하여 해당 자식을 표시합니다. 표시 하지 않을 열 또는 속성 옆에 있는 드롭다운 화살표를 클릭 하 고 **없음**을 클릭 합니다.

3. <xref:System.Windows.Controls.Grid>와 같은 디자이너의 유효한 컨테이너로 항목을 끌어 옵니다. 유효한 컨테이너에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]컨테이너에 새 데이터 바인딩된 컨트롤을 만듭니다. 각 컨트롤은 적절한 제목을 가진 <xref:System.Windows.Controls.Label> 컨트롤과 함께 서로 다른 열이나 속성에 바인딩됩니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]또한는 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 컨트롤을 데이터에 바인딩하기 위한 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a>디자이너의 기존 컨트롤에 데이터 바인딩
 **데이터 소스 창에** 데이터 소스를 추가한 후에는 디자이너의 기존 컨트롤에 데이터 바인딩을 추가할 수 있습니다.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>디자이너의 기존 컨트롤에 데이터를 바인딩하려면

1. **데이터 소스** 창에서 다음 절차 중 하나를 사용 합니다.

    - <xref:System.Windows.Controls.DataGrid> 또는 <xref:System.Windows.Controls.ListView>와 같이 여러 데이터 필드를 표시하는 기존 컨트롤에 대한 데이터 바인딩을 추가하려면 컨트롤에 바인딩할 테이블이나 개체를 나타내는 항목을 선택합니다.

    - <xref:System.Windows.Controls.ComboBox> 또는 <xref:System.Windows.Controls.TextBox>와 같이 단일 데이터 필드를 표시하는 기존 컨트롤에 대한 데이터 바인딩을 추가하려면 데이터가 포함된 테이블 또는 개체를 나타내는 항목을 확장한 다음 컨트롤에 바인딩할 데이터를 나타내는 항목을 선택합니다.

2. 선택한 항목을 **데이터 소스** 창에서 디자이너의 기존 컨트롤로 끌어 옵니다. 컨트롤은 유효한 놓기 대상이어야 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)][!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)]컨트롤을 데이터에 바인딩하기 위한 코드를 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

    > [!NOTE]
    > 컨트롤이 이미 데이터에 바인딩된 경우 컨트롤의 데이터 바인딩이 가장 최근에 컨트롤로 끌어 온 항목으로 다시 설정됩니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) wpf [응용 프로그램에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-wpf-applications.md) wpf 응용 프로그램에서 [관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md) wpf 컨트롤을 데이터 [집합에 바인딩](../data-tools/bind-wpf-controls-to-a-dataset.md) wpf 컨트롤을 [WCF 데이터 서비스에](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) 바인딩 [연습: wpf 응용 프로그램에서 관련 데이터 표시](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
