---
title: 이미지를 사용 하 여 사용자 지정 마스터 페이지 & 사이트 페이지로 가져오기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 311124b2e0b81e70c4c2a7b40754207e6c66b749
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015693"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>연습: 이미지를 사용 하 여 사용자 지정 마스터 페이지 및 사이트 페이지 가져오기
  이 연습에서는 SharePoint 사용자 지정 마스터 페이지와 이미지를 포함 하는 사이트 페이지를 sharepoint 프로젝트로 가져오는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 이 연습에서는 다음 작업을 수행 하는 방법을 보여 줍니다.

- SharePoint 디자이너에서 이미지를 사용 하 여 사용자 지정 마스터 페이지 및 사이트 페이지를 만듭니다.

- 사용자 지정 마스터 페이지, 이미지 및 사이트 페이지를 SharePoint 솔루션 (*.wsp*) 파일로 내보냅니다.

- *.wsp* [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Sharepoint 솔루션 패키지 가져오기 프로젝트를 사용 하 여 .wsp 파일을 가져와서 sharepoint 프로젝트에 배포 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 다음 구성 요소가 있어야 합니다.

- 및 SharePoint의 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]

- Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>SharePoint 디자이너에서 항목 만들기
 이 예제에서는 사용자 지정 마스터 페이지, 사용자 지정 마스터 페이지를 참조 하는 사이트 페이지 및 사이트 페이지에 표시 되는 이미지 파일을 내보내기 위해 SharePoint 디자이너에서 세 개의 항목을 만드는 방법을 보여 줍니다. 이미지가 SharePoint의/images/폴더에 추가 됩니다.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>SharePoint 디자이너에서 사용자 지정 마스터 페이지를 만들려면

1. SharePoint 디자이너의 탐색 창에서 **마스터 페이지** 사이트 개체를 선택 합니다.

2. **마스터 페이지** 리본에서 **빈 마스터 페이지**를 선택 합니다.

3. 새 마스터 페이지를 선택한 다음 **마스터 페이지** 리본에서 **파일 편집**을 선택 합니다.

4. SharePoint 디자이너의 맨 아래에서 **코드** 탭을 선택 합니다.

5. 기존 태그를 다음 태그로 바꿉니다.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. 페이지를 저장 하 고 **마스터 페이지** 탭을 선택 하 고 마스터 페이지의 이름을 **mybasic1**로 바꿉니다.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint 디자이너에서 콘텐츠 데이터베이스에 이미지 추가
 이제 사이트 페이지에 표시할 이미지를 추가할 수 있습니다. 이미지는 SharePoint 콘텐츠 데이터베이스에 배포 됩니다.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>SharePoint 디자이너에서 콘텐츠 데이터베이스에 이미지를 추가 하려면

1. 탐색 창에서 **모든 파일** 사이트 개체를 선택한 다음 트리 뷰에서 **images** 폴더를 선택 합니다.

2. **모든 파일** 리본에서 **파일 가져오기**를 선택 하 고 원하는 파일을 선택한 다음 **확인** 단추를 선택 합니다. 이 예에서는 파일 이름이 **myimg1.png**입니다.

     필요에 따라 이미지를 구성 하는 데 도움이 되는 하위 폴더를 만들 수 있습니다.

3. **가져오기** 대화 상자를 닫습니다.

## <a name="create-a-site-page"></a>사이트 페이지 만들기
 이 기본 사이트 페이지에서는 사용자 지정 마스터 페이지를 사용 하 고 이전 단계에서 추가한 이미지를 표시 합니다.

#### <a name="to-create-a-site-page"></a>사이트 페이지를 만들려면

1. 탐색 창에서 **사이트 페이지** 개체를 선택 합니다.

2. **페이지 리본에서** **페이지** 단추를 선택 하 고, **ASPX** 페이지 유형을 선택한 다음, 새 파일의 이름을 **mycontentpage1**로 설정 합니다.

     필요한 경우 사이트 페이지를 구성 하는 데 도움이 되는 하위 폴더를 만들 수 있습니다.

3. 사이트 페이지 목록에서 **MyContentPage1** 를 선택 하 여 해당 속성 페이지를 연 다음 페이지 맨 아래에서 **파일 편집** 링크를 선택 합니다.

     메시지가 표시 되는 경우이 페이지에 안전 모드에서 편집할 수 있는 지역이 없고 고급 모드에서이 페이지를 열지 여부를 묻는 메시지가 표시 되 면 **예** 단추를 선택 합니다.

