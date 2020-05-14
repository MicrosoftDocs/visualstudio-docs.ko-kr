---
title: 성능 보고서 뷰 필터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a5642a8e153a4dfc7705d91d933397b6f8acb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778456"
---
# <a name="performance-report-view-filter"></a>성능 보고서 뷰 필터
**프로파일러 보고서 뷰 필터** 창은 **성능 보고서** 창 위쪽에 있습니다. 이 창이 표시되지 않으면 **필터 표시** 단추를 클릭합니다.

 각 필터 절을 수정하여 결과를 구체화할 수 있습니다. 필터 작성기에서 사용 가능한 열은 다음과 같습니다.

|필터 항목|Description|
|-----------------|-----------------|
|및/또는|이 절과 다음 절이 둘 다 true여야 결과와 일치하는 경우 **및**을 선택합니다. 이 절이나 다음 절 중 하나가 true이면 결과와 일치하는 경우 **또는**을 선택합니다.|
|필드|현재 보고서 파일에서 사용할 수 있는 데이터 필드의 목록에서 필터 절에 사용할 필드를 선택합니다.|
|연산자|필드와 값 간에 설정할 관계를 지정하는 연산자를 선택합니다.<br /><br /> =    같음<br /><br /> <>  같지 않음<br /><br /> <    보다 작음<br /><br /> >    보다 큼<br /><br /> <=  작거나 같음<br /><br /> >=  크거나 같음|
|값|찾을 값을 선택하거나 입력합니다. 필드에 대해 사용 가능한 값이 나열되는 필드도 있습니다.|

 필터가 최적의 결과를 제공할 때까지 필터 절을 추가할 수 있습니다. 데이터 파일에 필터를 적용하려면 **필터 실행**을 클릭합니다.

 **표시** 보고서 뷰에서는 필터 절을 생성하여 보고서 뷰의 데이터를 두 표시 간에 수집되는 데이터로 제한할 수 있습니다. 이렇게 하려면 보고서 데이터를 시작하고 종료할 표시를 선택한 다음 마우스 오른쪽 단추를 클릭하고 **표시에 대한 필터 추가** 또는 **타임스탬프에 대한 필터 추가**를 선택합니다. 두 필터는 모두 현재 데이터 파일의 데이터를 같은 범위로 제한합니다. **표시에 대한 필터 추가**는 다른 .vsp 파일에 적용할 수 있습니다.

 필터를 저장하려면 **성능 보고서** 도구 모음에서 **필터 내보내기**를 클릭하고 .*vspf* 파일의 위치와 파일 이름을 지정합니다. 이전에 저장한 필터를 로드하려면 **필터 가져오기**를 클릭하고 저장된 필터 파일을 찾습니다. 필터 파일을 사용하여 독립 실행형 프로파일링 도구가 설치되어 있는 컴퓨터에서 데이터 파일을 필터링할 수도 있습니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

## <a name="see-also"></a>참고 항목
- [성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)
- [VSPerfReport](../profiling/vsperfreport.md)
