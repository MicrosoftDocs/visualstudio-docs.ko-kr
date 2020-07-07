---
title: '연습: SharePoint 응용 프로그램 페이지 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76375c15077bf672eaba01c840ba406228046435
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016493"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>연습: SharePoint 응용 프로그램 페이지 만들기

응용 프로그램 페이지는 ASP.NET 페이지의 특수 한 형태입니다. 응용 프로그램 페이지에는 SharePoint 마스터 페이지와 병합 된 콘텐츠가 포함 되어 있습니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

이 연습에서는 응용 프로그램 페이지를 만든 다음 로컬 SharePoint 사이트를 사용 하 여 디버그 하는 방법을 보여 줍니다. 이 페이지에는 각 사용자가 서버 팜의 모든 사이트에서 만들었거나 수정한 모든 항목이 표시 됩니다.

이 연습에서는 다음 작업을 수행합니다.

- SharePoint 프로젝트 만들기
- SharePoint 프로젝트에 응용 프로그램 페이지 추가
- 응용 프로그램 페이지에 ASP.NET 컨트롤을 추가 하는 중입니다.
- ASP.NET 컨트롤 뒤에 코드를 추가 합니다.
- 응용 프로그램 페이지 테스트

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

- 지원 되는 버전의 Windows 및 SharePoint

## <a name="create-a-sharepoint-project"></a>SharePoint 프로젝트 만들기

먼저 **빈 SharePoint 프로젝트**를 만듭니다. 나중에이 프로젝트에 **응용 프로그램 페이지** 항목을 추가 합니다.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **새 프로젝트** 대화 상자를 열고 사용 하려는 언어 아래의 **Office/SharePoint** 노드를 확장 한 다음 **SharePoint 솔루션** 노드를 선택 합니다.

3. **Visual Studio에 설치 된 템플릿** 창에서 **SharePoint 2010-빈 프로젝트** 템플릿을 선택 합니다. 프로젝트 이름을 **MySharePointProject**로 지정한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다. 이 마법사를 사용 하 여 프로젝트를 디버깅 하는 데 사용할 사이트와 솔루션의 신뢰 수준을 선택할 수 있습니다.

4. **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 하 여 기본 로컬 SharePoint 사이트를 적용 합니다.

## <a name="create-an-application-page"></a>응용 프로그램 페이지 만들기

응용 프로그램 페이지를 만들려면 프로젝트에 **응용 프로그램 페이지** 항목을 추가 합니다.

1. **솔루션 탐색기**에서 **MySharePointProject** 프로젝트를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **새 항목 추가** 대화 상자에서 **응용 프로그램 페이지 (팜 솔루션 전용 템플릿)** 를 선택 합니다.

4. 페이지의 이름을 **Searchitems**로 지정한 다음 **추가** 단추를 선택 합니다.

     Visual Web Developer designer는 페이지의 HTML 요소를 볼 수 있는 **소스** 뷰에 응용 프로그램 페이지를 표시 합니다. 디자이너에 여러 컨트롤의 태그가 표시 됩니다 <xref:System.Web.UI.WebControls.Content> . 각 컨트롤은 <xref:System.Web.UI.WebControls.ContentPlaceHolder> 기본 응용 프로그램 마스터 페이지에 정의 된 컨트롤에 매핑됩니다.

## <a name="design-the-layout-of-the-application-page"></a>응용 프로그램 페이지의 레이아웃 디자인

응용 프로그램 페이지 항목을 사용 하면 디자이너를 사용 하 여 응용 프로그램 페이지에 ASP.NET 컨트롤을 추가할 수 있습니다. 이 디자이너는 Visual Web Developer에서 사용 되는 것과 같은 디자이너입니다. 디자이너의 **소스** 뷰에 레이블, 라디오 단추 목록 및 테이블을 추가한 다음 표준 ASP.NET 페이지를 디자인할 때와 동일한 방법으로 속성을 설정 합니다.

