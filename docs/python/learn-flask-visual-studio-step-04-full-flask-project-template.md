---
title: Visual Studio 4단계, 웹 프로젝트 템플릿에서 Flask 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Flask 기본 사항을 검토하는 연습 과정으로, Flask 웹 프로젝트 및 Flask/Jade 웹 프로젝트 템플릿에서 제공하는 기능을 구체적으로 설명합니다.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9f4c165f3e882cea71ee4aaff9f2358c27ce6a2b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957279"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>4단계: 전체 Flask 웹 프로젝트 템플릿 사용

**이전 단계: [정적 파일 제공, 페이지 추가 및 템플릿 상속 사용](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Visual Studio에서 “빈 Flask 앱 프로젝트” 템플릿을 기반으로 앱을 작성하여 Flask의 기본 사항을 살펴보았으므로 “Flask 웹 프로젝트” 템플릿에 의해 생성된 전체 앱을 쉽게 이해할 수 있습니다.

이 단계에서는 다음을 수행합니다.

> [!div class="checklist"]
> - “Flask 웹 프로젝트” 템플릿을 사용하여 전체 Flask 웹앱을 만들고 프로젝트 구조 검사(4-1단계)
> - 프로젝트 템플릿에서 만든 보기 및 템플릿(기본 페이지 템플릿에서 상속되고 jQuery 및 부트스트랩과 같은 정적 JavaScript 라이브러리를 사용하는 세 페이지로 구성) 이해(4-2단계)
> - 템플릿에서 제공하는 URL 라우팅 이해(4-3단계)

이 문서는 Jinja 대신 Jade 템플릿 엔진을 사용하는 “Flask 웹 프로젝트”와 동일한 앱을 생성하는 “Flask/Jade 웹 프로젝트” 템플릿에도 적용됩니다. 추가 세부 정보는 이 문서의 끝부분에 나옵니다.

## <a name="step-4-1-create-a-project-from-the-template"></a>4-1단계: 템플릿에서 프로젝트 만들기

1. Visual Studio에서 **솔루션 탐색기**로 이동하여 이 자습서의 앞부분에서 만든 **LearningFlask** 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 새 솔루션을 사용하려는 경우에는 **파일** > **새로 만들기** > **프로젝트**를 대신 선택합니다.

1. 새 프로젝트 대화 상자에서 **Flask 웹 프로젝트** 템플릿을 검색하여 선택하고, 프로젝트의 이름을 "FlaskWeb"으로 지정하고, **확인**을 선택합니다.

1. 템플릿에는 *requirements.txt* 파일이 포함되어 있으므로 Visual Studio에서 해당 종속성을 설치할 위치를 묻습니다. **가상 환경에 설치** 옵션을 선택하고 **가상 환경 추가** 대화 상자에서 **만들기**를 선택하여 기본값을 그대로 사용합니다.

1. Visual Studio에서 가상 환경 설정을 완료하면 **솔루션 탐색기**에서 해당 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택하여 **FlaskWeb** 프로젝트가 Visual Studio 솔루션의 기본값이 되도록 설정합니다. 굵게 표시된 시작 프로젝트는 디버거를 시작할 때 실행됩니다.

    ![FlaskWeb 프로젝트를 시작 프로젝트로 표시하는 솔루션 탐색기](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용하여 서버를 실행합니다.

    ![Visual Studio의 웹 서버 실행 도구 모음 단추](media/flask/run-web-server-toolbar-button.png)

1. 템플릿으로 만든 앱에는 홈, 정보, 연락처라는 세 개의 페이지가 있으며, 탐색 모음을 사용하여 페이지 간에 이동할 수 있습니다. 1-2분 동안 앱의 다른 부분을 살펴보세요. **로그인** 명령을 통해 앱을 인증하려면 앞에서 만든 슈퍼 사용자 자격 증명을 사용합니다.

    ![Flask 웹 프로젝트 앱의 전체 브라우저 보기](media/flask/step04-full-app-desktop-view.png)

1. “Flask 웹 프로젝트” 템플릿으로 만든 앱은 모바일 폼 팩터를 수용하는 반응형 레이아웃에 부트스트랩을 사용합니다. 이러한 응답성을 확인하려면 콘텐츠가 세로로 렌더링되고 탐색 모음이 메뉴 아이콘으로 전환되도록 브라우저 크기를 좁은 보기로 조정합니다.

    ![Flask 웹 프로젝트 앱의 모바일(좁은) 보기](media/flask/step04-full-app-mobile-view.png)

1. 다음 섹션을 위해 앱이 계속 실행되도록 할 수 있습니다.

    앱을 중지하고 [변경 내용을 소스 제어에 커밋](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)하려면 먼저 **팀 탐색기**에서 **변경 내용** 페이지를 열고, 가상 환경에 대한 폴더(**env**)를 마우스 오른쪽 단추로 클릭하고, **이 로컬 항목 무시**를 선택합니다.

### <a name="examine-what-the-template-creates"></a>템플릿에서 만드는 항목 검사

“Flask 웹 프로젝트” 템플릿으로 아래 구조가 만들어집니다. 내용이 이전 단계에서 만든 것과 매우 유사합니다. 차이점은 반응이 빠른 디자인을 위해 “Flask 웹 프로젝트” 템플릿이 jQuery와 Bootstrap을 포함하므로 *static* 폴더에 더 많은 구조가 포함되어 있다는 것입니다. 또한 템플릿은 연락처 페이지도 추가합니다. 전반적으로 이 자습서의 이전 단계를 수행한 경우 템플릿의 모든 내용에 익숙할 것입니다.

- 프로젝트 루트의 파일:
  - *runserver.py*는 개발 서버에서 앱을 실행하는 스크립트입니다.
  - *requirements.txt*는 Flask 0.x에 대한 종속성을 포함합니다.
- *FlaskWeb* 폴더는 모든 앱 파일을 포함합니다.
  - *\_\_init.py\_\_* 는 앱 코드를 Python 모듈로 표시하고, Flask 개체를 만들며 앱의 뷰를 가져옵니다.
  - *views.py*는 페이지를 렌더링할 코드를 포함합니다.
  - *static* 폴더는 *content*(CSS 파일), *fonts*(글꼴 파일) 및 *scripts*(JavaScript 파일)라는 하위 폴더를 포함합니다.
  - *templates* 폴더에는 각각 *layout.html*을 확장하는 특정 페이지에 대한 *about.html*, *contact.html* 및 * index.html*과 함께 *layout.html* 기본 템플릿이 포함됩니다.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>질문: Visual Studio 프로젝트 간에 가상 환경을 공유할 수 있나요?

대답: 예, 하지만 시간이 지나면 프로젝트마다 다른 패키지를 사용할 수 있다는 점을 인식하고 공유해야 합니다. 따라서 공유된 가상 환경에는 해당 환경을 사용하는 모든 프로젝트에 대한 모든 패키지가 포함되어야 합니다.

그래도 기존 가상 환경을 사용하려면 다음을 수행하세요.

1. Visual Studio에 종속성을 설치하라는 메시지가 표시되면 **직접 설치** 옵션을 선택합니다.
1. **솔루션 탐색기**에서 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **기존 가상 환경 추가**를 선택합니다.
1. 가상 환경을 포함하는 폴더로 이동하여 선택하고 **확인**을 선택합니다.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>4-2단계: 프로젝트 템플릿으로 만든 보기 및 페이지 템플릿 이해

프로젝트를 실행하면 앱에 홈, 정보, 연락처의 세 가지 보기가 포함되어 있음을 알 수 있습니다. 이러한 보기에 대한 코드는 *FlaskWeb/views.py* 폴더에 있습니다. 각 보기 함수는 템플릿 경로 및 템플릿에 제공할 값에 대한 인수의 변수 목록과 함께 `flask.render_template`을 호출합니다. 예를 들어 정보 페이지는 `about` 함수에 의해 처리됩니다(데코레이터가 URL 라우팅을 제공).

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` 및 `contact` 함수는 유사한 데코레이터와 약간 다른 인수를 포함하여 거의 동일합니다.

템플릿은 앱의 *templates* 폴더에 있습니다. 기본 템플릿인 *layout.html*이 가장 광범위합니다. 이 템플릿은 필요한 모든 정적 파일(JavaScript 및 CSS)을 참조하고, 다른 페이지에서 재정의하는 “content”라는 블록을 정의하며, “scripts”라는 다른 블록을 제공합니다. *layout.html*에서 주석 처리된 다음 발췌 부분은 이러한 특정 영역을 보여줍니다.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

개별 페이지 템플릿인 *about.html*, *contact.html* 및 *index.html*은 각각 기본 템플릿인 *layout.html*을 확장합니다. *about.html*은 가장 간단하며 `{% extends %}` 및 `{% block content %}` 태그를 표시합니다.

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* 및 *contact.html*은 동일한 구조를 사용하고 "content" 블록에 보다 긴 콘텐츠를 제공합니다.

## <a name="the-flaskjade-web-project-template"></a>Flask/Jade 웹 프로젝트 템플릿

이 문서의 시작 부분에서 언급했듯이, Visual Studio는 “Flask 웹 프로젝트”에 의해 생성된 것과 시각적으로 동일한 애플리케이션을 만드는 “Flask/Jade 웹 프로젝트” 템플릿을 제공합니다. 주된 차이점은 동일한 개념을 보다 간결한 언어로 구현하는 Jinja의 확장인 Jade 템플릿 엔진을 사용한다는 것입니다. 특히 Jade는 예를 들어 {% %} 구분 기호로 묶인 태그 대신, 키워드를 사용하며 키워드를 사용하여 CSS 스타일과 HTML 요소를 참조할 수 있습니다.

Jade를 사용하도록 설정하려면 먼저 프로젝트 템플릿은 *requirements.txt*에 pyjade 패키지를 포함합니다.

앱의 *\_\_init\_\_.py* 파일은 다음 줄을 포함합니다.

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

*템플릿* 폴더에는 *.html* 템플릿 대신 *.jade* 파일이 있고, *views.py*의 보기는 `flask.render_template`에 대한 호출에서 이러한 파일을 참조합니다. 그렇지 않은 경우 보기 코드는 동일합니다.

*.jade* 파일 중 하나를 열면 템플릿의 보다 간결한 표현을 확인할 수 있습니다. 예를 들어, 다음은 "Flask/Jade 웹 프로젝트" 템플릿으로 만들어진 *templates/layout.jade*의 내용입니다.

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

*templates/about.jade*의 내용은 다음과 같습니다. 자리 표시자로 `#{ <name>}`을 사용하는 것을 확인할 수 있습니다.

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Jinja 및 Jade 구문 모두를 원하는 대로 실험해 보고 어떤 것이 가장 적합한지 확인해 보세요.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [설문조사 Flask 웹 프로젝트 템플릿](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Writing your first Flask app, part 4 - forms and generic views](https://docs.djangoproject.com/en/2.0/intro/tutorial04/)(첫 번째 Flask 앱 작성, 4부 - 양식 및 일반 보기)(docs.djangoproject.com)
- [GitHib의 Jade(문서)](https://github.com/liuliqiang/pyjade)(github.com)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
