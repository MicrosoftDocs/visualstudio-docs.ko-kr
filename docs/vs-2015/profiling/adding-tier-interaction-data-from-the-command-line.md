---
title: 명령줄에서 계층 상호 작용 데이터 추가 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 369c5b75780e9d557dedbde60b5b584c8b3345b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705841"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>명령줄에서 계층 상호 작용 데이터 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

계층 상호 작용 프로파일링은 하나 이상의 데이터베이스와 통신하는 다중 계층 애플리케이션의 함수에서 동기 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 호출의 실행 시간에 대한 추가 정보를 제공합니다.  
  
 **Windows 8 및 Windows Server 2012**  
  
 Windows 8 데스크톱 앱 및 Windows Server 2012 앱에서 계층 상호 작용 데이터를 수집하려면 계측 방법을 사용해야 합니다. Windows 스토어 앱에서 계층 상호 작용 데이터를 수집하는 것은 지원되지 않습니다.  
  
 **Visual Studio 버전**  
  
 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]를 사용하여 계층 상호 작용 프로파일링을 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 및 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]에서만 볼 수 있습니다.  
  
 **원격 컴퓨터에서 TIP 데이터 수집**  
  
 원격 컴퓨터에 대 한 계층 상호 작용 데이터를 수집 하려면 ** \_ \_ ** _\<Platform>_ **\_** _\<Language>_ Visual Studio 컴퓨터의 _% VSInstallDir%_**\team tooltoolss\ststoms** 폴더에 있는 vs profiler **.exe** 파일을 원격 컴퓨터에 복사 하 여 설치 해야 합니다. [Visual Studio 원격 도구](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) 다운로드 패키지의 프로파일링 도구를 사용할 수 없습니다.  
  
 **TIP 보고서**  
  
 계층 상호 작용 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] IDE에서만 볼 수 있습니다. [VSPerfReport](../profiling/vsperfreport.md)를 통한 파일 기반 계층 상호 작용 보고서를 사용할 수 없습니다.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>VSPerfCmd를 사용하여 계층 상호 작용 데이터 추가  
 VSPerfASPNETCmd 명령줄 도구를 사용하면 프로파일링 도구에서 사용할 수 있는 전체 기능에 액세스할 수 있습니다. VSPerfCmd를 사용하여 수집된 프로파일링 데이터에 계층 상호 작용을 추가하려면 **VSPerfCLREnv** 유틸리티를 사용하여 계층 상호 작용 데이터를 사용하도록 설정하는 환경 변수를 설정 및 제거해야 합니다. 지정하는 옵션 및 데이터 수집에 필요한 절차는 프로파일링하는 애플리케이션의 유형에 따라 다릅니다.  
  
### <a name="profiling-stand-alone-applications"></a>독립 실행형 애플리케이션 프로파일링  
 SQLServer 데이터베이스에 대해 동기 [!INCLUDE[vstecado](../includes/vstecado-md.md)] 호출을 수행하는 Windows 데스크톱 애플리케이션과 같이 다른 프로세스에 의해 실행되지 않는 애플리케이션에 계층 상호 작용 데이터를 추가하려면 **VSPerfClrEnv /InteractionOn** 옵션을 사용하여 환경 변수를 설정하고 **VSPerfClrEnv /InteractionOff** 옵션을 사용하여 제거합니다.  
  
 다음 예제에서는 계측 방법을 사용하여 Windows 데스크톱 애플리케이션을 프로파일링하고 계층 상호 작용 데이터를 수집합니다.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Windows 데스크톱 애플리케이션 예제 프로파일링  
  
1. 관리자 권한으로 명령 프롬프트 창을 엽니다. **시작**을 클릭하고 **모든 프로그램**, **보조 프로그램**을 차례로 가리킵니다. **명령 프롬프트**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.  
  
