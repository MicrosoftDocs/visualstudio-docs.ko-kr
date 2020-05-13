---
title: 프로그램 디버깅 가능 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738900"
---
# <a name="enable-a-program-to-be-debugged"></a>프로그램을 디버깅할 수 있도록 설정
DEBug 엔진(DE)이 프로그램을 디버깅하려면 먼저 DE를 시작하거나 기존 프로그램에 연결해야 합니다.

## <a name="in-this-section"></a>섹션 내용
 [포트 받기](../../extensibility/debugger/getting-a-port.md) 프로그램을 디버깅할 수 있도록 하는 첫 번째 단계로 포트를 가져오는 방법에 대해 설명합니다.

 [프로그램 등록](../../extensibility/debugger/registering-the-program.md) 프로그램을 디버깅할 수 있도록 하는 다음 단계, 즉 포트에 등록하는 다음 단계를 설명합니다. 등록이 완료되면 프로그램을 연결하는 프로세스 또는 JIT(적시) 디버깅 프로세스를 통해 디버깅할 수 있습니다.

 [프로그램에 연결](../../extensibility/debugger/attaching-to-the-program.md) 다음 단계: 디버거를 프로그램에 연결 합니다.

 [발사 기반 연결](../../extensibility/debugger/launch-based-attachment.md) SDM에서 실행시 자동으로 프로그램에 대한 시작 기반 첨부 파일을 설명합니다.

 [필요한 이벤트 보내기](../../extensibility/debugger/sending-the-required-events.md) DEBug 엔진(DE)을 만들고 프로그램에 연결할 때 필요한 이벤트를 단계로 이동합니다.

## <a name="related-sections"></a>관련 단원
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) DE(디버그 엔진)를 정의하고 DE 인터페이스를 통해 구현된 서비스와 디버거가 서로 다른 운영 모드 간에 전환되는 방법을 설명합니다.
