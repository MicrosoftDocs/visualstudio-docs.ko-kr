---
title: 이벤트 전송 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204737"
---
# <a name="sending-events"></a>이벤트 보내기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거와 디버그 엔진 (DE) 간의 통신 메커니즘은 DCOM을 기반으로 하는 이벤트 모델입니다. 이벤트는 COM 개체로 전송 되며, 각 이벤트에는 다음을 지정 하는 매개 변수가 있습니다.  
  
- 이벤트를 호출한 DE입니다.  
  
- 발생 한 상황에 대 한 설명입니다.  
  
- 이벤트가 발생 한 컨텍스트를 식별 하는 프로세스, 프로그램 및 스레드 정보입니다. DE에서 전송 된 이벤트에 대해서는 프로세스가 전송 되지 않습니다.  
  
- 이벤트가 동기 또는 비동기 인지 여부를 나타내는 이벤트 형식입니다.  
  
  모든 디버그 이벤트는 메서드 [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)를 사용 하 여 전송 됩니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [이벤트 원본](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 디버그 엔진 (DE) 및 세션 디버그 관리자 (SDM)의 두 이벤트 소스에 대해 설명 합니다.  
  
 [지원되는 이벤트 형식](../../extensibility/debugger/supported-event-types.md)  
 현재 지원 되는 이벤트 유형인 비동기 및 동기를 설명 합니다.  
  
 [이벤트 설명](../../extensibility/debugger/event-descriptions.md)  
 이벤트 및 해당 사용 이유를 정의 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 DE 또는 운영 체제에서 DE를 사용 하 여 디버깅 서비스를 제공 하는 방법을 설명 합니다.
