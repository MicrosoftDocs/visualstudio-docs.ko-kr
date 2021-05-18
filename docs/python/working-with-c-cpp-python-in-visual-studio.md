---
title: Python용 C++ 확장명 작성
description: 혼합 모드 디버깅을 비롯하여 Visual Studio, CPython 및 PyBind11을 사용하여 Python에 대한 C++ 확장을 만드는 연습 과정입니다.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 286d5f2c316379316b1a1cf55334cab39cdc247c
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782636"
---
# <a name="create-a-c-extension-for-python"></a>Python용 C++ 확장 만들기

C++(또는 C)로 작성된 모듈은 하위 수준 운영 체제 기능에 대한 액세스를 가능하게 할 뿐만 아니라 Python 인터프리터의 기능을 확장하는 데 일반적으로 사용됩니다. 모듈은 세 가지 기본 형식이 있습니다.

- 액셀러레이터 모듈: Python은 해석된 언어이기 때문에 성능 향상을 위해 특정 코드 부분을 C++로 작성할 수 있습니다.
- 래퍼 모듈: 기존 C/C++ 인터페이스를 Python 코드에 노출하거나 Python에서 사용하기 쉬운 보다 “Python” 최적화된 API를 노출합니다.
- 하위 수준 시스템 액세스 모듈: `CPython` 런타임, 운영 체제 또는 기본 하드웨어의 하위 수준 기능에 액세스하기 위해 만들었습니다.

이 문서에서는 쌍곡선 탄젠트를 계산하고 Python 코드에서 호출하는 `CPython`용 C++ 확장을 빌드하는 방법에 대해 설명합니다. C++에서 동일한 루틴을 구현할 경우의 관련된 성능 향상을 보여 주기 위해 Python에서 먼저 루틴을 구현합니다.

이 문서에는 Python에서 C++를 사용할 수 있도록 만드는 두 가지 방법을 보여 줍니다.

