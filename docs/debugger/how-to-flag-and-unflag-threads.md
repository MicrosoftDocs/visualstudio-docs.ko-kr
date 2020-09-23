---
title: 스레드 플래그 지정 및 플래그 해제 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- treads, switching [debugging]
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e381faac8a8e4ae6f45f1fde6e2e20dd9f127a97
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852063"
---
# <a name="how-to-flag-and-unflag-threads-c-visual-basic-c"></a>방법: 스레드 플래그 지정 및 플래그 해제(C#, Visual Basic, C++)

**스레드**, **병렬 스택**(스레드 뷰), **병렬 조사식** 및 **GPU 스레드** 창에서 아이콘으로 스레드를 표시하여 특별한 주의가 필요한 스레드에 플래그를 지정할 수 있습니다. 이 아이콘은 플래그 설정된 스레드를 다른 스레드와 구분하는 데 도움이 됩니다.

또한 플래그가 지정된 스레드는 **디버그 위치** 도구 모음의 **스레드** 목록이나 다른 다중 스레드 디버깅 창에서 별도로 처리됩니다. **스레드** 목록 또는 다른 창에 모든 스레드 또는 플래그가 지정된 스레드만 표시할 수 있습니다.

### <a name="to-flag-or-unflag-a-thread"></a>스레드에 플래그를 지정하거나 해제하려면

- **스레드** 또는 **병렬 조사식** 창에서 원하는 스레드를 찾고 플래그 아이콘을 클릭하여 플래그를 선택하거나 선택 취소합니다.
- **병렬 스택** 창에서 스레드 또는 스레드 그룹을 마우스 오른쪽 단추로 클릭하고 **Flag / \<thread>** 또는 **Unflag / \<thread>** 를 선택합니다.

### <a name="to-unflag-all-threads"></a>모든 스레드의 플래그를 해제하려면

- **스레드** 창에서 스레드를 마우스 오른쪽 단추로 클릭하고 **모든 스레드 플래그 해제**를 클릭합니다.
- **병렬 조사식** 창에서 플래그가 지정된 모든 스레드를 선택하고, 마우스 오른쪽 단추를 클릭한 다음, **플래그 해제**를 선택합니다.

### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면

- 다중 스레드 디버깅 창 중 하나에서 **플래그가 지정된 스레드만 표시** 버튼을 선택합니다.

### <a name="to-flag-just-my-code"></a>내 코드만 플래그를 설정하려면

1. **스레드** 창의 맨 위에 있는 도구 모음에서 플래그 아이콘을 클릭합니다.

2. 드롭다운 목록에서 **내 코드만 플래그 지정**을 클릭합니다.

### <a name="to-flag-threads-that-are-associated-with-selected-modules"></a>선택한 모듈과 연결된 스레드에 플래그를 설정하려면

1. **스레드** 창의 도구 모음에서 플래그 아이콘을 클릭합니다.

2. 드롭다운 목록에서 **사용자 지정 모듈 선택 영역 플래그 지정**을 클릭합니다.

3. **모듈 선택** 대화 상자에서 원하는 모듈을 선택합니다.

4. (선택 사항) **검색** 상자에서 특정 모듈을 검색할 문자열을 입력합니다.

5. **확인**을 클릭합니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [다중 스레드 애플리케이션 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)
- [연습: 스레드 창을 사용하여 다중 스레드 애플리케이션 디버그](../debugger/how-to-use-the-threads-window.md)