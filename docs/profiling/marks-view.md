---
title: 표시 뷰 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4d7483f309a3d7edb92d25c34e9665a6212c8038
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037519"
---
# <a name="marks-view"></a>표시 뷰
표시 뷰에는 애플리케이션에 삽입된 샘플링 및 ETW 이벤트가 표시됩니다.

 보고서에 미리 채워지는 기본 표시는 프로그램의 시작과 프로그램의 끝을 레이블로 지정합니다.

 자동으로 생성되는 표시의 Windows 카운터 데이터는 이 뷰에도 표시됩니다. 자세한 내용은 [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)을 참조하세요.

 두 표시 사이에 필터를 만들려면 표시를 선택하고 마우스 오른쪽 단추로 클릭한 다음 **표시에 대한 필터 추가** 또는 **타임스탬프에 대한 필터 추가**를 클릭합니다.

 다음 표에는 표시 뷰에서 사용할 수 있는 열에 대한 정의가 나와 있습니다.

 **Mark ID** 프로파일링 표시의 고유 식별자입니다.

 **Mark Name** 이벤트의 이름입니다.

 **Timestamp** 프로파일링 시작 시간부터 이벤트가 기록되는 시간까지입니다.

 Windows 성능 카운터 데이터 - Windows 성능 카운터 데이터가 수집되면 카운터 이름이 있는 열에 값이 표시됩니다.

## <a name="see-also"></a>참고 항목
- [성능 보고서 개요](../profiling/performance-report-overview.md)
- [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; 데이터 수집 제어 창](/previous-versions/bb385767(v=vs.110))