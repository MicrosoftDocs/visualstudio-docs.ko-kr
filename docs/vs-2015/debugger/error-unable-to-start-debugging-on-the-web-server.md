---
title: '오류: 웹 서버에서 디버깅을 시작할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185477"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>오류: 웹 서버에서 디버깅을 시작할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

웹 서버에서 실행 중인 ASP.NET 애플리케이션을 디버깅하려고 하면 ‘웹 서버에서 디버깅을 시작할 수 없습니다.’라는 오류 메시지가 표시될 수 있습니다.
  
대부분의 경우이 오류는 IIS가 올바르게 구성 되지 않았기 때문에 발생 합니다.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> IIS 구성 확인

여기에 설명 된 문제를 해결 하는 단계를 수행 하 고 디버깅을 다시 시도 하기 전에 IIS를 다시 설정 해야 할 수도 있습니다. 관리자 명령 프롬프트를 열고를 입력 하 여이 작업을 수행 `iisreset` 하거나 IIS 관리자에서이 작업을 수행할 수 있습니다. 

* 응용 프로그램 풀을 중지 한 후 다시 시작 하 고 다시 시도 하세요.

    응용 프로그램 풀이 중지 되었거나 응용 프로그램 풀을 중지 하 고 다시 시작 해야 할 수도 있습니다.
    
    > [!NOTE]
    > 응용 프로그램 풀을 계속 중지할 경우 제어판에서 URL 재작성 모듈을 제거한 다음 웹 플랫폼 설치 관리자 (WPI)를 사용 하 여 다시 설치 해야 할 수 있습니다. 이는 중요 한 시스템 업그레이드 후에 발생할 수 있습니다.

* 애플리케이션 풀 구성을 확인하고 필요에 따라 수정한 후 다시 시도하세요.

    암호 자격 증명이 변경 된 경우 응용 프로그램 풀에서 업데이트 해야 할 수 있습니다. 또한 최근에 ASP.NET을 설치한 경우 응용 프로그램 풀이 잘못 된 버전의 ASP.NET에 대해 구성 될 수 있습니다. 문제를 해결 하 고 응용 프로그램 풀을 다시 시작 합니다.
    
* 웹 애플리케이션 폴더에 올바른 권한이 있는지 확인합니다.

    웹 응용 프로그램 폴더에 대 한 읽기 및 실행 권한을 IIS_IUSRS 또는 IUSR (또는 응용 프로그램 풀과 연결 된 특정 사용자)에 게 제공 해야 합니다. 문제를 해결하고 애플리케이션 풀을 다시 시작합니다.

* 로컬 주소를 사용하는 HOSTS 파일을 사용하는 경우 머신의 IP 주소 대신 루프백 주소를 사용해 봅니다.

* 브라우저에서 localhost 페이지를 엽니다.

     IIS가 올바르게 설치되어 있지 않은 경우 브라우저에 `http://localhost` 를 입력하면 오류가 발생합니다.
     
     IIS에 배포 하는 방법에 대 한 자세한 내용은 원격 [디버깅 ASP.NET 원격 Iis 컴퓨터에서](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) 또는 ASP.NET Core의 경우 [iis에 게시](https://docs.asp.net/en/latest/publishing/iis.html))를 참조 하세요.

* IIS에 올바른 버전의 ASP.NET이 설치되도록 확인합니다.  [ASP.NET 응용 프로그램 배포](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) 또는 ASP.NET Core의 경우 [IIS에 게시](https://docs.asp.net/en/latest/publishing/iis.html))를 참조 하세요.

* 서버에 기본 ASP.NET 응용 프로그램을 만듭니다.

     앱이 작동하지 않는 문제를 디버거로 해결할 수 없는 경우에는 서버에서 로컬로 기본 ASP.NET 애플리케이션을 만들고 기본 앱을 디버그해 보세요. 기본 앱을 디버그할 수 있는 경우 두 구성 간의 차이점을 식별 하는 데 도움이 될 수 있습니다.
  
* IP 주소만 사용하는 경우의 인증 오류 해결

     기본적으로 IP 주소는 인터넷의 일부로 인식되는데 인터넷에서는 NTLM 인증을 수행할 수 없습니다. 웹 사이트가 인증을 요구 하도록 IIS에서 구성 된 경우에는이 인증에 실패 합니다. 이 문제를 해결하려면 IP 주소 대신 원격 컴퓨터의 이름을 지정하면 됩니다.
     
## <a name="other-causes"></a>기타 원인

이전 버전의 Visual Studio를 사용 하는 경우:

- 상승 된 권한으로 Visual Studio를 다시 시작 하 고 다시 시도 하세요.

    이전 버전의 버그 (나중에 수정 됨)에는 일부 ASP.NET 디버깅 시나리오에서 상승 된 권한이 필요 합니다.
    
- Visual Studio의 여러 인스턴스가 실행 중인 경우 Visual Studio의 한 인스턴스에서 프로젝트를 다시 열고 다시 시도 하세요.

## <a name="see-also"></a>관련 항목  
 [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
