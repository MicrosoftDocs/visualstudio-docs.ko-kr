---
title: Visual Studio 3단계, 정적 파일 및 페이지에서 Flask 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Flask 기본 사항을 검토하는 연습 과정으로, 정적 파일을 제공하고 앱에 페이지를 추가하고 템플릿 상속을 사용하는 방법을 구체적으로 설명합니다.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 69fd704976ee941cb053d75040a3d3ec7871a380
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238744"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>3단계: Flask 앱을 사용하여 정적 파일 제공, 페이지 추가 및 템플릿 상속 사용

**이전 단계: [보기 및 페이지 템플릿을 사용하여 Flask 앱 만들기](learn-flask-visual-studio-step-02-create-app.md)**

이 자습서의 이전 단계에서는 자체 포함된 HTML의 단일 페이지로 최소 Flask 앱을 만드는 방법을 학습했습니다. 그러나 최신 웹앱은 일반적으로 여러 페이지로 구성되며 CSS 및 JavaScript 파일과 같은 공유 리소스를 사용하여 일관된 스타일과 동작을 제공합니다.

이 단계에서는 다음 방법을 학습합니다.

> [!div class="checklist"]
> - Visual Studio 항목 템플릿을 사용하여 편리한 상용구 코드로 신속하게 다양한 형식의 새 파일 추가(3-1단계)
> - 코드에서 정적 파일 제공(3-2단계, 옵션)
> - 앱에 페이지 추가(3-3단계)
> - 템플릿 상속을 사용하여 전체 페이지에서 사용되는 헤더 및 탐색 모음 만들기(3-4단계)

## <a name="step-3-1-become-familiar-with-item-templates"></a>3-1단계: 항목 템플릿 익히기

Flask 앱을 개발하는 경우 일반적으로 더 많은 Python, HTML, CSS 및 JavaScript 파일을 추가합니다. 각 파일 형식(배포에 필요할 수 있는 *web.config*와 같은 다른 파일 포함)에 대해 Visual Studio는 시작하는 데 도움이 되는 편리한 [항목 템플릿](python-item-templates.md)을 제공합니다.

사용 가능한 템플릿을 보려면 **솔루션 탐색기**로 이동하여 항목을 만들 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

![Visual Studio의 새 항목 추가 대화 상자](media/flask/step03-add-new-item-dialog.png)

템플릿을 사용하려면 원하는 템플릿을 선택하고 파일 이름을 지정한 후 **확인**을 선택합니다. 이런 방식으로 항목을 추가하면 파일이 Visual Studio 프로젝트에 자동으로 추가되고 소스 제어에 대한 변경 내용이 표시됩니다.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>질문: Visual Studio에서는 제공할 항목 템플릿을 어떻게 알 수 있나요?

대답: Visual Studio 프로젝트 파일(*.pyproj*)에는 Python 프로젝트로 표시하는 프로젝트 형식 식별자가 포함되어 있습니다. Visual Studio에서는 이 형식 식별자를 사용하여 프로젝트 형식에 적합한 항목 템플릿만 표시합니다. 이런 방식으로 Visual Studio에서는 매번 정렬 여부를 묻는 메시지를 표시하지 않고 여러 프로젝트 형식에 대해 다양한 항목 템플릿을 제공할 수 있습니다.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2단계: 앱에서 정적 파일 제공

Python(모든 프레임워크 사용)으로 빌드된 웹앱에서 Python 파일은 항상 웹 호스트의 서버에서 실행되며 사용자의 컴퓨터로 전송되지 않습니다. 그러나 CSS 및 JavaScript와 같은 다른 파일은 브라우저에서만 사용되므로 호스트 서버는 해당 파일이 요청될 때마다 있는 그대로 제공하기만 합니다. 이러한 파일을 “정적” 파일이라고 하며 Flask에서는 코드를 작성할 필요 없이 이러한 파일을 자동으로 제공할 수 있습니다. 예를 들어 HTML 파일 내에서 프로젝트의 상대 경로를 사용하여 정적 파일을 참조할 수 있습니다. 이 단계의 첫 번째 섹션에서는 기존 페이지 템플릿에 CSS 파일을 추가합니다.

API 엔드포인트 구현 등을 통해 코드에서 정적 파일을 제공해야 하는 경우, Flask는 *static*이라는 폴더(프로젝트 루트에 있음) 내의 상대 경로를 사용하여 파일을 참조할 수 있는 편리한 메서드를 제공합니다. 이 단계의 두 번째 섹션에서는 간단한 정적 데이터 파일을 사용하는 메서드를 보여 줍니다.

두 경우 모두 원하는 대로 *static* 아래에 파일을 구성할 수 있습니다.

### <a name="use-a-static-file-in-a-template"></a>템플릿에서 정적 파일 사용

1. **솔루션 탐색기**에서 Visual Studio 프로젝트의 **HelloFlask** 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 폴더**를 선택하고, 폴더의 이름을 `static`으로 지정합니다.

