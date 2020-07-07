---
title: '방법: 마스터 페이지 또는 테마 가져오기 | Microsoft Docs'
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
ms.openlocfilehash: 7abca9e9141fdc8d4540e8a38e9579862fc540f1
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015296"
---
# <a name="how-to-import-a-master-page-or-theme"></a>방법: 마스터 페이지 또는 테마 가져오기
  마스터 페이지와 테마를 만들고 사용 하 여 SharePoint 사이트의 페이지를 일관 된 모양으로 지정할 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]는 이러한 요소에 대 한 템플릿을 제공 하지 않지만 SharePoint 디자이너에서 만든 다음로 가져올 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 자세한 내용은 Microsoft 웹 사이트의 [구성 요소: 페이지 및 사용자 인터페이스](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) 를 참조 하세요.

### <a name="to-import-a-master-page-or-theme"></a>마스터 페이지 또는 테마를 가져오려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트를 만들거나 엽니다.

     SharePoint 프로젝트를 만드는 방법에 대 한 자세한 내용은 [sharepoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **새 항목 추가** 대화 상자에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. SharePoint 템플릿 목록에서 **모듈** 템플릿을 선택 하 고 모듈의 이름을 지정 합니다.

     모듈에는 SharePoint에서 지정 하는 위치에 배포할 파일 (예: 마스터 페이지 또는 테마 파일)이 포함 되어 있습니다.

5. 모듈에서 이름이 *Sample.txt*기본 파일을 삭제 합니다.

6. 모듈 노드를 선택 합니다.

7. 메뉴 모음에서 **프로젝트**  >  **기존 항목 추가**를 선택한 다음 마스터 페이지 또는 테마 파일을 선택 합니다.

     마스터 페이지 파일의 확장명은 .master 이며 테마 파일의 확장명은 thmx입니다.

8. 마스터 페이지를 추가한 경우 모듈의 속성에서 해당 **배포 충돌 해결** 설정을 **자동** 으로 변경 합니다.

    > [!NOTE]
    > 마스터 페이지의 이름이 기본 마스터 페이지 또는 사용자 지정 마스터 페이지로 표시 된 기존 마스터 페이지의 이름과 같을 경우 오류가 발생할 수 있습니다. 이 문제를 해결 하는 방법에 대 한 자세한 내용은 [연습: 이미지를 사용 하 여 사용자 지정 마스터 페이지 및 사이트 페이지 가져오기](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)를 참조 하세요.

9. 모듈에서 *Elements.xml*를 엽니다.

     추가한 마스터 페이지나 테마를 참조 하도록 *Elements.xml* 파일을 업데이트 해야 합니다.

10. 마스터 페이지의 경우 기존 모듈 태그를 다음 태그로 바꿉니다.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     테마의 경우 기존 모듈 태그를 다음 태그로 바꿉니다.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     자리 표시자 값을 모듈과 마스터 페이지나 테마의 실제 이름으로 바꾸어야 합니다.

     특성은 `Type="GhostableInLibrary"` 항목이 콘텐츠 데이터베이스에 추가 됨을 나타내고, `Url` 모듈의 특성은 SharePoint 콘텐츠 데이터베이스에 파일을 저장할 위치를 지정 합니다.

11. 마스터 페이지의 배포 범위를 변경 하려면 **솔루션 탐색기**의 기능 디자이너에서 기능 파일을 열고 **범위** 목록에서 새 배포 범위를 선택 합니다.

     **웹** 값은 마스터 페이지가 현재 프로젝트에 지정 된 웹 사이트에만 적용 됨을 의미 합니다. **Site** 값은 마스터 페이지가 현재 사이트 모음에 적용 됨을 의미 합니다. 여기에는 모든 하위 사이트와 루트 웹이 포함 됩니다. 다른 값은 적용 되지 않습니다.

    > [!NOTE]
    > 테마는 사이트 모음 수준에만 적용 되므로 테마의 범위를 **사이트**이외의 값으로 설정 하지 않는 것이 좋습니다. 하위 사이트에서 테마를 사용 하는 경우 오류가 발생할 수 있습니다.

12. 메뉴 모음에서 **빌드**  >  **솔루션 배포**를 선택 합니다.

13. 파일이 제대로 배포 되었는지 확인 하려면 SharePoint 사이트를 열고 **사이트 작업** 메뉴를 선택한 후 **사이트 설정** 명령을 선택 하 고 **마스터 페이지** 링크 또는 **테마** 링크를 선택 합니다.

     마스터 페이지 또는 테마 목록이 표시 되 고 가져온 마스터 페이지나 테마가 포함 됩니다.

## <a name="see-also"></a>참고 항목
- [마스터 페이지](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint에 대 한 페이지 만들기](../sharepoint/creating-pages-for-sharepoint.md)
- [모듈을 사용 하 여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)
