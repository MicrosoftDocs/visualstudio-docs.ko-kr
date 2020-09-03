---
title: SharePoint에서 지 원하는 MSBuild 속성 Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985170"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>SharePoint에서 지 원하는 MsBuild 속성
  [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]VisualStudio 파일, 프로젝트 파일 또는 프로젝트 사용자 파일에 정의 된 모든 속성은 sharepoint 프로젝트에서 사용할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . SharePoint는 프로젝트에서 제공 하는 공용 속성 외에도 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sharepoint 프로젝트와 관련 된 추가 속성을 정의 합니다.

 공용 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 속성 목록은 [일반적인 MSBuild 프로젝트 속성](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100))을 참조 하세요. 프로그래밍 언어로 지원 되는 속성의 전체 목록은 *.targets* 파일, 프로젝트 파일 (*.csproj* 또는 *.vbproj*) 또는 프로젝트 사용자 파일 (*.csproj. user* 또는 *.vbproj*)을 참조 하세요.

## <a name="msbuild-properties-specific-to-sharepoint"></a>SharePoint에 특정 한 MsBuild 속성
 다음 표에서는 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] 의 SharePoint 프로젝트에 특별히 적용 되는 속성을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 다른 속성은 있지만 내부적으로 사용 됩니다.

|속성 이름|Description|
|-------------------|-----------------|
|SharePointSiteUrl|SharePoint 사이트에 대 한를 나타내는 문자열입니다 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] .|
|SandboxedSolution|솔루션이 샌드박스 솔루션 인지 여부를 나타내는 부울 값입니다.|
|ActiveDeploymentConfiguration|활성 배포 구성입니다.|
|IncludeAssemblyInPackage|어셈블리가 패키지 파일에 포함 되어 있는지 여부를 나타내는 부울 값입니다.|
|PreDeploymentCommand|배포 전 명령 단계에서 실행할 명령을 나타내는 문자열 값입니다.|
|PostDeploymentCommand|배포 후 명령 단계에서 실행할 명령을 나타내는 문자열 값입니다.|
|CustomBeforeSharePointTargets|대상 파일의 경로를 나타내는 문자열입니다 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . 대상 파일이 있고 정의 된 경우에는 SharePoint가 대상으로 하는 데이터 보다 먼저 가져옵니다. 이 속성을 사용 하면 제공 된 SharePoint 대상 파일을 수정 하지 않고 패키지 관련 속성을 predefining 패키지 프로세스를 사용자 지정할 수 있지만 대상 파일은 여전히 모든 SharePoint 프로젝트에 적용 됩니다.|
|CustomAfterSharePointTargets|대상 파일의 경로를 나타내는 문자열입니다 [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . 대상 파일이 있고 정의 된 경우 모든 SharePoint 대상 데이터 다음에 해당 파일이 가져옵니다. 이 속성을 사용 하면 제공 된 SharePoint 대상 파일을 수정 하지 않고도 패키지 관련 속성 및 대상을 재정의 하 여 패키지 프로세스를 사용자 지정할 수 있습니다. 그러나 대상 파일은 모든 SharePoint 프로젝트에 계속 적용 됩니다.|
|LayoutPath|패키지할 파일이 *.wsp* 파일에 추가 되기 전에 일시적으로 배치 되는 루트 디렉터리를 나타내는 문자열입니다. 이 경로를 사용 하면 파일을 추가, 제거 또는 수정 하는 BeforeLayout 및 AfterLayout 대상을 재정의할 때이를 사용 하 여 *.wsp* 파일의 콘텐츠를 변경할 수 있으므로이 경로를 파악 하는 것이 유용할 수 있습니다.|
|BasePackagePath|패키지가 배치 된 폴더를 나타내는 문자열입니다. 이 값은 프로젝트의 출력 디렉터리 (예: Bin\debug입니다.)를 사용 합니다.|
|PackageExtension|패키지에 추가할 파일 이름 확장명을 나타내는 문자열입니다. 기본값은 wsp입니다.|
|AssemblyDeploymentTarget|SharePoint 서버에서 프로젝트 어셈블리를 배포 하는 위치를 나타내는 문자열입니다. 해당 값은 GlobalAssemblyCache (기본값) 또는 WebApplication입니다. 속성 창에서이 속성을 설정할 수도 있습니다.|
|PackageWithValidation|패키징 전에 유효성 검사를 수행할지 여부를 지정 하는 부울 값입니다. 이 속성을 사용 하면 패키지를 작성 하는 동안 유효성 검사 오류를 무시할 수 있습니다.|
|ValidatePackageDependsOn|ValidatePackage 대상 전에 실행할 추가 대상을 정의 하는 문자열입니다.|
|TokenReplacementFileExensions|패키징 중에 토큰을 대체 한 파일을 정의 하는 문자열입니다.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>속성 페이지에서 MsBuild 속성 사용
 유연성을 위해 SharePoint 속성 페이지의 **배포 전 명령줄** 및 **배포 후** 명령줄 상자에서 하드 코드 된 문자열을 사용 하는 대신 sharepoint 속성을 인수로 사용할 수 있습니다. 예를 들어 SharePoint 사이트에 대 한 특정 문자열을 지정 하는 대신를 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 대신 사용할 수 있습니다 `$(SharePointSiteUrl)` .

> [!NOTE]
> [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]변수 구문 `$(` *propertyname* `)` 또는 환경 변수 구문 `%` *propertyname* `%` 을 사용 하 여 속성을 지정할 수 있습니다.

## <a name="see-also"></a>참조

- [MSBuild 참조](../msbuild/msbuild-reference.md)