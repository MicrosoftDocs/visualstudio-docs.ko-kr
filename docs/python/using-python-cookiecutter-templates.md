---
title: Python과 함께 CookieCutter 템플릿 사용
description: Visual Studio는 Python 코드용 템플릿을 검색하고 해당 템플릿으로 프로젝트를 만들기 위한 그래픽 Cookiecutter 확장을 지원합니다.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eeea19b1d2ff4a4d24f27280a48b9ae673406908
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62832195"
---
# <a name="use-the-cookiecutter-extension"></a>Cookiecutter 확장 사용

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/)는 템플릿을 검색하고, 템플릿 옵션을 입력하며, 프로젝트와 파일을 만들 수 있는 그래픽 사용자 인터페이스를 제공합니다. Visual Studio 2017 이상에 포함되어 있으며, 이전 버전의 Visual Studio에서는 개별적으로 설치할 수 있습니다.

Cookiecutter에는 Python 3.3 이상(32비트 또는 64비트) 또는 Anaconda 3 4.2 이상(32비트 또는 64비트)이 필요합니다. 적합한 Python 인터프리터를 사용할 수 없는 경우 Visual Studio에서 경고가 표시됩니다. Visual Studio를 실행하는 중에 Python 인터프리터를 설치하는 경우 Cookiecutter 도구 모음에서 **홈** 단추를 클릭하여 새로 설치된 인터프리터를 검색합니다. (일반적으로 환경에 대한 자세한 내용은 [Python 환경](managing-python-environments-in-visual-studio.md)을 참조하세요.)

설치되면 **보기** > **Cookiecutter 탐색기**를 선택하여 다음 창을 엽니다.

