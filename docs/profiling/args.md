---
title: Args | Microsoft 문서
description: VSPerfCmd.exe의 ARGS 옵션을 사용하여 시작 하위 명령의 대상 애플리케이션에 인수 목록을 전달합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44e68822ebd444b8683b85b2df0c49b14d78bcaa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901069"
---
# <a name="args"></a>Args
VSPerfCmd.exe **Args** 옵션은 **Launch** 하위 명령의 대상 애플리케이션에 전달되는 인수 목록을 지정합니다.

 명령줄에서 **Launch** 도 지정한 경우에만 **Args** 를 사용할 수 있습니다. **Launch** 가 지정된 경우 **Args** 는 선택 사항입니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>매개 변수
 `Arguments`**Launch** 명령의 대상 애플리케이션에 대한 인수 목록입니다.

## <a name="required-options"></a>필수 옵션
 **시작:** `AppName` 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.

## <a name="example"></a>예제
 다음 예제에서는 **Args** 옵션을 사용하여 TestApp.exe에 인수를 전달합니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
