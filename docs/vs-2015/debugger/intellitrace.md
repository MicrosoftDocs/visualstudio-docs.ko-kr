---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c379054506672f36368b6da99c40a0a75a25e0ac
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543925"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전은 [IntelliTrace](/visualstudio/debugger/intellitrace) 에서 찾을 수 있습니다.  
  
IntelliTrace를 사용하여 코드의 실행 내역을 기록하고 추적하면 애플리케이션 디버깅에 사용되는 시간을 줄일 수 있습니다. IntelliTrace를 사용하면 다음이 가능하므로 손쉽게 버그를 찾을 수 있습니다.  
  
- 특정 이벤트 기록  
  
   디버거 이벤트 중 **지역** 창에 표시되는 관련 코드와 데이터 및 함수 호출 정보 검사  
  
- 재현하기 어렵거나 배포에서 발생하는 오류 디버그  
  
  Visual Studio Enterprise Edition(Professional 또는 Community Edition 아님)에서 IntelliTrace를 사용할 수 있습니다.  
  
## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.  
  
|시나리오|문서|  
|-|-|  
|**IntelliTrace를 사용하여 애플리케이션 디버그:**<br /><br /> -이전 이벤트를 표시 합니다.<br />-이전 이벤트와 함께 통화 정보를 표시 합니다.<br />-IntelliTrace 세션을 저장 합니다.<br />-IntelliTrace에서 수집 하는 데이터를 제어 합니다.|-   [연습: IntelliTrace 사용](../debugger/walkthrough-using-intellitrace.md)<br />     [IntelliTrace 기능](../debugger/intellitrace-features.md)<br />-   [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [기록 디버깅](../debugger/historical-debugging.md)|  
|**Test Manager에서 테스트 세션 동안 IntelliTrace 데이터 수집**|-   [수동 테스트에서 추가 진단 데이터 수집](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**배포된 애플리케이션에서 IntelliTrace 데이터 수집**|-   [IntelliTrace 독립 실행형 수집기 사용](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**IntelliTrace 로그 파일(.iTrace 파일)에서 디버깅 시작**|-   [저장된 IntelliTrace 데이터 사용](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a> IntelliTrace를 사용하여 어떤 앱을 디버깅할 수 있나요?  
  
|지원 수준|앱 유형|  
|-|-|  
|**지원됨**|-Visual Basic 및 .NET Framework 2.0 이상 버전을 사용 하는 Visual c # 응용 프로그램입니다.<br />     ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 및 64비트 앱을 포함한 대부분의 애플리케이션을 디버깅할 수 있습니다.<br />     IntelliTrace를 사용하여 SharePoint 애플리케이션을 디버그하려면 [연습: IntelliTrace를 사용하여 SharePoint 애플리케이션 디버그](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)를 참조하세요.<br />     IntelliTrace를 사용하여 Microsoft Azure 앱을 디버그하려면 [IntelliTrace 및 Visual Studio를 사용하여 게시된 클라우드 서비스 디버그](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)를 참조하세요.|  
|**제한적 지원**|-실험 기반의 F # 앱<br />-이벤트 전용으로 지원 되는 Windows 스토어 앱|  
|**지원되지 않음**|-C + +, 다른 언어 및 스크립트<br />-Windows 서비스, Silverlight, Xbox 또는 [!INCLUDE[winmobile](../includes/winmobile-md.md)] 앱|  
  
> [!NOTE]
> 이미 실행 중인 프로세스를 디버깅하는 경우 IntelliTrace를 사용할 수 없습니다. 프로세스를 시작할 때 IntelliTrace를 시작해야 합니다.  
  
## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> IntelliTrace로 디버깅하는 이유는 무엇인가요?  
 전통적인 디버깅이나 ‘라이브’ 디버깅은 이전 이벤트에 대해 제한된 데이터를 사용하여 애플리케이션의 현재 상태만 보여 줍니다. 애플리케이션의 현재 상태를 기반으로 이러한 이벤트를 유추하거나 애플리케이션을 다시 실행하여 이러한 이벤트를 다시 만들어야 합니다.  
  
 IntelliTrace는 이러한 시점에 특정 이벤트와 데이터를 기록하여 전통적인 디버깅 경험을 확장합니다. 이렇게 하면 특히 버그가 발생한 위치를 지나친 경우 애플리케이션을 다시 시작하지 않고 어떤 일이 발생했는지 확인할 수 있습니다. IntelliTrace는 전통적인 디버깅 중에 기본적으로 켜지며 데이터를 표시하지 않고 자동으로 수집합니다. 이렇게 하면 전통적인 디버깅과 IntelliTrace 디버깅 사이를 쉽게 전환하여 기록된 정보를 볼 수 있습니다. [IntelliTrace 기능](../debugger/intellitrace-features.md) 및 [IntelliTrace에서 수집하는 데이터는 무엇입니까?](#WhatData)를 참조하세요.  
  
 IntelliTrace는 재현하기 어렵거나 배포할 때 발생하는 오류를 디버깅할 수도 있습니다. IntelliTrace 데이터를 수집하고 IntelliTrace 로그 파일(.iTrace 파일)에 저장할 수 있습니다. .iTrace 파일은 예외, 성능 이벤트, 웹 요청, 테스트 데이터, 스레드, 모듈 및 기타 시스템 정보에 대한 세부 정보를 포함하고 있습니다. Visual Studio Enterprise에서 이 파일을 열고 항목을 선택하고 IntelliTrace를 사용하여 디버깅을 시작할 수 있습니다. 이렇게 하면 파일에 있는 이벤트로 이동하여 해당 시점의 애플리케이션에 대한 특정 정보를 볼 수 있습니다.  
  
 다음 소스의 IntelliTrace 데이터를 저장할 수 있습니다.  
  
- Visual Studio 2015 Enterprise 또는 이전 버전의 Visual Studio Ultimate에 IntelliTrace 세션이 있습니다.  
  
- Microsoft Test Manager의 테스트 세션  
  
- Microsoft Monitoring Agent 단독으로 또는 System Center 2012와 함께 사용할 때 IIS에서 호스팅된 ASP.NET 웹 앱 또는 배포에서 실행 중인 SharePoint 2010 및 SharePoint 2013 애플리케이션. [IntelliTrace 독립 실행형 수집기 사용](../debugger/using-the-intellitrace-stand-alone-collector.md) 및 [Microsoft Monitoring Agent로 모니터링](https://technet.microsoft.com/library/dn465153.aspx)을 참조 하세요.  
  
  다음은 IntelliTrace를 이용하여 디버깅하는 몇 가지 예입니다.  
  
- 애플리케이션의 데이터 파일이 손상되었지만 이 이벤트가 어디에서 발생했는지 모릅니다.  
  
   이 경우 IntelliTrace를 사용하지 않는다면 코드 전체를 검사하여 가능한 모든 파일 액세스를 찾고, 해당 액세스 지점에 중단점을 설정한 다음, 애플리케이션을 다시 실행하여 문제가 발생하는 지점을 찾아야 합니다. IntelliTrace를 사용하면 수집된 모든 파일 액세스 이벤트와 각 이벤트가 발생했을 때 애플리케이션에 대한 특정 세부 사항을 볼 수 있습니다.  
  
- 예외가 발생합니다.  
  
   IntelliTrace가 없으면 예외에 대한 메시지가 표시되지만 예외를 일으킨 이벤트에 대한 많은 정보를 갖지 못하게 됩니다. 호출 스택을 검사하여 예외를 초래한 호출 체인을 확인할 수 있지만 이러한 호출 중 발생한 이벤트 시퀀스는 확인할 수 없습니다. IntelliTrace를 사용하면 예외가 발생하기 전에 발생한 이벤트를 검사할 수 있습니다.  
  
- 애플리케이션이 테스트 컴퓨터에서 충돌하더라도 개발 컴퓨터에서는 성공적으로 실행됩니다.  
  
   Microsoft Test Manager에서 IntelliTrace 데이터를 수집하고 데이터를 .iTrace 파일에 저장하며 이 파일을 향후 조사를 위해 Team Foundation Server 작업 항목에 첨부할 수 있습니다. [수동 테스트에서 추가 진단 데이터 수집](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) 및 [저장 된 IntelliTrace 데이터 사용](../debugger/using-saved-intellitrace-data.md)을 참조 하세요.  
  
- 배포된 애플리케이션에서 버그 또는 충돌이 발생합니다.  
  
   Microsoft Azure 기반 애플리케이션의 경우 애플리케이션을 게시하기 전에 IntelliTrace 데이터 수집을 구성할 수 있습니다. 애플리케이션을 실행하는 동안 IntelliTrace는 데이터를 .iTrace 파일에 저장합니다. [IntelliTrace 및 Visual Studio를 사용하여 게시된 클라우드 서비스 디버깅](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)을 참조하세요.  
  
   IIS 7.0, 7.5 및 8.0에서 호스팅된 ASP.NET 웹 앱과 SharePoint 2010 또는 SharePoint 2013 애플리케이션에 대해 Microsoft Monitoring Agent 단독으로 또는 System Center 2012와 함께 사용하여 IntelliTrace 데이터를 .iTrace 파일에 저장합니다.  
  
   배포에서 응용 프로그램의 문제를 진단할 때 유용합니다. [IntelliTrace 독립 실행형 수집기 사용](../debugger/using-the-intellitrace-stand-alone-collector.md)을 참조하세요.  
  
## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> IntelliTrace에서 수집하는 데이터는 무엇인가요?  
 **이벤트 정보 수집**  
  
 기본적으로 IntelliTrace는 디버거 이벤트, 예외, .NET Framework 이벤트와 같은 IntelliTrace 이벤트와 디버깅에 유용한 기타 시스템 이벤트만 기록합니다. 항상 수집되는 디버거 이벤트와 예외를 제외하고 수집하려는 IntelliTrace 이벤트 종류를 선택할 수 있습니다. [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)을 참조 하세요.  
  
- **디버거 이벤트**  
  
   IntelliTrace는 Visual Studio 디버거에서 발생하는 이벤트는 항상 기록합니다. 예를 들어, 애플리케이션 시작은 디버거 이벤트입니다. 다른 디버거 이벤트로는 애플리케이션의 실행을 중단시키는 중지 이벤트가 있습니다. 예를 들어, 프로그램이 중단점이나 추적점에 도달하거나, **단계** 명령을 실행합니다.  
  
   성능을 위해 IntelliTrace는 디버거 이벤트에 대한 모든 값을 가능하면 기록하지 않습니다. 대신, 다음 값을 기록합니다.  
  
  - **지역** 창의 값. 이러한 값을 보려면 **지역** 창을 열어 둡니다.  
  
  - **자동** 창이 열려 있는 경우에 한해 **자동** 창의 값  
  
  - 해당 값을 보기 위해 소스 창에 있는 변수 위로 마우스 포인터를 이동하면 나타나는 DataTips의 값입니다. IntelliTrace는 고정된 DataTips에서는 값을 수집하지 않습니다.  
  
- **예외**  
  
   IntelliTrace에서는 이러한 종류의 예외에 대한 예외 형식과 메시지를 기록합니다.  
  
  - 예외가 throw되고 catch된 경우의 처리된 예외  
  
  - 처리되지 않은 예외  
  
- **.NET Framework 이벤트**  
  
   기본적으로 IntelliTrace는 가장 일반적인 .NET Framework 이벤트를 기록합니다. 예를 들면 다음과 같습니다.  
  
  - 파일 액세스 이벤트의 경우 IntelliTrace가 파일 이름을 수집합니다.  
  
  - 확인란 확인 이벤트의 경우 IntelliTrace는 확인란 상태와 텍스트를 수집합니다.  
  
- **SharePoint 2010 및 SharePoint 2013 애플리케이션 이벤트**  
  
   Visual Studio 외부에서 실행되는 SharePoint 2010 및 2013 애플리케이션에 대해 사용자 프로필 이벤트 및 ULS(Unified Logging System) 이벤트의 하위 집합을 기록할 수 있습니다. 이러한 이벤트를 .iTrace 파일에 저장할 수 있습니다. Visual Studio Enterprise 2015, 이전 버전의 Visual Studio Ultimate 또는 **추적** 모드에서 실행 되는 [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771) 가 필요 합니다.  
  
   .iTrace 파일을 열면 SharePoint 상관 관계 ID를 입력하여 일치하는 웹 요청을 찾고 기록된 이벤트를 보고 특정 이벤트에서 디버깅을 시작합니다. 파일에 처리되지 않은 예외가 있는 경우 상관 관계 ID를 선택하여 예외 디버깅을 시작할 수 있습니다.  
  
   참조  
  
  - [IntelliTrace 독립 실행형 수집기 사용](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [저장된 IntelliTrace 데이터 사용](../debugger/using-saved-intellitrace-data.md)  
  
  - [연습: IntelliTrace를 사용하여 SharePoint 애플리케이션 디버그](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **함수 호출 정보 수집**  
  
  함수의 호출 정보를 수집하도록 IntelliTrace를 구성할 수 있습니다. 이 정보를 사용하면 호출 스택의 내역을 확인하고 코드에 있는 호출을 통해 뒤로/앞으로 이동할 수 있습니다. 각 함수 호출에 대해 IntelliTrace는 이 데이터를 기록합니다.  
  
- 함수 이름  
  
- 함수 시작 지점에서 매개 변수로 전달하고 함수 종료 지점에서 반환되는 기본 데이터 형식의 값  
  
- 읽히거나 변경될 때의 자동 속성 값  
  
- 첫 번째 수준 자식 개체에 대한 포인터, null인지 여부만을 나타내며 해당 값에 대한 포인터는 아님  
  
> [!NOTE]
> IntelliTrace는 배열에서 처음 256 개체와 문자열의 경우 처음 256자만 수집합니다.  
  
 [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)을 참조 하세요.  
  
 **모듈 정보 수집**  
  
 IntelliTrace가 호출 정보를 어느 정도 수집할지 제어하려면 관심 있는 모듈만 지정합니다. 이와 같이 하면 컬렉션하는 동안 애플리케이션 성능을 향상시킬 수 있습니다. [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)을 참조 하세요.  
  
## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace가 애플리케이션 속도를 저하시키나요?  
 기본적으로 IntelliTrace에서는 선택한 IntelliTrace 이벤트에 대해서만 데이터를 수집합니다. 코드의 구조와 구성에 따라 애플리케이션이 느려지거나 느려지지 않을 수 있습니다. 예를 들어 IntelliTrace가 자주 이벤트를 기록한다면 이로 인해 애플리케이션 속도가 느려질 수 있습니다. 또한 이에 따라 애플리케이션 리팩터링을 고려해 볼 수도 있습니다.  
  
 호출 정보를 수집하면 애플리케이션 성능이 크게 느려질 수 있습니다. 디스크에 저장하는 경우 IntelliTrace 로그 파일(.iTrace 파일)의 크기도 증가할 수 있습니다. 이러한 효과를 최소화하려면 관심 있는 모듈에 대한 호출 정보만 수집합니다.  .iTrace 파일의 최대 크기를 변경하려면 **도구**, **옵션**, **IntelliTrace**, **고급**으로 이동합니다. [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)을 참조 하세요.  
  
## <a name="in-this-section"></a>단원 내용  
 [IntelliTrace 기능](../debugger/intellitrace-features.md)  
  
 [IntelliTrace 구성](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [재현하기 어려운 버그에 진단 추적 데이터 포함](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [배포 후 문제 진단](../debugger/diagnose-problems-after-deployment.md)  
  
 [저장된 IntelliTrace 데이터 사용](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>블로그  
 [Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)  
  
### <a name="forums"></a>포럼  
 [Visual Studio 진단](https://social.msdn.microsoft.com/Forums/vsdebug)
