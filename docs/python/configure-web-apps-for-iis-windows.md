---
title: IIS용 Python 웹앱 구성
description: Windows 가상 머신에서 인터넷 정보 서비스를 사용하여 실행할 Python 웹앱을 구성하는 방법입니다.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3c756f3d9a89294ecce054650037be3f7b26c291
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540935"
---
# <a name="configure-python-web-apps-for-iis"></a>IIS용 Python 웹앱 구성

Windows 컴퓨터([Azure의 Windows 가상 머신](/azure/architecture/reference-architectures/n-tier/windows-vm) 포함)에서 IIS(인터넷 정보 서비스)를 웹 서버로 사용하는 경우 IIS에서 Python 코드를 적절하게 처리할 수 있도록 Python 앱의 *web.config* 파일에 특정 설정이 포함되어야 합니다. 컴퓨터 자체에도 웹앱에 필요한 패키지와 함께 Python이 설치되어 있어야 합니다.

> [!Note]
> 이전에는 이 문서에 Windows의 Azure App Service에서 Python을 구성하는 방법에 대한 지침이 포함되어 있었습니다. 해당 시나리오에서 사용된 Python 확장 및 Windows 호스트는 사용이 중단되었으며 Linux의 Azure App Service로 대체되었습니다. 자세한 내용은 [Azure App Service(Linux)에 Python 앱 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)를 참조하세요. 그러나 [Python 확장을 사용하여 Windows의 App Service 관리](managing-python-on-azure-app-service.md)에서 이전 문서를 계속 사용할 수 있습니다.

## <a name="install-python-on-windows"></a>Windows에 Python 설치

웹앱을 실행하려면 먼저 [Python 인터프리터 설치](installing-python-interpreters.md)에 설명된 대로 Windows 호스트 머신에 바로, 필요한 버전의 Python을 설치합니다.

이후 단계를 위해 `python.exe` 인터프리터의 위치를 기록합니다. 편의상, 해당 위치를 PATH 환경 변수에 추가할 수 있습니다.

## <a name="install-packages"></a>패키지 설치

전용 호스트를 사용하는 경우 가상 환경 대신 글로벌 Python 환경을 사용하여 앱을 실행할 수 있습니다. 따라서 명령 프롬프트에서 `pip install -r requirements.txt`를 실행하여 모든 앱의 요구 사항을 전역 환경에 설치할 수 있습니다.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python 인터프리터를 가리키도록 web.config 설정

앱의 *web.config* 파일은 Windows에서 실행 중인 IIS(7 이상) 웹 서버에 HttpPlatform(권장) 또는 FastCGI를 통해 Python 요청을 처리하는 방법을 지시합니다. Visual Studio 버전 2015 및 이전 버전에서는 이러한 수정 작업을 자동으로 확인합니다. Visual Studio 2017 이상을 사용하는 경우 *web.config*를 수동으로 수정해야 합니다.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform 처리기 구성

HttpPlatform 모듈은 소켓 연결을 독립 실행형 Python 프로세스에 직접 전달합니다. 이 전달을 통해 원하는 모든 웹 서버를 실행할 수 있지만 로컬 웹 서버를 실행하는 시작 스크립트가 필요합니다. *web.config*의 `<httpPlatform>` 요소에 스크립트를 지정합니다. 여기서 `processPath` 특성은 사이트 확장의 Python 인터프리터를 가리키고, `arguments` 특성은 스크립트 및 제공하려는 모든 인수를 가리킵니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

여기에 표시된 `HTTP_PLATFORM_PORT` 환경 변수에는 로컬 서버가 localhost의 연결을 수신 대기해야 하는 포트가 포함됩니다. 이 예제에서는 원하는 경우 다른 환경 변수(이 경우 `SERVER_PORT`)를 만드는 방법도 보여 줍니다.

### <a name="configure-the-fastcgi-handler"></a>FastCGI 처리기 구성

FastCGI는 요청 수준에서 작동하는 인터페이스입니다. IIS는 들어오는 연결을 받은 다음 하나 이상의 영구적 Python 프로세스에서 실행되는 WSGI 앱에 각 요청을 전달합니다.

사용하려면 먼저 [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi)에 설명된 대로 wfastcgi 패키지를 설치하고 구성합니다.

