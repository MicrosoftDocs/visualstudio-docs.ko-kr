---
title: Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a704215d-d252-4087-921b-ac81ebe2a9c9
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a2fa9581d94b3b70ca427c292c147562a11d55a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847992"
---
# <a name="performance-tools-on-windows-8-and-windows-server-2012-applications"></a>Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 성능 도구가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. 이 항목에서는 Windows 8 및 Windows Server 2012 플랫폼의 성능 도구 관련 변경 내용에 대해 설명합니다.  
  
> [!NOTE]
> 기타 지원되는 버전의 Windows(Windows 7, Windows Server 2008 R2)용 성능 도구는 변경되지 않았습니다.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용  
 [Visual Studio IDE에서 Windows 스토어 앱에 대 한 데이터 수집](#BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE)  
  
 [Visual Studio IDE에서 Windows 8 데스크톱 또는 Windows Server 2012에서 실행되는 앱에 대한 데이터 수집](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE)  
  
- [Visual Studio IDE에서 샘플링을 사용하여 Windows 8 데스크톱 또는 Windows Server 2012에서 실행되는 앱에 대한 데이터 수집](#BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE)  
  
  [명령줄에서 프로파일링](#BKMK_Profiling_from_the_command_line)  
  
  [TIP(계층 상호 작용) 데이터 수집](#BKMK_Collecting_tier_interaction__TIP__data)  
  
## <a name="collecting-data-on-windows-store-apps-from-the-visual-studio-ide"></a><a name="BKMK_Profiling_Windows_Store_apps_from_the_Visual_Studio_IDE"></a> Visual Studio IDE에서 Windows 스토어 앱에 대한 데이터 수집  
 JavaScript 및 HTML 5로 작성된 Windows 스토어 앱을 프로파일링하는 경우 JavaScript 코드에 대한 계측 데이터를 수집합니다. Visual C++, Visual C# 또는 Visual Basic으로 작성된 Windows 스토어 앱 또는 구성 요소를 프로파일링하는 경우 네이티브 코드 및 관리 코드에 대한 샘플링 데이터를 수집합니다. 로컬이나 원격 컴퓨터에서 앱을 프로파일링할 수 있습니다.  
  
 Windows 스토어 앱을 프로파일링하는 경우 다음 프로파일링 기능과 옵션은 지원되지 않습니다.  
  
- 샘플링 방법을 사용하여 JavaScript 앱 프로파일링  
  
- 계측 방법을 사용하여 관리 코드 및 네이티브 코드 프로파일링  
  
- 동시성 프로파일링  
  
- .NET 메모리 프로파일링  
  
- TIP(계층 상호 작용 프로파일링)  
  
- 샘플링 이벤트 및 타이밍 간격 설정 또는 추가 성능 카운터 데이터 수집과 같은 샘플링 옵션  
  
- 성능 및 Windows 카운터 데이터 수집 또는 추가 명령줄 옵션 지정과 같은 계측 옵션  
  
  Windows 스토어 앱을 프로파일링하는 방법에 대한 자세한 내용은 Windows 개발자 센터에서 다음 항목을 참조하세요.  
  
  [로컬 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-the-local-machine.md)  
  
  [원격 컴퓨터에서 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)  
  
  [앱 성능 분석](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
  
- [JavaScript 함수 타이밍](https://msdn.microsoft.com/library/b2bf49fc-aea7-4d9c-8fcf-cff8b8dd0c03)  
  
- [원격 장치의 JavaScript 함수 타이밍](https://msdn.microsoft.com/library/d78812b6-a97e-46dc-8d99-e724d1d725d8)  
  
- [JavaScript 함수 타이밍 데이터 분석](https://msdn.microsoft.com/library/b5aea8d8-36df-47ba-a7ca-95406700ca9b)  
  
- [로컬 컴퓨터의 Windows 스토어 앱에서 Visual C++, Visual C# 및 Visual Basic 코드 프로파일링](https://msdn.microsoft.com/2d0c939e-0bac-48c5-b727-46f6c6113060)  
  
- [원격 디바이스의 Windows 스토어 앱에서 Visual C++, Visual C# 및 Visual Basic 코드 프로파일링](https://msdn.microsoft.com/b932a2be-11b0-40fd-b996-75c6b6a79d22)  
  
- [Windows 스토어 앱의 Visual C++, Visual C# 및 Visual Basic 코드에 대한 성능 데이터 분석](https://msdn.microsoft.com/5de4a413-d924-425f-afc4-e1ecfb0fca18)  
  
  [항목 내용](#BKMK_In_this_topic)  
  
## <a name="collecting-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-from-the-visual-studio-ide"></a><a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_from_the_Visual_Studio_IDE"></a> Visual Studio IDE에서 windows 8 데스크톱 또는 Windows Server 2012를 실행 하는 앱에서 데이터 수집  
 Windows 8에서는 계측 방법을 사용한 프로파일링이 변경되지 않았습니다.  
  
 샘플링 방법을 사용한 TIP(계층 상호 작용 프로파일링)는 지원되지 않습니다.  
  
### <a name="collecting-data-on-apps-running-on-the-windows-8-desktop-or-on-windows-server-2012-by-using-sampling-from-the-visual-studio-ide"></a><a name="BKMK_Profiling_apps_running_on_the_Windows_8_desktop_or_on_Windows_Server_2012_by_using_sampling_from_the_Visual_Studio_IDE"></a> Visual Studio IDE에서 샘플링을 사용 하 여 Windows 8 데스크톱 또는 Windows Server 2012에서 실행 되는 앱에서 데이터 수집  
 샘플링 방법을 사용하여 Windows 8 데스크톱 애플리케이션 또는 Windows Server 2012 애플리케이션을 프로파일링하는 경우 다음 프로파일링 기능과 옵션은 지원되지 않습니다.  
  
- TIP(계층 상호 작용 프로파일링). 계측을 사용한 TIP 데이터 수집이 지원됩니다.  
  
- 샘플링 이벤트 및 타이밍 간격 설정 또는 추가 성능 카운터 데이터 수집과 같은 샘플링 옵션  
  
## <a name="profiling-from-the-command-line"></a><a name="BKMK_Profiling_from_the_command_line"></a> 명령줄에서 프로 파일링  
 다음 두 명령줄 도구를 사용하여 Visual Studio가 설치되지 않은 디바이스를 비롯한 Windows 8 및 Windows Server 2012 디바이스에서 프로파일링 데이터를 수집합니다.  
  
|도구 이름|설명|  
|---------------|-----------------|  
|[VSPerf](../profiling/vsperf.md)|Windows 스토어 앱에서 프로파일링 데이터를 수집하고 Windows 8 데스크톱 애플리케이션 및 Windows Server 2012 애플리케이션에서 샘플 프로파일링 데이터를 수집합니다.|  
|[VSPerfCmd](../profiling/vsperfcmd.md)|Windows 8 데스크톱 또는 Windows Server 2012에서 실행되는 앱에서 계측, 동시성 및 계층 상호 작용 프로파일링 데이터를 수집합니다. 이전 버전의 Windows에서 모든 유형의 프로파일링 데이터를 수집합니다.|  
  
 두 도구는 로컬 컴퓨터에서 사용하기 위해 Visual Studio와 함께 설치됩니다.  
  
 Visual Studio가 설치되지 않은 디바이스에서 애플리케이션을 프로파일링하려면 다음 중 하나를 수행합니다.  
  
- [MSDN 웹 사이트](https://www.microsoft.com/visualstudio/eng#downloads+d-additional-software)에서 Visual Studio용 원격 도구의 일부로 도구를 다운로드합니다.  
  
- Visual Studio 컴퓨터에서 독립 실행형 프로파일러 도구 설치 프로그램을 복사하여 실행합니다. 설치 프로그램은 *% VSInstallDir%* **\stoststststststststststystststyst** 원격 컴퓨터의 운영 체제(x86/x64)용 설치 프로그램을 선택합니다.  
  
> [!NOTE]
> TIP 프로파일링 데이터를 수집하려면 원격 컴퓨터에 Visual Studio 컴퓨터의 독립 실행형 프로파일러를 설치해야 합니다.  
  
 명령줄에서 Windows 8 및 Windows Server 2012 애플리케이션을 프로파일링하는 경우 다음 프로파일링 기능과 옵션은 지원되지 않습니다.  
  
- [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)와 함께 샘플링 모드를 사용하여 Windows 8 및 Windows Server 2012 웹앱에서 데이터 수집  
  
- VsPerfCmd.exe를 사용하여 샘플링 데이터 수집  
  
- 샘플링 이벤트 및 타이밍 간격 설정 또는 추가 성능 카운터 데이터 수집과 같은 샘플링 옵션  
  
## <a name="collecting-tier-interaction-tip-data"></a><a name="BKMK_Collecting_tier_interaction__TIP__data"></a> TIP (계층 상호 작용) 데이터 수집  
 상호 작용 프로파일링은 ADO.NET 서비스를 통해 데이터베이스와 통신하는 다중 계층 애플리케이션의 함수 실행 시간에 대한 추가 정보를 제공합니다. 동기 함수 호출에 대해서만 데이터가 수집됩니다.  
  
 **Visual Studio 버전**  
  
 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]또는 [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]을 사용하여 계층 상호 작용 프로파일링 데이터를 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 및 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]에서만 볼 수 있습니다.  
  
 **Windows 8 및 Windows Server 2012**  
  
1. Windows 8 데스크톱 또는 Windows Server 2012에서 실행되는 앱에서 계층 상호 작용 데이터를 수집하려면 계측 방법을 사용해야 합니다.  
  
2. Windows 스토어 앱에 대한 계층 상호 작용 데이터는 수집할 수 없습니다.  
  
3. 지원되는 다른 Windows 버전의 모든 프로파일링 방법에 계층 상호 작용 데이터를 포함할 수 있습니다.  
  
   **성능 마법사 및 성능 탐색기**  
  
   성능 탐색기에서 프로파일링 실행에 계층 상호 작용 데이터 수집 옵션을 추가해야 합니다. 또한 성능 탐색기의 대상 노드에 프로젝트, 실행 파일 또는 웹 사이트를 추가해야 합니다. [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)을 참조하세요.  
  
   **원격 컴퓨터에서 TIP 데이터 수집**  
  
   원격 컴퓨터에 대 한 계층 상호 작용 데이터를 수집 하려면 ** \_ \_ ** _\<Platform>_ **\_** _\<Language>_ Visual Studio 컴퓨터의 _% VSInstallDir%_**\team tooltoolss\ststoms** 폴더에 있는 vs profiler **.exe** 파일을 원격 컴퓨터에 복사 하 여 설치 해야 합니다. [Visual Studio 원격 도구](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 다운로드 패키지의 프로파일링 도구를 사용할 수 없습니다.  
  
   [VSPerfCmd](../profiling/vsperfcmd.md) 또는 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md)를 사용하여 프로파일링 데이터를 수집할 수 있습니다.  
  
   **TIP 보고서**  
  
   계층 상호 작용 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 또는 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] IDE에서만 볼 수 있습니다. [VSPerfReport](../profiling/vsperfreport.md) 를 통한 파일 기반 계층 상호 작용 보고서를 사용할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [성능 탐색기](../profiling/performance-explorer.md)   
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)
