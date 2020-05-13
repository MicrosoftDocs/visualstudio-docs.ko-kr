---
title: 단위 테스트 Python 코드
description: Visual Studio에서 Python 코드에 대한 단위 테스트를 설정하면 테스트 탐색기 기능을 최대한 활용하여 테스트를 검색, 실행 및 디버그할 수 있습니다.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933478"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Python 프로젝트에 대한 테스트 프레임워크 선택

Visual Studio는 Python의 두 가지 테스트 프레임워크인 [unittest](https://docs.python.org/3/library/unittest.html) 및 [pytest](https://pytest.org/en/latest/)(Visual Studio 2019 버전 16.3부터 제공)를 지원합니다. 기본적으로 Python 프로젝트를 만들 때 프레임워크는 선택되지 않습니다. 프레임워크를 지정하려면 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **속성** 옵션을 선택합니다. 프로젝트 디자이너가 열리고, **테스트** 탭을 통해 테스트를 구성할 수 있습니다. 이 탭에서 프로젝트에 사용하고자 하는 테스트 프레임워크를 선택할 수 있습니다. 

* **unittest** 프레임워크의 경우 프로젝트의 루트 디렉터리가 테스트 검색에 사용됩니다. 이 위치와 테스트 식별을 위한 텍스트 패턴을 **테스트** 탭에서 사용자 지정 값으로 수정할 수 있습니다.
* **pytest** 프레임워크의 경우 테스트 위치 및 파일 이름 패턴과 같은 테스트 옵션이 표준 pytest .ini 구성 파일을 사용하여 지정됩니다. 자세한 내용은 [pytest 참조 설명서](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)를 참조하세요.

프레임워크 선택 및 설정을 저장하면 테스트 탐색기에서 테스트 검색이 시작됩니다. 테스트 탐색기 창이 아직 열려 있지 않은 경우 도구 모음으로 이동하여 **테스트** > **테스트 탐색기**를 선택합니다.

## <a name="configure-testing-for-python-without-a-project"></a>프로젝트 없이 Python 테스트 구성
Visual Studio를 사용하여 Python 코드가 포함된 [폴더를 열어](../../quickstart-05-python-visual-studio-open-folder.md) 프로젝트 없이 기존 Python 코드를 실행 및 테스트할 수 있습니다. 해당 상황에서 **PythonSettings.json** 파일을 사용하여 테스트를 구성해야 합니다. 
1. **로컬 폴더 열기** 옵션을 사용하여 기존 Python 코드를 엽니다. 

   ![Visual Studio 시작 화면](../../media/quickstart-open-folder/01-open-local-folder.png)

1. 솔루션 탐색기 창에서 **모든 파일 표시** 아이콘을 클릭하여 현재 폴더의 모든 파일을 표시합니다.

   ![모든 파일 표시 단추](../../media/unit-test-show-files.png)

1. **Local Settings** 폴더 내에 있는 **PythonSettings.json** 파일로 이동합니다. **Local Settings** 폴더에서 이 파일이 표시되지 않는 경우 수동으로 만듭니다.
   
1. 설정 파일에 **TestFramework** 필드를 추가하고 사용하고자 하는 테스트 프레임워크에 따라 **pytest** 또는 **unittest**를 선택합니다.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > **unittest** 프레임워크의 경우 PythonSettings.json 파일에서 **UnitTestRootDirectory** 및 **UnitTestPattern** 필드가 지정되지 않으면 각각 기본값인 “.” 및 “test*.py”로 추가 및 지정됩니다.

1. 폴더에 테스트에 포함된 폴더와는 별개인 **src** 디렉터리가 포함된 경우 **PythonSettings.json** 파일의 **SearchPaths** 필드를 사용하여 **src** 폴더에 대한 경로를 지정합니다.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. PythonSettings.json 파일에 변경 사항을 저장하여 지정된 프레임워크에 대한 테스트 검색을 시작합니다. 
   > [!Note]
   > 테스트 탐색기가 이미 열린 경우 **CTRL** + **R,A**를 누르면 검색이 실행됩니다.

## <a name="discover-and-view-tests"></a>테스트 검색 및 보기

기본적으로 Visual Studio는 이름이 `test`로 시작하는 메서드로 **unittest** 및 **pytest** 테스트를 식별합니다. 테스트 검색을 확인하려면 다음을 수행합니다.

1. [Python 프로젝트](../../managing-python-projects-in-visual-studio.md)를 엽니다.

1. Visual Studio에 프로젝트가 로드되면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 속성 **테스트** 탭에서 **unittest** 또는 **pytest** 프레임워크를 선택합니다.
   > [!Note]
   > pytest 프레임워크를 사용하는 경우 표준 pytest .ini 구성 파일을 사용하여 테스트 위치 및 파일 이름 패턴을 지정할 수 있습니다. 기본적으로 작업 영역/프로젝트 폴더는 `test_*py` 및 `*_test.py` 패턴으로 사용됩니다. 자세한 내용은 [pytest 참조 설명서](https://docs.pytest.org/en/latest/reference.html#ini-options-ref)를 참조하세요.

1. 프레임워크를 선택한 후 프로젝트를 다시 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택한 다음, **Python 단위 테스트**를 선택한 후 **추가**를 선택합니다.

1. 이렇게 하면 표준 `unittest` 모듈을 가져오고, `unittest.TestCase`에서 테스트 클래스를 파생하며. 스크립트를 직접 실행하는 경우 `unittest.main()`을 호출하는 코드가 있는 *test_1.py* 파일이 만들어집니다.

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. 필요한 경우 파일을 저장하고 **테스트** > **테스트 탐색기** 메뉴 명령을 사용하여 **테스트 탐색기**를 엽니다.

1. **테스트 탐색기**는 프로젝트에서 테스트를 검색하고 아래와 같이 표시합니다. 테스트를 두 번 클릭하면 해당 소스 파일이 열립니다.

    ![기본 test_A를 보여 주는 테스트 탐색기](../../media/unit-test-a-2.png) 

1. 프로젝트에 더 많은 테스트를 추가함에 따라 도구 모음의 **그룹화 방법** 메뉴를 사용하여 **테스트 탐색기**에서 보기를 구성할 수 있습니다.

    ![테스트 탐색기 그룹화 방법 도구 모음 메뉴](../../media/unit-test-group-menu-2.png) 

1. 또한 **검색** 필드에 텍스트를 입력하여 이름별로 테스트를 필터링할 수도 있습니다.

`unittest` 모듈 및 테스트 작성에 대한 자세한 내용은 [Python 2.7 설명서](https://docs.python.org/2/library/unittest.html) 또는 [Python 3.7 설명서](https://docs.python.org/3/library/unittest.html)(python.org)를 참조하세요.

## <a name="run-tests"></a>테스트 실행

**테스트 탐색기**에서 다양한 방법으로 테스트를 실행할 수 있습니다.

- **모두 실행**은 표시된 모든 테스트를 명확하게 실행합니다(필터 적용).
- **실행** 메뉴는 실패한 테스트, 성공한 테스트 또는 실행하지 않은 테스트를 하나의 그룹으로 실행하는 명령을 제공합니다.
- 하나 이상의 테스트를 선택하고 마우스 오른쪽 단추로 클릭한 후 **선택한 테스트 실행**을 선택합니다.

백그라운드에서 테스트가 실행되고, 테스트가 완료되면 **테스트 탐색기**에 각 테스트 상태가 업데이트됩니다.

- 성공한 테스트에는 녹색 틱과 테스트를 실행하는 데 소요된 시간이 표시됩니다.

    ![test_A 성공 상태](../../media/unit-test-A-pass.png)

- 실패한 테스트에는 빨간색 십자 표시와 콘솔 출력 및 테스트 실행의 `unittest` 출력을 보여 주는 **출력** 링크가 표시됩니다.

    ![test_A 실패 상태](../../media/unit-test-A-fail.png)

    ![test_A 실패 및 이유](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>테스트 디버그

단위 테스트는 코드 조각이므로 다른 코드처럼 버그가 있을 수 있으며 경우에 따라 디버거에서 실행해야 합니다. 디버거에서 중단점을 설정하고 변수를 검사하며 코드를 단계별로 실행할 수 있습니다. Visual Studio는 단위 테스트에 대한 진단 도구도 제공합니다.

> [!Note]
> 기본적으로 테스트 디버깅은 ptvsd 4 디버거를 사용합니다. ptvsd 3을 대신 사용하려면 
**도구** > **옵션** > **Python** > **디버깅**의 **레거시 디버거 사용** 옵션을 선택할 수 있습니다. 

디버깅을 시작하려면 코드에 초기 중단점을 설정하고 **테스트 탐색기**에서 테스트(또는 선택 항목)를 마우스 오른쪽 단추로 클릭한 다음, **선택한 테스트 디버그**를 선택합니다. 애플리케이션 코드의 경우처럼 Visual Studio에서 Python 디버거를 시작합니다.

![테스트 디버깅](../../media/unit-test-debugging.png)

**선택한 테스트에 대한 코드 검사 분석**을 사용할 수 있습니다. 자세한 내용은 [코드 검사를 사용하여 테스트할 코드 범위 결정](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)을 참조하세요.
