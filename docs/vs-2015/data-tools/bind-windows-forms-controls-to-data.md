---
title: Windows Forms 컨트롤을 데이터에 바인딩 | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672967"
---
# <a name="bind-windows-forms-controls-to-data"></a>데이터에 Windows Forms 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**데이터 소스** 창에서 Windows form으로 또는 폼의 기존 컨트롤로 개체를 끌어 데이터 소스를 컨트롤에 바인딩할 수 있습니다. 항목을 끌기 전에 바인딩하려는 컨트롤의 형식을 설정할 수 있습니다. 테이블 자체를 선택 하는지 아니면 개별 열을 선택 하는지에 따라 다른 값이 표시 됩니다.  사용자 지정 값을 설정할 수도 있습니다. 테이블의 경우 "세부 정보"는 각 열이 별도의 컨트롤에 바인딩되어 있음을 의미 합니다.

 ![DataGridView에 데이터 소스 바인딩](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata 데이터 소스를 DataGridView에 바인딩")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView 컨트롤의 데이터에 바인딩
 DataGridView의 경우 전체 테이블이 해당 단일 컨트롤에 바인딩됩니다. DataGridView를 폼으로 끌면 레코드 탐색을 위한 도구 스트립 ( <xref:System.Windows.Forms.BindingNavigator> )도 표시 됩니다. [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter <xref:System.Windows.Forms.BindingSource> 및가 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다. 다음 그림에서는 Customers 테이블에 Orders 테이블과의 관계가 있으므로 TableAdapterManager도 추가 되었습니다. 이러한 변수는 모두 자동 생성 코드에서 form 클래스의 private 멤버로 선언 됩니다. DataGridView를 채우기 위한 자동 생성 코드는 form_load 이벤트 처리기에 있습니다. 데이터베이스를 업데이트 하기 위해 데이터를 저장 하는 코드는 BindingNavigator의 저장 이벤트 처리기에 있습니다. 필요에 따라이 코드를 이동 하거나 수정할 수 있습니다.

 ![BindingNavigator를 사용 하는 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView (BindingNavigator 포함)")

 각각의 오른쪽 위 모퉁이에 있는 스마트 태그를 클릭 하 여 DataGridView 및 BindingNavigator의 동작을 사용자 지정할 수 있습니다.

 ![DataGridView 및 바인딩 탐색기 스마트 태그](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 및 바인딩 탐색기 스마트 태그")

 응용 프로그램에 필요한 컨트롤을 **데이터 소스** 창에서 사용할 수 없는 경우 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤 추가](../data-tools/add-custom-controls-to-the-data-sources-window.md)를 참조 하세요.

 **데이터 소스** 창에서 폼에 이미 있는 컨트롤로 항목을 끌어와 서 컨트롤을 데이터에 바인딩할 수도 있습니다. 이미 데이터에 바인딩된 컨트롤의 데이터 바인딩이 가장 최근에 끌어온 항목으로 다시 설정 됩니다. 유효한 놓기 대상이 되려면 컨트롤이 **데이터 소스** 창에서 끌어 온 항목의 기본 데이터 형식을 표시할 수 있어야 합니다. 예를 들어 데이터 형식이 인 항목을로 끌 수 없습니다 <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> .는 날짜를 표시할 수 없기 때문입니다 <xref:System.Windows.Forms.CheckBox> .

## <a name="bind-to--data-in-individual-controls"></a>개별 컨트롤의 데이터에 바인딩
 데이터 원본을 "세부 정보"에 바인딩하면 데이터 집합의 각 열이 별도의 컨트롤에 바인딩됩니다.

 ![세부 정보에 데이터 소스 바인딩](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 데이터 원본에 대 한 바인딩 정보")

> [!IMPORTANT]
> 위의 그림에서는 Orders 테이블이 아니라 Customers 테이블의 Orders 속성에서 끌어 옵니다. Customer. Orders 속성에 바인딩하면 DataGridView에서 수행 된 탐색 명령이 details 컨트롤에 즉시 반영 됩니다. Orders 테이블에서 끌어 오면 컨트롤이 데이터 집합에 계속 바인딩되어 있지만 DataGridView와 동기화 되지 않습니다.

 다음 그림은 Customers 테이블의 Orders 속성이 **데이터 소스** 창에서 "세부 정보"에 바인딩된 후 폼에 추가 되는 기본 데이터 바인딩된 컨트롤을 보여 줍니다.

 ![세부 정보에 바인딩된 Orders 테이블](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 테이블 바인딩 세부 정보")

 또한 각 컨트롤에는 스마트 태그가 있습니다. 이 태그를 사용 하면 해당 컨트롤에만 적용 되는 사용자 지정이 가능 합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
