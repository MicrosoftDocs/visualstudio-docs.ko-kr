---
title: Visual Studio 2단계, 보기 및 템플릿에서 Flask 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Flask 기본 사항을 검토하는 연습 과정으로, 앱을 만들고 보기 및 템플릿을 사용하는 단계를 구체적으로 설명합니다.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 03a0eb6808b2298e0727492978d9beb7cfaf2216
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79300878"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>2단계: 보기 및 페이지 템플릿을 사용하여 Flask 앱 만들기

**이전 단계: [Visual Studio 프로젝트 및 솔루션 만들기](learn-flask-visual-studio-step-01-project-solution.md)**

이 자습서의 1단계에서는 한 페이지와 모든 코드가 하나의 파일에 포함된 Flask 앱을 만들었습니다. 향후 개발을 위해서는 코드를 리팩터링하고 페이지 템플릿 구조를 만드는 것이 가장 좋습니다. 특히, 앱 보기의 코드와 시작 코드와 같은 다른 요소를 분리하는 것이 좋습니다.

이 단계에서는 다음 작업을 수행하는 방법을 배웁니다.

> [!div class="checklist"]
> - 시작 코드와 보기를 분리하기 위해 앱의 코드 리팩터링(2-1단계)
> - 페이지 템플릿을 사용하여 보기 렌더링(2-2단계)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>2-1단계: 추가 개발을 지원하기 위해 프로젝트 리팩터링

"빈 Flask 웹 프로젝트" 템플릿으로 생성된 코드에는 단일 보기와 시작 코드가 포함된 단일 *app.py* 파일이 있습니다. 나중에 여러 보기 및 템플릿이 있는 앱을 개발하려면 이러한 문제를 구분하는 것이 가장 좋습니다.

1. 프로젝트 폴더에서 `HelloFlask`라는 앱 폴더를 만듭니다(**솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 폴더**를 선택함).

2. *HelloFlask* 폴더에서 다음 콘텐츠가 포함된 *\_\_init\_\_.py*라는 파일을 만듭니다. 이 파일은 `Flask` 인스턴스를 만들고 앱의 보기를 로드합니다(다음 단계에서 생성).

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. *HelloFlask* 폴더에서 다음 콘텐츠가 포함된 *views.py*라는 파일을 만듭니다. *\_\_init\_\_.py* 내에서 `import HelloFlask.views`를 사용했기 때문에 *views.py*이라는 이름은 중요합니다. 이름이 일치하지 않으면 런타임에 오류가 표시됩니다.

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    이 코드는 함수의 이름과 경로를 `home`으로 변경하는 것 외에도 *app.py*의 페이지 렌더링 코드를 포함하고 *\_\_init\_\_.py*에 선언된 `app` 개체를 가져옵니다.

4. *HelloFlask*에 *templates*라는 하위 폴더를 만듭니다. 이 폴더는 현재 비어 있습니다.

5. 프로젝트의 루트 폴더에서 *app.py*의 이름을 *runserver.py*로 바꾸고, 콘텐츠를 다음 코드와 일치시킵니다.

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. 전체 프로젝트 구조는 다음 이미지와 같아야 합니다.

    ![코드 리팩터링 후 프로젝트 구조](media/flask/step02-project-structure.png)

7. **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용(표시되는 브라우저가 다를 수 있음)하여 앱을 시작하고 브라우저를 엽니다. / 및 /home URL 경로를 둘 다 시도해 봅니다.

8. 또한 코드의 여러 부분에서 중단점을 설정하고 앱을 다시 시작하여 시작 시퀀스를 따를 수 있습니다. 예를 들어 *runserver.py* 및 *HelloFlask\_* init *_.py*의 첫 번째 줄 및 *views.py*의 `return "Hello Flask!"` 줄에 중단점을 설정합니다. 그런 다음, 앱을 다시 시작(**디버그** > **다시 시작**, **Ctrl**+**F5** 또는 아래 표시된 도구 모음 단추)하고 코드를 단계별로 실행(**F10**)하거나 **F5** 키를 사용하여 각 중단점에서 실행합니다.

    ![Visual Studio 디버깅 도구 모음의 다시 시작 단추](media/debugging-restart-toolbar-button.png)

