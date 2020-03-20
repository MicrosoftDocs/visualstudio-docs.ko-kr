---
title: Visual Studio, 5단계, 인증에서 Django 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Django 기본 사항을 검토하는 연습 과정으로, Django 웹 프로젝트 템플릿에서 제공하는 인증 기능을 구체적으로 설명합니다.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bdc76b0a7b9d3f74da77b317faf31dae83706f04
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957871"
---
# <a name="step-5-authenticate-users-in-django"></a>5단계: Django에서 사용자 인증

**이전 단계: [전체 Django 웹 프로젝트 템플릿 사용](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

인증은 웹앱에 일반적으로 필요하므로 “Django 웹 프로젝트” 템플릿에는 기본 인증 흐름이 포함됩니다. 이 자습서의 6단계에서 설명하는 “설문 조사 Django 웹 프로젝트” 템플릿에도 동일한 흐름이 포함되어 있습니다. Django 프로젝트 템플릿을 사용하는 경우 Visual Studio는 인증에 필요한 모든 모듈을 Django 프로젝트의 *settings.py*에 포함합니다.

이 단계에서는 다음 내용을 학습합니다.

> [!div class="checklist"]
> - Visual Studio 템플릿에 제공된 인증 흐름을 사용하는 방법(5-1단계)

## <a name="step-5-1-use-the-authentication-flow"></a>5-1단계: 인증 흐름 사용

다음 단계에서는 인증 흐름을 실행하고 프로젝트의 관련 부분에 대해 설명합니다.

1. 프로젝트 루트에 있는 *readme.html* 파일의 지침에 따라 슈퍼 사용자(관리자) 계정을 아직 만들지 않은 경우 지금 만듭니다.

1. Visual Studio에서 **디버그** > **디버깅 시작**(**F5**)을 사용하여 앱을 실행합니다. 앱이 브라우저에 나타나면 **로그인**이 탐색 모음 오른쪽 위에 나타나는지 확인합니다.

    ![Django 웹 프로젝트 앱 페이지의 로그인 컨트롤](media/django/step05-login-control.png)

1. *templates/app/layout.html*을 열고 `<div class="navbar ...>` 요소에 `{% include app/loginpartial.html %}` 태그가 포함되어 있는지 확인합니다. `{% include %}` 태그는 포함하는 템플릿의 이 지점에서 포함된 파일의 내용을 풀하도록 Django의 템플릿 시스템에 지시합니다.

1. *templates/app/loginpartial.html*을 열고 `{% else %}` 태그와 함께 조건부 태그 `{% if user.is_authenticated %}`를 사용하여 사용자가 인증되었는지 여부에 따라 다른 UI 요소를 렌더링하는 방법을 확인합니다.

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. 처음으로 앱을 시작하면 인증된 사용자가 없기 때문에 이 템플릿 코드는 “로그인” 링크를 상대 경로 “login”으로만 렌더링합니다. 이전 섹션에 표시된 *urls.py*에 지정된 대로 해당 경로는 `django.contrib.auth.views.login` 보기에 매핑됩니다. 해당 보기는 다음 데이터를 수신합니다.

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    여기서 `template_name`은 로그인 페이지(이 경우 *templates/app/login.html*)의 템플릿을 식별합니다. `extra_context` 속성이 템플릿에 지정된 기본 컨텍스트 데이터에 추가됩니다. 마지막으로 `authentication_form`은 `form` 개체로 나타나는 템플릿에서 로그인에 사용할 양식 클래스를 지정합니다. 기본값은 `django.contrib.auth.views`의 `AuthenticationForm`입니다. Visual Studio 프로젝트 템플릿은 앱의 *forms.py* 파일에 정의된 양식을 대신 사용합니다.

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    여기서는 이 양식 클래스가 `AuthenticationForm`에서 파생되며, 특히 사용자 이름 및 암호 필드를 재정의하여 자리 표시자 텍스트를 추가합니다. 암호 강도 유효성 검사 추가와 같이 양식을 사용자 지정할 수 있다는 가정하에 Visual Studio 템플릿에는 이 명시적 코드가 포함되어 있습니다.

1. 로그인 페이지로 이동하면 앱이 *login.html* 템플릿을 렌더링합니다. `{{ form.username }}` 및 `{{ form.password }}` 변수는 `BootstrapAuthenticationForm`에서 `CharField` 양식을 렌더링합니다. 유효성 검사 오류를 표시하는 기본 제공 섹션과 해당 서비스를 추가하도록 선택한 경우 소셜 로그인에 대해 미리 만들어진 요소도 있습니다.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. 양식을 제출하면 Django는 사용자 자격 증명(예: 슈퍼 사용자의 자격 증명)을 인증하려고 합니다. 인증에 실패하면 현재 페이지에 유지되지만 `form.errors`는 true로 설정됩니다. 인증에 성공하면 Django는 “next” 필드 `<input type="hidden" name="next" value="/" />`의 상대 URL(이 경우 홈페이지(`/`))로 이동합니다.

1. 이제 홈페이지를 다시 렌더링하면 *loginpartial.html* 템플릿이 렌더링될 때 `user.is_authenticated` 속성은 true입니다. 따라서 **Hello (사용자 이름)** 메시지와 **로그오프**가 표시됩니다. 앱의 다른 부분에서 `user.is_authenticated`를 사용하여 인증을 확인할 수 있습니다.

    ![Django 웹 프로젝트 앱 페이지의 Hello 메시지 및 로그오프 컨트롤](media/django/step05-logoff-control.png)

1. 인증된 사용자에게 특정 리소스에 액세스할 수 있는 권한이 있는지 확인하려면 데이터베이스에서 사용자별 사용 권한을 검색해야 합니다. 자세한 내용은 [Django 인증 시스템 사용](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization)(Django 문서)을 참조하세요.

1. 특히 슈퍼 사용자 또는 관리자는 상대 URL “/admin/” 및 “/admin/doc/”를 사용하여 기본 제공 Django 관리자 인터페이스에 액세스할 수 있습니다. 이러한 인터페이스를 사용하도록 설정하려면 다음을 수행합니다.

    1. 사용자 환경에 docutils Python 패키지를 설치합니다. 이 작업을 수행하는 적합한 방법은 "docutils"를 *requirements.txt* 파일에 추가한 다음, **솔루션 탐색기**에서 프로젝트 및 **Python 환경** 노드를 차례로 확장한 다음, 사용하는 환경을 마우스 오른쪽 단추로 클릭하여 **requirements.txt에서 설치**를 선택합니다.

    1. Django 프로젝트의 *urls.py*를 열고, 다음 항목에서 기본 주석을 제거합니다.

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. Django 프로젝트의 *settings.py* 파일의 `INSTALLED_APPS` 컬렉션으로 이동하여 `'django.contrib.admindocs'`를 추가합니다.

    1. 앱을 다시 시작하면 “/admin/” 및 “/admin/doc/”로 이동하여 추가 사용자 계정 만들기와 같은 작업을 수행할 수 있습니다.

        ![Django 관리자 인터페이스](media/django/step05-administrator-interface.png)

1. 인증 흐름의 마지막 부분은 로그오프입니다. *loginpartial.html*에서처럼 **로그오프** 링크는 상대 URL "/login"에 대해 POST를 수행하며, 기본 제공 보기 `django.contrib.auth.views.logout`에 의해 처리됩니다. 이 보기는 UI를 표시하지 않으며 “^logout$” 패턴에 대해 *urls.py*에 표시된 대로 홈페이지로 이동하기만 합니다. 로그오프 페이지를 표시하려면 먼저 URL 패턴을 다음과 같이 변경하여 “template_name” 속성을 추가하고 “next_page” 속성을 제거합니다.

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    그런 다음, 다음 최소 내용으로 *templates/app/loggedoff.html*을 만듭니다.

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    결과는 다음과 같이 나타납니다.

    ![추가된 로그오프된 페이지](media/django/step05-logged-off-page.png)

1. 모든 작업이 완료되면 서버를 중지하고 다시 한번 변경 내용을 소스 제어에 커밋합니다.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>질문: \<form\> 요소에 나타나는 {% csrf_token %} 태그의 용도는 무엇인가요?

대답: `{% csrf_token %}` 태그에는 Django의 기본 제공 [CSRF(교차 사이트 요청 위조) 보호](https://docs.djangoproject.com/en/2.0/ref/csrf/)(Django 문서)가 포함됩니다. 일반적으로 양식과 같이 POST, PUT 또는 DELETE 요청 메서드를 포함하는 요소에 이 태그를 추가합니다. 그런 다음, 템플릿 렌더링 함수(`render`)에서 필요한 보호를 삽입합니다.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [설문 조사 Django 웹 프로젝트 템플릿 사용](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>자세히 알아보기

- [User authentication in Django](https://docs.djangoproject.com/en/2.0/topics/auth/)(Django의 사용자 인증)(docs.djangoproject.com)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
