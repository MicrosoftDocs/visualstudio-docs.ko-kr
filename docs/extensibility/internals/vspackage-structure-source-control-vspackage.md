---
title: VS패키지 구조(소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703802"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 구조(소스 제어 VSPackage)

소스 제어 패키지 SDK는 소스 제어 구현자가 자신의 소스 제어 기능을 Visual Studio 환경과 통합할 수 있도록 VSPackage를 만드는 지침을 제공합니다. VSPackage는 일반적으로 레지스트리 항목의 패키지에 의해 보급되는 서비스를 기반으로 IDE(Visual Studio 통합 개발 환경)에서 요청 시 로드되는 COM 구성 요소입니다. 모든 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>을 구현해야 합니다. VSPackage는 일반적으로 Visual Studio IDE에서 제공하는 서비스를 사용하고 자체 서비스를 제공합니다.

VSPackage는 메뉴 항목을 선언하고 .vsct 파일을 통해 기본 항목 상태를 설정합니다. 비주얼 스튜디오 IDE는 VSPackage가 로드될 때까지 이 상태의 메뉴 항목을 표시합니다. 그런 다음 VSPackage의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 구현을 호출하여 메뉴 항목을 사용하거나 사용하지 않도록 설정합니다.

## <a name="source-control-package-characteristics"></a>소스 제어 패키지 특성

소스 제어 VSPackage는 Visual Studio에 깊이 통합되어 있습니다. VSPackage 의미 체계는 다음과 같습니다.

- `IVsPackage` VSPackage(인터페이스)이기 때문에 구현할 인터페이스

- UI 명령 구현(.vsct 파일 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 및 인터페이스 구현)

- 비주얼 스튜디오와 VS패키지의 등록.

소스 제어 VSPackage는 다음과 같은 다른 Visual Studio 엔터티와 통신해야 합니다.

- 프로젝트

- 편집기

- 솔루션

- Windows

- 실행 중인 문서 테이블

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>사용할 수 있는 비주얼 스튜디오 환경 서비스

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciprovider 서비스

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP 인터페이스 구현 및 호출

소스 제어 패키지는 VSPackage이므로 Visual Studio에 등록된 다른 VSPackage와 직접 상호 작용할 수 있습니다. 소스 제어 기능의 전체 폭을 제공하기 위해 소스 제어 VSPackage는 프로젝트 또는 셸에서 제공하는 인터페이스를 처리할 수 있습니다.

Visual Studio의 모든 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 프로젝트는 Visual Studio IDE 내의 프로젝트로 인식되기 위해 구현해야 합니다. 그러나 이 인터페이스는 소스 제어를 위해 충분히 전문화되지 않습니다. 소스 제어 구현에 따라 수행될 것으로 예상되는 프로젝트 입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 이 인터페이스는 소스 제어 VSPackage에서 해당 내용에 대한 프로젝트를 쿼리하고 글리프 및 바인딩 정보(서버 위치와 소스 제어 중인 프로젝트의 디스크 위치 간의 연결을 설정하는 데 필요한 정보)를 제공하는 데 사용됩니다.

소스 제어 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>구현, 차례로 프로젝트 소스 제어에 대 한 자신을 등록 하 고 해당 상태 문말 기를 검색할 수 있습니다.

소스 제어 VSPackage에서 고려해야 하는 인터페이스의 전체 목록은 [관련 서비스 및 인터페이스를](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)참조하십시오.

## <a name="see-also"></a>참조

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
