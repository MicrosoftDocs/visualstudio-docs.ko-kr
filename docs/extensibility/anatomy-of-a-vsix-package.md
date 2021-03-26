---
title: VSIX 패키지의 분석 | Microsoft Docs
description: Visual Studio에서 하나 이상의 Visual Studio 확장 및 메타 데이터 매니페스트 파일이 포함 된 파일인 VSIX 패키지의 내용에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67b3775509e330ad55a2531a9e42a7cca93c50a6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097502"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX 패키지 분석
VSIX 패키지는 visual Studio에서 확장을 분류 하 고 설치 하는 데 사용 하는 메타 데이터와 함께 하나 이상의 Visual Studio 확장을 포함 하는 *.vsix* 파일입니다. 이 메타 데이터는 VSIX 매니페스트와 *[Content_Types] .xml* 파일에 포함 되어 있습니다. VSIX 패키지에는 지역화 된 설정 텍스트를 제공 하기 위해 하나 이상의 *확장명 vsixlangpack* 파일이 포함 되어 있을 수 있으며, 종속성을 설치 하기 위한 추가 VSIX 패키지가 포함 될 수도 있습니다.

 VSIX 패키지 형식은 OPC (Open 패키징 규칙) 표준을 따릅니다. 패키지에는 이진 파일과 지원 파일, *[Content_Types] .xml* 파일 및 *.vsix* 매니페스트 파일이 포함 되어 있습니다. 하나의 VSIX 패키지는 여러 프로젝트의 출력 또는 자체 매니페스트가 있는 여러 패키지를 포함할 수 있습니다.

> [!NOTE]
> VSIX 패키지에 포함 된 파일의 이름에는 공백이 포함 될 수 없으며 [ \[ RFC2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)아래에 정의 된 대로 URI (Uniform resource identifier)로 예약 된 문자도 포함 되지 않아야 합니다.

## <a name="the-vsix-manifest"></a>VSIX 매니페스트
 VSIX 매니페스트에는 설치할 확장에 대 한 정보가 포함 되어 있으며 VSX 스키마를 따릅니다. 자세한 내용은 [VSIX 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))를 참조 하세요. 예제 VSIX 매니페스트는 [PackageManifest 요소 (root 요소, VSX schema)](/previous-versions/dd393754(v=vs.110))를 참조 하세요.

 VSIX 매니페스트는 `extension.vsixmanifest` ^ .vsix * 파일에 포함 될 때 이름이 지정 되어야 합니다.

## <a name="the-content"></a>콘텐츠
 VSIX 패키지는 템플릿, 도구 상자 항목, Vspackage 또는 Visual Studio에서 지원 되는 다른 종류의 확장 프로그램을 포함할 수 있습니다.

## <a name="language-packs"></a>언어 팩
 VSIX 패키지는 설치 하는 동안 지역화 된 텍스트를 제공 하기 위해 한 번 이상 *확장명이 vsixlangpack* 파일을 포함할 수 있습니다. 자세한 내용은 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)를 참조 하세요.

## <a name="dependencies-and-references"></a>종속성 및 참조
 VSIX 패키지에는 다른 VSIX 패키지가 참조로 포함 될 수 있습니다. 이러한 각 패키지는 자체 VSIX 매니페스트를 포함 해야 합니다.

 사용자가 종속성이 있는 확장을 설치 하려고 하면 설치 관리자가 필수 어셈블리가 사용자 시스템에 설치 되어 있는지 확인 합니다. 필요한 어셈블리를 찾을 수 없는 경우 **확장 및 업데이트** 에서 누락 된 어셈블리의 목록을 표시 합니다.

 확장 매니페스트에 하나 이상의 [참조](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) 요소가 포함 된 경우 **확장 및 업데이트** 는 각 참조의 매니페스트를 시스템에 설치 된 확장과 비교 하 고 아직 설치 되지 않은 경우 참조 된 확장을 설치 합니다. 참조 된 확장의 이전 버전이 설치 되어 있으면 최신 버전으로 대체 됩니다.

 다중 프로젝트 솔루션의 프로젝트가 동일한 솔루션의 다른 프로젝트에 대 한 참조를 포함 하는 경우 VSIX 패키지에는 해당 프로젝트의 종속성이 포함 됩니다. 내부 프로젝트에 대 한 참조를 선택한 다음 **속성** 창에서 **VSIX 속성에 포함 된 출력 그룹** 을로 설정 하 여이 동작을 재정의할 수 있습니다 `BuiltProjectOutputGroup` .

 VSIX 패키지에서 참조 된 어셈블리의 위성 Dll을 포함 하려면 `SatelliteDllsProjectOutputGroup` **vsix 속성에 포함 된 출력 그룹** 에를 추가 합니다.

## <a name="installation-location"></a>설치 위치
 설치 하는 동안 **확장 및 업데이트** 는 *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* 아래의 폴더에 있는 VSIX 패키지의 콘텐츠를 찾습니다.

 *% LocalAppData%은 (* 는) 사용자별 디렉터리 이므로 기본적으로 현재 사용자 에게만 설치가 적용 됩니다. 그러나 매니페스트의 [AllUsers](/previous-versions/ee191547(v=vs.110)) 요소를로 설정 하는 경우 `True` 확장은 <em> \\ .</em> 로 설치 됩니다. VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> 는 컴퓨터의 모든 사용자가 사용할 수 있습니다.

## <a name="content_typesxml"></a>[Content_Types] .xml
 *[Content_Types] .xml* 파일은 확장 된 *.vsix* 파일의 파일 형식을 식별 합니다. Visual Studio는 패키지를 설치 하는 동안이 파일을 사용 하지만 파일 자체는 설치 하지 않습니다. 이 파일에 대 한 자세한 내용은 [[Content_types] .xml 파일의 구조](the-structure-of-the-content-types-dot-xml-file.md)를 참조 하십시오.

 *[Content_Types] .xml* 파일은 OPC (Open 패키징 규칙) 표준에 필요 합니다. OPC에 대 한 자세한 내용은 Opc: MSDN 웹 사이트에서 [데이터를 패키징하는 새 표준](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) 을 참조 하세요.