---
title: SharePoint 솔루션을 원격으로 배포, 게시, & 업그레이드
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- remote deployment [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, remote deployment
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f05f42f8aed35696b962e71a5fce86c2956b3661
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016807"
---
# <a name="how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server"></a>방법: 원격 서버에서 SharePoint 솔루션 배포, 게시 및 업그레이드
  로컬 시스템에 SharePoint 솔루션을 배포 하는 것 외에도 샌드박스가 적용 된 SharePoint 솔루션을 원격 사이트 또는 로컬 SharePoint 사이트에 게시할 수 있습니다. 원격 게시 프로세스는 .wsp 파일을 SharePoint 서버에 복사 하 고, 솔루션을 설치한 후 솔루션을 활성화할 수 있도록 합니다 *.* 변경한 후 원격 SharePoint 솔루션 설치를 업그레이드할 수도 있습니다.

## <a name="to-publish-a-sandboxed-sharepoint-solution-to-a-remote-sharepoint-server"></a>샌드박스 SharePoint 솔루션을 원격 SharePoint 서버에 게시 하려면

1. **솔루션 탐색기**에서 게시 하려는 샌드박스가 적용 된 SharePoint 프로젝트에 대 한 바로 가기 메뉴를 열고 **게시**를 선택 합니다.

2. **게시** 대화 상자에서 **SharePoint 사이트에 게시** 옵션 단추를 선택한 다음 온라인 게시 사이트의 URL (예:)을 입력 `https://mytestsite.sharepoint.microsoftonline.com` 합니다.

3. 게시 한 후 솔루션 **갤러리** 페이지에서 솔루션 목록을 보려면 **게시 후 브라우저 옵션 단추에서 솔루션 갤러리 열기 페이지** 를 선택 합니다.

4. **게시** 단추를 선택합니다.

5. 사용자 인증이 필요한 경우 원격 서버에 로그인 합니다.

     게시 진행률이 Visual Studio **출력** 창에 표시 됩니다. 프로세스가 완료 되 면 솔루션 (*.wsp*) 파일이 원격 SharePoint 서버에 설치 됩니다. 그러나 SharePoint에서 사용 하려면 먼저 활성화 되어 있어야 합니다.

6. **솔루션 갤러리** 페이지에서 SharePoint 응용 프로그램을 선택 하 고 리본에서 **활성화** 단추를 선택 합니다.

7. **솔루션 활성화** 대화 상자의 리본에서 **활성화** 단추를 다시 선택 합니다.

     **솔루션 갤러리** 페이지의 **상태** 열에는 응용 프로그램이 활성화 되어 있음을 나타냅니다.

## <a name="to-upgrade-a-sandboxed-sharepoint-solution-on-a-remote-sharepoint-server"></a>원격 SharePoint 서버에서 샌드박스 SharePoint 솔루션을 업그레이드 하려면
 샌드 박싱된 SharePoint 솔루션이 원격 서버에 이미 게시 된 경우에서 응용 프로그램을 변경한 후 다음 프로세스를 통해 업그레이드할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. 에서 SharePoint 패키지의 이름을 바꿉니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 이렇게 하려면에서 패키지를 **솔루션 탐색기** 엽니다. **패키지 탐색기**에 나타납니다.

2. **패키지 탐색기**의 **이름** 상자에서 패키지 이름을 고유한 이름으로 변경 합니다.

3. 프로젝트를 저장합니다.

4. **솔루션 탐색기**에서 프로젝트에 대 한 바로 가기 메뉴를 열고 **게시**를 선택 합니다.

5. **게시** 대화 상자에서 **SharePoint 사이트에 게시** 옵션 단추를 선택한 후 솔루션이 저장 된 원격 서버의 URL이 없는 경우 해당 URL을 입력 합니다.

6. 게시 한 후 솔루션 **갤러리** 페이지에서 솔루션 목록을 보려면 **게시 후 브라우저 옵션 단추에서 솔루션 갤러리 열기 페이지** 를 선택 합니다.

7. **게시** 단추를 선택합니다.

8. 사용자 인증이 필요한 경우 원격 서버에 로그인 합니다.

     최근에 원격 서버에 로그인 한 경우 인증이 필요 하지 않을 수 있습니다.

     이름이 같은 이전 버전의 응용 프로그램이 SharePoint 서버에 여전히 있는 경우 이름이 같은 패키지가 SharePoint 서버에 이미 존재 한다는 오류가 표시 됩니다. 게시 하기 전에 패키지 이름을 고유한 이름으로 바꾸어야 합니다.

9. SharePoint에서 새 응용 프로그램을 선택 하 고 리본에서 **업그레이드** 단추를 선택 합니다.

10. **업그레이드 솔루션** 대화 상자의 리본에서 **업그레이드** 단추를 다시 선택 합니다. **솔루션 갤러리** 페이지의 **상태** 열에는 이제 응용 프로그램이 활성화 된 것으로 표시 됩니다.

     이전 버전의 솔루션이 비활성화 되 고 새 버전의 솔루션이 이전 솔루션에서 유지 관리 되는 데이터로 업그레이드 되며 새 솔루션이 SharePoint에서 활성화 됩니다.

## <a name="see-also"></a>추가 정보
- [방법: 로컬 SharePoint 사이트에 SharePoint 솔루션 배포 및 게시](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)
- [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)
- [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [방법: 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
