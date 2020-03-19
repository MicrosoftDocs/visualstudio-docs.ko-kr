---
title: '방법: 수집 방법 선택 | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3c633e12b2e0bf157ffd94ef06a5898fdc3ec830
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776347"
---
# <a name="how-to-choose-collection-methods"></a>방법: 수집 방법 선택

Visual Studio 프로파일링 도구는 성능 데이터를 수집하는 세 가지 방법, 샘플링, 계측 및 동시성을 지원합니다. 샘플링 또는 계측 방법을 사용하여 .NET 메모리 할당 및 수명 데이터를 수집할 수도 있습니다.

성능 세션 **Method** 속성을 사용하여 애플리케이션에 가장 적절한 수집 방법을 지정할 수 있습니다. 성능 마법사, 성능 탐색기 또는 성능 세션의 속성 페이지에서 수집 방법을 설정할 수 있습니다. 명령줄 도구를 사용할 경우 자세한 내용은 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)을 참조하세요.

## <a name="performance-wizard"></a>성능 마법사

### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>성능 마법사를 사용하여 수집 방법을 선택하려면

- 마법사의 첫 번째 페이지에서 다음 옵션 중 하나를 선택합니다.

| 옵션 | Description |
|----------------------------| - |
| **CPU 샘플링** | 초기 분석 및 CPU 사용률 문제 분석에 유용한 애플리케이션 통계를 수집합니다. |
| **계측** | 집중 분석 및 입/출력 성능 문제 분석에 유용한 자세한 타이밍 데이터를 수집합니다. |
| **.NET 메모리 할당** | 샘플링 프로파일링 방법을 사용하여 .NET Framework 메모리 할당 데이터를 수집합니다. |
| **동시성** | 숫자 리소스 경합 데이터를 수집합니다. |

## <a name="performance-explorer"></a>성능 탐색기

### <a name="to-select-a-collection-method-using-performance-explorer"></a>성능 탐색기를 사용하여 수집 방법을 선택하려면

1. **성능 탐색기** 도구 모음에서 **방법** 드롭다운 목록 옆에 있는 화살표를 클릭합니다.

2. 원하는 수집 방법을 클릭합니다.

## <a name="performance-session-property-pages"></a>성능 세션 속성 페이지

### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>성능 세션 속성을 사용하여 샘플링 또는 계측 방법을 선택하려면

1. **성능 탐색기**에서 성능 세션을 선택합니다.

     성능 세션 파일 이름의 확장명은 .*psess*입니다.

2. 성능 세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

3. **속성 페이지**에서 **일반**을 클릭합니다.

4. 원하는 수집 방법을 클릭합니다.

    - 샘플링 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [샘플링을 사용하여 성능 통계 수집](../profiling/collecting-performance-statistics-by-using-sampling.md)을 참조하세요.

    - 샘플링 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [계측을 사용하여 자세한 타이밍 데이터 수집](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)을 참조하세요.

### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>성능 세션 속성을 사용하여 .NET 메모리 데이터 수집을 선택하려면

1. **성능 탐색기**에서 성능 세션을 선택합니다.

     성능 세션 파일 이름의 확장명은 .psess입니다.

2. 성능 세션을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

3. **속성 페이지**에서 **일반**을 클릭합니다.

4. **샘플링** 또는 **계측**을 클릭합니다.

5. **.NET 개체 할당 정보 수집**을 클릭하여 .NET Framework 개체 할당의 크기와 개수를 수집합니다.

6. (선택 사항) **추가적으로 .NET 개체 수명 정보 수집**을 클릭하여 개체 메모리가 회수된 가비지 수집 생성에 대한 데이터를 수집합니다.

     .NET 메모리 데이터를 수집할 때 사용할 수 있는 다른 옵션에 대한 자세한 내용은 [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)을 참조하세요.

### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>성능 세션 속성을 사용하여 동시성 데이터 수집을 선택하려면

1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

2. **속성 페이지**에서 **일반**을 클릭합니다.

3. **동시성**을 클릭합니다.

## <a name="see-also"></a>참고 항목

[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)
[성능 세션 속성](../profiling/performance-session-properties.md)
