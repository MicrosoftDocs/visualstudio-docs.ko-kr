---
title: SharePoint 솔루션 패키징 및 배포 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a4bf3394cf47b4f355fbe6a330ff5374e2da1c9
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015593"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>SharePoint 솔루션 패키징 및 배포
  일반적으로 SharePoint 솔루션은 솔루션 패키지 (.wsp) 파일을 사용 하 여 SharePoint 서버에 배포 됩니다. Visual Studio를 사용 하 여 SharePoint 프로젝트 항목을 기능으로 구성 하 고 SharePoint 기능을 배포 하는 패키지를 만들 수 있습니다.

 이 항목에서는 다음 정보를 제공합니다.

- [기능 및 패키지 만들기](#create-features-and-packages)

- [기능 및 패키징 도구 지원](#feature-and-packaging-tool-support)

- [SharePoint 솔루션 배포](#deploy-sharepoint-solutions)

- [SharePoint 솔루션에서 파일 배포](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>기능 및 패키지 만들기
 Visual Studio를 사용 하 여 관련 SharePoint 요소를 *기능*으로 그룹화 할 수 있습니다. 예를 들어 연락처 목록 정의의 기능에는 목록 인스턴스 및 목록 정의가 포함 될 수 있습니다. 이러한 두 요소를 배포 목적으로 단일 기능으로 결합할 수 있습니다. 기능에 대 한 자세한 내용은 [문서 블록: 기능](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))을 참조 하세요.

 그런 다음 SharePoint 솔루션 패키지 (*.wsp*)를 만들어 여러 기능, 사이트 정의, 어셈블리 및 기타 파일을 단일 패키지로 묶을 수 있습니다. 그러면 파일은 sharepoint에서 서버에 파일을 배포 하는 데 필요한 형식으로 저장 됩니다. 자세한 내용은 [빌딩 Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14))을 참조 하세요.

## <a name="feature-and-packaging-tool-support"></a>기능 및 패키징 도구 지원
 Visual Studio의 SharePoint 개발 도구를 사용 하 여 쉽게 배포할 수 있도록 SharePoint 파일을 기능 및 솔루션 패키지로 신속 하 게 구성할 수 있습니다. 다음 도구를 사용 하 여 기능 및 솔루션 패키지를 구성할 수 있습니다.

- 기능 디자이너 및 패키지 디자이너.

- 패키징 탐색기, 도구 창

- 솔루션 탐색기.

### <a name="feature-designer-and-package-designer"></a>기능 디자이너 및 패키지 디자이너
 기능 디자이너를 사용 하 여 기능을 만들고, 범위를 설정 하 고, 다른 기능을 종속성으로 표시할 수 있습니다. 또한 디자이너에는 각 기능을 설명 하는 최종 XML 파일이 표시 됩니다. 자세한 내용은 [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)를 참조 하세요.

 기능 디자이너에서 해당 *범위* 를 설정 하 여 특정 웹 사이트 또는 웹 사이트 그룹에 기능을 적용 합니다. 개별 웹 사이트에 대해 기능을 활성화 하는 경우이 기능은 특정 웹 사이트 에서만 작동 합니다. 사이트 모음에 대해 기능을 활성화 한 경우 기능의 항목은 전체 사이트 모음에 적용 됩니다. 자세한 내용은 [요소 범위](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14))를 참조 하세요.

 기능이 다른 기능을 사용 하는 경우 기능 *활성화 종속성* 을 설정 하 여 기능을 사용 하도록 설정 하기 전에 종속 기능을 표시할 수 있습니다. 기능 활성화 종속성은 종속 기능이 해당 범위에서 이미 활성화 되어 있는지 확인 합니다. 자세한 내용은 [활성화 종속성 및 범위](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14))를 참조 하세요.

 패키지 디자이너에서 SharePoint 요소를 단일 솔루션 패키지로 그룹화 하 고 배포 중에 웹 서버를 다시 설정할지 여부를 구성할 수 있습니다. 배포 서버 유형을 설정 하려면 **속성** 창을 사용 합니다. 또한 디자이너는 패키지 콘텐츠를 설명 하는 XML 파일을 생성 합니다. 자세한 내용은 [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)를 참조 하세요.

 배포 하는 동안 인터넷 정보 서비스 (IIS) 서비스를 중지 하 여 솔루션 파일을 SharePoint 서버에 복사 합니다. Visual Studio의 패키지 디자이너를 사용 하 여 웹 서버를 다시 시작할지 여부를 선택할 수 있습니다. 프런트 엔드 웹 서버 또는 응용 프로그램 서버에 솔루션을 배포 하는 경우 구성 하려면 **속성** 창을 사용 합니다. 자세한 내용은 [Solution 요소 (solution)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14))를 참조 하세요.

### <a name="packaging-explorer"></a>패키징 탐색기
 기능 디자이너 및 패키지 디자이너를 보완 하기 위해 패키징 탐색기를 사용 하 여 SharePoint 파일을 기능과 패키지로 그룹화 할 수 있습니다. 또한 패키지, 기능, SharePoint 프로젝트 항목 및 파일의 계층 구조 보기를 볼 수 있습니다. 패키징 탐색기는 다음 작업을 완료 하는 데 사용할 수 있는 도구 창입니다.

- SharePoint 프로젝트 항목 및 파일을 엽니다.

- 한 기능에서 다른 기능으로 SharePoint 프로젝트 항목을 끌어서 놓습니다.

