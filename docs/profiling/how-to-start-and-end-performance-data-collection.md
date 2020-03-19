---
title: '방법: 성능 데이터 수집 시작 및 종료 | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da75306018cf19855c7cb7f74ac3ffc4e84bcd9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774513"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>방법: 성능 데이터 수집 시작 및 종료
프로파일링을 시작하기 전에 프로파일링할 대상 이진 파일을 성능 세션에 추가해야 합니다. 대상을 추가하려면 **성능 탐색기**에서 **대상**을 마우스 오른쪽 단추로 클릭하고 **대상 이진 파일 추가**를 클릭합니다. **대상 이진 파일 추가** 대화 상자에서 파일 이름을 선택하고 **열기**를 클릭합니다. 새 이진 파일이 추가됩니다.

### <a name="to-start-profiling"></a>프로파일링을 시작하려면

1. **성능 탐색기** 창에서 성능 세션의 이름을 마우스 오른쪽 단추로 클릭하고 다음 옵션 중 하나를 선택합니다.

    - **프로파일링 시작** - 애플리케이션을 시작하고 즉시 프로파일링을 시작합니다.

    - **일시 중지된 프로파일링 시작** - 애플리케이션을 시작하지만 프로파일링을 시작하지 않습니다. **데이터 수집 제어** 창에서 **수집 다시 시작**을 선택하여 프로파일링을 시작할 수 있습니다. 자세한 내용은 [방법: 성능 데이터 수집 일시 중지 및 다시 시작](../profiling/how-to-pause-and-resume-performance-data-collection.md)을 참조하세요.

### <a name="to-end-profiling"></a>프로파일링을 종료하려면

- 프로파일링 세션을 종료하는 기본 설정 방법은 애플리케이션을 종료하는 것입니다. 프로파일링을 즉시 중지하려면**성능 탐색기** 도구 모음에서 **중지**를 클릭합니다.

## <a name="see-also"></a>참고 항목
- [데이터 수집 제어](../profiling/controlling-data-collection.md)
- [방법: 성능 데이터 수집 일시 중지 및 다시 시작](../profiling/how-to-pause-and-resume-performance-data-collection.md)
