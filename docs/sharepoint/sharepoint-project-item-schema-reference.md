---
title: SharePoint 프로젝트 항목 스키마 참조 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc15ff5c384ec63f99ed50a5f3c700efd7ba3c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63007721"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint 프로젝트 항목 스키마 참조
  Visual Studio는 SharePoint 프로젝트 항목 스키마를 사용 하 여 *.spdata* 파일의 내용에 대 한 유효성을 검사 합니다. *.Spdata* 파일은 SharePoint 프로젝트 항목의 내용과 동작을 지정 합니다. SharePoint 프로젝트 항목의 내용에 대 한 자세한 내용은 [sharepoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

 SharePoint 프로젝트 항목 스키마의 이름은 ProjectItemModelSchema 이며, 기본적 으로% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.에 설치 됩니다.

 Root 요소는 [ProjectItem](../sharepoint/projectitem-element.md) 요소입니다. 다음 표에서는 스키마에 정의 된 모든 요소에 대해 설명 합니다.

|요소|설명|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목의 컬렉션을 나타냅니다.|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목 (키/값 형식)을 나타냅니다. 키와 값은 모두 문자열 이어야 합니다.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint에 배포 될 때 기능에 포함 된 속성 값의 컬렉션을 나타냅니다. 기능이 배포 된 후 코드에서 속성 값에 액세스할 수 있습니다.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint에 배포 될 때 기능에 포함 되는 사용자 지정 속성을 나타냅니다. 기능이 배포 된 후에는 코드에서 속성에 액세스할 수 있습니다.|
|[파일](../sharepoint/files-element.md)|기능 요소 파일 또는 프로젝트 출력과 같은 SharePoint 프로젝트 항목을 사용 하 여 배포할 파일을 지정 합니다.|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다.|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|SharePoint에 배포 될 때 프로젝트 항목에 포함할 기능 요소 파일 등의 SharePoint 파일을 나타냅니다.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|매핑된 폴더를 나타냅니다.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint에 배포 될 때 프로젝트 항목과 함께 포함할 프로젝트의 출력을 나타냅니다.|
|[SafeControl](../sharepoint/safecontrol-element.md)|모든 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤이 나 웹 파트를 나타냅니다.|
|[SafeControls](../sharepoint/safecontrols-element.md)|사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤 및 웹 파트의 컬렉션을 나타냅니다.|

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