![Cookiecutter 주 창](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter 워크플로

Cookiecutter 작업은 다음 섹션에서 설명한 대로 템플릿을 검색하여 선택하고, 로컬 컴퓨터에 복제하고, 옵션을 설정한 다음, 해당 템플릿에서 코드를 만드는 프로세스입니다.

### <a name="browse-templates"></a>템플릿 찾아보기

Cookiecutter 홈페이지에는 선택하여 다음과 같은 그룹으로 구성할 수 있는 템플릿 목록이 표시됩니다.

| 그룹 | Description |
| --- | --- |
| **설치됨** | 로컬 컴퓨터에 설치된 템플릿입니다. 온라인 템플릿을 사용하면 리포지토리가 *~/.cookiecutters*의 하위 폴더에 자동으로 복제됩니다. **Delete** 키를 눌러 선택한 설치된 템플릿을 삭제할 수 있습니다. |
| **권장** | 권장 피드에서 로드된 템플릿입니다. 기본 피드는 Microsoft에서 큐레이트합니다. 피드 사용자 지정에 대한 자세한 내용은 [Cookiecutter 옵션](#cookiecutter-options)을 참조하세요. |
| **GitHub** | cookiecutter 키워드에 대한 GitHub 검색 결과입니다. GitHub의 결과는 페이지가 매겨져 다시 표시됩니다. 더 많은 결과를 사용할 수 있는 경우 목록 끝에 **추가 로드**가 표시되어 있습니다. |
| **Custom** | 검색 창에 사용자 지정 검색 위치를 입력하면 이 그룹에 표시됩니다. GitHub 리포지토리의 전체 경로 또는 로컬 디스크의 폴더에 대한 전체 경로를 입력할 수 있습니다. |

### <a name="cloning"></a>복제 비교

템플릿을 선택한 후 **다음**을 선택하면 Cookiecutter에서 작업할 로컬 복사본을 만듭니다.

**권장** 또는 **GitHub** 그룹에서 템플릿을 선택하거나 검색 상자에 사용자 지정 URL을 입력하고 템플릿을 선택하면 해당 템플릿이 복제되어 로컬 컴퓨터에 설치됩니다. 해당 템플릿이 Visual Studio의 이전 세션에 설치되는 경우 이전 버전이 자동으로 삭제되고 최신 버전이 복제됩니다.

**설치됨** 그룹에서 템플릿을 선택하거나 검색 상자에 사용자 지정 폴더 경로를 입력하고 템플릿을 선택하면 Visual Studio에서 해당 템플릿을 복제하지 않고 로드합니다.

> [!Important]
> Cookiecutter 템플릿은 *~/.cookiecutters* 단일 폴더 아래에 복제됩니다. 각 하위 폴더의 이름은 GitHub 사용자 이름을 포함하지 않은 Git 리포지토리 이름 뒤에 지정됩니다. 여러 작성자의 이름이 동일한 템플릿을 여러 개 복제하면 충돌이 발생할 수 있습니다. 이 경우 Cookiecutter는 기존 템플릿을 동일한 이름의 다른 템플릿으로 덮어쓰지 못하게 합니다. 다른 템플릿을 설치하려면 먼저 기존 템플릿을 삭제해야 합니다.

### <a name="set-template-options"></a>템플릿 옵션 설정

템플릿을 로컬로 설치하면 Cookiecutter에서 옵션 페이지를 표시합니다. 이 페이지에서 Cookiecutter를 통해 다른 옵션과 함께 파일을 생성하려는 위치를 지정할 수 있습니다.

![Cookiecutter 옵션 페이지](media/cookiecutter-template-options.png)

각 Cookiecutter 템플릿마다 고유한 옵션 집합을 정의하고 각 옵션에 대해 기본값(각 입력 필드에 제안된 텍스트로 표시됨)을 지정합니다. 기본값은 종종 다른 옵션을 사용하는 동적 값인 경우 코드 조각일 수 있습니다.

사용자 구성 파일을 사용하여 특정 옵션에 대한 기본값을 사용자 지정할 수 있습니다. Cookiecutter 확장에서 사용자 구성 파일을 감지하면 템플릿의 기본값을 사용자 구성 파일의 기본값으로 덮어씁니다. 이 동작에 대해서는 Cookiecutter 설명서의 [User Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html)(사용자 구성) 섹션에서 설명합니다.

템플릿에서 코드 생성 후 실행할 특정 Visual Studio 작업을 지정하면 이러한 작업을 건너뛰도록 선택할 수 있는 **완성 시 추가 작업 실행** 추가 옵션이 표시됩니다. 가장 일반적으로 사용되는 작업은 웹 브라우저를 열고, 편집기에서 파일을 열고, 종속성을 설치하는 등입니다.

### <a name="create"></a>생성

옵션을 설정했으면 **만들기**를 선택하여 코드를 생성합니다(출력 폴더가 비어 있지 않은 경우 경고가 표시됨). 템플릿의 출력에 익숙하고 파일 덮어쓰기에 신경 쓰지 않는다면 경고를 해제할 수 있습니다. 그렇지 않으면 **취소**를 선택하고, 빈 출력 폴더를 지정한 다음, 이 출력 폴더에 만든 파일을 수동으로 복사합니다.

파일이 성공적으로 만들어졌으면 Cookiecutter의 **솔루션 탐색기**에서 파일을 여는 옵션을 제공합니다.

![솔루션 탐색기 명령을 보여 주는 Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter 옵션

Cookiecutter 옵션은 **도구** > **옵션** > **Cookiecutter**를 통해 사용할 수 있습니다.

![Cookiecutter 옵션](media/cookiecutter-tools-options.png)

| 옵션 | Description |
| --- | --- |
| **권장 피드 URL** | 권장 템플릿 피드의 위치입니다. URL 또는 로컬 파일에 대한 경로일 수 있습니다. Microsoft에서 큐레이트하는 기본 피드를 사용하려면 URL을 비워 둡니다. 피드는 줄 바꿈 문자로 구분된 템플릿 위치의 간단한 목록을 제공합니다. 큐레이트된 피드에 대한 변경을 요청하려면 [GitHub 원본](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt)에 대한 끌어오기를 요청합니다. |
| **도움말 표시** | Cookiecutter 창 위쪽에 있는 도움말 정보 표시줄의 가시성을 제어합니다. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Visual Studio용 Cookiecutter 템플릿 최적화

Cookiecutter 템플릿 작성의 기본 사항은 [Cookiecutter 설명서](https://cookiecutter.readthedocs.io/en/latest/first_steps.html)(영문)를 참조하세요. Visual Studio용 Cookiecutter 확장은 Cookiecutter v1.4용으로 만들어진 템플릿을 지원합니다.

템플릿 변수의 기본 렌더링은 다음과 같이 데이터 형식(문자열 또는 목록)에 따라 달라집니다.

- 문자열: 변수 이름의 레이블, 값 입력을 위한 텍스트 상자 및 기본값을 보여 주는 워터마크입니다. 텍스트 상자의 도구 설명에는 기본값이 표시됩니다.
- 목록: 변수 이름의 레이블 및 값 선택을 위한 콤보 상자입니다. 콤보 상자의 도구 설명에는 기본값이 표시됩니다.

Visual Studio와 관련된 *cookiecutter.json* 파일에 추가 메타데이터를 지정하여 이 렌더링에서 향상할 수 있습니다(Cookiecutter CLI에서는 무시됨). 모든 속성은 선택적입니다.

| 속성 | Description |
| --- | --- |
| 레이블 | 변수 이름 대신 변수의 편집기 위에 표시되는 항목을 지정합니다. |
| Description | 해당 변수의 기본값 대신 편집 컨트롤에 표시되는 도구 설명을 지정합니다. |
| URL | URL을 표시하는 도구 설명을 사용하여 레이블을 하이퍼링크로 변경합니다. 하이퍼링크를 클릭하면 사용자의 기본 브라우저를 해당 URL로 엽니다. |
| 선택기 | 변수에 대한 편집기의 사용자 지정을 허용합니다. 현재 지원되는 선택기는 다음과 같습니다.<ul><li>`string`: 문자열에 대한 기본 표준 텍스트 상자입니다.</li><li>`list`: 목록에 대한 기본 표준 콤보 상자입니다.</li><li>`yesno`: 문자열에 대해 `y`와 `n` 중에서 선택하는 콤보 상자입니다.</li><li>`odbcConnection`: 데이터베이스 연결 대화 상자를 호출하는 **...** 단추가 있는 텍스트 상자입니다.</li></ul> |

예제:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Visual Studio 작업 실행

Cookiecutter에는 *생성 후 후크*라는 기능이 있으므로 파일을 생성한 후에 임의의 Python 코드를 실행할 수 있습니다. 이 기능은 유연하지만 Visual Studio에 쉽게 액세스할 수 없습니다.

예를 들어 Visual Studio 편집기 또는 웹 브라우저에서 파일을 열거나, 가상 환경을 만들고 패키지 요구 사항을 설치하도록 사용자에게 요청하는 Visual Studio UI를 트리거할 수 있습니다.

이러한 시나리오를 허용하기 위해 Visual Studio에서는 사용자가 *솔루션 탐색기*에서 생성된 파일을 열거나 파일이 기존 프로젝트에 추가된 후에 실행할 명령을 설명하는 확장 메타데이터를 **cookiecutter.json**에서 찾습니다. (사용자는 다시 한번 템플릿 옵션에서 **완성 시 추가 작업 실행**을 선택 취소하여 작업 실행을 옵트아웃(opt out)할 수 있습니다.)

예제:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

명령은 이름으로 지정되므로 지역화되지 않은 이름(영문)을 사용하여 Visual Studio의 지역화된 설치에서 작동해야 합니다. Visual Studio **명령** 창에서 명령 이름을 테스트하고 검색할 수 있습니다.

단일 인수를 전달하려면 앞의 예제와 같이 해당 인수를 문자열로 지정합니다.

인수를 전달할 필요가 없으면 빈 문자열로 남겨 두거나 JSON에서 생략합니다.

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

여러 인수에 대해서는 배열을 사용합니다. 스위치의 경우 스위치와 해당 값을 별도의 인수로 분할하고 적절한 따옴표로 묶습니다. 다음은 그 예입니다.

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

인수는 다른 Cookiecutter 변수를 참조할 수 있습니다. 위의 예제에서 내부 `_output_folder_path` 변수는 생성된 파일의 절대 경로를 구성하는 데 사용됩니다.

`Python.InstallProjectRequirements` 명령은 기존 프로젝트에 파일을 추가할 때만 작동합니다. 이 제한은 명령이 **솔루션 탐색기**에서 Python 프로젝트로 처리되고, **솔루션 탐색기** - **폴더 보기**에서 메시지를 받을 프로젝트가 없기 때문에 발생합니다. 향후 릴리스에서는 이 제한 사항을 해결하고 전반적으로 더 나은 **폴더 보기**를 지원하겠습니다.

## <a name="troubleshooting"></a>문제 해결

### <a name="error-loading-template"></a>템플릿 로드 중 오류

일부 템플릿이 *cookiecutter.json*에서 부울 등의 잘못된 데이터 형식을 사용 중일 수 있습니다. 템플릿 정보 창에서 **문제** 링크를 선택하여 이러한 인스턴스를 템플릿 작성자에게 보고합니다.

### <a name="hook-script-failed"></a>후크 스크립트 실패

일부 템플릿에서 Cookiecutter UI와 호환되지 않는 생성 후 스크립트를 사용할 수도 있습니다. 예를 들어 터미널 콘솔을 사용하지 않기 때문에 사용자에게 입력을 쿼리하는 스크립트는 실패합니다.

### <a name="hook-script-not-supported-on-windows"></a>Windows에서 지원하지 않는 후크 스크립트

게시 스크립트가 *.sh*인 경우 Windows 컴퓨터의 애플리케이션과 연결되지 않을 수 있습니다. Windows 스토어에서 호환되는 애플리케이션을 찾도록 요청하는 Windows 대화 상자가 나타날 수 있습니다.

### <a name="templates-with-known-issues"></a>알려진 문제점이 있는 템플릿

복제 실패:

- **wildfish/cookiecutter-django-crud**(하위 폴더 이름에 잘못된 `|` 문자)
- **cookiecutter-pyvanguard**(하위 폴더 이름에 잘못된 `|` 문자)

로드 실패:

- **chrisdev/wagtail-cookiecutter-foundation**(*cookiecutter.json*에서 부울 형식 사용)
- **quintoandar/cookiecutter-android**(템플릿 폴더 없음)

실행 실패:

- **iknite/cookiecutter-ansible-role**(사후 후크 스크립트에 콘솔 입력 필요)
- **benregn/cookiecutter-django-ansible**(Jinja 오류)

bash 사용(치명적이지 않음):

- **openstack-dev/cookiecutter**
