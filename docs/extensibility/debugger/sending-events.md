---
title: 이벤트 보내기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713037"
---
# <a name="send-events"></a>이벤트 보내기
디버거와 디버그 엔진(DE) 간의 통신 메커니즘은 DCOM을 기반으로 하는 이벤트 모델입니다. 이벤트는 COM 개체로 전송되며 각 이벤트에는 다음을 지정하는 매개 변수가 있습니다.

- 이벤트를 호출한 DE입니다.

- 무슨 일이 있었는지에 대한 설명입니다.

- 이벤트가 발생한 위치의 컨텍스트를 식별하는 프로세스, 프로그램 및 스레드 정보입니다. DE에서 보낸 이벤트에 대해 프로세스가 전송되지 않습니다.

- 이벤트가 동기인지 비동기인지를 나타내는 이벤트 유형입니다.

  모든 디버그 이벤트는 [IDebugEventCallback2:Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)메서드를 사용하여 전송됩니다.

## <a name="in-this-section"></a>섹션 내용
 [이벤트 소스](../../extensibility/debugger/event-sources-visual-studio-sdk.md) 디버그 엔진(DE)과 세션 디버그 관리자(SDM)의 두 가지 이벤트 소스에 대해 설명합니다.

 [지원되는 이벤트 유형](../../extensibility/debugger/supported-event-types.md) 현재 지원되는 이벤트 유형인 비동기 및 동기에 대해 설명합니다.

 [이벤트 설명](../../extensibility/debugger/event-descriptions.md) 이벤트및이벤트사용사유를정의합니다.

## <a name="related-sections"></a>관련 단원
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) DE가 인터버깅 서비스를 제공하기 위해 인터프리터 또는 운영 체제와 함께 작동하는 방법을 설명합니다.
