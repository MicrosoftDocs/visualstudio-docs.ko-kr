---
title: '빠른 시작: Visual Studio를 사용하여 Python 웹앱 만들기'
description: 이 빠른 시작에서 Visual Studio 및 Flask 프레임워크를 사용하여 Python에서 간단한 웹앱을 빌드합니다.
ms.date: 03/07/2019
ms.technology: vs-python
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: cbb06ac800fd21e2354b04fb2e7e46306da7ed72
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180348"
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>빠른 시작: Visual Studio를 사용하여 첫 번째 Python 웹앱 만들기

Python IDE인 Visual Studio에 대한 5~10분 분량의 소개에서는 Flask 프레임워크에 따라 간단한 Python 웹 애플리케이션을 만듭니다. Visual Studio의 기본 기능에 대해 알 수 있는 불연속 단계를 통해 프로젝트를 만듭니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다. 설치 관리자에서 **Python 개발** 워크로드를 선택하도록 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다. 설치 관리자에서 **Python 개발** 워크로드를 선택하도록 합니다.

::: moniker-end

## <a name="create-the-project"></a>프로젝트를 만듭니다.

다음 단계에서는 애플리케이션에 대한 컨테이너로 제공되는 빈 프로젝트를 만듭니다.

::: moniker range="vs-2017"
1. Visual Studio 2017을 엽니다.

2. 메뉴 모음에서 **파일 > 새로 만들기 > 프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 오른쪽 아래의 검색 필드에 "Python 웹 프로젝트"를 입력한 다음, 중간 목록에서 **웹 프로젝트**를 선택하고, 프로젝트에 "HelloPython"과 같은 이름을 지정한 다음, **확인**을 선택합니다.

    ![Python 웹 프로젝트가 선택된 새 프로젝트 대화 상자](media/quickstart-python-00-web-project.png)

    Python 프로젝트 템플릿이 표시되지 않으면 **Visual Studio 설치 관리자**를 실행하여 **추가** > **수정**을 선택하고 **Python 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

    ![Visual Studio 설치 관리자의 Python 개발 작업](../python/media/installation-python-workload.png)