1. **static** 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다. 대화 상자가 표시되면 **스타일시트** 템플릿을 선택하고 파일의 이름을 `site.css`로 지정하고 **확인**을 선택합니다. **site.css** 파일이 프로젝트에 표시되고 편집기에서 열립니다. 폴더 구조는 다음 이미지와 유사합니다.

    ![솔루션 탐색기에 표시된 정적 파일 구조](media/flask/step03-static-file-structure.png)

1. *site.css*의 내용을 다음 코드로 바꾸고 파일을 저장합니다.

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. 앱의 *templates/index.html* 파일 내용을 다음 코드로 바꿉니다. 이 코드는 2단계에서 사용된 `<strong>` 요소를 `message` 스타일 클래스를 참조하는 `<span>`으로 바꿉니다. 이런 식으로 스타일 클래스를 사용하면 훨씬 더 유연하게 요소의 스타일을 지정할 수 있습니다.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. 프로젝트를 실행하여 결과를 확인합니다. 완료되면 앱을 중지하고, 원하는 경우 소스 제어에 변경 내용을 커밋합니다(자세한 내용은 [2단계](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control) 참조).

### <a name="serve-a-static-file-from-code"></a>코드에서 정적 파일 제공

Flask는 코드에서 호출하여 프로젝트의 *static* 폴더 내의 모든 파일을 참조할 수 있는 `serve_static_file`이라는 함수를 제공합니다. 다음 프로세스는 정적 데이터 파일을 반환하는 간단한 API 엔드포인트를 만듭니다.

1. 아직 *static* 폴더를 만들지 않은 경우, **솔루션 탐색기**에서 Visual Studio 프로젝트의 **HelloFlask** 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 폴더**를 선택하고, 폴더의 이름을 `static`으로 지정합니다.

1. *static* 폴더에서 다음 내용(의미 없는 샘플 데이터)을 사용하여 *data.json*이라는 정적 JSON 데이터 파일을 만듭니다.

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. *views.py*에서 `send_static_file` 메서드를 사용하여 정적 데이터 파일을 반환하는 /api/data 경로가 있는 함수를 추가합니다.

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. 앱을 실행하고 /api/data 엔드포인트로 이동하여 정적 파일이 반환되는지 확인합니다. 완료되면 앱을 중지합니다.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>질문: 정적 파일 구성에 대한 규칙이 있나요?

대답: 원하는 방식으로 *static* 폴더에서 다른 CSS, JavaScript 및 HTML 파일을 추가할 수 있습니다. 일반적으로 정적 파일을 구성하려면 스타일시트 및 다른 모든 파일에 대해 *fonts*, *scripts* 및 *content*라는 하위 폴더를 만듭니다.

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>질문: API에서 URL 변수와 쿼리 매개 변수를 처리하려면 어떻게 할까요?

대답: 1-4단계의 답변을 [질문: Flask는 다양한 URL 경로와 쿼리 매개 변수에서 어떻게 작동하나요?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)에 대해 참조하세요.

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3단계: 앱에 페이지 추가

앱에 다른 페이지를 추가하는 것은 다음을 의미합니다.

- 보기를 정의하는 Python 함수를 추가합니다.
- 페이지의 태그에 대한 템플릿을 추가합니다.
- Django 프로젝트의 *urls.py* 파일에 필요한 라우팅을 추가합니다.

다음 단계에서는 “HelloFlask” 프로젝트에 “About” 페이지를 추가하고 홈페이지에서 해당 페이지에 연결합니다.

1. **솔루션 탐색기**에서 **templates** 폴더를 마우스 오른쪽 단추로 클릭하고, **추가** > **새 항목**을 선택하고, **HTML 페이지** 항목 템플릿을 선택하고, 파일의 이름을 `about.html`로 지정하고, **확인**을 선택합니다.

    > [!Tip]
    > **새 항목** 명령이 **추가** 메뉴에 나타나지 않으면 Visual Studio가 디버깅 모드를 종료하도록 앱을 중지했는지 확인하세요.

1. *about.html*의 내용을 다음 태그로 바꿉니다. 홈페이지에 대한 명시적 링크를 3-4단계의 간단한 탐색 모음으로 바꿉니다.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. 앱의 *views.py* 파일을 열고 템플릿을 사용하는 `about`이라는 함수를 추가합니다.

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. *templates/index.html* 파일을 열고 `<body>` 요소 내에서 즉시 다음 줄을 추가하여 About 페이지에 연결합니다. 다시 이 링크를 3-4단계의 탐색 모음으로 바꿉니다.

    ```html
    <div><a href="about">About</a></div>
    ```

1. **파일** > **모두 저장** 메뉴 명령을 사용하여 모든 파일을 저장하거나, **Ctrl**+**Shift**+**S**를 누르기만 하면 됩니다. Visual Studio에서는 프로젝트를 실행하면 파일이 자동으로 저장되기 때문에 기술적인 측면에서 이 단계는 필요하지 않습니다. 그러나 알고 있으면 도움이 되는 명령입니다.

