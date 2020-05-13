---
title: 중단점 (비주얼 스튜디오 SDK) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739194"
---
# <a name="breakpoints-visual-studio-sdk"></a>중단점(Visual Studio SDK)
중단점에는 보류 중, 바인딩 및 오류의 세 가지 유형이 있습니다.

 **보류 중인 중단점:**

- 하나 이상의 프로그램에서 중단점을 하나 이상의 코드 컨텍스트에 바인딩하는 데 필요한 모든 정보를 포함하는 추상화입니다. 디버깅 중인 프로그램이 코드를 로드할 때마다 디버그 엔진은 보류 중인 모든 중단점을 검사하여 바인딩할 수 있는지 확인합니다.

   보류 중인 중단점 자체는 코드에 바인딩되지 않고 생성되는 모든 바인딩된 중단점을 수집하여 포함한다고 합니다.

- [IDebugPending중단포인트2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스로 표시됩니다.

  **바인딩된 중단점:**

- 단일 코드 컨텍스트와 연결되거나 바인딩된 중단점에 대한 추상화입니다. 각 바인딩된 중단점은 보류 중인 중단점에 대한 응답으로 생성됩니다. 그러나 보류 중인 중단점은 하나 이상의 바인딩된 중단점을 생성할 수 있습니다.

   코드가 언로드되면 바인딩된 중단점은 언바운드되고 삭제될 수 있습니다.

- [IDebug바운드Breakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스로 표시됩니다.

  **오류 중단점:**

- 보류 중인 중단점을 코드 컨텍스트에 바인딩하려고 할 때 오류를 설명하는 추상화입니다. 오류 중단점은 위치 또는 중단점 식 자체의 오류를 설명합니다. 자세한 내용은 [바인딩 중단점을](../../extensibility/debugger/binding-breakpoints.md)참조하십시오.

   중단점 오류는 오류 또는 경고일 수 있습니다.

- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스로 표시됩니다.

## <a name="see-also"></a>참조
- [Programs](../../extensibility/debugger/programs.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
