---
title: SharePoint 솔루션 패키지 및 배포 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015593"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>SharePoint 솔루션 패키지 및 배포
  일반적으로 SharePoint 솔루션은 솔루션 패키지(.wsp) 파일을 사용하여 SharePoint Server에 배포됩니다. Visual Studio를 사용하여 SharePoint 프로젝트 항목을 기능으로 구성하고 패키지를 만들어 SharePoint 기능을 배포할 수 있습니다.

 이 항목에서는 다음 정보를 제공합니다.

- [기능 및 패키지 만들기](#create-features-and-packages)

- [기능 및 패키징 도구 지원](#feature-and-packaging-tool-support)

- [SharePoint 솔루션 배포](#deploy-sharepoint-solutions)

- [SharePoint 솔루션에 파일 배포](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>기능 및 패키지 만들기
 Visual Studio를 사용하여 관련 SharePoint 요소를 ‘기능’으로 그룹화할 수 있습니다. 예를 들어 연락처 목록 정의 기능에는 목록 인스턴스와 목록 정의가 포함될 수 있습니다. 배포 목적으로 두 요소를 단일 기능으로 결합할 수 있습니다. 기능에 대한 자세한 내용은 [구성 요소: 기능](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14))을 참조하세요.

 그런 다음, SharePoint 솔루션 패키지( *.wsp*)를 만들어 여러 개의 기능, 사이트 정의, 어셈블리, 기타 파일을 단일 패키지로 묶을 수 있습니다. 패키지에는 SharePoint에서 파일을 서버에 배포하는 데 필요한 형식으로 파일이 저장됩니다. 자세한 내용은 [구성 요소: 솔루션](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14))을 참조하세요.

## <a name="feature-and-packaging-tool-support"></a>기능 및 패키징 도구 지원
 Visual Studio의 SharePoint 개발 도구를 사용하여 간편한 배포를 위해 SharePoint 파일을 기능 및 솔루션 패키지로 신속하게 구성할 수 있습니다. 다음 도구를 사용하여 기능 및 솔루션 패키지를 구성할 수 있습니다.

- 기능 디자이너 및 패키지 디자이너

- 패키징 탐색기, 도구 창

- 솔루션 탐색기.

### <a name="feature-designer-and-package-designer"></a>기능 디자이너 및 패키지 디자이너
 기능 디자이너를 사용하여 기능을 만들고, 범위를 설정하고, 다른 기능을 종속성으로 표시할 수 있습니다. 또한 디자이너에는 각 기능을 설명하는 최종 XML 파일이 표시됩니다. 자세한 내용은 [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)를 참조하세요.

 기능 디자이너에서 ‘범위’를 설정하여 특정 웹 사이트 또는 웹 사이트 그룹에 기능을 적용합니다. 개별 웹 사이트에 대해 활성화한 기능은 특정 웹 사이트에서만 작동합니다. 사이트 모음에 대해 기능을 활성화한 경우에는 기능의 항목이 전체 사이트 모음에 적용됩니다. 자세한 내용은 [요소 범위](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14))를 참조하세요.

 다른 기능을 사용하는 기능의 경우 사용할 수 있도록 설정하기 전에 ‘기능 활성화 종속성’을 설정하여 종속 기능을 표시할 수 있습니다. 기능 활성화 종속성은 종속 기능이 해당 범위에서 이미 활성화되었는지 확인합니다. 자세한 내용은 [활성화 종속성 및 범위](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14))를 참조하세요.

 패키지 디자이너에서 SharePoint 요소를 단일 솔루션 패키지로 그룹화하고, 배포 중에 웹 서버를 다시 설정할지 여부를 구성할 수 있습니다. 배포 서버 유형을 설정하려면 **속성** 창을 사용합니다. 디자이너에서 패키지 내용을 설명하는 XML 파일도 생성합니다. 자세한 내용은 [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)를 참조하세요.

 배포 중에 솔루션 파일을 SharePoint Server에 복사하기 위해 IIS(인터넷 정보 서비스) 서비스가 중지됩니다. Visual Studio의 패키지 디자이너를 사용하여 웹 서버를 다시 시작할지 여부를 선택할 수 있습니다. 솔루션을 프런트 엔드 웹 서버에 배포할지 또는 애플리케이션 서버에 배포할지 구성하려면 **속성** 창을 사용합니다. 자세한 내용은 [Solution 요소(Solution)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14))를 참조하세요.

### <a name="packaging-explorer"></a>패키징 탐색기
 기능 디자이너와 패키지 디자이너를 보완하기 위해 패키징 탐색기를 사용하여 SharePoint 파일을 기능 및 패키지로 그룹화할 수 있습니다. 또한 패키지, 기능, SharePoint 프로젝트 항목, 파일의 계층적 뷰를 볼 수 있습니다. 패키징 탐색기는 다음 작업을 완료하는 데 사용할 수 있는 도구 창입니다.

- SharePoint 프로젝트 항목 및 파일을 엽니다.

- SharePoint 프로젝트 항목을 기능 간에 끌어서 놓습니다.

- SharePoint 프로젝트 항목과 기능을 패키지 간에 끌어서 놓습니다.

- 패키지에 새 기능을 추가합니다.

