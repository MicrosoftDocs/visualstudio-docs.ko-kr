---
title: 실행 중인 ASP.NET 프로세스 찾기 | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187663"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET 프로세스의 이름 찾기

실행 중인 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 앱을 디버그하려면 Visual Studio 디버거가 이름으로 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로세스에 연결되어야 합니다.

**ASP.NET 앱을 실행하는 프로세스를 찾으려면:**

1. 앱을 실행하는 동안 Visual Studio에서 **디버그** > **프로세스에 연결**을 선택합니다.

1. **프로세스에 연결** 대화 상자에서 다음 목록에 있는 프로세스 이름의 첫 문자를 입력하거나 검색 상자에 입력합니다. 실행 중인 항목은 ASP.NET 앱을 실행하는 항목입니다. 해당 프로세스에 연결하여 앱을 디버그합니다.

    - *w3wp.exe*는 IIS 6.0 이상입니다.
    - *aspnet_wp.exe*는 IIS의 이전 버전입니다.
    - *iisexpress.exe*는 IISExpress입니다.
    - *dotnet.exe*는 ASP.NET Core입니다.
    - *inetinfo.exe*는 in-process를 실행하는 이전 ASP 애플리케이션입니다.

>[!NOTE]
>Visual Studio 2012 이하 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 코드는 파일 시스템에 있고 테스트 서버 *WebDev.WebServer.exe* 또는 *WebDev.WebServer40.exe*에서 실행될 수 있습니다. 이 경우 로컬 디버깅을 위해 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 프로세스가 아닌 *WebDev.WebServer.exe* 또는 *WebDev.WebServer40.exe*에 연결합니다.

**참고 항목:**

- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [웹 애플리케이션 원격 디버깅의 필수 구성 요소](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET 애플리케이션 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)