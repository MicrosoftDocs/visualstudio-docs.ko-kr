---
title: 방법 - 고성능 클러스터에서 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 905a196b0872ac0d8665293200837861adf49795
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350071"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>방법: 고성능 클러스터에서 디버그(C#, Visual Basic, C++)

고성능 클러스터에서 다중 처리 프로그램을 디버깅하는 방법은 원격 컴퓨터에서 일반적인 프로그램을 디버깅하는 방법과 비슷합니다. 그러나 여기에는 몇 가지 추가로 고려해야 할 사항이 있습니다. 일반적인 원격 설치 요구 사항은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

 고성능 클러스터에서 디버깅하는 경우 원격 디버깅에 제공되는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 디버깅 창과 기술을 모두 사용할 수 있습니다. 그러나 디버깅을 원격으로 수행하므로 외부 콘솔 창은 사용할 수 없습니다.

 **스레드** 창과 **프로세스** 창은 병렬 애플리케이션을 디버깅하는 데 특히 유용합니다. 해당 창을 사용하는 방법에 관한 팁은 [방법: 프로세스 창 사용](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) 및 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md)를 참조하세요.

 다음 절차에서는 고성능 클러스터에서 디버깅을 수행할 때 특히 유용한 몇 가지 방법을 보여 줍니다.

 병렬 애플리케이션을 디버깅할 때는 특정 스레드, 프로세스 또는 컴퓨터에 중단점을 설정해야 하는 경우가 있습니다. 일반적인 중단점을 만든 다음 중단점 필터를 추가하면 이를 쉽게 수행할 수 있습니다.

### <a name="to-open-the-breakpoint-filter-dialog-box"></a>중단점 필터 대화 상자를 열려면

1. 소스 창, **디스어셈블리** 창, **호출 스택** 창 또는 **중단점** 창에서 중단점 문자 모양을 마우스 오른쪽 단추로 클릭합니다.

2. 바로 가기 메뉴에서 **필터**를 클릭합니다. 이 옵션은 맨 위 또는 **중단점** 아래의 하위 메뉴에 표시됩니다.

### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>특정 프로세스에 중단점을 설정하려면

1. **프로세스** 창에서 컴퓨터 이름을 가져옵니다.

2. 중단점을 선택하고 위 절차에서 설명한 것처럼 **중단점 필터** 대화 상자를 엽니다.

3. **중단점 필터** 대화 상자에 다음을 입력합니다.

     MachineName =*yourmachinename*

     좀 더 복잡한 필터를 만들려면 `&`(AND 연산자), `||`(OR 연산자), `!`(NOT 연산자) 및 괄호를 사용하여 절을 조합합니다.

4. **확인**을 클릭합니다.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>특정 프로세스에 중단점을 설정하려면

1. **프로세스** 창에서 프로세스 이름이나 프로세스 ID 번호를 가져옵니다.

2. 중단점을 선택하고 첫 번째 절차에서 설명한 것처럼 **중단점 필터** 대화 상자를 엽니다.

3. **중단점 필터** 대화 상자에 다음을 입력합니다.

     `ProcessName =`  *yourprocessname*

     또는

     `ProcessID =` *yourprocessIDnumber*

     좀 더 복잡한 필터를 만들려면 `&`(AND 연산자), `||`(OR 연산자), `!`(NOT 연산자) 및 괄호를 사용하여 절을 조합합니다.

4. **확인**을 클릭합니다.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>특정 스레드에 중단점을 설정하려면

1. **스레드** 창에서 스레드 이름이나 스레드 ID 번호를 가져옵니다.

2. 중단점을 선택하고 첫 번째 절차에서 설명한 것처럼 **중단점 필터** 대화 상자를 엽니다.

3. **중단점 필터** 대화 상자에 다음을 입력합니다.

     `ThreadName =` *yourthreadname*

     또는

     `ThreadID =` *yourthreadIDnumber*

     좀 더 복잡한 필터를 만들려면 `&`(AND 연산자), `||`(OR 연산자), `!`(NOT 연산자) 및 괄호를 사용하여 절을 조합합니다.

4. **확인**을 클릭합니다.

## <a name="example"></a>예제
 다음 예제에서는 `marvin`이라는 컴퓨터와 `fourier1`이라는 스레드에 중단점 필터를 만드는 방법을 보여 줍니다.

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Remote Debugging](../debugger/remote-debugging.md)
- [방법: 프로세스 창 사용](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [다중 스레드 앱 디버그 시작](../debugger/get-started-debugging-multithreaded-apps.md)
- [스레드 및 프로세스](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [중단점 사용](../debugger/using-breakpoints.md)