---
title: '방법: 웹 응용 프로그램 디버깅 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205397"
---
# <a name="how-to-debug-web-applications"></a>방법: 웹 애플리케이션 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 는에서 웹 응용 프로그램을 개발 하기 위한 기본 기술입니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거에서는 로컬 컴퓨터 또는 원격 서버에서 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 디버깅하는 강력한 도구를 제공합니다. 이 항목에서는 개발 중에 프로젝트를 디버깅 하는 방법에 대해 설명 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 합니다. 프로덕션 서버에 이미 배포 된 웹 응용 프로그램을 디버깅 하는 방법에 대 한 자세한 내용은 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] [배포 된 웹 응용 프로그램 디버깅](../debugger/debugging-deployed-web-applications.md)을 참조 하세요.  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 디버깅하려면  
  
- 필요한 권한이 있어야 합니다. 자세한 내용은 [System Requirements](../debugger/aspnet-debugging-system-requirements.md)을 참조하세요.  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]**프로젝트 속성**에서 디버깅을 사용 하도록 설정 해야 합니다.  
  
- 애플리케이션의 구성 파일(Web.config)이 디버그 모드로 설정되어 있어야 합니다. 디버그 모드를 설정하면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에서 동적으로 생성된 파일에 대한 기호를 만들고 디버거가 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션에 연결할 수 있도록 합니다. 웹 프로젝트 템플릿에서 프로젝트를 만든 경우 디버깅을 시작하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 이를 자동으로 설정합니다.  
  
- 자세한 내용은 [방법: ASP.NET 응용 프로그램에 디버깅 사용](../debugger/how-to-enable-debugging-for-aspnet-applications.md)을 참조 하세요.  
  
### <a name="to-debug-a-web-application-during-development"></a>개발하는 동안 웹 애플리케이션을 디버깅하려면  
  
1. **디버그** 메뉴에서 **시작** 을 클릭 하 여 웹 응용 프로그램 디버깅을 시작 합니다.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 웹 응용 프로그램 프로젝트를 빌드하고, 필요한 경우 응용 프로그램을 배포 하 고, 로컬로 디버깅 하 고 작업자 프로세스에 연결 하는 경우 ASP.NET 개발 서버를 시작 합니다 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
2. 다른 애플리케이션을 디버깅할 때처럼 디버거를 사용하여 중단점을 설정하거나 지우고 단계별로 실행하며 기타 디버깅 작업을 수행합니다.  
  
     자세한 내용은 [디버거 기본 사항](../debugger/debugger-basics.md)을 참조 하세요.  
  
3. **디버그** 메뉴에서 **디버깅 중지** 를 클릭 하 여 디버깅 세션을 종료 하거나 Internet Explorer의 **파일** 메뉴에서 **닫기**를 클릭 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [웹 응용 프로그램 및 스크립트 디버깅](../debugger/debugging-web-applications-and-script.md)   
 [ASP.NET 및 AJAX 응용 프로그램 디버깅](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [방법: ASP.NET 애플리케이션에 디버깅 사용](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
