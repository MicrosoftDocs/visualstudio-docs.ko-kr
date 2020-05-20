---
title: Python용 웹 애플리케이션 템플릿
description: Visual Studio는 Bottle, Flask 및 Django 프레임워크를 사용하는 Python 웹 애플리케이션용 템플릿을 제공합니다. 지원에는 디버깅 구성 및 Azure App Service에 게시하는 것이 포함됩니다.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 73420f5fa6a90638f4a3dbbdf484178c5e177ce9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307108"
---
# <a name="python-web-application-project-templates"></a>Python 웹 애플리케이션 프로젝트 템플릿

Visual Studio의 Python은 다양한 프레임워크를 처리하도록 구성할 수 있는 디버그 시작 관리자 및 프로젝트 템플릿을 통해 Bottle, Flask 및 Django 프레임워크에서 웹 프로젝트 개발을 지원합니다. 이러한 템플릿에는 필요한 종속성을 선언하는 *requirements.txt* 파일이 포함됩니다. 이러한 템플릿 중 하나에서 프로젝트를 만들 때 Visual Studio에서 해당 패키지를 설치하라는 메시지가 표시됩니다. 이 아티클의 뒷부분에 나오는 [프로젝트 요구 사항 설치](#install-project-requirements)를 참조하세요.

Pyramid와 같은 다른 프레임워크에 대한 일반 **웹 프로젝트** 템플릿을 사용할 수도 있습니다. 이 경우, 프레임워크가 템플릿과 함께 설치되지 않습니다. 대신 프로젝트에 사용 중인 환경에 필요한 패키지를 설치합니다([Python 환경 창 - 패키지 탭](python-environments-window-tab-reference.md#packages-tab)을 참조하세요).

Python 웹앱을 Azure에 배포하는 방법에 대한 정보는 [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)를 참조하세요.

## <a name="use-a-project-template"></a>프로젝트 템플릿 사용

**파일** > **새로 만들기** > **프로젝트**를 사용하여 템플릿에서 프로젝트를 만듭니다. 웹 프로젝트에 대한 템플릿을 보려면 대화 상자의 왼쪽에서 **Python** > **웹**를 선택합니다. 그런 다음, 원하는 템플릿을 선택하여 프로젝트 및 솔루션의 이름을 제공하고 솔루션 디렉터리와 Git 리포지토리에 대한 옵션을 설정한 후 **확인**을 선택합니다.

![웹앱의 새 프로젝트 대화 상자](media/projects-new-project-dialog-web.png)

앞에서 설명한 일반 **웹 프로젝트** 템플릿은 코드가 없고 Python 프로젝트라는 사실 외에 다른 가정이 없는 빈 Visual Studio 프로젝트만 제공합니다. **Azure Cloud Service** 템플릿에 대한 자세한 내용은 [Python용 Azure Cloud Service 프로젝트](python-azure-cloud-service-project-template.md)를 참조하세요.

다른 모든 템플릿은 Bottle, Flask 또는 Django 웹 프레임워크를 기반으로 하며, 다음 섹션에 설명된 대로 세 개의 일반 그룹으로 나뉩니다. 이러한 템플릿으로 만든 앱에는 충분한 코드가 포함되어 로컬에서 앱을 실행하고 디버그할 수 있습니다. 또한 각 항목은 프로덕션 웹 서버에서 사용하는 데 필요한 [WSGI 앱 개체](https://www.python.org/dev/peps/pep-3333/)(python.org)를 제공합니다.

### <a name="blank-group"></a>빈 그룹

모든 **빈 \<프레임워크> 웹 프로젝트** 템플릿은 *requirements.txt* 파일에 선언된 거의 최소한의 상용구 코드와 필요한 종속성을 사용하여 프로젝트를 만듭니다.

| 템플릿 | Description |
| --- | --- |
| **빈 Bottle 웹 프로젝트** | 매우 짧은 인라인 페이지 템플릿을 사용하여 `<name>`을 에코하는 `/` 및 `/hello/<name>` 페이지의 홈페이지를 사용하여 *app.py*에 최소 앱을 생성합니다. |
| **빈 Django 웹 프로젝트** | 코어 Django 사이트 구조를 사용하지만 Django 앱은 포함되지 않은 Django 프로젝트를 생성합니다. 자세한 내용은 [Django 템플릿](python-django-web-application-project-template.md) 및 [Django 알아보기 1단계](learn-django-in-visual-studio-step-01-project-and-solution.md)를 참조하세요. |
| **빈 Flask 웹 프로젝트** | 최소 앱을 `/`에 대한 단일 “Hello World!” 페이지로 생성합니다. 이 앱은 [빠른 시작: Visual Studio를 사용하여 첫 번째 Python 웹앱 만들기](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)의 자세한 단계를 수행한 결과와 유사합니다. [Flask 알아보기 1단계](learn-flask-visual-studio-step-01-project-solution.md)도 참조하세요.

### <a name="web-group"></a>웹 그룹

모든 **\<프레임워크> 웹 프로젝트** 템플릿은 선택한 프레임워크와 관계없이 동일한 디자인으로 시작 웹앱을 만듭니다. 이 앱에는 부트스트랩을 사용하는 탐색 모음 및 반응형 디자인과 함께 홈, 정보 및 연락처 페이지가 포함됩니다. 각 앱은 정적 파일(CSS, JavaScript 및 글꼴)을 제공하도록 적절하게 구성되며, 프레임워크에 적합한 페이지 템플릿 메커니즘을 사용합니다.

| 템플릿 | Description |
| --- | --- |
| **Bottle 웹 프로젝트** | 정적 파일이 *static* 폴더에 포함되고 *app.py*의 코드를 통해 처리되는 앱을 생성합니다. 개별 페이지에 대한 라우팅은 *routes.py*에 포함되며, *보기* 폴더에는 페이지 템플릿이 포함되어 있습니다.|
| **Django 웹 프로젝트** | 세 개의 페이지, 인증 지원 및 SQLite 데이터베이스(데이터 모델 없음)를 사용하여 Django 프로젝트 및 Django 앱을 생성합니다. 자세한 내용은 [Django 템플릿](python-django-web-application-project-template.md) 및 [Django 알아보기 4단계](learn-django-in-visual-studio-step-04-full-django-project-template.md)를 참조하세요. |
| **Flask 웹 프로젝트** | 정적 파일이 *static* 폴더에 포함되는 앱을 생성합니다. *views.py*의 코드는 *templates* 폴더에 포함된 Jinja 엔진을 사용하는 페이지 템플릿을 사용하여 라우팅을 처리합니다. *runserver.py*파일은 시작 코드를 제공합니다. [Flask 알아보기 4단계](learn-flask-visual-studio-step-04-full-flask-project-template.md)를 참조하세요. |
| **Flask/Jade 웹 프로젝트** | **Flask 웹 프로젝트** 템플릿과 동일한 앱을 생성하지만 Jinja 템플레이팅 엔진용 Jade 확장을 사용합니다. |

### <a name="polls-group"></a>설문 조사 그룹

**설문 조사 \<프레임워크> 웹 프로젝트** 템플릿은 사용자가 다양한 설문 조사 질문에 투표할 수 있는 시작 웹앱을 만듭니다. 각 앱은 데이터베이스를 사용하여 설문 조사 및 사용자 응답을 관리하는 **웹** 프로젝트 템플릿의 구조를 기반으로 합니다. 앱에는 *samples.json* 파일에서 설문 조사를 로드하는 적절한 데이터 모델과 특수한 앱 페이지(/seed)가 포함됩니다.

| 템플릿 | Description |
| --- | --- |
| **설문 조사 Bottle 웹 프로젝트** | 메모리 내 데이터베이스, MongoDB 또는 Azure Table Storage에 대해 실행할 수 있는 앱을 생성하며, `REPOSITORY_NAME` 환경 변수를 사용하여 구성합니다. 데이터 모델 및 데이터 저장소 코드는 *모델* 폴더에 포함되고 *settings.py* 파일에는 사용되는 데이터 저장소를 확인하는 코드가 포함되어 있습니다. |
| **설문 조사 Django 웹 프로젝트** | 세 개의 페이지와 SQLite 데이터베이스를 사용하여 Django 프로젝트 및 Django 앱을 생성합니다. 인증된 관리자가 설문 조사를 만들고 관리할 수 있도록 하는 Django 관리 인터페이스에 대한 사용자 지정을 포함합니다. 자세한 내용은 [Django 템플릿](python-django-web-application-project-template.md) 및 [Django 알아보기 6단계](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)를 참조하세요. |
| **설문 조사 Flask 웹 프로젝트** | 메모리 내 데이터베이스, MongoDB 또는 Azure Table Storage에 대해 실행할 수 있는 앱을 생성하며, `REPOSITORY_NAME` 환경 변수를 사용하여 구성합니다. 데이터 모델 및 데이터 저장소 코드는 *모델* 폴더에 포함되고 *settings.py* 파일에는 사용되는 데이터 저장소를 확인하는 코드가 포함되어 있습니다. 앱은 페이지 템플릿에 Jinja 엔진을 사용합니다. [Flask 알아보기 5단계](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)를 참조하세요. |
| **설문 조사 Flask/Jade 웹 프로젝트** | **설문 조사 Flask 웹 프로젝트** 템플릿과 동일한 앱을 생성하지만 Jinja 템플레이팅 엔진용 Jade 확장을 사용합니다. |

## <a name="install-project-requirements"></a>프로젝트 요구 사항 설치

프레임워크별 템플릿에서 프로젝트를 만들 때 pip를 사용하여 필요한 패키지를 설치할 수 있는 대화 상자가 나타납니다. 웹 프로젝트에 대해 [가상 환경](selecting-a-python-environment-for-a-project.md#use-virtual-environments)을 사용하여 웹 사이트를 게시할 때 올바른 종속성이 포함되도록 하는 것이 좋습니다.

![프로젝트 템플릿에 대해 필요한 패키지를 설치하는 대화 상자](media/template-web-requirements-txt-wizard.png)

소스 제어를 사용하는 경우 가상 환경은 *requirements.txt*만 사용하여 다시 만들 수 있기 때문에 일반적으로 가상 환경 폴더를 생략합니다. 폴더를 제외하는 가장 좋은 방법은 먼저 위에 표시된 프롬프트에서 **직접 설치**를 선택한 다음, 가상 환경을 만들기 전에 자동 커밋을 사용하지 않도록 설정하는 것입니다. 자세한 내용은 [Django 자습서 학습 - 1-2 및 1-3단계](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) 및 [Flask 자습서 학습 - 1-2 및 1-3단계](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)를 참조하세요.

Microsoft Azure App Service에 배포할 때는 [사이트 확장](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019)으로 Python 버전을 선택하고 패키지를 수동으로 설치합니다. 또한 Azure App Service는 Visual Studio에서 배포할 때 *requirements.txt* 파일에서 패키지를 자동으로 설치하지 **않으므로**[aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md)의 구성 세부 정보를 따릅니다.

Microsoft Azure Cloud Services는 *requirements.txt* 파일을 *지원합니다*. 자세한 내용은 [Azure Cloud Service 프로젝트](python-azure-cloud-service-project-template.md)를 참조하세요.

## <a name="debugging"></a>디버깅

디버깅을 위해 웹 프로젝트가 시작되면 Visual Studio는 임의 포트에서 로컬 웹 서버를 시작하고 해당 주소 및 포트로 기본 브라우저를 엽니다. 추가 옵션을 지정하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**를 선택하고 **웹 시작 관리자** 탭을 선택합니다.

![일반 웹 템플릿에 대한 웹 시작 관리자 속성](media/template-web-launcher-properties.png)

**디버그** 그룹에서:

- **경로 검색**, **스크립트 인수**, **인터프리터 인수** 및 **인터프리터 경로**: 이러한 옵션은 [일반 디버깅](debugging-python-in-visual-studio.md)과 동일합니다.
- **URL 시작**: 브라우저에서 열리는 URL을 지정합니다. 기본값은 `localhost`입니다.
- **포트 번호**: URL에 지정되지 않은 경우 사용할 포트입니다(기본적으로 Visual Studio에서 자동으로 선택). 이 설정을 사용하면 로컬 디버그 서버에서 수신 대기하는 포트를 구성하기 위해 템플릿에서 사용하는 `SERVER_PORT` 환경 변수의 기본값을 재정의할 수 있습니다.

**서버 실행 명령** 및 **서버 디버그 명령** 그룹의 속성(후자는 아래 이미지에 표시됨)에 따라 웹 서버가 시작되는 방식이 결정됩니다. 많은 프레임워크에서는 현재 프로젝트 외부에서 스크립트를 사용해야 하기 때문에 여기에서 스크립트를 구성할 수 있으며 시작 모듈의 이름을 매개 변수로 전달할 수 있습니다.

- **명령**: Python 스크립트( *\*.py* 파일), 모듈 이름(`python.exe -m module_name`에서와 같이) 또는 단일 코드 줄(`python.exe -c "code"`에서와 같이)일 수 있습니다. 드롭다운의 값은 이러한 형식 중 어떤 것이 의도되었는지를 나타냅니다.
- **인수**: 이러한 인수는 명령줄에서 명령 다음에 전달됩니다.
- **환경**: 환경 변수를 지정하는 줄 바꿈 문자로 구분된 \<NAME>=\<VALUE> 쌍 목록입니다. 이러한 변수는 포트 번호 및 검색 경로 등 환경을 수정할 수 있는 모든 속성 뒤에 설정되므로 이러한 값을 덮어쓸 수 있습니다.

MSBuild 구문으로 모든 프로젝트 속성 또는 환경 변수를 지정할 수 있습니다. 예를 들면 `$(StartupFile) --port $(SERVER_PORT)`입니다.
`$(StartupFile)`은 시작 파일에 대한 상대 경로이며 `{StartupModule}`은 시작 파일의 가져올 수 있는 이름입니다. `$(SERVER_HOST)` 및 `$(SERVER_PORT)`는 **시작 URL** 및 **포트 번호** 속성으로 자동으로 설정되거나 **환경** 속성으로 설정되는 일반 환경 변수입니다.

> [!Note]
> **서버 실행 명령**의 값은 **디버그** > **서버 시작** 명령이나 **Ctrl**+**F5**에 사용되며 **서버 디버그 명령** 그룹의 값은 **디버그** > **서버 디버그 시작** 명령이나 **F5**에 사용됩니다.

### <a name="sample-bottle-configuration"></a>샘플 Bottle 구성

**Bottle 웹 프로젝트** 템플릿은 필요한 구성을 수행하는 상용구 코드를 포함합니다. 그러나 가져온 bottle 앱에는 이 코드가 포함되어 있지 않을 수 있으며 이 경우 다음 설정으로 설치된 `bottle` 모듈을 사용하여 앱을 시작합니다.

- **서버 실행 명령** 그룹:
  - **명령**: `bottle`(모듈)
  - **인수**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **서버 디버그 명령** 그룹:
  - **명령**: `bottle`(모듈)
  - **인수** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload` 옵션은 디버깅에 Visual Studio를 사용할 때는 권장되지 않습니다.

### <a name="sample-pyramid-configuration"></a>샘플 Pyramid 구성

Pyramid 앱은 현재 `pcreate` 명령줄 도구를 사용하여 최적으로 만들어집니다. 앱을 만들었으면 [**기존 Python 코드에서**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) 템플릿을 사용하여 가져올 수 있습니다. 그런 다음 **일반 웹 프로젝트** 사용자 지정을 선택하여 옵션을 구성합니다. 이러한 설정은 가상 환경의 `..\env`에 Pyramid가 설치되어 있다고 가정합니다.

- **디버그** 그룹:
  - **서버 포트**: 6543(또는 *.ini* 파일에 구성된 모든 항목)

- **서버 실행 명령** 그룹:
  - 명령: `..\env\scripts\pserve-script.py`(스크립트)
  - 인수: `Production.ini`

- **서버 디버그 명령** 그룹:
  - 명령: `..\env\scripts\pserve-script.py`(스크립트)
  - 인수: `Development.ini`

> [!Tip]
> Pyramid 앱은 일반적으로 프로젝트 루트 아래의 폴더이므로 프로젝트의 **작업 디렉터리** 속성을 구성해야 할 수 있습니다.

### <a name="other-configurations"></a>기타 구성

공유하려는 다른 프레임워크 설정이 있거나 다른 프레임워크 설정을 요청하려면 [GitHub에서 문제](https://github.com/Microsoft/PTVS/issues)를 엽니다.

## <a name="convert-a-project-to-azure-cloud-service"></a>프로젝트를 Azure Cloud Service로 변환

**Microsoft Azure 클라우드 서비스 프로젝트로 변환** 명령(아래 이미지)은 클라우드 서비스 프로젝트를 솔루션에 추가합니다. 이 프로젝트에는 사용되는 가상 컴퓨터 및 서비스에 대한 배포 설정 및 구성이 포함됩니다. 클라우드 서비스에 배포하려면 클라우드 프로젝트에서 **Publish** 명령을 사용합니다. Python 프로젝트에서 **Publish** 명령을 사용하면 여전히 웹 사이트에 배포됩니다. 자세한 내용은 [Azure Cloud Service 프로젝트](python-azure-cloud-service-project-template.md)를 참조하세요.

![Microsoft Azure Cloud Service 프로젝트 명령으로 변환](media/template-web-convert-menu.png)

## <a name="see-also"></a>참고 항목

- [Python 항목 템플릿 참조](python-item-templates.md)
- [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)