그런 다음, 앱의 *web.config* 파일을 수정하여 *python.exe* 및 *wfastcgi.py*의 전체 경로를 `PythonHandler` 키에 포함합니다. 아래 단계에서는 Python이 *c:\python36-32*에 설치되어 있고 앱 코드가 *c:\home\site\wwwroot*에 있다고 가정합니다. 사용자 경로에 맞게 적절하게 조정합니다.

1. 경로가 Python 설치 위치와 일치하도록 *web.config*의 `PythonHandler` 항목을 수정합니다. 정확한 정보는 [IIS 구성 참조](https://www.iis.net/configreference)(iis.net)를 참조하세요.

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. *web.config*의 `<appSettings>` 섹션 내에서 `WSGI_HANDLER`, `WSGI_LOG`(옵션) 및 `PYTHONPATH`에 대한 키를 추가합니다.

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    이러한 `<appSettings>` 값은 앱에서 환경 변수로 사용할 수 있습니다.

    - `PYTHONPATH`의 값은 자유롭게 확장될 수 있지만 해당 앱의 루트를 포함해야 합니다.
    - `WSGI_HANDLER`는 해당 앱에서 가져올 수 있는 WSGI 앱을 가리켜야 합니다.
    - `WSGI_LOG`는 선택 사항이지만 앱 디버깅을 위해 권장됩니다.

1. *web.config*의 `WSGI_HANDLER` 항목을 사용 중인 프레임워크에 적합하게 설정합니다.

    - **Bottle**: 아래 표시된 대로 `app.wsgi_app` 뒤에 괄호가 있는지 확인합니다. 이는 해당 개체가 변수가 아닌 함수이기 때문에 필요합니다(*app.py* 참조).

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: `WSGI_HANDLER` 값을 `<project_name>.app`으로 변경합니다. 여기서 `<project_name>`은 프로젝트 이름과 일치합니다. *runserver.py*의 `from <project_name> import app` 문을 살펴보면 정확한 식별자를 찾을 수 있습니다. 예를 들어 프로젝트 이름이 “FlaskAzurePublishExample”인 경우 항목은 다음과 같이 표시됩니다.

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django**: Django 프로젝트에 대한 *web.config*에서 두 가지 사항을 변경해야 합니다. 먼저, `WSGI_HANDLER` 값을 `django.core.wsgi.get_wsgi_application()`으로 변경합니다(개체가 *wsgi.py* 파일에 있음).

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        둘째, `DjangoAzurePublishExample`을 사용자의 프로젝트 이름으로 대체하여 `WSGI_HANDLER`에 대한 아래 항목을 추가합니다.

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Django 앱만 해당**: Django 프로젝트의 *settings.py* 파일에서 아래와 같이 사이트 URL 도메인 또는 IP 주소를 `ALLOWED_HOSTS`에 추가합니다. ‘1.2.3.4’는 사용자 URL 또는 IP 주소로 바꿉니다.

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    배열에 사용자 URL을 추가하지 않으면 다음 오류가 표시됩니다. **DisallowedHost/잘못된 HTTP_HOST 헤더: '\<site URL\>'. '\<site URL\>'를 ALLOWED_HOSTS에 추가해야 할 수도 있습니다.**

    배열이 비어 있으면 Django는 ‘localhost’ 및 ‘127.0.0.1’을 자동으로 허용하지만 프로덕션 URL을 추가하면 해당 기능이 제거됩니다. 이러한 이유로 *settings.py*의 개발 및 프로덕션 복사본을 별도로 유지 관리하거나, 환경 변수를 사용하여 런타임 값을 제어하는 것이 좋습니다.

## <a name="deploy-to-iis-or-a-windows-vm"></a>IIS 또는 Windows VM에 배포

프로젝트에 올바른 *web.config* 파일이 있으면 **솔루션 탐색기**에서 프로젝트 상황에 맞는 메뉴의 **게시** 명령을 사용하고 **IIS, FTP 등** 옵션을 선택하여 IIS를 실행하는 컴퓨터에 게시할 수 있습니다. 이 경우 Visual Studio는 단순히 프로젝트 파일을 서버에 복사하기만 하며, 모든 서버 쪽 구성은 사용자의 책임입니다.
