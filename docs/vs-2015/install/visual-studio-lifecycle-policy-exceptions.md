---
title: Visual Studio 수명 주기 정책 예외 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cc3a18fe1ce76b6214766ba45fc5441e80c56cef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918483"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Visual Studio 수명 주기 정책 예외
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에는 여러 Microsoft 플랫폼에 대한 개발을 가능하게 하는 컴파일러, 언어, 런타임, 환경 및 기타 리소스의 컬렉션이 포함되어 있습니다. Visual Studio 고객의 편의를 위해 Visual Studio에서 특정 Microsoft SDK 및 해당 Microsoft 플랫폼을 대상으로 하고 지원하는 기타 Microsoft 구성 요소를 설치할 수 있습니다. 이러한 구성 요소는 고유한 조건과 정책에 따라 사용이 허가되고 지원될 수도 있습니다.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Visual Studio 정책이 아닌 다른 수명 주기 정책을 따르는 외부 구성 요소  
 다음 표에서는 특정 Visual Studio 소프트웨어 버전에 따라 Visual Studio에 포함될 수 있고 고유한 지원 정책 및 시간 프레임이 적용될 수 있는 Microsoft 플랫폼 구성 요소를 보여 줍니다.  
  
|제품군|외부 이름|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack(클래식)<br /><br /> .NET 4.5.1 멀티 타기팅 팩(스토어)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 재배포 가능 패키지<br /><br /> .NET 4.5.1 재배포 가능 패키지 언어 팩<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET 웹 자료](https://support.microsoft.com/kb/2902020)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> ASP.NET 웹 페이지 2<br /><br /> ASP.NET 웹 페이지 3|  
|[Entity Framework 6](https://support.microsoft.com/kb/2902020)|Entity Framework 6|  
|[Exchange 2013](https://support.microsoft.com/kb/2902020)|Exchange 웹 서비스|  
|[Microsoft OWIN](https://support.microsoft.com/kb/2902020)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://support.microsoft.com/kb/2902020)|Microsoft Web Developer Tools 2013|  
|이러한 구성 요소에 대한 업데이트는 NuGet을 통해 배포되며 표준 Microsoft 수명 주기 정책을 따르지 않습니다.  [http://docs.nuget.org/](/nuget/)자세한 내용은을 참조 하세요.|Microsoft .NET Framework 4.5용 JSON 웹 토큰 처리기<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> 웹 최적화 프레임워크<br /><br /> WebGrease|  
|[ODataLib](https://support.microsoft.com/kb/2902020)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[온라인 서비스 정책](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint 클라이언트 구성 요소<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation Extensions|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> 참고 항목: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5 런타임<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL 시스템 CLR 형식(SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx(DACFramework)<br /><br /> SMO(SharedManagementObjects)<br /><br /> SQL 명령줄 유틸리티<br /><br /> SQL 언어 서비스 - IntelliSense(TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client(Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL 시스템 CLR 형식(SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx(DACFramework)<br /><br /> SMO(SharedManagementObjects)<br /><br /> SQL 명령줄 유틸리티<br /><br /> SQL 언어 서비스 - IntelliSense(TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client(Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL 시스템 CLR 형식(SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services v1.0 SP2](https://support.microsoft.com/kb/2902020)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Server 2008용 WWS(Windows 웹 서비스)|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> JavaScript용 Windows 라이브러리(WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> 참고 항목: [온라인 수명 주기 정책](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Azure Mobile Services SDK<br /><br /> Microsoft Azure 모바일 서비스 도구|
