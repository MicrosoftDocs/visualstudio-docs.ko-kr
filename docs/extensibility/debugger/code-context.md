---
title: 코드 컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739157"
---
# <a name="code-context"></a>코드 컨텍스트
디버깅에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **코드 컨텍스트**:

- 디버그 엔진(DE)에 알려진 코드의 위치 추상화를 제공합니다. 오늘날 대부분의 런타임 아키텍처의 경우 코드 컨텍스트는 프로그램의 명령 스트림에서 주소로 생각할 수 있습니다. 코드가 지침으로 표현되지 않는 비전통적인 언어의 경우 코드 컨텍스트가 다른 방법으로 표현될 수 있습니다.

- 디버깅하는 프로그램의 실행 스트림의 현재 위치를 설명합니다.

- 프로그램이 중단점에서 중지된 경우에만 존재합니다.

- 연결된 문서 컨텍스트가 있습니다.

- [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스에 의해 구현됩니다.

## <a name="see-also"></a>참조
- [문서 컨텍스트](../../extensibility/debugger/document-context.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