- SharePoint 프로젝트 항목과 기능을 패키지 간에 끌어서 놓습니다.

- 패키지에 새 기능을 추가 합니다.

- 기능 또는 패키지 디자이너를 엽니다.

- 기능 및 패키지의 유효성을 검사 합니다.

  Visual Studio의 SharePoint 개발 도구에는 솔루션 패키지가 올바르게 구성 되었는지 확인 하는 데 도움이 되는 유효성 검사 규칙이 포함 되어 있습니다. 또한이 규칙은 *.wsp* 솔루션 파일이 SharePoint 서버에서 성공적으로 배포 및 활성화 될 수 있는지 확인 합니다. 기능의 XML 스키마에 대 한 자세한 내용은 [기능 스키마](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))를 참조 하세요.

  SharePoint 프로젝트 시스템에 사용자 지정 기능 및 패키지 유효성 검사 규칙을 추가할 수 있습니다. 자세한 내용은 [방법: SharePoint 솔루션에 대 한 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)를 참조 하세요.

  패키징 탐색기에 대 한 자세한 내용은 [방법: 패키징 탐색기를 사용 하 여 패키지에 기능 및 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)를 참조 하세요.

### <a name="solution-explorer"></a>솔루션 탐색기
 솔루션 탐색기를 사용 하 여 SharePoint 프로젝트의 파일을 탐색 하 고 열 수 있습니다. 솔루션 탐색기의 상황에 맞는 메뉴를 사용 하 여 기능, 기능 이벤트 수신자 및 기능 리소스를 추가 합니다. 또한 기능 디자이너 및 패키지 디자이너를 열어 배포용 기능과 패키지를 구성할 수 있습니다.

## <a name="deploy-sharepoint-solutions"></a>SharePoint 솔루션 배포
 Visual Studio에서 기능 및 패키지를 사용자 지정한 후에는 *.wsp* 파일을 만들어 SharePoint 서버에 배포할 수 있습니다. Visual Studio를 사용 하 여를 디버깅 하 고 테스트할 수 있습니다. 배포 컴퓨터의 SharePoint 서버에만 *wsp* 원격 SharePoint 서버에 SharePoint 솔루션을 배포 하는 방법에 대 한 자세한 내용은 [솔루션 배포](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14))를 참조 하세요.

 개발 컴퓨터에서 배포 단계를 사용자 지정할 수도 있습니다. 자세한 내용은 [SharePoint 솔루션 패키지 배포, 게시 및 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)를 참조 하세요.

## <a name="deploy-files-in-sharepoint-solutions"></a>SharePoint 솔루션에서 파일 배포
 일반적으로 sharepoint 프로젝트 항목을 SharePoint 솔루션에 추가 하면 필요한 모든 파일이 포함 됩니다. 컴파일할 수 있는 파일 (코드 파일)은 솔루션의 출력 어셈블리에 빌드됩니다. 그러나 컴파일되지 않은 파일 (예: *.xml*, *.txt*또는 리소스 파일)을 SharePoint 프로젝트에 추가 해야 할 수도 있습니다. 이러한 파일은 솔루션에 자동으로 패키지 되지 않습니다. 패키지가 패키지 되도록 하려면 매핑된 폴더 또는 SharePoint 프로젝트 항목에 파일을 추가 합니다.

 매핑된 폴더에 추가 된 파일은 솔루션을 배포할 때 자동으로 SharePoint 하이브에 복사 됩니다. SharePoint 프로젝트 항목에 추가 되는 파일은 배포 **유형** 속성에 따라 부분적으로 설정 된 각 파일에 대 한 **배포 위치** 속성에 지정 된 위치에 배포 됩니다. 기본적으로 **배포 유형** 속성 값은 **nodeployment**입니다. 즉, 파일이 솔루션과 함께 배포 되지 않습니다. 패키지에 파일을 포함 하려면 속성에 대해 다른 값을 설정 해야 합니다.

 예를 들어, SharePoint 프로젝트에 .xml 파일을 추가 하려면 다음 작업 중 하나를 수행 *합니다* .

- SharePoint "레이아웃" 매핑된 폴더를 프로젝트에 추가 합니다. 이는 프로젝트에 대 한 하위 폴더가 있는 **레이아웃** 이라는 폴더를 **솔루션 탐색기** 에 만듭니다. 새 하위 폴더에 *.xml* 파일을 추가 합니다. 기본적으로 파일은의 SharePoint 파일 시스템에 배포 *됩니다. \\ATE\레이아웃 \\ \<Folder Name> *. 매핑된 폴더를 추가 하는 방법에 대 한 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조 하세요.

- *.Xml* 파일을 SharePoint 프로젝트 항목의 폴더에 추가한 다음, *.Xml* 파일의 **배포 유형** 속성을 **Nodeployment** 에서 **rootfile** 또는 **elementfile**과 같은 다른 설정으로 변경 합니다. 적절 한 **배포 유형** 설정은 파일 및 프로젝트에 따라 다릅니다. **배포 유형** 속성 설정에 대 한 자세한 내용은 [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)을 참조 하세요.

  추가 된 파일이 솔루션의 특정 프로젝트에 적용 되지 않는 경우 솔루션에 빈 SharePoint 프로젝트를 추가한 다음 추가 파일을 추가할 수 있습니다. SharePoint에 파일을 배포 하는 또 다른 대안은 특히 콘텐츠 데이터베이스에 모듈을 추가한 다음 모듈에 추가 하는 것입니다. 자세한 내용은 [모듈을 사용 하 여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
