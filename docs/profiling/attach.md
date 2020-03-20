---
title: 연결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 634169607a7d581de1b1332d78e8d5abde1a722e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773741"
---
# <a name="attach"></a>연결
*VSPerfCmd.exe* **Attach** 옵션은 PID(프로세스 ID)로 지정된 실행 중인 프로세스의 샘플 프로파일링을 시작합니다.

 **Attach** 옵션을 사용하려면 Start 옵션에서 **Sample** 메서드를 지정해야 합니다.

> [!NOTE]
> **Start** 옵션이 **Crosssession** 옵션으로 지정된 경우 **VSPerfCmd/Attach** 또는 **VSPerfCmd/Detach**에 대한 모든 호출은 **Crosssession**을 지정해야 합니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>매개 변수
 `ProcessID` 실행 중인 프로세스의 PID(프로세스 ID)입니다. 실행 중인 프로세스의 PID는 Windows 작업 관리자의 프로세스 탭에 나열됩니다.

## <a name="valid-options"></a>유효한 옵션
 다음 **VSPerfCmd** 옵션은 단일 명령줄에서 **Attach** 옵션과 함께 결합될 수 있습니다.

 **Crosssession** 로그온 세션 이외의 세션에서 프로파일링 애플리케이션을 활성화합니다. **Start** 옵션이 **Crosssession** 옵션으로 지정된 경우 필요합니다.

 **시작:** `Method` 명령줄 프로파일러 세션을 초기화하고 지정된 프로파일링 방법을 설정합니다.

 **TargetCLR** 프로파일링 세션에 두 개 이상의 버전이 로드된 경우 프로파일링할 .NET Framework CLR(공용 언어 런타임) 버전을 지정합니다. 기본적으로 첫 번째 로드된 버전이 프로파일링됩니다.

 **GlobalOn GlobalOff** 프로파일링을 다시 시작(**GlobalOn**)하거나 일시 중지(**GlobalOff**)하지만 프로파일링 세션을 종료하지 않습니다.

 **ProcessOn:** `PID` **ProcessOff:** `PID` 지정된 프로세스에 대한 프로파일링을 다시 시작(**ProcessOn**)하거나 일시 중지(**ProcessOff**)합니다.

## <a name="interval-options"></a>간격 옵션
 다음 샘플링 간격 옵션 중 하나를 Attach 명령줄에 지정할 수 있습니다. 기본 샘플링 간격은 10,000,000 프로세서 클록 주기입니다.

 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[<strong>:</strong>Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`] 샘플링 간격의 종류와 수를 지정합니다.

- **Timer** - 모든 `Cycles` 프로세서 클록 주기를 샘플링합니다. `Cycles`를 지정하지 않은 경우 10,000,000 주기가 사용됩니다.

- **PF** - 모든 `Events` 페이지 폴트를 샘플링합니다. `Events`가 지정되지 않은 경우 10 페이지 폴트가 사용됩니다.

- **Sys** - 운영 체제에 대한 모든 `Events` 호출을 샘플링합니다. `Events`가 지정되지 않은 경우 10 시스템 호출이 사용됩니다.

- **Counter** - `Name`에서 지정된 CPU 성능 카운터의 모든 `Reload` 수를 샘플링합니다. 필요에 따라 `FriendlyName`은 프로파일러 보고서의 열 헤더로 사용할 문자열을 지정할 수 있습니다.

## <a name="example"></a>예제
 이 예제에서는 12345의 프로세스 ID로 애플리케이션의 실행 중인 인스턴스에 연결하는 방법을 보여 줍니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>참조
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
