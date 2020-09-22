---
title: Visual Studio 2단계, 보기 및 페이지 템플릿에서 Django 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Django 기본 사항을 검토하는 연습 과정으로, 앱을 만들고 보기 및 템플릿을 사용하는 단계를 구체적으로 설명합니다.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 8d91e587f354efe14db7cd669fa89a0f4658a538
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90097309"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2단계: 보기 및 페이지 템플릿을 사용하여 Django 앱 만들기

**이전 단계: [Visual Studio 프로젝트 및 솔루션 만들기](learn-django-in-visual-studio-step-01-project-and-solution.md)**

지금까지 Visual Studio 프로젝트에는 하나 이상의 Django *앱*을 실행할 수 있는, Django *프로젝트*의 사이트 수준 구성 요소만 있었습니다. 다음 단계에서는 단일 페이지로 구성된 첫 번째 앱을 만듭니다.

이 단계에서는 다음 작업을 수행하는 방법을 배웁니다.

> [!div class="checklist"]
> - 단일 페이지로 구성된 Django 앱 만들기(2-1단계)
> - Django 프로젝트에서 앱 실행(2-2단계)
> - HTML을 사용하여 보기 렌더링(2-3단계)
> - Django 페이지 템플릿을 사용하여 보기 렌더링(2-4단계)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>2-1단계: 기본 구조로 앱 만들기

Django 앱은 특정 용도로 관련 파일 집합을 포함하는 별도의 Python 패키지입니다. Django 프로젝트에는 많은 앱이 포함될 수 있으며, 이는 웹 호스트가 단일 도메인 이름으로 많은 별도의 진입점을 제공할 수 있다는 사실을 반영합니다. 예를 들어 contoso.com과 같은 도메인에 대한 Django 프로젝트에는 `www.contoso.com`용 앱 하나와 support.contoso.com용 두 번째 앱 및 docs.contoso.com용 세 번째 앱이 포함될 수 있습니다. 이 경우에 Django 프로젝트는 해당 *urls.py* 및 *settings.py* 파일에서 사이트 수준 URL 라우팅 및 설정을 처리하는 반면, 각 앱은 내부 라우팅, 보기, 모델, 정적 파일 및 관리 인터페이스를 통해 고유한 스타일 및 동작을 갖습니다.

Django 앱은 일반적으로 표준 파일 집합으로 시작합니다. Visual Studio는 Django 프로젝트 내에서 Django 앱을 초기화하는 항목 템플릿을 동일한 용도로 사용되는 통합 메뉴 명령과 함께 제공합니다.

- 템플릿: **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다. **새 항목 추가** 대화 상자에서 **Django 1.9 앱** 템플릿을 선택하고, **이름** 필드에 앱 이름을 지정하고, **확인**을 선택합니다.

- 통합 명령: **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **Django 앱**을 선택합니다. 이 명령은 이름 입력을 요청하고 Django 1.9 앱을 만듭니다.

    ![Django 앱을 추가하는 메뉴 명령](media/django/step02-add-django-app-command.png)

두 방법 중 하나를 사용하여 “HelloDjangoApp”이라는 이름으로 앱을 만듭니다. 그 결과 다음 표에 설명된 항목을 포함하는 해당 이름의 폴더가 프로젝트에 생성됩니다.

![솔루션 탐색기의 Django 앱 파일](media/django/step02-django-app-in-solution-explorer.png)

