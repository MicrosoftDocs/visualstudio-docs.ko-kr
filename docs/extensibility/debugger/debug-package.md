---
title: 디버그 패키지 | Microsoft Docs
description: 디버그 패키지를 사용 하 여 Visual Studio shell에서 디버그 패키지를 실행 하 고 디버깅 인터페이스를 사용 하 고 세션 디버그 관리자와 통신 하 여 UI를 처리 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067909"
---
# <a name="debug-package"></a>패키지 디버그
디버그 패키지는 Visual Studio 셸에서 실행 되며 모든 UI를 처리 합니다. Visual Studio 디버깅 인터페이스를 사용 하 고, SDM (세션 디버그 관리자)과 통신 합니다.

 SDM을 통해 전송 되는 이벤트 중단 디버거를 실행 모드에서 중단 모드로 전환 하 고 중단이 발생 한 프로그램에 포커스를 변경 합니다. 디버그 패키지는 이벤트에 의해 전송 된 정보에서 스택 프레임과 스레드를 추적 합니다.

 디버그 패키지에는 언어 또는 런타임 환경 종속성이 없습니다. 디버그 패키지를 구현 하거나 수정할 필요는 없습니다.

 디버그 패키지는 *vsdebug.dll* 에 의해 구현 됩니다.

## <a name="see-also"></a>참조
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
