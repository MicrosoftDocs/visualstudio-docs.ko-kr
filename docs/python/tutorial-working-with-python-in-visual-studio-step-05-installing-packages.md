---
title: Visual Studio 자습서 5단계에서 Python 패키지 설치
titleSuffix: ''
description: Visual Studio의 Python 기능에 대한 핵심 연습의 5단계로, Python 환경에서 패키지를 관리하는 Visual Studio의 기능을 보여줍니다.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372931"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>5단계: Python 환경에서 패키지 설치

**이전 단계: [디버거에서 코드 실행](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Python 개발자 커뮤니티에서는 사용자 소유의 프로젝트에 통합할 수 있는 유용한 패키지가 무수히 만들어졌습니다. Visual Studio는 Python 환경에서 패키지를 관리하기 위한 UI를 제공합니다.

## <a name="view-environments"></a>환경 보기

1. **보기** > **다른 창** > **Python 환경** 메뉴 명령을 선택합니다. **Python 환경** 창이 **솔루션 탐색기**에 대한 피어로 열리고 사용할 수 있는 다양한 환경을 표시합니다. 목록에는 Visual Studio 설치 관리자를 사용하여 설치한 환경과 별도로 설치한 환경이 모두 표시됩니다. 여기에는 글로벌 환경, 가상 환경 및 Conda 환경이 포함됩니다. 굵게 표시된 환경은 새 프로젝트에 사용되는 기본 환경입니다. 환경 사용에 대한 자세한 내용은 [Visual Studio에서 Python 환경을 만들고 관리하는 방법](managing-python-environments-in-visual-studio.md)을 참조하세요.

   ![Python 환경 창](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > 솔루션 탐색기 창을 클릭하고 Ctrl+K, Ctrl+’ 바로 가기 키를 사용하여 Python 환경 창을 열 수도 있습니다. 바로 가기가 작동하지 않고 메뉴에서 Python 환경 창을 찾을 수 없는 경우 Python 워크로드를 설치하지 않았을 수 있습니다. Python을 설치하는 방법에 대한 지침은 [Visual Studio에서 Python 지원을 설치하는 방법](installing-python-support-in-visual-studio.md)을 참조하세요.

2. 환경의 **개요** 탭에서는 환경의 설치 폴더 및 인터프리터와 함께 해당 환경에 대한 **대화형** 창에 빠르게 액세스할 수 있습니다. 예를 들어 **대화형 창 열기**를 선택하면 Visual Studio에서 해당 특정 환경에 대한 **대화형** 창이 나타납니다.

3. 이제 **파일** > **새로 만들기** > **프로젝트**에서 **Python 애플리케이션** 템플릿을 선택하여 새 프로젝트를 만듭니다. 표시되는 코드 파일에서 이전 자습서 단계와 같이 코사인 웨이브를 만드는, 이번에만 그래픽으로 표시된 다음 코드를 붙여넣습니다. 또는 이전에 만든 프로젝트를 사용하고 코드를 바꿀 수 있습니다. 

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Python 프로젝트를 연 상태에서 Python 환경을 마우스 오른쪽 단추로 클릭하고 **모든 Python 환경 보기**를 선택하여 솔루션 탐색기에서 Python 환경 창을 열 수도 있습니다.

   ![환경](media/environments/environments-view-all-2019.png)

5. 편집기 창에서 `numpy` 및 `matplotlib`를 마우스로 가리키면 확인되지 않은 문을 가져오는 것을 알 수 있습니다. 이는 패키지가 기본 글로벌 환경에 설치되어 있지 않기 때문입니다.

   ![확인되지 않은 패키지 가져오기](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Python 환경 창을 사용하여 패키지 설치

1. Python 환경 창에서 새 Python 프로젝트에 대한 기본 환경을 클릭하고 **패키지** 탭을 선택합니다. 그러면 환경에 현재 설치된 패키지 목록이 표시됩니다.

   ![환경에 설치된 패키지](media/environments/environments-installed-packages-2019.png)

2. 검색 필드에 해당 이름을 입력하고 **명령 실행: pip 설치 matplotlib** 옵션을 선택하여 `matplotlib`를 설치합니다. 이렇게 하면 `matplotlib` 및 해당 패키지가 종속된 패키지(이 경우 `numpy` 포함)가 설치됩니다.

   ![환경에 matplotlib 설치](media/environments/environments-add-matplotlib-2019.png)

5. 메시지가 표시되면 권한 상승에 동의하여 수행합니다.

6. 패키지가 설치된 후 **Python 환경** 창에 나타납니다. 패키지의 오른쪽에 있는 **X**를 누르면 제거됩니다.

   ![환경에 matplotlib 설치 완료](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > 작은 진행률 표시줄이 환경 아래에 표시되어 Visual Studio에서 새로 설치된 패키지에 대한 IntelliSense 데이터베이스를 빌드 중임을 나타낼 수 있습니다. **IntelliSense** 탭에 더 자세한 정보가 표시됩니다. 해당 데이터베이스가 완료될 때까지 자동 완성 및 구문 검사와 같은 IntelliSense 기능은 해당 패키지에 대한 편집기에서 활성화되지 않습니다.
   > 
   > Visual Studio 2017 버전 15.6 이상에서는 IntelliSense 작업에 더 빠른 다른 방법을 사용하며, **IntelliSense** 탭에 해당 효과에 대한 메시지를 표시합니다.

## <a name="run-the-program"></a>프로그램 실행

1. [matplotlib](https://matplotlib.org/)가 설치되었으면 디버거를 사용하거나(**F5**) 사용하지 않고(**Ctrl**+**F5**) 프로그램을 실행하여 출력을 확인합니다.

   ![matplotlib의 출력 예제](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [Git 작업](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>자세히 알아보기

- [Python 환경](managing-python-environments-in-visual-studio.md)
- [Visual Studio의 Django 알아보기](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Visual Studio의 Flask 알아보기](learn-flask-visual-studio-step-01-project-solution.md)
