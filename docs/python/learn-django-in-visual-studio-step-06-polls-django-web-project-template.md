---
title: Visual Studio 6단계, 설문 조사 프로젝트 템플릿에서 Django 자습서 알아보기
titleSuffix: ''
description: Visual Studio 프로젝트 컨텍스트에서 Django 기본 사항을 검토하는 연습 과정으로, 관리 사용자 지정과 같은 설문 조사 Django 웹 프로젝트 템플릿의 기능을 구체적으로 설명합니다.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1fe3db702508267e96dc79f2f789a17a7edf98b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75755581"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>6단계: 설문 조사 Django 웹 프로젝트 템플릿 사용

**이전 단계: [Django에서 사용자 인증](learn-django-in-visual-studio-step-05-django-authentication.md)**

Visual Studio의 “Django 웹 프로젝트” 템플릿을 이해했으면 이제 동일한 코드베이스를 기반으로 하고 데이터베이스 작업을 보여주는 “설문 조사 Django 웹 프로젝트”라는 세 번째 Django 템플릿을 살펴볼 수 있습니다.

이 단계에서는 다음 방법을 학습합니다.

> [!div class="checklist"]
> - 템플릿에서 프로젝트를 만들고 데이터베이스 초기화(6-1단계)
> - 데이터 모델 이해(6-2단계)
> - 마이그레이션 적용(6-3단계)
> - 프로젝트 템플릿으로 만든 보기 및 페이지 템플릿 이해(6-4단계)
> - 사용자 지정 관리 인터페이스 만들기(6-5단계)

