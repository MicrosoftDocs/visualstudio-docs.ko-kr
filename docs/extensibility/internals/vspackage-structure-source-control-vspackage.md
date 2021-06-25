---
title: VSPackage 구조체(소스 제어 VSPackage) | Microsoft Docs
description: 소스 제어 구현자가 있는 VSPackage가 Visual Studio 통합하기 위한 지침을 제공하는 소스 제어 패키지 SDK에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898824"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage 구조(소스 제어 VSPackage)

소스 제어 패키지 SDK는 소스 제어 구현자가 소스 제어 기능을 Visual Studio 환경과 통합할 수 있도록 VSPackage를 만들기 위한 지침을 제공합니다. VSPackage는 일반적으로 레지스트리 항목에서 패키지에 의해 보급되는 서비스에 따라 Visual Studio IDE(통합 개발 환경)에 의해 필요에 따라 로드되는 COM 구성 요소입니다. 모든 VSPackage는 를 구현해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 합니다. VSPackage는 일반적으로 Visual Studio IDE에서 제공하는 서비스를 사용하고 자체의 일부 서비스를 제공합니다.

VSPackage는 메뉴 항목을 선언하고 .vsct 파일을 통해 기본 항목 상태를 설정합니다. Visual Studio IDE는 VSPackage가 로드될 때까지 메뉴 항목을 이 상태로 표시합니다. 이후에 VSPackage의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 구현은 메뉴 항목을 사용하거나 사용하지 않도록 설정하기 위해 호출됩니다.

## <a name="source-control-package-characteristics"></a>소스 제어 패키지 특징

소스 제어 VSPackage는 Visual Studio 깊이 통합됩니다. VSPackage 의미 체계는 다음과 같습니다.

- VSPackage(인터페이스)가 되어 구현할 `IVsPackage` 인터페이스

- UI 명령 구현(.vsct 파일 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 구현)

- Visual Studio VSPackage 등록

소스 제어 VSPackage는 다음과 같은 다른 Visual Studio 엔터티와 통신해야 합니다.

- 프로젝트

- 편집기

- 솔루션

- Windows

- 실행 중인 문서 테이블

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>사용할 수 있는 Visual Studio Environment Services

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider 서비스

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>구현 및 호출된 VSIP 인터페이스

소스 제어 패키지는 VSPackage이므로 Visual Studio 등록된 다른 VSPackage와 직접 상호 작용할 수 있습니다. 소스 제어 기능의 전체 너비를 제공하기 위해 VSPackage는 프로젝트 또는 셸에서 제공하는 인터페이스를 처리할 수 있습니다.

Visual Studio 모든 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio IDE 내에서 프로젝트로 인식되기 위해 를 구현해야 합니다. 그러나 이 인터페이스는 소스 제어에 대해 충분히 특수화되지 않습니다. 소스 제어에 있어야 하는 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 를 구현합니다. 이 인터페이스는 소스 제어 VSPackage에서 해당 콘텐츠에 대한 프로젝트를 쿼리하고 문자와 바인딩 정보를 제공하는 데 사용됩니다(서버 위치와 소스 제어 대상 프로젝트의 디스크 위치 간에 연결을 설정하는 데 필요한 정보).

소스 제어 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> 를 구현합니다. 그러면 프로젝트에서 소스 제어를 위해 자신을 등록하고 해당 상태 문자 표시를 검색할 수 있습니다.

소스 제어 VSPackage에서 고려해야 하는 인터페이스의 전체 목록은 [관련 서비스 및 인터페이스를 참조하세요.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>참조

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [관련 서비스 및 인터페이스](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
