---
title: VSIX 패키지의 해부학 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740084"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 패키지의 해부학
VSIX 패키지는 하나 이상의 Visual Studio 확장명이 포함된 *.vsix* 파일로, Visual Studio에서 확장프로그램을 분류하고 설치하는 데 사용하는 메타데이터도 함께 제공합니다. 해당 메타데이터는 VSIX 매니페스트와 *[Content_Types].xml* 파일에 포함됩니다. VSIX 패키지에는 지역화된 설치 텍스트를 제공하기 위해 하나 이상의 *Extension.vsixlangpack* 파일이 포함될 수 있으며 종속성을 설치하는 추가 VSIX 패키지가 포함될 수 있습니다.

 VSIX 패키지 형식은 개방형 패키징 규칙(OPC) 표준을 따릅니다. 패키지에는 *[Content_Types].xml* 파일 및 *.vsix* 매니페스트 파일과 함께 바이너리 및 지원 파일이 포함되어 있습니다. 하나의 VSIX 패키지에는 여러 프로젝트의 출력또는 자체 매니페스트가 있는 여러 패키지가 포함될 수 있습니다.

> [!NOTE]
> VSIX 패키지에 포함된 파일 이름에는 [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt)에 정의된 대로 공백이나 URI(균일 리소스 식별자)에 예약된 문자가 포함되어서는 안 됩니다.

## <a name="the-vsix-manifest"></a>VSIX 매니페스트
 VSIX 매니페스트에는 설치할 확장에 대한 정보가 포함되어 있으며 VSX 스키마를 따릅니다. 자세한 내용은 [VSIX 확장 스키마 1.0 참조를](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)참조하십시오. VSIX 매니페스트예제의 경우 [PackageManifest 요소(루트 요소, VSX 스키마)를](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187)참조하십시오.

 VSIX 매니페스트는 `extension.vsixmanifest` ^.vsix* 파일에 포함될 때 이름을 지정해야 합니다.

## <a name="the-content"></a>콘텐츠
 VSIX 패키지에는 템플릿, 도구 상자 항목, VSPackage 또는 Visual Studio에서 지원하는 다른 종류의 확장이 포함될 수 있습니다.

## <a name="language-packs"></a>언어 팩
 VSIX 패키지에는 설치 하는 동안 지역화된 텍스트를 제공 하기 위해 한 번 이상의 *Extension.vsixlangpack* 파일이 포함 될 수 있습니다. 자세한 내용은 [VSIX 패키지 지역화를](../extensibility/localizing-vsix-packages.md)참조하십시오.

## <a name="dependencies-and-references"></a>종속성 및 참조
 VSIX 패키지에는 다른 VSIX 패키지가 참조로 포함될 수 있습니다. 이러한 다른 각 패키지에는 자체 VSIX 매니페스트가 포함되어야 합니다.

 사용자가 종속성이 있는 확장을 설치하려고 하면 설치 관리자는 필요한 어셈블리가 사용자 시스템에 설치되었는지 확인합니다. 필요한 어셈블리를 찾을 수 없는 경우 **확장 및 업데이트에는** 누락된 어셈블리 목록이 표시됩니다.

 확장 매니페스트에 하나 이상의 [참조](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) 요소가 포함된 경우 **확장 및 업데이트는** 각 참조의 매니페스트를 시스템에 설치된 확장과 비교하고 아직 설치되지 않은 경우 참조된 확장을 설치합니다. 참조된 확장의 이전 버전이 설치된 경우 최신 버전이 이를 대체합니다.

 다중 프로젝트 솔루션의 프로젝트에 동일한 솔루션의 다른 프로젝트에 대한 참조가 포함된 경우 VSIX 패키지에는 해당 프로젝트의 종속성이 포함됩니다. 내부 프로젝트에 대한 참조를 클릭한 다음 **속성** 창에서 **VSIX 속성에 포함된 출력 그룹을** 로 `BuiltProjectOutputGroup`설정하여 이 동작을 재정의할 수 있습니다.

 VSIX 패키지에 참조된 어셈블리의 위성 DDL을 포함하려면 **VSIX** 속성에 포함된 출력 그룹에 추가합니다. `SatelliteDllsProjectOutputGroup`

## <a name="installation-location"></a>설치 위치
 설치 하는 동안 **확장 및 업데이트** 는 *%LocalAppData%\Microsoft\VisualStudio\14.0\확장*아래 의 폴더에 있는 VSIX 패키지의 내용을 찾습니다.

 *기본적으로 설치는 %LocalAppData%가* 사용자 별 디렉터리이므로 현재 사용자에게만 적용됩니다. 그러나 매니페스트의 [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) 요소를 설정 `True`하면 확장 <em>.. \\ </em>VisualStudioInstallationFolder<em>\Common7\IDE\확장</em> 및 컴퓨터의 모든 사용자가 사용할 수 있습니다.

## <a name="content_typesxml"></a>【Content_Types】.xml
 *[Content_Types].xml* 파일은 확장된 *.vsix* 파일의 파일 형식을 식별합니다. Visual Studio는 패키지를 설치하는 동안 이 파일을 사용하지만 파일 자체는 설치하지 않습니다. 이 파일에 대한 자세한 내용은 [[Content_types].xml 파일의 구조를](the-structure-of-the-content-types-dot-xml-file.md)참조하십시오.

 *[Content_Types].xml* 파일은 개방형 패키징 협약(OPC) 표준에 따라 필요합니다. OPC에 대한 자세한 내용은 OPC: MSDN 웹 사이트에서 [데이터를 패키징하기 위한 새로운 표준을](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) 참조하십시오.
