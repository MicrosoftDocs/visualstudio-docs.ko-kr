---
title: Windows의 Azure App Service에 Python 앱 게시
description: web.config 파일에 필요한 콘텐츠를 포함하여 Visual Studio에서 Windows의 Azure App Service에 직접 Python 웹 애플리케이션을 게시하는 방법입니다.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 9a3aee5dc1c2d1272c3814fa6cfb2561f6cb4564
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801310"
---
# <a name="publishing-to-azure-app-service-on-windows"></a>Windows의 Azure App Service에 게시

> [!Note]
> 이 콘텐츠 및 설명한 기능은 더 이상 사용되지 않지만 계속 작동합니다. Python 개발자는 가능한 경우 [Linux의 App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)로 마이그레이션하는 것이 좋습니다.

Visual Studio는 Python 웹앱을 Windows의 Azure App Service에 직접 게시하는 기능을 제공합니다. Windows의 Azure App Service에 게시하는 작업은 서버에 필요한 파일을 복사하고, 웹 서버에 앱을 시작하는 방법을 지시하는 적절한 `web.config` 파일을 설정하는 과정을 의미합니다.

게시 프로세스는 Visual Studio 2017 이상과 Visual Studio 2015 사이가 다릅니다. 특히 Visual Studio 2015는 `web.config` 만들기를 비롯한 단계 중 일부를 자동화합니다. 단, 이 자동화로 인해 장기 유연성 및 제어에 제한이 있습니다. Visual Studio 2017 이상은 더 많은 수동 단계가 필요하지만 Python 환경에서 보다 정확한 제어를 제공합니다. 두 옵션 모두 여기에 설명되어 있습니다.