4. 페이지 맨 아래에서 **코드** 단추를 선택 합니다.

5. 기존 태그를 다음 태그로 바꿉니다.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. 업데이트 된 사이트 페이지를 저장 합니다.

## <a name="export-the-items-from-sharepoint"></a>SharePoint에서 항목 내보내기
 SharePoint에서 SharePoint 솔루션 파일 (*.wsp*)로 항목을 내보냅니다.

#### <a name="to-export-items-from-sharepoint-designer"></a>SharePoint 디자이너에서 항목을 내보내려면

1. SharePoint 디자이너의 탐색 창에서 **팀 사이트** 개체를 선택한 다음 **사이트** 리본에서 **템플릿으로 저장**을 선택 합니다.

2. **템플릿으로 저장** 대화 상자에서 파일 이름 및 템플릿 이름을 입력 하 고 **콘텐츠 포함** 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

     이렇게 하면 사이트의 내용이 *.wsp* 파일에 저장 됩니다.

3. 솔루션이 내보내기 후 **솔루션 갤러리** 링크를 선택 하 여 사용 가능한 솔루션 파일 목록을 표시 합니다.

4. 새 *.wsp* 파일에 대 한 바로 가기 메뉴를 열고 다른 **이름으로 대상 저장** 을 선택 하 여 시스템에 저장 합니다.

## <a name="import-the-items-into-visual-studio"></a>Visual Studio로 항목 가져오기
 *.Wsp* 파일을로 가져옵니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 콘텐츠를 가져온 후 사용자 지정 하 고, 항목을 추가 하 고, 배포할 수 있습니다.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>.Wsp 파일에서 Visual Studio로 항목을 가져오려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **SharePoint 2010 솔루션 패키지 가져오기** 프로젝트를 만듭니다.

2. **가져올 항목 선택** 페이지의 **유형** 열에서 **모듈** 의 가져오기에 대 한 다음 표에 있는 파일의 확인란을 선택 합니다.

   | 파일 이름 | 설명 |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | 사용자 지정 마스터 페이지입니다. |
   | images_ | SharePoint 파일 시스템의 이미지 파일입니다. |
   | SitePages_ | 사이트 페이지입니다. |

3. **마침** 단추를 선택 하 여 선택한 항목을 가져옵니다.

4. **솔루션 탐색기**에서 \_ catalogsmasterpage \_ 노드를 선택 하 고 **배포 충돌 해결** 속성의 값을 **자동**으로 설정 합니다.

    이렇게 하면 배포 충돌을 자동으로 해결할 수 있습니다.

5. 새 마스터 페이지의 이름이 기존 페이지의 이름과 같을 경우 기존 페이지가 SharePoint 디자이너의 기본 마스터 페이지나 사용자 지정 마스터 페이지로 표시 되어 있지 않은지 확인 합니다.

    기존 마스터 페이지가 기본 마스터 페이지 또는 사용자 지정 마스터 페이지로 표시 되는 경우 마스터 페이지를 삭제할 수 없다는 배포 오류가 발생 합니다. 이 문제를 방지 하려면 다음을 수행 합니다.

   - 기존 마스터 페이지가 기본 마스터 페이지로 설정 된 경우 일시적으로 다른 마스터 페이지를 기본 마스터 페이지로 설정 합니다. SharePoint에 파일을 배포한 후 새 마스터 페이지를 기본 마스터 페이지로 설정 합니다.

   - 기존 마스터 페이지가 사용자 지정 마스터 페이지로 설정 된 경우 일시적으로 다른 마스터 페이지를 사용자 지정 마스터 페이지로 설정 합니다. SharePoint에 파일을 배포한 후 새 마스터 페이지를 사용자 지정 마스터 페이지로 설정 합니다.

6. 메뉴 모음에서 **빌드**  >  **솔루션 배포**를 선택 합니다.

7. SharePoint 사이트를 열어 배포 된 항목을 확인 합니다.

   파일로 파일을 가져와서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint에 배포 하는 다른 방법은에서 모듈에 파일을 추가 하는 것입니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][방법: 마스터 페이지 또는 테마 가져오기](../sharepoint/how-to-import-a-master-page-or-theme.md) 및 [모듈을 사용 하 여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)

## <a name="see-also"></a>추가 정보
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
