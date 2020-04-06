---
title: interop 어셈블리를 사용하여 명령 상태 결정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52bea32997b083cd13349a37201411e357f94a90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708709"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>interop 어셈블리를 사용하여 명령 상태 확인
VSPackage는 처리할 수 있는 명령의 상태를 추적해야 합니다. VSPackage 내에서 처리되는 명령이 활성화되거나 비활성화되는 시기를 환경에서 확인할 수 없습니다. VSPackage는 명령 상태(예: **잘라내기,** **복사**및 **붙여넣기)와**같은 일반 명령의 상태를 환경에 알리는 것이 VSPackage의 책임입니다.

## <a name="status-notification-sources"></a>상태 알림 소스
 환경은 VSPackage의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 인터페이스 구현의 일부인 VSPackage' 메서드를 통해 명령에 대한 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 정보를 수신합니다. 환경은 다음 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 두 가지 조건에서 VSPackage 메서드를 호출합니다.

- 사용자가 주 메뉴 또는 컨텍스트 메뉴를 마우스 오른쪽 단추로 클릭하면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 환경이 해당 메뉴의 모든 명령에 대한 메서드를 실행하여 상태를 확인합니다.

- VSPackage가 환경이 현재 사용자 인터페이스(UI)를 업데이트하도록 요청하는 경우 이 업데이트는 표준 도구 모음에서 **잘라내기,** **복사**및 **붙여넣기** 그룹화와 같이 현재 사용자에게 표시되는 명령이 컨텍스트 및 사용자 작업에 대한 응답으로 활성화되고 비활성화될 때 발생합니다.

  셸은 여러 VSPackage를 호스트하므로 명령 상태를 결정하기 위해 각 VSPackage를 폴링해야 하는 경우 셸의 성능이 허용되지 않습니다. 대신 VSPackage는 변경 시 UI가 변경될 때 환경에 적극적으로 알려야 합니다. 업데이트 알림에 대한 자세한 내용은 [사용자 인터페이스 업데이트를](../../extensibility/updating-the-user-interface.md)참조하십시오.

## <a name="status-notification-failure"></a>상태 알림 오류
 명령 상태 변경의 환경을 알리는 VSPackage를 실패하면 UI가 일치하지 않는 상태가 될 수 있습니다. 사용자가 도구 모음에 메뉴 또는 컨텍스트 메뉴 명령을 배치할 수 있습니다. 따라서 메뉴 또는 컨텍스트 메뉴가 열리는 경우에만 UI를 업데이트하는 것만으로는 충분하지 않습니다.

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [구현](../../extensibility/internals/command-implementation.md)
