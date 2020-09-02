---
title: '방법: ASP.NET 프로세스의 이름 찾기 | Microsoft Docs'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685947"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>방법: ASP.NET 프로세스의 이름 찾기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

실행 중인 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션에 연결하려면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 프로세스의 이름을 알고 있어야 합니다.  
  
- IIS 6.0 또는 IIS 7.0을 실행하는 경우 이 이름은 w3wp.exe입니다.  
  
- 이전 버전의 IIS를 실행하는 경우 이 이름은 aspnet_wp.exe입니다.  
  
  이상 버전을 사용 하 여 빌드된 응용 프로그램의 경우 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 코드는 파일 시스템에 상주 하 고 WebDev.WebServer.exe 테스트 서버에서 실행할 수 있습니다. 이 경우 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 프로세스가 아닌 WebDev.WebServer.exe에 연결해야 합니다. 이 시나리오는 로컬 디버깅에만 적용됩니다.  
  
  이전 버전의 ASP 애플리케이션은 in-process로 실행되는 경우 IIS 프로세스 inetinfo.exe 내에서 실행됩니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>프로젝트 코드가 파일 시스템에 상주하는지 아니면 IIS에 상주하는지 확인하려면  
  
1. 아직 열려 있지 않은 경우 Visual Studio에서 **솔루션 탐색기** 를 엽니다.  
  
2. 애플리케이션의 이름이 들어 있는 최상위 노드를 선택합니다.  
  
3. **속성** 창 제목에 파일 경로가 포함 되어 있으면 응용 프로그램 코드는 파일 시스템에 상주 합니다.  
  
     그렇지 않으면 **속성** 창 제목에 웹 사이트 이름이 포함 됩니다.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>애플리케이션이 실행되는 IIS 버전을 확인하려면  
  
1. **관리 도구** 를 찾아서 실행 합니다. 운영 체제에 따라 **제어판**안에 아이콘이 표시 되거나 **시작**을 클릭 하면 표시 되는 메뉴 항목이 표시 될 수 있습니다.  
  
     Windows XP에서 **제어판** 은 종류별 보기 또는 클래식 보기로 표시 될 수 있습니다. 범주 보기에서 **클래식 보기로 전환** 또는 **성능 및 유지 관리** 를 클릭 하 여 **관리 도구** 아이콘을 표시 해야 합니다.  
  
2. **관리 도구**에서 인터넷 정보 서비스를 실행 합니다. MMC 대화 상자가 나타납니다.  
  
3. 왼쪽 창에 컴퓨터 목록이 표시되면 애플리케이션 코드가 상주하는 컴퓨터를 선택합니다.  
  
4. IIS 버전은 오른쪽 창의 **버전** 열에 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [웹 응용 프로그램에 대 한 원격 디버깅 필수 구성 요소](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET 디버그 준비](../debugger/preparing-to-debug-aspnet.md)   
 [웹 애플리케이션 및 스크립트 디버그](../debugger/debugging-web-applications-and-script.md)
