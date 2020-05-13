---
title: Python용 Django 웹 프로젝트 템플릿
description: Visual Studio는 python으로 Django 웹 애플리케이션을 빠르게 생성할 수 있는 포괄적인 템플릿을 제공합니다.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 136c03ef11071e5d548e36e45a6a541cffce1469
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784886"
---
# <a name="django-web-project-template"></a>Django 웹 프로젝트 템플릿

[Django](https://www.djangoproject.com/)는 신속하고 안전하며 확장성 있는 웹 개발을 위해 고안된 상위 수준 Python 프레임워크입니다. Visual Studio의 Python 지원에서는 Django 기반 웹 애플리케이션의 구조를 설정하기 위한 여러 가지 프로젝트 템플릿을 제공합니다. Visual Studio에서 템플릿을 사용하려면 **파일** > **새로 만들기** > **프로젝트**를 선택하고 “Django”를 검색한 다음, **빈 Django 웹 프로젝트**, **Django 웹 프로젝트** 및 **설문 조사 Django 웹 프로젝트** 템플릿을 선택하세요. 모든 템플릿에 대한 연습은 [Django 알아보기 자습서](learn-django-in-visual-studio-step-01-project-and-solution.md)를 참조하세요.

Visual Studio는 Django 프로젝트용 전체 IntelliSense를 제공합니다.

- 템플릿에 전달된 컨텍스트 변수:

    ![컨텍스트 변수에 대한 IntelliSense](media/template-django-intellisense.png)

- 기본 제공 및 사용자 정의 항목에 대한 태깅 및 필터링

    ![태그 및 필터에 대한 IntelliSense](media/template-django-intellisense-filter.png)

- 포함된 CSS 및 JavaScript에 대한 구문 색 지정:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio에서는 Django 프로젝트에 대해 전체 [디버깅 지원](debugging-python-in-visual-studio.md)도 제공합니다.

![중단점](media/template-django-debugging.png)

*manage.py* 파일을 통해 Django 프로젝트를 관리하는 것이 일반적이며, Visual Studio는 이 가정을 따릅니다. 해당 파일을 진입점으로 사용하지 않으면 기본적으로 프로젝트 파일이 손상됩니다. 이 경우 Django 프로젝트로 표시하지 않고 [기존 파일에서 프로젝트를 다시 만들어야](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) 합니다.

## <a name="django-management-console"></a>Django 관리 콘솔

Django 관리 콘솔은 **프로젝트** 메뉴의 다양한 명령을 통해서나 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하여 액세스합니다.

- **Django Shell 열기**: 모델을 조작할 수 있는 애플리케이션 컨텍스트에서 셸을 엽니다.

    ![Django Shell 열기 명령의 결과](media/template-django-console-shell.png)

- **Django Sync DB**: `manage.py syncdb`대화형**창에서**를 실행합니다.

    ![Django Sync DB 명령의 결과](media/template-django-console-sync-db.png)

- **정적 수집**: `manage.py collectstatic --noinput`을 실행하여 `STATIC_ROOT`settings.py*의* 에 지정된 경로에 모든 정적 파일을 복사합니다.

    ![정적 수집 명령의 결과](media/template-django-console-collect-static.png)

- **유효성 검사**: `manage.py validate`를 실행하여 `INSTALLED_APPS`settings.py*의* 에 지정된 설치된 모델에서 모든 유효성 검사 오류를 보고합니다.

    ![유효성 검사 명령의 결과](media/template-django-console-validate.png)

## <a name="see-also"></a>참고 항목

- [Django 알아보기 자습서](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)
