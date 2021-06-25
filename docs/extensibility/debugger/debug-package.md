---
title: 패키지 | 디버그 Microsoft Docs
description: 디버그 패키지가 Visual Studio 셸에서 실행되고 디버깅 인터페이스를 사용하며 세션 디버그 관리자와 통신하여 UI를 처리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905672"
---
# <a name="debug-package"></a>패키지 디버그
디버그 패키지는 Visual Studio 셸에서 실행되고 모든 UI를 처리합니다. Visual Studio 디버깅 인터페이스를 사용하고 SDM(세션 디버그 관리자)과 통신합니다.

 SDM을 통해 전송된 중단 이벤트는 디버거를 실행 모드에서 중단 모드로 전환하고 중단이 발생한 프로그램으로 포커스를 변경합니다. 디버그 패키지는 이벤트가 전송한 정보에서 스택 프레임 및 스레드를 추적합니다.

 디버그 패키지에는 언어 또는 런타임 환경이 없습니다. 디버그 패키지를 구현하거나 수정할 필요는 없습니다.

 디버그 패키지는 *vsdebug.dll* 의해 구현됩니다.

## <a name="see-also"></a>참조
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
