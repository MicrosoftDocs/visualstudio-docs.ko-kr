---
title: 사용자(VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7dbb1a155e8e0ffd2690b5850299b8075a63ea3d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779963"
---
# <a name="user-vsperfcmd"></a>사용자(VSPerfCmd)
**User** 옵션은 프로파일링된 프로세스를 소유한 계정의 도메인 및 사용자 이름을 지정합니다. 이 옵션은 프로세스가 로그온한 사용자 이외의 사용자로 실행 중인 경우에만 필요합니다. Windows 작업 관리자의 **프로세스** 탭에 있는 사용자 이름 열에 프로세스 소유자가 나열됩니다.

 **User** 옵션은 **Start** 옵션도 포함하는 명령줄에서만 지정할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]
```

#### <a name="parameters"></a>매개 변수
 `Domain` 사용자 도메인의 이름입니다.

 `UserName` 사용자의 이름입니다.

## <a name="required-options"></a>필수 옵션
 **User** 옵션은 **Start** 옵션에만 사용할 수 있습니다.

 **시작:** `Method` 지정된 프로파일링 방법으로 프로파일러를 초기화합니다.

## <a name="example"></a>예제
 다음 예제에서는 **User** 옵션을 사용하는 방법을 보여 줍니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
