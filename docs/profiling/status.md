---
title: 상태 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778247"
---
# <a name="status"></a>Status
*VSPerfCmd.exe* **Status** 옵션은 프로파일러의 상태에 대한 정보 및 현재 프로파일링되는 모든 프로세스를 표시합니다.

 **Status** 옵션은 명령줄에 지정된 유일한 옵션이어야 합니다. 프로파일러는 상태를 표시하려면 *VSPerfCmd.exe* **Start** 옵션으로 초기화되어야 합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>매개 변수
 없음

## <a name="remarks"></a>설명
 **Status** 옵션은 프로파일러에 대한 다음 상태 정보를 표시합니다.

 **출력 파일 이름** 현재 프로파일러 데이터 파일의 경로 및 파일 이름입니다.

 **컬렉션 모드** SAMPLE 또는 TRACE

 **Maximum Processes** 한 번에 프로파일링될 수 있는 최대 프로세스 수와 현재 활성 프로세스의 수입니다.

 **Maximum Threads** 한 번에 프로파일링될 수 있는 최대 스레드 수입니다.

 **버퍼 수** 프로파일링 데이터 쓰기 전용 메모리 버퍼의 수입니다.

 **버퍼 크기** 메모리 버퍼의 크기(바이트)입니다.

 **Status** 옵션은 현재 프로파일링되고 있는 각 프로세스에 대한 다음 상태 정보를 표시합니다.

 **Process** 프로파일링된 프로세스의 이름입니다.

 **Process ID** 프로세스의 시스템 식별자입니다.

 **스레드 수** 현재 실행 중인 스레드 수입니다.

 **Start/Stop Count** 이 프로세스에 대한 데이터 수집을 제어하는 기본 내부 프로파일러 카운트입니다. 카운트는 데이터를 수집하기 위해 1과 같아야 합니다. 프로파일러 API 및 VSPerfCmd 옵션 **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** 및 **ThreadOff**에서 Start/Stop 카운트를 조작할 수 있습니다.

 **Suspend/Resume Count** 이 프로세스에 대한 데이터 수집을 제어하는 보조 내부 프로파일러 카운트입니다. 카운트는 데이터를 수집하기 위해 0보다 작거나 같아야 합니다. **Suspend/Resume** 카운트는 프로파일러 API에 의해서만 조작할 수 있습니다.

 **모니터에 액세스할 수 있는 권한을 가진 사용자** 프로파일러에 대한 액세스 권한이 있는 사용자의 이름을 나열합니다. VSPerfCmd.exe **Admin** 옵션을 사용하여 추가 사용자에게 액세스를 부여할 수 있습니다.

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
