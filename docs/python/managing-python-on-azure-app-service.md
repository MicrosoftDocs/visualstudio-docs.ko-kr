---
title: Azure App Service에서 Python 구성(Windows)
description: Azure App Service에 Python 인터프리터 및 라이브러리를 설치하고 해당 인터프리터를 제대로 참조하도록 웹 애플리케이션을 구성하는 방법입니다.
ms.date: 01/07/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 7ffe0de939eba8af38c132fc3de5c96a9499e3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535993"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Azure App Service에서 Python 환경을 설정하는 방법(Windows)

> [!Important]
> Microsoft는 [Linux의 App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)에 직접 배포하기 위해 이 문서에 설명된 Windows의 App Service에 대한 Python 확장의 사용을 중단했습니다.

[Azure App Service](https://azure.microsoft.com/services/app-service/)는 브라우저를 통해 액세스한 사이트, 고유한 클라이언트에서 사용된 REST API, 이벤트 트리거된 처리 등 웹앱용 Platform-as-a-Service 제품입니다. App Service는 Python을 사용한 앱 구현을 완벽하게 지원합니다.

사용자 지정이 가능한 Azure App Service의 Python 지원은 각각 특정 버전의 Python 런타임이 포함된 App Service *사이트 확장* 집합으로 제공됩니다. 이 문서에 설명된 대로 원하는 모든 패키지를 해당 환경에 직접 설치할 수 있습니다. App Service 자체에서 환경을 사용자 지정하면 웹 앱 프로젝트에서 패키지를 유지 관리하거나 앱 코드로 업로드할 필요가 없습니다.

> [!Tip]
> 기본적으로 App Service는 서버의 루트 폴더에 Python 2.7 및 Python 3.4가 설치되어 있지만, 이러한 환경에서 패키지를 사용자 지정하거나 설치할 수도 없고, 현재 상태에 의존할 수도 없습니다. 대신 이 문서에 설명된 대로 직접 제어하는 사이트 확장을 사용해야 합니다.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Azure Portal을 통해 Python 버전 선택

1. Azure Portal에서 웹앱에 대한 App Service를 만듭니다.
1. App Service의 페이지에서 **개발 도구** 섹션으로 스크롤하고, **확장**을 선택한 다음, **+ 추가**를 선택합니다.
1. 목록에서 원하는 Python의 버전을 포함하는 확장까지 아래로 스크롤합니다.

    ![Python 확장이 표시된 Azure Portal](media/python-on-azure-extensions.png)

    > [!Tip]
    > Python의 이전 버전이 필요한데 사이트 확장에 표시되지 않을 경우, 다음 섹션에 설명된 대로 Azure Resource Manager를 통해 설치할 수 있습니다.

1. 확장을 선택하고, 법률 조항에 동의한 다음, **확인**을 선택합니다.
1. 설치가 완료되면 포털에서 알림이 나타납니다.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Azure Resource Manager를 통해 Python 버전 선택

Azure Resource Manager 템플릿을 사용하여 App Service를 배포하는 경우 사이트 확장을 리소스로 추가합니다. 특히 확장은 `resources` 형식과 `resources`siteextensions.net`siteextensions`의 이름을 사용하여 중첩된 리소스([ 아래의 ](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) 개체)로 표시됩니다.

예를 들어 `python361x64`(Python 3.6.1 x64)에 참조를 추가한 후 템플릿이 다음과 같이 표시될 수 있습니다(일부 속성 생략됨).

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python 인터프리터를 가리키도록 web.config 설정

포털이나 Azure Resource Manager 템플릿을 통해 사이트 확장을 설치한 후, Python 인터프리터를 가리키도록 앱의 *web.config* 파일을 설정합니다. *web.config* 파일은 App Service에서 실행 중인 IIS(7 이상) 웹 서버에 HttpPlatform(권장) 또는 FastCGI를 통해 Python 요청을 처리해야 하는 방법을 지시합니다.

먼저 사이트 확장의 *python.exe*에 대한 전체 경로를 찾은 다음, 적절한 *web.config* 파일을 만들고 수정합니다.

### <a name="find-the-path-to-pythonexe"></a>python.exe에 대한 경로 찾기

Python 사이트 확장은 서버의 *d:\home* 아래에서 Python 버전 및 아키텍처에 적합한 폴더에 설치됩니다(일부 이전 버전의 경우 제외). 예를 들어 Python 3.6.1 x64는 *d:\home\python361x64*에 설치됩니다. Python 인터프리터의 전체 경로는 *d:\home\python361x64\python.exe*입니다.

App Service에서 특정 경로를 보려면 App Service 페이지에서 **확장**을 선택한 다음, 목록에서 확장을 선택합니다.

![Azure App Service의 확장 목록](media/python-on-azure-extension-list.png)

그러면 경로를 포함하는 확장의 설명 페이지가 열립니다.

![Azure App Service의 확장 세부 정보](media/python-on-azure-extension-detail.png)

확장에 대한 경로를 보는 데 문제가 있는 경우 콘솔을 사용하여 수동으로 찾을 수 있습니다.

1. App Service 페이지에서 **개발 도구** > **콘솔**을 선택합니다.
1. `ls ../home` 또는 `dir ..\home` 명령을 입력하여 *Python361x64*와 같은 최상위 확장 폴더를 확인합니다.
1. `ls ../home/python361x64` 또는 `dir ..\home\python361x64`와 같은 명령을 입력하여 *python.exe* 및 기타 인터프리터 파일이 포함되어 있는지 확인합니다.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform 처리기 구성

HttpPlatform 모듈은 소켓 연결을 독립 실행형 Python 프로세스에 직접 전달합니다. 이 전달을 통해 원하는 모든 웹 서버를 실행할 수 있지만 로컬 웹 서버를 실행하는 시작 스크립트가 필요합니다. `<httpPlatform>`web.config*의*  요소에 스크립트를 지정합니다. 여기서 `processPath` 특성은 사이트 확장의 Python 인터프리터를 가리키고, `arguments` 특성은 스크립트 및 제공하려는 모든 인수를 가리킵니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

FastCGI는 요청 수준에서 작동하는 인터페이스입니다. IIS는 들어오는 연결을 받은 다음 하나 이상의 영구적 Python 프로세스에서 실행되는 WSGI 앱에 각 요청을 전달합니다. [wfastcgi 패키지](https://pypi.io/project/wfastcgi)는 사전 설치되고 각 Python 사이트 확장으로 구성되어 있으므로, Bottle 프레임워크를 기반으로 하는 웹앱에 대해 다음과 같은 코드를 *web.config*에 포함하여 쉽게 사용할 수 있습니다. *python.exe* 및 *wfastcgi.py*에 대한 전체 경로는 `PythonHandler` 키에 있습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

여기서 정의된 `<appSettings>`는 앱에서 환경 변수로 사용할 수 있습니다.

- `PYTHONPATH`의 값은 자유롭게 확장될 수 있지만 해당 앱의 루트를 포함해야 합니다.
- `WSGI_HANDLER`는 해당 앱에서 가져올 수 있는 WSGI 앱을 가리켜야 합니다.
- `WSGI_LOG`는 선택 사항이지만 앱 디버깅을 위해 권장됩니다.

[Azure에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)를 참조하여 Bottle, Flask 및 Django 웹앱을 위한 *web.config* 콘텐츠에 대한 추가 정보를 확인하세요.

## <a name="install-packages"></a>패키지 설치

사이트 확장을 통해 설치된 Python 인터프리터는 사용자의 Python 환경 중 한 부분일 뿐입니다. 해당 환경에서도 서로 다른 패키지를 설치해야 하는 경우가 많습니다.

서버 환경에서 직접 패키지를 설치하려면 다음 방법 중 하나를 사용합니다.

| 메서드 | 사용 |
| --- | --- |
| [Azure App Service Kudu 콘솔](#azure-app-service-kudu-console) | 대화형으로 패키지를 설치합니다. 패키지는 순수한 Python이거나 휠을 게시해야 합니다. |
| [Kudu REST API](#kudu-rest-api) | 패키지 설치를 자동화하는 데 사용할 수 있습니다.  패키지는 순수한 Python이거나 휠을 게시해야 합니다. |
| 앱을 사용한 번들 | 패키지를 프로젝트에 직접 설치한 다음, 앱의 일부인 경우처럼 App Service에 배포합니다. 보유한 종속성 수와 업데이트 빈도에 따라 이 방법은 배포 작업을 진행하는 가장 쉬운 방법일 수 있습니다. 주의 사항은 이러한 라이브러리가 서버의 Python 버전과 정확하게 일치해야 한다는 것입니다. 일치하지 않으면 배포 후에 모호한 오류가 표시됩니다. 그러나 App Service 사이트 확장의 Python 버전은 python.org에 릴리스된 버전과 정확히 동일하기 때문에 로컬 개발에 사용할 호환되는 버전을 쉽게 얻을 수 있습니다. |
| 가상 환경 | 지원되지 않습니다. 대신, 번들을 사용하고 `PYTHONPATH` 환경 변수를 패키지의 위치를 가리키도록 설정합니다. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service Kudu 콘솔

[Kudu 콘솔](https://github.com/projectkudu/kudu/wiki/Kudu-console)은 App Service 서버와 해당 파일 시스템에 대한 직접적인 관리자 권한 명령줄 액세스를 제공합니다. 이는 모두 유용한 디버깅 도구이며 패키지를 설치하는 등의 CLI 작업을 허용합니다.

1. **개발 도구** > **고급 도구**를 선택하고 **이동**을 선택하여 Azure Portal의 App Service 페이지에서 Kudu를 엽니다. 이 작업을 통해 `.scm`이 삽입된 것 외에는 기본 App Service URL과 동일한 URL로 이동합니다. 예를 들어 기본 URL이 `https://vspython-test.azurewebsites.net/`이면 Kudu는 `https://vspython-test.scm.azurewebsites.net/`에 있습니다(책갈피 사용 가능).

    ![Azure App Service용 Kudu 콘솔](media/python-on-azure-console01.png)

1. **디버그 콘솔** > **CMD**를 선택하여 콘솔을 엽니다. 여기서 Python 설치로 이동하여 어떤 라이브러리가 있는지 확인할 수 있습니다.

1. 단일 패키지를 설치하려면

    a. 패키지를 설치하려는 Python 설치 폴더(예: *d:\home\python361x64*)로 이동합니다.

    b. `python.exe -m pip install <package_name>`을 사용하여 패키지를 설치합니다.

    ![Azure App Service용 Kudu 콘솔을 통한 bottle 설치의 예](media/python-on-azure-console02.png)

1. 앱용 *requirements.txt*를 서버에 이미 배포한 경우 다음과 같이 해당 요구 사항을 모두 설치합니다.

    a. 패키지를 설치하려는 Python 설치 폴더(예: *d:\home\python361x64*)로 이동합니다.

    b. `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` 명령을 실행합니다.

    로컬 및 서버 모두에서 정확한 패키지 집합을 쉽게 재현할 수 있기 때문에 *requirements.txt*를 사용하는 것이 좋습니다. *requirements.txt*에 대한 변경 내용을 배포한 후 콘솔을 방문하여 명령을 다시 실행해야 합니다.

> [!Note]
> App Service에는 C 컴파일러가 없으므로 기본 확장 모듈이 있는 모든 패키지에 대해 휠을 설치해야 합니다. 인기 있는 많은 패키지가 자체 휠을 제공합니다. 자체 휠을 제공하지 않는 패키지의 경우 로컬 개발 컴퓨터의 `pip wheel <package_name>`을 사용한 다음 휠을 사이트에 업로드합니다. 예제를 보려면 [requirements.txt를 사용하여 필수 패키지 관리](managing-required-packages-with-requirements-txt.md)를 참조하세요.

### <a name="kudu-rest-api"></a>Kudu REST API

Azure Portal을 통해 Kudu 콘솔을 사용하는 대신 `https://yoursite.scm.azurewebsites.net/api/command`에 명령을 게시하여 Kudu REST API를 통해 원격으로 명령을 실행할 수 있습니다. 예를 들어 `bottle` 패키지를 설치하려면 다음 JSON을 `/api/command`에 게시합니다.

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

명령 및 인증에 대한 자세한 내용은 [Kudu 설명서](https://github.com/projectkudu/kudu/wiki/REST-API)를 참조하세요.

`az webapp deployment list-publishing-profiles` 명령을 사용하여 Azure CLI를 통해 자격 증명을 볼 수 있습니다([az webapp 배포](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles) 참조). Kudu 명령을 게시하는 도우미 라이브러리도 [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)에서 사용할 수 있습니다.