- [Python 설명서](https://docs.python.org/3/c-api/)에 설명된 표준 `CPython` 확장
- 단순성 때문에 C++ 11에 권장되는 [PyBind11](https://github.com/pybind/pybind11).

이 연습에서 완료된 샘플은 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)(GitHub)에서 찾을 수 있습니다.

## <a name="prerequisites"></a>필수 조건

- **Python 개발** 워크로드가 설치된 Visual Studio 2017 이상(네이티브 확장에 필요한 C++ 워크로드 및 도구 집합을 가져오는 **Python 네이티브 개발 도구** 포함)

    ![Python 네이티브 개발 도구 옵션 선택](media/cpp-install-native.png)

    > [!Tip]
    > **데이터 과학 및 분석 애플리케이션** 워크로드 설치에는 Python 및 **Python 네이티브 개발 도구** 옵션이 기본적으로 포함됩니다.

설치 옵션에 대한 자세한 내용은 [Visual Studio용 Python 지원 설치](installing-python-support-in-visual-studio.md)를 참조하세요. Python을 별도로 설치하는 경우 설치 관리자의 **고급 옵션** 에서 **디버깅 기호 다운로드** 를 선택해야 합니다. Python 코드와 네이티브 코드 간의 혼합 모드 디버깅을 사용하려면 이 옵션을 반드시 사용해야 합니다.

## <a name="create-the-python-application"></a>Python 애플리케이션 만들기

1. **파일** > **새로 만들기** > **프로젝트** 를 선택하여 Visual Studio에서 새 Python 프로젝트를 만듭니다. ‘Python’을 검색하고 **Python 애플리케이션** 템플릿을 선택한 다음 원하는 이름과 위치를 지정하고 **확인** 을 선택합니다.

1. 프로젝트의 *.py* 파일에 다음 코드를 붙여넣습니다(또는 수동으로 입력하여 [Python 편집 기능](editing-python-code-in-visual-studio.md)의 일부를 경험해 보세요). 이 코드는 수학 라이브러리를 사용하지 않고 쌍곡선 탄젠트를 계산하며, 네이티브 확장을 사용하여 코드를 가속합니다.

    > [!Tip]
    > C++로 다시 작성하기 전에 순수한 Python에서 코드를 작성하세요. 이렇게 하면 네이티브 코드가 올바른지 쉽게 확인할 수 있습니다.

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. **디버그** > **디버깅하지 않고 시작**(**Ctrl**+**F5**)을 사용하여 프로그램을 실행하고 결과를 확인합니다. `COUNT` 변수를 조정하여 벤치 마크를 실행할 시간을 변경할 수 있습니다. 이 연습의 목적을 위해 벤치마크에 약 2초가 걸리도록 수를 설정합니다.

> [!TIP]
> 벤치 마크를 실행할 때는 항상 **디버깅** > **디버깅하지 않고 시작** 을 사용하여 Visual Studio 디버거 내에서 코드를 실행할 때 발생하는 오버헤드를 방지합니다.

## <a name="create-the-core-c-projects"></a>핵심 C++ 프로젝트 만들기

"superfastcode" 및 "superfastcode2"라는 두 개의 동일한 C++ 프로젝트를 만들려면 이 섹션의 지침을 따릅니다. 나중에 각 프로젝트에서 두 가지 방법을 사용하여 Python에 C++ 코드를 공개합니다.

1. **솔루션 탐색기** 에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트** 를 선택합니다. Visual Studio 솔루션은 Python 및 C++ 프로젝트를 모두 함께 포함합니다(Python용 Visual Studio 사용에 대한 이점 중 하나).

1. "C++"를 검색하고, **빈 프로젝트** 를 선택하고, 이름을 "superfastcode"(두 번째 프로젝트는 "superfastcode2")로 지정하고 **확인** 을 선택합니다.

    > [!Tip]
    > Visual Studio에 설치된 **Python 네이티브 개발 도구** 를 사용하면 아래 설명된 내용이 이미 많이 포함되어 있는 **Python 확장 모듈** 템플릿으로 시작할 수 있습니다. 그러나 이 연습에서는 빈 프로젝트로 시작하여 확장 모듈 빌드를 단계별로 보여 줍니다. 프로세스를 이해하고 나면 사용자 고유의 확장을 작성할 때 템플릿으로 시간을 절약할 수 있습니다.

1. 새 프로젝트에서 **소스 파일** 노드를 마우스 오른쪽 단추로 클릭하여 C++ 파일을 만들고 **추가** > **새 항목** 을 선택한 다음, **C++ 파일** 을 선택하여 이름을 `module.cpp`로 지정하고 **확인** 을 선택합니다.

    > [!Important]
    > 이어지는 다음 단계에서 C++ 속성 페이지를 켜려면 *.cpp* 확장명을 가진 파일이 필요합니다.

1. 64비트 Python 런타임을 사용하는 경우 기본 도구 모음의 드롭다운 메뉴를 사용하여 **x64** 구성을 활성화합니다. 32비트 Python 런타임의 경우 **Win32** 구성을 활성화합니다.

1. **솔루션 탐색기** 에서 C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다. **구성** 의 값은 **활성(디버그)** 이어야 하고, **플랫폼** 은 이전 단계의 선택 사항에 따라 **활성(x64)** 또는 **활성(Win32)** 이 됩니다.

    > [!Tip]
    > 사용자 자체 프로젝트에 대해서는 디버그 구성과 릴리스 구성을 모두 구성하는 것이 좋습니다. 여기서는 디버그 구성만 구성하며, 어설션을 포함한 C++ 런타임의 일부 디버깅 기능을 사용하지 않도록 설정하는 `CPython`의 릴리스 빌드를 사용하도록 설정합니다. `CPython` 디버그 이진 파일(`python_d.exe`)을 사용하려면 다른 설정이 필요합니다.

1. 다음 표에 설명된 대로 특정 속성을 설정한 다음, **확인** 을 선택합니다.
    ::: moniker range=">=vs-2019"
    | 탭 | 속성 | 값 |
    | --- | --- | --- |
    | **일반** | **대상 이름** | `from...import` 문의 Python에서 참조하려는 모듈의 이름을 지정합니다. Python에 대한 모듈을 정의하는 경우 C++에서 이 동일한 이름을 사용합니다. 프로젝트 이름을 모듈 이름으로 사용하려는 경우 **$(ProjectName)** 기본값을 그대로 둡니다. `python_d.exe`의 경우 이름 끝에 `_d`를 추가합니다. |
    | | **구성 유형** | **동적 라이브러리(.dll)** |
    | **고급** | **대상 파일 확장명** | **.pyd** |
    | **C/C++** > **일반** | **추가 포함 디렉터리** | 설치에 맞게 Python *include* 폴더를 추가합니다(예: `c:\Python36\include`).  |
    | **C/C++** > **전처리기** | **전처리기 정의** | 존재하는 경우 **_DEBUG** 값을 **NDEBUG** 로 변경하여 `CPython`의 디버그 이외 버전과 일치시킵니다. (`python_d.exe`를 사용하는 경우에는 이 항목을 변경하지 않습니다.) |
    | **C/C++** > **코드 생성** | **런타임 라이브러리** | `CPython`의 디버그 이외 버전과 일치시키기 위한 **다중 스레드 DLL(/MD)** (`python_d.exe`를 사용하는 경우에는 이 항목을 변경하지 않습니다.) |
    | **링커** > **일반** | **추가 라이브러리 디렉터리** | *.lib* 파일을 포함하는 Python *libs* 폴더를 설치에 맞게 추가합니다(예: `c:\Python36\libs`). *.py* 파일을 포함하는 *Lib* 폴더가 ‘아니라’ *.lib* 파일을 포함하는 *libs* 폴더를 가리켜야 합니다. |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | 탭 | 속성 | 값 |
    | --- | --- | --- |
    | **일반** | **일반** > **대상 이름** | `from...import` 문의 Python에서 참조하려는 모듈의 이름을 지정합니다. Python에 대한 모듈을 정의하는 경우 C++에서 이 동일한 이름을 사용합니다. 프로젝트 이름을 모듈 이름으로 사용하려는 경우 **$(ProjectName)** 기본값을 그대로 둡니다. `python_d.exe`의 경우 이름 끝에 `_d`를 추가합니다. |
    | | **일반** > **대상 확장명** | **.pyd** |
    | | **프로젝트 기본값** > **구성 형식** | **동적 라이브러리(.dll)** |
    | **C/C++** > **일반** | **추가 포함 디렉터리** | 설치에 맞게 Python *include* 폴더를 추가합니다(예: `c:\Python36\include`).  |
    | **C/C++** > **전처리기** | **전처리기 정의** | 존재하는 경우 **_DEBUG** 값을 **NDEBUG** 로 변경하여 `CPython`의 디버그 이외 버전과 일치시킵니다. (`python_d.exe`를 사용하는 경우에는 이 항목을 변경하지 않습니다.) |
    | **C/C++** > **코드 생성** | **런타임 라이브러리** | `CPython`의 디버그 이외 버전과 일치시키기 위한 **다중 스레드 DLL(/MD)** (`python_d.exe`를 사용하는 경우에는 이 항목을 변경하지 않습니다.) |
    | **링커** > **일반** | **추가 라이브러리 디렉터리** | *.lib* 파일을 포함하는 Python *libs* 폴더를 설치에 맞게 추가합니다(예: `c:\Python36\libs`). *.py* 파일을 포함하는 *Lib* 폴더가 ‘아니라’ *.lib* 파일을 포함하는 *libs* 폴더를 가리켜야 합니다. |
    ::: moniker-end
    
    > [!Tip]
    > 프로젝트 속성에서 C/C++ 탭이 표시되지 않는 경우 프로젝트에 C/C++ 소스 파일로 식별되는 파일이 포함되어 있지 않기 때문입니다. *.c* 또는 *.cpp* 확장명을 사용하지 않고 소스 파일을 만드는 경우 이런 상태가 발생할 수 있습니다. 예를 들어 이전의 새 항목 대화 상자에서 실수로 `module.cpp` 대신 `module.coo`를 입력한 경우, Visual Studio는 해당 파일을 생성하지만 파일 형식을 C/C++ 속성 탭을 활성화하는 “C/C+ 코드”로 설정하지 않습니다. 이와 같은 잘못된 식별 정보는 해당 파일의 이름을 `.cpp`로 바꾸는 경우에도 그대로 남게 됩니다. 파일 형식을 제대로 설정하려면 **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택한 다음, **파일 형식** 을 **C/C++ 코드** 로 설정합니다.

1. C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **빌드** 를 선택하여 구성(**디버그** 및 **릴리스**)을 테스트합니다. *.pyd* 파일은 C++ 프로젝트 폴더 자체가 아니라 **디버그** 및 **릴리스** 아래의 **솔루션** 폴더에 있습니다.

1. C++ 프로젝트의 주 *module.cpp* 파일에 다음 코드를 추가합니다.

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. C++ 프로젝트를 다시 빌드하여 코드가 올바른지 확인합니다.

1. 아직 만들지 않았다면 위의 단계를 반복하여 동일한 콘텐츠의 "superfastcode2"라는 두 번째 프로젝트를 만듭니다.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ 프로젝트를 Python용 확장으로 변환

C++ DLL을 Python용 확장으로 만들려면 먼저 내보낸 메서드를 Python 형식과 상호 작용하도록 수정해야 합니다. 그런 다음 모듈의 메서드 정의와 함께 모듈을 내보내는 함수를 추가해야 합니다.

이어지는 섹션에서는 `CPython` 확장과 PyBind11을 사용하여 이러한 단계를 수행하는 방법에 대해 설명합니다.

### <a name="cpython-extensions"></a>CPython 확장

이 섹션에 표시된 기능에 대한 자세한 배경은 [Python/C API 참조 설명서](https://docs.python.org/3/c-api/index.html) 및 특히 python.org에 있는 [모듈 개체](https://docs.python.org/3/c-api/module.html)를 참조하세요(올바른 설명서를 보려면 오른쪽 위에 있는 드롭다운 컨트롤에서 Python의 버전을 선택해야 함).

1. *module.cpp* 의 맨 위에 *Python.h* 를 포함시킵니다.

    ```cpp
    #include <Python.h>
    ```

1. Python 형식을 허용하고 반환하도록 `tanh_impl` 메서드를 수정합니다(즉, `PyObject*`).

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` 함수가 Python에 표시되는 방식을 정의하는 구조체를 추가합니다.

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. 특히 `from...import` 문을 사용할 때 Python 코드에서 참조하려는 모듈을 정의하는 구조를 추가합니다. (**구성 속성** > **일반** > **대상 이름** 에서 프로젝트 속성 값과 일치하도록 합니다.) 다음 예제에서 “superfastcode” 모듈 이름은 `fast_tanh`가 `superfastcode_methods` 내에 정의되어 있으므로 Python에서 `from superfastcode import fast_tanh`를 사용할 수 있음을 나타냅니다. *module.cpp* 와 같은 C++ 프로젝트 내부의 파일 이름은 중요하지 않습니다.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python에서 이름이 `PyInit_<module-name>`인 모듈을 로드할 때 호출하는 메서드를 추가합니다. 여기서 &lt;module-name&gt;은 C++ 프로젝트의 **일반** > **대상 이름** 속성과 정확하게 일치합니다. 즉, 프로젝트에서 빌드된 *.pyd* 의 파일 이름과 일치합니다.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. C++ 프로젝트를 다시 빌드하여 코드를 확인합니다. 오류가 발생할 경우 아래의 [문제 해결](#troubleshooting) 섹션을 참조하세요.

### <a name="pybind11"></a>PyBind11

이전 섹션에서 단계를 완료한 경우 C++ 코드에 필요한 모듈 구조체를 만들기 위해 많은 상용구 코드를 사용했음을 알 수 있습니다. PyBind11에서는 C++ 헤더 파일에서 훨씬 적은 코드를 사용하여 동일한 결과를 달성하는 매크로를 통해 프로세스를 간소화합니다. 이 섹션에 나온 배경 지식은 [PyBind11 기본](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)(github.com)을 참조하세요.

1. pip(`pip install pybind11` 또는 `py -m pip install pybind11`)를 사용하여 PyBind11을 설치합니다. (Python 환경 창을 사용하여 설치하고 다음 단계에서 ‘Open in Powershell’ 명령을 사용해도 됩니다.)

1. 동일한 터미널에서 `python -m pybind11 --includes` 또는 `py -m pybind11 --includes`를 실행합니다. 그러면 프로젝트의 **C/C++**  > **일반** > **추가 포함 디렉터리** 속성에 추가해야 하는 경로의 목록이 출력됩니다(`-I` 접두사가 있다면 제거하세요).

1. 이전 섹션의 변경 내용을 포함하지 않는 새 *module.cpp* 의 맨 위에 *pybind11.h* 를 포함합니다.

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *module.cpp* 의 맨 아래에서 `PYBIND11_MODULE` 매크로를 사용하여 C++ 함수에 대한 진입점을 정의합니다.

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. C++ 프로젝트를 빌드하여 코드를 확인합니다. 오류가 발생할 경우 다음의 문제 해결 섹션을 참조하세요.

### <a name="troubleshooting"></a>문제 해결

C++ 모듈은 다음과 같은 이유로 컴파일에 실패할 수 있습니다.

- *Python.h* 를 찾을 수 없음(**E1696: 소스 파일 “Python.h”를 열 수 없음** 및/또는 **C1083: “Python.h” 포함 파일을 열 수 없음: 해당 파일 또는 디렉터리 없음**): 프로젝트 속성의 **C/C++** > **일반** > **추가 포함 디렉터리** 의 경로가 Python 설치의 *include* 폴더로 설정되어 있는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- Python 라이브러리를 찾을 수 없음: 프로젝트 속성에서 **링커** > **일반** > **추가 라이브러리 디렉터리** 의 경로가 Python 설치의 *libs* 폴더를 가리키는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- 대상 아키텍처와 관련된 링커 오류: C++ 대상 프로젝트 아키텍처를 Python 설치에 맞게 변경합니다. 예를 들어 C++ 프로젝트에서 **Win32** 를 대상으로 지정하지만 Python 설치가 64비트인 경우, C++ 프로젝트를 **x64** 로 변경합니다.

## <a name="test-the-code-and-compare-the-results"></a>코드를 테스트하고 결과 비교

DLL을 Python 확장으로 구조화했으므로 Python 프로젝트에서 이를 참조하고, 모듈을 가져오고, 해당 메서드를 사용할 수 있습니다.

### <a name="make-the-dll-available-to-python"></a>Python에서 DLL을 사용할 수 있도록 설정

Python에서 DLL을 사용할 수 있도록 설정하는 방법은 두 가지가 있습니다.

Python 프로젝트와 C++ 프로젝트가 같은 솔루션에 있는 경우 첫 번째 방법을 사용할 수 있습니다. **솔루션 탐색기** 로 이동하여 Python 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭한 다음, **참조 추가** 를 선택합니다. 표시되는 대화 상자에서 **프로젝트** 탭을 선택하고 **superfastcode** 와 **superfastcode2** 프로젝트를 모두 선택한 다음, **확인** 을 선택합니다.

![superfastcode 프로젝트에 참조 추가](media/cpp-add-reference.png)

다음 단계에 설명된 두 번째 방법은 다른 Python 프로젝트에서도 사용 가능하도록 모듈을 Python 환경에 설치합니다. 자세한 설명서는 [**setuptools** 프로젝트](https://setuptools.readthedocs.io/)를 참조하세요.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** 을 선택하여 C++ 프로젝트에서 *setup.py* 라는 파일을 만듭니다. 그런 다음, **C++ 파일(.cpp)** 을 선택하고 파일 이름을 `setup.py`로 변경한 다음, **확인** 을 선택합니다(*.py* 확장명을 사용하여 파일 이름을 지정하면 C++ 파일 템플릿을 사용해도 Visual Studio에서 Python으로 인식함). 편집기에 파일이 표시되면 확장 메서드에 적절하게 다음 코드를 붙여넣습니다.

    **`CPython` 확장(superfastcode 프로젝트):**

    ```python
    from setuptools import setup, Extension

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(
        name='superfastcode',
        version='1.0',
        description='Python Package with superfastcode C++ extension',
        ext_modules=[sfc_module]
    )
    ```

    **`PyBind11`(superfastcode2 프로젝트):**

    ```python
    from setuptools import setup, Extension
    import pybind11

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2',
        sources=['module.cpp'],
        include_dirs=[pybind11.get_include()],
        language='c++',
        extra_compile_args=cpp_args,
        )

    setup(
        name='superfastcode2',
        version='1.0',
        description='Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules=[sfc_module],
    )
    ```

1. C++ 프로젝트에서 *pyproject.toml* 이라는 두 번째 파일을 만들고 다음 코드를 붙여넣습니다.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. 확장을 빌드하려면 *pyproject.toml* 탭을 마우스 오른쪽 단추로 클릭하고 ‘전체 경로 복사’를 선택합니다(이 파일을 사용하기 전에 경로에서 *pyproject.toml* 이름을 삭제합니다).

1. 솔루션 탐색기에서 활성 Python 환경을 마우스 오른쪽 단추로 클릭하고 Python 패키지 관리를 선택합니다.

    > [!Tip]
    > 패키지를 이미 설치한 경우에는 여기에 표시됩니다. 계속하기 전에 ‘X’를 클릭하여 제거하세요.

1. 복사한 경로를 검색 상자에 붙여넣고 끝에 있는 `pyproject.toml`을 삭제합니다. 그런 다음 Enter 키를 눌러 해당 디렉터리에서 설치를 진행합니다.

    > [!Tip]
    > 권한 오류 때문에 설치가 실패한다면 `--user`를 추가하고 명령을 다시 시도합니다.


### <a name="call-the-dll-from-python"></a>Python에서 DLL 호출

이전 섹션에서 설명한 대로 Python에 사용할 수 있는 DLL을 만들었으면 이제 Python 코드에서 `superfastcode.fast_tanh` 및 `superfastcode2.fast_tanh2` 함수를 호출하여 Python 구현과 성능을 비교할 수 있습니다.

1. *.py* 파일에 다음 줄을 추가하여 DLL에서 가져온 메서드를 호출하고 출력을 표시합니다.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Python 프로그램을 실행하고(**디버깅** > **디버깅하지 않고 시작** 또는 **Ctrl**+**F5**) C++ 루틴이 Python 구현보다 대략 5~20배 빠르게 실행되는지 확인합니다. 일반적인 출력은 다음과 같습니다.

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    **디버깅하지 않고 시작** 명령이 비활성화된 경우 **솔루션 탐색기** 에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.

1. 차이가 더 분명해지도록 `COUNT` 변수를 늘려 보세요. 또한 **디버그** 빌드는 덜 최적화되고 다양한 오류 검사를 포함하기 때문에 C++ 모듈의 **디버그** 빌드가 **릴리스** 빌드보다 더 느리게 실행됩니다. 이러한 구성을 마음껏 전환하여 비교해 보세요(하지만 비교가 끝나면 앞에 나온 **릴리스** 구성의 속성을 업데이트해야 합니다).

출력에서는 PyBind11 확장이 `CPython` 확장만큼 빠르지는 않지만, 순수한 Python 확장보다는 훨씬 빠름을 알 수 있습니다. 이러한 차이는 주로 여러 매개 변수, 매개 변수 이름 또는 키워드 인수를 지원하지 않는 `METH_O` 호출을 사용했기에 발생합니다. PyBind11은 Python형 인터페이스를 호출자에게 제공하기 위해 좀 더 복잡한 코드를 생성하지만, 테스트 코드는 함수를 500,000번 호출하기 때문에 오버헤드가 대폭 증가할 수 있습니다.

`for` 루프를 네이티브 코드로 옮겨 오버헤드를 줄일 수 있었습니다. 이렇게 하려면 [반복기 프로토콜](https://docs.python.org/c-api/iter.html)(또는 [함수 매개 변수](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)에는 PyBind11의 `py::iterable` 형식)을 사용하여 각 요소를 처리해야 합니다. Python과 C++ 사이에서 반복되는 전환을 제거하면 시퀀스를 처리하는 데 걸리는 시간을 효과적으로 줄일 수 있습니다.

### <a name="troubleshooting"></a>문제 해결

모듈을 가져올 때 `ImportError`가 발생한다면, 다음 문제 중 하나가 원인일 수 있습니다.

* 프로젝트 참조를 통해 빌드하는 경우에는 C++ 프로젝트 속성이 Python 프로젝트에 활성화된 Python 환경과, 특히 Include 및 Library 디렉터리와 일치하는지 확인합니다.

* 출력 파일의 이름이 `superfastcode.pyd`인지 확인합니다. 다른 이름이나 확장명을 사용하면 가져올 수 없게 됩니다.

* *setup.py* 파일을 사용하여 모듈을 설치한 경우에는 Python 프로젝트에 활성화된 Python 환경에서 *pip* 명령을 실행했는지 확인합니다. 솔루션 탐색기에서 Python 환경을 확장하면 `superfastcode` 관련 항목이 표시됩니다.

## <a name="debug-the-c-code"></a>C++ 코드 디버그

Visual Studio는 디버깅 Python 및 C++ 코드를 함께 지원합니다. 이 섹션에서는 **superfastcode** 프로젝트를 사용하여 프로세스를 설명하며, 단계는 **superfastcode2** 프로젝트에서도 동일합니다.

1. **솔루션 탐색기** 에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**, **디버그** 탭을 차례로 선택한 다음, **디버그** > **네이티브 코드 디버깅 사용** 옵션을 선택합니다.

    > [!Tip]
    > 네이티브 코드 디버깅을 사용하면 프로그램이 완료되었을 때 일반적인 **계속하려면 아무 키나 누르세요.** 일시 중지를 제공하지 않고 Python 출력 창이 바로 사라질 수 있습니다. 강제로 일시 중지하려면 네이티브 코드 디버깅을 사용할 때 **디버그** 탭의 **실행** > **인터프리터 인수** 필드에 `-i` 옵션을 추가합니다. 이 인수는 코드가 마무리된 후에 Python 인터프리터를 대화형 모드로 전환하며, 이때 **Ctrl**+**Z** > **Enter** 키를 눌러 종료할 때까지 대기합니다. 또는 Python 코드를 수정하지 않으려면 프로그램의 끝에 `import os` 및 `os.system("pause")` 문을 추가할 수 있습니다. 이 코드는 원래 일시 중지 프롬프트를 복제합니다.

1. **파일** > **저장** 을 선택하여 속성 변경 내용을 저장합니다.

1. Visual Studio 도구 모음에서 빌드 구성을 **디버그** 로 설정합니다.

    ![빌드 구성을 디버그로 설정](media/cpp-set-debug.png)

1. 일반적으로 디버거에서 코드를 실행하는 데 더 많은 시간이 걸리기 때문에 *.py* 파일의 `COUNT` 변수를 약 5배 작은 값으로 변경하는 것이 좋습니다(예: `500000`에서 `100000`으로 변경).

1. C++ 코드에서는 `tanh_impl` 메서드의 첫 줄에 중단점을 설정한 다음 디버거를 시작합니다(**F5** 또는 **디버그** > **디버깅 시작**). 해당 코드가 호출되면 디버거가 중지합니다. 중단점이 적중되지 않는 경우 구성이 **디버그** 로 설정되어 있는지, 프로젝트를 저장했는지 확인합니다(디버거를 시작할 때 자동으로 수행되지 않음).

    ![C++ 코드의 중단점에서 중지](media/cpp-debugging.png)

1. 이때 C++ 코드를 단계별로 실행하고 변수를 검사하는 등의 작업을 수행할 수 있습니다. 이러한 기능은 [C++ 및 Python 디버그](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)에 자세히 설명되어 있습니다.

## <a name="alternative-approaches"></a>대체 방법

아래 표에 설명된 대로 다른 방법으로 Python 확장을 만들 수 있습니다. `CPython` 및 `PyBind11`에 대한 처음 두 항목은 이 문서에서 이미 설명했습니다.

| 접근 방식 | Vintage | 담당자 | 
| --- | --- | --- |
| `CPython`용 C/C++ 확장 모듈 | 1991 | 표준 라이브러리 | 
| [PyBind11](https://github.com/pybind/pybind11)(C++에 권장됨) | 2015 |  |
| [Cython](https://cython.org)(C에 권장됨) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [cryptography](https://cryptography.io/), [pypy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>추가 정보

이 연습에서 완료된 샘플은 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)(GitHub)에서 찾을 수 있습니다.
