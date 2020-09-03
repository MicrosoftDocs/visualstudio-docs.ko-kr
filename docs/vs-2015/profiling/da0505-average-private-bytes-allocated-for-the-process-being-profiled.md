---
title: 'DA0505: 프로파일링 중인 프로세스에 할당되는 평균 전용 바이트 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69a7eaeecd65ffdfbd575b59fbea15c476d0fbeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850873"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: 프로파일링되고 있는 프로세스에 할당된 평균 전용 바이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0505 |  
| 범주 | 리소스 관리 |  
| 프로 파일링 방법 | 모두 |  
| 메시지 | 이 정보는 정보를 위해서만 수집 되었습니다. Process Private Bytes 카운터는 프로파일링하고 있는 프로세스에 의해 할당된 가상 메모리를 측정합니다. 보고된 값은 모든 측정 간격에 걸쳐 계산된 평균값입니다.|  
| 규칙 유형 | 정보 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 이 메시지는 프로세스가 현재 할당한 가상 메모리의 평균 크기(바이트)를 보고합니다(전용 바이트). 전용 바이트는 프로세스 내에서 실행되는 스레드만 액세스할 수 있는, 프로세스에 의해 할당된 가상 메모리 위치를 나타냅니다.  
  
 32비트 컴퓨터에서 실행되는 32비트 프로세스의 경우 프로세스 중 전용 부분의 상한은 2GB입니다. 32비트 프로세스는 [/3GB](https://msdn.microsoft.com/library/ff556232.aspx) Boot.ini 스위치를 사용해서 최대 3GB의 가상 메모리를 얻을 수 있습니다. 64비트 컴퓨터에서 실행되는 32비트 프로세스는 전용 가상 메모리를 4GB까지 확보할 수 있습니다.  
  
 64비트 컴퓨터에서 실행되는 64비트 프로세스는 전용 가상 메모리를 8TB까지 확보할 수 있습니다.  
  
 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격에 대한 평균입니다.  
  
 프로세스 주소 공간에 대한 자세한 내용은 Windows 메모리 관리 설명서에서 [Virtual Address Space](https://msdn.microsoft.com/library/aa366912.aspx)(가상 주소 공간)를 참조하세요.  
  
## <a name="how-to-use-rule-data"></a>규칙 데이터를 사용하는 방법  
 보고된 값을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 프로파일링 시나리오에서 애플리케이션의 성능을 파악합니다.
