---
title: VSPackage 구조체 (소스 제어 VSPackage) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703802"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 구조(소스 제어 VSPackage)

소스 제어 패키지 SDK는 소스 제어 구현자를 사용 하 여 소스 제어 기능을 Visual Studio 환경과 통합할 수 있는 VSPackage를 만들기 위한 지침을 제공 합니다. VSPackage는 일반적으로 Visual Studio IDE (통합 개발 환경)에서 요청 시 해당 레지스트리 항목에서 패키지에 의해 보급 된 서비스를 기반으로 로드 되는 COM 구성 요소입니다. 모든 VSPackage은를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . VSPackage는 일반적으로 Visual Studio IDE에서 제공 하는 서비스를 사용 하 고 일부 서비스를 자체적으로 제공 합니다.

VSPackage는 해당 메뉴 항목을 선언 하 고 vsct 파일을 통해 기본 항목 상태를 설정 합니다. VSPackage이 로드 될 때까지 Visual Studio IDE는이 상태의 메뉴 항목을 표시 합니다. 그런 다음, VSPackage의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 구현이 호출 되어 메뉴 항목을 사용 하거나 사용 하지 않도록 설정 합니다.

## <a name="source-control-package-characteristics"></a>소스 제어 패키지 특징

소스 제어 VSPackage은 Visual Studio에 긴밀 하 게 통합 되어 있습니다. VSPackage 의미 체계는 다음과 같습니다.

- VSPackage (인터페이스)로 구현 되는 인터페이스입니다. `IVsPackage`

- UI 명령 구현 (vsct 파일 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 구현)

- Visual Studio를 사용 하 여 VSPackage를 등록 합니다.

소스 제어 VSPackage는 다음과 같은 다른 Visual Studio 엔터티와 통신 해야 합니다.

- 프로젝트

- 편집기

- 솔루션

- Windows

- 실행 중인 문서 테이블

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>사용 될 수 있는 Visual Studio 환경 서비스

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider 서비스

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>구현 및 호출 된 VSIP 인터페이스

원본 제어 패키지는 VSPackage 이므로 Visual Studio에 등록 된 다른 Vspackage와 직접 상호 작용할 수 있습니다. 모든 범위의 소스 제어 기능을 제공 하기 위해 소스 제어 VSPackage는 프로젝트 또는 셸에서 제공 하는 인터페이스를 처리할 수 있습니다.

Visual Studio의 모든 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual STUDIO IDE 내에서 프로젝트로 인식 되도록 구현 해야 합니다. 그러나이 인터페이스는 소스 제어에 충분 하지 않습니다. 소스 제어에서 구현 될 것으로 예상 되는 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 입니다. 이 인터페이스는 소스 제어 VSPackage에서 프로젝트의 내용에 대 한 프로젝트를 쿼리하고이 인터페이스에 문자 모양 및 바인딩 정보를 제공 하는 데 사용 됩니다 (서버 위치와 소스 제어에서 사용 중인 프로젝트의 디스크 위치 간에 연결을 설정 하는 데 필요한 정보).

소스 제어 VSPackage 구현 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> ,이를 통해 프로젝트에서 소스 제어를 위해 자체를 등록 하 고 해당 상태 문자 모양을 검색할 수 있습니다.

소스 제어에서 고려해 야 하는 인터페이스의 전체 목록은 [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)VSPackage를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
