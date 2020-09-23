---
title: Visual Studio 1단계, Flask 기본 사항에서 Flask 자습서 알아보기
titleSuffix: ''
description: 필수 구성 요소, Git 및 가상 환경을 비롯하여 Visual Studio 프로젝트의 컨텍스트에서 Flask 기본 사항을 살펴봅니다.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 018b9a6707ea46a9b1c46f820faf7bd47dac1ff9
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809900"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>자습서: Visual Studio에서 Flask 웹 프레임워크 시작

[Flask](https://palletsprojects.com/p/flask/)는 URL 라우팅 및 페이지 렌더링을 위한 기본 사항을 제공하는 웹 애플리케이션용 경량 Python 프레임워크입니다.

Flask는 폼 유효성 검사, 데이터베이스 추상화, 인증 등과 같은 기능을 직접 제공하지 않기 때문에 "마이크로" 프레임워크라고 합니다. 대신 이러한 기능은 Flask *확장*이라는 특별한 Python 패키지를 통해 제공됩니다. 확장은 Flask와 원활하게 통합되어 Flask의 일부인 것처럼 보입니다. 예를 들어 Flask 자체는 페이지 템플릿 엔진을 제공하지 않습니다. 템플레이팅은 이 자습서에서 설명한 대로 Jinja 및 Jade와 같은 확장에서 제공됩니다.

이 자습서에서는 다음 작업 방법을 알아봅니다.

> [!div class="checklist"]
> - “빈 Flask 웹 프로젝트” 템플릿을 사용하여 Git 리포지토리에 기본 Flask 프로젝트 만들기(1단계)
> - 한 페이지의 Flask 앱을 만들고 템플릿을 사용하여 해당 페이지 렌더링(2단계)
> - 정적 파일 제공, 페이지 추가 및 템플릿 상속 사용(3단계)
> - Flask 웹 프로젝트 템플릿을 사용하여 여러 페이지로 구성되고 반응이 빠른 디자인의 앱 만들기(4단계)
> - 여론 조사 Flask 웹 프로젝트 템플릿을 사용하여 다양한 스토리지 옵션(Azure 스토리지, MongoDB 또는 메모리)을 사용하는 여론 조사 앱을 만들 수 있습니다.

이 단계를 진행하는 동안 세 개의 개별 프로젝트가 포함된 단일 Visual Studio 솔루션을 만듭니다. Visual Studio에 포함된 여러 Flask 프로젝트 템플릿을 사용하여 프로젝트를 만듭니다. 프로젝트를 동일한 솔루션에 유지하면 서로 다른 파일 간에 쉽게 전환하여 비교할 수 있습니다.

> [!Note]
> 이 자습서는 Flask에 대해 자세히 배우고, 자신의 프로젝트에 보다 광범위한 시작점을 제공하는 여러 Flask 프로젝트 템플릿을 사용하는 방법에 대해 배운다는 점에서 [Flask 빠른 시작](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)과 다릅니다. 예를 들어 프로젝트 템플릿은 빠른 시작에 표시된 대로 수동으로 패키지를 설치하지 않고, 프로젝트를 생성할 때 자동으로 Flask 패키지를 설치합니다.

## <a name="prerequisites"></a>사전 요구 사항

- 다음 옵션을 포함하는 Windows의 Visual Studio 2017 이상:
  - **Python 개발** 워크로드(설치 관리자의 **워크로드**) 자세한 내용은 [Visual Studio에서 Python 지원 설치](installing-python-support-in-visual-studio.md)를 참조하세요.
  - **코드 도구**의 **개별 구성 요소** 탭에 있는 **Git for Windows** 및 **Visual Studio용 GitHub 확장**

Flask 프로젝트 템플릿은 Visual Studio용 Python 도구의 모든 이전 버전에 포함되어 있지만 세부 정보는 이 자습서에 설명된 내용과 다를 수 있습니다.

현재 Mac용 Visual Studio에서는 Python 개발이 지원되지 않습니다. Mac 및 Linux의 경우, [Visual Studio Code의 Python 확장](https://code.visualstudio.com/docs/python/python-tutorial)을 사용합니다.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>1-1단계: Visual Studio 프로젝트 및 솔루션 만들기

1. Visual Studio에서 **파일** > **새로 만들기** > **프로젝트**를 선택하고 “Flask”를 검색한 후 **빈 Flask 웹 프로젝트** 템플릿을 선택합니다. 템플릿은 왼쪽 목록의 **Python** > **웹** 아래에도 있습니다.

    ![빈 Flask 웹 프로젝트에 대한 Visual Studio의 새 프로젝트 대화 상자](media/flask/step01-new-blank-project.png)

1. 대화 상자 아래쪽에 있는 필드에서 위 그래픽에 표시된 대로 다음 정보를 입력하고 **확인**을 선택합니다.

    - **이름**: Visual Studio 프로젝트의 이름을 **BasicProject**로 설정합니다. 이 이름은 Flask 프로젝트에도 사용됩니다.
    - **위치**: Visual Studio 솔루션 및 프로젝트를 만들 위치를 지정합니다.
    - **솔루션 이름**: 이 자습서의 여러 프로젝트에 대한 컨테이너로 솔루션에 적합한 **LearningFlask**로 설정합니다.
    - **솔루션용 디렉터리 만들기**: 설정된 상태(기본값)로 유지합니다.
    - **새 Git 리포지토리 만들기**: Visual Studio에서 솔루션을 만들 때 로컬 Git 리포지토리를 만들도록 이 옵션(기본적으로 선택 취소되어 있음)을 선택합니다. 이 옵션이 표시되지 않으면 Visual Studio 설치 관리자를 실행하고 **코드 도구** 아래의 **개별 구성 요소** 탭에 **Windows용 Git** 및 **Visual Studio용 GitHub 확장**을 추가합니다.

1. 잠시 후 Visual Studio에는 **이 프로젝트에는 외부 패키지가 필요합니다.** 라는 대화 상자가 표시됩니다(아래 표시). 이 대화 상자는 템플릿에 최신 Flask 1.x 패키지를 참조하는 *requirements.txt* 파일이 포함되어 있기 때문에 나타납니다. 정확한 종속성을 확인하려면 **필수 패키지 표시**를 선택하세요.

    ![프로젝트에 외부 패키지가 필요하다는 프롬프트](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. **직접 설치** 옵션을 선택합니다. 바로 가상 환경을 만들어 소스 제어에서 제외되는지 확인합니다. 이 환경은 언제든지 *requirements.txt*에서 만들 수 있습니다.

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>1-2단계: Git 컨트롤을 검사하고 원격 리포지토리에 게시

**새 프로젝트** 대화 상자에서 **새 Git 리포지토리 만들기**를 선택했기 때문에 프로젝트는 만들기 프로세스가 완료되는 즉시 로컬 소스 제어에 이미 커밋되었습니다. 이 단계에서는 Visual Studio의 Git 컨트롤과 소스 제어를 사용하는 **팀 탐색기** 창에 대해 알아봅니다.

1. Visual Studio 주 창의 아래쪽 모서리에 있는 Git 컨트롤을 검사합니다. 왼쪽에서 오른쪽으로 이러한 컨트롤에는 푸시되지 않은 커밋, 커밋되지 않은 변경 내용, 리포지토리 이름 및 현재 분기가 표시됩니다.

    ![Visual Studio 창의 Git 컨트롤](media/flask/step01-git-controls.png)

    > [!Note]
    > **새 프로젝트** 대화 상자에서 **새 Git 리포지토리 만들기**를 선택하지 않으면 Git 컨트롤에는 로컬 리포지토리를 만드는 **소스 제어에 추가** 명령만 표시됩니다.
    >
    > ![리포지토리를 만들지 않은 경우 소스 제어에 추가가 Visual Studio에 나타남](media/tutorials-common/step01-git-add-to-source-control.png)

1. 변경 내용 단추를 선택하면 Visual Studio에서 **팀 탐색기** 창의 **변경 내용** 페이지가 열립니다. 새로 만든 프로젝트는 이미 자동으로 소스 제어에 커밋되었기 때문에 보류 중인 변경 내용이 표시되지 않습니다.

    ![변경 내용 페이지의 팀 탐색기 창](media/flask/step01-team-explorer-changes.png)

1. Visual Studio 상태 표시줄에서 푸시되지 않은 커밋 단추(**2**가 표시된 위쪽 화살표)를 선택하여 **팀 탐색기**에서 **동기화** 페이지를 엽니다. 로컬 리포지토리만 있으므로 이 페이지에서는 다른 원격 리포지토리에 리포지토리를 게시하는 간단한 옵션을 제공합니다.

    ![소스 제어에 사용 가능한 Git 리포지토리 옵션을 보여주는 팀 탐색기 창](media/flask/step01-team-explorer.png)

    자신만의 프로젝트에 원하는 서비스를 선택할 수 있습니다. 이 자습서에서는 자습서에 대해 완료된 샘플 코드가 [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) 리포지토리에서 유지 관리되는 GitHub의 사용을 보여 줍니다.

1. **게시** 컨트롤 중 하나를 선택하면 **팀 탐색기**에서 추가 정보를 묻는 메시지가 표시됩니다. 예를 들어 이 자습서에 대한 샘플을 게시하려면 먼저 리포지토리 자체를 만들어야 했습니다. 이 경우 **원격 리포지토리에 푸시** 옵션이 리포지토리의 URL과 함께 사용되었습니다.

    ![기존 원격 리포지토리에 푸시에 대한 팀 탐색기 창](media/flask/step01-push-to-github.png)

    기존 리포지토리가 없는 경우 **GitHub에 게시** 및 **Azure DevOps에 푸시** 옵션을 사용하여 Visual Studio 내에서 직접 만들 수 있습니다.

1. 이 자습서를 진행하면서 주기적으로 Visual Studio의 컨트롤을 사용하여 변경 내용을 커밋하고 푸시하는 습관을 기르는 것이 좋습니다. 이 자습서에서는 적절한 시점에 알려줍니다.

> [!Tip]
> **팀 탐색기** 내에서 신속하게 이동하려면 헤더(위 이미지에서 **변경 내용** 또는 **푸시**로 표시)를 선택하여 사용 가능한 페이지의 팝업 메뉴를 표시하세요.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>질문: 프로젝트를 시작할 때부터 소스 제어를 사용하면 어떤 이점이 있나요?

대답: 무엇보다도 처음부터 소스 제어를 사용하면 특히 원격 리포지토리를 사용하는 경우에도 정기적으로 프로젝트를 오프사이트에 백업할 수 있습니다. 로컬 파일 시스템에서만 프로젝트를 유지 관리하는 것과 달리 소스 제어는 단일 파일이나 전체 프로젝트를 이전 상태로 되돌릴 수 있는 간단한 기능과 전체 변경 기록도 제공합니다. 이 변경 기록은 회귀(테스트 실패)의 원인을 확인하는 데 도움이 됩니다. 또한 소스 제어는 여러 명의 사용자가 한 프로젝트에서 작업하는 경우 덮어쓰기를 관리하고 충돌 해결을 제공하기 때문에 꼭 필요합니다. 마지막으로, 기본적으로 자동화 형태인 소스 제어는 빌드, 테스트 및 릴리스 관리를 자동화하는 데 적합합니다. 실제로 프로젝트에 DevOps를 사용하는 첫 번째 단계이며, 진입 장벽이 매우 낮기 때문에 처음부터 소스 제어를 사용하지 않을 이유가 없습니다.

자동화로서 소스 제어에 대한 자세한 내용은 모바일 앱용으로 작성되고 웹앱에도 적용되는 MSDN Magazine의 [The Source of Truth: The Role of Repositories in DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops)(정보의 출처: DevOps에서 리포지토리의 역할) 문서를 참조하세요.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>질문: Visual Studio에서 새 프로젝트를 자동 커밋하지 않도록 할 수 있나요?

대답: 예. 자동 커밋을 사용하지 않도록 설정하려면 **팀 탐색기**의 **설정** 페이지로 이동하여 **Git** > **전역 설정**을 선택하고 **기본적으로 병합 후 변경 내용 커밋**이라는 옵션을 선택 취소한 후 **업데이트**를 선택합니다.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>1-3단계: 가상 환경을 만들고 소스 제어에서 제외

프로젝트에 대해 소스 제어를 구성했으므로 프로젝트에 필요한 Flask 패키지로 가상 환경을 만들 수 있습니다. 그런 다음, **팀 탐색기**를 사용하여 소스 제어에서 환경의 폴더를 제외할 수 있습니다.

1. **솔루션 탐색기**에서 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **가상 환경 추가**를 선택합니다.

    ![솔루션 탐색기의 가상 환경 추가 명령](media/flask/step01-add-virtual-environment-command.png)

1. **가상 환경 추가** 대화 상자는 **requirements.txt 파일이 있습니다.** 라는 메시지와 함께 나타납니다. 이 메시지는 Visual Studio에서 해당 파일을 사용하여 가상 환경을 구성함을 나타냅니다.

    ![requirements.txt 메시지가 표시된 가상 환경 추가 대화 상자](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. **만들기**를 선택하여 기본값을 그대로 사용합니다. 원하는 경우 가상 환경의 이름을 변경할 수 있지만 하위 폴더의 이름만 변경되고 `env`는 표준 규칙입니다.

1. 프롬프트가 표시되면 관리자 권한에 동의하고 Visual Studio에서 패키지를 다운로드하여 설치하는 동안 잠시 기다립니다. 이는 Flask 및 종속성에 따라 100개가 넘는 하위 폴더에서 약 1,000개의 파일을 확장한다는 것을 의미합니다. Visual Studio **출력** 창에서 진행률을 확인할 수 있습니다. 기다리는 동안 다음에 나오는 질문 섹션을 살펴보세요. [Flask 설치](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) 페이지(flask.pcocoo.org)에서 Flask의 종속성에 대한 설명을 볼 수도 있습니다.

1. 상태 표시줄에 있는 Visual Studio Git 컨트롤에서 **팀 탐색기**의 **변경 내용** 페이지를 여는 변경 내용 표시기(**99&#42;** 로 표시됨)를 선택합니다.

    가상 환경을 만들면 수백 가지 변경 내용이 표시되지만, 사용자나 프로젝트를 복제하는 다른 모든 사람이 언제든지 *requirements.txt*에서 환경을 다시 만들 수 있으므로 소스 제어에 포함할 필요가 없습니다.

    가상 환경을 제외하려면 **env** 폴더를 마우스 오른쪽 단추로 클릭하고 **이 로컬 항목 무시**를 선택합니다.

    ![소스 제어 변경 내용에서 가상 환경 무시](media/flask/step01-ignore-local-items.png)

1. 가상 환경을 제외하면 프로젝트 파일과 *.gitignore*에 대한 변경 내용만 남습니다. *.gitignore* 파일에는 가상 환경 폴더에 대해 추가된 항목이 포함되어 있습니다. 이 파일을 두 번 클릭하여 차이를 확인할 수 있습니다.

1. 커밋 메시지를 입력하고 **모두 커밋** 단추를 선택한 후 원하는 경우 원격 리포지토리에 커밋을 푸시합니다.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>질문: 가상 환경을 만들려는 이유는 무엇인가요?

대답: 가상 환경은 앱의 정확한 종속성을 격리하는 좋은 방법입니다. 이러한 격리는 전역 Python 환경 내에서 충돌을 방지하고 테스트 및 협업을 지원합니다. 시간에 따라 앱을 개발하면서 여러 유용한 Python 패키지가 동일하게 표시됩니다. 프로젝트별 가상 환경에 패키지를 유지하면 소스 제어에 포함되어 있는, 해당 환경을 설명하는 프로젝트의 *requirements.txt* 파일을 쉽게 업데이트할 수 있습니다. 빌드 서버, 배포 서버 및 기타 개발 컴퓨터를 포함하여 다른 컴퓨터에 프로젝트를 복사하는 경우 *requirements.txt*만 사용하여 환경을 다시 만들기가 수월합니다. 따라서 환경이 소스 제어에 있을 필요가 없습니다. 자세한 내용은 [가상 환경 사용](selecting-a-python-environment-for-a-project.md#use-virtual-environments)을 참조하세요.

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>질문: 소스 제어에 이미 커밋된 가상 환경을 제거하려면 어떻게 해야 하나요?

대답: 먼저 *.gitignore* 파일을 편집하여 폴더를 제외합니다. `# Python Tools for Visual Studio (PTVS)` 주석이 있는 끝에서 섹션을 찾아 가상 환경 폴더에 대한 새 줄(예: `/BasicProject/env`)을 추가합니다. Visual Studio는 **솔루션 탐색기**에 파일을 표시하지 않으므로 **파일** > **열기** > **파일** 메뉴 명령을 사용하여 직접 파일을 엽니다. **팀 탐색기**에서 파일을 열 수도 있습니다. **설정** 페이지에서 **리포지토리 설정**을 선택하고 **무시 및 특성 파일** 섹션으로 이동한 다음, **.gitignore** 옆에 있는 **편집** 링크를 선택합니다.

두 번째로 명령 창을 열고, *env*와 같은 가상 환경 폴더를 포함하는 *BasicProject*와 같은 폴더로 이동하고, `git rm -r env`를 실행합니다. 그런 다음, 명령줄(`git commit -m 'Remove venv'`)에서 해당 변경 내용을 커밋하거나 **팀 탐색기**의 **변경 내용** 페이지에서 커밋합니다.

## <a name="step-1-4-examine-the-boilerplate-code"></a>1-4단계: 상용구 코드 검사

1. 프로젝트 생성이 완료되면 **솔루션 탐색기**에 솔루션 및 프로젝트가 표시됩니다. 여기서 프로젝트에는 *app.py* 및 *requirements.txt*라는 두 개의 파일만 포함됩니다.

    ![솔루션 탐색기의 빈 Flask 프로젝트 파일](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. 앞에서 설명한 대로 *requirements.txt* 파일은 Flask 패키지 종속성을 지정합니다. 이 파일은 처음으로 프로젝트를 만들 때 가상 환경을 만들도록 초대하는 데 필요합니다.

1. 단일 *requirements.txt* 파일에는 세 부분이 포함되어 있습니다. 첫 번째는 Flask에 대한 `import` 문으로, `app` 변수에 할당된 `Flask` 클래스의 인스턴스를 만든 다음, `wsgi_app` 변수를 할당합니다(이는 웹 호스트에 배포할 때 유용하지만 현재 사용되지 않음).

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. 파일 끝에 있는 두 번째 부분은 환경 변수에서 가져온 특정 호스트 및 포트 값(localhost로 기본 설정:5555)을 사용하여 Flask 개발 서버를 시작하는 선택적 코드입니다.

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. 세 번째는 URL 경로에 함수를 할당하는 짧은 코드로, 함수가 URL로 식별되는 리소스를 제공함을 의미합니다. Flask의 `@app.route` 데코레이터를 사용하여 경로를 정의합니다. 이 경우 인수는 사이트 루트의 상대 URL입니다. 코드에서 볼 수 있듯이, 여기에서 함수는 브라우저에서 렌더링할 수 있는 텍스트 문자열만 반환합니다. 다음 단계에서는 HTML로 서식 있는 페이지를 렌더링합니다.

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>질문: Flask 클래스에 대한 __name__ 인수의 용도는 무엇인가요?

답변: 인수는 앱의 모듈 또는 패키지의 이름이며, 템플릿, 정적 파일 및 앱에 속한 기타 리소스를 찾을 수 있는 위치를 Flask에 알려 줍니다. 단일 모듈에 포함된 앱의 경우 `__name__`이 항상 적절한 값입니다. 디버깅 정보가 필요한 확장의 경우에도 중요합니다. 자세한 정보 및 추가 인수는 [Flask 클래스 설명서](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask)(flask.pocoo.org)를 참조하세요.

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>질문: 함수에 둘 이상의 경로 데코레이터가 있을 수 있나요?

답변: 예, 동일한 기능이 여러 경로를 제공하는 경우 원하는 만큼 데코레이터를 사용할 수 있습니다. 예를 들어 "/" 및 "/ hello" 둘 다에 `hello` 함수를 사용하려면 다음 코드를 사용합니다.

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>질문: Flask는 다양한 URL 경로와 쿼리 매개 변수에서 어떻게 작동하나요?

답변: 경로에서 `<variable_name>`으로 변수를 표시하고, Flask는 명명된 인수를 사용하여 변수를 함수에 전달합니다. 변수는 URL 경로의 일부이거나 쿼리 매개 변수일 수 있습니다. 예를 들어 `'/hello/<name>` 형식의 경로는 함수에 `name`이라는 문자열 인수를 생성하고, 경로에서 `?message=<msg>`를 사용하여 "message=" 쿼리 매개 변수에 지정된 값을 구문 분석하고, 함수에 `msg`로 전달합니다.

```python
@app.route('/hello/<name>?message=<msg>')
def hello(name, msg):
    return "Hello " + name + "! Message is " + msg + "."
```

형식을 변경하려면 변수 앞에 `int`, `float`, `path`(폴더 이름을 설명하는 슬래시를 허용함) 및 `uuid`를 붙입니다 자세한 내용은 Flask 설명서의 [변수 규칙](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules)을 참조하세요.

쿼리 매개 변수는 `request.args` 속성을 통해, 특히 `request.args.get` 메서드를 통해서도 사용할 수 있습니다. 자세한 내용은 Flask 설명서의 [요청 개체](https://flask.palletsprojects.com/en/1.0.x/quickstart/#the-request-object)를 참조하세요.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>질문: 다른 패키지를 설치한 후 Visual Studio가 가상 환경에서 requirements.txt 파일을 생성할 수 있나요?

대답: 예. **Python 환경** 노드를 확장하고 가상 환경을 마우스 오른쪽 단추로 클릭한 다음, **requirements.txt 생성** 명령을 선택합니다. 환경을 수정하고 해당 환경에 종속된 다른 코드 변경 내용과 함께 *requirements.txt*의 변경 내용을 소스 제어에 커밋할 때 이 명령을 주기적으로 사용하는 것이 좋습니다. 빌드 서버에서 지속적인 통합을 설정하는 경우 환경을 수정할 때마다 파일을 생성하고 변경 내용을 커밋해야 합니다.

## <a name="step-1-5-run-the-project"></a>1-5단계: 프로젝트 실행

1. Visual Studio에서 **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용합니다(표시되는 브라우저가 다를 수 있음).

    ![Visual Studio의 웹 서버 실행 도구 모음 단추](media/tutorials-common/run-web-server-toolbar-button.png)

1. 두 명령 모두 PORT 환경 변수에 임의의 포트 번호를 할당한 다음, `python app.py`를 실행합니다. 이 코드는 Flask의 개발 서버 내에서 해당 포트를 사용하여 앱을 시작합니다. Visual Studio에 시작 파일이 없다는 메시지와 함께 **디버거를 시작하지 못했습니다.** 가 표시되면 **솔루션 탐색기**에서 **app.py**를 마우스 오른쪽 단추로 클릭하고 **시작 파일로 설정**을 선택합니다.

1. 서버가 시작되면 서버 로그를 표시하는 콘솔 창이 열립니다. 그런 다음, Visual Studio는 브라우저에 `http://localhost:<port>`를 자동으로 열어 `hello` 함수로 렌더링된 메시지를 표시합니다.

    ![Flask 프로젝트 기본 보기](media/flask/step01-first-run-success.png)

1. 완료되면 콘솔 창을 닫거나 Visual Studio에서 **디버그** > **디버깅 중지** 명령을 사용하여 서버를 중지합니다.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>질문: 프로젝트의 Python 하위 메뉴에서 디버그 메뉴 명령과 서버 명령을 사용하는 것의 차이점은 무엇인가요?

대답: **디버그** 메뉴 명령 및 도구 모음 단추 외에 프로젝트의 상황에 맞는 메뉴에서 **Python** > **서버 실행** 또는 **Python** > **디버그 서버 실행**을 사용하여 서버를 시작할 수도 있습니다. 두 명령 모두 실행 중인 서버에 대한 로컬 URL(localhost: port)이 표시되는 콘솔 창을 엽니다. 그러나 해당 URL을 사용하여 브라우저를 수동으로 열어야 하며 디버그 서버를 실행해도 Visual Studio 디버거가 자동으로 시작되지는 않습니다. 원하는 경우 **디버그** > **프로세스에 연결** 명령을 사용하여 나중에 실행 중인 프로세스에 디버거를 연결할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 시점에서 기본 Flask 프로젝트에는 동일한 파일에 시작 코드와 페이지 코드가 들어 있습니다. 이러한 두 가지 문제를 분리하고 템플릿을 사용하여 HTML 및 데이터를 구분하는 것이 가장 좋습니다.

> [!div class="nextstepaction"]
> [보기 및 페이지 템플릿을 사용하여 Flask 앱 만들기](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Flask 빠른 시작](https://flask.palletsprojects.com/en/1.0.x/quickstart/)(flask.pocoo.org)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)