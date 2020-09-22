---
title: '방법: 활동 로그 사용 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842099"
---
# <a name="how-to-use-the-activity-log"></a>방법: 활동 로그 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage은 활동 로그에 메시지를 쓸 수 있습니다. 이 기능은 소매 환경에서 Vspackage를 디버깅 하는 데 특히 유용 합니다.  
  
> [!TIP]
> 활동 로그는 항상 켜져 있습니다. Visual Studio는 마지막 100 항목 뿐만 아니라 일반 구성 정보가 있는 처음 10 개 항목의 롤링 버퍼를 유지 합니다.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>활동 로그에 항목을 쓰려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>VSPackage 생성자를 제외 하 고 메서드 또는 다른 메서드에이 코드를 삽입 합니다.  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     이 코드는 서비스를 가져와 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스로 캐스팅 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 현재 문화권 컨텍스트를 사용 하 여 활동 로그에 정보 항목을 씁니다.  
  
2. VSPackage 로드 될 때 (일반적으로 명령이 호출 되거나 창이 열리면) 텍스트는 활동 로그에 기록 됩니다.  
  
### <a name="to-examine-the-activity-log"></a>활동 로그를 검사 하려면  
  
1. Visual Studio 데이터의 하위 폴더에서 활동 로그를 찾습니다. *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML.  
  
2. 텍스트 편집기를 사용 하 여 활동 로그를 엽니다. 일반적인 항목은 다음과 같습니다.  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 활동 로그는 서비스 이므로 활동 로그는 VSPackage 생성자에서 사용할 수 없습니다.  
  
 활동 로그에 쓰기 전에 활동 로그를 가져와야 합니다. 나중에 사용 하기 위해 활동 로그를 캐시 하거나 저장 하지 마십시오.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Vspackage 문제 해결](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
