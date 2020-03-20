---
title: VSPerfMon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 50519554f7ec71e277dc776b05bc2967c1071f52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779898"
---
# <a name="vsperfmon"></a>VSPerfMon
VSPerfMon 도구를 사용하면 애플리케이션의 성능 데이터를 수집할 수 있습니다. 일반적으로는 *VSPerfCmd.exe*를 사용하여 이 도구를 실행합니다. VSPerfMon에는 VSPerfCmd 도구를 사용하는 경우에는 제공되지 않는 프로세스 연결 또는 분리에 대한 추가 정보가 표시됩니다. 이 정보를 보려면 별도의 창에서 VSPerfMon을 시작합니다. VSPerfMon을 호출하려면 다음 구문을 사용합니다.

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 아래 표에는 VSPerfMon 도구의 옵션에 대한 설명이 나와 있습니다.

|옵션|설명|
|-------------|-----------------|
|**U**|리디렉션된 콘솔 출력이 유니코드로 기록됩니다.  이 옵션을 첫 번째 옵션으로 지정해야 합니다.|
|**OUTPUT:** `<` *file name* `>`|출력을 지정한 파일 이름으로 리디렉션합니다.|
|**TRACE**|계측된 프로파일링에 대해 성능 모니터를 시작합니다.|
|**SAMPLE**|샘플링 프로파일링에 대해 성능 모니터를 시작합니다.|
|**COVERAGE**|코드 검사 수집에 대해 성능 모니터를 시작합니다.|
|**CONCURRENCY**|리소스 경합 프로파일링에 대한 성능 모니터를 시작합니다.|
|**USER:** `[` *domain* `\]` *username*|클라이언트가 지정한 계정에서 성능 모니터에 액세스할 수 있습니다.|
|**CROSSSESSION**|상호 세션 프로파일링을 사용하도록 설정합니다.|
|**COUNTER** `:cfg`|계측(TRACE) 프로파일링 방법을 사용할 때 각 계측 지점에서 수집할 CPU 카운터를 지정합니다. 여러 Counter 옵션을 지정하면 여러 카운터 데이터를 수집할 수 있습니다.<br /><br /> 카운터(*cfg*) 데이터를 지정하려면 다음 구문을 사용합니다.<br /><br /> **CounterName** [ **,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName**은 VSPerfCmd /QueryCounters 명령에서 반환하는 카운터의 이름입니다.<br />-   **Reload**는 카운터 이벤트 샘플링 간격입니다. 계측 방법에서는 *Reload*를 사용하지 마세요.<br />-   **FriendlyName**은 지정하는 경우 프로파일링 도구 보고서 열 이름의 **CounterName**을 바꿉니다.|
|**WINCOUNTER** `:path`|표시 데이터와 함께 포함할 Windows 성능 카운터를 지정합니다. `path`는 PDH 카운터 경로 형식의 Windows 성능 카운터 문자열입니다. 예를 들어:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK** `:n`|/WINCOUNTER 사용 시 자동 표시 간의 시간 간격(밀리초)을 지정합니다. 가장 가까운 500ms로 반올림됩니다.<br /><br /> 자동 표시를 사용하지 않으려면 0을 사용합니다. 값을 지정하지 않는 경우의 기본값은 500ms입니다.|

## <a name="see-also"></a>참조
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [성능 보고서 뷰](../profiling/performance-report-views.md)