> [!Note]
> Visual Studio 2015와 Visual Studio 2017 이상 간 변경 사항에 대한 배경 정보는 블로그 게시물 [Visual Studio 2017에서 Azure에 게시](https://devblogs.microsoft.com/python/publish-to-azure-in-vs-2017/)를 참조하세요.

## <a name="prerequisites"></a>사전 요구 사항

이 연습에서는 Bottle, Flask 또는 Django 프레임워크를 기반으로 하는 웹앱 프로젝트가 필요합니다. 프로젝트가 아직 없거나 게시 프로세스를 사용해보려는 경우 다음과 같이 간단한 테스트 프로젝트를 만듭니다.

1. Visual Studio에서 **파일 > 새로 만들기 > 프로젝트**를 선택하고, "Bottle"을 검색하여 **Bottle 웹 프로젝트**를 선택한 다음, 프로젝트에 사용할 이름 및 경로를 지정하고 **확인**을 선택합니다. (Bottle 템플릿은 Python 개발 작업에 포함됩니다. [설치](installing-python-support-in-visual-studio.md)를 참조하세요.)

1. **가상 환경에 설치** 및 가상 환경에 대한 사용자의 기본 설정된 기준 인터프리터를 선택하여 지침에 따라 외부 패키지를 설치합니다. 일반적으로 이 선택은 App Service에 설치된 Python의 버전과 일치합니다.

1. F5 키를 누르거나 **디버그 > 디버깅 시작**을 선택하여 프로젝트를 로컬에서 테스트합니다.

## <a name="create-an-azure-app-service"></a>Azure App Service 만들기

Azure에 게시하려면 대상 App Service가 필요합니다. 이 목적의 경우 Azure 구독을 사용하여 App Service를 만들거나 임시 사이트를 사용할 수 있습니다.

아직 구독이 없는 경우 [전체 무료 Azure 계정](https://azure.microsoft.com/free/)으로 시작하세요. 여기에는 Azure 서비스에 대한 일반적인 크레딧이 포함됩니다. 또한 1년 동안 매달 $25 크레딧을 제공하는 [Visual Studio Dev Essentials](https://azure.microsoft.com/pricing/member-offers/vs-dev-essentials/)에 등록하는 것이 좋습니다.

> [!Tip]
> Azure에서 사용자 계정을 확인하기 위해 신용 카드를 요청하지만 카드에 요금이 부과되지는 않습니다. 추가 요금이 발생하지 않는 무료 크레딧과 동일한 [지출 한도](/azure/billing/billing-spending-limit)를 설정할 수도 있습니다. 또한 Azure는 다음 섹션에 설명된 대로 간단한 테스트 앱에 이상적인 무료 App Service 계획 계층을 제공합니다.

### <a name="using-a-subscription"></a>구독 사용

활성 Azure 구독에서 다음과 같이 빈 웹앱을 사용하는 App Service를 만듭니다.

1. [portal.azure.com](https://portal.azure.com)에 로그인합니다.
1. **+ 새로 만들기**를 선택한 다음, **웹 + 모바일**, **웹 앱**을 차례로 선택합니다.
1. 웹앱에 대한 이름을 지정하고, **리소스 그룹**을 “새로 만들기”로 둔 다음, **Windows**를 운영 체제로 선택합니다.
1. **App Service 계획/위치**를 선택하고, **새로 만들기**를 선택한 다음, 이름 및 위치를 지정합니다. 그런 다음 **가격 책정 계층**을 선택하고, 아래로 스크롤하여 **F1 무료** 계획을 선택하고, **선택**, **확인**, **만들기**를 차례로 선택합니다.
1. (선택 사항) App Service를 만든 후에 **게시 프로필 가져오기**로 이동하여 선택하고, 파일을 로컬로 저장합니다.

### <a name="using-a-temporary-app-service"></a>임시 App Service 사용

다음과 같이 Azure 구독이 필요하지 않는 임시 App Service를 만듭니다.

1. 브라우저에서 [https://azure.microsoft.com/try/app-service/web/](https://azure.microsoft.com/try/app-service/web/)을(를) 엽니다.
1. 앱 유형에 **Web App**을 선택하고 **다음**을 선택합니다.
1. **빈 사이트**, **만들기**를 차례로 선택합니다.
1. 선택한 소셜 로그인을 사용하여 로그인하면 잠시 후에 사이트가 표시된 URL에서 준비됩니다.
1. **게시 프로필 다운로드**를 선택하고 `.publishsettings` 파일을 저장합니다. 이 파일을 나중에 사용할 수 있습니다.

## <a name="configure-python-on-azure-app-service"></a>Azure App Service에서 Python 구성

(구독에서 또는 무료 사이트에서) 실행 중인 빈 웹앱을 사용하는 App Service가 있으면, [Azure App Service에서 Python 관리](managing-python-on-azure-app-service.md)에 설명된 대로 선택한 Python 버전을 설치합니다. Visual Studio 2017 이상에서 게시하려면 해당 문서에 설명된 대로 사이트 확장과 함께 설치된 Python 인터프리터에 대한 정확한 경로를 기록합니다.

또한 원하는 경우 이 지침의 프로세스를 사용하여 `bottle` 패키지를 설치할 수 있습니다. 해당 패키지는 이 연습 중 다른 단계의 일부로 설치됩니다.

## <a name="publish-to-app-service---visual-studio-2017-and-later"></a>App Service에 게시 - Visual Studio 2017 이상

Visual Studio 2017 이상에서 Azure App Service에 게시하려면 프로젝트의 복사본 파일만 서버에 복사합니다. 따라서 서버 환경을 구성하는 데 필요한 파일을 만들어야 합니다.

1. Visual Studio **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목...** 을 선택합니다. 나타나는 대화 상자에서 “Azure web.config(빠른 CGI)” 템플릿을 선택하고 확인을 선택합니다. 그러면 프로젝트 루트에 `web.config` 파일이 만들어집니다.

1. 경로가 서버의 Python 설치와 일치하도록 `web.config`에서 `PythonHandler` 항목을 수정합니다. 정확한 정보는 [IIS 구성 참조](https://www.iis.net/configreference)(iis.net)를 참조하세요. 예를 들어 Python 3.6.1 x64의 경우 항목은 다음과 같아야 합니다.

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. `web.config`의 `WSGI_HANDLER` 항목을 사용 중인 프레임워크에 적절하게 설정합니다.

    - **Bottle**: 다음과 같이 `app.wsgi_app` 뒤에 괄호를 추가합니다. 이는 해당 개체가 변수가 아닌 함수이기 때문에 필요합니다(`app.py` 참조).

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask**: `WSGI_HANDLER` 값을 `<project_name>.app`으로 변경합니다. 여기서 `<project_name>`은 프로젝트 이름과 일치합니다. `runserver.py`의 `from <project_name> import app` 문을 살펴보면 정확한 식별자를 찾을 수 있습니다. 예를 들어 프로젝트 이름이 “FlaskAzurePublishExample”인 경우 항목은 다음과 같이 표시됩니다.

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django**: Django 프로젝트에 대한 `web.config`에서 두 가지 사항을 변경해야 합니다. 먼저, `WSGI_HANDLER` 값을 `django.core.wsgi.get_wsgi_application()`으로 변경합니다(개체가 `wsgi.py` 파일에 있음).

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        둘째, `DjangoAzurePublishExample`을 사용자의 프로젝트 이름으로 대체하여 `WSGI_HANDLER`에 대한 아래 항목을 추가합니다.

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="DjangoAzurePublishExample.settings" />
        ```

1. **Django 앱만 해당**: Django 프로젝트의 `settings.py` 파일에서 아래와 같이 사이트 URL 도메인을 `ALLOWED_HOSTS`에 추가하고 ‘vspython-test-02.azurewebsites.net’을 다음 URL로 바꿉니다.

    ```python
    # Change the URL to your specific site
    ALLOWED_HOSTS = ['vspython-test-02.azurewebsites.net']
    ```

    배열에 사용자 URL을 추가하지 않으면 다음 오류가 표시됩니다. "DisallowedHost at / Invalid HTTP_HOST header: '\<site URL\>'. '\<site URL\>'를 ALLOWED_HOSTS에 추가해야 할 수도 있습니다."

    배열이 비어 있으면 Django는 ‘localhost’를 자동으로 허용하지만 프로덕션 URL을 추가하면 해당 기능이 제거됩니다. 이러한 이유로 `settings.py`의 개별 개발 및 프로덕션 복사본을 유지 관리하거나, 환경 변수를 사용하여 런타임 값을 제어할 수 있습니다.

1. **솔루션 탐색기**에서 이름이 사용자의 프로젝트와 동일한 폴더를 확장하고, `static` 폴더를 마우스 오른쪽 단추로 클릭하고, **추가 > 새 항목...** 을 선택하고, “Azure 정적 파일 web.config” 템플릿을 선택하고, **확인**을 선택합니다. 그러면 해당 폴더에 대해 Python 프로세스를 비활성화하는 `static` 폴더에 `web.config`가 만들어집니다. 이 구성은 Python 애플리케이션을 사용하지 않고 기본 웹 서버에 정적 파일에 대한 요청을 보냅니다.

1. 프로젝트를 저장한 다음, Visual Studio **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

    ![프로젝트의 상황에 맞는 메뉴에서 게시 명령](media/template-web-publish-command.png)

1. 표시되는 **게시** 탭에서 게시 대상을 선택합니다.

    a. 사용자의 Azure 구독: **Microsoft Azure App Service**를 선택한 다음, **기존 선택**에 이어 **게시**를 선택합니다. 적절한 구독 및 App Service를 선택할 수 있는 대화 상자가 나타납니다. App Service가 나타나지 않으면 임시 App Service에 대해 아래 설명된 대로 다운로드한 게시 프로필을 사용합니다.

    ![Azure 1단계, Visual Studio 2017 이상, 기존 구독에 게시](media/tutorials-common-publish-1a-2017.png)

    b. try.azurewebsites.net에서 임시 App Service를 사용하거나 게시 프로필을 사용해야 하는 경우 **>** 컨트롤을 선택하여 **프로필 가져오기**를 찾아, 해당 옵션을 선택한 다음, **게시**를 선택합니다. 그러면 이전에 다운로드한 `.publishsettings` 파일의 위치에 대한 메시지가 표시됩니다.

    ![Azure 1단계, Visual Studio 2017 이상, 임시 앱 서비스에 게시](media/tutorials-common-publish-1b-2017.png)

1. Visual Studio는 “웹 게시 활동” 창 및 게시 창에 게시 상태를 표시합니다. 게시가 완료되면 사이트 URL에 기본 브라우저가 열립니다. 또한 URL은 게시 창에 표시됩니다.

1. 브라우저가 열리면 “내부 서버 오류가 발생하여 페이지를 표시할 수 없습니다.”라는 메시지가 표시될 수 있습니다. 이 메시지는 서버에서 Python 환경이 완벽하게 구성되지 않았음을 나타내며, 이 경우 다음 단계를 수행합니다.

    a. [Azure App Service에서 Python 관리](managing-python-on-azure-app-service.md)를 다시 참조하여 적절한 Python 사이트 확장이 설치되어 있는지 확인합니다.

    b. `web.config` 파일에서 Python 인터프리터에 대한 경로를 한 번 더 확인합니다. 경로는 사용자가 선택한 사이트 확장의 설치 위치와 정확히 일치해야 합니다.

    c. Kudu 콘솔을 사용하여 사용자 앱의 `requirements.txt` 파일에 나열되어 있는 모든 패키지를 업그레이드합니다. `/home/python361x64`와 같이 `web.config`에서 사용되는 동일한 Python 폴더로 이동하고, [Kudu 콘솔](managing-python-on-azure-app-service.md#azure-app-service-kudu-console) 섹션에 설명된 대로 다음 명령을 실행합니다.

    ```command
    python -m pip install --upgrade -r /home/site/wwwroot/requirements.txt
    ```

    이 명령을 실행할 때 사용 권한 오류가 표시되는 경우 App Service의 기본 Python 설치 중 하나의 폴더가 *아닌* 사이트 확장 폴더에서 명령을 실행하고 있는지 한 번 더 확인합니다. 이러한 기본 환경은 수정할 수 없으므로 패키지 설치에 실패하게 됩니다.

    d. 자세한 오류 출력의 경우, 더 자세한 오류 출력을 제공하는 다음 줄을 `<system.webServer>` 노드 내 `web.config`에 추가합니다.

    ```xml
    <httpErrors errorMode="Detailed"></httpErrors>
    ```

    e. 새 패키지를 설치한 후 App Service를 다시 시작합니다. App Service는 `web.config`가 변경될 때마다 자동 다시 시작을 수행하므로 `web.config`를 변경하는 경우 다시 시작할 필요가 없습니다.

    > [!Tip]
    > 앱의 `requirements.txt` 파일을 변경하는 경우 다시 Kudu 콘솔을 사용하여 해당 파일에 현재 나열되어 있는 모든 패키지를 설치하도록 합니다.

1. 서버 환경을 완전히 구성한 후 브라우저에서 페이지를 새로 고치면 웹앱이 표시됩니다.

    ![App Service에 Bottle, Flask 및 Django 앱 게시의 결과](media/azure-publish-results.png)

## <a name="publishing-to-app-service---visual-studio-2015"></a>App Service에 게시 - Visual Studio 2015

> [!Note]
> 이 프로세스에 대한 짧은 비디오는 [Visual Studio Python 자습서: 웹 사이트 빌드](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)(youtube.com, 3분 10초)에서 볼 수 있습니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **게시**를 선택합니다.

1. **게시** 대화 상자에서 **Microsoft Azure App Service**를 선택합니다.

  ![Azure에 게시 1단계](media/tutorials-common-publish-1.png)

1. 대상을 선택합니다.

    - Azure 구독이 있는 경우 **Microsoft Azure App Service**를 게시 대상으로 선택하고 다음 대화 상자에서 기존 App Service를 선택하거나 **새로 만들기**를 선택하여 새 계정을 만듭니다.
    - try.azurewebsites.net에서 임시 사이트를 사용하는 경우 **가져오기**를 게시 대상으로 선택한 다음 사이트에서 다운로드한 `.publishsettings` 파일을 찾아보고 **확인**을 선택합니다.

1. App Service 세부 정보는 아래에서 **게시** 대화 상자의 **연결** 탭에 표시됩니다.

  ![Azure에 게시 2단계](media/tutorials-common-publish-2.png)

1. 추가 설정을 검토하는 데 필요하면 **다음 >** 을 선택합니다.

1. **게시**를 선택합니다. 애플리케이션을 Azure에 배포하면 해당 사이트에서 기본 브라우저가 열립니다.

이 프로세스의 일환으로, Visual Studio는 다음 단계도 수행합니다.

- 앱의 `wsgi_app` 함수 및 App Service의 기본 Python 3.4 인터프리터에 대한 적절한 포인터를 포함하는 `web.config` 파일을 서버에 만듭니다.
- 프로젝트의 `static` 폴더에서 파일에 대한 프로세스를 해제합니다(이에 대한 규칙은 `web.config`에 있음).
- 가상 환경을 서버에 게시합니다.
- `web.debug.config` 파일 및 디버깅 도구를 추가하여 원격 디버깅을 활성화합니다. Visual Studio 2019 버전 16.4 이전의 경우 디버깅 도구는 ptvsd입니다. Visual Studio 2019 버전 16.5 이상에서는 디버깅 도구가 debugpy입니다.

앞에서 설명한 대로 이러한 자동 단계는 게시 프로세스를 간소화하는 반면, Python 환경을 제어하기는 더 어려워집니다. 예를 들어 `web.config` 파일은 서버에서만 생성되지만 사용자의 프로젝트에는 추가되지 않습니다. 또한 서버 구성에 의존하는 것이 아니라 개발 컴퓨터에서 전체 가상 환경을 복사하기 때문에 게시 프로세스에 시간이 더 걸릴 수 있습니다.

결국 자체 `web.config` 파일을 유지하거나 `requirements.txt`를 사용하여 서버에서 패키지를 직접 유지 관리하고자 할 수 있습니다. 특히 `requirements.txt`를 사용하면 개발 및 서버 환경이 항상 일치함을 보증합니다.