9. 완료되면 앱을 중지합니다.

### <a name="commit-to-source-control"></a>소스 제어에 커밋

코드를 변경하고 성공적으로 테스트했으므로 이제 변경 내용을 검토하고 소스 제어에 커밋해야 합니다. 이 자습서의 이후 단계에서는 소스 제어에 다시 커밋해야 하는 적절한 시간을 알려주므로 이 섹션을 다시 참조하세요.

1. Visual Studio의 아래쪽(아래 원)에 있는 변경 단추를 선택하여 **팀 탐색기**로 이동합니다.

    ![Visual Studio 상태 표시줄의 소스 제어 변경 단추](media/flask/step02-source-control-changes-button.png)

1. **팀 탐색기**에서 “Refactor code”와 같은 커밋 메시지를 입력하고 **모두 커밋**을 선택합니다. 커밋이 완료되면 **커밋 \<해쉬>를 로컬에서 만들었습니다. 서버의 변경 내용을 공유하여 동기화합니다.** 라는 메시지가 표시됩니다. 원격 리포지토리에 변경 내용을 푸시하려면 **동기화**를 선택한 다음, **나가는 커밋**에서 **푸시**를 선택합니다. 원격에 푸시하기 전에 여러 개의 로컬 커밋을 누적할 수도 있습니다.

    ![팀 탐색기에서 원격에 커밋 푸시](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>질문: 소스 제어에 얼마나 자주 커밋해야 하나요?

대답: 소스 제어에 변경 내용을 커밋하면 변경 로그에 레코드가 생성되고 필요한 경우 리포지토리를 되돌릴 수 있는 지점이 생성됩니다. 각 커밋에서 특정 변경 내용을 검사할 수도 있습니다. Git 커밋은 비용이 많이 들지 않기 때문에, 한 번의 커밋에 많은 수의 변경 내용을 누적하는 것보다 커밋을 자주 수행하는 것이 좋습니다. 따라서 사소한 변경 내용을 매번 개별 파일에 커밋할 필요가 없습니다. 일반적으로 기능을 추가하거나, 이 단계에서 수행한 것과 같은 구조 변경을 수행하거나, 코드 리팩터링을 수행했을 때 커밋을 실행합니다. 또한 모두에게 가장 적합한 커밋 빈도를 다른 팀원과 함께 확인합니다.

커밋 빈도와 원격 리포지토리에 커밋을 푸시하는 빈도는 다른 문제입니다. 원격 리포지토리에 커밋을 푸시하기 전에 로컬 리포지토리에 여러 커밋을 누적할 수 있습니다. 다시 말하지만, 커밋 빈도는 팀에서 원하는 리포지토리 관리 방법에 따라 달라집니다.

## <a name="step-2-2-use-a-template-to-render-a-page"></a>2-2단계: 템플릿을 사용하여 페이지 렌더링

지금까지 *views.py*의 `home` 함수는 페이지에 대해 일반 텍스트 HTTP 응답만 생성했습니다. 그러나 대부분의 실제 웹 페이지는 라이브 데이터를 통합하는 서식 있는 HTML 페이지로 응답합니다. 실제로 함수를 사용하여 보기를 정의하는 주된 이유는 콘텐츠를 동적으로 생성하기 위함입니다.

보기의 반환 값은 단순한 문자열이므로, 동적 콘텐츠를 사용하여 문자열 내에서 원하는 HTML을 빌드할 수 있습니다. 그러나 데이터와 태그를 분리하는 것이 가장 좋으므로, 태그를 템플릿에 배치하고 데이터를 코드에 유지하는 것이 훨씬 좋습니다.

1. 먼저 *views.py*를 편집하여 일부 동적 콘텐츠가 있는 페이지에 인라인 HTML을 사용하는 다음 코드를 포함합니다.

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. 앱을 실행하고 페이지를 여러 번 새로 고쳐서 날짜/시간이 업데이트되었는지 확인합니다. 완료되면 앱을 중지합니다.

1. 템플릿을 사용하도록 페이지 렌더링을 변환하려면 *templates* 폴더에 다음 콘텐츠가 포함된 *index.html*이라는 파일을 만듭니다. 여기서 `{{ content }}`는 코드에 값을 제공하는 자리 표시자 또는 대체 토큰(*템플릿 변수*라고도 함)입니다.

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. `render_template`을 사용하여 템플릿을 로드하도록 `home` 함수를 수정하고, "content"에 값을 지정합니다. 이 작업은 자리 표시자의 이름과 일치하는 명명된 인수를 사용하여 수행됩니다. Flask는 *templates* 폴더에서 템플릿을 자동으로 찾으므로, 템플릿에 대한 선언은 해당 폴더에 상대적입니다.

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. 앱을 실행하여 결과를 확인하고, 템플레이팅 엔진(Jinja)이 HTML 콘텐츠를 자동으로 이스케이프하므로 `content` 값의 인라인 HTML이 HTML*로* 렌더링되지 않는지 확인합니다. 자동 이스케이프는 주입 공격에 대한 우발적인 취약성을 방지합니다. 개발자는 종종 한 페이지에서 입력을 수집하고 템플릿 자리 표시자를 통해 다른 페이지의 값으로 사용합니다. 이스케이프는 HTML을 코드에 넣지 않는 것이 최선이라는 것을 다시 한 번 상기시켜 주는 역할도 합니다.

    따라서 *templates\index.html*을 검토하여 태그 내의 각 데이터 조각마다 고유한 자리 표시자를 포함하도록 합니다.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    그런 다음, `home` 함수를 업데이트하여 모든 자리 표시자에 값을 지정합니다.

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. 앱을 다시 실행하여 올바르게 렌더링된 출력을 확인합니다.

    ![템플릿을 사용하여 앱 실행](media/flask/step02-result.png)

1. 원하는 경우 [2-1단계](#commit-to-source-control)에 설명된 대로 변경 내용을 소스 제어에 커밋하고 원격 리포지토리를 업데이트합니다.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>질문: 페이지 템플릿은 별도의 파일에 있어야 하나요?

대답: 템플릿은 일반적으로 별도의 HTML 파일에서 유지 관리되지만 인라인 템플릿을 사용할 수도 있습니다. 그러나 태그와 코드를 명확하게 분리하려면 별도의 파일을 사용하는 것이 좋습니다.

### <a name="question-must-templates-use-the-html-file-extension"></a>질문: 템플릿은 .html 파일 확장명을 사용해야 하나요?

대답: 항상 `render_template` 함수에 대한 첫 번째 인수에서 파일의 정확한 상대 경로를 식별하므로 페이지 템플릿 파일의 *.html* 확장명은 전적으로 선택 사항입니다. 그러나 Visual Studio(및 기타 편집기)는 일반적으로 *.html* 파일을 사용하여 코드 완성 및 구문 색 지정과 같은 기능을 제공하므로 페이지 템플릿이 엄격하게 HTML이 아니라는 사실보다 중요합니다.

실제로 Flask 프로젝트로 작업할 때 Visual Studio는 편집 중인 HTML 파일이 실제로 Flask 템플릿인 경우를 자동으로 감지하고 특정 자동 완성 기능을 제공합니다. 예를 들어 Flask 페이지 템플릿 주석 `{#`을 입력하기 시작하면 Visual Studio에서 닫는 `#}` 문자를 자동으로 제공합니다. **선택 영역을 주석으로 처리** 및 **선택 영역의 주석 처리 제거** 명령(**편집** >  **고급** 메뉴 및 도구 모음)에서도 HTML 주석 대신 템플릿 주석을 사용합니다.

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>질문: 템플릿을 추가 하위 폴더로 구성할 수 있나요?

대답: 예, 하위 폴더를 사용한 다음, `render_template`에 대한 호출에서 *템플릿* 아래의 상대 경로를 참조할 수 있습니다. 이는 템플릿의 네임스페이스를 효과적으로 만들 수 있는 좋은 방법입니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [정적 파일 제공, 페이지 추가 및 템플릿 상속 사용](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Flask 빠른 시작 - 렌더링 템플릿](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates)(flask.pocoo.org)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
