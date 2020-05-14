---
title: AutoMark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 072f80508f81a7b42ad481048f604cbd4c54af88
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779794"
---
# <a name="automark"></a>AutoMark
**AutoMark** 옵션은 Windows 소프트웨어 성능 카운터 이벤트의 컬렉션 간 밀리초의 수를 지정합니다. Windows 성능 카운터는 **WinCounter** 옵션에서 지정됩니다.

 하나의 **AutoMark** 옵션만 명령줄에서 지정할 수 있습니다. **AutoMark**에서 지정한 **WinCounter** 샘플링 간격은 주 샘플링 간격과 무관합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds
```

#### <a name="parameters"></a>매개 변수
 `Milliseconds` Windows 성능 카운터 이벤트의 컬렉션 간 밀리초의 수를 지정합니다.

## <a name="required-options"></a>필수 옵션
 **WinCounter:** `Path` 수집할 Windows 성능 카운터를 지정합니다. 계측 방법을 사용하는 경우 여러 Windows 카운터를 지정할 수 있습니다. 샘플링 방법을 사용하는 경우 하나의 Windows 카운터만 지정할 수 있습니다. **WinCounter** 옵션은 **Start** 옵션을 포함하는 명령줄에서 지정되어야 합니다.

## <a name="example"></a>예제
 이 예제에서 1000밀리초의 샘플링 간격은 두 개의 Windows 성능 카운터에 대해 설정됩니다.

```cmd
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
