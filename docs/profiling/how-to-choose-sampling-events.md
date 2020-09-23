---
title: 샘플링 이벤트 선택 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f28859b1c17c735be405c6c56ebabcbe43903170
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851296"
---
# <a name="how-to-choose-sampling-events"></a>방법: 샘플링 이벤트 선택
기본적으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구는 프로파일링된 프로세스에 사용되는 프로세서 주기 수로 지정된 간격으로 성능 데이터를 수집합니다. 간격의 기본 주기 수는 10,000,000이며, 1GH 컴퓨터에서 약 0.01초가 걸립니다. 간격의 주기 수를 변경하고 샘플 이벤트를 변경할 수 있습니다. 다음 샘플 이벤트를 사용할 수 있습니다.

- 클록 주기 - CPU 바인딩 문제

- 페이지 폴트 - 메모리 관련 문제

- 시스템 호출 - I/O 관련 문제

- 성능 카운터 - 낮은 수준의 성능 문제에 대한 CPU 카운터

> [!IMPORTANT]
> 샘플링 방법을 사용하여 .NET 메모리 데이터(할당, 개체 수명 또는 둘 다)를 수집하는 경우 모든 사용자 지정 샘플링 이벤트가 무시되며 적절한 메모리 할당, 가비지 수집 이벤트 또는 두 방법이 모두 데이터를 수집하는 데 사용됩니다.

### <a name="to-select-a-sample-event"></a>샘플 이벤트를 선택하려면

1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

2. **속성 페이지**에서 **샘플링** 속성을 클릭합니다.

3. **샘플 이벤트** 드롭다운 목록에서 애플리케이션 프로파일링에 사용할 샘플 이벤트를 선택합니다.

    > [!NOTE]
    > **사용 가능한 성능 카운터**는 **샘플 이벤트** 드롭다운 목록에서 **성능 카운터**를 선택한 경우에만 사용하도록 설정됩니다.

4. **성능 카운터**를 선택하면 **사용 가능한 성능 카운터** 트리 뷰 컨트롤에서 특정 CPU 카운터를 선택합니다.

    - **Portable Events** 노드의 카운터는 모든 형식의 프로세스에서 사용할 수 있습니다.

    - **Platform Events** 노드의 카운터는 현재 컴퓨터의 프로세서에 특정하고 다른 형식의 프로세서에서는 사용할 수 없습니다.

5. 샘플 이벤트를 선택하면 기본 샘플링 간격 값이 **샘플링 간격** 텍스트 상자에 표시됩니다. 필요한 경우 텍스트 상자에 원하는 값을 입력할 수 있습니다.

## <a name="see-also"></a>참조
- [성능 세션 구성](../profiling/configuring-performance-sessions.md)
- [방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)
- [CPU 및 Windows 카운터](../profiling/cpu-and-windows-counters.md)
- [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)
- [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)
