---
title: 오류 - 웹 서버에서 디버깅을 시작할 수 없음 | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00d27dafd5e44b058cff05b3c478322e45242b3c
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460041"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>오류: 웹 서버에서 디버깅을 시작할 수 없습니다.

웹 서버에서 실행되는 ASP.NET 애플리케이션을 디버깅하려고 할 때 `Unable to start debugging on the Web server` 오류 메시지가 나타날 수 있습니다.

애플리케이션 풀, IIS 초기화 또는 둘 다 업데이트해야 하는 오류나 구성 변경이 발생할 때 이 오류가 종종 발생합니다. 관리자 권한 명령 프롬프트를 열고 `iisreset`을 입력하여 IIS를 초기화할 수 있습니다.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>상세 오류 메시지는 무엇인가요?

`Unable to start debugging on the Web server`는 일반적인 메시지입니다. 일반적으로 더 구체적인 메시지에는 오류 문자열이 포함되며, 문제의 원인을 파악하고 더 정확한 수정 사항을 찾는 데 도움이 될 수 있습니다. 다음은 주요 오류 메시지에 추가되는 몇 가지 일반적인 오류 메시지입니다.

- [IIS가 시작 url과 일치하는 웹 사이트를 나열하지 않습니다.](#IISlist)
- [웹 서버가 제대로 구성되어 있지 않습니다.](#web_server_config)
- [웹 서버에 연결할 수 없습니다.](#unabletoconnect)
- [웹 서버가 적시에 응답하지 않습니다.](#webservertimeout)
- [Microsoft Visual Studio 원격 디버깅 모니터(msvsmon.exe)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.](#msvsmon)
- [원격 서버에서 오류를 반환했습니다.](#server_error)
- [ASP.NET 디버깅을 시작할 수 없습니다.](#aspnet)
- [디버거에서 원격 컴퓨터에 연결할 수 없습니다.](#cannot_connect)
- [일반적인 구성 오류는 도움말을 참조하세요. 웹 페이지를 디버거 외부에서 실행하면 추가 정보가 제공될 수도 있습니다.](#see_help)
- [작업이 지원되지 않습니다. 알 수 없는 오류: *오류 번호*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a>IIS가 시작 url과 일치하는 웹 사이트를 나열하지 않습니다.

- 관리자 권한으로 Visual Studio를 다시 시작하고 디버깅을 다시 시도하세요. (일부 ASP.NET 디버깅 시나리오는 상승된 권한이 필요합니다.)

    Visual studio 바로 가기 아이콘을 마우스 오른쪽 단추로 클릭하고 **속성 > 고급**을 선택한 다음, 항상 관리자 권한으로 실행하도록 선택하여 Visual Studio가 항상 관리자 권한으로 실행되도록 구성할 수 있습니다.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> 웹 서버가 제대로 구성되어 있지 않습니다.

- 각 배포 시나리오의 해결 방법에 대한 지원 포럼에서 [오류: 웹 서버가 제대로 구성되어 있지 않습니다.](../debugger/error-the-web-server-is-not-configured-correctly.md)

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a>웹 서버에 연결할 수 없습니다.

- Visual Studio와 웹 서버를 동일한 머신에서 실행 중이고 **프로세스에 연결** 대신 **F5** 키를 사용하여 디버깅하나요? 프로젝트 속성을 열고, 프로젝트가 올바른 웹 서버에 연결하여 URL을 시작하도록 구성되었는지 확인합니다. (프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**를 엽니다. Web Forms 프로젝트의 경우 **속성 페이지 > 시작 옵션 > 서버**를 엽니다.)

- 그렇지 않다면 애플리케이션 풀을 다시 시작하고 IIS를 초기화합니다. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조하세요.

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout">웹 서버가 적시에 응답하지 않습니다.</a>

- IIS를 초기화하고 디버깅을 다시 시도합니다. IIS 프로세스에 여러 디버거 인스턴스가 연결되었을 수 있습니다. 초기화하면 디버거 인스턴스가 종료됩니다. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조하세요.

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft Visual Studio 원격 디버깅 모니터(msvsmon.exe)가 원격 컴퓨터에서 실행 중인 것 같지 않습니다.

- 원격 머신에서 디버깅하는 경우 [원격 디버거를 설치하여 실행 중](../debugger/remote-debugging.md)인지 확인합니다. 메시지에서 방화벽이 언급된 경우 [방화벽의 올바른 포트](../debugger/remote-debugger-port-assignments.md)가 열려 있는지 확인합니다. 특히 타사 방화벽을 사용하는 경우 더욱 주의해야 합니다.
- HOSTS 파일을 사용하는 경우 파일이 올바르게 구성되었는지 확인합니다. 예를 들어 **프로세스에 연결** 대신 **F5** 키를 사용하여 디버깅하는 경우 프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**의 프로젝트 속성과 동일한 프로젝트 URL이 HOSTS 파일에 포함되어야 합니다.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a>원격 서버에서 오류를 반환했습니다.

[IIS 로그 파일](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0)에서 오류 하위 코드 및 추가 정보를 확인하고, 이 IIS 7 [블로그 게시물](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)을 읽어보세요.

그 외에도 몇 가지 일반적인 오류 코드와 제안 사항이 있습니다.
- (403) 사용할 수 없습니다. 이 오류는 여러 원인으로 발생할 수 있으므로 웹 사이트의 로그 파일과 IIS 보안 설정을 확인해야 합니다. 서버 web.config 파일의 컴파일 요소에 `debug=true`가 포함되어 있는지 확인합니다. 웹 애플리케이션 폴더에 적절한 권한이 있고 애플리케이션 풀 구성이 올바른지 확인합니다(암호가 변경되었을 수 있음). [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조하세요. 이러한 설정이 이미 올바르고 로컬에서 디버깅하는 경우에는 올바른 서버 유형 및 URL에 연결하고 있는지 확인합니다(프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**에서 확인)
- (503) 서버를 사용할 수 없습니다. 오류 또는 구성 변경으로 인해 애플리케이션 풀이 중지되었을 수 있습니다. 애플리케이션 풀을 다시 시작하세요.
- (404) 찾을 수 없습니다. 애플리케이션 풀이 올바른 버전의 ASP.NET에 대해 구성되었는지 확인합니다.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a>ASP.NET 디버깅을 시작할 수 없습니다.

- 애플리케이션 풀을 다시 시작하고 IIS를 초기화하세요. 자세한 내용은 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)을 참조하세요.
- URL 재작성을 수행하는 경우 URL 재작성 없이 기본 web.config를 테스트하세요. [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)의 URL 재작성 모듈에 대한 **참고**를 확인하세요.

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a>디버거에서 원격 컴퓨터에 연결할 수 없습니다.

로컬로 디버깅하는 경우 Visual Studio에서 프로젝트 속성을 열고, 프로젝트가 올바른 웹 서버 및 URL에 연결하도록 구성되었는지 확인합니다. (프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**를 엽니다.)

Visual Studio는 32비트 애플리케이션이므로 64비트 버전의 원격 디버거를 사용하여 64비트 애플리케이션을 디버그합니다. 따라서 로컬로 디버깅할 때 이 오류가 발생할 수 있습니다. IIS의 앱 풀을 검사하여 **32비트 애플리케이션 사용**이 `true`로 설정되었는지 확인하고 IIS를 다시 시작한 후 다시 시도하세요.

또한 HOSTS 파일을 사용하는 경우 파일이 올바르게 구성되었는지 확인하세요. 예를 들어 프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**의 프로젝트 속성과 동일한 프로젝트 URL이 HOSTS 파일에 포함되어야 합니다.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> 일반적인 구성 오류는 도움말을 참조하십시오. 웹 페이지를 디버거 외부에서 실행하면 추가 정보가 제공될 수도 있습니다.

- Visual Studio와 웹 서버를 동일한 머신에서 실행하고 있나요? 프로젝트 속성을 열고, 프로젝트가 올바른 웹 서버에 연결하여 URL을 시작하도록 구성되었는지 확인합니다. (프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**를 엽니다.)

- 이 방법으로 해결되지 않거나 원격으로 디버깅하는 경우 [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)의 단계를 수행합니다.

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> 작업이 지원되지 않습니다. 알 수 없는 오류: *오류 번호*

URL 재작성을 수행하는 경우 URL 재작성 없이 기본 web.config를 테스트하세요. [IIS 구성 확인](#vxtbshttpservererrorsthingstocheck)의 URL 재작성 모듈에 대한 **참고**를 확인하세요.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> IIS 구성 확인

여기에 설명된 단계를 수행하여 문제를 해결한 후, 디버깅을 다시 시도하기 전에 IIS를 초기화해야 할 수도 있습니다. 관리자 권한 명령 프롬프트를 열고 `iisreset`을 입력하면 됩니다.

* IIS 애플리케이션 풀을 중지했다가 다시 시작한 후 다시 시도하세요.

    오류로 인해 애플리케이션 풀이 중지되었을 수 있습니다. 또는 또 다른 구성 변경 때문에 애플리케이션 풀을 중지했다가 다시 시작해야 할 수도 있습니다.

    > [!NOTE]
    > 애플리케이션 풀이 계속 중지되면 제어판에서 URL 재작성 모듈을 제거해야 할 수도 있습니다. WebPI(웹 플랫폼 설치 관리자)를 사용하여 다시 설치할 수 있습니다. 이 문제는 중요한 시스템 업그레이드 후에 발생할 수 있습니다.

* 애플리케이션 풀 구성을 확인하고 필요에 따라 수정한 후 다시 시도하세요.

    Visual Studio 프로젝트와 일치하지 않는 ASP.NET 버전에 대해 애플리케이션 풀이 구성되었을 수 있습니다. 애플리케이션 풀에서 ASP.NET 버전을 업데이트하고 다시 시작하세요. 자세한 내용은 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)을 참조하세요.

    그리고 암호 자격 증명이 변경된 경우 애플리케이션 풀 또는 웹 사이트에서 암호 자격 증명을 업데이트 해야 할 수도 있습니다.  애플리케이션 풀의 **고급 설정 > 프로세스 모델 > ID**에서 자격 증명을 업데이트합니다. 웹 사이트의 경우 **기본 설정 > 연결 계정...** 에서 자격 증명을 업데이트합니다. 애플리케이션 풀을 다시 시작합니다.

* 웹 애플리케이션 폴더에 올바른 권한이 있는지 확인합니다.

    IIS_IUSRS, IUSR 또는 [애플리케이션 풀](/iis/manage/configuring-security/application-pool-identities)과 연결된 특정 사용자에게 웹 애플리케이션 폴더에 대한 읽기 및 실행 권한을 부여해야 합니다. 문제를 해결하고 애플리케이션 풀을 다시 시작합니다.

* IIS에 올바른 버전의 ASP.NET이 설치되도록 확인합니다.

    IIS와 Visual Studio 프로젝트의 ASP.NET 버전이 일치하지 않으면 이 문제가 발생할 수 있습니다. web.config에서 프레임워크 버전을 설정해야 할 수 있습니다. IIS에 ASP.NET을 설치하려면 [WebPI(웹 플랫폼 설치 관리자)](https://www.microsoft.com/web/downloads/platform.aspx)를 사용합니다. [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core인 경우 [IIS를 사용하여 Windows에 호스트](https://docs.asp.net/en/latest/publishing/iis.html)를 참조하세요.

* IP 주소만 사용하는 경우의 인증 오류 해결

     기본적으로 IP 주소는 인터넷의 일부로 인식되는데 인터넷에서는 NTLM 인증을 수행할 수 없습니다. 인증이 필요하도록 IIS에서 웹 사이트를 구성한 경우에는 이 인증이 실패합니다. 이 문제를 해결하려면 IP 주소 대신 원격 컴퓨터의 이름을 지정하면 됩니다.

## <a name="other-causes"></a>기타 원인

IIS 구성이 문제의 원인이 아닌 경우 다음 단계를 수행합니다.

- 또는 관리자 권한으로 Visual Studio를 다시 시작한 후 다시 시도합니다.

    웹 배포 사용과 같은 일부 ASP.NET 디버깅 시나리오는 Visual Studio에 대한 상승된 권한이 필요합니다.

- Visual Studio의 여러 인스턴스가 실행 중인 경우 Visual Studio의 한 인스턴스에서 프로젝트를 다시 열고(관리자 권한으로) 다시 시도합니다.

- 로컬 주소를 사용하는 HOSTS 파일을 사용하는 경우 머신의 IP 주소 대신 루프백 주소를 사용해 봅니다.

    로컬 주소를 사용하지 않는 경우 프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**의 프로젝트 속성과 동일한 프로젝트 URL이 HOSTS 파일에 포함되어 있는지 확인합니다.

## <a name="more-troubleshooting-steps"></a>더 많은 문제 해결 단계

* 서버의 브라우저에서 localhost 페이지를 엽니다.

     IIS가 올바르게 설치되어 있지 않은 경우 브라우저에 `http://localhost` 를 입력하면 오류가 발생합니다.

     IIS에 배포하는 방법에 대한 자세한 내용은 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core인 경우 [IIS를 사용하여 Windows에 호스트](https://docs.asp.net/en/latest/publishing/iis.html)을 참조하세요.

* 서버에서 기본 ASP.NET 애플리케이션 만들기(또는 기본 web.config 파일 사용)

    앱이 작동하지 않는 문제를 디버거로 해결할 수 없는 경우에는 서버에서 로컬로 기본 ASP.NET 애플리케이션을 만들고 기본 앱을 디버그해 보세요. (기본 ASP.NET MVC 템플릿을 사용해도 됩니다.) 기본 앱을 디버그할 수 있으면 두 구성 간의 차이점을 알아보는 데 도움이 될 것입니다. web.config 파일에서 URL 재작성 규칙과 같은 설정이 어떻게 다른지 살펴보세요.

## <a name="see-also"></a>참조
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)