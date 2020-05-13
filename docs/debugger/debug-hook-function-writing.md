---
title: 디버그 후크 함수 작성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563375"
---
# <a name="debug-hook-function-writing"></a>디버그 후크 함수 작성
이 단원에서는 디버거의 표준 처리 과정에서 미리 정의된 특정 지점에 코드를 삽입하기 위해 작성할 수 있는 여러 가지 사용자 지정 디버그 후크 함수에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
 [클라이언트 블록 후크 함수](../debugger/client-block-hook-functions.md) _CLIENT_BLOCK 블록에 저장 된 데이터의 내용을 보고 하거나 유효성을 검사 하는 함수를 작성 하기 위한 지침과 프로토타입을 제공 합니다.

 [할당 후크 함수](../debugger/allocation-hook-functions.md) 할당 후크 함수를 정의 다른 용도 탐색, 제한 사항 지적 및 프로토타입을 제공 합니다.

 [할당 후크 및 CRT 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) 내부 메모리를 할당하는 C 런타임 라이브러리 함수를 호출하는 경우 `_CRT_BLOCK` 블록을 명시적으로 무시하는 할당 후크 함수 제한에 대해 설명합니다. 또한 이 항목에서는 할당 후크가 `_CRT_BLOCK` 블록을 무시하지 않을 경우에 발생하는 결과(예제 포함) 및 기본 할당 후크 함수 **CrtDefaultAllocHook**를 변경하는 방법도 소개합니다.

 [보고서 후크 함수](../debugger/report-hook-functions.md) 특정 형식의 할당에 초점을 맞추기 위해 보고서를 필터링하는 데 사용할 수 있는 `_CrtSetReportHook`에 대해 설명합니다. 이 항목은 프로토타입도 제공합니다.

## <a name="related-sections"></a>관련 단원

- [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md) - CRT 디버그 라이브러리 사용, 보고서 매크로, `malloc`과 `_malloc_dbg`의 차이점, 디버그 후크 함수 작성 및 CRT 디버그 힙을 포함하여 C 런타임 라이브러리의 디버깅 기술에 대한 링크입니다.
