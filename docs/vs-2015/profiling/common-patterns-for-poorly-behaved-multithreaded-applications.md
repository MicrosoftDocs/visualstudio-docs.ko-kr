---
title: 잘못 동작하는 다중 스레드 애플리케이션의 일반 패턴 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
ms.assetid: 00d10629-e20f-4d6d-8643-c59a3879812e
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 128de95d347fece01c9177057346b00e412e1e6f
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586634"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>잘못 동작하는 다중 스레드 애플리케이션의 일반 패턴
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미를 사용하면 개발자는 다중 스레드 애플리케이션의 동작을 시각화할 수 있습니다. 이 도구에는 잘못 동작하는 다중 스레드 애플리케이션에 대한 일반적인 패턴의 갤러리가 포함되어 있습니다. 갤러리에는 각 패턴으로 표시되는 동작에 대한 설명, 해당 동작의 가능한 결과 및 그 동작을 해결하는 가장 일반적인 방법과 함께 도구를 통해 노출되는 일반적이고 인식 가능한 시각적 패턴이 포함되어 있습니다.  
  
## <a name="lock-contention-and-serialized-execution"></a>잠금 경합 및 직렬화된 실행  
 ![잠금 경합으로 인해 발생하는 serialize된 실행](../profiling/media/lockcontention-serialized.png "LockContention_Serialized")  
  
 스레드가 여러 개 있고 컴퓨터에 논리 코어 수가 충분한 경우에도 때로 병렬화된 애플리케이션이 직렬로 계속 실행할 수 있습니다. 첫 번째 증상은 다중 스레드의 성능 저하로, 직렬 구현보다 약간 더 느릴 수도 있습니다. 스레드 뷰에서 병렬로 실행 중인 여러 스레드는 볼 수 없지만 대신, 하나의 스레드만 실행되는 것은 언제든지 볼 수 있습니다. 여기서 스레드의 동기화 세그먼트를 클릭하면 차단된 스레드(차단 호출 스택) 및 차단 조건을 제거하는 스레드(차단 해제 호출 스택)에 대한 호출 스택을 볼 수 있습니다. 또한 분석 중인 프로세스에서 호출 스택 차단 해제가 발생하는 경우 스레드 준비 커넥터가 표시됩니다. 여기서, 차단 및 차단 해제 호출 스택으로부터 코드로 이동하여 더 많은 serialization의 원인을 조사할 수 있습니다.  
  
 다음 그림과 같이 동시성 시각화 도우미가 CPU 사용률 뷰에 이 증상을 표시할 수 있습니다. 여기서 다중 스레드가 있더라도 애플리케이션은 하나의 논리 코어만 사용합니다.  
  
 자세한 내용은 MSDN 블로그 웹 사이트에 있는 Hazim Shafi의 [Parallel Performance Tools For Windows](https://docs.microsoft.com/archive/blogs/hshafi/)(Windows용 병렬 성능 도구) 블로그에서 "Performance Pattern 1: Identifying Lock Contention"(성능 패턴 1: 잠금 경합 식별)을 참조하세요.  
  
 ![잠금 경합](../profiling/media/lockcontention-2.png "LockContention_2")  
  
## <a name="uneven-workload-distribution"></a>균등하지 않은 작업 부하 분산  
 ![균등하지 않은 작업 부하](../profiling/media/unevenworkload-1.png "UnevenWorkLoad_1")  
  
 위의 그림처럼 애플리케이션에서 여러 병렬 스레드 간에 균등하지 않은 작업 분산이 발생하면 각 스레드가 작업을 완료할 때 일반적인 계단 단계 패턴이 나타납니다. 동시성 시각화 도우미는 대개 각 동시 스레드에 대해 근접한 시작 시간을 보여줍니다. 그러나 이러한 스레드는 동시에 종료하는 대신 일반적으로 불균등하게 종료됩니다. 이 패턴은 병렬 스레드의 그룹 간에 불균등한 작업 분산을 나타내며, 이로 인해 성능이 저하될 수 있습니다. 이러한 문제를 해결하기 위해서는 병렬 스레드 간에 작업을 나누는 알고리즘을 다시 평가하는 것이 좋습니다.  
  
 다음 그림과 같이 동시성 시각화 도우미는 CPU 사용률 뷰에 이 증상을 CPU 사용률의 점진적인 단계별 감소로 표시할 수 있습니다.  
  
 ![균등하지 않은 작업 부하](../profiling/media/unevenworkload-2.png "UnevenWorkload_2")  
  
## <a name="oversubscription"></a>초과 구독  
 ![초과 구독](../profiling/media/oversubscription.png "초과 구독")  
  
 초과 구독이 발생하는 경우 프로세스의 활성 스레드 수가 시스템에서 사용 가능한 논리 코어의 수보다 큽니다. 위의 그림에서는 모든 활성 스레드의 상당한 선점 밴드와 함께 초과 구독의 결과를 보여 줍니다. 또한 범례를 보면 상당한 시간이 선점에 소요된 것(이 예제의 84%)을 알 수 있습니다. 이는 프로세스에서 논리 코어 수보다 더 많은 동시 스레드를 실행하도록 시스템에 요청하는 것을 나타냅니다. 그러나 시스템의 다른 프로세스가 이 프로세스에 사용 가능한 것으로 간주된 리소스를 사용하는 것을 나타낼 수도 있습니다.  
  
 이 문제를 평가할 때 다음 사항을 고려해야 합니다.  
  
- 전체 시스템이 초과 구독될 수 있습니다. 시스템의 다른 프로세스가 스레드를 선점하는 것이 좋습니다. 스레드 뷰에서, 선점 세그먼트 위에서 마우스를 잠시 멈추면 도구 설명에서 스레드 및 스레드를 선점한 프로세스를 식별해 줍니다. 이 프로세스가 반드시 사용자의 프로세스가 선점된 전체 시간 동안 실행된 프로세스는 아닐 수 있지만 사용자의 프로세스에 대해 선점 압력을 형성한 요인에 대한 힌트를 제공합니다.  
  
- 이 작업의 단계 중 사용자의 프로세스에서 실행할 적절한 스레드 수를 확인하는 방법을 평가합니다. 프로세스에서 직접 활성 병렬 스레드의 수를 계산하는 경우 시스템의 사용 가능한 논리 코어 수를 더 적절히 처리하도록 알고리즘을 수정하는 것이 좋습니다. 동시성 런타임, 작업 병렬 라이브러리 또는 PLINQ를 사용하면 이러한 라이브러리에서 스레드 수를 계산하는 작업을 수행합니다.  
  
## <a name="inefficient-io"></a>불충분한 I/O  
 ![비효율적인 I&#47;O](../profiling/media/inefficient-io.png "Inefficient_IO")  
  
 I/O의 오용 또는 남용은 애플리케이션의 비효율성에 대한 일반적인 원인입니다. 위의 그림을 살펴보세요. 표시되는 시간 표시 막대 프로필은 표시되는 스레드 시간의 42%가 I/O에 사용되는 것을 보여 줍니다. 타임라인은 많은 양의 I/O를 보여 주며, 이는 프로파일링된 애플리케이션이 자주 I/O에 의해 차단되었음을 나타냅니다. I/O의 종류 및 프로그램이 차단되는 위치에 대한 세부 정보를 보려면 문제 영역을 확대하고, 표시되는 시간 표시 막대 프로필을 검사한 다음 특정 I/O 블록을 클릭하여 현재 호출 스택을 표시합니다.  
  
## <a name="lock-convoys"></a>잠금 호송  
 ![잠금 호송](../profiling/media/lock-convoys.png "Lock_Convoys")  
  
 애플리케이션이 선착순으로 잠금을 획득하고 잠금의 도착률이 잠금 획득률보다 높은 경우 잠금 호송이 발생합니다. 이러한 두 조건이 결합되면 잠금에서 백업을 시작하라는 요청이 발생합니다. 이 문제를 해결하는 방법은 "불공정" 잠금 또는 잠금 해제된 상태의 스레드를 찾을 수 있도록 첫 번째 스레드에 대한 액세스를 제공하는 잠금을 사용하는 것입니다. 위의 그림에서는 이 호송 동작을 보여 줍니다. 이 문제를 해결하려면 동기화 개체에 대한 경합을 줄이고 불공정 잠금을 사용해 보세요.  
  
## <a name="see-also"></a>참고 항목  
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)
