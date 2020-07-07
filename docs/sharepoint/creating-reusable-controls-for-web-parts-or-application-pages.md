---
title: 웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기 | Microsoft Docs
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
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015145"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기
  Visual Studio에서는 SharePoint에서 실행되는 애플리케이션 페이지와 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만들 수 있습니다. 이러한 컨트롤을 사용자 정의 컨트롤 이라고 합니다. 사용자 정의 컨트롤은 ASP.NET 웹 페이지와 매우 유사 하 게 작동 하는 일종의 복합 컨트롤입니다. 사용자 정의 컨트롤에 기존 웹 서버 컨트롤과 태그를 추가 하 고 컨트롤에 대 한 속성 및 메서드를 정의할 수 있습니다. 그런 다음 ASP.NET 웹 페이지에 포함할 수 있습니다. 여기서는 하나의 단위로 작동 합니다.

## <a name="create-a-user-control"></a>사용자 정의 컨트롤 만들기
 사용자 정의 컨트롤을 만들려면 **빈 SharePoint 프로젝트**에 **사용자 정의 컨트롤** 을 추가 합니다. 자세한 내용은 [방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)를 참조 하세요.

 **사용자 정의 컨트롤** 항목을 추가 하는 경우 Visual Studio는 프로젝트에 폴더를 만든 다음 여러 개의 파일을 폴더에 추가 합니다. 다음 표에서는 각 파일에 대해 설명 합니다.

|파일|Description|
|----------|-----------------|
|사용자 정의 컨트롤 파일|사용자 정의 컨트롤을 정의 합니다. 컨트롤과 태그를이 파일에 추가 하 여 사용자 정의 컨트롤을 디자인 합니다.|
|코드 파일|사용자 컨트롤 뒤에 코드를 포함 합니다. 이 파일에 대 한 이벤트를 처리 하는 코드를 추가 합니다.|
|디자이너 코드 파일|디자이너에서 생성 된 코드를 포함 하며 직접 편집 하면 안 됩니다.|

## <a name="design-the-user-control"></a>사용자 정의 컨트롤 디자인
 Visual Studio의 Visual Web Developer designer를 사용 하 여 사용자 정의 컨트롤을 디자인 합니다. 이 디자이너는 프로젝트에서 사용자 정의 컨트롤 파일을 열고 **디자인** 탭을 선택할 때 나타납니다.

## <a name="consume-the-user-control"></a>사용자 정의 컨트롤 사용
 사용자 정의 컨트롤은 응용 프로그램 페이지 또는 웹 파트에 포함 될 때까지 SharePoint에 표시 되지 않습니다.

 응용 프로그램 페이지에 사용자 정의 컨트롤을 포함 하려면 ASP.NET 사용자 정의 컨트롤을 추가 하려는 웹 페이지를 엽니다. 디자인 뷰로 전환한 다음 솔루션 탐색기에서 사용자 지정 사용자 정의 컨트롤 파일을 선택 하 여 페이지로 끌어옵니다. ASP.NET 사용자 정의 컨트롤이 페이지에 추가 되 고 디자이너는 페이지에서 사용자 정의 컨트롤을 인식 하는 데 필요한 @ Register 지시문을 만듭니다. 이제 컨트롤의 공용 속성 및 메서드를 사용할 수 있습니다.

 웹 파트에 사용자 정의 컨트롤을 포함 하려면 웹 파트 코드 파일의 웹 파트 컬렉션에 사용자 정의 컨트롤을 추가 합니다 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> . 다음 예제에서는 <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> 웹 파트의 컬렉션에 사용자 정의 컨트롤을 추가 합니다.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>사용자 정의 컨트롤 디버그
 사용자 정의 컨트롤을 디버깅 하려면 사용자 정의 컨트롤이 SharePoint 프로젝트의 응용 프로그램 페이지 또는 웹 파트에 포함 되어 있는지 확인 합니다. 그런 다음 Visual Studio 프로젝트에서 코드를 디버그할 때 처럼 사용자 정의 컨트롤에서 코드를 디버그할 수 있습니다.

 Visual Studio 디버거를 시작 하면 Visual Studio에서 SharePoint 사이트를 엽니다.

 SharePoint에서 사용자 정의 컨트롤을 포함 하는 응용 프로그램 페이지를 엽니다. 사용자 정의 컨트롤이 웹 파트에 포함 되어 있는 경우 SharePoint의 웹 파트 페이지에 웹 파트를 추가 합니다.

 SharePoint 프로젝트를 디버깅 하는 방법에 대 한 자세한 내용은 [sharepoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)을 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[방법: SharePoint 응용 프로그램 페이지 또는 웹 파트에 대 한 사용자 정의 컨트롤 만들기](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|SharePoint에서 실행 되는 응용 프로그램 페이지 및 웹 파트에서 사용할 수 있는 재사용 가능한 사용자 지정 컨트롤을 만드는 방법을 보여 줍니다.|
