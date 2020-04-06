---
title: '방법: 활동 로그 사용 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710576"
---
# <a name="how-to-use-the-activity-log"></a>방법: 활동 로그 사용
VSPackage는 활동 로그에 메시지를 쓸 수 있습니다. 이 기능은 소매 환경에서 VSPackage를 디버깅하는 데 특히 유용합니다.

> [!TIP]
> 활동 로그는 항상 켜져 있습니다. Visual Studio는 일반적인 구성 정보가 있는 처음 10개의 항목뿐만 아니라 마지막 100개의 항목의 롤링 버퍼를 유지합니다.

## <a name="to-write-an-entry-to-the-activity-log"></a>활동 로그에 항목을 작성하려면

1. VSPackage 생성자 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 제외 한 메서드 또는 다른 메서드에이 코드를 삽입 합니다.

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     이 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 서비스를 받고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스로 캐스팅합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>은 현재 문화적 컨텍스트를 사용하여 활동 로그에 정보 입력을 씁니다.

2. VSPackage가 로드되면(일반적으로 명령이 호출되거나 창이 열리는 경우) 텍스트가 활동 로그에 기록됩니다.

## <a name="to-examine-the-activity-log"></a>활동 로그를 검사하려면

1. [/Log](../ide/reference/log-devenv-exe.md) 명령줄 스위치를 사용하여 Visual Studio를 실행하여 세션 중에 ActivityLog.xml을 디스크에 씁니다.

2. Visual Studio를 닫은 후 Visual Studio 데이터의 하위 폴더에서 활동 로그를 찾습니다.

   <em> *%AppData%</em>\마이크로소프트\비주얼\\\<스튜디오 버전>\활동Log.xml*.

3. 텍스트 편집기에서 활동 로그를 엽니다. 다음은 일반적인 항목입니다.

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>강력한 프로그래밍

활동 로그는 서비스이므로 VSPackage 생성자에서 활동 로그를 사용할 수 없습니다.

쓰기 직전에 활동 로그를 가져와야 합니다. 나중에 사용할 수 위해 활동 로그를 캐시하거나 저장하지 마십시오.

## <a name="see-also"></a>참조

- [/log(devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [VSPackage 문제 해결](../extensibility/troubleshooting-vspackages.md)
- [VSPackage](../extensibility/internals/vspackages.md)
