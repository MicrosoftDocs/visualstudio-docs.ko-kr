---
title: 웹 파트 또는 애플리케이션 페이지용 재사용 가능 컨트롤 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015145"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>웹 파트 또는 애플리케이션 페이지용 재사용 가능 컨트롤 만들기
  Visual Studio에서는 SharePoint에서 실행되는 애플리케이션 페이지와 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만들 수 있습니다. 해당 컨트롤을 사용자 정의 컨트롤이라고 합니다. 사용자 정의 컨트롤은 ASP.NET 웹 페이지와 유사하게 작동하는 일종의 복합 컨트롤입니다. 사용자 정의 컨트롤에 기존 웹 서버 컨트롤 및 태그를 추가하고 컨트롤의 속성과 메서드를 정의할 수 있습니다. 그런 다음 ASP.NET 웹 페이지에 포함할 수 있으며, 여기서는 하나의 단위로 작동합니다.

## <a name="create-a-user-control"></a>사용자 정의 컨트롤 만들기
 사용자 정의 컨트롤을 만들려면 **빈 SharePoint 프로젝트**에 **사용자 정의 컨트롤**을 추가합니다. 자세한 내용은 [방법: SharePoint 애플리케이션 페이지 또는 웹 파트용 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)를 참조하세요.

 **사용자 정의 컨트롤** 항목을 추가하면 Visual Studio에서 프로젝트에 폴더를 생성하고 여러 개의 파일을 폴더에 추가합니다. 다음 표에서는 각 파일에 관해 설명합니다.

|파일|설명|
|----------|-----------------|
|사용자 정의 컨트롤 파일|사용자 정의 컨트롤을 정의합니다. 이 파일에 컨트롤과 태그를 추가하여 사용자 정의 컨트롤을 디자인합니다.|
|코드 파일|사용자 정의 컨트롤의 숨김 코드를 포함합니다. 이 파일에 이벤트 처리 코드를 추가합니다.|
|디자이너 코드 파일|디자이너에서 생성된 코드를 포함하며 직접 편집할 수 없습니다.|

## <a name="design-the-user-control"></a>사용자 정의 컨트롤 디자인
 Visual Studio의 Visual Web Developer 디자이너를 사용하여 사용자 정의 컨트롤을 디자인합니다. 이 디자이너는 프로젝트에서 사용자 정의 컨트롤 파일을 열고 **디자인** 탭을 선택하면 나타납니다.

## <a name="consume-the-user-control"></a>사용자 정의 컨트롤 사용
 사용자 정의 컨트롤은 애플리케이션 페이지 또는 웹 파트에 포함해야 SharePoint에 표시됩니다.

 애플리케이션 페이지에 사용자 정의 컨트롤을 포함하려면 ASP.NET 사용자 정의 컨트롤을 추가할 웹 페이지를 엽니다. 디자인 뷰로 전환한 다음, 솔루션 탐색기에서 사용자 지정 사용자 정의 컨트롤 파일을 선택하고 페이지로 끌어옵니다. ASP.NET 사용자 정의 컨트롤이 페이지에 추가되고, 디자이너에서 페이지가 사용자 정의 컨트롤을 인식하는 데 필요한 @ Register 지시문을 만듭니다. 이제 컨트롤의 퍼블릭 속성과 메서드를 사용할 수 있습니다.

 웹 파트에 사용자 정의 컨트롤을 포함하려면 웹 파트 코드 파일의 웹 파트 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 컬렉션에 사용자 정의 컨트롤을 추가합니다. 다음 예제에서는 웹 파트의 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 컬렉션에 사용자 정의 컨트롤을 추가합니다.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>사용자 정의 컨트롤 디버그
 사용자 정의 컨트롤을 디버그하려면 사용자 정의 컨트롤이 SharePoint 프로젝트의 애플리케이션 페이지 또는 웹 파트에 포함되어 있는지 확인합니다. 그런 다음, Visual Studio 프로젝트에서 코드를 디버그하는 것과 마찬가지로 사용자 정의 컨트롤에서 코드를 디버그할 수 있습니다.

 Visual Studio 디버거를 시작하면 Visual Studio에서 SharePoint 사이트가 열립니다.

 SharePoint에서 사용자 정의 컨트롤이 포함된 애플리케이션 페이지를 엽니다. 사용자 정의 컨트롤이 웹 파트에 포함된 경우 SharePoint의 웹 파트 페이지에 웹 파트를 추가합니다.

 SharePoint 프로젝트를 디버그하는 방법에 대한 자세한 내용은 [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 애플리케이션 페이지 또는 웹 파트용 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint에서 실행되는 애플리케이션 페이지와 웹 파트에 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
