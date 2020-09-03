---
title: 프로젝트 항목의 배포 정보 & 패키징
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SafeControlEntries
- VS.SharePointTools.Project.ProjectOutputReference
- VS.SharePointTools.Project.FeatureProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature properties
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
- feature properties [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, feature receiver
- feature receiver [SharePoint development in Visual Studio]
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db805c308fd245554824997b24236eb2e2d80e62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72984210"
---
# <a name="provide-packaging-and-deployment-information-in-project-items"></a>프로젝트 항목에 패키징 및 배포 정보 제공
  의 모든 SharePoint 프로젝트 항목에는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트가 sharepoint에 배포 될 때 추가 데이터를 제공 하는 데 사용할 수 있는 속성이 있습니다. 속성은 다음과 같습니다.

- 기능 속성

- 기능 수신기

- 프로젝트 출력 참조

- 안전 컨트롤 항목

  이러한 속성은 **속성** 창에 표시 됩니다.

## <a name="feature-properties"></a>기능 속성
 기능 **속성** 속성을 사용 하 여 기능에서 사용 하는 데이터를 지정 합니다. 기능 속성 데이터는 SharePoint에 배포할 때 기능과 함께 포함 되는 값 집합 (키/값 쌍으로 저장 됨)입니다. 기능이 배포되고 나서 코드에서 속성 값에 액세스할 수 있습니다.

 기능 속성 값을 프로젝트 항목에 추가 하면 해당 값이 항목의 기능 매니페스트에 요소로 추가 됩니다. 예를 들어 BDC (비즈니스 데이터 연결) 모델 프로젝트에서 ModelFileName 기능 속성은 다음과 같이 표시 됩니다.

```xml
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />
```

 기능 속성 값을 설정 하면 프로젝트의 *.spdata* 파일에 featureproperty 요소로 추가 됩니다. SharePoint의 속성에 액세스 하는 방법에 대 한 자세한 내용은 [SPFeaturePropertyCollection 클래스](/previous-versions/office/sharepoint-server/ms461895(v=office.15))를 참조 하세요.

 모든 프로젝트 항목의 동일한 기능 속성 값은 기능 매니페스트에서 함께 병합 됩니다. 그러나 두 개의 다른 프로젝트 항목에서 일치 하지 않는 값을 가진 동일한 기능 속성 키를 지정 하는 경우 유효성 검사 오류가 발생 합니다.

 기능 파일 (*. 기능*)에 기능 속성을 직접 추가 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 개체 모델 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> . 이 방법을 사용 하는 경우 기능 속성에서 동일한 기능 속성 값을 추가 하는 것과 동일한 규칙이 기능 파일에 직접 추가 된 속성에도 적용 됩니다.

## <a name="feature-receiver"></a>기능 수신기
 기능 수신기는 프로젝트 항목의 포함 기능에 대 한 특정 이벤트가 발생할 때 실행 되는 코드입니다. 예를 들어 기능이 설치, 활성화 또는 업그레이드 될 때 실행 되는 기능 수신기를 정의할 수 있습니다. 기능 수신기를 추가 하는 한 가지 방법은 [연습: 기능 이벤트 수신자 추가](../sharepoint/walkthrough-add-feature-event-receivers.md)에 설명 된 대로 기능에 직접 추가 하는 것입니다. 또 다른 **방법은 기능 수신기 속성에서** 기능 수신기 클래스 이름 및 어셈블리를 참조 하는 것입니다.

### <a name="direct-method"></a>직접 메서드
 기능에 기능 수신기를 직접 추가 하는 경우 코드 파일이 솔루션 탐색기의 **기능** 노드 아래에 배치 됩니다. SharePoint 솔루션을 빌드하면 코드가 어셈블리로 컴파일되고 SharePoint에 배포 됩니다. 기본적으로 기능 속성 **수신기 어셈블리** 와 **수신자 클래스** 는 클래스 이름 및 어셈블리를 참조 합니다.

### <a name="reference-method"></a>Reference 메서드
 기능 수신기를 추가 하는 또 다른 방법은 프로젝트 항목의 **기능 수신기** 속성을 사용 하 여 기능 수신기 어셈블리를 참조 하는 것입니다. 기능 수신기 속성 값에는 **어셈블리** 와 **클래스 이름**이라는 두 개의 하위 속성이 있습니다. 어셈블리는 정규화 된 "강력한" 이름을 사용 해야 하며 클래스 이름은 전체 형식 이름 이어야 합니다. 자세한 내용은 [강력한 이름의 어셈블리](/previous-versions/dotnet/netframework-4.0/wd40t7ad(v=vs.100))를 참조하세요. SharePoint에 솔루션을 배포한 후이 기능은 참조 된 기능 수신기를 사용 하 여 기능 이벤트를 처리 합니다.

 솔루션 빌드 시 기능 및 해당 프로젝트의 기능 수신기 속성 값이 함께 병합 되어 SharePoint 솔루션 (*.wsp*) 파일의 기능 매니페스트에 있는 Feature 요소의 ReceiverAssembly 및 ReceiverClass 특성을 설정 합니다. 따라서 프로젝트 항목과 기능의 어셈블리 및 클래스 이름 속성 값이 모두 지정 된 경우 프로젝트 항목과 기능 속성 값이 일치 해야 합니다. 값이 일치 하지 않으면 유효성 검사 오류가 표시 됩니다. 프로젝트 항목이 기능에서 사용 하는 것과 다른 기능 수신기 어셈블리를 참조 하도록 하려면 다른 기능으로 이동 합니다.

 서버에 없는 기능 수신기 어셈블리를 참조 하는 경우 패키지에도 어셈블리 파일을 포함 해야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 추가 하지 않습니다. 기능을 배포할 때 어셈블리 파일은 [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] SharePoint 물리적 디렉터리의 시스템 또는 Bin 폴더에 복사 됩니다. 자세한 내용은 방법: [추가 어셈블리 추가 및 제거](../sharepoint/how-to-add-and-remove-additional-assemblies.md)를 참조 하세요.

 기능 수신기에 대 한 자세한 내용은 [기능 이벤트 수신기](/previous-versions/office/developer/sharepoint-2007/bb862634(v=office.12)) 및 [기능 이벤트](/previous-versions/office/developer/sharepoint-2010/ms469501(v=office.14))를 참조 하세요.

## <a name="project-output-references"></a>프로젝트 출력 참조
 프로젝트 출력 참조 속성은 프로젝트 항목을 실행 해야 하는 어셈블리와 같은 종속성을 지정 합니다. 예를 들어, 솔루션에 BDC 프로젝트와 클래스 프로젝트가 있다고 가정 합니다. BDC 프로젝트가 클래스 프로젝트에 의해 출력 되는 어셈블리에 종속 되어 있는 경우 BDC 프로젝트의 프로젝트 출력 참조 속성에서 어셈블리를 참조할 수 있습니다. BDC 프로젝트를 패키지할 때 종속 어셈블리는 패키지에 포함 됩니다.

 프로젝트 출력 참조는 일반적으로 어셈블리 이지만 경우에 따라 Silverlight 프로젝트와 같은 다른 파일 형식일 수 있습니다.

 자세한 내용은 [방법: 프로젝트 출력 참조 추가](../sharepoint/how-to-add-a-project-output-reference.md)를 참조 하세요.

## <a name="safe-control-entries"></a>안전 컨트롤 항목
 SharePoint는 신뢰할 수 없는 사용자의 액세스를 특정 컨트롤로 제한 하기 위해 안전 컨트롤 항목 이라고 하는 보안 메커니즘을 제공 합니다. 기본적으로 SharePoint를 사용 하면 신뢰할 수 없는 사용자가 SharePoint 서버에서 ASPX 페이지를 업로드 하 고 만들 수 있습니다. 이러한 사용자가 안전 하지 않은 코드를 ASPX 페이지에 추가 하지 못하도록 방지 하기 위해 SharePoint는 *안전 컨트롤*에 대 한 액세스를 제한 합니다. 안전 컨트롤은 보안으로 지정 되 고 사이트의 모든 사용자가 사용할 수 있는 ASPX 컨트롤 및 웹 파트입니다. 자세한 내용은 [4 단계: 안전한 컨트롤 목록에 웹 파트 추가](/previous-versions/office/developer/sharepoint-2007/ms581321(v=office.12))를 참조 하세요.

 의 모든 SharePoint 프로젝트 항목에는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 두 개의 부울 하위 속성인 **Safe** 와 **스크립트에 대 한**Safe를 포함 하는 **안전 컨트롤 항목** 이라는 속성이 있습니다. 안전 속성은 신뢰할 수 없는 사용자가 컨트롤에 액세스할 수 있는지 여부를 지정합니다. Safe for Script 속성은 신뢰할 수 없는 사용자가 컨트롤의 속성을 보고 변경할 수 있는지 여부를 지정 합니다.

 안전 컨트롤 항목은 어셈블리를 기준으로 참조 됩니다. 프로젝트 항목의 **안전 컨트롤** 항목 속성에 입력 하 여 안전 컨트롤 항목을 프로젝트의 어셈블리에 추가 합니다. 그러나 패키지에 어셈블리를 추가 하는 경우 **패키지 디자이너** 의 **고급** 탭을 통해 프로젝트 어셈블리에 안전 컨트롤 항목을 추가할 수도 있습니다. 자세한 내용은 [방법: 컨트롤을 안전한 컨트롤로 표시](../sharepoint/how-to-mark-controls-as-safe-controls.md) 또는 [웹 파트 어셈블리를 안전 컨트롤로 등록](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))을 참조 하세요.

### <a name="xml-entries-for-safe-controls"></a>안전 컨트롤에 대 한 XML 항목
 프로젝트 항목 또는 프로젝트의 어셈블리에 안전 컨트롤 항목을 추가 하는 경우 참조는 다음과 같은 형식으로 패키지 매니페스트에 기록 됩니다.

```xml
<Assemblies>
    <Assembly Location="<assembly name>.dll"
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>
        <SafeControls>
            <SafeControl Assembly="<assembly name>.dll" Namespace=
              "<SharePoint project name>" Safe="<true/false>"
                TypeName="<control name>"
                SafeAgainstScript="<true/false>" />
        </SafeControls>
    </Assembly>
</Assemblies>
```

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [모듈을 사용 하 여 솔루션에 파일 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
