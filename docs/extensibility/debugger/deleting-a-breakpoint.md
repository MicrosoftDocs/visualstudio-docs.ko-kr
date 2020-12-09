---
title: 중단점 삭제 | Microsoft Docs
description: 보류 중인 중단점을 삭제 하는 경우 세션 디버그 관리자가 보류 중인 중단점과 해당 중단점에서 바인딩된 모든 중단점을 제거 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915559"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
다음은 보류 중인 중단점을 삭제 하는 프로세스에 대 한 설명입니다.

## <a name="deletion-process"></a>삭제 프로세스
 [IDebugPendingBreakpoint2::D e)](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 메서드를 호출 하 여 보류 중인 중단점과 여기에서 바인딩된 모든 바인딩된 중단점을 제거 합니다.

> [!NOTE]
> [IDebugBoundBreakpoint2::D e)](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)를 호출 하 여 단일 바인딩된 중단점을 삭제할 수도 있습니다.

## <a name="see-also"></a>참고 항목
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
