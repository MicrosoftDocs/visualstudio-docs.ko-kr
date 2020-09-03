---
title: WPF 응용 프로그램에서 관련 데이터 표시 | Microsoft Docs
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6efa79fc59ed9812cf6162096dd462100b71fbca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672410"
---
# <a name="display-related-data-in-wpf-applications"></a>WPF 애플리케이션에서 관련 데이터 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일부 응용 프로그램에서는 여러 테이블이 나 부모-자식 관계에서 서로 관련 된 엔터티에서 제공 되는 데이터로 작업 하는 것이 좋습니다. 예를 들어 테이블의 고객을 표시 하는 표를 표시할 수 있습니다 `Customers` . 사용자가 특정 고객을 선택 하면 다른 표에는 관련 테이블에서 해당 고객에 대 한 주문이 표시 됩니다 `Orders` .

 **데이터 소스** 창에서 WPF 디자이너로 항목을 끌어 관련 데이터를 표시 하는 데이터 바인딩된 컨트롤을 만들 수 있습니다.

## <a name="to-create-controls-that-display-related-records"></a>관련 레코드를 표시 하는 컨트롤을 만들려면

1. **데이터** 메뉴에서 **데이터 원본 표시**를 클릭하여 **데이터 원본** 창을 엽니다.

2. **새 데이터 원본 추가**를 클릭하고 **데이터 원본 구성 마법사** 완료합니다.

3. WPF 디자이너를 열고 디자이너에 **데이터 소스** 창의 항목에 대 한 유효한 놓기 대상인 컨테이너가 포함 되어 있는지 확인 합니다.

     유효한 놓기 대상에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

4. **데이터 소스** 창에서 관계의 부모 테이블이 나 개체를 나타내는 노드를 확장 합니다. 부모 테이블 또는 개체가 일 대 다 관계의 "일" 쪽에 있습니다.

5. 부모 노드 또는 부모 노드의 모든 개별 항목을 **데이터 소스** 창에서 디자이너의 유효한 놓기 대상으로 끌어 옵니다.

     Visual Studio는 끌어 온 각 항목에 대해 새로운 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. 또한 XAML은 <xref:System.Windows.Data.CollectionViewSource> 부모 테이블이 나 개체에 대 한 새를 놓기 대상의 리소스에 추가 합니다. 일부 데이터 원본의 경우에는 Visual Studio에서 부모 테이블이 나 개체에 데이터를 로드 하는 코드도 생성 합니다. 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

6. **데이터 소스** 창에서 관련 자식 테이블이 나 개체를 찾습니다. 관련 자식 테이블 및 개체가 부모 노드의 데이터 목록 아래쪽에 확장 가능한 노드로 표시 됩니다.

7. 자식 노드 (또는 자식 노드의 모든 개별 항목)를 **데이터 소스** 창에서 디자이너의 유효한 놓기 대상으로 끌어 옵니다.

     Visual Studio는 끌어 온 각 항목에 대해 새로운 데이터 바인딩된 컨트롤을 만드는 XAML을 생성 합니다. 또한 XAML은 <xref:System.Windows.Data.CollectionViewSource> 자식 테이블이 나 개체에 대 한 새를 놓기 대상의 리소스에 추가 합니다. 이 새로운 <xref:System.Windows.Data.CollectionViewSource> 는 방금 디자이너로 끌어온 부모 테이블이 나 개체의 속성에 바인딩됩니다. 일부 데이터 원본의 경우에는 Visual Studio에서 자식 테이블이 나 개체에 데이터를 로드 하는 코드도 생성 합니다.

     다음 그림에서는 **데이터 소스** 창에서 데이터 집합에 있는 **Customers** 테이블의 관련 **Orders** 테이블을 보여 줍니다.

     ![관계를 보여 주는 데이터 소스 창](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>관련 항목
 [Visual studio에서 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) visual [studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [wpf 응용 프로그램에서 조회 테이블 만들기](../data-tools/create-lookup-tables-in-wpf-applications.md) [연습: wpf 응용 프로그램에서 관련 데이터 표시](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