- 기능 또는 패키지 디자이너를 엽니다.

- 기능 및 패키지의 유효성을 검사합니다.

  Visual Studio의 SharePoint 개발 도구에는 솔루션 패키지가 올바르게 구성되었는지 확인하는 유효성 검사 규칙이 있습니다. 또한 규칙은 SharePoint Server에 *.wsp* 솔루션 파일을 성공적으로 배포하고 활성화할 수 있는지 확인합니다. 기능의 XML 스키마에 대한 자세한 내용은 [기능 스키마](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))를 참조하세요.

  SharePoint 프로젝트 시스템에 사용자 지정 기능 및 패키지 유효성 검사 규칙을 추가할 수 있습니다. 자세한 내용은 [방법: SharePoint 솔루션에 대한 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)를 참조하세요.

  패키징 탐색기에 대한 자세한 내용은 [방법: 패키징 탐색기를 사용하여 패키지에 기능과 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)를 참조하세요.

### <a name="solution-explorer"></a>솔루션 탐색기
 솔루션 탐색기를 사용하여 SharePoint 프로젝트의 파일을 탐색하고 열 수 있습니다. 솔루션 탐색기의 상황에 맞는 메뉴를 사용하여 기능, 기능 이벤트 수신기, 기능 리소스를 추가합니다. 또한 기능 디자이너와 패키지 디자이너를 열어 배포할 기능 및 패키지를 구성할 수 있습니다.

## <a name="deploy-sharepoint-solutions"></a>SharePoint 솔루션 배포
 Visual Studio에서 기능 및 패키지를 사용자 지정한 후 SharePoint Server에 배포할 *.wsp* 파일을 만들 수 있습니다. 개발 컴퓨터의 SharePoint Server에 있는 *.wsp*만 Visual Studio에서 디버그하고 테스트할 수 있습니다. 원격 SharePoint Server에 SharePoint 솔루션을 배포하는 방법에 대한 자세한 내용은 [솔루션 배포](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14))를 참조하세요.

 개발 컴퓨터의 배포 단계를 사용자 지정할 수도 있습니다. 자세한 내용은 [SharePoint 솔루션 패키지 배포, 게시, 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)를 참조하세요.

## <a name="deploy-files-in-sharepoint-solutions"></a>SharePoint 솔루션에 파일 배포
 일반적으로 SharePoint 솔루션에 SharePoint 프로젝트 항목을 추가하면 필요한 모든 파일이 포함됩니다. 컴파일할 수 있는 파일(코드 파일)은 솔루션의 출력 어셈블리에 빌드됩니다. 그러나 컴파일할 수 없는 파일(예: *.xml*, *.txt* 또는 리소스 파일)을 SharePoint 프로젝트에 추가해야 하는 경우도 있습니다. 해당 파일은 솔루션에 자동으로 패키지되지 않습니다. 파일이 패키지되게 하려면 매핑된 폴더 또는 SharePoint 프로젝트 항목에 파일을 추가합니다.

 매핑된 폴더에 추가한 파일은 솔루션을 배포할 때 자동으로 SharePoint 하이브에 복사됩니다. SharePoint 프로젝트 항목에 추가한 파일은 각 파일의 **배포 위치** 속성에 지정한 위치에 배포됩니다. 이 위치는 부분적으로 **배포 유형** 속성에 따라 설정됩니다. 기본적으로 **배포 유형** 속성 값은 **NoDeployment**로, 파일이 솔루션과 함께 배포되지 않습니다. 패키지에 파일을 포함하려면 속성에 다른 값을 설정해야 합니다.

 예를 들어 SharePoint 프로젝트에 *.xml* 파일을 추가하려면 다음 작업 중 하나를 수행합니다.

- SharePoint의 매핑된 폴더 “레이아웃”을 프로젝트에 추가합니다. 그러면 **솔루션 탐색기**에 프로젝트 하위 폴더를 포함하는 **레이아웃** 폴더가 생성됩니다. 새 하위 폴더에 *.xml* 파일을 추가합니다. 기본적으로 파일은 SharePoint 파일 시스템의 *..\TEMPLATE\LAYOUTS\\\<Folder Name>* 아래에 배포됩니다. 매핑된 폴더를 추가하는 방법에 대한 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조하세요.

- SharePoint 프로젝트 항목 폴더에 *.xml* 파일을 추가하고 *.xml* 파일의 **배포 유형** 속성을 **NoDeployment**에서 다른 설정(예: **RootFile** 또는 **ElementFile**)으로 변경합니다. 적절한 **배포 유형** 설정은 파일 및 프로젝트에 따라 다릅니다. **배포 유형** 속성 설정에 대한 자세한 내용은 [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)을 참조하세요.

  추가한 파일이 솔루션의 특정 프로젝트에 적용되지 않는 경우 솔루션에 빈 SharePoint 프로젝트를 추가한 다음, 파일을 더 추가할 수 있습니다. SharePoint, 특히 콘텐츠 데이터베이스에 파일을 배포하는 또 다른 방법은 프로젝트에 모듈을 추가한 다음, 모듈에 파일을 추가하는 것입니다. 자세한 내용은 [모듈을 사용하여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)을 참조하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
