---
title: '방법: 활동 로그 사용 Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 824feee64f928dc837a379aeb539daaa5ba0d1db
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905589"
---
# <a name="how-to-use-the-activity-log"></a>방법: 활동 로그 사용
Vspackage은 활동 로그에 메시지를 쓸 수 있습니다. 이 기능은 소매 환경에서 Vspackage를 디버깅 하는 데 특히 유용 합니다.

> [!TIP]
> 활동 로그는 항상 켜져 있습니다. Visual Studio는 일반 구성 정보를 포함 하는 처음 10 개 항목 뿐만 아니라 마지막 100 항목의 롤링 버퍼를 유지 합니다.

## <a name="to-write-an-entry-to-the-activity-log"></a>활동 로그에 항목을 쓰려면

1. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>VSPackage 생성자를 제외 하 고 메서드 또는 다른 메서드에이 코드를 삽입 합니다.

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     이 코드는 서비스를 가져와 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스로 캐스팅 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>현재 문화권 컨텍스트를 사용 하 여 활동 로그에 정보 항목을 씁니다.

2. VSPackage 로드 될 때 (일반적으로 명령이 호출 되거나 창이 열리면) 텍스트는 활동 로그에 기록 됩니다.

## <a name="to-examine-the-activity-log"></a>활동 로그를 검사 하려면

1. [/Log](../ide/reference/log-devenv-exe.md) 명령줄 스위치를 사용 하 여 Visual Studio를 실행 하 여 세션 중에 디스크에 ActivityLog.xml을 씁니다.

2. Visual Studio를 닫은 후 Visual Studio 데이터의 하위 폴더에서 활동 로그를 찾습니다.

   <em> *% AppData%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. 텍스트 편집기를 사용 하 여 활동 로그를 엽니다. 일반적인 항목은 다음과 같습니다.

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>강력한 프로그래밍

활동 로그는 서비스 이므로 활동 로그는 VSPackage 생성자에서 사용할 수 없습니다.

활동 로그에 쓰기 전에 활동 로그를 가져와야 합니다. 나중에 사용 하기 위해 활동 로그를 캐시 하거나 저장 하지 마십시오.

## <a name="see-also"></a>참조

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [VSPackage 문제 해결](../extensibility/troubleshooting-vspackages.md)
- [VSPackage](../extensibility/internals/vspackages.md)
