---
title: 채널(스레드 뷰) | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.channelnames
helpviewer_keywords:
- Concurrency Visualizer, Channels (Threads View)
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ac6e9e85a2d7dd504b2d2bd83bd1bbdb265ea0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62776779"
---
# <a name="channels-threads-view"></a>채널(스레드 뷰)
동시성 시각화 도우미는 스레드 채널, 디스크 채널, 표식 채널 및 GPU 채널의 4가지 채널을 보여줍니다.

## <a name="thread-channels"></a>스레드 채널
 스레드 채널은 하나의 스레드에 대해서만 스레드 상태를 색으로 보여 줍니다. 채널 이름에서 일시 중지하면 지정된 스레드의 시작 함수가 표시됩니다. 동시성 시각화 도우미는 여러 종류의 스레드를 검색합니다. 가장 일반적인 종류가 다음 표에 나와 있습니다.

|||
|-|-|
|주 스레드|응용 프로그램을 시작한 스레드입니다.|
|작업자 스레드|애플리케이션의 주 스레드에 의해 생성된 스레드입니다.|
|CLR 작업자 스레드|CLR(공용 언어 런타임)에 의해 생성된 작업자 스레드입니다.|
|디버거 도우미|Visual Studio 디버거에 의해 생성된 작업자 스레드입니다.|
|ConcRT 스레드|Microsoft 동시성 런타임에 의해 생성된 스레드입니다.|
|GDI 스레드|GDIPlus에 의해 생성된 스레드입니다.|
|OLE/RPC 스레드|RPC 작업자 스레드로 생성된 스레드입니다.|
|RPC 스레드|RPC 스레드로 생성된 스레드입니다.|
|Winsock 스레드|Winsock 스레드로 생성된 스레드입니다.|
|스레드 풀|CLR 스레드 풀에 의해 생성된 스레드입니다.|

## <a name="disk-channels"></a>디스크 채널
 디스크 채널은 컴퓨터에 있는 실제 드라이브에 해당합니다. 시스템의 각 실제 드라이브에 대해 읽기 및 쓰기 작업용 별도 채널이 존재하므로 각 드라이브에는 두 개의 채널이 있습니다. 디스크 번호는 커널 디바이스 이름에 해당합니다. 디스크 채널은 디스크 작업이 있을 때만 표시됩니다.

## <a name="marker-channels"></a>표식 채널
 표식 채널은 응용 프로그램에서 생성된 이벤트 및 여기에 사용되는 라이브러리에 해당합니다. 예를 들어 작업 병렬 라이브러리, 병렬 패턴 라이브러리 및 C++ AMP는 표식으로 나타나는 이벤트를 생성합니다. 각 표식 채널은 채널 설명 옆에 표시되는 스레드 ID와 연결됩니다. ID는 이벤트를 생성한 스레드를 식별합니다. 채널 설명에는 이벤트를 생성한 ETW(Windows용 이벤트 추적) 공급자의 이름이 포함됩니다. 채널에 [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)의 이벤트가 표시될 경우 계열 이름도 표시됩니다.

## <a name="gpu-channels"></a>GPU 채널
 GPU 채널에는 시스템의 DirectX 11 작업에 대한 정보가 표시됩니다.  그래픽 카드와 연결된 각 DirectX 엔진에는 개별 채널이 포함됩니다.  개별 세그먼트는 DMA 패킷 처리 시간을 나타냅니다.

## <a name="see-also"></a>참고 항목
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)