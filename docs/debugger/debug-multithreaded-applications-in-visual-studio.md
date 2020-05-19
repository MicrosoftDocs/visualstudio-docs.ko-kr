---
title: 다중 스레드 애플리케이션 디버그 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431812"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Visual Studio에서 다중 스레드 애플리케이션 디버그
스레드는 운영 체제에서 프로세서 시간을 부여받는 명령 시퀀스입니다. 운영 체제에서 실행되는 모든 프로세스는 최소한 하나의 스레드로 구성됩니다. 프로세스에 스레드가 둘 이상인 경우를 다중 스레드라고 합니다.

다중 프로세서, 다중 코어 프로세서 또는 하이퍼스레딩 프로세스를 갖춘 컴퓨터는 몇 개의 동시 스레드를 실행할 수 있습니다. 많은 스레드를 사용하는 병렬 처리는 프로그램 성능을 크게 향상할 수 있지만 많은 스레드를 추적하기 때문에 디버깅을 더 어렵게 만들 수도 있습니다.

다중 스레딩을 통해 새로운 유형의 잠재적 버그가 도입될 수 있습니다. 예를 들어 둘 이상의 스레드에서 동일한 리소스에 액세스해야 하지만 한 번에 스레드 하나만 안전하게 리소스에 액세스할 수 있습니다. 한 번에 한 스레드만 리소스에 액세스할 수 있게 하려면 특정한 형태의 상호 배제가 필요합니다. 상호 배제가 잘못 구현되면 어떠한 스레드도 실행되지 않는 ‘교착 상태’ 조건이 발생할 수 있습니다. 교착 상태는 종종 디버그하기 어려운 문제입니다.

## <a name="tools-for-debugging-multithreaded-apps"></a>다중 스레드 앱을 디버깅 도구

Visual Studio는 다중 스레드 앱을 디버그하는 데 사용할 다양한 도구를 제공합니다.

- 스레드의 경우 스레드 디버깅을 위한 기본 도구는 **스레드** 창, 소스 창의 스레드 마커, **병렬 스택** 창, **병렬 조사식** 창, **디버그 위치** 도구 모음입니다. **스레드** 창과 **디버그 위치** 도구 모음에 대한 자세한 내용은 다음을 참조하세요. [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md). **병렬 스택** 및 **병렬 조사식** 창을 사용하는 방법을 알아보려면 [다중 스레드 애플리케이션 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)을 참조하세요. 두 항목 모두 스레드 마커를 사용하는 방법을 보여 줍니다.

- [TPL(작업 병렬 라이브러리)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)이나 [동시성 런타임](/cpp/parallel/concrt/concurrency-runtime/)을 사용하는 코드의 경우 디버깅용 기본 도구는 **병렬 스택** 창, **병렬 조사식** 창, **작업** 창이며 이러한 도구는 JavaScript도 지원합니다. 시작하려면 [연습: 병렬 애플리케이션 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md) 및 [연습: C++ AMP 애플리케이션 디버깅](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)을 참조하세요.

- GPU에서 스레드를 디버그하는 경우 기본 도구는 **GPU 스레드** 창입니다. [방법: GPU 스레드 창 사용](../debugger/how-to-use-the-gpu-threads-window.md)을 참조하세요.

- 프로세스의 경우 기본 도구는 **프로세스에 연결** 대화 상자, **프로세스** 창, **디버그 위치** 도구 모음입니다.

Visual Studio에서 제공하는 강력한 중단점 및 추적점은 다중 스레드 애플리케이션을 디버그할 때 유용할 수 있습니다. 중단점 조건 및 필터를 사용하여 개별 스레드에 중단점을 배치합니다. 추적점을 통해 프로그램 실행을 중단 없이 추적하여 교착 상태와 같은 문제를 검토할 수 있습니다. 자세한 내용은 [중단점 작업 및 추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)을 참조하세요.

사용자 인터페이스가 있는 다중 스레드 애플리케이션은 특히 디버깅하기 어려울 수 있습니다. 애플리케이션을 다른 컴퓨터에서 실행하면서 원격 디버깅을 사용하는 것이 좋습니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

## <a name="articles-about-debugging-multithreaded-apps"></a>다중 스레드 앱 디버깅에 대한 문서

 [다중 스레드 애플리케이션 디버깅 시작](../debugger/get-started-debugging-multithreaded-apps.md)

**병렬 스택** 창과 **병렬 조사식** 창의 기능을 집중적으로 보여 주는 스레드 디버깅 기능 둘러보기입니다.

 [스레드 및 프로세스 디버깅 도구](../debugger/debug-threads-and-processes.md)

스레드 및 프로세스 디버깅 도구의 기능을 나열합니다.

 [여러 프로세스 디버그](../debugger/debug-multiple-processes.md)

여러 프로세스 디버깅 방법에 대해 설명합니다.

 [연습: 스레드 창을 사용하여 디버그](../debugger/how-to-use-the-threads-window.md).

**스레드** 창과 **디버그 위치**  도구 모음을 사용하는 방법을 보여 주는 연습입니다.

 [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)

**병렬 스택**  및 **작업** 창을 사용하는 방법을 보여 주는 연습입니다.

 [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)

디버깅 컨텍스트를 다른 스레드로 전환하는 몇 가지 방법입니다.

 [방법: 스레드에 플래그 지정 및 스레드의 플래그 해제](../debugger/how-to-flag-and-unflag-threads.md)

디버깅 도중 특별히 주의하려는 스레드를 표시하거나 플래그를 지정합니다.

 [방법: 고성능 클러스터에서 디버그](../debugger/how-to-debug-on-a-high-performance-cluster.md)

고성능 클러스터에서 실행되는 애플리케이션을 디버깅하는 방법을 보여 줍니다.

 [네이티브 코드의 스레드 디버깅 팁](../debugger/tips-for-debugging-threads-in-native-code.md)

네이티브 스레드를 디버깅하는 단순하지만 유용한 방법을 보여 줍니다.

 [방법: 네이티브 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-native-code.md)

**스레드** 창에 표시되는 스레드에 이름을 지정합니다.

 [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md)

**스레드** 창에 표시되는 스레드에 이름을 지정합니다.

## <a name="see-also"></a>참조

- [중단점 사용](../debugger/using-breakpoints.md)
- [스레딩](/dotnet/standard/threading/index)
- [구성 요소에서 다중 스레딩](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [이전 코드를 위한 다중 스레딩 지원](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [스레드 및 프로세스 디버그](../debugger/debug-threads-and-processes.md)
- [원격 디버깅](../debugger/remote-debugging.md)