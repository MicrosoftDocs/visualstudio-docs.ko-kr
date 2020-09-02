---
title: Interop 어셈블리를 사용 하는 명령 및 메뉴 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709492"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Interop 어셈블리를 사용 하는 명령 및 메뉴
Interop 어셈블리를 사용 하 여 메뉴 및 도구 모음 명령을 구현 하는 VSPackage는 다음을 수행 해야 합니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (통합 개발 환경)에 지원 되는 명령 및 현재 활성화 되어 있는지 여부를 알려 줍니다.

- 명령을 처리 하는 규칙 (계약)을 따릅니다.

- 또는 인터페이스 중 하나를 사용 하 여 명령 처리를 명시적으로 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 합니다.

  다음 섹션에서는 이러한 작업을 수행 하는 방법을 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [Interop 어셈블리를 사용 하 여 명령 상태 결정](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 VSPackage가 지 원하는 명령 및 현재 활성화 되어 있는지 여부를 IDE에 알리는 방법을 설명 합니다.

- [Interop 어셈블리의 명령 계약](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Interop 어셈블리를 사용 하 여 명령을 구현 하는 모든 Vspackage에서 사용 하는 기본 명령 계약의 정의를 제공 합니다.

- [명령 구현](../../extensibility/internals/command-implementation.md)

 VSPackage가 명령을 구현 하는 방법에 대 한 개요를 제공 합니다.

- [Interop 어셈블리 명령 처리기 등록](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 VSPackage 명령 처리기를 제공 한다는 것을 IDE에 알리는 데 필요한 레지스트리 항목에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [명령 가용성](../../extensibility/internals/command-availability.md)

 IDE에서 사용할 수 있는 VSPackage 명령과이 명령을 처리 하는 개체를 결정 하는 데 사용 되는 조건을 설명 합니다.

- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 명령 지원을 사용 하는 UI를 만드는 방법에 대해 자세히 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

- [Vspackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)

 개체와 올바른 명령 요청을 연결 하는 데 사용 되는 프로세스의 개요입니다.
