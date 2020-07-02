---
title: VSPerf | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8042b228a481dc3d720d8b422963db41abbddcd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533837"
---
# <a name="vsperf"></a>VSPerf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VsPerf** 명령줄 도구를 사용하면 다음을 수행할 수 있습니다.  
  
1. 디바이스에 Visual Studio가 설치되어 있지 않으면 명령줄에서 Windows 스토어 앱을 프로파일링합니다.  
  
2. 샘플링 프로파일링 방법을 사용하여 Windows 8 데스크톱 애플리케이션 및 Windows Server 2012 애플리케이션을 프로파일링합니다.  
  
   프로 파일링 옵션에 대한 자세한 내용은 [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용  
 이 항목에서는 `vsperf.exe` 명령줄 도구와 함께 사용할 수 있는 옵션에 대해 설명합니다. 이 항목에는 다음과 같은 단원이 포함되어 있습니다.  
  
 [Windows 스토어 앱만](#BKMK_windows_store_apps_only)  
  
 [Windows 8 데스크톱 애플리케이션 및 Windows Server 2012 애플리케이션 전용](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [모든 애플리케이션](#BKMK_All_applications)  
  
## <a name="windows-store-apps-only"></a><a name="BKMK_windows_store_apps_only"></a> Windows 스토어 앱 전용  
 이러한 옵션은 Windows 스토어 앱에만 적용됩니다.  
  
|옵션|설명|  
|-|-|  
|**/app:{AppName}**|프로파일러를 시작하고 지정한 앱이 시작 메뉴에서 시작될 때까지 기다립니다.<br /><br /> 설치된 앱의 앱 Name 및 PackageFullName을 보려면 `vsperf /listapps`를 실행합니다.|  
|**/package:{PackageFullName}**|프로파일러를 시작하고 지정한 앱이 시작 메뉴에서 시작될 때까지 기다립니다.<br /><br /> 설치된 앱의 앱 Name 및 PackageFullName을 보려면 `vsperf /listapps`를 실행합니다.|  
|**/js**|JavaScript 앱을 프로파일링하는 데 필요합니다.<br /><br /> JavaScript 앱에서 성능 데이터를 수집합니다.<br /><br /> /package 또는 /attach와 함께 사용해야 합니다.|  
|**/noclr**|선택 사항입니다. CLR 데이터를 수집하지 않습니다.<br /><br /> /package 또는 /attach와 함께 사용해야 합니다.<br /><br /> 최적화 상태이며 관리되는 기호를 확인하지 않습니다.|  
|**/listapps**|설치된 응용 프로그램 Name 및 PackageFullNames의 목록을 표시합니다.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a><a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a>Windows 8 데스크톱 응용 프로그램 및 Windows Server 2012 응용 프로그램에만 해당  
 이러한 옵션은 Windows 스토어 앱에서 작동하지 않습니다.  
  
|옵션|설명|  
|-|-|  
|**/launch:{Executable}**|지정한 실행 파일을 시작하고 프로파일링을 시작합니다.|  
|**/args:{ExecutableArguments}**|**/launch** 대상을 전달할 명령줄 인수를 지정합니다.|  
|**/console**|새 명령 창에서 **/launch** 대상을 실행합니다.|  
  
## <a name="all-applications"></a><a name="BKMK_All_applications"></a>모든 응용 프로그램  
 이러한 옵션은 모든 Windows 8 또는 Windows Server 2012 애플리케이션에 적용됩니다.  
  
|옵션|설명|  
|-|-|  
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|지정된 프로세스에서 데이터를 수집합니다.<br /><br /> 작업 관리자를 사용하여 실행 중인 앱의 PID(프로세스 ID) 및 프로세스 이름을 확인합니다.|  
|**/file:{ReportName}**|선택 사항입니다. 기존 파일을 덮어쓰는 출력 파일을 지정합니다.<br /><br /> /package 또는 /attach와 함께 사용해야 합니다.|  
|**/pause**|데이터 수집을 일시 중지합니다.|  
|**/resume**|데이터 수집을 다시 시작합니다.|  
|**/stop**|데이터 수집을 중지하고 대상 프로세스를 종료합니다.|  
|**/detach**|데이터 수집을 중지하되 대상 프로세스는 계속 실행되도록 합니다.|  
|**/status**|프로파일러 상태를 표시합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Windows 8 및 Windows Server 2012 응용 프로그램의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)
