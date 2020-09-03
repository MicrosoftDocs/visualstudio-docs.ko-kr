---
title: 디버깅할 프로그램 사용 설정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738900"
---
# <a name="enable-a-program-to-be-debugged"></a>디버깅할 프로그램 사용
디버그 엔진 (DE)이 프로그램을 디버깅 하려면 먼저 DE를 시작 하거나 기존 프로그램에 연결 해야 합니다.

## <a name="in-this-section"></a>섹션 내용
 [포트 가져오기](../../extensibility/debugger/getting-a-port.md) 프로그램을 디버그할 수 있도록 첫 번째 단계로 포트를 가져오는 방법에 대해 설명 합니다.

 [프로그램 등록](../../extensibility/debugger/registering-the-program.md) 프로그램을 디버그할 수 있도록 하는 다음 단계에 대해 설명 합니다. 포트를 사용 하 여 등록 합니다. 등록 한 후에는 연결 또는 JIT (just-in-time) 디버깅 프로세스를 통해 프로그램을 디버그할 수 있습니다.

 [프로그램에 연결](../../extensibility/debugger/attaching-to-the-program.md) 프로그램에 디버거를 연결 하는 다음 단계에 대해 설명 합니다.

 [시작 기반 연결](../../extensibility/debugger/launch-based-attachment.md) 프로그램에 대 한 시작 기반 첨부 파일에 대해 설명 합니다 .이는 SDM에서 시작 될 때 자동으로 실행 됩니다.

 [필요한 이벤트 보내기](../../extensibility/debugger/sending-the-required-events.md) 디버그 엔진 (DE)을 만들고 프로그램에 연결할 때 필요한 이벤트를 단계별로 안내 합니다.

## <a name="related-sections"></a>관련 단원
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) DE (디버그 엔진)를 정의 하 고 DE 인터페이스를 통해 구현 되는 서비스 및이로 인해 디버거가 여러 작업 모드 간에 전환 되는 방법을 설명 합니다.
