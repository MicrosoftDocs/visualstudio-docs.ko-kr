---
title: Visual Studio 4단계, 웹 프로젝트 템플릿에서 Django 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Django 기본 사항을 검토하는 연습 과정으로, Django 웹 프로젝트 템플릿에서 제공하는 기능을 구체적으로 설명합니다.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c778d830b20797962306700a5af938eb3a3bb142
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62961696"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>4단계: 전체 Django 웹 프로젝트 템플릿 사용

**이전 단계: [정적 파일 제공, 페이지 추가 및 템플릿 상속 사용](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Visual Studio에서 “빈 Django 웹 프로젝트” 템플릿을 기반으로 앱을 작성하여 Django의 기본 사항을 살펴보았으므로 “Django 웹 프로젝트” 템플릿에 의해 생성된 전체 앱을 쉽게 이해할 수 있습니다.

이 단계에서는 다음을 수행합니다.

> [!div class="checklist"]
> - “Django 웹 프로젝트” 템플릿을 사용하여 전체 Django 웹앱을 만들고 프로젝트 구조 검사(4-1단계)
> - 프로젝트 템플릿에서 만든 보기 및 템플릿(기본 페이지 템플릿에서 상속되고 jQuery 및 부트스트랩과 같은 정적 JavaScript 라이브러리를 사용하는 세 페이지로 구성) 이해(4-2단계)
> - 템플릿에서 제공하는 URL 라우팅 이해(4-3단계)

템플릿은 5단계에서 다루는 기본 인증도 제공합니다.

## <a name="step-4-1-create-a-project-from-the-template"></a>4-1단계: 템플릿에서 프로젝트 만들기

1. Visual Studio에서 **솔루션 탐색기**로 이동하여 이 자습서의 앞부분에서 만든 **LearningDjango** 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 새 솔루션을 사용하려는 경우에는 **파일** > **새로 만들기** > **프로젝트**를 대신 선택합니다.

1. 새 프로젝트 대화 상자에서 **Django 웹 프로젝트** 템플릿을 검색하여 선택하고 프로젝트의 이름을 "DjangoWeb"으로 지정하고 **확인**을 선택합니다.

1. 템플릿에는 *requirements.txt* 파일이 포함되어 있으므로 Visual Studio에서 해당 종속성을 설치할 위치를 묻습니다. **가상 환경에 설치** 옵션을 선택하고 **가상 환경 추가** 대화 상자에서 **만들기**를 선택하여 기본값을 그대로 사용합니다.

1. Visual Studio에서 가상 환경 설정이 완료되면 표시된 *readme.html*의 지침에 따라 Django 슈퍼 사용자(즉, 관리자)를 만듭니다. Visual Studio 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Python** > **Django Create Superuser**(Django 슈퍼 사용자 만들기) 명령을 선택한 다음, 프롬프트에 따릅니다. 앱의 인증 기능을 연습할 때 사용하게 되므로 사용자 이름과 암호를 기록해 두어야 합니다.

1. **솔루션 탐색기**에서 해당 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택하여 **DjangoWeb** 프로젝트가 Visual Studio 솔루션의 기본값이 되도록 설정합니다. 굵게 표시된 시작 프로젝트는 디버거를 시작할 때 실행됩니다.

    ![DjangoWeb 프로젝트를 시작 프로젝트로 표시하는 솔루션 탐색기](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용하여 서버를 실행합니다.

    ![Visual Studio의 웹 서버 실행 도구 모음 단추](media/django/run-web-server-toolbar-button.png)

1. 템플릿으로 만든 앱에는 홈, 정보, 연락처라는 세 개의 페이지가 있으며, 탐색 모음을 사용하여 페이지 간에 이동할 수 있습니다. 1-2분 동안 앱의 다른 부분을 살펴보세요. **로그인** 명령을 통해 앱을 인증하려면 앞에서 만든 슈퍼 사용자 자격 증명을 사용합니다.

    ![Django 웹 프로젝트 앱의 전체 브라우저 보기](media/django/step04-full-app-desktop-view.png)

1. “Django 웹 프로젝트” 템플릿으로 만든 앱은 모바일 폼 팩터를 수용하는 반응형 레이아웃에 부트스트랩을 사용합니다. 이러한 응답성을 확인하려면 콘텐츠가 세로로 렌더링되고 탐색 모음이 메뉴 아이콘으로 전환되도록 브라우저 크기를 좁은 보기로 조정합니다.

    ![Django 웹 프로젝트 앱의 모바일(좁은) 보기](media/django/step04-full-app-mobile-view.png)

1. 다음 섹션을 위해 앱이 계속 실행되도록 할 수 있습니다.

    앱을 중지하고 [변경 내용을 소스 제어에 커밋](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)하려면 먼저 **팀 탐색기**에서 **변경 내용** 페이지를 열고, 가상 환경에 대한 폴더(**env**)를 마우스 오른쪽 단추로 클릭하고, **이 로컬 항목 무시**를 선택합니다.

### <a name="examine-what-the-template-creates"></a>템플릿에서 만드는 항목 검사

가장 광범위한 수준에서 “Django 웹 프로젝트” 템플릿은 다음과 같은 구조를 만듭니다.

- 프로젝트 루트의 파일:
  - *manage.py*: Django 관리 유틸리티.
  - *db.sqlite3*: 기본 SQLite 데이터베이스.
  - *requirements.txt*는 Django 1.x에 대한 종속성을 포함합니다.
  - *readme.html*: 프로젝트를 만든 후 Visual Studio에 표시되는 파일. 이전 섹션에서 설명한 대로 여기에 표시되는 지침에 따라 앱에 대한 슈퍼 사용자(관리자) 계정을 만듭니다.
- *app* 폴더에는 보기, 모델, 테스트, 양식, 템플릿 및 정적 파일을 포함한 모든 앱 파일이 포함됩니다(4-2단계 참조). 일반적으로 보다 고유한 앱 이름을 사용하려면 이 폴더의 이름을 바꿉니다.
- *DjangoWeb*(Django 프로젝트) 폴더에는 *\_\_init\_\_.py*, *settings.py*, *urls.py* 및 *wsgi.py*와 같은 일반적인 Django 프로젝트 파일이 포함됩니다. 프로젝트 템플릿을 사용하여 *settings.py*는 앱 및 데이터베이스 파일에 대해 이미 구성하고 *urls.py*는 로그인 양식을 포함하여 모든 앱 페이지에 대한 경로로 이미 구성했습니다.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>질문: Visual Studio 프로젝트 간에 가상 환경을 공유할 수 있나요?

대답: 예, 하지만 시간이 지나면 프로젝트마다 다른 패키지를 사용할 수 있다는 점을 인식하고 공유해야 합니다. 따라서 공유된 가상 환경에는 해당 환경을 사용하는 모든 프로젝트에 대한 모든 패키지가 포함되어야 합니다.

그래도 기존 가상 환경을 사용하려면 다음을 수행하세요.

1. Visual Studio에 종속성을 설치하라는 메시지가 표시되면 **직접 설치** 옵션을 선택합니다.
1. **솔루션 탐색기**에서 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **기존 가상 환경 추가**를 선택합니다.
1. 가상 환경을 포함하는 폴더로 이동하여 선택하고 **확인**을 선택합니다.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>4-2단계: 프로젝트 템플릿으로 만든 보기 및 페이지 템플릿 이해

프로젝트를 실행하면 앱에 홈, 정보, 연락처의 세 가지 보기가 포함되어 있음을 알 수 있습니다. 이러한 보기에 대한 코드는 *app/views* 폴더에 있습니다. 각 보기 함수는 템플릿의 경로 및 간단한 사전 개체로 `django.shortcuts.render`를 호출합니다. 예를 들어 정보 페이지는 `about` 함수에 의해 처리됩니다.

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

템플릿은 앱의 *templates/app* 폴더에 있으며, 일반적으로 *앱*의 이름을 실제 앱의 이름으로 바꾸려고 합니다. 기본 템플릿인 *layout.html*이 가장 광범위합니다. 이 템플릿은 필요한 모든 정적 파일(JavaScript 및 CSS)을 참조하고, 다른 페이지에서 재정의하는 “content”라는 블록을 정의하며, “scripts”라는 다른 블록을 제공합니다. *layout.html*에서 주석 처리된 다음 발췌 부분은 이러한 특정 영역을 보여줍니다.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
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

또한 *templates/app* 폴더에는 `{% include %}`를 사용하여 *layout.html*을 가져오는 *loginpartial.html*과 함께 네 번째 페이지인 *login.html*이 있습니다. 이 템플릿 파일은 인증에 대한 5단계에서 설명합니다.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>질문: {% block %} 및 {% endblock %}은 Django 페이지 템플릿에서 들여쓰기할 수 있나요?

대답: 예, Django 페이지 템플릿은 블록 태그를 들여쓰기하여 적절한 부모 요소에 맞추는 경우에도 제대로 작동합니다. Visual Studio 프로젝트 템플릿으로 생성한 페이지 템플릿에서는 들여쓰기되지 않으므로 위치를 명확하게 확인할 수 있습니다.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>4-3단계: 템플릿으로 만든 URL 라우팅 이해

"Django 웹 프로젝트" 템플릿으로 만든 Django 프로젝트의 *urls.py* 파일에는 다음 코드가 포함되어 있습니다.

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

처음 세 개의 URL 패턴은 앱의 *views.py* 파일에 있는 `home`, `contact` 및 `about` 보기에 직접 매핑됩니다. 반면 `^login/$` 및 `^logout$` 패턴은 앱 정의 보기 대신 기본 제공 Django 보기를 사용합니다. `url` 메서드 호출에도 보기를 사용자 지정할 수 있는 추가 데이터가 포함됩니다. 5단계에서 이러한 호출을 살펴봅니다.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>질문: 제가 만든 프로젝트에서 "about" URL 패턴이 여기에 표시된 '^about$' 대신 '^about'을 사용하는 이유는 무엇인가요?

대답: 정규식에서 후행 ‘$’를 사용하지 않는 것은 여러 버전의 프로젝트 템플릿에서 단순한 실수였습니다. URL 패턴은 “about”이라는 페이지에서 완벽하게 작동하지만 후행 ‘$’가 없을 경우 URL 패턴은 “about=django”, “about09876”, “aboutoflaughter” 등의 URL과도 일치합니다. 후행 ‘$’는 “about”과’만’ 일치하는 URL 패턴을 만들기 위해 여기에 표시된 것입니다. 

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Django에서 사용자 인증](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Azure App Service에 웹앱 배포](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Writing your first Django app, part 4 - forms and generic views](https://docs.djangoproject.com/en/2.0/intro/tutorial04/)(첫 번째 Django 앱 작성, 4부 - 양식 및 일반 보기)(docs.djangoproject.com)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
