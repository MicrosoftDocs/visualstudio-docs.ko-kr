---
title: '방법: 사용자 계정으로 작업자 프로세스 실행 | Microsoft Docs'
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
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157865"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>방법: 사용자 계정으로 작업자 프로세스 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스(aspnet_wp.exe 또는 w3wp.exe)를 사용자 계정으로 실행할 수 있도록 컴퓨터를 설정하려면 다음 단계를 따르세요.  
  
## <a name="procedure"></a>프로시저  
  
#### <a name="to-run-aspnet_wpexe-under-a-user-account"></a>aspnet_wp.exe를 사용자 계정에서 실행하려면  
  
1. 컴퓨터에서 런타임을 설치한 경로에 있는 CONFIG 폴더의 machine.config 파일을 엽니다.  
  
2. &lt;processModel&gt; 섹션을 찾아 사용자 및 암호 특성을 aspnet_wp.exe를 실행할 사용자 계정의 이름과 암호로 변경합니다.  
  
3. machine.config 파일을 저장합니다.  
  
4. [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]에는 기본적으로 IIS 6.0이 설치되어 있습니다. 해당 작업자 프로세스는 w3wp.exe입니다. IIS 6.0 모드에서 aspnet_wp.exe를 작업자 프로세스로 사용하여 실행하려면 다음 단계를 수행해야 합니다.  
  
    1. **시작**과 **관리 도구** 를 차례로 클릭한 다음 **인터넷 정보 서비스**를 선택합니다.  
  
    2. **인터넷 정보 서비스** 대화 상자에서 **웹 사이트** 폴더를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
    3. **웹 사이트 등록 정보** 대화 상자에서 **서비스**를 선택합니다.  
  
    4. **IIS6.0 격리 모드에서 WWW 서비스 실행**을 선택합니다.  
  
    5. **속성** 대화 상자와 **인터넷 서비스 관리자**를 닫습니다.  
  
5. Windows 명령 프롬프트를 열고 다음을 실행하여 서버를 다시 설정합니다.  
  
    ```  
    iisreset  
    ```  

    — 또는 —  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. CONFIG 폴더와 같은 경로에 있는 Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files 폴더를 찾습니다. Temporary [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Files 폴더를 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성** 을 선택합니다.  
  
7. **Temporary ASP.NET Files 속성** 대화 상자에서 **보안** 탭을 클릭합니다.  
  
8. **고급**을 클릭합니다.  
  
9. **Temporary ASP.Net Files 고급 보안 설정** 대화 상자에서 **추가**를 클릭합니다.  
  
    **사용자, 컴퓨터 또는 그룹 선택** 대화 상자가 나타납니다.  
  
10. **선택할 개체 이름 입력** 상자에 사용자 이름을 입력하고 **확인**을 클릭합니다. 사용자 이름은 다음 형식을 따라야 합니다. DomainName\UserName.  
  
11. **Temporary ASP.NET Files 권한 항목** 대화 상자에서 사용자에게 **모든 권한**을 부여한 다음 **확인** 을 클릭하여 **Temporary ASP.NET Files 권한 항목** 대화 상자를 닫습니다.  
  
12. 시스템 폴더에 대한 사용 권한을 변경할지 여부를 묻는 **보안** 대화 상자가 나타납니다. **예**를 클릭합니다.  
  
13. **확인** 을 클릭하여 **Temporary ASP.NET Files 속성** 대화 상자를 닫습니다.  
  
## <a name="see-also"></a>관련 항목  
[ASP.NET 디버깅: 시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)  