| 항목 | 설명 |
| --- | --- |
| **\_\_init\_\_.py** | 앱을 패키지로 식별하는 파일입니다. |
| **migrations** | Django가 모델의 변경 내용에 맞게 데이터베이스를 업데이트하는 스크립트를 저장하는 폴더입니다. Django의 마이그레이션 도구는 현재 모델과 일치하도록 이전 버전의 데이터베이스에 필요한 변경 내용을 적용합니다. 마이그레이션을 사용하여 모델에 초점을 맞추고 Django에서 기본 데이터베이스 스키마를 처리하도록 합니다. 마이그레이션은 6단계에서 설명합니다. 지금 폴더에는 폴더가 고유한 Python 패키지를 정의한다고 나타내는 *\_\_init\_\_.py* 파일만 포함됩니다. |
| **templates** | 앱 이름과 일치하는 폴더 내에서 단일 파일 *index.html*을 포함하는 Django 페이지 템플릿의 폴더입니다. (Visual Studio 2017 15.7 이전 버전에서 파일은 *템플릿* 바로 아래에 포함되고 2-4단계에서는 사용자가 하위 폴더를 만들도록 지시합니다.) 템플릿은 보기에서 페이지를 동적으로 렌더링하기 위해 정보를 추가할 수 있는 HTML의 블록입니다. *index.html*의 `{{ content }}`와 같은 페이지 템플릿 "변수"는 이 아티클의 뒷부분(2단계)에서 설명하는 동적 값의 자리 표시자입니다. 일반적으로 Django 앱은 앱 이름과 일치하는 하위 폴더에 템플릿을 저장하여 해당 템플릿에 대한 네임스페이스를 만듭니다. |
| **admin.py** | 데이터베이스의 데이터를 시드하고 편집하는 데 사용되는 앱의 관리 인터페이스(6단계 참조)를 확장하는 Python 파일입니다. 처음에는 이 파일에 `from django.contrib import admin` 문만 포함되어 있습니다. 기본적으로 Django에는 Django 프로젝트의 *settings.py* 파일에 있는 항목을 통해 표준 관리 인터페이스가 포함됩니다. 이 인터페이스는 *urls.py*에 있는 기존 항목의 주석 처리를 제거하여 설정할 수 있습니다. |
| **apps.py** | 앱에 대한 구성 클래스를 정의하는 Python 파일입니다(이 표 다음의 아래 참조). |
| **models.py** | 모델은 보기가 앱의 기본 데이터베이스와 상호 작용하는 데 사용되는 데이터 개체로, 함수로 식별됩니다(6단계 참조). Django는 앱이 세부 정보에 주의를 기울일 필요가 없도록 데이터베이스 연결 계층을 제공합니다. *models.py* 파일은 모델을 만들 기본 위치이며, 처음에는 `from django.db import models` 문만 포함되어 있습니다. |
| **tests.py** | 단위 테스트의 기본 구조를 포함하는 Python 파일입니다. |
| **views.py** | 보기는 일반적으로 웹 페이지로 간주되는 항목으로, HTTP 요청을 만들고 HTTP 응답을 반환합니다. 일반적으로 보기는 웹 브라우저에서 표시하는 방법을 알고 있는 HTML로 렌더링되지만 중간 양식처럼 보기가 반드시 표시되어야 하는 것은 아닙니다. 보기는 HTML을 렌더링하여 브라우저로 보내는 Python 함수에 의해 정의됩니다. *views.py* 파일은 보기를 만들 기본 위치이며, 처음에는 `from django.shortcuts import render` 문만 포함되어 있습니다. |

"HelloDjangoApp"이라는 이름을 사용하면 *apps.py*의 내용이 다음과 같이 표시됩니다.

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>질문: Visual Studio에서 Django 앱을 만들면 명령줄에서 앱을 만드는 것과 다른가요?

대답: **추가** > **Django 앱** 명령을 실행하거나 Django 앱 템플릿에서 **추가** > **새 항목**을 사용하면 Django 명령 `manage.py startapp <app_name>`과 동일한 파일이 생성됩니다. Visual Studio에서 앱을 만들면 앱 폴더와 모든 파일이 프로젝트에 자동으로 통합되는 장점이 있습니다. 동일한 Visual Studio 명령을 사용하여 프로젝트에 많은 앱을 만들 수 있습니다.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>2-2단계: Django 프로젝트에서 앱 실행

이때 Visual Studio에서 도구 모음 단추나 **디버그** > **디버깅 시작**을 사용하여 프로젝트를 다시 실행하면 기본 페이지가 표시됩니다. 앱 관련 페이지를 정의하고 Django 프로젝트에 앱을 추가해야 하므로 앱 콘텐츠가 나타나지 않습니다.

1. *HelloDjangoApp* 폴더에서 아래 코드와 일치하도록 *views.py*를 수정하여 "index"라는 보기를 정의합니다.

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. 1단계에서 만든 *BasicProject* 폴더에서 적어도 다음 코드와 일치하도록 *urls.py*를 수정합니다. 원하는 경우 유용한 주석을 유지할 수 있습니다.

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    각 URL 패턴은 Django가 특정 사이트 기준 URL(즉, `https://www.domain.com/` 다음에 오는 부분)을 라우팅하는 보기를 설명합니다. 정규식 `^$`로 시작하는 `urlPatterns`의 첫 번째 항목은 사이트 루트 “/”에 대한 라우팅입니다. 두 번째 항목인 `^home$`은 특히 “/home”을 라우팅합니다. 동일한 보기에 대한 라우팅이 여러 개 있을 수 있습니다.

