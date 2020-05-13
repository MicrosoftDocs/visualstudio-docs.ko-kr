---
title: 디버깅 작업 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738964"
---
# <a name="debug-tasks"></a>디버그 작업
프로그램을 디버깅하려면 프로그램을 시작하고 DE(디버그 엔진)를 연결해야 하며, 그렇지 않으면 DE를 이전에 시작한 프로그램에 연결해야 합니다. 연결되면 DE는 특정 시작 이벤트를 생성해야 합니다. 이에 대한 응답으로 디버그 패키지는 IDE에 설정된 중단점을 바인딩하려고 시도합니다. 프로그램이 바인딩된 중단점에 도달하면 중지되고 사용자 입력이 대기됩니다.

## <a name="in-this-section"></a>섹션 내용
 [보안 문제](../../extensibility/debugger/security-issues.md) 프로그램을 디버깅하는 데 필요한 보안 단계에 대해 설명합니다.

 [프로그램 실행](../../extensibility/debugger/launching-a-program.md) 프로그램을 실행하기 위해 운영 체제를 호출하는 DE를 지정하는 방법에 대한 단계별 지침을 제공합니다.

 [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md) 이미 실행 중인 프로세스에서 프로그램을 디버깅하는 데 사용되는 프로세스에 대해 설명합니다.

 [시작 후 시작 이벤트 보내기](../../extensibility/debugger/sending-startup-events-after-a-launch.md) 프로그램이 기본 진입점에 있고 디버깅할 준비가 될 때까지 DE가 프로그램에 연결되면 수행되는 이벤트를 나열합니다.

 [실행 제어](../../extensibility/debugger/control-of-execution.md) DE는 일반적으로 상황에 따라 진입점 이벤트, 로드 완료 이벤트 또는 중지 이벤트를 보내는 방법을 설명합니다.

 [중단점 바인딩](../../extensibility/debugger/binding-breakpoints.md) 사용자가 중단점을 설정하는 경우 IDE가 요청을 공식화하고 디버그 세션을 표시하여 중단점을 만드는 방법을 설명합니다.

 [표현식 평가](../../extensibility/debugger/evaluating-expressions.md) 식을 만들 때 와 식이 평가될 때 어떤 일이 발생하는지 설명합니다.

 [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md) 식 평가기(EE)에서 형식 시각화 도우미 및 사용자 지정 뷰어를 지원하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념에 대해 설명합니다.

 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md) DE, EE 및 기호 처리기(SH)를 포함하는 Visual Studio 디버깅 구성 요소에 대한 개요를 제공합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) DE가 코드, 설명서 및 식 평가 컨텍스트 내에서 동시에 작동하는 방법을 설명합니다. 세 가지 컨텍스트 각각에 대해 해당 컨텍스트와 관련된 위치, 위치 또는 평가에 대해 설명합니다.

## <a name="see-also"></a>참조
 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
