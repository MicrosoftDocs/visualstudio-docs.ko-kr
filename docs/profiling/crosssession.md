---
title: CrossSession | Microsoft Docs
description: VSPerfCmd.exe CrossSession 옵션을 사용하여 프로파일러가 콘솔 세션에서 데이터를 수집할 수 있도록 하는 방법을 알아봅니다. Start 옵션도 지정해야 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a52acb80bac511706086c56074eb5bfe450b7674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955907"
---
# <a name="crosssession"></a>CrossSession
*VSPerfCmd.exe* **CrossSession** 옵션을 통해 프로파일러는 모든 콘솔 세션에서 데이터를 수집할 수 있습니다. **CrossSession** 옵션은 **Start** 옵션과 함께 사용되어야 합니다.

 **CrossSession** 대신 약어 **CS** 를 사용할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>매개 변수
 없음

## <a name="valid-options"></a>유효한 옵션
 다른 세션에서 프로파일링을 활성화하기 위해 **CrossSession** 옵션은 **Start** 옵션에서 지정되어야 합니다. 또한 **CrossSession** 은 다음 **VSPerfCmd Attach** 및 **Detach** 명령에 지정되어야 합니다.

 **시작:** `Method`**Start** 옵션은 지정된 프로파일링 방법으로 프로파일러를 초기화합니다.

 **연결:** _PID_[ **,** _PID_] 지정된 프로세스의 프로파일링을 시작합니다.

 **Detach**[**:**_PID_[,_PID_]] 지정된 프로세스의 프로파일링을 중지합니다.

## <a name="example"></a>예
 이 예제에서 **CrossSession** 옵션은 다른 콘솔 세션에서 시작된 애플리케이션에 연결하는 데 사용됩니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
