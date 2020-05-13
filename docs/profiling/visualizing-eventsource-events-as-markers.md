---
title: EventSource 이벤트를 표식으로 시각화 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6339b3f55b4a4c9a1e2c90ff3183a36f16c178
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "64811539"
---
# <a name="visualize-eventsource-events-as-markers"></a>EventSource 이벤트를 표식으로 시각화
Concurrency 시각화는 EventSource 이벤트를 표식으로 표시할 수 있으며, 표식이 표시되는 방식을 제어할 수 있습니다. EventSource 표식을 보려면 [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자를 사용하여 ETW 공급자 GUID를 등록합니다. Concurrency 시각화에는 EventSource 이벤트를 [플래그 표식](../profiling/flag-markers.md), [범위 표식](../profiling/span-markers.md) 및 [메시지 표식](../profiling/message-markers.md)으로 나타내기 위한 기본 규칙이 있습니다. 이벤트에 사용자 지정 필드를 추가하여 EventSource 이벤트가 표시되는 방식을 사용자 지정할 수 있습니다. 표식에 대한 자세한 내용은 [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)을 참조하세요. EventSource 이벤트에 대한 자세한 내용은 <xref:System.Diagnostics.Tracing>를 참조하세요.

## <a name="default-visualization-of-eventsource-events"></a>EventSource 이벤트의 기본 시각화
 기본적으로 Concurrency 시각화는 다음 규칙을 사용해 EventSource 이벤트를 나타냅니다.

### <a name="marker-type"></a>표식 유형

1. [Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start 또는 win:Stop이 포함된 이벤트는 각각 범위의 시작이나 끝으로 처리됩니다.  중첩되거나 겹치는 범위는 표시할 수 없습니다. 시작되는 스레드와 끝나는 스레드가 다른 이벤트 쌍은 표시할 수 없습니다.

2. Opcode가 win:Start도 아니고 win:Stop도 아닌 이벤트는 해당 [Level](/windows/desktop/WES/defining-severity-levels)(EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR의 필드)이 win:Verbose 이상인 경우가 아니면 표식 플래그로 처리됩니다.

3. 그 외의 모든 경우 이벤트는 메시지로 처리됩니다.

### <a name="importance"></a>중요도
 다음 표에는 이벤트 수준과 표식 중요도 간의 매핑 방식이 정의되어 있습니다.

|ETW 수준|Concurrency 시각화의 중요도|
|---------------|---------------------------------------|
|win:LogAlways|정상|
|win:Critical|위험|
|win:Error|위험|
|win:Warning|높음|
|win:Informational|정상|
|win:Verbose|낮음|
|win:verbose보다 높은 수준|낮음|

### <a name="series-name"></a>계열 이름
 이벤트의 작업 이름이 계열 이름에 사용됩니다. 이벤트에 대해 작업이 정의되지 않은 경우 계열 이름은 비어 있습니다.

### <a name="category"></a>Category
 Level이 win:Critical 또는 win:Error이면 범주는 Alert(-1)입니다. 그렇지 않으면 범주는 기본값(0)입니다.

### <a name="text"></a>텍스트
 이벤트에 대해 printf-type 형식의 텍스트 메시지가 정의된 경우 표식의 설명으로 해당 메시지가 표시됩니다. 그렇지 않으면 이벤트의 이름 및 각 페이로드 필드의 값이 설명으로 사용됩니다.

## <a name="customize-visualization-of-eventsource-events"></a>EventSource 이벤트의 시각화 사용자 지정
 다음 섹션의 설명에 따라 이벤트에 적절한 필드를 추가하여 EventSource 이벤트가 표시되는 방식을 사용자 지정할 수 있습니다.

### <a name="marker-type"></a>표식 유형
 `cvType` 필드(바이트)를 사용하여 이벤트를 나타내는 데 사용되는 표식의 종류를 제어합니다. cvType에 사용할 수 있는 값은 다음과 같습니다.

|cvType 값|결과 표식 유형|
|------------------|---------------------------|
|0|메시지|
|1|범위 시작|
|2|범위 끝|
|3|플래그|
|기타 모든 값|메시지|

### <a name="importance"></a>중요도
 `cvImportance` 필드(바이트)를 사용하여 EventSource 이벤트에 대한 중요도 설정을 제어할 수 있습니다. 그러나 이벤트의 Level을 사용하여 표시되는 이벤트 중요도를 제어하는 것이 좋습니다.

|cvImportance 값|Concurrency 시각화의 중요도|
|------------------------|---------------------------------------|
|0|정상|
|1|위험|
|2|높음|
|3|높음|
|4|정상|
|5|낮음|
|기타 모든 값|낮음|

### <a name="series-name"></a>계열 이름
 `cvSeries` 이벤트 필드(문자열)를 사용하여 Concurrency 시각화가 EventSource 이벤트에 제공하는 계열 이름을 제어합니다.

### <a name="category"></a>Category
 `cvCategory` 필드(바이트)를 사용하여 Concurrency 시각화가 EventSource 이벤트에 제공하는 범주를 제어합니다.

### <a name="text"></a>텍스트
 `cvTextW` 필드(문자열)를 사용하여 Concurrency 시각화가 EventSource 이벤트에 제공하는 설명을 제어합니다.

### <a name="spanid"></a>SpanID
 cvSpanId 필드(정수)를 사용하여 이벤트 쌍 일치를 확인합니다. 범위를 나타내는 각 시작/중지 이벤트 쌍의 값은 고유해야 합니다. 일반적으로 동시 코드의 경우 고유한 값을 지정하려면 <xref:System.Threading.Interlocked.Exchange%2A>와 같은 동기화 기본 형식을 사용하여 키(CvSpanID에 사용되는 값)가 정확한지 확인해야 합니다.

> [!NOTE]
> SpanID를 사용하여 범위를 중첩하거나, 같은 스레드에서 해당 범위를 일부분 겹치거나, 시작되는 스레드와 끝나는 스레드를 서로 다르게 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목
- [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)