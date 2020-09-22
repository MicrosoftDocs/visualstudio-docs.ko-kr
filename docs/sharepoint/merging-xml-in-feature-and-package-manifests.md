---
title: 기능 및 패키지 매니페스트에서 XML 병합 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1378cddbc9770af923a98f1b7083a8792874b5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841791"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>기능 및 패키지 매니페스트에서 XML 병합
  기능 및 패키지는 매니페스트 파일에 의해 정의 됩니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . 이러한 패키지 된 매니페스트는 디자이너에서 생성 된 데이터와 사용자가 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 템플릿에 입력 한 사용자 지정의 조합입니다. 패키징 시는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 패키지 된 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 매니페스트 파일을 구성 하기 위해 제공 된 디자이너와 사용자 지정 문을 병합 합니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . 병합 예외에서 나중에 설명 된 예외를 포함 하는 비슷한 요소는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] SharePoint에 파일을 배포한 후에 유효성 검사 오류를 방지 하 고 매니페스트 파일을 더 작고 효율적으로 만드는 데 병합 됩니다.

## <a name="modify-the-manifests"></a>매니페스트 수정
 패키지 매니페스트 파일은 기능 또는 패키지 디자이너를 사용 하지 않도록 설정할 때까지 직접 수정할 수 없습니다. 그러나 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 기능 및 패키지 디자이너나 편집기를 통해 사용자 지정 요소를 매니페스트 템플릿에 수동으로 추가할 수 있습니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . 자세한 내용은 [방법: Sharepoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md) 및 [방법: Sharepoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)을 참조 하세요.

## <a name="feature-and-package-manifest-merge-process"></a>기능 및 패키지 매니페스트 병합 프로세스
 사용자 지정 요소를 디자이너에서 제공 하는 요소와 함께 결합 하면에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 프로세스를 사용 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 각 요소에 고유한 키 값이 있는지 여부를 확인 합니다. 요소에 고유한 키 값이 없으면 요소가 패키지된 매니페스트 파일에 추가됩니다. 이와 마찬가지로 여러 키가 있는 요소는 병합될 수 없으므로 따라서 매니페스트 파일에 추가 됩니다.

 요소에 고유 키가 있는 경우는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디자이너와 사용자 지정 키의 값을 비교 합니다. 값이 일치 하면 단일 값으로 병합 됩니다. 값이 다르면 디자이너 키 값이 삭제 되 고 사용자 지정 키 값이 사용 됩니다. 컬렉션도 병합 됩니다. 예를 들어 디자이너에서 생성 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 하 고 사용자 지정에 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 모두 어셈블리 컬렉션이 포함 된 경우 패키지 매니페스트는 하나의 어셈블리 컬렉션만 포함 합니다.

## <a name="merge-exceptions"></a>병합 예외
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 고유한 단일 식별 특성이 있는 한 대부분의 디자이너 요소를 유사한 사용자 지정 요소와 병합 합니다. 그러나 일부 요소에는 병합에 필요한 고유 식별자가 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 없습니다. 이러한 요소를 *병합 예외*라고 합니다. 이러한 경우는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용자 지정 요소를 디자이너에서 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 제공 하는 요소와 함께 병합 하지 않고 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 대신 패키지 된 매니페스트 파일에 추가 합니다.

 다음은 기능 및 패키지 매니페스트 파일에 대 한 병합 예외 목록입니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Designer|XML 요소|
|--------------|-----------------|
|기능 디자이너|ActivationDependency|
|기능 디자이너|UpgradeAction|
|패키지 디자이너|SafeControl|
|패키지 디자이너|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>기능 매니페스트 요소
 다음 표는 병합할 수 있는 모든 기능 매니페스트 요소와 일치에 사용 되는 고유 키의 목록입니다.

|요소 이름|고유 키|
|------------------|----------------|
|기능 (모든 특성)|*특성 이름* (기능 요소의 각 특성 이름이 고유 키입니다.)|
|ElementFile|위치|
|ElementManifests/Elementmanifests|위치|
|속성/속성|키|
|CustomUpgradeAction|Name|
|CustomUpgradeActionParameter|Name|

> [!NOTE]
> CustomUpgradeAction 요소를 수정 하는 유일한 방법은 사용자 지정 편집기에 있기 때문입니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] . 병합 하지 않는 효과는 낮습니다.

## <a name="package-manifest-elements"></a>패키지 매니페스트 요소
 다음 표는 병합할 수 있는 모든 패키지 매니페스트 요소와 일치에 사용 되는 고유 키의 목록입니다.

|요소 이름|고유 키|
|------------------|----------------|
|솔루션 (모든 특성)|*특성 이름* (솔루션 요소의 각 특성 이름이 고유 키입니다.)|
|ApplicationResourceFiles/ApplicationResourceFile|위치|
|어셈블리/어셈블리|위치|
|ClassResources/Classresources|위치|
|DwpFiles/DwpFile|위치|
|FeatureManifests/Featuremanifests|위치|
|리소스/리소스|위치|
|RootFiles/Rootfiles|위치|
|SiteDefinitionManifests/Sitedefinitionmanifests|위치|
|WebTempFile|위치|
|템플릿 파일/템플릿 파일|위치|
|솔루션 종속성|솔루션 Id|

## <a name="manually-add-deployed-files"></a>수동으로 배포 된 파일 추가
 ApplicationResourceFile 및 DwpFiles와 같은 일부 매니페스트 요소는 파일 이름을 포함 하는 위치를 지정 합니다. 그러나 매니페스트 템플릿에 파일 이름 항목을 추가 하면 기본 파일이 패키지에 추가 되지 않습니다. 프로젝트에 파일을 추가 하 여 패키지에 포함 하 고 해당 배포 유형 속성을 적절 하 게 설정 해야 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
