---
title: 종료 및 분리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712487"
---
# <a name="termination-and-detaching"></a>종단 및 분리
다음 섹션에서는 정상적인 종료에 대해 설명합니다.

## <a name="discussion"></a>토론
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 또는 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 인터페이스가 계속된 후 디버깅할 응용 프로그램의 중단점, 예외, 런타임 오류 또는 무한 루프가 없는 경우 디버깅중인 프로그램이 실행됩니다. 이 프로세스는 정상적인 종료입니다.

 정상적인 종료를 구현하려면 [IDebugProgramDestroyEvent2를](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) 보내야 합니다. 정상적인 종료는 [IDebugProgramDestroyEvent2:GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) 메서드를 실행해야 합니다.

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
