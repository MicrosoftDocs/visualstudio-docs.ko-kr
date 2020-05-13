---
title: Visual Studio 5단계, 설문 조사 프로젝트 템플릿에서 Flask 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Flask 기본 사항을 검토하는 연습 과정으로, 특히 설문 조사 Flask 웹 프로젝트 및 설문 조사 Flask/Jadek 웹 프로젝트 템플릿의 기능을 구체적으로 설명합니다.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c540dfef9d2d46bb621432b3e37438e0b6b07298
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154890"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>5단계: 설문조사 Flask 웹 프로젝트 템플릿 사용

**이전 단계: [전체 Flask 웹 프로젝트 템플릿 사용](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Visual Studio의 “Flask 웹 프로젝트” 템플릿을 이해했으면 이제 동일한 코드베이스를 기반으로 하는 “설문 조사 Flask 웹 프로젝트”라는 세 번째 Flask 템플릿을 살펴볼 수 있습니다.

이 단계에서는 다음 방법을 학습합니다.

> [!div class="checklist"]
> - 템플릿에서 프로젝트를 만들고 데이터베이스 초기화(5-1단계)
> - 데이터 모델 이해(5-2단계)
> - 백업 데이터 저장소 이해(5-3단계)
> - 설문 조사 세부 정보 및 결과 보기(단계 5-4) 이해

또한 Visual Studio는 동일한 앱을 생성하지만 Jinja 템플레이팅 엔진에 Jade 확장을 사용하는 "설문 조사 Flask/Jade 웹 프로젝트" 템플릿도 제공합니다. 자세한 내용은 [4단계 - Flask/Jade 웹 프로젝트 템플릿](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template)을 참조하세요.

## <a name="step-5-1-create-the-project"></a>5-1단계: 프로젝트 만들기

1. Visual Studio에서 **솔루션 탐색기**로 이동하여 이 자습서의 앞부분에서 만든 **LearningFlask** 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 새 솔루션을 사용하려는 경우에는 **파일** > **새로 만들기** > **프로젝트**를 대신 선택합니다.

1. 새 프로젝트 대화 상자에서 **설문 조사 Flask 웹 프로젝트** 템플릿을 검색하여 선택하고 프로젝트의 이름을 "FlaskPolls"로 지정하고 **확인**을 선택합니다.

1. Visual Studio의 다른 프로젝트 템플릿과 마찬가지로 "설문 조사 Flask 웹 프로젝트" 템플릿에는 *requirements.txt* 파일이 포함되어 있으므로 Visual Studio에서는 해당 종속성을 설치할 위치를 묻습니다. **가상 환경에 설치** 옵션을 선택하고 **가상 환경 추가** 대화 상자에서 **만들기**를 선택하여 기본값을 그대로 사용합니다. (이 템플릿은 Flask와 azure-storage 및 pymongo 패키지가 필요하고, "설문 조사 Flask/Jade 웹 프로젝트"도 pyjade가 필요합니다.)

1. **솔루션 탐색기**에서 해당 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택하여 **FlaskPolls** 프로젝트가 Visual Studio 솔루션의 기본값이 되도록 설정합니다. 굵게 표시된 시작 프로젝트는 디버거를 시작할 때 실행됩니다.

1. **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용하여 서버를 실행합니다.

    ![Visual Studio의 웹 서버 실행 도구 모음 단추](media/django/run-web-server-toolbar-button.png)

1. 템플릿으로 만든 앱에는 홈, 정보, 연락처라는 세 개의 페이지가 있으며, 맨 위의 탐색 모음을 사용하여 페이지 간에 이동할 수 있습니다. 1-2분 동안 앱의 다른 부분을 살펴보세요. 정보 및 연락처 페이지는 “Flask 웹 프로젝트”와 매우 유사하므로 더 자세히 설명하지 않습니다.

    ![설문 조사 Flask 웹 프로젝트 앱 전체 보기](media/flask/step06-full-app-view.png)

1. 홈 페이지에서 **샘플 설문 조사 만들기** 단추는 *models/samples.json* 페이지에 설명된 세 가지 설문 조사를 사용하여 앱의 데이터 저장소를 초기화합니다. 기본적으로 앱은 정보 페이지에 표시된 대로 메모리 내 데이터베이스를 사용하며, 앱이 다시 시작될 때마다 재설정됩니다. 이 앱에는 문서의 뒷부분에 설명한 대로 Azure Storage 및 Mongo DB와 함께 작동하는 코드도 포함되어 있습니다.

1. 데이터 저장소를 초기화한 후 홈 페이지에 표시된 대로 여러 설문 조사에 투표할 수 있습니다(간략하게 하기 위해 탐색 모음과 바닥글은 생략됨).

    ![데이터 저장소가 초기화된 후 설문 조사 앱 보기](media/flask/step06-polls-initialized.png)

1. 설문 조사를 선택하면 세부적인 선택 항목이 표시됩니다.

    ![설문 조사용 투표 인터페이스](media/flask/step06-polls-voting-interface.png)

1. 투표가 완료되면 앱에 결과 페이지가 표시되고 다시 투표할 수 있습니다.

    ![투표 후 결과 보기](media/flask/step06-polls-results.png)

1. 다음 섹션을 위해 앱이 계속 실행되도록 할 수 있습니다.

    앱을 중지하고 [변경 내용을 소스 제어에 커밋](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)하려면 먼저 **팀 탐색기**에서 **변경 내용** 페이지를 열고, 가상 환경에 대한 폴더(**env**)를 마우스 오른쪽 단추로 클릭하고, **이 로컬 항목 무시**를 선택합니다.

### <a name="examine-the-project-contents"></a>프로젝트 콘텐츠 검사

앞에서 설명한 대로 “설문 조사 Flask 웹 프로젝트” 템플릿(및 “설문 조사 Flask/Jade” 템플릿)에서 만든 프로젝트의 많은 부분이 Visual Studio의 다른 프로젝트 템플릿을 살펴본 경우처럼 익숙해야 합니다. 이 문서의 추가 단계에서는 보다 중요한 변경 사항 및 추가 사항 즉, 데이터 모델 및 추가 보기에 대해 간략하게 설명합니다.

## <a name="step-5-2-understand-the-data-models"></a>5-2단계: 데이터 모델 이해

앱의 데이터 모델은 *models/\_\_init\_\_.py*에 정의된 Poll 및 Choice라는 Python 클래스입니다. Poll은 질문을 나타내며, Choice 인스턴스 컬렉션은 이 질문에 사용 가능한 답변을 나타냅니다. Poll은 모든 선택 사항에 대한 총 투표 수와 보기를 생성하는 데 사용되는 통계를 계산하는 메서드를 유지합니다.

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

이러한 데이터 모델은 다음 단계에서 설명하는 여러 가지 백업 데이터 저장소에서 앱의 보기가 작동할 수 있도록 하는 일반 추상화입니다.

## <a name="step-5-3-understand-the-backing-data-stores"></a>5-3단계: 백업 데이터 저장소 이해

"설문 조사 Flask 웹 프로젝트" 템플릿으로 만든 앱은 메모리, Azure 테이블 스토리지 또는 Mongo DB 데이터베이스의 데이터 저장소에서 실행할 수 있습니다.

데이터 스토리지 메커니즘은 다음과 같이 작동합니다.

1. 리포지토리 형식은 `REPOSITORY_NAME` 환경 변수를 통해 지정됩니다. 이 변수는 "memory", "azuretablestore" 또는 "mongodb"로 설정할 수 있습니다. *settings.py*의 코드 중 일부는 "memory"를 기본값으로 사용하여 이름을 검색합니다. 백업 저장소를 변경하려면 환경 변수를 설정하고 앱을 다시 시작해야 합니다.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. 그런 다음, *settings.py* 코드는 `REPOSITORY_SETTINGS` 개체를 초기화합니다. Azure 테이블 저장소 또는 Mondo DB를 사용하려는 경우 먼저 해당 데이터 저장소를 다른 위치에서 초기화한 다음, 앱에 저장소 연결 방법을 알려주는 데 필요한 환경 변수를 설정해야 합니다.

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. *views.py*에서 앱은 데이터 저장소의 이름 및 설정을 사용하여 `Repository` 개체를 초기화하는 팩터리 메서드를 호출합니다.

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` 메서드는 *models\factory.py*에 있습니다. 이 메서드는 적절한 리포지토리 모듈을 가져온 다음, `Repository` 인스턴스를 만듭니다.

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. 각 데이터 저장소에 지정된 `Repository` 클래스의 구현은 *models\azuretablestorage.py*, *models\mongodb.py* 및 *models\memory.py* 에서 찾을 수 있습니다. Azure 스토리지 구현에는 azure-storage 패키지가 사용되고, Mongo DB 구현에는 pymongo 패키지가 사용됩니다. 5-1단계에서 설명한 대로 두 패키지는 모두 프로젝트 템플릿의 *requirements.txt* 파일에 포함됩니다. 세부 정보의 탐색은 reader의 활동으로 남겨둡니다.

즉, `Repository` 클래스는 데이터 저장소의 세부 사항을 추상화하며, 앱은 런타임에 환경 변수를 사용하여 세 가지 구현 중에 사용할 구현을 선택하고 구성합니다.

다음 단계에서는 필요한 경우 프로젝트 템플릿에서 제공하는 세 가지 데이터 저장소가 아닌 다른 데이터 저장소에 대한 지원을 추가합니다.

1. *memory.py*를 새 파일에 복사하여 `Repository` 클래스의 기본 인터페이스를 사용합니다.
1. 사용 중인 데이터 저장소에 맞게 클래스의 구현을 수정합니다.
1. 추가된 데이터 저장소의 이름을 인식하고 적절한 모듈을 가져오는 다른 *사례를 추가하려면*factory.py`elif`를 수정합니다.
1. *settings.py*를 수정하여 `REPOSITORY_NAME` 환경 변수에서 다른 이름을 인식하고 이에 따라 `REPOSITORY_SETTINGS`를 초기화합니다.

### <a name="seed-the-data-store-from-samplesjson"></a>samples.json에서 데이터 저장소 시드

처음에는 선택한 데이터 저장소에 설문 조사가 없으므로 앱의 홈 페이지에 **샘플 설문 만들기** 단추와 함께 **사용할 수 있는 설문 조사가 없음**이라는 메시지가 표시됩니다. 그러나 단추를 선택하면 사용 가능한 설문 조사가 표시되도록 보기가 변경됩니다. 이러한 전환은 *templates\index.html*의 조건부 태그를 통해 이루어집니다(간결하게 하기 위해 일부 빈 줄 생략).

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

템플릿의 `polls` 변수는 `repository.get_polls`에 대한 호출에서 비롯된 것으로, 데이터 저장소가 초기화될 때까지 아무것도 반환하지 않습니다.

**샘플 설문 조사 만들기** 단추를 선택하면 /seed URL로 이동합니다. 해당 경로의 처리기는 *views.py*에 정의되어 있습니다.

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

`repository.add_sample_polls()`에 대한 호출은 선택한 데이터 저장소의 특정 `Repository` 구현 중 하나에서 종료됩니다. 각 구현에서는 `_load_samples_json`models *\_init\_\_.py\_에 있는*  메서드를 호출하여 *models\samples.json* 파일을 메모리에 로드한 다음, 해당 데이터를 반복하여 데이터 저장소에 필요한 `Poll` 및 `Choice` 개체를 만듭니다.

해당 프로세스가 완료되면 `redirect('/')` 메서드의 `seed` 문이 홈 페이지로 다시 이동합니다. 이제 `repository.get_polls`가 데이터 개체를 반환하므로 *templates\index.html*의 조건부 태그에서 설문 조사가 포함된 테이블을 렌더링합니다.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>질문: 새 설문 조사를 앱에 어떻게 추가하나요?

답변: 프로젝트 템플릿을 통해 제공된 앱에는 설문 조사를 추가하거나 편집할 수 있는 기능이 없습니다. *models\samples.json*을 수정하여 새 초기화 데이터를 만들 수는 있지만 그럴 경우 데이터 저장소를 다시 설정해야 합니다 편집 기능을 구현하려면 필요한 `Repository` 및 `Choice` 인스턴스를 만드는 메서드로 `Poll` 클래스 인터페이스를 확장한 다음, 해당 메서드를 사용하는 추가 페이지에 UI를 구현해야 합니다.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>5-4단계: 설문 조사 세부 정보 및 결과 보기 이해

정보 및 연락처 페이지에 대한 보기와 같이 “설문 조사 Flask 웹 프로젝트” 및 “설문 조사 Flask/Jade 웹 프로젝트” 템플릿에서 생성된 대부분의 보기는 이 자습서의 앞부분에서 “Flask 웹 프로젝트”(또는 "Flask/Jade 웹 프로젝트") 템플릿으로 만든 보기와 매우 유사합니다. 이전 섹션에서는 초기화 단추 또는 설문 조사 목록을 표시하기 위해 홈 페이지를 구현하는 방법도 배웠습니다.

남은 것은 개별 설문 조사의 투표(세부 사항)와 결과 보기를 검토하는 것입니다.

홈 페이지에서 설문 조사를 선택하면 앱이 URL /poll/\<key\>로 이동합니다. 여기서 *key*는 설문 조사의 고유한 식별자입니다. *views.py*에서 GET 요청의 해당 URL 라우팅을 처리하기 위해 `details` 함수가 할당되어 있는지 확인할 수 있습니다. 또한 URL 경로에서 `<key>`를 사용하면 해당 양식의 모든 경로를 동일한 함수로 매핑하고, 같은 이름의 함수에 대한 인수를 생성할 수 있습니다.

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

설문 조사(GET 요청 수)를 표시하기 위해 이 함수는 *templates\details.html*만 호출합니다. 이 함수는 설문 조사의 `choices` 배열을 반복하여 각각에 대한 라디오 단추를 만듭니다.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

**투표** 단추에 `type="submit"`이 있으므로, 이를 선택하면 `details` 함수로 한 번 더 라우팅된 동일한 URL에 대한 POST 요청이 생성됩니다. 그러나 이번에는 양식 데이터에서 선택 사항을 추출하고 /results/\<choice\>로 리디렉션합니다.

그리고 /results/\<key\> URL이 `results`views.py*의*  함수로 라우팅된 다음, 설문 조사의 `calculate_stats` 메서드를 호출하고, 렌더링을 위해 *templates\results.html*을 적용합니다.

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

*results.html* 템플릿은 해당 부분에서 설문 조사의 선택 항목을 반복하고 각각에 대한 진행률 표시줄을 생성합니다.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>다음 단계

> [!Note]
> 이 자습서를 진행하는 동안 Visual Studio 솔루션을 소스 제어에 커밋했으면 다른 커밋을 수행할 수 있습니다. 솔루션이 GitHub의 자습서 소스 코드([Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask))와 일치해야 합니다.

이제 Visual Studio에서 “빈 Flask 웹 프로젝트”, “Flask[/Jade] 웹 프로젝트” 및 “설문 조사 Flask[/Jade] 웹 프로젝트” 템플릿 전체를 살펴보았습니다. 보기, 템플릿 및 라우팅 사용과 같은 Flask의 모든 기본 사항을 배웠으며, 백업 데이터 저장소를 사용하는 방법을 알아보았습니다. 이제 필요한 모든 보기 및 모델을 사용하여 웹앱을 직접 시작할 수 있습니다.

개발 컴퓨터에서 웹앱을 실행하는 것은 고객에게 앱을 제공하기 위한 과정의 한 단계일 뿐입니다. 다음 단계에는 다음과 같은 작업이 포함될 수 있습니다.

- Azure App Service와 같은 프로덕션 서버에 웹앱을 배포합니다. [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)를 참조하세요.

- PostgreSQL, MySQL 및 SQL Server와 같은 다른 프로덕션 수준 데이터 저장소(모두 Azure에서 호스팅할 수 있음)를 사용하는 리포지토리 구현을 추가합니다. 또한 [Python용 Azure SDK](/azure/python/)를 사용하여 Cosmos DB뿐만 아니라 테이블 및 Blob과 같은 Azure 스토리지 서비스 작업을 수행할 수도 있습니다.

- Azure DevOps와 같은 서비스에서 지속적인 통합/지속적인 배포 파이프라인을 설정합니다. Azure Repos, GitHub 등을 통한 소스 제어 작업 외에도 Azure DevOps Project를 구성하여 릴리스의 사전 필수 구성 요소로 단위 테스트를 자동으로 실행하고, 프로덕션 환경에 배포하기 전에 추가 테스트를 위해 준비 서버에 배포하도록 파이프라인을 구성할 수 있습니다. 또한 Azure DevOps는 App Insights와 같은 모니터링 솔루션과 통합되며 agile 계획 도구를 사용하여 전체 주기를 닫습니다. 자세한 내용은 [Azure DevOps Projects를 사용하여 Python용 CI/CD 파이프라인 만들기](/azure/devops-project/azure-devops-project-python?view=vsts) 및 일반 [Azure DevOps 설명서](/azure/devops/?view=vsts)를 참조하세요.
