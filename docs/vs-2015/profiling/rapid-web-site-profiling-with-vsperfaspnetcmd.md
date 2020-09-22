---
title: VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce5534f5723a3f0e570779939f207018cac71cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843323"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfASPNETCmd** 명령줄 도구를 사용하면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 쉽게 프로파일링할 수 있습니다. [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구와 비교하면 옵션 수가 더 적고, 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. 독립 실행형 프로파일러를 사용하여 프로파일링할 때는 기본적으로 **VSPerfASPNETCmd**를 사용합니다. 자세한 내용은 [방법: 독립 실행형 프로파일러 설치](../profiling/how-to-install-the-stand-alone-profiler.md)를 참조하세요.  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
 동시성 데이터를 수집하거나 프로파일링을 일시 중지했닫가 다시 시작하는 등의 일부 시나리오에서는 기본 프로파일링 방법으로 **VSPerfCmd**를 사용합니다.  
  
> [!NOTE]
> 프로파일링 도구의 명령줄 도구는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 설치 디렉터리의 \Team Tools\Performance Tools 하위 디렉터리에 있습니다. 64비트 컴퓨터의 경우 32 bit\Team Tools\Performance Tools 디렉터리에 있는 VSPerfASPNETCmd 도구를 사용합니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다. 자세한 내용은 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요.  
  
## <a name="profiling-an-aspnet-application"></a>ASP.NET 애플리케이션 프로파일링  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 프로파일링하려면 다음 섹션에서 설명하는 명령 중 하나를 입력합니다. 그러면 웹 사이트가 시작되고 프로파일러가 데이터 수집을 시작합니다. 애플리케이션을 사용한 후에 브라우저를 닫습니다. 프로파일링을 중지하려면 명령 프롬프트 창에서 Enter 키를 누릅니다.  
  
> [!NOTE]
> 기본적으로 명령 프롬프트는 **vsperfaspnetcmd** 명령을 실행한 후에 원래 상태로 돌아오지 않습니다. **/nowait** 옵션을 사용하면 명령 프롬프트가 원래 상태로 돌아오도록 강제 지정할 수 있습니다. [/NoWait 옵션 사용](#UsingNoWait)을 참조하세요.  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 애플리케이션 통계를 수집하려면  
 샘플링은 **VSPerfASPNETCmd** 도구의 기본 프로파일링 방법이며 명령줄에서 지정하지 않아도 됩니다. 다음 명령줄은 지정한 웹 애플리케이션에서 애플리케이션 통계를 수집합니다.  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 자세한 타이밍 데이터를 수집하려면  
 동적으로 컴파일된 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션에서 자세한 타이밍 데이터를 수집하려면 다음 명령줄을 사용합니다.  
  
 **vsperfaspnetcmd /trace**  *websiteUrl*  
  
 웹 응용 프로그램에서 정적으로 컴파일된 .dll 파일을 프로 파일링 하려면 [VSInstr](../profiling/vsinstr.md) 명령줄 도구를 사용 하 여 파일을 계측 해야 합니다. vsperfaspnetcmd /trace 명령을 실행하면 계측된 파일의 데이터가 포함됩니다.  
  
## <a name="to-collect-net-memory-data"></a>.NET 메모리 데이터를 수집하려면  
 **/Memory** 옵션을 사용하면 .NET 메모리의 개체 할당에 대한 데이터가 수집되며, 해당 개체의 수명에 대한 데이터를 수집할 수 있습니다. 할당 데이터 수집은 **/Memory** 데이터 옵션의 기본 모드이며 명령줄에서 지정하지 않아도 됩니다.  
  
 **vsperfaspnetcmd /memory** *websiteUrl*  
  
 할당 데이터와 함께 개체 수명 데이터를 수집하려면 **Lifetime** 매개 변수를 사용합니다.  
  
 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*  
  
 **/Trace** 옵션을 사용하여 .NET 메모리 데이터와 함께 자세한 타이밍 정보를 포함할 수도 있습니다.  
  
 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>계층 상호 작용 데이터를 수집하려면  
  
> [!WARNING]
> TIP(계층 상호 작용 프로파일) 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]을 사용해서 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] 및 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]에서만 볼 수 있습니다.  
>   
> Windows 8 또는 Windows Server 2012에서 TIP 데이터를 수집하려면 계측(**/trace**) 옵션을 사용해야 합니다.  
  
 샘플링 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.  
  
 **vsperfaspnetcmd /tip** `websiteUrl`  
  
 계측 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.  
  
 **vsperfaspnetcmd /trace /tip** *websiteUrl*  
  
 .NET 메모리 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.  
  
 **vsperfaspnetcmd/memory**[**: lifetime**] **/memory**_websiteUrl_  
  
## <a name="using-the-nowait-option"></a><a name="UsingNoWait"></a> /NoWait 옵션 사용  
 기본적으로 명령 프롬프트는 **vsperfaspnetcmd** 명령을 실행한 후에 원래 상태로 돌아오지 않습니다. 다음 구문 옵션을 사용하면 명령 프롬프트가 원래 상태로 돌아오도록 강제 지정할 수 있습니다. 그러면 명령 프롬프트 창에서 다른 작업을 수행할 수 있습니다. 프로파일링을 종료하려면 별도의 **vsperfaspnetcmd** 명령에서 **/shutdown** 옵션을 사용합니다.  
  
 프로파일링을 시작하려면 다음 명령을 사용합니다.  
  
 **vsperfaspnetcmd** [*/Options*] **/nowait**_websiteUrl_  
  
 프로파일링을 종료하려면 다음 명령을 사용합니다.  
  
 **vsperfaspnetcmd /shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>추가 옵션  
 **vsperfaspnetcmd /shutdown** 명령을 제외한 이 섹션 앞부분에 나와 있는 명령에 다음 옵션을 추가할 수 있습니다.  
  
|옵션|Description|  
|------------|-----------------|  
|**/Output:**`VspFile`|기본적으로는 현재 디렉터리에 파일 이름 **PerformanceReport.vsp**으로 프로파일링 데이터(.vsp) 파일이 만들어집니다. /output 옵션을 사용하면 다른 위치나 파일 이름 또는 둘 다를 지정할 수 있습니다.|  
|**/PackSymbols:Off**|VsPerfASPNETCmd는 기본적으로 .vsp 파일에 기호(함수 및 매개 변수 이름 등)를 포함합니다. 기호를 포함하면 프로파일링 데이터 파일이 매우 커질 수 있습니다. 데이터를 분석할 때 기호가 포함된 .pdb 파일에 액세스해야 하는 경우 /packsymbols:off 옵션을 사용하여 기호 포함을 사용하지 않도록 설정합니다.|
