---
title: 'DA0039: 매우 높은 비율의 잠금 경합 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ae2b836549918fa1179e4e70d51d760efbe2c35
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544926"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: 잠금 경합의 비율이 매우 높습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대 한 최신 설명서는 [DA0039: 매우 높은 비율의 잠금 경합](/visualstudio/profiling/da0039-very-high-rate-of-lock-contentions)을 참조 하세요.  
  
|항목|값|  
|-|-|  
|규칙 ID|DA0039|  
|범주|.NET Framework 사용|  
|프로파일링 방법|샘플링<br /><br /> 계측<br /><br /> .NET 메모리|  
|메시지|.NET 잠금 경합의 비율이 매우 높습니다. 동시성 프로필을 실행하여 이 잠금 경합의 원인을 조사하세요.|  
|규칙 유형|경고|  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 25개 이상의 샘플을 수집해야 합니다.  
  
## <a name="cause"></a>원인  
 프로파일링 데이터와 함께 수집되는 시스템 성능 데이터가 애플리케이션 실행 중에 발생한 잠금 경합의 비율이 지나치게 높다는 것을 나타냅니다. 동시성 프로파일링 방법을 통해 다시 프로파일링하여 경합의 원인을 찾아 보세요.  
  
## <a name="rule-description"></a>규칙 설명  
 다중 스레드 애플리케이션에서 한 번에 스레드 하나씩 직렬로 실행되어야 하는 코드의 임계 영역을 보호하는 데 잠금을 사용합니다. Microsoft .NET CLR(공용 언어 런타임)는 동기화 및 잠금 기본 형식의 전체 집합을 제공합니다. 예를 들어 C# 언어는 잠금 문(Visual Basic의 경우 SyncLock)을 지원합니다. 관리 되는 응용 프로그램은 `Monitor.Enter` `Monitor.Exit` system.object 네임 스페이스의 및 메서드를 호출 하 여 잠금을 직접 획득 하 고 해제할 수 있습니다. .NET Framework는 Mutex, ReaderWriterLock 및 Semaphore를 지원하는 클래스를 비롯하여 추가적인 동기화 및 잠금 기본 형식을 지원합니다. 자세한 내용은 MSDN 웹 사이트에 있는 .NET Framework 개발자 가이드에서 [동기화 기본 형식 개요](https://msdn.microsoft.com/library/ms228964.aspx)를 참조하세요. .NET Framework 클래스는 Windows 운영 체제에 기본 제공되는 하위 수준 동기화 서비스 위에 계층화됩니다. 이러한 클래스에는 임계 영역 개체와 많은 다양한 Wait 및 이벤트 알림 함수가 포함됩니다. 자세한 내용은 MSDN 라이브러리에서 Win32 및 COM 개발의 [Synchronization](https://msdn.microsoft.com/library/ms686353.aspx)(동기화) 섹션을 참조하세요.  
  
 동기화와 잠금에 사용되는 기본적인 .NET Framework 클래스와 네이티브 Windows 개체는 둘 다 연동 작업을 사용하여 변경해야 하는 공유 메모리 위치입니다. 연동 작업은 공유 메모리 위치에서 작동하는 하드웨어 관련 명령을 사용하여 원자성 작업을 통해 해당 상태를 변경합니다. 원자성 작업은 컴퓨터의 모든 프로세서에서 일관성이 있어야 합니다. Lock 및 WaitHandle은 설정되거나 재설정될 때 자동으로 연동 작업을 사용하는 .NET 개체입니다. 스레드로부터 안전한 방식으로 업데이트하기 위해 연동 작업을 사용해야 하는 애플리케이션에 다른 공유 메모리 데이터 구조가 있을 수 있습니다. 자세한 내용은 MSDN 라이브러리의 .NET Framework 섹션에서 [연동 작업](https://msdn.microsoft.com/library/sbhbke0y.aspx)을 참조하세요.  
  
 동기화와 잠금은 다중 스레드 애플리케이션이 제대로 실행되게 하는 데 사용되는 메커니즘입니다. 다중 스레드 애플리케이션의 각 스레드는 운영 체제에 의해 독립적으로 예약되는 독립 실행 단위입니다. 또 다른 스레드가 잠금을 유지하고 있기 때문에 잠금 획득을 시도하는 스레드가 지연될 때마다 잠금 경합이 발생합니다.  
  
 잠금이 빈번히 중첩됩니다. 임계 영역을 실행하는 스레드가 나중에 또 다른 잠금이 필요한 함수를 실행할 경우 중첩이 발생합니다. 일부 잠금 중첩은 피할 수 없습니다. 임계 영역은 스레드로부터 안전할 수 있도록 잠금에 의존하는 .NET Framework 메서드를 호출할 수 있습니다. 애플리케이션의 일부 임계 영역에서 다른 잠금 핸들을 통해 잠기는 Framework 메서드를 호출하면 잠금이 중첩됩니다. 중첩된 잠금 조건이 있으면 해결하고 수정하기가 너무 어려운 성능 문제가 발생할 수 있습니다.  
  
 프로파일링 실행 중에 수집된 측정값이 잠금 경합 수가 지나치게 많다는 것을 나타낼 경우 이 규칙이 실행됩니다. 잠금 경합은 잠금을 기다리고 있는 스레드의 실행을 지연시킵니다. 저사양 하드웨어에서 실행되는 부하 테스트나 단위 테스트의 잠금 경합 수가 적더라도 잠금 경합을 조사해야 합니다.  
  
> [!NOTE]
> 프로파일링 데이터에서 보고된 잠금 경합 비율이 높지만 과도하지 않으면 이 경고 메시지 대신 [DA0038: 높은 비율의 잠금 경합](../profiling/da0038-high-rate-of-lock-contentions.md) 경고 메시지가 실행됩니다.  
  
## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법  
 메시지를 두 번 클릭하여 프로파일링 데이터의 [표시](../profiling/marks-view.md) 뷰로 이동합니다.  **.NET CLR LocksAndThreads\Contention Rate / sec** 열을 찾습니다. 다른 단계보다 잠금 경합 수가 더 많은 특정 프로그램 실행 단계가 있는지 확인합니다.  
  
 동시성 프로파일링 방법을 사용하지 않을 경우에만 이 규칙이 실행됩니다. 동시성 프로파일링 방법은 애플리케이션에서 잠금 경합에 관련된 성능 문제를 진단할 때 사용할 가장 좋은 도구입니다. 동시성 프로파일링 데이터를 수집하여 애플리케이션의 잠금 동작을 파악합니다. 어떤 잠금이 아주 많이 경합되는지, 경합된 잠금을 기다리는 스레드의 실행 시간이 지연되는 기간, 특정 코드의 의미 등을 파악해야 합니다. 동시성 프로필은 네이티브 Windows 기능, .NET Framework 클래스 및 응용 프로그램에서 참조 하는 기타 모든 타사 라이브러리의 잠금 동작을 포함 하 여 모든 잠금 경합에 대 한 데이터를 수집 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE의 동시성 프로파일링에 대한 자세한 내용은 [스레드 및 프로세스 동시성 데이터 수집](../profiling/collecting-thread-and-process-concurrency-data.md)을 참조하세요. 명령줄의 동시성 프로파일링 정보에 대한 링크는 [명령줄에서 프로파일링 방법 사용](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)의 **동시성 방법을 사용하여 리소스 경합 및 스레드 작업 데이터 수집** 섹션을 참조하세요.
