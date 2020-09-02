---
title: SharePoint 솔루션 패키지 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b250be3b61cdfc524f049f952f0cf7e65f1c295a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74876066"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint 솔루션 패키지 만들기
  패키지 디자이너를 사용 하 여 배포 패키지를 만들고 사용자 지정할 수 있습니다. 예를 들어 SharePoint 프로젝트 항목 및 기능을 추가 하 고, IIS 서버를 다시 설정 하 고, 기능 활성화 범위를 설정 하 고, 기능 종속성을 식별할 수 있습니다. 또한 디자이너는 각 패키지를 설명 하는 XML 파일인 매니페스트를 생성 합니다.

## <a name="packaging-tools"></a>패키징 도구
 **패키지 디자이너** 를 사용 하 여 패키지를 사용자 지정 하 고 매니페스트를 생성할 수 있습니다. SharePoint 프로젝트 항목을 포함 하 고, 웹 서버를 다시 설정할지 여부를 구성 하 고, 배포 서버 유형을 설정할 수 있습니다. 자세한 내용은 [방법: 패키지 디자이너를 사용 하 여 패키지에 기능 및 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)를 참조 하세요.

 또는 **패키징 탐색기** 를 사용 하 여 패키지 파일 (*.Wsp*)의 기능 및 항목을 수정할 수 있습니다. 자세한 내용은 [방법: 패키징 탐색기를 사용 하 여 패키지에 기능 및 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)를 참조 하세요.

 Visual Studio 및 MSBuild를 사용 하 여 SharePoint 솔루션을 배포 하는 패키지 파일 (*.wsp*)을 만들 수 있습니다. 이 프로세스는 SharePoint 배포에 필요한 매니페스트 파일을 생성 합니다. 자세한 내용은 [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)를 참조 하세요.

## <a name="package-designer-options"></a>패키지 디자이너 옵션
 다음 표에서는 **패키지 디자이너**를 사용 하 여 SharePoint 패키지에서 사용자 지정할 수 있는 속성을 보여 줍니다.

|패키지 디자이너 속성|기본 설정에 대 한 설명|
|-------------------------------|------------------------------------|
|속성|필수 사항입니다. 패키지의 기본 이름은 *ProjectName*로 설정 됩니다.|
|웹 서버 다시 설정|선택 사항입니다. SharePoint 서버에 *.wsp* 파일이 설치 된 후 웹 서버를 다시 시작할지 여부를 선택 합니다.|
|배포 서버 유형|선택 사항입니다. 패키지를 호스팅하는 서버의 유형을 나타냅니다. 설정 하지 않으면 기본적으로 WebFrontEnd 엔드가로 설정 됩니다.<br /><br /> ApplicationServer: 서비스를 호스팅하는 서버를 설명 합니다.<br /><br /> WebFrontEnd 엔드: 웹 사이트를 호스트 하는 서버를 설명 합니다.|
|솔루션의 항목|패키지에 추가할 수 있는 모든 SharePoint 프로젝트 항목 및 기능입니다.|
|패키지의 항목|선택 사항입니다. 패키지에 배포 하려는 모든 SharePoint 항목 및 기능입니다.|

## <a name="configure-the-packaging-process"></a>패키징 프로세스 구성
 Visual Studio에서 SharePoint 솔루션을 개발한 후 프로젝트가 패키지되는 방법을 사용자 지정할 수 있습니다.

 다음 표에서는 *.wsp* 파일을 만드는 방법을 사용자 지정 하는 데 사용할 수 있는 두 가지 MSBuild 대상을 보여 줍니다.

|Target|설명|
|------------|-----------------|
|BeforeLayout|파일이 중간 디렉터리에 복사 되기 직전에 작업을 수행 하는 대상입니다. 패키지 파일 (*.wsp*)을 만들기 전에 파일을 수정할 수 있습니다.|
|AfterLayout|파일이 중간 디렉터리에 복사 된 직후에 작업을 수행 하는 대상입니다.|

 자세한 내용은 [방법: MSBuild 대상을 사용 하 여 SharePoint 솔루션 패키지 사용자 지정을 수행](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)합니다.

## <a name="packaging-architecture"></a>패키징 아키텍처
 다음 단계는 Visual Studio에서 SharePoint 패키지 (*.wsp*)를 만들 때 발생 합니다.

1. 기능 및 패키지의 유효성을 검사 하 여 패키지의 물리적 및 의미 체계 구조가 올바른지 확인 합니다.

2. 패키지의 기능, 프로젝트 항목 및 패키지 파일이 열거 됩니다. 패키지 및 기능에 대 한 매니페스트 파일은 배포 및 활성화에 필요한 모든 정보를 포함 하도록 변환 됩니다. 토큰은 정규화 된 값으로 대체 됩니다.

3. 사용자 지정 가능한 BeforeLayout MSBuild 대상이 수행 됩니다. 이 단계를 만들어 *.wsp* 파일을 만들기 전에 패키지에 대 한 사용자 지정 수정을 수행할 수 있습니다.

4. 열거 된 파일은 중간 디렉터리에 복사 됩니다.

5. 사용자 지정 가능한 AfterLayout MSBuild 대상이 수행 됩니다. 이 단계를 만들어 *.wsp* 파일을 만들기 전에 패키지에 대 한 사용자 지정 수정을 수행할 수 있습니다.

6. 중간 디렉터리의 파일은 *.wsp* 파일에 추가 됩니다.

## <a name="package-folder-structure"></a>패키지 폴더 구조
 SharePoint 프로젝트를 패키지할 때 *.wsp* 파일은 *솔루션 \\ \<BuildConfiguration> * 폴더에 생성 됩니다. 예를 들어 솔루션이 *C:\visual studio 2013 \ Projects\ListDefinition1* 에 있고 빌드 구성이 릴리스로 설정 된 경우 *.Wsp* 파일은 *C:\visual studio 2013 \ Projects\ListDefinition1\bin\Release*에 있습니다.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [방법: 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [방법: MSBuild 대상을 사용 하 여 SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
