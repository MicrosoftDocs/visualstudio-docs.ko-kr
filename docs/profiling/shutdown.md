---
title: 종료 | Microsoft Docs
description: Shutdown 옵션을 사용하여 현재 프로파일링된 프로세스가 종료 또는 분리되기를 기다린 다음, 프로파일러를 끄고 프로파일링 데이터 파일을 닫는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 455278f7fccbc9e4f80ce4f11a167e5b433ca8ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950041"
---
# <a name="shutdown"></a>종료
**Shutdown** 옵션은 현재 프로파일링된 프로세스가 종료 또는 분리되기를 기다린 다음, 프로파일러를 해제하고 프로파일링 데이터 파일을 닫습니다. **Shutdown** 옵션은 프로파일링 실행의 마지막 명령이어야 합니다.

 시간 제한 매개 변수를 지정하지 않는 경우 **Shutdown** 옵션은 무기한으로 대기합니다. 시간 제한 매개 변수를 지정하는 경우 옵션은 프로파일러를 해제하거나 데이터 파일을 닫지 않고 지정된 시간(초) 후 반환합니다.

 **Shutdown** 옵션은 명령줄에 지정된 유일한 옵션이어야 합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Shutdown[:Timeout]
```

#### <a name="parameters"></a>매개 변수
`Timeout`
- (선택 사항) 지정하는 경우 옵션은 프로파일러를 해제하거나 프로파일링 데이터 파일을 닫지 않고 지정된 시간(초) 후 반환합니다.

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
