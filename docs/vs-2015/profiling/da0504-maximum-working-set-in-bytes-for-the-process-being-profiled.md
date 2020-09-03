---
title: 'DA0504: 프로파일링 중인 프로세스에 대한 최대 작업 집합(바이트) | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c57e006196611b49909f3ad6bfc866a028a8621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850878"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: 프로파일링되고 있는 프로세스의 최대 작업 세트(바이트)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0504 |  
| 범주 | 리소스 관리 |  
| 프로 파일링 방법 | 모두 |  
| 메시지 | 이 정보는 정보를 위해서만 수집 되었습니다. Process Working Set 카운터는 프로파일링하고 있는 프로세스의 실제 메모리 사용량을 측정합니다. 보고된 값은 모든 측정 간격에서 관찰되는 최댓값입니다.|  
| 규칙 유형 | 정보 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 이 메시지는 프로세스가 현재 사용 중인 실제 메모리의 최대 크기(바이트)를 보고합니다. 프로세스 작업 집합은 현재 실제 메모리에 있는 프로세스 주소 공간의 페이지를 나타냅니다. 이 규칙은 프로파일링이 활성화된 동안 프로세스 작업 집합의 최대값을 보고합니다.  
  
 보고된 값에는 프로세스가 참조한 공유 메모리 세그먼트의 상주 페이지가 포함됩니다. 프로세스가 참조하는 공유 DLL은 계산되는 공유 메모리 세그먼트에 포함됩니다. 공유 메모리 세그먼트 때문에 프로세스 작업 집합의 값은 프로세스가 할당한 가상 메모리 크기보다 클 수 있습니다.  
  
 프로세스 작업 집합의 크기는 프로세스가 적극적으로 사용하는 가상 메모리 크기를 반영합니다. 또한 애플리케이션을 실행할 수 있는 실제 메모리(또는 RAM)의 크기 및 해당 실제 메모리에 대한 실행 중인 다른 프로세스의 경합이 이 크기에 영향을 미칩니다. 프로세스 작업 집합에 대한 자세한 내용은 MSDN의 Windows 메모리 관리 설명서에 있는 [Working Set](https://msdn.microsoft.com/library/cc441804.aspx)(작업 집합)를 참조하세요.  
  
## <a name="how-to-use-rule-data"></a>규칙 데이터를 사용하는 방법  
 규칙은 Windows 성능 모니터링 기능에서 이 측정 데이터를 수집하고 참고용으로만 보고합니다. 규칙을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 테스트 시나리오에서 애플리케이션의 성능을 파악합니다.  
  
 [오류 목록] 창에서 메시지를 두 번 클릭하여 프로파일링 데이터의 [표시 뷰](../profiling/marks-view.md)로 이동합니다. **Process\Working Set** 및 **Memory\Pages/sec** 카운터 열을 찾습니다. 그런 다음 **Process\Working Set**의 최대값을 찾아 **Memory\Pages/sec** 갑에 비교합니다. 대개 작업 집합 최대값은, 특히 컴퓨터의 메모리가 제한될 경우 감소한 페이징 IO 활동이 있는 간격과 연관됩니다.
