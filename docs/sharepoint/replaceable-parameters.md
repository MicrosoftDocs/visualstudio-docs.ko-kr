---
title: 대체 가능 매개 변수 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: 165ef1256a0150e0942d85c4f876c8b3f5e15c72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842127"
---
# <a name="replaceable-parameters"></a>대체 가능 매개 변수
  대체 가능 매개 변수 또는 *토큰*은 프로젝트 파일 내에서 실제 값이 디자인 타임에 알려지지 않은 SharePoint 솔루션 항목에 대 한 값을 제공 하기 위해 프로젝트 파일 내에서 사용할 수 있습니다. 함수는 표준 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 템플릿 토큰과 유사 합니다. 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조 하세요.

## <a name="token-format"></a>토큰 형식
 토큰은 달러 기호 ($) 문자로 시작 하 고 끝납니다. 배포 시 프로젝트를 SharePoint 솔루션 패키지 (*.wsp* 파일)에 패키지할 때 사용 되는 모든 토큰이 실제 값으로 바뀝니다. 예를 들어 **Package.Name $ $SharePoint** 토큰은 "Test SharePoint Package" 문자열로 확인 될 수 있습니다.

## <a name="token-rules"></a>토큰 규칙
 토큰에 적용 되는 규칙은 다음과 같습니다.

- 토큰은 줄의 아무 곳에 나 지정할 수 있습니다.

- 토큰은 여러 줄에 걸쳐 있을 수 없습니다.

- 동일한 줄과 동일한 파일에 동일한 토큰을 두 번 이상 지정할 수 있습니다.

- 동일한 줄에 다른 토큰을 지정할 수 있습니다.

  이러한 규칙을 따르지 않는 토큰은 무시 되며 경고나 오류가 발생 하지 않습니다.

  토큰을 문자열 값으로 대체 하는 것은 매니페스트 변환 직후에 수행 됩니다. 이 대체를 통해 사용자는 토큰을 사용 하 여 매니페스트 템플릿을 편집할 수 있습니다.

### <a name="token-name-resolution"></a>토큰 이름 확인
 대부분의 경우 토큰은 포함 된 위치에 관계 없이 특정 값으로 확인 됩니다. 그러나 토큰이 패키지 또는 기능과 관련 된 경우 토큰의 값은 포함 된 위치에 따라 달라 집니다. 예를 들어, 기능이 패키지 A에 있는 경우 토큰은 `$SharePoint.Package.Name$` "Package a" 값으로 확인 됩니다. 패키지 B에 동일한 기능이 있는 경우는 `$SharePoint.Package.Name$` "패키지 b"로 확인 됩니다.

## <a name="tokens-list"></a>토큰 목록
 다음 표에서는 사용 가능한 토큰을 보여 줍니다.

