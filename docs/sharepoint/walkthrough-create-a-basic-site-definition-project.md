---
title: '연습: 기본 사이트 정의 프로젝트 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c06f4df5d1efe06ad2537bd2e65f2c239f3be2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016762"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>연습: 기본 사이트 정의 프로젝트 만들기
  이 연습에서는 일부 컨트롤을 포함 하는 시각적 웹 파트를 포함 하는 기본 사이트 정의를 만드는 방법을 보여 줍니다. 명확 하 게 하기 위해 만드는 시각적 웹 파트에는 몇 개의 컨트롤만 있습니다. 그러나 더 많은 기능을 포함 하는 보다 정교한 SharePoint 사이트 정의를 만들 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- 프로젝트 템플릿을 사용 하 여 사이트 정의 만들기 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]

- SharePoint에서 사이트 정의를 사용 하 여 SharePoint 사이트 만들기

- 시각적 웹 파트를 솔루션에 추가 합니다.

- 새 시각적 웹 파트를 추가 하 여 사이트의 default.aspx 페이지를 사용자 지정 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전. 자세한 내용은 SharePoint 솔루션 개발을 위한 요구 사항을 참조 하세요.

- Visual Studio.

## <a name="create-a-site-definition-solution"></a>사이트 정의 솔루션 만들기
 먼저에서 사이트 정의 프로젝트를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>사이트 정의 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다. IDE가 Visual Basic 개발 설정을 사용 하도록 설정 된 경우 메뉴 모음에서 **파일**  >  **새로 만들기 프로젝트**를 선택 합니다.

    **새 프로젝트** 대화 상자가 나타납니다.

2. **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. **템플릿** 목록에서 **SharePoint 2010 프로젝트** 템플릿을 선택 합니다.

4. **이름** 상자에 **testsitedef**를 입력 하 고 **확인** 단추를 선택 합니다.

    **SharePoint 사용자 지정 마법사** 가 나타납니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 사이트 정의를 디버그할 SharePoint 사이트의 URL을 입력 하거나 기본 위치 (Http://<em>시스템 이름</em>/)를 사용 합니다.

6. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

    모든 사이트 정의 프로젝트를 팜 솔루션으로 배포 해야 합니다. 샌드박스 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **마침** 단추를 선택합니다.

    프로젝트가 **솔루션 탐색기**에 나타납니다.

8. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

9. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

10. **템플릿** 창에서 **사이트 정의** 템플릿을 선택 하 고 **이름을** **SiteDefinition1**로 지정한 다음 **추가** 단추를 선택 합니다.

## <a name="create-a-visual-web-part"></a>시각적 웹 파트 만들기
 그런 다음 사이트 정의의 기본 페이지에 표시 되는 시각적 웹 파트를 만듭니다.

#### <a name="to-create-a-visual-web-part"></a>비주얼 웹 파트를 만들려면

1. **솔루션 탐색기**에서 **모든 파일 표시** 단추를 선택 합니다.

2. **SiteDefinition1** 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

3. **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. 템플릿 목록에서 **비주얼 웹 파트** 템플릿을 선택 하 고 기본 이름인 VisualWebPart1을 유지 한 다음 **추가** 단추를 선택 합니다.

     *VisualWebPart1* 파일이 열립니다.

5. *VisualWebPart1*의 맨 아래에 다음 태그를 추가 하 여 텍스트 상자, 단추 및 레이블의 세 가지 컨트롤을 폼에 추가 합니다.

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. *VisualWebPart1*에서 *VisualWebPart1.ascx.cs* 파일 (의 경우) [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] 또는 *VisualWebPart1* (의 경우 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] )을 열고 다음 코드를 추가 합니다.

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     이 코드는 웹 파트의 단추 클릭에 대 한 기능을 추가 합니다.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>기본 ASPX 페이지에 비주얼 웹 파트 추가
 다음으로, 사이트 정의의 기본 ASPX 페이지에 비주얼 웹 파트를 추가 합니다.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>기본 ASPX 페이지에 비주얼 웹 파트를 추가 하려면

1. Default.aspx 페이지를 연 다음 태그 아래에 다음 줄을 추가 합니다 `WebPartPages` .

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     이 줄은 이름이 MyWebPartControls와 웹 파트 및 해당 코드를 연결 합니다. *Namespace* 매개 변수는 *VisualWebPart1* 코드 파일에서 사용 되는 네임 스페이스와 일치 합니다.

2. 요소 뒤에서 `</asp:Content>` 전체 `ContentPlaceHolderId="PlaceHolderMain"` 섹션과 해당 내용을 다음 코드로 바꿉니다.

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     이 코드는 이전에 만든 비주얼 웹 파트에 대 한 참조를 만듭니다.

3. **솔루션 탐색기**에서 **SiteDefinition1** 노드의 바로 가기 메뉴를 열고 **시작 항목으로 설정**을 선택 합니다.

## <a name="deploy-and-run-the-site-definition-solution"></a>사이트 정의 솔루션 배포 및 실행
 그런 다음 프로젝트를 SharePoint에 배포 하 고 프로젝트를 실행 합니다.

#### <a name="to-deploy-and-run-the-site-definition"></a>사이트 정의를 배포 및 실행하려면

- 메뉴 모음에서 **빌드**  >  **testsitedef 배포**를 선택 합니다.

- **F5** 키를 선택합니다.

     Visual Studio는 코드를 컴파일하고 해당 기능을 추가 하 고 모든 파일을 SharePoint 솔루션 (WSP) 파일에 패키지 한 다음 WSP 파일을 SharePoint 서버에 배포 합니다. 그런 다음 SharePoint에서 파일을 설치 하 고 기능을 활성화 합니다.

## <a name="create-a-site-based-on-the-site-definition"></a>사이트 정의를 기반으로 사이트 만들기
 다음으로 새 사이트 정의를 사용 하 여 사이트를 만듭니다.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>사이트 정의를 사용 하 여 사이트를 만들려면

1. SharePoint 사이트에 새 SharePoint 사이트 페이지가 나타납니다.

2. **제목 및 설명** 섹션에서 제목에 대해 **새 사이트** 를 입력 하 고 사이트에 대 한 설명을 입력 합니다.

3. **웹 사이트 주소** 섹션에서 **URL 이름** 상자에 **mynewsite** 을 입력 합니다.

4. **템플릿** 섹션에서 **SharePoint 사용자 지정** 탭을 선택 합니다.

5. **템플릿 선택** 목록에서 **SiteDefinition1**를 선택 합니다.

6. 다른 설정은 기본값으로 유지 하 고 **만들기** 단추를 선택 합니다.

     새 사이트가 나타납니다.

## <a name="test-the-new-site"></a>새 사이트 테스트
 그런 다음 새 사이트를 테스트 하 여 제대로 작동 하는지 확인 합니다.

#### <a name="to-test-the-new-site"></a>새 사이트를 테스트 하려면

- 기본 ASPX 페이지에서 텍스트를 입력 한 다음 텍스트 상자 옆에 있는 **레이블 텍스트 변경** 단추를 선택 합니다.

     텍스트는 단추 오른쪽의 레이블에 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
