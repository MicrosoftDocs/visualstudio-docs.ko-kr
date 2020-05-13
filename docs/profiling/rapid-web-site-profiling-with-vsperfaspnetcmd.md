---
title: VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fff2486c4197cbbe28c3b5deb0099e264805e12b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771694"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링

**VSPerfASPNETCmd** 명령줄 도구를 사용하면 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 손쉽게 프로파일링할 수 있습니다. [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구와 비교하면 옵션 수가 더 적고, 환경 변수를 설정할 필요가 없으며, 컴퓨터를 다시 부팅하지 않아도 됩니다. 독립 실행형 프로파일러를 사용하여 프로파일링할 때는 기본적으로 **VSPerfASPNETCmd**를 사용합니다. 자세한 내용은 [방법: 독립 실행형 프로파일러 설치](../profiling/how-to-install-the-stand-alone-profiler.md)를 참조하세요.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

 동시성 데이터를 수집하거나 프로파일링을 일시 중지했닫가 다시 시작하는 등의 일부 시나리오에서는 기본 프로파일링 방법으로 **VSPerfCmd**를 사용합니다.

> [!NOTE]
> 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

## <a name="profile-an-aspnet-application"></a>ASP.NET 애플리케이션 프로파일링

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션을 프로파일링하려면 다음 섹션에서 설명하는 명령 중 하나를 입력합니다. 그러면 웹 사이트가 시작되고 프로파일러가 데이터 수집을 시작합니다. 애플리케이션을 사용한 후에 브라우저를 닫습니다. 프로파일링을 중지하려면 명령 프롬프트 창에서 **Enter** 키를 누릅니다.

> [!NOTE]
> 기본적으로 명령 프롬프트는 **vsperfaspnetcmd** 명령을 실행한 후에 원래 상태로 돌아오지 않습니다. **/nowait** 옵션을 사용하면 명령 프롬프트가 원래 상태로 돌아오도록 강제 지정할 수 있습니다. [/NoWait 옵션 사용](#use-the-nowait-option)을 참조하세요.

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 애플리케이션 통계를 수집하려면
 샘플링은 **VSPerfASPNETCmd** 도구의 기본 프로파일링 방법이며 명령줄에서 지정하지 않아도 됩니다. 다음 명령줄은 지정한 웹 애플리케이션에서 애플리케이션 통계를 수집합니다.

 **vsperfaspnetcmd**  *websiteUrl*

 로컬 서버에 호스트된 *websiteUrl*의 예로는 *http://localhost/MySite/default.aspx* 를 들 수 있습니다. 외부 사이트의 예로는 *http://www.contoso.com* 이 있습니다. 자세한 내용은 [Visual Studio에서 프로젝트를 열지 않고 웹 사이트를 프로파일링하는 방법](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio)에서 예제 URL을 참조하세요.

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 자세한 타이밍 데이터를 수집하려면

동적으로 컴파일된 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션에서 자세한 타이밍 데이터를 수집하려면 다음 명령줄을 사용합니다.

**vsperfaspnetcmd /trace**  *websiteUrl*

웹 애플리케이션에서 정적으로 컴파일된 .*dll* 파일을 프로파일링하려는 경우에는 [VSInstr](../profiling/vsinstr.md) 명령줄 도구를 사용하여 파일을 계측해야 합니다. vsperfaspnetcmd /trace 명령을 실행하면 계측된 파일의 데이터가 포함됩니다.

## <a name="to-collect-net-memory-data"></a>.NET 메모리 데이터를 수집하려면

**/Memory** 옵션을 사용하면 .NET 메모리의 개체 할당에 대한 데이터가 수집되며, 해당 개체의 수명에 대한 데이터를 수집할 수 있습니다. 할당 데이터 수집은 **/Memory** 데이터 옵션의 기본 모드이며 명령줄에서 지정하지 않아도 됩니다.

 **vsperfaspnetcmd /memory** *websiteUrl*

 할당 데이터와 함께 개체 수명 데이터를 수집하려면 **Lifetime** 매개 변수를 사용합니다.

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 **/Trace** 옵션을 사용하여 .NET 메모리 데이터와 함께 자세한 타이밍 정보를 포함할 수도 있습니다.

 **vsperfaspnetcmd /memory**[ **:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>계층 상호 작용 데이터를 수집하려면

> [!WARNING]
> TIP(계층 상호 작용 프로파일링) 데이터는 Visual Studio의 모든 버전을 사용하여 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 Visual Studio Enterprise에서만 볼 수 있습니다.
>
> Windows 8 또는 Windows Server 2012에서 TIP 데이터를 수집하려면 계측( **/trace**) 옵션을 사용해야 합니다.

샘플링 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.

**vsperfaspnetcmd /tip** `websiteUrl`

계측 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.

**vsperfaspnetcmd /trace /tip** *websiteUrl*

.NET 메모리 데이터와 함께 계층 상호 작용 데이터를 수집하려면 다음 명령을 사용합니다.

**vsperfaspnetcmd /memory**[ **:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>/NoWait 옵션 사용

기본적으로 명령 프롬프트는 **vsperfaspnetcmd** 명령을 실행한 후에 원래 상태로 돌아오지 않습니다. 다음 구문 옵션을 사용하면 명령 프롬프트가 원래 상태로 돌아오도록 강제 지정할 수 있습니다. 그러면 명령 프롬프트 창에서 다른 작업을 수행할 수 있습니다. 프로파일링을 종료하려면 별도의 **vsperfaspnetcmd** 명령에서 **/shutdown** 옵션을 사용합니다.

프로파일링을 시작하려면 다음 명령을 사용합니다.

**vsperfaspnetcmd** [ */Options*] **/nowait**_websiteUrl_

프로파일링을 종료하려면 다음 명령을 사용합니다.

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>추가 옵션

**vsperfaspnetcmd /shutdown** 명령을 제외한 이 섹션 앞부분에 나와 있는 명령에 다음 옵션을 추가할 수 있습니다.

|옵션|설명|
|------------|-----------------|
|**/Output:** `VspFile`|기본적으로는 현재 디렉터리에 파일 이름 **PerformanceReport.vsp**로 프로파일링 데이터(.*vsp*) 파일이 만들어집니다. /output 옵션을 사용하면 다른 위치나 파일 이름 또는 둘 다를 지정할 수 있습니다.|
|**/PackSymbols:Off**|VsPerfASPNETCmd는 기본적으로 .*vsp* 파일에 기호(함수 및 매개 변수 이름 등)를 포함합니다. 기호를 포함하면 프로파일링 데이터 파일이 매우 커질 수 있습니다. 데이터를 분석할 때 기호가 포함된 .*pdb* 파일에 액세스해야 하는 경우 /packsymbols:off 옵션을 사용하여 기호 포함을 사용하지 않도록 설정합니다.|