1. 프로젝트를 실행하여 결과를 확인하고 페이지 간 탐색을 확인합니다. 완료되면 앱을 중지합니다.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>질문: 페이지 함수의 이름이 Flask에 중요합니까?

대답: 아니요, Flask가 응답을 생성하기 위해 함수를 호출할 URL을 결정하는 것은 `@app.route` 데코레이터이기 때문입니다. 개발자는 일반적으로 함수 이름을 경로와 일치시키지만, 이러한 일치는 필요하지 않습니다.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4단계: 템플릿 상속을 사용하여 헤더 및 탐색 모음 만들기

최신 웹앱에서는 각 페이지에 명시적 탐색 링크를 넣는 대신 일반적으로 가장 중요한 페이지 링크, 팝업 메뉴 등을 제공하는 브랜딩 헤더 및 탐색 모음을 사용합니다. 그러나 헤더 및 탐색 모음을 모든 페이지에서 동일하게 표시하기 위해 모든 페이지 템플릿에서 동일한 코드를 반복하지는 않습니다. 대신 모든 페이지에서 공통되는 부분을 한 곳에서 정의하려고 합니다.

Flask의 템플릿 시스템(기본적으로 Jinja)은 템플릿에서 특정 요소를 다시 사용할 수 있는 두 가지 방법(포함과 상속)을 제공합니다.

- ‘포함’은 `{% include <template_path> %}` 구문을 사용하여 참조 템플릿의 특정 위치에 삽입하는 다른 페이지 템플릿입니다. 코드에서 동적으로 경로를 변경하려는 경우 변수를 사용할 수도 있습니다. 포함은 일반적으로 페이지의 특정 위치에서 공유 템플릿을 풀하기 위해 페이지 본문에 사용됩니다.

- ‘상속’은 페이지 템플릿 시작 부분에서 `{% extends <template_path> %}`를 사용하여 참조 템플릿의 기반이 되는 공유 기본 템플릿을 지정합니다. 일반적으로 상속은 공유 레이아웃, 탐색 모음 및 기타 앱 페이지 구조를 정의하는 데 사용되므로, 참조 템플릿에서는 ‘블록’이라는 기본 템플릿의 특정 영역을 추가하거나 수정하기만 하면 됩니다.

두 경우 모두 `<template_path>`는 앱의 *templates* 폴더(`../` 또는 `./`도 허용됨)에 대해 상대적입니다.

기본 템플릿은 `{% block <block_name> %}` 및 `{% endblock %}` 태그를 사용하여 *블록*을 나타냅니다. 참조 템플릿에서 블록 이름이 같은 태그를 사용하는 경우 해당 블록 콘텐츠가 기본 템플릿의 콘텐츠를 재정의합니다.

다음 단계에서는 상속을 보여줍니다.

1. 앱의 *templates* 폴더에서 *layout.html*이라는 새 HTML 파일을 만들고(**추가** > **새 항목** 바로 가기 메뉴 또는 **추가** > **HTML 페이지** 사용) 콘텐츠를 아래의 태그로 대체합니다. 참조 페이지에서 바꿔야 하는 “content”라는 블록이 이 템플릿에 포함되어 있음을 알 수 있습니다.

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. 앱의 *static/site.css* 파일에 다음 스타일을 추가합니다. 이 연습에서는 반응이 빠른 디자인을 보여주려는 것이 아니며, 이러한 스타일은 단순히 흥미로운 결과를 생성하기 위한 것입니다.

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. 기본 템플릿을 참조하고 콘텐츠 블록을 재정의하도록 *templates/index.html*을 수정합니다. 상속을 사용하여 이를 확인할 수 있으며 이 템플릿은 간단해집니다.

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. 기본 템플릿을 참조하고 콘텐츠 블록을 재정의하도록 *templates/about.html*도 수정합니다.

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. 서버를 실행하여 결과를 확인합니다. 완료되면 서버를 닫습니다.

    ![앱을 실행하여 탐색 모음 표시](media/flask/step03-nav-bar.png)

1. 앱이 많이 변경되었으므로 다시 [소스 제어에 변경 내용을 커밋](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)하는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [전체 Flask 웹 프로젝트 템플릿 사용](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Azure App Service에 웹앱 배포](publishing-python-web-applications-to-azure-from-visual-studio.md)
- 제어 흐름과 같은 Jinja 템플릿의 더 많은 기능을 보려면, [Jinja 템플릿 디자이너 문서](http://jinja.palletsprojects.com/en/2.10.x/templates/)(jinja.pocoo.org)를 참조하세요.
- `url_for` 사용에 대한 자세한 내용은 Flask 애플리케이션 개체 설명서(flask.pocoo.org) 내의 [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for)를 참조하세요.
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
