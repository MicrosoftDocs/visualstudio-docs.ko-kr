---
title: 서버(Visual Studio SDK) | Microsoft Docs
description: 이 문서에서는 Visual Studio 디버거 아키텍처에서 서버의 정의 및 역할에 대해 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902126"
---
# <a name="servers-visual-studio-sdk"></a>서버(Visual Studio SDK)
디버거 아키텍처에서 *서버:*

- 포트 및 포트 공급자의 컨테이너이며 포트 및 포트 공급자를 SDM(세션 디버그 관리자) 및 디버그 엔진과 통신합니다.

- 이름으로 자신을 식별하고 포트 및 포트 공급자를 열거할 수 있습니다.

- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) 인터페이스로 표시됩니다. 이 인터페이스는 Visual Studio 의해서만 구현됩니다(실행 중인 Visual Studio 각 인스턴스에 대해 하나의 서버 인스턴스).

## <a name="see-also"></a>참조
- [Ports](../../extensibility/debugger/ports.md)
- [포트 공급자](../../extensibility/debugger/port-suppliers.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
