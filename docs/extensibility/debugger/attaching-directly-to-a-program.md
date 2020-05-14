---
title: 프로그램에 직접 연결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739253"
---
# <a name="attach-directly-to-a-program"></a>프로그램에 직접 연결
이미 실행 중인 프로세스에서 프로그램을 디버깅하려는 사용자는 일반적으로 다음 프로세스를 따릅니다.

1. IDE에서 **도구** 메뉴에서 **디버그 프로세스** 명령을 선택합니다.

    **프로세스** 대화 상자가 표시됩니다.

2. 프로세스를 선택하고 **연결** 단추를 클릭합니다.

    **프로세스에 연결** 대화 상자가 나타나컴퓨터에 설치된 모든 디버그 엔진(DEs)을 나열합니다.

3. 선택한 프로세스를 디버깅하는 데 사용할 DE를 지정한 다음 **확인을**클릭합니다.

   디버그 패키지는 디버그 세션을 시작하고 DEs 목록을 전달합니다. 디버그 세션은 콜백 함수와 함께 이 목록을 선택한 프로세스로 전달한 다음 실행 중인 프로그램을 나열하는 프로세스를 요청합니다.

   프로그래밍 방식으로 사용자 요청에 대한 응답으로 디버그 패키지는 세션 디버그 관리자(SDM)를 인스턴스화하고 선택한 DEs 목록을 전달합니다. 목록과 함께 디버그 패키지는 SDM에 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스를 전달합니다. 디버그 패키지는 [IDebugProcess2:Attach를](../../extensibility/debugger/reference/idebugprocess2-attach.md)호출하여 선택한 프로세스에 DEs 목록을 전달합니다. 그런 다음 SDM은 프로세스에서 실행 중인 프로그램을 열거하기 위해 포트의 [IDebugProcess2::EnumPrograms를](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 호출합니다.

   이 시점부터 각 디버그 엔진은 두 가지 예외를 제외하고 [시작 후 연결에](../../extensibility/debugger/attaching-after-a-launch.md)자세히 설명된 대로 프로그램에 연결됩니다.

   효율성을 위해 주소 공간을 SDM과 공유하도록 구현된 D는 그룹화되어 각 DE에 연결할 프로그램 집합이 있습니다. 이 경우 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 호출 [IDebugEngine2::연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 하 고 연결할 프로그램의 배열을 전달 합니다.

   두 번째 예외는 이미 실행 중인 프로그램에 연결한 DE에서 보낸 시작 이벤트에일반적으로 진입점 이벤트가 포함되지 않는다는 것입니다.

## <a name="see-also"></a>참조
- [시작 후 시작 이벤트 보내기](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
