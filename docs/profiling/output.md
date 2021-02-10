---
title: 출력 | Microsoft Docs
description: Output 옵션을 사용하여 성능 세션에 대한 프로파일링 데이터 파일의 이름을 지정하는 방법을 알아봅니다. Output은 Start 옵션과 함께 사용되어야 합니다.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de3edb5e9b9c04b53d6b669828020c0999d218e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922397"
---
# <a name="output"></a>출력
**Output** 옵션은 성능 세션에 대한 프로파일링 데이터 파일의 이름을 지정합니다. **Output** 은 **Start** 옵션과 함께 사용되어야 합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>매개 변수
 `FileName` 데이터 파일의 이름입니다. 전체 및 부분 경로를 사용할 수 있습니다. 경로가 지정되지 않은 경우 파일이 현재 디렉터리에 만들어집니다.

## <a name="required-options"></a>필수 옵션
 **Output** 옵션은 **Start** 옵션과 함께 사용되어야 합니다.

 **시작:** `Method` 출력 파일 이름을 지정합니다.

## <a name="example"></a>예
 다음 예제에서 프로파일링 데이터 파일은 현재 디렉터리에 만들어집니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
