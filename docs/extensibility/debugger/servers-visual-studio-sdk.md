---
title: 서버(비주얼 스튜디오 SDK) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712891"
---
# <a name="servers-visual-studio-sdk"></a>서버(Visual Studio SDK)
디버거 아키텍처에서 *서버:*

- 포트 및 포트 공급자의 컨테이너이며 포트 및 포트 공급자를 세션 디버그 관리자(SDM) 및 디버그 엔진에 전달합니다.

- 이름으로 자신을 식별하고 포트 및 포트 공급자를 열거할 수 있습니다.

- Visual Studio에서만 구현되는 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스로 표시됩니다(실행되는 각 Visual Studio 인스턴스에 대한 서버 인스턴스 하나).

## <a name="see-also"></a>참조
- [Ports](../../extensibility/debugger/ports.md)
- [항구 공급업체](../../extensibility/debugger/port-suppliers.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
