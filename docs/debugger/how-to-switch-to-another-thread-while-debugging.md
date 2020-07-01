---
title: 디버그 중 다른 스레드로 전환
ms.custom: seodec18
ms.date: 04/27/2017
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9306e68c7d8906c6956eb5e3810327898bc56567
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348914"
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio-c-visual-basic-c"></a>방법: Visual Studio에서 디버그 중 다른 스레드로 전환(C#, Visual Basic, C++)
다중 스레드 애플리케이션을 디버그하는 경우 작업 중인 스레드에서 다른 스레드로 전환하는 여러 가지 방법 중 하나를 사용할 수 있습니다.

> [!NOTE]
> 스레드가 실행되는 순서를 제어하려면 [스레드를 동결 및 재개](../debugger/get-started-debugging-multithreaded-apps.md)해야 합니다.

코드 편집기 및 다른 다중 스레드 디버깅 창에서 스레드를 검사하는 경우 노란색 화살표는 현재 스레드를 나타냅니다. 끝이 굽은 녹색 화살표는 현재 스레드가 아닌 스레드에 현재 디버거 컨텍스트가 있음을 나타냅니다.

### <a name="to-switch-to-any-thread-that-appears"></a>나타나는 스레드로 전환하려면

- **스레드** 또는 **병렬 조사식** 창에서 스레드를 두 번 클릭합니다.

### <a name="to-switch-to-a-thread-in-a-source-window"></a>소스 창에서 스레드를 전환하려면

- 왼쪽 여백에서 스레드 마커 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")를 마우스 단추로 클릭하고, **전환**을 가리킨 다음, 전환할 스레드의 이름을 클릭합니다. 특정 위치의 스레드만 바로 가기 메뉴에 표시됩니다.

     스레드 마커가 나타나지 않으면 **스레드** 창을 마우스 오른쪽 단추로 클릭하고 **소스의 스레드 표시**가 선택되어 있는지 확인합니다.

### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>디버그 위치 도구 모음에서 스레드로 전환하려면

1. **디버그 위치** 도구 모음에서 **스레드** 목록을 클릭합니다.

2. 목록에서 전환할 스레드를 클릭합니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
