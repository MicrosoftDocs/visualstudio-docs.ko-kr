---
title: Interop 어셈블리를 사용 하 여 명령 상태 결정 | Microsoft Docs
description: VisualStudio 인터페이스를 사용 하 여 VSPackage에서 처리 되는 명령의 상태를 확인 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5473fffa00723735b022412e7f37f184e043df4b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963447"
---
# <a name="determine-command-status-by-using-interop-assemblies"></a>Interop 어셈블리를 사용 하 여 명령 상태 결정
VSPackage는 처리할 수 있는 명령의 상태를 추적 해야 합니다. 환경에서는 VSPackage 내에서 처리 된 명령이 활성화 또는 비활성화 상태가 되는 시점을 확인할 수 없습니다. VSPackage는 명령 상태 (예: **잘라내기**, **복사**, **붙여넣기** 등의 일반 명령 상태)를 환경에 알리는 것이 가장 좋습니다.

## <a name="status-notification-sources"></a>상태 알림 원본
 환경에서는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage의 인터페이스 구현에 포함 된 vspackage ' 메서드를 통해 명령에 대 한 정보를 수신 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . 환경에서는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 다음 두 조건에서 VSPackage의 메서드를 호출 합니다.

- 사용자가 마우스 오른쪽 단추를 클릭 하 여 주 메뉴 또는 상황에 맞는 메뉴를 열면 환경에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 해당 메뉴의 모든 명령에 대해 메서드를 실행 하 여 해당 상태를 확인 합니다.

- VSPackage는 환경에서 현재 UI (사용자 인터페이스)를 업데이트 하도록 요청 합니다. 이 업데이트는 표준 도구 모음에서 **잘라내기**, **복사** 및 **붙여넣기** 그룹과 같이 사용자에 게 현재 표시 되는 명령으로 발생 하며, 컨텍스트 및 사용자 동작에 대 한 응답으로 활성화 및 비활성화 됩니다.

  셸은 여러 Vspackage를 호스트 하므로 각 VSPackage를 폴링하여 명령 상태를 결정 해야 하는 경우 셸의 성능이 크게 저하 됩니다. 대신, 변경 시 VSPackage UI가 변경 되 면 환경에 적극적으로 알려야 합니다. 업데이트 알림에 대 한 자세한 내용은 [사용자 인터페이스 업데이트](../../extensibility/updating-the-user-interface.md)를 참조 하세요.

## <a name="status-notification-failure"></a>상태 알림 오류
 환경에 명령 상태 변경 내용에 대 한 알림을 VSPackage 하는 데 실패 하면 UI가 일관 되지 않은 상태가 될 수 있습니다. 메뉴 또는 상황에 맞는 메뉴 명령은 사용자가 도구 모음에 배치할 수 있습니다. 따라서 메뉴 또는 상황에 맞는 메뉴가 열리면 UI를 업데이트 하는 것 만으로는 충분 하지 않습니다.

## <a name="see-also"></a>참고 항목
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [구현](../../extensibility/internals/command-implementation.md)
