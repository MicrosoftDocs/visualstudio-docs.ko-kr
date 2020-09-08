---
title: 작업 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 070068853d962bdf9b209edb9410d33d46ccf853
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903560"
---
# <a name="debug-tasks"></a>작업 디버그
프로그램을 디버그하려면 프로그램을 시작하고 디버그 엔진(DE)을 연결해야 합니다. 그러지 않으면 이전에 실행한 프로그램에 DE를 연결해야 합니다. 연결되면 DE는 특정 시작 이벤트를 생성해야 합니다. 이에 대한 응답으로 디버그 패키지는 IDE에 설정된 중단점을 바인딩하려고 시도합니다. 프로그램이 바인딩된 중단점에 도달하면 중단되어 사용자 입력을 기다립니다.

## <a name="in-this-section"></a>섹션 내용
 [보안 문제](../../extensibility/debugger/security-issues.md) 프로그램을 디버그하는 데 필요한 보안 단계에 관해 설명합니다.

 [프로그램 시작](../../extensibility/debugger/launching-a-program.md) 운영 체제를 호출하여 프로그램을 시작하는 DE를 지정하는 방법에 대한 단계별 지침을 제공합니다.

 [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md) 이미 실행 중인 프로세스에서 프로그램을 디버그하는 데 사용되는 프로세스를 설명합니다.

 [시작 후 시작 이벤트 보내기](../../extensibility/debugger/sending-startup-events-after-a-launch.md) 프로그램이 기본 진입점에 있고 디버그 준비가 될 때까지 DE가 프로그램에 연결되면 발생하는 이벤트를 나열합니다.

 [실행 제어](../../extensibility/debugger/control-of-execution.md) 환경에 따라 일반적으로 DE가 진입점 이벤트, 로드 완료 이벤트 또는 중지 이벤트를 보내는 방법에 관해 설명합니다.

 [중단점 바인딩](../../extensibility/debugger/binding-breakpoints.md) 사용자가 중단점을 설정한 경우 IDE에서 요청을 공식화하고 디버그 세션에 중단점을 만들도록 대화 상자를 표시하는 방법을 설명합니다.

 [식 계산](../../extensibility/debugger/evaluating-expressions.md) 식이 생성되는 방법과 식이 계산될 때 발생하는 상황을 설명합니다.

 [데이터 시각화 및 보기](../../extensibility/debugger/visualizing-and-viewing-data.md) 식 계산기(EE)에서 형식 시각화 도우미 및 사용자 지정 뷰어를 지원하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 기본 디버깅 아키텍처 개념을 설명합니다.

 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md) DE, EE 및 기호 처리기(SH)를 포함하는 Visual Studio 디버깅 구성 요소에 대한 개요를 제공합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 코드, 문서 및 식 계산 컨텍스트 내에서 DE가 동시에 작동하는 방식을 설명합니다. 세 가지 컨텍스트, 위치 또는 관련 계산에 관해 설명합니다.

## <a name="see-also"></a>추가 정보
 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
