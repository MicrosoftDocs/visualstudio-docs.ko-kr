---
title: 이벤트 뷰어 | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4cba043d8300d47ae5ffba1c175a19fcfa2e65ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330337"
---
# <a name="events-viewer"></a>이벤트 뷰어

일반 이벤트 뷰어는 모듈 로드, 스레드 시작, 시스템 구성과 같은 이벤트 목록을 통해 앱 활동을 표시합니다. 이 뷰를 사용하면 Visual Studio 프로파일러 내에서 앱 작동을 더 잘 진단할 수 있습니다.

## <a name="setup"></a>설정

1. Visual Studio에서 **Alt+F2** 키를 눌러 성능 프로파일러를 엽니다.

1. **이벤트 뷰어** 확인란을 선택합니다.

   ![이벤트 뷰어 확인란 선택됨](../profiling/media/eventsviewerselected.png "이벤트 뷰어 확인란 선택됨")

1. **시작** 단추를 선택하여 도구를 실행합니다.

1. 도구가 시작되면 앱에서 프로파일링할 시나리오를 진행합니다. 그런 다음 **수집 중지**를 선택하거나 앱을 닫아 데이터를 확인합니다.

   ![수집 중지를 표시하는 창](../profiling/media/stopcollectioneventsviewer.png "수집 중지를 표시하는 창")

도구를 보다 효율적으로 만드는 방법에 대한 자세한 내용은 [프로파일링 설정 최적화](../profiling/optimize-profiler-settings.md)를 참조하세요.

## <a name="understand-your-data"></a>데이터 이해

![이벤트 뷰어 추적](../profiling/media/eventviewertrace.png "이벤트 뷰어 추적")

|열 이름|설명|
|----------|---------------------|
|공급자 이름|이벤트 소스입니다.|
|이벤트 이름|해당 공급자가 지정한 이벤트입니다.|
|텍스트|이벤트의 공급자, 이벤트 이름 및 ID에 대한 설명입니다.|
|타임스탬프(ms)|이벤트가 발생한 시간입니다.|
|공급자 GUID|이벤트 공급자의 ID입니다.|
|이벤트 ID|이벤트의 ID입니다.|
|프로세스 ID|이벤트가 발생한 프로세스입니다(알려진 경우).|
|프로세스 이름|실행 중인 프로세스의 이름입니다.|
|스레드 ID|이벤트가 발생한 스레드의 ID입니다(알려진 경우).|

열이 기본적으로 누락된 경우 기존 열 머리글 중 하나를 마우스 오른쪽 단추로 클릭하고 추가하려는 열을 선택합니다.

![이벤트 뷰어에 열 추가](../profiling/media/eventvieweraddcolumns.png "이벤트 뷰어에 열 추가")

이벤트를 선택하면 **추가 속성** 창이 표시됩니다. **공용 속성**은 이벤트에 대해 표시되는 속성 목록을 표시합니다. **페이로드 속성**은 이벤트와 관련된 속성을 표시합니다. 일부 이벤트의 경우 **스택**을 볼 수도 있습니다.

![스택을 보여 주는 이벤트 뷰어](../profiling/media/eventviewerstacks.png "스택을 보여 주는 이벤트 뷰어")

## <a name="organize-your-data"></a>데이터 구성

**텍스트** 열을 제외한 모든 열을 정렬할 수 있습니다.

![이벤트 뷰어 추적](../profiling/media/eventviewertrace.png "이벤트 뷰어 추적")

이벤트 뷰어는 한 번에 최대 2만 개의 이벤트를 표시합니다. 관심 이벤트에 초점을 맞추기 위해 이벤트 필터를 선택하여 이벤트 표시를 필터링할 수 있습니다. 각 공급자에 대해 발생한 총 이벤트 대비 백분율을 확인할 수도 있습니다. 단일 이벤트 필터를 마우스로 가리키면 다음을 보여 주는 도구 설명이 표시됩니다.

- 이벤트 이름
- 공급자
- GUID
- 총 이벤트에 대한 백분율
- 이벤트 수

![이벤트 뷰어 이벤트 필터](../profiling/media/eventviewereventfilter.png "이벤트 뷰어 이벤트 필터")

공급자 필터에는 각 공급자에 대해 발생한 총 이벤트 대비 백분율이 표시됩니다. 공급자 이름, 총 이벤트 대비 백분율 및 이벤트 수가 포함된 유사한 도구 설명을 보려면 단일 공급자를 마우스로 가리킵니다.

![이벤트 뷰어 공급자 필터](../profiling/media/eventviewerproviderfilter.png "이벤트 뷰어 공급자 필터")
