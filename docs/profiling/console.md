---
title: 콘솔 | Microsoft Docs
description: VSPerfCmd.exe의 Console 옵션을 사용하여 새 명령 프롬프트 창에서 지정된 애플리케이션을 시작합니다. 해당 옵션은 Launch 옵션과 함께 사용해야 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a5234c2b7368a992676e12ecbdcd5ea36219f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955413"
---
# <a name="console"></a>Console
VSPerfCmd.exe **콘솔** 옵션은 새 명령 프롬프트 창에서 지정된 애플리케이션을 시작합니다. **콘솔** 은 VSPerfCmd **Launch** 옵션에만 사용할 수 있습니다. 애플리케이션이 명령줄 애플리케이션이 아닌 경우 **콘솔** 에 영향을 주지 않습니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Launch:AppName /Console
```

#### <a name="parameters"></a>매개 변수
 없음

## <a name="required-options"></a>필수 옵션
 **콘솔** 은 **Launch** 옵션도 포함하는 명령줄에서만 지정할 수 있습니다.

 **시작:** `AppName` 프로파일러 및 `AppName`에서 지정한 애플리케이션을 시작합니다.

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
