---
title: 사용자 지정 디버그 엔진 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739032"
---
# <a name="create-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 만들기
DE(디버그 엔진)는 특정 런타임 아키텍처를 디버깅할 수 있는 구성 요소입니다. 일반적으로 런타임 환경당 하나의 DE 구현만 있습니다.

> [!NOTE]
> 트랜스액트 SQL 및 JScript에 대한 별도의 DE 구현이 있지만 VBScript와 JScript는 단일 DE를 공유합니다.

 DE는 인터프리터 또는 운영 시스템과 협력하여 실행 제어, 중단점 및 식 평가와 같은 디버깅 서비스를 제공합니다. 이러한 서비스는 DE 인터페이스를 통해 구현되며 디버거가 서로 다른 운영 모드 간에 전환될 수 있습니다. 자세한 내용은 [작동 모드를](../../extensibility/debugger/operational-modes.md)참조하십시오.

 DE 만들기는 다음 단계로 구성됩니다.

1. 비주얼 스튜디오로 DE 등록

2. 프로그램을 디버깅할 수 있도록 설정

3. 실행 제어 및 상태 평가 구현

4. 이벤트 보내기

5. 종단 설정 및 분리

## <a name="in-this-section"></a>섹션 내용
 [사용자 지정 디버그 엔진 등록](../../extensibility/debugger/registering-a-custom-debug-engine.md) 디버그 엔진을 사용할 수 있도록 Visual Studio에 등록하는 데 필요한 단계를 설명합니다.

 [프로그램을 디버깅할 수 있도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) DE가 프로그램을 디버깅하기 전에 먼저 DE를 시작하거나 기존 프로그램에 연결해야 한다고 설명합니다.

 [실행 제어 및 상태 평가 구현](../../extensibility/debugger/execution-control-and-state-evaluation.md) 응용 프로그램을 디버깅하려면 실행 제어 기능을 구현해야 하는 이유에 대해 설명합니다.

 [이벤트 보내기](../../extensibility/debugger/sending-events.md) 디버거와 DE 간의 통신을 DCOM을 기반으로 하는 이벤트 모델로 설명합니다.

 [종단 설정 및 분리](../../extensibility/debugger/termination-and-detaching.md) 디버깅할 응용 프로그램에 중단점, 예외, 런타임 오류 또는 무한 루프가 없음을 의미하는 일반 종료를 달성하는 방법을 설명합니다.

 [호출 디버거 이벤트](../../extensibility/debugger/calling-debugger-events.md) 디버깅 세션에서 발생하는 이벤트의 호출 순서를 문서화합니다.

 [방법: 사용자 지정 디버그 엔진 디버그](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) 사용자 지정 DE를 디버깅하는 방법을 설명합니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
