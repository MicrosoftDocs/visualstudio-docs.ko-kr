---
title: ProjectItem 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44fc1b918960f0268d916ccfa560f118cea47144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536879"
---
# <a name="projectitem-element"></a>ProjectItem 요소
  SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 *.spdata* 파일의 필수 루트 요소입니다.

## <a name="syntax"></a>구문

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**DefaultFile**|선택적 **xs: string** 특성입니다.<br /><br /> **솔루션 탐색기**에서 SharePoint 프로젝트 항목을 열 때 Visual Studio 편집기에서 열리는 파일의 상대 경로 (파일 이름 포함)입니다. 경로는 *.spdata* 파일이 들어 있는 폴더의 상대 경로입니다.|
|**FeatureReceiverClass**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목에 대 한 기능 수신기 클래스의 정규화 된 이름입니다. 기능 수신기에 대 한 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요.|
|**FeatureReceiverAssembly**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목의 기능 수신기를 정의 하는 어셈블리의 정규화 된 이름을 지정 합니다. 기능 수신기에 대 한 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요. 정규화 된 어셈블리 이름에 대 한 자세한 내용은 [어셈블리 이름](/dotnet/framework/app-domains/assembly-names)을 참조 하세요.|
|**SupportedTrustLevels**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목에서 지 원하는 신뢰 수준을 지정 합니다. 이 값은 다음 문자열 중 하나일 수 있습니다. Sandbox, FullTrust 또는 모두. 모두 값은 샌드박스가 적용 되 고 FullTrust를 모두 지정 합니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 항목 형식에서이 특성의 값은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 메서드 구현에서 속성에 할당 하는 값에 해당 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . 이 특성에 대해 다른 값을 지정 하는 경우 Visual Studio는 속성에서 지정 하는 것과 동일한 신뢰 수준을 지정 하도록 값을 덮어씁니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> .|
|**SupportedDeploymentScopes**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목에서 지 원하는 배포 범위를 지정 합니다. 이 값은 다음 문자열 중 하나 이상으로 구성 된 쉼표로 구분 된 문자열입니다. 팜, 사이트, 웹, WebApplication 또는 패키지 예: `Web, Site`<br /><br /> 사용자 지정 SharePoint 프로젝트 항목 형식에서이 특성의 값은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 메서드 구현에서 속성에 할당 하는 값에 해당 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . 이 특성에 대해 다른 값을 지정 하는 경우 Visual Studio는 속성에서 지정 하는 것과 동일한 신뢰 수준을 지정 하도록 값을 덮어씁니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> .|
|**유형**|필수 **xs: string** 특성입니다.<br /><br /> SharePoint 프로젝트 항목의 식별자입니다. 사용자 지정 SharePoint 프로젝트 항목 형식에서 식별자는에 전달 하는 문자열입니다 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)를 참조 하세요.<br /><br /> Visual Studio에 포함 된 기본 제공 SharePoint 프로젝트 항목의 식별자 목록은 [SharePoint 프로젝트 항목 확장](../sharepoint/extending-sharepoint-project-items.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|선택적 요소입니다.<br /><br /> SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목의 컬렉션을 나타냅니다.<br /><br /> **Extensiondata** 요소를 하나만 포함할 수 있습니다.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|선택적 요소입니다.<br /><br /> SharePoint에 배포 될 때 기능에 포함 된 속성 값의 컬렉션을 나타냅니다.<br /><br /> **Featureproperties** 요소는 하나만 포함할 수 있습니다.|
|[파일](../sharepoint/files-element.md)|선택적 **FileCollectionType** 요소입니다.<br /><br /> 기능 요소 파일 및 종속 비 SharePoint 프로젝트의 출력과 같은 SharePoint 프로젝트 항목을 사용 하 여 배포할 파일을 지정 합니다.<br /><br /> **파일이** 나 **ProjectItemFolder** 요소 중 하나만 포함 합니다.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|선택적 **ProjectItemFolderType** 요소입니다.<br /><br /> 매핑된 폴더를 나타냅니다.<br /><br /> **파일이** 나 **ProjectItemFolder** 요소 중 하나만 포함 합니다.|
|[SafeControls](../sharepoint/safecontrols-element.md)|선택적 요소입니다.<br /><br /> 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤 및 웹 파트의 컬렉션을 나타냅니다.<br /><br /> **SafeControls** 요소는 하나만 포함할 수 있습니다.|

### <a name="parent-elements"></a>부모 요소
 없음

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
[SharePoint 프로젝트 항목 스키마 rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
