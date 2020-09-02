---
title: 코드 컨텍스트 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739157"
---
# <a name="code-context"></a>코드 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅에서 **코드 컨텍스트**는 다음과 같습니다.

- 디버그 엔진 (DE)에 알려진 코드의 위치에 대 한 추상화를 제공 합니다. 오늘날 대부분의 런타임 아키텍처에서 코드 컨텍스트는 프로그램의 명령 스트림에서 주소로 간주할 수 있습니다. 특수 언어의 경우 코드를 명령으로 표현할 수 없는 경우 다른 방법으로 코드 컨텍스트를 나타낼 수 있습니다.

- 디버깅 중인 프로그램의 실행 스트림에서 현재 위치를 설명 합니다.

- 프로그램이 중단점에서 중지 된 경우에만 존재 합니다.

- 에는 연결 된 문서 컨텍스트가 있습니다.

- 는 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스에 의해 구현 됩니다.

## <a name="see-also"></a>추가 정보
- [문서 컨텍스트](../../extensibility/debugger/document-context.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
