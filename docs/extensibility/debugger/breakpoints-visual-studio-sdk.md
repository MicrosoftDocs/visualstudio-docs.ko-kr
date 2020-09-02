---
title: 중단점 (Visual Studio SDK) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739194"
---
# <a name="breakpoints-visual-studio-sdk"></a>중단점(Visual Studio SDK)
중단점에는 보류 중, 바인딩 및 오류의 세 가지 유형이 있습니다.

 **보류 중인 중단점:**

- 는 하나 이상의 프로그램에서 하나 이상의 코드 컨텍스트에 중단점을 바인딩하는 데 필요한 모든 정보를 포함 하는 추상화입니다. 디버깅할 프로그램에서 코드가 로드 될 때마다 디버그 엔진은 보류 중인 모든 중단점을 검사 하 여 바인딩할 수 있는지 여부를 확인 합니다.

   보류 중인 중단점 자체는 코드에 바인딩되지 않으며 생성 되는 모든 바인딩된 중단점을 포함 하는 것으로 간주 됩니다.

- 는 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스로 표시 됩니다.

  **바인딩된 중단점:**

- 는 단일 코드 컨텍스트에 연결 되거나 바인딩된 중단점에 대 한 추상화입니다. 바인딩된 각 중단점은 보류 중인 중단점에 대 한 응답으로 생성 됩니다. 그러나 보류 중인 중단점은 둘 이상의 바인딩된 중단점을 생성할 수 있습니다.

   코드가 언로드될 때 바인딩된 중단점의 바인딩을 해제 하 고 삭제할 수 있습니다.

- 는 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스로 표시 됩니다.

  **오류 중단점:**

- 는 보류 중인 중단점을 코드 컨텍스트에 바인딩하는 동안 발생 하는 오류를 설명 하는 추상화입니다. 오류 중단점은 위치 또는 중단점 식 자체의 오류를 설명 합니다. 자세한 내용은 [중단점 바인딩](../../extensibility/debugger/binding-breakpoints.md)을 참조 하세요.

   중단점 오류는 오류 또는 경고 일 수 있습니다.

- 는 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [프로그램](../../extensibility/debugger/programs.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
