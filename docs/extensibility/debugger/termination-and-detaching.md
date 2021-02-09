---
title: 종료 및 분리 | Microsoft Docs
description: 정상적인 종료는 디버깅 중인 프로그램이 중단점, 예외, 런타임 오류 또는 무한 루프 없이 완료 될 때까지 실행 됨을 의미 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895897"
---
# <a name="termination-and-detaching"></a>종료 및 분리
다음 섹션에서는 일반적인 종료에 대해 설명 합니다.

## <a name="discussion"></a>토론(Discussion)
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 또는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 인터페이스가 계속 되 면 디버깅 될 응용 프로그램에서 중단점, 예외, 런타임 오류 또는 무한 루프가 발생 하지 않는 경우 디버깅 중인 프로그램이 완료 될 때까지 실행 됩니다. 이 프로세스는 정상적인 종료입니다.

 정상적인 종료를 구현 하려면 [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 을 보내야 합니다. 정상적인 종료를 수행 하려면 [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 메서드를 실행 해야 합니다.

## <a name="see-also"></a>참고 항목
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
