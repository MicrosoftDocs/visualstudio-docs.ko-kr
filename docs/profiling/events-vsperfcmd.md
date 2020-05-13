---
title: 이벤트(VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777323"
---
# <a name="events-vsperfcmd"></a>이벤트(VSPerfCmd)
*VSPerfCmd.exe* **Events** 옵션은 ETW(Windows용 이벤트 추적) 로깅을 제어합니다. ETW 데이터는 프로파일러 데이터 파일에서 분리된 .etl 파일에 저장됩니다. [VSPerfReport](../profiling/vsperfreport.md) /summary:etw 명령을 사용하여 보고서에서 데이터를 볼 수 있습니다.

 VSPerfCmd **Shutdown** 명령이 프로파일링을 중지하기 위해 호출되기 전에 언제든지 **Events** 옵션을 호출할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>매개 변수
 **On**&#124;**Off** 이벤트 데이터 수집을 시작하거나 중지합니다.

 `Guid` 공급자의 컨트롤의 GUID입니다.

 `ProviderName` WMI(Windows Management Instrumentation)로 등록된 공급자의 이름입니다.

 `Flags` 이벤트 공급자에 의해 정의된 "0x" 접두사 16진수 플래그 값입니다.

 `Level` 수집되는 데이터 양을 지정합니다. `Level`은 이벤트 공급자에 의해 정의됩니다.

 **Events** 옵션은 다음 커널 키워드를 공급자 이름으로 인식합니다.

 **Process** 프로세스 이벤트

 **Thread** 스레드 이벤트

 **Image** 이미지 로드 및 언로드 이벤트

 **Disk** 디스크 I/O 이벤트

 **File** 파일 I/O 이벤트

 **Hardfault** 하드 페이지 폴트

 **Pagefault** 소프트 페이지 폴트

 **Network** 네트워크 이벤트

 **Registry** 레지스트리 액세스 이벤트

 커널 공급자만 사용할 수 있습니다. 모니터가 종료될 때까지 비활성화되거나 해당 플래그를 수정할 수 없습니다.

## <a name="remarks"></a>설명

> [!NOTE]
> CLR ETW 이벤트를 활성화하면 추가 시작 데이터도 추적 뷰 보고서에 수집됩니다. 시작 이벤트를 보고서 표시에서 제외하려면 다음 명령을 사용합니다.

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> 시작 이벤트를 제외하지 않는 경우 이러한 이벤트는 MOF(Managed Object Format) 파일에 나열되지 않으므로 보고서에 GUID로 표시됩니다. 자세한 내용은 Microsoft 웹 사이트의 다음 페이지를 참조하세요. [샘플 MOF(Managed Object Format) 파일](https://msdn.microsoft.com/library/default.aspx)

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
