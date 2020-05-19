---
title: '오류: 웹 서버가 제대로 구성되어 있지 않습니다. | Microsoft Docs'
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736920"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>오류: 웹 서버가 제대로 구성되어 있지 않습니다.

여기에 설명된 단계를 수행하여 문제를 해결한 후, 디버깅을 다시 시도하기 전에 IIS를 초기화해야 할 수도 있습니다. 관리자 명령 프롬프트를 열고 `iisreset`를 입력하여 이 작업을 수행할 수 있습니다.

이 문제를 해결하려면 다음 단계를 따릅니다.

1. 서버에서 호스트되는 웹앱이 릴리스 빌드로 구성된 경우 디버그 빌드로 다시 게시하고 컴파일 요소에서 web.config 파일에 `debug=true`가 포함되어 있는지 확인합니다. IIS를 다시 설정하고 다시 시도합니다.

    예를 들어 릴리스 빌드의 게시 프로필을 사용하는 경우 디버그로 변경하고 다시 게시합니다. 이렇게 하지 않으면 게시할 때 debug 특성이 `false`로 설정됩니다.

2. (IIS) 실제 경로가 올바른지 확인합니다. IIS의 경우 **기본 설정 > 실제 경로**(또는 이전 버전 IIS에서는 **고급 설정**)에서 이 설정을 찾을 수 있습니다.

    웹 애플리케이션이 다른 머신에 복사되었거나, 수동으로 이름이 바뀌었거나, 이동된 경우 실제 경로라 올바르지 않을 수 있습니다. IIS를 다시 설정하고 다시 시도합니다.

3. Visual Studio에서 로컬로 디버그하는 경우 속성에서 올바른 서버가 선택되어 있는지 확인합니다. (프로젝트 형식에 따라 **속성 > 웹 > 서버** 또는 **속성 > 디버그**를 엽니다. Web Forms 프로젝트의 경우 **속성 페이지 > 시작 옵션 > 서버**를 엽니다.)

    IIS와 같은 외부(사용자 지정) 서버를 사용하는 경우 URL이 정확해야 합니다. 정확하지 않으면 IIS Express를 선택하고 다시 시도합니다.

4. (IIS) 올바른 버전의 ASP.NET이 서버에 설치되어 있는지 확인합니다.

    IIS와 Visual Studio 프로젝트의 ASP.NET 버전이 일치하지 않으면 이 문제가 발생할 수 있습니다. web.config에서 프레임워크 버전을 설정해야 할 수 있습니다. IIS에 ASP.NET을 설치하려면 [WebPI(웹 플랫폼 설치 관리자)](https://www.microsoft.com/web/downloads/platform.aspx)를 사용합니다. 또한 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) 또는 ASP.NET Core인 경우 [IIS를 사용하여 Windows에 호스트](https://docs.asp.net/en/latest/publishing/iis.html)를 참조하세요.

4. IIS의 `maxConnection` 제한이 너무 적고 연결 수가 너무 많은 경우 [연결 제한을 늘려야](/iis/configuration/system.applicationhost/sites/sitedefaults/limits) 할 수 있습니다.

## <a name="see-also"></a>참조
- [원격 IIS 컴퓨터의 원격 디버깅 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)