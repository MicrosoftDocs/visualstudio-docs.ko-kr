---
title: Visual Studio 자습서 1단계의 Python 프로젝트 만들기
titleSuffix: ''
description: 필수 구성 요소 및 새 Python 프로젝트 만들기를 포함하여 Visual Studio의 Python 기능에 대한 핵심 연습의 개요 및 1단계입니다.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ed4fdbfe7090a66d955461f2c3a394f6fb661c5a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430746"
---
# <a name="tutorial-work-with-python-in-visual-studio"></a>자습서: Visual Studio에서 Python 작업

Python은 안정적이고 유연하며 배우기 쉬울뿐만 아니라 모든 운영 체제에서 무료로 사용할 수 있으며, 유용한 개발자 커뮤니티와 다양한 무료 라이브러리에서 지원되며 널리 사용되는 프로그래밍 언어입니다. 언어는 웹 애플리케이션, 웹 서비스, 데스크톱 앱, 스크립팅 및 과학적 컴퓨팅 등 모든 방식의 개발을 지원하며 대학, 과학자, 아마추어 개발자 및 전문 개발자 등 많은 분야에 사용됩니다.

Visual Studio는 Python에 대한 고급 언어 지원을 제공합니다. 이 자습서가 다음 단계를 안내합니다.

- [0단계: 설치](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [1단계: Python 프로젝트 만들기(이 문서)](#step-1-create-a-new-python-project)
- [2단계: 작업에서 Visual Studio IntelliSense를 표시하도록 코드 작성 및 실행](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [3단계: 대화형 REPL 창에서 더 많은 코드 만들기](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [4단계: Visual Studio 디버거에서 완성된 프로그램 실행](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [5단계: 패키지 설치 및 Python 환경 관리](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [6단계: Git 작업](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

[!INCLUDE[tutorial-prereqs](includes/tutorial-prereqs.md)]

## <a name="step-1-create-a-new-python-project"></a>1단계: 새 Python 프로젝트 만들기

*프로젝트*는 Visual Studio에서 소스 코드, 리소스, 구성 등을 포함하여 단일 애플리케이션을 생성하기 위해 함께 제공되는 모든 파일을 관리하는 방법입니다. 프로젝트는 여러 프로젝트에서 공유되는 외부 리소스뿐만 아니라 모든 프로젝트의 파일 간의 관계를 공식화하고 유지합니다. 따라서 프로젝트를 사용하면 임시 폴더, 스크립트, 텍스트 파일에서 심지어 사용자의 마음대로 프로젝트의 관계를 관리하는 것보다 훨씬 더 쉽게 애플리케이션을 확장하고 성장시킬 수 있습니다.

이 자습서에서 단일 빈 코드 파일을 포함하는 간단한 프로젝트부터 시작합니다.

1. Visual Studio에서 **파일** > **새로 만들기** > **프로젝트**(**Ctrl**+**Shift**+**N**)를 선택하면 **새 프로젝트** 대화 상자가 표시됩니다. 여기에서 다른 언어에서 템플릿을 찾아본 다음 프로젝트에 대한 템플릿을 선택하고 Visual Studio에서 파일을 삽입하는 위치를 지정합니다.

1. Python 템플릿을 보려면 왼쪽의 **설치됨** > **Python**을 선택하거나 “Python”을 검색합니다. 검색을 사용하는 것은 언어 트리에서 해당 위치를 기억할 수 없는 경우 템플릿을 찾을 수 있는 좋은 방법입니다.

    ![Python 프로젝트가 표시된 새 프로젝트 대화 상자](media/vs-getting-started-python-01-new-project.png)

    Visual Studio에서 Python을 지원하는 방법에는 Bottle, Flask 및 Django 프레임워크를 사용하는 웹 애플리케이션을 비롯한 많은 프로젝트 템플릿이 포함되어 있습니다. 그러나 이 연습에서는 빈 프로젝트로 시작하겠습니다.

1. **Python 애플리케이션** 템플릿을 선택하고, 프로젝트 이름을 지정하고, **확인**을 선택합니다.

1. 몇 분 후에 Visual Studio는 **솔루션 탐색기** 창(1)에 프로젝트 구조를 표시합니다. 기본 코드 파일은 편집기(2)에 열립니다. 디스크에서의 정확한 위치를 포함하여 **솔루션 탐색기**에서 선택한 모든 항목에 대한 추가 정보를 보여 주는 **속성** 창(3)도 표시됩니다.

    ![Python 프로젝트와 솔루션 탐색기](media/vs-getting-started-python-02-windows.png)

1. 잠시 시간을 내어, 프로젝트의 파일 및 폴더를 검색하는 데 사용되는 **솔루션 탐색기**를 살펴봅니다.

    ![다양한 기능을 표시하도록 확장된 솔루션 탐색기](media/vs-getting-started-python-03-solution-explorer.png)

    (1) 굵게 강조 표시된 것은 **새 프로젝트** 대화 상자에서 지정한 이름을 사용하는 프로젝트입니다. 디스크에서 이 프로젝트는 프로젝트 폴더의 *.pyproj* 파일로 표시됩니다.

    (2) 최상위 수준은 기본적으로 프로젝트와 동일한 이름이 있는 *솔루션*입니다. 디스크에서 *.sln* 파일로 표시되는 솔루션은 하나 이상의 관련된 프로젝트에 대한 컨테이너입니다. 예를 들어 Python 애플리케이션에 대한 C++ 확장명을 작성하는 경우 해당 C++ 프로젝트는 동일한 솔루션 내에 있을 수 있습니다. 솔루션은 전용 테스트 프로그램에 대한 프로세스와 함께 웹 서비스에 대한 프로젝트를 포함할 수도 있습니다.

    (3) 프로젝트 아래에 소스 파일이 표시됩니다. 이 경우 단일 *.py* 파일만 표시됩니다. 파일을 선택하면 해당 속성이 **속성** 창에 표시됩니다. 파일을 두 번 클릭하면 해당 파일에 대한 적절한 방식으로 열립니다.

    (4) 또한 프로젝트 아래는 **Python 환경** 노드입니다. 확장하면 사용할 수 있는 Python 인터프리터가 표시됩니다. 인터프리터 노드를 확장하여 해당 환경(5)에 설치되는 라이브러리를 봅니다.

    **솔루션 탐색기**에서 노드 또는 항목을 마우스 오른쪽 단추로 클릭하여 해당 명령의 메뉴에 액세스합니다. 예를 들어 **Rename** 명령을 통해 프로젝트와 솔루션을 포함하여 노드 또는 항목의 이름을 변경할 수 있습니다.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [코드 작성 및 실행](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Visual Studio의 Python 프로젝트](managing-python-projects-in-visual-studio.md).
- [python.org의 Python 언어에 대한 자세한 정보](https://www.python.org)
- [초보자용 Python](https://www.python.org/about/gettingstarted/)(python.org)
