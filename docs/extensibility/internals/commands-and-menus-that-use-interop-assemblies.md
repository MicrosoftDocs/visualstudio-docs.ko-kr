---
title: 인터옵 어셈블리를 사용하는 명령 및 메뉴 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709492"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Interop 어셈블리를 사용하는 명령 및 메뉴
INTERop 어셈블리를 사용하여 메뉴 및 도구 모음 명령을 구현하는 VSPackage는 다음을 수행해야 합니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)에 지원하는 명령과 현재 사용 가능한 명령여부를 알립니다.

- 명령 처리를 위한 규칙(계약)을 준수합니다.

- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스를 사용하여 명령 처리를 명시적으로 구현합니다.

  다음 섹션에서는 이러한 작업을 수행하는 방법을 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [Interop 어셈블리를 사용하여 명령 상태 확인](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 VSPackage가 지원하는 명령과 현재 사용 가능한 지 여부에 대해 IDE에 알리는 방법을 설명합니다.

- [Interop 어셈블리의 명령 계약](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Interop 어셈블리를 사용하여 명령을 구현하는 모든 VSPackage에서 사용하는 기본 명령 계약에 대한 정의를 제공합니다.

- [명령 구현](../../extensibility/internals/command-implementation.md)

 VSPackage가 명령을 구현하는 방법에 대한 개요를 제공합니다.

- [Interop 어셈블리 명령 처리기 등록](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 VSPackage 명령 처리기를 제공 하는 IDE를 알리는 데 필요한 레지스트리 항목을 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [명령 가용성](../../extensibility/internals/command-availability.md)

 IDE에서 사용할 수 있는 VSPackage 명령과 해당 명령을 처리하는 개체를 결정하는 데 사용되는 조건을 설명합니다.

- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 명령 지원을 사용하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI를 만드는 방법에 대한 세부 정보를 제공합니다.

- [VS패키지의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)

 개체를 올바른 명령 요청과 연관하는 데 사용되는 프로세스의 개요입니다.
