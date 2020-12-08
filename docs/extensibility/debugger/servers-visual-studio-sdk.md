---
title: 서버 (Visual Studio SDK) | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 서버 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9eaccebf874fa5fc0e7aaf63823547742215a568
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845299"
---
# <a name="servers-visual-studio-sdk"></a>서버(Visual Studio SDK)
디버거 아키텍처에서 *서버*:

- 는 포트 및 포트 공급자의 컨테이너 이며 포트 및 포트 공급자를 세션 디버그 관리자 (SDM) 및 디버그 엔진에 전달 합니다.

- 이름으로 자신을 식별 하 고 해당 포트 및 포트 공급자를 열거할 수 있습니다.

- 는 Visual Studio 에서만 구현 되는 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스로 표시 됩니다 .이 인터페이스는 visual studio를 실행 하는 각 인스턴스에 대해 하나의 서버 인스턴스만 구현 합니다.

## <a name="see-also"></a>참고 항목
- [Ports](../../extensibility/debugger/ports.md)
- [포트 공급자](../../extensibility/debugger/port-suppliers.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