|Name|Description|
|----------|-----------------|
|$SharePoint. FileName $|포함 하는 프로젝트 파일의 이름입니다 (예: *Newproj .csproj*).|
|$SharePoint FileNameWithoutExtension $|파일 이름 확장명이 없는 포함 하는 프로젝트 파일의 이름입니다. 예를 들면 "NewProj"입니다.|
|$SharePoint. AssemblyFullName $|포함 하는 프로젝트의 출력 어셈블리에 대 한 표시 이름 (강력한 이름)입니다.|
|$SharePoint AssemblyFileName $|포함 하는 프로젝트의 출력 어셈블리 이름입니다.|
|$SharePoint AssemblyFileNameWithoutExtension $|파일 이름 확장명이 없는 포함 하는 프로젝트의 출력 어셈블리 이름입니다.|
|$SharePoint AssemblyPublicKeyToken $|포함 하는 프로젝트의 출력 어셈블리에 대 한 공개 키 토큰으로, 문자열로 변환 됩니다. (16 자 "x2" 16 진수 형식)|
|$SharePoint Package.Name $|포함 하는 패키지의 이름입니다.|
|$SharePoint. FileName $|포함 하는 패키지 정의 파일의 이름입니다.|
|$SharePoint FileNameWithoutExtension $|포함 하는 패키지 정의 파일의 이름 (확장명 없음)입니다.|
|$SharePoint Package.Id $|포함 하는 패키지에 대 한 SharePoint ID입니다. 하나 이상의 패키지에서 기능을 사용 하는 경우이 값이 변경 됩니다.|
|$SharePoint. FileName $|포함 하는 기능의 정의 파일 이름 (예: *Feature1*)입니다.|
|$SharePoint FileNameWithoutExtension $|파일 이름 확장명이 없는 기능 정의 파일의 이름입니다.|
|$SharePoint. DeploymentPath $|패키지의 기능을 포함 하는 폴더의 이름입니다. 이 토큰은 기능 디자이너의 "배포 경로" 속성에 해당 합니다. 예제 값은 "Project1_Feature1"입니다.|
|$SharePoint Feature.Id $|포함 하는 기능의 SharePoint ID입니다. 모든 기능 수준 토큰과 마찬가지로이 토큰은 기능을 통해 패키지에 포함 된 파일에만 사용할 수 있으며 기능 외부의 패키지에는 직접 추가 되지 않습니다.|
|$SharePoint ProjectItem.Name $|**ISharePointProjectItem.Name**에서 가져온 프로젝트 항목의 이름 (파일 이름 아님)입니다.|
|$SharePoint \<GUID> . 형식. AssemblyQualifiedName $|토큰의 [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]와 일치하는 형식의 정규화된 어셈블리 이름입니다. [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)]의 형식은 소문자이며 Guid.ToString("D") 형식과 일치합니다(즉, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint \<GUID> . 형식. FullName $|토큰에서 GUID와 일치 하는 형식의 전체 이름입니다. GUID의 형식은 소문자 이며 Guid. ToString ("D") 형식에 해당 합니다 (즉, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>토큰 대체 파일 확장명 목록에 확장 추가
 토큰은 이론적으로 패키지에 포함 된 SharePoint 프로젝트 항목에 속하는 모든 파일에서 사용 될 수 있지만 기본적으로에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 패키지 파일, 매니페스트 파일 및 확장명이 다음과 같은 파일 에서만 토큰을 검색 합니다.

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- .ASCX

- LOGIN.ASPX

- 웹

- .DWP

  이러한 확장은 `<TokenReplacementFileExtensions>` ... \\<program files \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools 폴더에 있는 VisualStudio 파일의 요소에 의해 정의 됩니다.

  그러나 목록에 파일 확장명을 더 추가할 수 있습니다. Sharepoint `<TokenReplacementFileExtensions>` 대상 파일의 이전에 정의 된 sharepoint 프로젝트 파일의 모든 PropertyGroup에 요소를 추가 \<Import> 합니다.

> [!NOTE]
> 프로젝트를 컴파일한 후에 토큰 대체가 발생 하므로 *.cs*, *.vb* 또는 *.resx*와 같이 컴파일되는 파일 형식에 대 한 파일 확장명을 추가 하면 안 됩니다. 토큰은 컴파일되지 않은 파일 에서만 바뀝니다.

 예를 들어 토큰 대체 파일 이름 확장명 목록에 파일 이름 확장명 ( *yourextension*)을 추가 하려면 프로젝트 (*.csproj*) 파일에 다음을 추가*합니다.*

```xml
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
.
.
.
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>
</PropertyGroup>
```

 대상 (*.targets*) 파일에 확장을 직접 추가할 수 있습니다. 그러나 확장을 추가 하면 자체 뿐 아니라 로컬 시스템에 패키지 된 모든 SharePoint 프로젝트에 대 한 확장 목록이 변경 됩니다. 이 확장은 시스템의 유일한 개발자 이거나 대부분의 프로젝트에 필요한 경우에 편리할 수 있습니다. 그러나 시스템에 특정 하므로이 방법을 이식할 수 없으므로 프로젝트 파일에 확장을 추가 하는 것이 좋습니다.

## <a name="see-also"></a>참조
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