이 템플릿을 사용하여 만든 프로젝트는 Django 문서의 [Writing your first Django app](https://docs.djangoproject.com/en/2.0/intro/tutorial01/)(첫 번째 Django 앱 작성) 자습서를 수행하여 만든 프로젝트와 유사합니다. 웹앱은 설문 조사를 관리할 수 있는 사용자 지정 관리 인터페이스와 사람들이 설문 조사를 보고 투표할 수 있는 공용 사이트로 구성됩니다. 이 앱은 “Django 웹 프로젝트” 템플릿과 동일한 인증 시스템을 사용하며 다음 섹션에 설명된 대로 Django 모델을 구현하여 데이터베이스를 더 많이 활용합니다.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>6-1단계: 프로젝트를 만들고 데이터베이스 초기화

1. Visual Studio에서 **솔루션 탐색기**로 이동하여 이 자습서의 앞부분에서 만든 **LearningDjango** 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 새 솔루션을 사용하려는 경우에는 **파일** > **새로 만들기** > **프로젝트**를 대신 선택합니다.

1. 새 프로젝트 대화 상자에서 **설문 조사 Django 웹 프로젝트** 템플릿을 검색하여 선택하고, 프로젝트의 이름을 "DjangoPolls"로 지정하고, **확인**을 선택합니다.

1. Visual Studio의 다른 프로젝트 템플릿과 마찬가지로 "설문 조사 Django 웹 프로젝트" 템플릿에는 *requirements.txt* 파일이 포함되어 있으므로 Visual Studio에서 해당 종속성을 설치할 위치를 묻습니다. **가상 환경에 설치** 옵션을 선택하고 **가상 환경 추가** 대화 상자에서 **만들기**를 선택하여 기본값을 그대로 사용합니다.

1. Python에서 가상 환경 설정이 완료되면 표시된 *readme.html*의 지침에 따라 데이터베이스를 초기화하고 Django 슈퍼 사용자(즉, 관리자)를 만듭니다. 먼저 **솔루션 탐색기**에서 **DjangoPolls** 프로젝트를 마우스 오른쪽 단추로 클릭하고, **Python** > **Django 마이그레이션** 명령을 선택한 다음, 프로젝트를 다시 마우스 오른쪽 단추로 클릭하고, **Python** > **Django 슈퍼 사용자 만들기** 명령을 선택하고, 프롬프트에 따릅니다. 슈퍼 사용자를 먼저 만들려고 하면 데이터베이스가 초기화되지 않았기 때문에 오류가 표시됩니다.

1. **솔루션 탐색기**에서 해당 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택하여 **DjangoPolls** 프로젝트가 Visual Studio 솔루션의 기본값이 되도록 설정합니다. 굵게 표시된 시작 프로젝트는 디버거를 시작할 때 실행됩니다.

1. **디버그** > **디버깅 시작**(**F5**)을 선택하거나 도구 모음의 **웹 서버** 단추를 사용하여 서버를 실행합니다.

    ![Visual Studio의 웹 서버 실행 도구 모음 단추](media/django/run-web-server-toolbar-button.png)

1. 템플릿으로 만든 앱에는 홈, 정보, 연락처라는 세 개의 페이지가 있으며, 맨 위의 탐색 모음을 사용하여 페이지 간에 이동할 수 있습니다. 1-2분 동안 앱의 다른 부분을 살펴보세요. 정보 및 연락처 페이지는 “Django 웹 프로젝트”와 매우 유사하므로 더 자세히 설명하지 않습니다.

    ![설문 조사 Django 웹 프로젝트 앱의 전체 브라우저 보기](media/django/step06-full-app-view.png)

1. 또한 탐색 모음에서 **관리** 링크를 선택하면 인증된 관리자에게만 관리 인터페이스에 대한 권한이 부여되었음을 보여주는 로그인 화면이 표시됩니다. 슈퍼 사용자 자격 증명을 사용하면 이 프로젝트 템플릿을 사용할 때 기본적으로 사용되는 “/admin” 페이지로 라우팅됩니다.

    ![설문 조사 Django 웹 프로젝트 앱의 관리 보기](media/django/step06-polls-administrative-interface.png)

1. 다음 섹션을 위해 앱이 계속 실행되도록 할 수 있습니다.

    앱을 중지하고 [변경 내용을 소스 제어에 커밋](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)하려면 먼저 **팀 탐색기**에서 **변경 내용** 페이지를 열고, 가상 환경에 대한 폴더(**env**)를 마우스 오른쪽 단추로 클릭하고, **이 로컬 항목 무시**를 선택합니다.

### <a name="examine-the-project-contents"></a>프로젝트 콘텐츠 검사

앞에서 설명한 대로 “설문 조사 Django 웹 프로젝트” 템플릿에서 만든 프로젝트의 많은 부분이 Visual Studio의 다른 프로젝트 템플릿을 살펴본 경우처럼 익숙해야 합니다. 이 문서의 추가 단계에서는 보다 중요한 변경 사항 및 추가 사항 즉, 데이터 모델 및 추가 보기에 대해 간략하게 설명합니다.

### <a name="question-what-does-the-django-migrate-command-do"></a>질문: Django Migrate(Django 마이그레이션) 명령의 기능은 무엇인가요?

대답: **Django Migrate**(Django 마이그레이션) 명령은 특별히 `manage.py migrate` 명령을 실행하여 이전에 실행되지 않은 *app/migrations* 폴더의 스크립트를 실행합니다. 이 경우 명령은 해당 폴더에서 *0001_initial.py* 스크립트를 실행하여 데이터베이스에서 필요한 스키마를 설정합니다.

마이그레이션 스크립트 자체는 `manage.py makemigrations` 명령으로 작성되며, 앱의 *models.py* 파일을 검사하고 이를 데이터베이스의 현재 상태와 비교한 다음, 현재 모델과 일치하도록 데이터베이스 스키마를 마이그레이션하는 데 필요한 스크립트를 생성합니다. Django의 이 기능은 시간에 따라 모델을 업데이트하고 수정할 때 매우 강력합니다. 마이그레이션을 생성하고 실행하면 모델과 데이터베이스를 거의 문제 없이 동기화된 상태로 유지할 수 있습니다.

이 문서의 뒷부분에 나오는 6-3단계에서 마이그레이션 작업을 수행합니다.

## <a name="step-6-2-understand-data-models"></a>6-2단계: 데이터 모델 이해

Poll 및 Choice라는 앱에 대한 모델은 *app/models.py*에 정의되어 있습니다. 각각은 `django.db.models.Model`에서 파생되고 `CharField` 및 `IntegerField` 같은 `models` 클래스의 메서드를 사용하여 데이터베이스 열에 매핑되는 모델의 필드를 정의하는 Python 클래스입니다.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

여기서 볼 수 있듯이 Poll은 `text` 필드에서 설명을 유지 관리하고 `pub_date`에서 게시 날짜를 유지 관리합니다. 이러한 필드만 Poll과 관련해서 데이터베이스에 있고 `total_votes` 필드는 런타임에 계산됩니다.

Choice는 `poll` 필드를 통해 Poll과 관련되며, `text`에 설명을 포함하고, `votes`에서 해당 선택 사항의 개수를 유지 관리합니다. `votes_percentage` 필드는 런타임에 계산되며 데이터베이스에는 없습니다.

전체 필드 형식 목록은 `CharField`(제한된 텍스트) `TextField`(무제한 텍스트), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey` 및 `ManyToMany`입니다. 각 필드는 `max_length`와 같은 몇 가지 특성을 사용합니다. `blank=True` 특성은 필드가 선택 사항임을 의미하고, `null=true`는 값이 선택 사항임을 의미합니다. 값을 데이터 값/표시 값 튜플 배열의 값으로 제한하는 `choices` 특성도 있습니다. Django 설명서의 [Model field reference](https://docs.djangoproject.com/en/2.0/ref/models/fields/)(모델 필드 참조)를 참조하세요.

프로젝트에서 [SQLite 브라우저](https://sqlitebrowser.org/)와 같은 도구를 사용하여 *db.sqlite3* 파일을 검사하면 데이터베이스에 저장된 내용을 정확하게 확인할 수 있습니다. 데이터베이스에서 Choice 모델의 `poll` 같은 외래 키 필드가 `poll_id`로 저장되어 있음을 확인할 수 있으며, Django는 자동으로 매핑을 처리합니다.

일반적으로 Django에서 데이터베이스 작업은 Django가 사용자 대신 기본 데이터베이스를 관리할 수 있도록 모델을 통해서만 작업한다는 의미입니다.

### <a name="seed-the-database-from-samplesjson"></a>samples.json에서 데이터베이스 시드

처음에는 데이터베이스에 설문 조사가 없습니다. "/admin" URL에서 관리 인터페이스를 사용하여 수동으로 설문 조사를 추가할 수 있으며, 실행 중인 사이트에서 "/seed" 페이지를 방문하여 앱의 *samples.json* 파일에 정의된 설문 조사로 데이터베이스 시드를 추가할 수도 있습니다.

Django 프로젝트의 *urls.py* has an added URL pattern, 에 추가된 URL 패턴인 `url(r'^seed$', app.views.seed, name='seed'),`가 있습니다. *app/views.py*의 `seed` 보기는 *samples.json* 파일을 로드하고 필요한 모델 개체를 만듭니다. 그러면 Django에서 일치하는 레코드를 기본 데이터베이스에 자동으로 만듭니다.

`@login_required` 데코레이터를 사용하여 보기에 대한 권한 수준을 표시합니다.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

결과를 확인하려면 먼저 앱을 실행하여 설문 조사가 아직 없음을 확인합니다. 그런 다음, “/seed” URL을 방문하고 앱이 홈페이지로 돌아가면 설문 조사를 사용할 수 있게 된 것을 확인할 수 있습니다. 다시 [SQLite 브라우저](https://sqlitebrowser.org/) 같은 도구를 사용하여 원시 *db.sqlite3* 파일을 원하는 대로 검사하세요.

![시드된 데이터베이스가 있는 설문 조사 Django 웹 프로젝트 앱](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>질문: Django 관리 유틸리티를 사용하여 데이터베이스를 초기화할 수 있나요?

대답: 예, [django-admin loaddata 명령](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata)을 사용하여 앱의 시딩 페이지와 동일한 작업을 수행할 수 있습니다. 전체 웹앱에서 작업할 경우 두 가지 방법을 조합하여 사용할 수 있습니다. 즉, 명령줄에서 데이터베이스를 초기화한 다음, 하드 코드된 파일을 사용하지 않고 다른 모든 임의 JSON을 전송할 수 있는 API로 시드 페이지를 변환할 수 있습니다.

## <a name="step-6-3-use-migrations"></a>6-3단계: 마이그레이션 사용

프로젝트를 만든 후에 Visual Studio의 상황에 맞는 메뉴를 사용하여 `manage.py makemigrations` 명령을 실행했으면 Django에서 *app/migrations/0001_initial.py* 파일을 만들었습니다. 이 파일에는 초기 데이터베이스 테이블을 만드는 스크립트가 포함되어 있습니다.

시간에 따라 모델을 변경해야 하므로 Django에서는 모델을 사용하여 기본 데이터베이스 스키마를 최신 상태로 유지하는 것이 간단합니다. 일반적인 워크플로는 다음과 같습니다.

1. *models.py* 파일에서 모델을 변경합니다.
1. Visual Studio의 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Python** > **Django Make Migrations**(Django 마이그레이션 만들기) 명령을 선택합니다. 앞에서 설명한 대로 이 명령은 *app/migrations*에서 스크립트를 생성하여 데이터베이스를 현재 상태에서 새 상태로 마이그레이션합니다.
1. 실제 데이터베이스에 스크립트를 적용하려면 프로젝트를 다시 마우스 오른쪽 단추로 클릭하고 **Python** > **Django Migrate**(Django 마이그레이션)를 선택합니다.

Django는 지정된 데이터베이스에 적용된 마이그레이션을 추적하므로 마이그레이션 명령을 실행하면 Django는 필요한 모든 마이그레이션을 적용합니다. 예를 들어 비어 있는 새 데이터베이스를 만드는 경우 마이그레이션 명령을 실행하면 모든 마이그레이션 스크립트를 적용하여 현재 모델을 사용하는 최신 상태가 됩니다. 마찬가지로 여러 모델을 변경하고 개발 컴퓨터에서 마이그레이션을 생성하면 프로덕션 서버에서 마이그레이션 명령을 실행하여 프로덕션 데이터베이스에 누적 마이그레이션을 적용할 수 있습니다. 또한 Django는 프로덕션 데이터베이스의 마지막 마이그레이션 이후 생성된 마이그레이션 스크립트만 적용합니다.

모델 변경 결과를 확인하려면 다음 단계를 수행하세요.

1. 선택적 `author` 필드를 추가하는 `pub_date` 필드 다음에 다음 줄을 추가하여 *app/models.py*의 Poll 모델에 선택적 작성자 필드를 추가합니다.

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. 파일을 저장한 다음, **솔루션 탐색기**에서 **DjangoPolls** 프로젝트를 마우스 오른쪽 단추로 클릭하고, **Python** > **Django 마이그레이션 만들기** 명령을 선택합니다.
1. **프로젝트** > **모든 파일 표시** 명령을 선택하여 **마이그레이션** 폴더에서 이름이 **002_auto_** 로 시작하는 새로 생성된 스크립트를 확인합니다. 해당 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에 포함**을 선택합니다. 그런 다음, **프로젝트** > **모든 파일 표시**를 다시 선택하여 원래 보기를 복원할 수 있습니다. 이 단계에 대한 자세한 내용은 아래의 두 번째 질문을 참조하세요.
1. 원하는 경우 해당 파일을 열어 Django 스크립트가 이전 모델 상태에서 새 상태로 어떻게 변경되었는지 검사합니다.
1. Visual Studio 프로젝트를 다시 마우스 오른쪽 단추로 클릭하고 **Python** > **Django Migrate**(Django 마이그레이션)를 선택하여 데이터베이스에 변경 내용을 적용합니다.
1. 원하는 경우 적절한 뷰어에서 데이터베이스를 열어 변경 내용을 확인합니다.

전체적으로 Django의 마이그레이션 기능은 데이터베이스 스키마를 수동으로 관리할 필요가 없음을 의미합니다. 모델을 변경하고 마이그레이션 스크립트를 생성한 후 마이그레이션 명령으로 적용하면 됩니다.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>질문: 모델을 변경한 후 마이그레이션 명령을 실행하는 것을 잊으면 어떻게 되나요?

대답: 모델이 데이터베이스의 내용과 일치하지 않을 경우 Django가 런타임에 실패하고 관련 예외가 발생합니다. 예를 들어 이전 섹션에 표시된 모델 변경 내용을 마이그레이션하지 않을 경우 **no such column: app_poll.author** 오류가 표시됩니다.

![모델 변경 내용이 마이그레이션되지 않은 경우 표시되는 오류](media/django/step06-exception-when-forgetting-to-migrate.png)을 선택합니다.

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>질문: Django Make Migrations(Django 마이그레이션 만들기)를 실행한 후 솔루션 탐색기에 새로 생성된 스크립트가 표시되지 않는 이유는 무엇인가요?

대답: 새로 생성된 스크립트는 *app/migrations* 폴더에 있고 **Django 마이그레이션** 명령을 실행하면 적용되지만 Visual Studio 프로젝트에 추가되지 않았기 때문에 **솔루션 탐색기**에 자동으로 표시되지는 않습니다. 이러한 스크립트를 표시하려면 먼저 **프로젝트** > **모든 파일 표시** 메뉴 명령이나 아래 이미지에서 윤곽선이 있는 도구 모음 단추를 선택합니다. 이 명령을 선택하면 **솔루션 탐색기**에서 프로젝트 자체에 추가되지 않는 항목에 점선 윤곽선 아이콘을 사용하여 프로젝트 폴더의 모든 파일을 표시합니다. 추가할 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트에 포함**을 선택합니다. 그러면 다음 커밋 시 소스 제어에도 포함됩니다.

![솔루션 탐색기의 프로젝트에 포함 명령](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>질문: 마이그레이션 명령을 실행하기 전에 적용되는 마이그레이션을 확인할 수 있나요?

대답: 예, [django-admin showmigrations 명령](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations)을 사용하세요.

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>6-4단계: 프로젝트 템플릿으로 만든 보기 및 페이지 템플릿 이해

정보 및 연락처 페이지에 대한 보기와 같이 “설문 조사 Django 웹 프로젝트” 템플릿에서 생성된 대부분의 보기는 이 자습서의 앞부분에서 “Django 웹 프로젝트” 템플릿으로 만든 보기와 매우 유사합니다. 설문 조사 앱에서 달라진 점은 해당 홈페이지에서 모델을 사용하여 투표 및 설문 조사 결과 보기에 대한 페이지가 여러 개 추가되었다는 점입니다.

먼저 *urls.py* 파일에 있는 Django 프로젝트의 `urlpatterns` 배열에서 첫 줄은 앱 보기로의 단순한 라우팅 이상입니다. 대신 앱 자체의 *urls.py* 파일을 끌어옵니다.

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*app/urls.py* 파일에는 몇 가지 흥미로운 라우팅 코드(설명 주석 추가됨)가 포함되어 있습니다.

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

여기에 사용된 보다 복잡한 정규식에 익숙하지 않은 경우 식을 [regex101.com](https://regex101.com/)에 붙여넣어 일반 언어로 된 설명을 볼 수 있습니다. (이때 식 앞에 백슬래시(`\`)를 추가하여 슬래시(`/`)를 이스케이프해야 합니다. Python에서는 문자열에서 “원시”를 의미하는 `r` 접두사로 인해 이스케이프가 필요하지 않습니다.)

Django에서 `?P<name>pattern` 구문은 `name`이라는 그룹을 만들어 표시되는 순서대로 보기에 대한 인수로 전달합니다. 위의 코드에서 `PollsDetailView` 및 `PollsResultsView`는 `pk`라는 인수를 받고 `app.views.vote`는 `poll_id`라는 인수를 받습니다.

또한 대부분의 보기가 *app/views.py*의 보기 함수에 대한 직접 참조가 아님을 확인할 수 있습니다. 대신 대부분이 `django.views.generic.ListView` 또는 `django.views.generic.DetailView`에서 파생되는 동일한 파일의 클래스를 참조합니다. 기본 클래스는 템플릿을 식별하기 위해 `template_name` 인수를 사용하는 `as_view` 메서드를 제공합니다. 또한 홈페이지에 사용되는 `ListView` 기본 클래스에는 데이터를 포함하는 `queryset` 속성과 템플릿에서 데이터를 참조하는 데 사용되는 변수 이름(이 경우 `latest_poll_list`)이 있는 `context_object_name` 속성이 필요합니다.

이제 홈페이지의 `PollListView`를 검사할 수 있습니다. 이 작업은 *app/views.py*에 다음과 같이 정의되어 있습니다.

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

여기서 수행되는 모든 작업은 보기가 작동하는 모델(Poll)을 식별하는 것이며, `get_context_data` 메서드를 재정의하여 `title` 및 `year` 값을 컨텍스트에 추가합니다.

템플릿의 핵심(*templates/app/index.html*)은 다음과 같습니다.

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

간단히 말해서, 템플릿은 `latest_poll_list`에 있는 Poll 개체 목록을 수신한 다음, 설문 조사의 `text` 값을 사용하여 각 설문 조사에 대한 링크가 포함된 테이블 행을 만들기 위해 해당 목록을 반복합니다. `{% url %}` 태그에서 "app:detail"은 `poll.id`를 인수로 사용하여 “detail”이라는 *app/urls.py*의 URL 패턴을 참조합니다. 그 결과로 Django는 적절한 패턴을 사용하여 URL을 만들고 해당 URL을 링크에 사용합니다. 이에 따라 향후에 개발자나 IT 전문가가 해당 URL 패턴을 변경할 수 있으며 생성된 링크는 자동으로 업데이트되어 일치됩니다.

여기에 표시되지 않은 *app/views.py*의 `PollDetailView` 및 `PollResultsView` 클래스는 `DetailView`에서 파생된다는 점을 제외하면 `PollListView`와 거의 동일합니다. 각각의 *app/templates/details.html* 및 *app/templates/results.html* 템플릿은 다양한 HTML 컨트롤 내에 모델의 적절한 필드를 배치합니다. *details.html*에서 한 가지 고유한 부분은 설문 조사의 선택 사항이 제출될 때 /vote URL에 대해 POST를 수행하는 HTML 양식 내에 포함된다는 점입니다. 앞에서 살펴본 대로 URL 패턴은 `app.views.vote`로 라우팅되며 다음과 같이 구현됩니다. 이 보기에 대한 라우팅에서 사용되는 정규식에서 명명된 그룹인 `poll_id` 인수를 확인하세요.

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

이때 보기에는 다른 페이지처럼 해당되는 고유한 템플릿이 없습니다. 대신 선택한 설문 조사의 유효성을 검사하여 설문 조사가 없는 경우 404를 표시합니다(누군가가 “vote/1a2b3c” 같은 URL을 입력하는 경우만). 그런 다음, 투표한 선택 사항이 설문 조사에 유효한지 확인합니다. 유효하지 않으면 `except` 블록에서 세부 정보 페이지를 다시 렌더링하여 오류 메시지를 표시합니다. 선택 사항이 유효하면 보기에서 투표수를 기록하고 결과 페이지로 리디렉션합니다.

## <a name="step-6-5-create-a-custom-administration-interface"></a>6-5단계: 사용자 지정 관리 인터페이스 만들기

“설문 조사 Django 웹 프로젝트” 템플릿의 마지막 부분은 이 문서의 6-1단계에서 설명한 대로 기본 Django 관리 인터페이스에 대한 사용자 지정 확장입니다. 기본 인터페이스는 사용자 및 그룹 관리를 위해 제공될 뿐입니다. 설문 조사 프로젝트 템플릿은 설문 조사를 관리할 수 있는 기능도 추가합니다.

먼저 Django 프로젝트의 *urls.py*에 있는 URL 패턴에는 기본적으로 `url(r'^admin/', include(admin.site.urls)),`가 포함되어 있으며, "admin/doc" 패턴도 주석 처리되어 포함됩니다.

앱에는 *admin.py* 파일이 포함되어 있으며, *settings.py*의 `INSTALLED_APPS` 배열에 `django.contrib.admin`이 포함되어 있어서 관리 인터페이스를 방문하면 Django에서 이 파일을 자동으로 실행합니다. 프로젝트 템플릿에서 제공하는 해당 파일의 코드는 다음과 같습니다.

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

여기서 `PollAdmin` 클래스는 `django.contrib.admin.ModelAdmin`에서 파생되며, 관리하는 많은 필드를 `Poll` 모델의 이름을 사용하여 사용자 지정합니다. 이러한 필드는 Django 설명서의 [ModelAdmin options](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options)(ModelAdmin 옵션)에 설명되어 있습니다.

`admin.site.register` 호출은 해당 클래스를 모델(`Poll`)에 연결하고 관리 인터페이스에 포함시킵니다. 전체적 결과는 아래와 같습니다.

![설문 조사 Django 웹 프로젝트 앱의 관리 보기](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>다음 단계

> [!Note]
> 이 자습서를 진행하는 동안 Visual Studio 솔루션을 소스 제어에 커밋했으면 다른 커밋을 수행할 수 있습니다. 솔루션은 GitHub의 자습서 소스 코드와 일치해야 합니다. [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

이제 Visual Studio에서 “빈 Django 웹 프로젝트”, “Django 웹 프로젝트” 및 “설문 조사 Django 웹 프로젝트” 템플릿 전체를 살펴보았습니다. 보기 및 템플릿 사용과 같은 Django의 모든 기본 사항을 학습했으며 라우팅, 인증 및 데이터베이스 모델 사용을 검토했습니다. 이제 필요한 모든 보기 및 모델을 사용하여 웹앱을 직접 작성할 수 있어야 합니다.

개발 컴퓨터에서 웹앱을 실행하는 것은 고객에게 앱을 제공하기 위한 과정의 한 단계일 뿐입니다. 다음 단계에는 다음과 같은 작업이 포함될 수 있습니다.

- Azure App Service와 같은 프로덕션 서버에 웹앱을 배포합니다. [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)를 참조하세요.

- *templates/404.html*이라는 템플릿을 만들어 404페이지를 사용자 지정합니다. 이미 있는 경우 Django는 기본 템플릿 대신 이 템플릿을 사용합니다. 자세한 내용은 Django 설명서의 [Error views](https://docs.djangoproject.com/en/2.0/ref/views/#error-views)(오류 보기)를 참조하세요.

- *tests.py*에 단위 테스트를 작성합니다. Visual Studio 프로젝트 템플릿은 이러한 테스트에 대한 시작점을 제공하며, 자세한 내용은 Django 설명서의 [첫 번째 Django 앱 작성, 5부 - 테스트](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) 및 [Django의 테스트](https://docs.djangoproject.com/en/2.0/topics/testing/)에서 확인할 수 있습니다.

- 앱을 SQLite에서 PostgreSQL, MySQL 및 SQL Server와 같은 프로덕션 수준 데이터 저장소(모두 Azure에서 호스트할 수 있음)로 변경합니다. [When to use SQLite](https://www.sqlite.org/whentouse.html)(SQLite를 사용하는 경우)(sqlite.org)에 설명된 대로 SQLite는 일별 방문 횟수가 100K보다 적은, 트래픽이 낮거나 중간 정도인 사이트에서 제대로 작동하지만 더 큰 볼륨에는 권장되지 않습니다. 또한 단일 컴퓨터로 제한되므로 부하 분산 및 지역에서 복제와 같은 모든 다중 서버 시나리오에서는 사용할 수 없습니다. Django의 다른 데이터베이스 지원에 대한 자세한 내용은 [데이터베이스 설치](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup)를 참조하세요. 또한 [Python용 Azure SDK](/azure/python/)를 사용하여 테이블 및 Blob과 같은 Azure 스토리지 서비스 작업을 수행할 수도 있습니다.

- Azure DevOps와 같은 서비스에서 지속적인 통합/지속적인 배포 파이프라인을 설정합니다. Azure Repos, GitHub 등을 통한 소스 제어 작업 외에도 Azure DevOps Project를 구성하여 릴리스의 사전 필수 구성 요소로 단위 테스트를 자동으로 실행하고, 프로덕션 환경에 배포하기 전에 추가 테스트를 위해 준비 서버에 배포하도록 파이프라인을 구성할 수 있습니다. 또한 Azure DevOps는 App Insights와 같은 모니터링 솔루션과 통합되며 agile 계획 도구를 사용하여 전체 주기를 닫습니다. 자세한 내용은 [Azure DevOps 프로젝트로 Python용 CI/CD 파이프라인 만들기](/azure/devops-project/azure-devops-project-python?view=vsts) 및 일반적인 [Azure DevOps 설명서](/azure/devops/?view=vsts)도 참조하세요.
