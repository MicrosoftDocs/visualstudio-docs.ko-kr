---
title: AutoMark | Microsoft Docs
description: AutoMark 옵션을 사용하여 Windows 성능 카운터 데이터 수집 이벤트 간 시간 간격을 지정합니다. WinCounter 옵션과 함께 사용합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 94578571a9cfe6a170fd94019615eeec3071356a
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205764"
---
# <a name="automark"></a>AutoMark
**AutoMark** 옵션은 Windows 소프트웨어 성능 카운터 이벤트의 컬렉션 간 밀리초의 수를 지정합니다. Windows 성능 카운터는 **WinCounter** 옵션에서 지정됩니다.

 하나의 **AutoMark** 옵션만 명령줄에서 지정할 수 있습니다. **AutoMark** 에서 지정한 **WinCounter** 샘플링 간격은 주 샘플링 간격과 무관합니다.

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
