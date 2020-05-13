---
title: 디버그 패키지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739029"
---
# <a name="debug-package"></a>디버그 패키지
디버그 패키지는 Visual Studio 셸에서 실행되며 모든 UI를 처리합니다. Visual Studio 디버깅 인터페이스를 사용하고 세션 디버그 관리자(SDM)와 통신합니다.

 SDM을 통해 전송된 중단 이벤트는 디버거를 실행 모드에서 중단 모드로 전환하고 중단이 발생한 프로그램으로 포커스를 변경합니다. 디버그 패키지는 이벤트에서 전송된 정보에서 스택 프레임과 스레드를 추적합니다.

 디버그 패키지에는 언어 또는 런타임 환경 종속성이 없습니다. 디버그 패키지를 구현하거나 수정할 필요는 없습니다.

 디버그 패키지는 *vsdebug.dll에*의해 구현됩니다.

## <a name="see-also"></a>참조
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
