---
title: 이벤트 설명 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738796"
---
# <a name="event-descriptions"></a>이벤트 설명
각 이벤트 유형에는 특정 목적이 있습니다.

## <a name="events-and-the-reasons-for-their-use"></a>이벤트 및 사용 이유

|이벤트|설명|
|-----------|-----------------|
|문서 이벤트 활성화|디버그 엔진 (DE)에서 IDE를 열거나 문서를 전경으로 가져올 때 발생 합니다.|
|중단점 바인딩 또는 중단점 오류 이벤트|중단점이 바인딩되거나 중단점을 바인딩할 수 없고 오류가 반환 될 때 전송 됩니다.|
|중단점 바인딩되지 않은 이벤트|바인딩된 중단점이 코드에서 바인딩 해제 될 때 발생 합니다.|
|이벤트를 중지할 수 있음|사용자가 코드의 지정 된 지점에서 중지할지 여부를 확인 하기 위해 IDE에 전송 됩니다.|
|중단점 이벤트|코드 또는 데이터 중단점이 적중 될 때 발생 합니다.|
|문서 텍스트 이벤트|문서의 텍스트가 변경 될 때 발생 합니다. 이러한 이벤트는 메서드를 통해 전송 되지 않습니다 `IDebugEventCallBack2::Event` .|
|엔진 만들기 이벤트|엔진이 처음 생성 될 때 전송 됩니다.|
|진입점 이벤트|디버그할 프로그램에서 초기화 코드를 실행 하 고 첫 번째 사용자 진입점에 도달 하면 전송 됩니다.|
|예외 이벤트|실행 중인 프로그램에서 예외가 발생할 때 보냅니다.|
|식 계산 완료 이벤트|비동기 식 계산이 완료 되 면 전송 됩니다.|
|기호 이벤트 찾기|모듈에 대 한 기호를 찾기 위해 사용자에 게 요청 해야 할 때마다 전송 됩니다.|
|전체 이벤트 로드|초기 프로그램 로드가 완료 되 고 첫 번째 코드가 프로그램에서 실행 될 때만 전송 됩니다.|
|메시지 이벤트|메시지를 사용자에 게 보낼 때 전송 됩니다.|
|모듈 로드 이벤트|새 모듈을 로드 하거나 언로드할 때 전송 됩니다.|
|출력 문자열 이벤트|프로그램이 디버그 출력을 쓸 때 전송 됩니다.|
|이벤트 만들기 및 삭제|Visual Studio IDE에서 디버깅 중인 프로그램의 상태를 추적할 수 있도록 프로세스, 프로그램, 속성, 세션 및 스레드의 생성 또는 소멸을 알리기 위해 전송 됩니다.|
|단계 완료 이벤트|단계가 완료 될 때 전송 됩니다.|
|스레드 이름 변경 이벤트|사용자가 스레드 이름을 변경할 때 전송 됩니다.|
|프로그램 이름 변경 이벤트|사용자가 프로그램 이름을 변경할 때 전송 됩니다.|

## <a name="see-also"></a>추가 정보
- [이벤트 전송](../../extensibility/debugger/sending-events.md)