4. 오른쪽 창의 **솔루션 탐색기**에 새 프로젝트가 열립니다. 프로젝트에 다른 파일이 없기 때문에 이 시점에는 프로젝트가 비어 있습니다.

    ![새로 만든 빈 프로젝트를 보여주는 솔루션 탐색기](media/quickstart-python-01-empty-project.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio 2019를 엽니다.
2. 시작 화면에서 **새 프로젝트 만들기**를 선택합니다.
3. **새 프로젝트 만들기** 대화 상자의 맨 위에 있는 검색 필드에 "Python 웹"을 입력하고 가운데 목록에서 **웹 프로젝트**를 선택한 후, **다음**을 선택합니다.

    ![Python 웹 프로젝트가 선택된 새 프로젝트 화면 만들기](media/quickstart-python-00-web-project-2019a.png)

    Python 프로젝트 템플릿이 표시되지 않으면 **Visual Studio 설치 관리자**를 실행하여 **추가** > **수정**을 선택하고 **Python 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

    ![Visual Studio 설치 관리자의 Python 개발 작업](../python/media/installation-python-workload.png)

4. 다음의 **새 프로젝트 구성** 대화 상자에서 **프로젝트 이름**에 대해 "HelloPython"을 입력하고, 위치를 지정하고, **만들기**를 선택합니다. (**솔루션 이름**이 **프로젝트 이름**과 일치하도록 자동으로 설정됩니다.)

    ![새 프로젝트 구성 대화 상자](media/quickstart-python-00-web-project-2019b.png)

5. 오른쪽 창의 **솔루션 탐색기**에 새 프로젝트가 열립니다. 프로젝트에 다른 파일이 없기 때문에 이 시점에는 프로젝트가 비어 있습니다.

    ![새로 만든 빈 프로젝트를 보여주는 솔루션 탐색기](media/quickstart-python-01-empty-project-2019.png)
::: moniker-end

**질문: Python 애플리케이션에 대한 Visual Studio에서 프로젝트를 만드는 경우의 이점은 무엇인가요?**

**대답**: 일반적으로 Python 애플리케이션은 폴더 및 파일만 사용하여 정의되지만 애플리케이션이 커질수록 이 간단한 구조는 복잡해질 수 있으며 자동 생성된 파일, 웹 애플리케이션용 JavaScript 등을 포함할 수 있습니다. Visual Studio 프로젝트는 이러한 복잡성을 관리하는 데 도움이 됩니다. 프로젝트( *.pyproj* 파일)는 프로젝트와 관련된 모든 소스 및 콘텐츠 파일을 식별하며 각 파일에 대한 빌드 정보를 포함하고 소스 제어 시스템과 통합할 정보를 유지 관리하며 애플리케이션을 논리 구성 요소로 구성하는 데 도움을 줍니다.

**질문: 솔루션 탐색기에 표시된 "솔루션"이란?**

**대답**: Visual Studio 솔루션은 하나 이상의 관련 프로젝트를 그룹으로 관리할 수 있는 컨테이너이고, 프로젝트에 특정되지 않는 구성 설정을 저장합니다. 솔루션의 프로젝트는 어떤 프로젝트(Python 앱)를 실행하면 두 번째 프로젝트(예: Python 앱에서 사용하는 C++ 확장)를 자동으로 빌드하는 방식으로 서로 참조할 수도 있습니다.

## <a name="install-the-flask-library"></a>Flask 라이브러리 설치

Python의 웹앱은 다수의 사용 가능한 Python 라이브러리 중 하나를 웹 요청 라우팅과 응답 형성과 같은 낮은 수준의 세부 사항을 처리하기 위해 거의 항상 사용합니다. 이런 용도로 Visual Studio는 웹앱에 대한 다양한 템플릿을 제공하며, 이러한 템플릿은 이 빠른 시작에서 나중에 사용됩니다.

여기에서 다음 단계를 사용하여 Visual Studio에서 이 프로젝트에 사용하는 기본 "전역 환경"에 Flask 라이브러리를 설치합니다.

::: moniker range="vs-2017"
1. 프로젝트에서 **Python 환경** 노드를 확장하여 프로젝트의 기본 환경을 확인합니다.

    ![기본 환경을 보여 주는 솔루션 탐색기](media/quickstart-python-02-default-environment.png)

2. 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 설치**를 선택합니다. 이 명령은 **패키지** 탭에 **Python 환경** 창을 엽니다.

3. 검색 필드에 "flask"를 입력하고 **pip install flask from PyPI**를 선택합니다. 관리자 권한에 대한 프롬프트가 표시되면 수락하고 Visual Studio의 **출력** 창에서 진행률을 살펴봅니다. 전역 환경에 대한 패키지 폴더가 *C:\Program Files*와 같이 보호되는 영역 내에 있는 경우 권한 상승에 대한 프롬프트가 발생합니다.

    ![pip 설치를 통해 Flask 라이브러리 설치](media/quickstart-python-03-install-package.png)
::: moniker-end
::: moniker range=">=vs-2019"
1. 프로젝트에서 **Python 환경** 노드를 확장하여 프로젝트의 기본 환경을 확인합니다.

    ![기본 환경을 보여 주는 솔루션 탐색기](media/quickstart-python-02-default-environment-2019.png)

2. 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 관리...** 를 선택합니다. 이 명령은 **패키지(PyPI)** 탭에 **Python 환경** 창을 엽니다.

3. 검색 필드에 "flask"를 입력합니다. **Flask**가 검색 상자 아래에 나타나면 이 단계를 건너뛸 수 있습니다. 그렇지 않으면 **명령 실행: pip 설치 flask**를 선택합니다. 관리자 권한에 대한 프롬프트가 표시되면 수락하고 Visual Studio의 **출력** 창에서 진행률을 살펴봅니다. 전역 환경에 대한 패키지 폴더가 *C:\Program Files*와 같이 보호되는 영역 내에 있는 경우 권한 상승에 대한 프롬프트가 발생합니다.

    ![pip 설치를 통해 Flask 라이브러리 설치](media/quickstart-python-03-install-package-2019.png)
::: moniker-end

4. 설치 후에는 **솔루션 탐색기**의 환경에 라이브러리가 표시되며 Python 코드에서 해당 라이브러리를 사용할 수 있습니다.

    ::: moniker range="vs-2017"
    ![Flask 라이브러리가 설치되어 솔루션 탐색기에 표시됨](media/quickstart-python-04-package-installed.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![Flask 라이브러리가 설치되어 솔루션 탐색기에 표시됨](media/quickstart-python-04-package-installed-2019.png)
    ::: moniker-end

> [!Note]
> 일반적으로 개발자는 전역 환경에 라이브러리를 설치하는 대신 특정 프로젝트에 대한 라이브러리를 설치하는 "가상 환경"을 만듭니다. Visual Studio 템플릿은 일반적으로 [빠른 시작 - 템플릿을 사용하여 Python 프로젝트 만들기](../python/quickstart-02-python-in-visual-studio-project-from-template.md)에 설명된 대로 이 옵션을 제공합니다.

**질문: 어디에서 사용 가능한 다른 Python 패키지에 대해 자세히 알아볼 수 있나요?**

**대답**: [Python 패키지 인덱스](https://pypi.org/)를 방문하세요.

## <a name="add-a-code-file"></a>코드 파일 추가

이제 작은 웹앱을 구현하기 위해 약간의 Python 코드를 추가할 준비가 되었습니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목**을 차례로 선택합니다.

1. 대화 상자가 나타나면 **빈 Python 파일**을 선택하고 파일의 이름을 *app.py*라고 지정하고 **추가**를 선택합니다. Visual Studio의 편집기 창에서 파일이 자동으로 열립니다.

1. 다음 코드를 복사하여 *app.py*에 붙여넣습니다.

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. **추가 > 새 항목** 대화 상자에 Python 클래스, Python 패키지, Python 단위 테스트, *web.config* 파일 등 Python 프로젝트에 추가할 수 있는 다양한 형식의 파일이 표시됩니다. 일반적으로 호출된 이러한 항목 템플릿을 사용하여 유용한 상용구 코드로 신속하게 파일을 만들 수 있습니다.

**질문: 어디에서 Flask에 대해 자세히 알아볼 수 있나요?**

**대답**: [Flask 빠른 시작](https://flask.palletsprojects.com/en/1.1.x/quickstart/#quickstart)부터는 Flask 설명서를 참조하세요.

## <a name="run-the-application"></a>애플리케이션 실행

1. **솔루션 탐색기**에서 *app.py*를 마우스 오른쪽 단추로 클릭하고 **시작 파일로 설정**을 선택합니다. 이 명령은 앱을 실행할 때 Python으로 실행할 코드 파일을 식별합니다.

    ::: moniker range="vs-2017"
    ![솔루션 탐색기에서 프로젝트에 대한 시작 파일 설정](media/quickstart-python-05-set-as-startup-file.png)
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    ![솔루션 탐색기에서 프로젝트에 대한 시작 파일 설정](media/quickstart-python-05-set-as-startup-file-2019.png)
    ::: moniker-end

2. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. 그런 다음 **디버그** 탭을 선택하고 **포트 번호** 속성을 `4449`으로 설정합니다. 이 단계를 사용하면 Visual Studio가 코드에서 `app.run` 인수와 일치하는 `localhost:4449`으로 브라우저를 시작합니다.

3. **디버그 > 디버깅하지 않고 시작**(**Ctrl**+**F5**)을 선택하여 변경 내용을 파일에 저장하고 앱을 실행합니다.

4. 명령 창에는 "*<https://localhost:4449/>에서 실행" 메시지가 표시되고, 브라우저 창이 "Hello, Python!"이라는 메시지가 표시되는 `localhost:4449`에 열려야 합니다. 명령 창에 200 상태와 함께 GET 요청도 나타납니다.

    브라우저가 자동으로 열리지 않으면 원하는 브라우저를 시작하고 `localhost:4449`으로 이동합니다.

    명령 창에 Python 대화형 셸만 보이거나 창이 화면에서 잠시 깜박이면 위의 1단계에서 *app.py*를 시작 파일로 설정했는지 확인합니다.

5. `localhost:4449/hello`로 이동하여 `/hello` 리소스에 대한 데코레이터도 작동하는지 테스트합니다. 다시 명령 창에 200 상태와 함께 GET 요청이 나타납니다. 다른 URL도 사용하여 명령 창에서 404 상태 코드가 표시되는지 확인합니다.

6. 명령 창을 닫아 앱을 중지한 다음, 브라우저 창을 닫습니다.

**질문: 디버깅 없이 시작 명령과 디버깅 시작 간의 차이점은 무엇인가요?**

**대답**: **디버깅 시작**을 사용하여 [Visual Studio 디버거](../python/debugging-python-in-visual-studio.md)의 컨텍스트에서 앱을 실행하면 중단점을 설정하고, 변수를 확인하고, 한 줄씩 코드를 실행할 수 있습니다. 앱은 디버깅할 수 있게 하는 다양한 후크 때문에 디버거에서 느리게 실행될 수 있습니다. 반면, **디버깅 없이 시작**은 디버깅 컨텍스트 없이 명령줄에서 실행한 것처럼 앱을 직접 실행하고, 자동으로 브라우저를 시작하고, 프로젝트 속성  **디버그** 탭에 지정된 URL로 이동합니다.

## <a name="next-steps"></a>다음 단계

축하합니다! Visual Studio에서 첫 번째 Python 앱을 실행했습니다. 여기서 Python IDE인 Visual Studio를 사용하는 방법에 대해 알아보았습니다

> [!div class="nextstepaction"]
> [앱을 Azure App Service에 배포](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)

이 빠른 시작에서 수행한 단계가 매우 일반적이기 때문에 자동화될 수 있다고 추측할 수 있습니다. 이러한 자동화는 Visual Studio 프로젝트 템플릿의 역할입니다. 이 문서에서 만든 것과 비슷하지만 단계가 더 적은 웹앱을 만드는 데모는 [빠른 시작 - 템플릿을 사용하여 Python 프로젝트 만들기](../python/quickstart-02-python-in-visual-studio-project-from-template.md)를 참조하세요.

대화형 창 사용, 디버깅, 데이터 시각화 및 Git 작업을 포함하여, Visual Studio의 Python에 대한 자습서를 계속 진행하려면 [자습서: Visual Studio에서 Python 시작](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)을 살펴보세요.

Visual Studio에서 제공하는 다른 기능을 탐색하려면 아래 링크를 선택합니다.

- [Visual Studio의 Python 웹앱 템플릿](../python/python-web-application-project-templates.md)에 대해 알아보기
- [Python 디버깅](../python/debugging-python-in-visual-studio.md)에 대해 자세히 알아보기
- 일반적인 [Visual Studio IDE](../get-started/visual-studio-ide.md)에 대해 자세히 알아보기
