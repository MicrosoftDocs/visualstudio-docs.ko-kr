---
title: PerfTips | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295862"
---
# <a name="perftips"></a>PerfTips
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거 *PerfTips* 및 디버거 통합 **진단 도구** 는 디버그하는 동안 앱의 성능을 모니터링 및 분석하는 데 도움이 됩니다.  
  
 디버거 통합 진단 도구는 개발하는 동안 성능 문제를 인식할 수 있는 효율적인 방법이지만 디버거가 앱 성능에 상당한 영향을 미칠 수도 있습니다. 보다 정확한 성능 데이터를 수집하려면 성능 조사의 추가 부분으로 디버거 도구 외부에서 실행되는 Visual Studio 진단 도구를 사용하는 것이 좋습니다. [디버깅 하지 않고 프로 파일링 도구 실행](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)을 참조 하세요.  
  
## <a name="perftips"></a>PerfTips  
 디버거가 중단점 또는 단계별 실행 작업에서 실행을 중지하는 경우 중단점과 이전 중단점 사이의 경과 시간이 편집기 창에 팁으로 표시됩니다. 자세한 내용은 [PerfTips: Visual Studio에서 디버깅 중에 성능 정보 한눈에 확인](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)을 참조하세요.  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>진단 도구 창  
 중단점 및 관련된 타이밍 데이터가 진단 도구 창에 기록됩니다.  
  
 다음 그림은 Visual Studio 2015 업데이트 1의 진단 도구 창을 보여 줍니다.  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
- **중단 이벤트** 타임라인은 디버깅 세션에서 적중된 중단점을 표시합니다. 이벤트를 클릭하여 **디버거** 세부 정보 목록에서 선택합니다.  
  
- **CPU 사용률** 그래프는 디버깅 세션에서 모든 프로세서 코어의 CPU 사용 변경 내용을 보여 줍니다.  
  
- **디버거** 세부 정보 창의 **이벤트** 목록에는 각 중단 이벤트에 대한 항목이 포함됩니다.  
  
- 중단 이벤트의 **기간** 열에는 이벤트와 이전 중단점 사이의 경과 시간이 표시됩니다.  
  
## <a name="turn-perftips-on-or-off"></a>PerfTips 켜기 또는 끄기  
 PerfTips를 사용하거나 사용하지 않도록 설정하려면  
  
1. **디버그** 메뉴에서 **옵션**을 선택합니다.  
  
2. **디버깅 중에 경과한 시간 성능 팁 표시**를 선택하거나 선택 취소합니다.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>진단 도구 창 켜기 또는 끄기  
 진단 도구 창을 사용하거나 사용하지 않도록 설정하려면  
  
1. **디버그** 메뉴에서 **옵션**을 선택합니다.  
  
2. **디버그하는 동안 진단 도구 사용**을 선택하거나 선택 취소합니다.