1. 메뉴 모음에서 **View**  >  **도구 상자**보기를 선택 합니다.

2. **도구 상자**의 표준 노드에서 다음 단계 중 하나를 수행 합니다.

    - **레이블** 항목에 대 한 바로 가기 메뉴를 열고 **복사**를 선택 하 고 디자이너의 **PlaceHolderMain** content 컨트롤 아래에 있는 줄의 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    - **레이블** 항목을 **도구 상자** 에서 **PlaceHolderMain** 콘텐츠 컨트롤의 본문으로 끌어 놓습니다.

3. 이전 단계를 반복 하 여 **DropDownList** 항목 및 **테이블** 항목을 **PlaceHolderMain** 콘텐츠 컨트롤에 추가 합니다.

4. 디자이너에서 `Text` label 컨트롤의 특성 값을 변경 하 여 **모든 항목을 표시**합니다.

5. 디자이너에서 `<asp:DropDownList>` 요소를 다음 XML로 바꿉니다.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>페이지에서 컨트롤의 이벤트를 처리 합니다.

ASP.NET 페이지와 마찬가지로 응용 프로그램 페이지에서 컨트롤을 처리 합니다. 이 절차에서는 `SelectedIndexChanged` 드롭다운 목록의 이벤트를 처리 합니다.

1. **보기** 메뉴에서 **코드**를 선택 합니다.

     응용 프로그램 페이지 코드 파일이 코드 편집기에서 열립니다.

2. `SearchItems` 클래스에 다음 메서드를 추가합니다. 이 코드는 <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> <xref:System.Web.UI.WebControls.DropDownList> 이 연습의 뒷부분에서 만들 메서드를 호출 하 여의 이벤트를 처리 합니다.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. 응용 프로그램 페이지 코드 파일의 맨 위에 다음 문을 추가 합니다.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. `SearchItems` 클래스에 다음 메서드를 추가합니다. 이 메서드는 서버 팜의 모든 사이트를 반복 하 고 현재 사용자가 만들거나 수정한 항목을 검색 합니다.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. `SearchItems` 클래스에 다음 메서드를 추가합니다. 이 메서드는 현재 사용자가 테이블에서 만들었거나 수정한 항목을 표시 합니다.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>응용 프로그램 페이지 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열리고 응용 프로그램 페이지가 나타납니다.

1. **솔루션 탐색기**에서 응용 프로그램 페이지에 대 한 바로 가기 메뉴를 열고 **시작 항목으로 설정**을 선택 합니다.

2. **F5** 키를 선택합니다.

     SharePoint 사이트가 열립니다.

3. 응용 프로그램 페이지에서 **수정한 사람** 옵션을 선택 합니다.

     응용 프로그램 페이지가 새로 고쳐지고 서버 팜의 모든 사이트에서 수정한 모든 항목이 표시 됩니다.

4. 응용 프로그램 페이지의 목록에서 **만든 사람** 을 선택 합니다.

     응용 프로그램 페이지가 새로 고쳐지고 서버 팜의 모든 사이트에서 만든 모든 항목이 표시 됩니다.

## <a name="next-steps"></a>다음 단계

SharePoint 응용 프로그램 페이지에 대 한 자세한 내용은 [sharepoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

다음 항목에서 Visual Web Designer를 사용 하 여 SharePoint 페이지 콘텐츠를 디자인 하는 방법에 대해 자세히 알아볼 수 있습니다.

- [SharePoint 용 웹 파트를 만듭니다](../sharepoint/creating-web-parts-for-sharepoint.md).

- [웹 파트 또는 응용 프로그램 페이지에 다시 사용할 수 있는 컨트롤을 만듭니다](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>참고 항목

[방법: 응용 프로그램 페이지 만들기](../sharepoint/how-to-create-an-application-page.md) 
 [응용 프로그램 _Layouts 페이지 유형](/previous-versions/office/aa979604(v=office.14))