1. 프로젝트를 다시 실행하면 **Hello, Django!** 메시지가 표시됩니다. 메시지를 확인합니다. 완료되면 서버를 중지합니다.

### <a name="commit-to-source-control"></a>소스 제어에 커밋

코드를 변경하고 성공적으로 테스트했으므로 이제 변경 내용을 검토하고 소스 제어에 커밋해야 합니다. 이 자습서의 이후 단계에서는 소스 제어에 다시 커밋해야 하는 적절한 시간을 알려주므로 이 섹션을 다시 참조하세요.

1. Visual Studio의 아래쪽(아래 원)에 있는 변경 단추를 선택하여 **팀 탐색기**로 이동합니다.

    ![Visual Studio 상태 표시줄의 소스 제어 변경 단추](media/django/step02-source-control-changes-button.png)

1. **팀 탐색기**에서 “Create initial Django app”과 같은 커밋 메시지를 입력하고 **모두 커밋**을 선택합니다. 커밋이 완료되면 **커밋 \<hash>을(를) 로컬에서 만들었습니다. 서버의 변경 내용을 공유하여 동기화합니다.** 라는 메시지가 표시됩니다. 원격 리포지토리에 변경 내용을 푸시하려면 **동기화**를 선택한 다음, **나가는 커밋**에서 **푸시**를 선택합니다. 원격에 푸시하기 전에 여러 개의 로컬 커밋을 누적할 수도 있습니다.

    ![팀 탐색기에서 원격에 커밋 푸시](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>질문: 라우팅 문자열 앞에 있는 'r' 접두사는 무엇인가요?

대답: Python에서 문자열의 ‘r’ 접두사는 “원시”를 의미하며, Python에서 문자열 내의 문자를 이스케이프하지 않도록 지시합니다. 정규식에서는 여러 가지 특수 문자를 사용하므로 'r' 접두사를 사용하면 문자열에 많은 '\\' 이스케이프 문자가 포함된 경우보다 훨씬 더 쉽게 해당 문자열을 읽을 수 있습니다.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>질문: URL 라우팅 항목에서 ^ 및 $ 문자의 의미는 무엇인가요?

대답: URL 패턴을 정의하는 정규식에서 ^는 “줄의 시작”을 의미하고 $는 “줄의 끝”을 의미합니다. 이때 URL은 사이트 루트(`https://www.domain.com/` 다음에 오는 부분)에 상대적입니다. 정규식 `^$`는 결과적으로 “공백”을 의미하므로 전체 URL `https://www.domain.com/`(사이트 루트에 아무것도 추가되지 않음)과 일치합니다. `^home$` 패턴은 `https://www.domain.com/home/`과 정확히 일치합니다. Django는 패턴 일치에서 후행 /를 사용하지 않습니다.

`^home`과 마찬가지로 정규식에서 후행 $를 사용하지 않으면 URL 패턴이 “home”으로 시작하는 ‘모든’ URL(예: “home”, “homework”, “homestead” 및 “home192837”)과 일치합니다. 

다른 정규식으로 실험하려면 [pythex.org](https://www.pythex.org)에서 [regex101.com](https://regex101.com)과 같은 온라인 도구를 사용해 보세요.

## <a name="step-2-3-render-a-view-using-html"></a>2-3단계: HTML을 사용하여 보기 렌더링

지금까지 *views.py*의 `index` 함수는 페이지에 대해 일반 텍스트 HTTP 응답만 생성했습니다. 대부분의 실제 웹 페이지는 라이브 데이터를 자주 통합하는 서식 있는 HTML 페이지로 응답합니다. 실제로 함수를 사용하여 보기를 정의하는 주된 이유는 해당 콘텐츠를 동적으로 생성할 수 있기 때문입니다.

`HttpResponse`에 대한 인수는 단순한 문자열이므로 문자열 내에서 원하는 HTML을 작성할 수 있습니다. 간단한 예로 `index` 함수를 다음 코드(기존 `from` 문 유지)로 바꾸어 페이지를 새로 고칠 때마다 업데이트되는 동적 콘텐츠를 사용하여 HTML 응답을 생성합니다.

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

프로젝트를 다시 실행하여 “**Hello Django!** on Monday, 16 April, 2018 at 16:28:10”과 같은 메시지를 확인합니다. 페이지를 새로 고쳐 시간을 업데이트하고 각 요청과 함께 콘텐츠가 생성되는지 확인합니다. 완료되면 서버를 중지합니다.

> [!Tip]
> 프로젝트를 중지했다가 다시 시작하는 바로 가기는 **디버그** > **다시 시작** 메뉴 명령(**Ctrl**+**Shift**+**F5**)이나 디버깅 도구 모음의 **다시 시작** 단추를 사용하는 것입니다.
>
> ![Visual Studio 디버깅 도구 모음의 다시 시작 단추](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>2-4단계: 페이지 템플릿을 사용하여 보기 렌더링

매우 작은 페이지에서는 코드에서 HTML 생성이 제대로 작동하지만, 페이지가 더 복잡해지면 일반적으로 CSS 및 JavaScript 파일에 대한 참조와 함께 페이지의 정적 HTML 부분을 코드에서 생성된 동적 콘텐츠를 삽입하는 “페이지 템플릿”으로 유지 관리하려고 합니다. 이전 섹션에서는 `now.strftime` 호출의 날짜와 시간만 동적이며, 이는 다른 모든 콘텐츠를 페이지 템플릿에 배치할 수 있음을 의미합니다.

Django 페이지 템플릿은 `{{ content }}`에서처럼 `{{` 및 `}}`로 표시되는 “변수”라는 여러 가지 대체 토큰을 포함할 수 있는 HTML 블록입니다. Django의 템플릿 모듈에서는 변수를 코드에서 제공하는 동적 콘텐츠로 변수를 바꿉니다.

다음 단계에서는 페이지 템플릿의 사용을 보여줍니다.

1. Django 프로젝트가 포함된 *BasicProject* 폴더에서 *settings.py* 파일을 열고 앱 이름 "HelloDjangoApp"을 `INSTALLED_APPS` 목록에 추가합니다. 목록에 앱을 추가하면 앱이 포함된 해당 이름의 폴더가 있음을 Django 프로젝트에 알립니다.

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. 또한 *settings.py*에서 `TEMPLATES` 개체에 다음 줄이 포함되어 있는지 확인합니다(기본적으로 포함됨). 이 개체는 설치된 앱의 *templates* 폴더에서 템플릿을 검색하도록 Django에 지시합니다.

    ```json
    'APP_DIRS': True,
    ```

1. *HelloDjangoApp* 폴더에서 *templates/HelloDjangoApp/index.html* 페이지 템플릿 파일(또는 VS 2017 15.7 이전에서 *templates/index.html*)을 열어 하나의 변수인 `{{ content }}`가 포함되어 있는지 확인합니다.

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. *HelloDjangoApp* 폴더에서 *views.py*를 열고, `index` 함수를 `django.shortcuts.render` 도우미 함수를 사용하는 다음 코드로 바꿉니다. `render` 도우미는 페이지 템플릿 작업을 위한 간단한 인터페이스를 제공합니다. 기존 `from` 문은 모두 유지해야 합니다.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    여기서 `render`에 대한 첫 번째 인수는 요청 개체이며, 앱의 *templates* 폴더 내에 있는 템플릿 파일의 상대 경로가 뒤에 옵니다. 해당하는 경우 템플릿 파일의 이름은 보기에 대해 지정됩니다. `render`에 대한 세 번째 인수는 템플릿이 참조하는 변수의 사전입니다. 사전에 개체를 포함할 수 있으며, 이 경우 템플릿의 변수는 `{{ object.property }}`를 참조할 수 있습니다.

1. 프로젝트를 실행하고 출력을 확인합니다. 2-2단계에서 보여진 유사한 메시지가 표시되어 템플릿이 작동함을 나타냅니다.

    그러나 `content` 속성에 사용된 HTML은 `render` 함수가 해당 HTML을 자동으로 이스케이프하기 때문에 일반 텍스트로만 렌더링됩니다. 자동 이스케이프는 주입 공격에 대한 우발적인 취약성을 방지합니다. 개발자는 종종 한 페이지에서 입력을 수집하고 템플릿 자리 표시자를 통해 다른 페이지의 값으로 사용합니다. 이스케이프는 HTML을 페이지 템플릿에 두고 코드에는 넣지 않는 것이 최선이라는 것을 상기시켜 주는 역할도 합니다. 다행히 필요한 경우 추가 변수를 만드는 것이 간단합니다. 예를 들어 다음 태그와 일치하도록 *템플릿*을 포함한 *index.html*을 변경하여 페이지 제목을 추가하고 페이지 템플릿의 모든 서식을 유지합니다.

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

    그런 다음, `index` 보기 함수를 다음과 같이 작성하여 페이지 템플릿의 모든 변수에 대해 값을 제공합니다.

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. 서버를 중지하고 프로젝트를 다시 시작한 후 페이지가 올바르게 렌더링되는지 확인합니다.

    ![템플릿을 사용하여 앱 실행](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 버전 15.7 이하: 마지막 단계로 앱과 동일한 이름의 하위 폴더로 템플릿을 이동하여 네임스페이스를 만들고 프로젝트에 추가할 수 있는 다른 앱과의 잠재적인 충돌을 방지합니다. (VS 2017 15.8+의 템플릿은 이 작업을 자동으로 수행합니다.) 즉, *HelloDjangoApp*이라는 *templates*의 하위 폴더를 만들고, *index.html*을 해당 하위 폴더로 이동하고, 템플릿의 새 경로인 *HelloDjangoApp/index.html*을 참조하도록 `index` 보기 함수를 수정합니다. 그런 다음, 프로젝트를 실행하고 페이지가 올바르게 렌더링되는지 확인한 후 서버를 중지합니다.

1. 원하는 경우 [2-2단계](#commit-to-source-control)에 설명된 대로 변경 내용을 소스 제어에 커밋하고 원격 리포지토리를 업데이트합니다.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>질문: 페이지 템플릿은 별도의 파일에 있어야 하나요?

대답: 템플릿은 일반적으로 별도의 HTML 파일에서 유지 관리되지만 인라인 템플릿을 사용할 수도 있습니다. 그러나 태그와 코드를 명확하게 분리하려면 별도의 파일을 사용하는 것이 좋습니다.

### <a name="question-must-templates-use-the-html-file-extension"></a>질문: 템플릿은 .html 파일 확장명을 사용해야 하나요?

대답: 항상 `render` 함수에 대한 두 번째 인수에서 파일의 정확한 상대 경로를 식별하므로 페이지 템플릿 파일의 *.html* 확장명은 전적으로 선택 사항입니다. 그러나 Visual Studio(및 기타 편집기)는 일반적으로 *.html* 파일을 사용하여 코드 완성 및 구문 색 지정과 같은 기능을 제공하므로 페이지 템플릿이 엄격하게 HTML이 아니라는 사실보다 중요합니다.

실제로 Django 프로젝트로 작업할 때 Visual Studio는 편집 중인 HTML 파일이 실제로 Django 템플릿인 경우를 자동으로 감지하고 특정 자동 완성 기능을 제공합니다. 예를 들어 Django 페이지 템플릿 주석 `{#`을 입력하기 시작하면 Visual Studio에서 닫는 `#}` 문자를 자동으로 제공합니다. **선택 영역을 주석으로 처리** 및 **선택 영역의 주석 처리 제거** 명령(**편집** >  **고급** 메뉴 및 도구 모음)에서도 HTML 주석 대신 템플릿 주석을 사용합니다.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>질문: 프로젝트를 실행하면 템플릿을 찾을 수 없다는 오류가 표시됩니다. 무엇이 문제인가요?

대답: 템플릿을 찾을 수 없다는 오류가 표시되면 `INSTALLED_APPS` 목록에서 Django 프로젝트의 *settings.py*에 앱을 추가했는지 확인하세요. 해당 항목이 없으면 Django에서 앱의 *templates* 폴더를 찾을 수 없습니다.

### <a name="question-why-is-template-namespacing-important"></a>질문: 템플릿 네임스페이스 지정이 중요한 이유는 무엇인가요?

대답: Django가 `render` 함수에서 참조된 템플릿을 찾는 경우 처음으로 찾은 상대 경로와 일치하는 파일을 사용합니다. 템플릿에 동일한 폴더 구조를 사용하는 여러 Django 앱이 동일한 프로젝트에 있는 경우 한 앱에서 다른 앱의 템플릿을 실수로 사용할 수 있습니다. 이러한 오류를 방지하려면 항상 앱의 이름과 일치하는 앱의 *templates* 폴더 아래에 하위 폴더를 만들어 모든 중복을 방지하세요.

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [정적 파일 제공, 페이지 추가 및 템플릿 상속 사용](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Writing your first Django app, part 1 - views](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view)(첫 번째 Django 앱 작성, 1부 - 보기)(docs.djangoproject.com)
- 포함 및 상속과 같은 Django 템플릿의 추가 기능은 [The Django template language](https://docs.djangoproject.com/en/2.0/ref/templates/language/)(Django 템플릿 언어)(docs.djangoproject.com)를 참조하세요.
- [Regular expression training on inLearning](https://www.linkedin.com/learning/topics/regular-expressions)(inLearning의 정규식 교육)(LinkedIn)
- GitHub의 자습서 소스 코드: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
