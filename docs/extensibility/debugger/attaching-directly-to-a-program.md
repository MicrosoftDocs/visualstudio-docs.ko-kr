---
title: 프로그램에 직접 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc78234b31b98865f1779dd65d743d4196f9cbf5
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903269"
---
# <a name="attach-directly-to-a-program"></a>프로그램에 직접 연결
이미 실행 중인 프로세스에서 프로그램을 디버깅 하려는 사용자는 일반적으로 다음 프로세스를 따릅니다.

1. IDE의 **도구** 메뉴에서 **프로세스 디버그** 명령을 선택 합니다.

    **프로세스** 대화 상자가 표시됩니다.

2. 프로세스를 선택 하 고 **연결** 단추를 클릭 합니다.

    **프로세스에 연결** 대화 상자가 표시 되 고 컴퓨터에 설치 된 모든 DEs (디버그 엔진)가 나열 됩니다.

3. 선택한 프로세스를 디버깅 하는 데 사용할 DEs를 지정 하 고 **확인**을 클릭 합니다.

   디버그 패키지는 디버그 세션을 시작 하 고 DEs 목록을 여기에 전달 합니다. 그러면 디버그 세션에서이 목록을 콜백 함수와 함께 선택한 프로세스에 전달한 다음 프로세스에 실행 중인 프로그램을 열거 하도록 요청 합니다.

   사용자 요청에 대 한 응답으로 디버그 패키지는 세션 디버그 관리자 (SDM)를 인스턴스화하고 선택한 DEs의 목록을 전달 합니다. 목록과 함께 디버그 패키지는 SDM에 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스를 전달 합니다. 디버그 패키지는 [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)를 호출 하 여 선택한 프로세스에 DEs 목록을 전달 합니다. 그러면 SDM에서 포트의 [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 을 호출 하 여 프로세스에서 실행 되는 프로그램을 열거 합니다.

   이 시점부터 각 디버그 엔진은 [시작 후 연결](../../extensibility/debugger/attaching-after-a-launch.md)에 설명 된 대로 정확 하 게 프로그램에 연결 됩니다. 단, 두 가지 예외가 있습니다.

   효율성을 높이기 위해 SDM과 주소 공간을 공유 하도록 구현 된 DEs는 각 DE-DE에 연결 되는 프로그램 집합을 포함 하도록 그룹화 됩니다. 이 경우 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 는 [IDebugEngine2:: attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 를 호출 하 여 연결할 프로그램의 배열을 전달 합니다.

   두 번째 예외는 이미 실행 중인 프로그램에 연결 해제를 통해 전송 되는 시작 이벤트에는 일반적으로 진입점 이벤트가 포함 되지 않기 때문입니다.

## <a name="see-also"></a>참조
- [시작 후 시작 이벤트 보내기](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