2. .NET 프로파일링 및 TIP 환경 변수를 초기화합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfclrenv /traceon  
   vsperfclrenv /interactionon  
   ```  
  
3. 프로파일러를 시작합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfcmd /start:trace /output:Desktop_tip.vsp   
   ```  
  
4. VSPerfCmd로 애플리케이션을 시작합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfcmd /launch:DesktopApp.exe  
   ```  
  
5. 애플리케이션을 실행하여 프로파일링 데이터를 수집한 다음 정상적인 방법으로 애플리케이션을 닫습니다.  
  
6. TIP 환경 변수를 지웁니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfclrenv /off  
   ```  
  
   자세한 내용은 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)을 참조 하세요.  
  
### <a name="profiling-services"></a>서비스 프로파일링  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 포함하여 서비스를 프로파일링하려면 **VSPerfClrEnv /GlobalInteractionOn** 옵션을 사용하여 환경 변수를 설정하고 **VSPerfClrEnv /GlobalInteractionOff** 옵션을 사용하여 제거합니다.  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 포함하여 서비스를 프로파일링하는 경우, 프로파일링을 사용하도록 설정하기 위해 컴퓨터를 자주 다시 시작해야 합니다.  
  
 다음 예제에서는 계측 방법을 사용하여 Windows 서비스를 프로파일링하고 계층 상호 작용 데이터를 수집합니다.  
  
##### <a name="profiling-a-windows-service-example"></a>Windows 서비스 프로파일링 예제  
  
1. 필요한 경우 서비스를 설치합니다.  
  
2. 관리자 권한으로 명령 프롬프트 창을 엽니다. **시작**을 클릭하고 **모든 프로그램**, **보조 프로그램**을 차례로 가리킵니다. **명령 프롬프트**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.  
  
3. .NET 프로파일링 환경 변수를 초기화합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfclrenv /globaltraceon  
   ```  
  
4. TIP 환경 변수를 초기화합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfclrenv /globalinteractionon  
   ```  
  
5. 환경 변수를 등록하기 위해 컴퓨터를 다시 시작합니다.  
  
6. 관리자 권한으로 명령 프롬프트 창을 엽니다.  
  
7. 프로파일러를 시작합니다. 다음 명령을 입력합니다.  
  
   ```  
   vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
   ```  
  
8. 필요한 경우 서비스를 시작합니다.  
  
9. 프로파일러를 서비스에 연결합니다. 다음 명령을 입력합니다.  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. 서비스를 실행하고 프로파일링 데이터를 수집합니다.  
  
11. 프로파일러를 중지합니다. 다음 명령을 입력합니다.  
  
     `vsperfcmd /detach`  
  
12. .NET 및 TIP 프로파일링 환경 변수를 지웁니다. 다음 명령을 입력합니다.  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. 지운 환경 변수를 등록하기 위해 컴퓨터를 다시 시작합니다.  
  
    자세한 내용은 다음 항목 중 하나를 참조하십시오.  
  
    [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
    [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd를 사용하여 계층 상호 작용 데이터 추가  
 VSPerfASPNETCmd 명령줄 도구를 사용하면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 손쉽게 프로파일링할 수 있습니다. **VSPerfCmd** 명령줄 도구와 비교하면 옵션 수가 더 적고, 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. VSPerfASPNETCmd의 이러한 기능 덕분에 계층 상호 작용 데이터를 매우 쉽게 수집할 수 있습니다.  
  
 VSPerfASPNETCmd를 사용하여 수집한 프로파일링 데이터에 계층 상호 작용을 추가하려면 명령줄에 **/TIP** 옵션을 추가합니다. 예를 들어 계측 방법을 사용하여 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션에 대한 계층 상호 작용 데이터를 수집하려면 다음 명령줄을 사용합니다.  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 VSPerfASPNETCmd에 대 한 자세한 내용은 [VSPerfASPNETCmd로 신속한 웹 사이트 프로 파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)을 참조 하세요.
