---
title: 데이터에 컨트롤 바인딩
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
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673042"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio에서 데이터에 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터를 컨트롤에 바인딩하여 애플리케이션 사용자에게 데이터를 표시할 수 있습니다. **데이터 소스** 창에서 Visual Studio의 화면에 있는 컨트롤 또는 디자인 화면으로 항목을 끌어 이러한 데이터 바인딩된 컨트롤을 만들 수 있습니다.

 이 항목에서는 데이터 바인딩된 컨트롤을 만드는 데 사용할 수 있는 데이터 소스에 대해 설명합니다. 또한 데이터 바인딩과 관련된 일반적인 작업에 대해서도 설명합니다. 데이터 바인딩된 컨트롤을 만드는 방법에 대 한 자세한 내용은 [Visual studio에서 데이터에 컨트롤 Windows Forms 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) 및 [visual studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

## <a name="data-sources"></a>데이터 원본
 데이터 바인딩 컨텍스트에서 데이터 원본은 사용자 인터페이스에 바인딩할 수 있는 메모리의 데이터를 나타냅니다. 실제로 데이터 소스는 Entity Framework 클래스, 데이터 집합, .NET 프록시 개체에서 캡슐화 되는 서비스 끝점, LINQ to SQL 클래스 또는 .NET 개체나 컬렉션 일 수 있습니다. 일부 데이터 소스의 경우 **데이터 원본** 창에서 항목을 끌어 데이터에 바인딩된 컨트롤을 만들도록 설정하지만 모든 데이터 원본이 그러한 것은 아닙니다. 다음 표에서는 어떠한 데이터 소스가 지원되는지 보여 줍니다.

|데이터 원본|**Windows Forms 디자이너**에서의 끌어서 놓기 지원|**WPF 디자이너**에서의 끌어서 놓기 지원|**Silverlight 디자이너**에서의 끌어서 놓기 지원|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|데이터 세트|예|예|예|
|엔터티 데이터 모델|예<sup>1</sup>|예|예|
|LINQ to SQL 클래스|아니요<sup>2</sup>|아니요<sup>2</sup>|아니요<sup>2</sup>|
|[!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF 서비스, 웹 서비스 등의 서비스|예|예|예|
|Object|예|예|예|
|SharePoint|예|예|예|

 1. **엔터티 데이터 모델** 마법사를 사용 하 여 모델을 생성 한 다음 해당 개체를 디자이너로 끌어 옵니다.

 2. LINQ to SQL 클래스는 **데이터 원본** 창에 표시되지 않습니다. 그러나 LINQ to SQL 클래스에 기반하는 개체 데이터 소스를 새로 만든 다음 해당 개체를 디자이너로 끌어 와 데이터 바인딩된 컨트롤을 만들 수는 있습니다. 자세한 내용은 [연습: LINQ to SQL 클래스 만들기 (O-R 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)를 참조 하세요.

## <a name="data-sources-window"></a>데이터 소스 창
 데이터 원본은 프로젝트에서 **데이터 원본** 창의 항목으로 사용할 수 있습니다. 이 창은 폼 디자인 화면이 프로젝트의 활성 창이 면 표시 되거나 **보기** 메뉴에서 액세스할 수 있습니다. 이 창에서 항목을 끌어 기본 데이터에 바인딩된 컨트롤을 만들 수 있으며, 마우스 오른쪽 단추를 클릭 하 여 데이터 소스를 구성할 수도 있습니다.

 ![데이터 소스 창](../data-tools/media/raddata-data-sources-window.png "raddata 데이터 소스 창")

 **데이터 원본** 창에 표시되는 각 데이터 형식의 경우 디자이너로 항목을 끌 때 기본 컨트롤이 만들어집니다. **데이터 소스** 창에서 항목을 끌기 전에 생성 되는 컨트롤을 변경할 수 있습니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

## <a name="tasks-involved-in-binding-controls-to-data"></a>컨트롤을 데이터에 바인딩하는 것과 관련된 작업
 다음 표에서는 컨트롤을 데이터에 바인딩하기 위해 수행 하는 가장 일반적인 몇 가지 작업을 보여 줍니다.

|Task|추가 정보|
|----------|----------------------|
|**데이터 원본** 창을 엽니다.|편집기에서 디자인 화면을 열고 **View**  >  **데이터 원본**보기를 선택 합니다.|
|프로젝트에 데이터 원본을 추가합니다.|[새 데이터 원본 추가](../data-tools/add-new-data-sources.md)|
|**데이터 원본** 창의 항목을 디자이너로 끌 때 만들어지는 컨트롤을 설정합니다.|[데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|**데이터 원본** 창의 항목과 연결되는 컨트롤 목록을 수정합니다.|[데이터 소스 창에 사용자 지정 컨트롤 추가](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|데이터 바인딩된 컨트롤을 만듭니다.|[Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|개체 또는 컬렉션에 바인딩합니다.|[Visual Studio에서 개체 바인딩](../data-tools/bind-objects-in-visual-studio.md)|
|UI에 표시 되는 데이터를 필터링 합니다.|[Windows Forms 애플리케이션에서 데이터 필터링 및 정렬](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|컨트롤의 캡션을 사용자 지정 합니다.|[Visual Studio에서 데이터 바인딩된 컨트롤에 대한 캡션을 만드는 방식 사용자 지정](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>관련 항목
 [.Net 용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms 데이터 바인딩](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
