---
title: 프로파일링 도구 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686209"
---
# <a name="profiling-tools"></a>프로파일링 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로파일링 및 진단 도구는 메모리 및 CPU 사용량 진단 및 애플리케이션 수준 문제 진단을 도와줍니다. 이러한 도구를 사용하면 디버거에서 애플리케이션을 실행하는 동안 데이터(예: 변수 값, 함수 호출, 이벤트)를 누적할 수 있습니다. 코드를 실행하는 동안 다양한 지점에서 애플리케이션 상태를 볼 수 있습니다.  
  
 프로젝트 형식에(예: 데스크톱, UWP, ASP.NET) 사용할 수 있는 도구를 보려면 아래쪽의 요약을 확인합니다.  
  
 디버그 세션 중에 도구를 사용하려면 **디버그/Windows/진단 도구 표시** 를 사용하거나 포커스가 있는 성능 분석을 수행하려면 **디버그/성능 프로파일러...** 를 사용하여 프로파일링 도구에 액세스할 수 있습니다.  다른 방법에 대한 자세한 내용을 보려면 [Running Profiling Tools With or Without the Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) 을(를) 참조하세요.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 이 릴리스의 새 기능에 대해 자세히 알아보려면 [프로 파일링 도구의 새로운 기능](../profiling/what-s-new-in-profiling-tools.md)을 참조하세요.  
  
 다음 섹션에서는 Visual Studio에서 사용할 수 있는 다양한 성능 도구를 설명합니다.  
  
## <a name="memory-usage"></a>메모리 사용량  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 **메모리 사용량** 도구를 사용 하 여 디버깅 하는 동안 메모리 누수 및 비효율적인 메모리를 찾습니다. 이 도구를 통해 관리되는 메모리 및 기본 메모리 힙의 스냅샷을 만들 수 있습니다. 이 도구는 데스크톱 앱, Windows 유니버설 앱, ASP.NET 앱에서 사용할 수 있습니다. **메모리 사용량** 도구는 디버깅 하는 동안 **진단 도구** 창에서 실행 하거나 (디버그/w i n d o**w s/진단 도구 표시**) 디버거 외부에서 (**디버그/성능 프로파일러 ...**) 실행할 수 있습니다. 자세한 내용은 [디버깅 하지 않고](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) [메모리 사용](../profiling/memory-usage.md) 및 메모리 사용량을 참조 하세요.  
  
## <a name="cpu-usage"></a>CPU 사용량  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **CPU 사용량** 도구는 CPU에서 C++, C#/VB 및 JavaScript 코드 실행에 시간을 소모하는 상황을 보여 줍니다.  이 도구는 데스크톱 및 Windows 유니버설 앱은 물론 Azure 앱 서비스 앱에서 사용할 수 있습니다. **CPU 사용량** 도구는 디버깅 하는 동안 **진단 도구** 창에서 실행 하거나 (**디버그/Windows/진단 도구 표시**) 디버거 외부에서 (**디버그/성능 프로파일러 ...**) 실행할 수 있습니다. 자세한 내용은 [CPU 사용량](../profiling/cpu-usage.md) 을 참조 하세요.  
  
## <a name="performance-explorer"></a>성능 탐색기  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **성능 탐색기** (**디버그/프로파일러/성능 탐색기**)를 사용하면 **CPU 샘플링**,  **계측**, **.NET 메모리 할당**, **리소스 경합**을 비롯한 다양한 도구를 사용할 수 있습니다. 성능 탐색기 도구는 데스크톱 앱과 ASP.NET 앱에서 사용할 수 있지만 Windows 유니버설 앱에서는 사용할 수 없습니다. 자세한 내용은 [성능 탐색기](../profiling/performance-explorer.md)를 참조하세요.  
  
## <a name="gpu-usage"></a>GPU 사용량  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Direct3D 앱의 고급 하드웨어 사용률을 보다 잘 파악하려면 [GPU 사용량](../debugger/gpu-usage.md) 도구를 사용합니다. 이 도구는 데스크톱 및 Windows 유니버설 앱에서 사용할 수 있지만 ASP.NET 앱에서는 사용할 수 없습니다. **GPU 사용량** 도구는 디버깅하는 동안 **진단 도구** 창에서 실행하거나(**디버그/진단 도구 표시**) 디버거 외부에서(**디버그/성능 프로파일러...**) 실행할 수 있습니다.  
  
