---
title: 스레드 뷰에서 스레드 검색 | Microsoft Docs
description: Visual Studio에서 디버그할 때 스레드 ID 또는 모듈 문자열을 검색 조건으로 사용하여 Spy++ 도구의 스레드 뷰에서 특정 스레드를 검색합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85d82897144a0ed366d95dfa590a09224a875f55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845063"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>방법: 스레드 뷰에서 스레드 검색
스레드 뷰에서 스레드 ID 또는 모듈 문자열을 검색 조건으로 사용하여 특정 스레드를 검색할 수 있습니다. 검색의 초기 방향을 지정할 수도 있습니다. 대화 상자의 필드에는 스레드 트리에서 선택한 스레드의 특성이 표시됩니다.

### <a name="to-search-for-a-thread-in-threads-view"></a>스레드 뷰에서 스레드를 검색하려면

1. Spy++와 활성 [스레드 뷰](../debugger/threads-view.md) 창이 보이도록 창을 정렬합니다.

2. **검색** 메뉴에서 **스레드 찾기** 를 선택합니다.

    [스레드 검색 대화 상자](../debugger/thread-search-dialog-box.md)가 열립니다.

3. 검색 조건으로 스레드 ID나 모듈 문자열을 입력합니다.

4. 값을 지정하지 않을 필드의 선택을 취소합니다.

   > [!TIP]
   > 모듈이 소유한 모든 스레드를 찾으려면 **스레드** 텍스트 상자의 선택을 취소하고 **모듈** 상자에 모듈 이름을 입력합니다. 그리고 **다음 찾기** 를 사용하여 계속해서 스레드를 검색합니다.

5. 검색의 초기 방향으로 **위로** 또는 **아래로** 를 선택합니다.

6. **확인** 을 클릭합니다.

   일치하는 스레드가 검색되면 스레드 뷰 창에 강조 표시됩니다.