## <a name="application-timeline"></a>애플리케이션 타임라인  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Application Timeline](../profiling/application-timeline.md) 도구를 사용하면 리소스 소비에 대해 자세한 뷰를 제공하기 때문에 XAML 애플리케이션의 성능을 개선하는 데 도움이 됩니다. **애플리케이션 타임라인** 은 데스크톱 및 Windows 유니버설 앱에서 사용할 수 있지만 ASP.NET 앱에서는 사용할 수 없습니다. **애플리케이션 타임라인** 도구는 **진단 도구** 창에서(**디버그/성능 프로파일러...**) 실행할 수 있습니다.  
  
## <a name="perftips"></a>PerfTips  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 디버거가 중단점 또는 단계별 실행 작업에서 실행을 중지하는 경우 중단점과 이전 중단점 사이의 경과 시간이 편집기 창에 팁으로 표시됩니다. [PerfTips](../profiling/perftips.md) 는 디버깅 중에 앱의 성능을 모니터링하고 분석하도록 도와줍니다. **PerfTips** 는 데스크톱, Windows 유니버설, ASP.NET 앱에서 볼 수 있습니다.  
  
## <a name="javascript-memory"></a>JavaScript 메모리  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [JavaScript 메모리](../profiling/javascript-memory.md) 도구를 사용하면 앱에 포함된 각 함수의 진입 및 종료에서 타이밍 정보를 수집하여 코드의 성능 관련 문제를 측정, 평가 및 대상으로 지정할 수 있습니다. 이 도구는 Windows 유니버설 HTML 앱에서 사용할 수 있습니다. **JavaScript 함수 타이밍** 도구는 **진단 도구** 창에서(**디버그/성능 프로파일러...**) 실행할 수 있습니다.  
  
## <a name="html-ui-responsiveness"></a>HTML UI 응답성  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI 응답성](../profiling/html-ui-responsiveness.md) 도구는 앱에서 응답성 부족, 느린 로딩 시간, 예상보다 빈도가 낮은 시각적 업데이트를 비롯한 성능 문제를 격리하도록 도와줍니다. 이 도구는 Windows 유니버설 HTML 앱에서 사용할 수 있습니다. **HTML UI 응답성** 도구는 **진단 도구** 창에서(**디버그/성능 프로파일러...**) 실행할 수 있습니다.  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md)를 사용하면 재현하기 힘든 디버그 오류와 함수 호출 및 디버거 이벤트 중 **로컬** 창의 데이터를 검토하고, 특정 이벤트를 기록할 수 있습니다.  IntelliTrace는 본래 디버깅 도구이지만, 성능 조사에 사용할 수 있는 정보도 제공합니다. 이 도구는 데스크톱, Windows 유니버설, ASP.NET C# 앱의 Visual Studio Enterprise에서만 사용할 수 있습니다. IntelliTrace는 디버깅 중에 **진단 도구** 창에서(**디버그/Windows/진단 도구 표시**) 찾을 수 있습니다.  
  
## <a name="profiling-in-production"></a>프로덕션에서 프로파일링  
 프로덕션에서 프로파일링에 권장되는 방법은 [vsperf.exe를 사용하여 명령줄](../profiling/using-the-profiling-tools-from-the-command-line.md) 에서 프로파일링하여 CPU 프로필을 수집하는 것입니다. Azure 앱 서비스의 원격 프로파일링 지원의 경우, [서버 탐색기 또는 Kudu 포털](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/)을 통해 프로파일링할 수 있습니다.  
  
## <a name="which-tool-should-i-use"></a>사용해야 하는 도구  
 다음 테이블에는 Visual Studio가 제안하는 다양한 도구 및 그와 함께 사용할 수 있는 다양한 프로젝트 형식이 나열되어 있습니다.  
  
|성능 도구|Windows 데스크톱|Windows 유니버설/스토어|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[메모리 사용량](../profiling/memory-usage.md)|예|예|no|  
|[CPU 사용량](../profiling/cpu-usage.md)|예|예|Azure 앱 서비스만 해당|  
|[GPU 사용량](../debugger/gpu-usage.md)|예|예|no|  
|[애플리케이션 타임라인](../profiling/application-timeline.md)|예|예|no|  
|[PerfTips](../profiling/perftips.md)|예|XAML은 예, HTML은 no|no|  
|[성능 탐색기](../profiling/performance-explorer.md)|예|no|예|  
|[IntelliTrace](../debugger/intellitrace.md)|.NET Enterprise만 해당|.NET Enterprise만 해당|.NET Enterprise만 해당|  
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|no|HTML은 예, XAML은 no|no|  
|[JavaScript 메모리](../profiling/javascript-memory.md)|no|HTML은 예, XAML은 no|no|  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
