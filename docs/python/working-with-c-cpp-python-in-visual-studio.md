---
title: Python용 C++ 확장명 작성
description: 혼합 모드 디버깅을 비롯하여 Visual Studio, CPython 및 PyBind11을 사용하여 Python에 대한 C++ 확장을 만드는 연습 과정입니다.
ms.date: 11/19/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c81984e8921e44e32b58ae7f5c5c27c5fe8b12f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956960"
---
# <a name="create-a-c-extension-for-python"></a>Python용 C++ 확장 만들기

C++(또는 C)로 작성된 모듈은 하위 수준 운영 체제 기능에 대한 액세스를 가능하게 할 뿐만 아니라 Python 인터프리터의 기능을 확장하는 데 일반적으로 사용됩니다. 모듈은 세 가지 기본 형식이 있습니다.

- 액셀러레이터 모듈: Python은 해석된 언어이기 때문에 성능 향상을 위해 특정 코드 부분을 C++로 작성할 수 있습니다.
- 래퍼 모듈: 기존 C/C++ 인터페이스를 Python 코드에 노출하거나 Python에서 사용하기 쉬운 보다 “Python” 최적화된 API를 노출합니다.
- 하위 수준 시스템 액세스 모듈: CPython 런타임, 운영 체제 또는 기본 하드웨어의 하위 수준 기능에 액세스하기 위해 만들었습니다.

이 문서에서는 쌍곡 탄젠트를 계산하고 Python 코드에서 호출하는 CPython용 C++ 확장을 빌드하는 방법에 대해 설명합니다. C++에서 동일한 루틴을 구현할 경우의 관련된 성능 향상을 보여 주기 위해 Python에서 먼저 루틴을 구현합니다.

이 문서에는 Python에서 C++를 사용할 수 있도록 만드는 두 가지 방법을 보여 줍니다.

- [Python 설명서](https://docs.python.org/3/c-api/)에 설명된 표준 CPython 확장
- 단순성 때문에 C++ 11에 권장되는 [PyBind11](https://github.com/pybind/pybind11).

이 방법과 다른 방법의 비교는 이 문서의 끝에 있는 [대체 방법](#alternative-approaches)에 있습니다.

이 연습에서 완료된 샘플은 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)(GitHub)에서 찾을 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

- 기본 옵션과 함께 설치된 **C++를 사용한 데스크톱 개발** 및 **Python 개발** 워크로드를 모두 사용하는 Visual Studio 2017 이상.
- **Python 개발** 워크로드에서 **Python 네이티브 개발 도구** 오른쪽에 있는 상자를 선택합니다. 이 옵션은 이 문서에 설명된 대부분의 구성을 설정합니다. 이 옵션에는 C++ 워크로드도 자동으로 포함됩니다.

    ![Python 네이티브 개발 도구 옵션 선택](media/cpp-install-native.png)

    > [!Tip]
    > **데이터 과학 및 분석 애플리케이션** 워크로드 설치에는 Python 및 **Python 네이티브 개발 도구** 옵션이 기본적으로 포함됩니다.

다른 버전의 Visual Studio 사용을 포함한 자세한 내용은 [Visual Studio용 Python 지원 설치](installing-python-support-in-visual-studio.md)를 참조하세요. Python을 별도로 설치하는 경우 설치 관리자의 **고급 옵션**에서 **디버깅 기호 다운로드** 및 **디버그 버전의 이진 파일 다운로드**를 선택해야 합니다. 이 옵션은 디버그 빌드를 수행하도록 선택할 경우 필요한 디버그 라이브러리를 사용할 수 있도록 합니다.

## <a name="create-the-python-application"></a>Python 애플리케이션 만들기

1. **파일** > **새로 만들기** > **프로젝트**를 선택하여 Visual Studio에서 새 Python 프로젝트를 만듭니다. “Python”을 검색하고 **Python 애플리케이션** 템플릿을 선택한 다음 적합한 이름과 위치를 지정하고 **확인**을 선택합니다.

1. C++로 작업하려면 32비트 Python 인터프리터(Python 3.6 이상 권장)를 사용해야 합니다. Visual Studio의 **솔루션 탐색기** 창에서 프로젝트 노드를 확장한 다음, **Python 환경** 노드를 확장합니다. 32비트 환경이 기본값으로 표시(굵게 표시 또는 **전역 기본값** 레이블 지정)되지 않는 경우 [프로젝트에 대한 Python 환경 선택](selecting-a-python-environment-for-a-project.md)의 지침을 따르세요. 32비트 인터프리터가 설치되지 않은 경우 [Python 인터프리터 설치](installing-python-interpreters.md)를 참조하세요.

1. 프로젝트의 *.py* 파일에서 쌍곡 탄젠트 계산을 벤치마크하는 다음 코드(비교하기 쉽도록 수학 라이브러리를 사용하지 않고 구현됨)를 붙여넣습니다. 언제든지 코드를 수동으로 입력하여 [Python 편집 기능](editing-python-code-in-visual-studio.md)의 일부를 경험해 보세요.

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

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
> 벤치 마크를 실행할 때는 항상 **디버깅** > **디버깅하지 않고 시작**을 사용하여 Visual Studio 디버거 내에서 코드를 실행할 때 발생하는 오버헤드를 방지합니다.

## <a name="create-the-core-c-projects"></a>핵심 C++ 프로젝트 만들기

"superfastcode" 및 "superfastcode2"라는 두 개의 동일한 C++ 프로젝트를 만들려면 이 섹션의 지침을 따릅니다. 나중에 각 프로젝트에서 다른 방법을 사용하여 Python에 C++ 코드를 공개할 수 있습니다.

1. `PYTHONHOME` 환경 변수가 사용하려는 Python 인터프리터로 설정되어 있는지 확인합니다. Visual Studio의 C++ 프로젝트는 이 변수를 사용하여 Python 확장을 만들 때 사용되는 *python.h*와 같은 파일을 찾습니다.

1. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. Visual Studio 솔루션은 Python 및 C++ 프로젝트를 모두 함께 포함합니다(Python용 Visual Studio 사용에 대한 이점 중 하나).

1. "C++"를 검색하고, **빈 프로젝트**를 선택하고, 이름을 "superfastcode"(두 번째 프로젝트는 "superfastcode2")로 지정하고 **확인**을 선택합니다.

    > [!Tip]
    > Visual Studio에 설치된 **Python 네이티브 개발 도구**를 사용하면 아래 설명된 내용이 이미 많이 포함되어 있는 **Python 확장 모듈** 템플릿으로 시작할 수 있습니다. 그러나 이 연습에서는 빈 프로젝트로 시작하여 확장 모듈 빌드를 단계별로 보여 줍니다. 프로세스를 이해하고 나면 사용자 고유의 확장을 작성할 때 템플릿으로 시간을 절약할 수 있습니다.

1. 새 프로젝트에서 **소스 파일** 노드를 마우스 오른쪽 단추로 클릭하여 C++ 파일을 만들고 **추가** > **새 항목**을 선택한 다음, **C++ 파일**을 선택하여 이름을 `module.cpp`로 지정하고 **확인**을 선택합니다.

    > [!Important]
    > 이어지는 다음 단계에서 C++ 속성 페이지를 켜려면 *.cpp* 확장명을 가진 파일이 필요합니다.

1. **솔루션 탐색기**에서 C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. 표시되는 **속성 페이지** 대화 상자의 맨 위에서 **구성**을 **모든 구성**으로, **플랫폼**을 **Win32**로 설정합니다.

1. 다음 표에 설명된 대로 특정 속성을 설정한 다음, **확인**을 선택합니다.

    | 탭 | 속성 | 값 |
    | --- | --- | --- |
    | **일반** | **일반** > **대상 이름** | `from...import` 문의 Python에서 참조하려는 모듈의 이름을 지정합니다. Python에 대한 모듈을 정의하는 경우 C++에서 이 동일한 이름을 사용합니다. 프로젝트 이름을 모듈 이름으로 사용하려는 경우 **$(ProjectName)** 기본값을 그대로 둡니다. |
    | | **일반** > **대상 확장명** | **.pyd** |
    | | **프로젝트 기본값** > **구성 형식** | **동적 라이브러리(.dll)** |
    | **C/C++**  > **일반** | **추가 포함 디렉터리** | 설치에 맞게 Python *include* 폴더를 추가합니다(예: `c:\Python36\include`).  |
    | **C/C++**  > **전처리기** | **전처리기 정의** | **CPython만**: `Py_LIMITED_API;`를 문자열의 시작 부분에 추가합니다(세미콜론 포함). 이 정의로 Python에서 호출할 수 있는 일부 함수가 제한되고 다른 버전의 Python 간 코드 이식성이 향상됩니다. PyBind11을 사용하는 경우 이 정의를 추가하지 마세요. 추가하면 빌드 오류가 표시됩니다. |
    | **C/C++**  > **코드 생성** | **런타임 라이브러리** | **다중 스레드 DLL(/MD)** (아래 경고 참조) |
    | **링커** > **일반** | **추가 라이브러리 디렉터리** | *.lib* 파일을 포함하는 Python *libs* 폴더를 설치에 맞게 추가합니다(예: `c:\Python36\libs`). *.py* 파일을 포함하는 *Lib* 폴더가 ‘아니라’ *.lib* 파일을 포함하는 *libs* 폴더를 가리켜야 합니다.  |

    > [!Tip]
    > 프로젝트 속성에서 C/C++ 탭이 표시되지 않는 경우 프로젝트에 C/C++ 소스 파일로 식별되는 파일이 포함되어 있지 않기 때문입니다. *.c* 또는 *.cpp* 확장명을 사용하지 않고 소스 파일을 만드는 경우 이런 상태가 발생할 수 있습니다. 예를 들어 이전의 새 항목 대화 상자에서 실수로 `module.cpp` 대신 `module.coo`를 입력한 경우 Visual Studio에서 파일을 만들지만, C/C++ 속성 탭을 활성화하는 “C/C++ 코드”로 파일 형식을 설정하지 않습니다. 파일 이름을 `.cpp`로 변경하는 경우에도 여전히 잘못 식별됩니다. 파일 형식을 제대로 설정하려면 **솔루션 탐색기**에서 파일을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음, **파일 형식**을 **C/C++ 코드**로 설정합니다.

    > [!Warning]
    > 디버그 구성에 대해서도 **C/C++**  > **코드 생성** > **런타임 라이브러리** 옵션을 항상 **다중 스레드 DLL(/MD)** 로 설정합니다. 이 설정은 디버그가 아닌 Python 이진을 빌드할 때 사용되기 때문입니다. CPython에서는 **다중 스레드 디버그 DLL(/MDd)** 옵션을 설정하는 경우 **디버그** 구성을 빌드하면 **C1189: Py_LIMITED_API는 Py_DEBUG, Py_TRACE_REFS 및 Py_REF_DEBUG와 호환되지 않음** 오류가 발생합니다. 또한 빌드 오류를 방지하기 위해 `Py_LIMITED_API`(CPython에는 필요하지만 PyBind11에는 필요하지 않음)를 제거하는 경우 모듈을 가져오려고 하면 Python이 충돌합니다. (뒷부분에 설명된 대로 크래시는 DLL의 `PyModule_Create` 호출 내에서 발생하고 **심각한 Python 오류: PyThreadState_Get: 현재 스레드 없음**이라는 메시지가 출력됩니다.)
    >
    > /MDd 옵션은 Python 디버그 이진 파일(예: *python_d.exe*)을 빌드하는 데 사용되지만 확장 DLL용으로 선택하면 `Py_LIMITED_API`에서 빌드 오류가 발생합니다.

1. C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **빌드**를 선택하여 구성(**디버그** 및 **릴리스**)을 테스트합니다. *.pyd* 파일은 C++ 프로젝트 폴더 자체가 아니라 **디버그** 및 **릴리스** 아래의 **솔루션** 폴더에 있습니다.

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

이어지는 섹션에서는 CPython 확장과 PyBind11을 사용하여 이러한 단계를 수행하는 방법에 대해 설명합니다.

### <a name="cpython-extensions"></a>CPython 확장

Python 3.x에 대해 이 섹션에 표시된 기능의 배경은 [Python/C API 참조 설명서](https://docs.python.org/3/c-api/index.html) 및 특히 python.org에 있는 [모듈 개체](https://docs.python.org/3/c-api/module.html)를 참조하세요(올바른 설명서를 보려면 오른쪽 위에 있는 드롭다운 컨트롤에서 Python의 버전을 선택해야 함).

Python 2.7로 작업하는 경우 [Extending Python 2.7 with C or C++](https://docs.python.org/2.7/extending/extending.html)(C 또는 C++를 사용하여 Python 2.7 확장) 및 [Porting Extension Modules to Python 3](https://docs.python.org/2.7/howto/cporting.html)(확장 모듈을 Python 3에 이식) (python.org)을 참조하세요.

1. *module.cpp*의 맨 위에 *Python.h*를 포함시킵니다.

    ```cpp
    #include <Python.h>
    ```

1. Python 형식을 허용하고 반환하도록 `tanh_impl` 메서드를 수정합니다(즉, `PyOjbect*`).

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. C++ `tanh_impl` 함수가 Python에 표시되는 방식을 정의하는 구조체를 추가합니다.

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. 특히 `from...import` 문을 사용할 때 Python 코드에서 참조하려는 모듈을 정의하는 구조를 추가합니다. 이 항목이 **구성 속성** > **일반** > **대상 이름** 아래의 프로젝트 속성 값과 일치하도록 합니다. 다음 예제에서 "superfastcode" 모듈 이름은 Python에서 `from superfastcode import fast_tanh`를 사용할 수 있다는 뜻입니다. `fast_tanh`가 `superfastcode_methods` 안에 정의되었기 때문입니다. *module.cpp*와 같은 C++ 프로젝트 내부의 파일 이름은 중요하지 않습니다.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python에서 이름이 `PyInit_<module-name>`인 모듈을 로드할 때 호출하는 메서드를 추가합니다. 여기서 &lt;module-name&gt;은 C++ 프로젝트의 **일반** > **대상 이름** 속성과 정확하게 일치합니다. 즉, 프로젝트에서 빌드된 *.pyd*의 파일 이름과 일치합니다.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. 대상 구성을 **릴리스**로 설정하고 C++ 프로젝트를 다시 빌드하여 코드를 확인합니다. 오류가 발생할 경우 아래의 [문제 해결](#troubleshooting) 섹션을 참조하세요.

### <a name="pybind11"></a>PyBind11

이전 섹션에서 단계를 완료한 경우 C++ 코드에 필요한 모듈 구조체를 만들기 위해 많은 상용구 코드를 사용했음을 알 수 있습니다. PyBind11에서는 C++ 헤더 파일에서 훨씬 적은 코드를 사용하여 동일한 결과를 달성하는 매크로를 통해 프로세스를 간소화합니다. 이 섹션에 나온 배경 지식은 [PyBind11 기본](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)(github.com)을 참조하세요.

1. pip(`pip install pybind11` 또는 `py -m pip install pybind11`)를 사용하여 PyBind11을 설치합니다.

1. *module.cpp*의 맨 위에 *pybind11.h*를 포함시킵니다.

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. *module.cpp*의 맨 아래에서 `PYBIND11_MODULE` 매크로를 사용하여 C++ 함수에 대한 진입점을 정의합니다.

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

1. 대상 구성을 **릴리스**로 설정하고 C++ 프로젝트를 빌드하여 코드를 확인합니다. 오류가 발생할 경우 다음의 문제 해결 섹션을 참조하세요.

### <a name="troubleshooting"></a>문제 해결

C++ 모듈은 다음과 같은 이유로 컴파일에 실패할 수 있습니다.

- *Python.h*를 찾을 수 없음(**E1696: 원본 파일 "Python.h"**  및/또는 **C1083: 포함 파일을 열 수 없습니다. "Python.h": 해당 파일 또는 디렉터리 없음**): 프로젝트 속성에서 **C/C++**  > **일반** > **추가 포함 디렉터리**의 경로가 Python 설치의 *include* 폴더를 가리키는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- Python 라이브러리를 찾을 수 없음: 프로젝트 속성에서 **링커** > **일반** > **추가 라이브러리 디렉터리**의 경로가 Python 설치의 *libs* 폴더를 가리키는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- 대상 아키텍처와 관련된 링커 오류: C++ 대상 프로젝트 아키텍처를 Python 설치에 맞게 변경합니다. 예를 들어 C++ 프로젝트에서 x64를 대상으로 지정하지만 Python 설치가 x86인 경우 C++ 프로젝트를 변경하여 x86을 대상으로 지정합니다.

## <a name="test-the-code-and-compare-the-results"></a>코드를 테스트하고 결과 비교

DLL을 Python 확장으로 구조화했으므로 Python 프로젝트에서 이를 참조하고, 모듈을 가져오고, 해당 메서드를 사용할 수 있습니다.

### <a name="make-the-dll-available-to-python"></a>Python에서 DLL을 사용할 수 있도록 설정

Python에서 DLL을 사용할 수 있도록 설정하는 방법은 두 가지가 있습니다.

Python 프로젝트와 C++ 프로젝트가 같은 솔루션에 있는 경우 첫 번째 방법을 사용할 수 있습니다. **솔루션 탐색기**로 이동하여 Python 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭한 다음, **참조 추가**를 선택합니다. 표시되는 대화 상자에서 **프로젝트** 탭을 선택하고 **superfastcode**와 **superfastcode2** 프로젝트를 모두 선택한 다음, **확인**을 선택합니다.

![superfastcode 프로젝트에 참조 추가](media/cpp-add-reference.png)

다음 단계에 설명된 두 번째 방법은 다른 Python 프로젝트에서도 사용 가능하도록 모듈을 전역 Python 환경에 설치합니다. (이 경우 Visual Studio 2017 버전 15.5 및 이전 버전에서는 일반적으로 해당 환경에 대한 IntelliSense 완성 데이터베이스를 새로 고쳐야 합니다. 환경에서 모듈을 제거하는 경우에도 새로 고침이 필요합니다.)

1. Visual Studio 2017 이상을 사용하고 있는 경우 Visual Studio 설치 관리자를 실행하고 **수정**을 선택한 다음, **개별 구성 요소** > **컴파일러, 빌드 도구 및 런타임** > **Visual C++ 2015.3 v140 도구 집합**을 선택합니다. 이 단계가 필요한 이유는 Python(Windows용) 자체는 Visual Studio 2015(버전 14.0)로 빌드되며 여기에 설명된 메서드를 통해 확장을 빌드할 경우 이러한 도구를 사용할 수 있다고 예상하기 때문입니다. (Python의 32비트 버전을 설치하고 DLL 대상을 x64가 아닌 Win32로 지정해야 할 수 있습니다.)

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택하여 C++ 프로젝트에서 *setup.py*라는 파일을 만듭니다. 그런 다음, **C++ 파일(.cpp)** 을 선택하고 파일 이름을 `setup.py`로 변경한 다음, **확인**을 선택합니다( *.py* 확장명을 사용하여 파일 이름을 지정하면 C++ 파일 템플릿을 사용해도 Visual Studio에서 Python으로 인식함). 편집기에 파일이 표시되면 확장 메서드에 적절하게 다음 코드를 붙여넣습니다.

    **CPython 확장(superfastcode 프로젝트):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    이 스크립트에 대한 설명서는 [C 및 C++ 확장 빌드](https://docs.python.org/3/extending/building.html)(python.org)를 참조하세요.

    **PyBind11(superfastcode2 프로젝트):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. *setup.py* 코드는 명령줄에서 사용되는 경우 Visual Studio 2015 C++ 도구 집합을 사용하여 확장을 빌드하도록 Python에 지시합니다. 관리자 권한 명령 프롬프트를 열고 C++ 프로젝트를 포함하는 폴더(즉, *setup.py*를 포함하는 폴더)로 이동한 후 다음 명령을 입력합니다.

    ```command
    pip install .
    ```

    또는

    ```command
    py -m pip install .
    ```

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

    **디버깅하지 않고 시작** 명령이 비활성화된 경우 **솔루션 탐색기**에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

1. 차이가 더 분명해지도록 `COUNT` 변수를 늘려 보세요. 또한 **디버그** 빌드는 덜 최적화되고 다양한 오류 검사를 포함하기 때문에 C++ 모듈의 **디버그** 빌드가 **릴리스** 빌드보다 더 느리게 실행됩니다. 그러한 구성을 자유롭게 전환하여 비교해 보세요.

> [!NOTE]
> 출력에서 보면 직접 Python 구현하는 것보다는 훨씬 빠르지만 PyBind11 확장이 CPython 확장 만큼 빠르지 않음을 알 수 있습니다. 해당 C++ 인터페이스를 더 간단하게 만들기 위해 PyBind11에서 도입한 호출당 오버헤드의 양이 적기 때문에 차이가 발생합니다. 이 호출별 차이점은 실제로는 상당히 미미합니다. 여기에 표시된 결과는 테스트 코드가 확장 함수를 500,000번 호출하기 때문에 오버헤드를 크게 확대합니다. 일반적으로 C++ 함수는 여기에서 사용된 간단한 `fast_tanh[2]` 메서드보다 훨씬 많은 작업을 수행하므로 오버헤드가 발생해도 중요하지 않습니다. 그러나 초당 수천 번 호출될 수 있는 메서드를 구현하는 경우 CPython 방식을 사용하면PyBind11보다 성능이 향상될 수 있습니다.

## <a name="debug-the-c-code"></a>C++ 코드 디버그

Visual Studio는 디버깅 Python 및 C++ 코드를 함께 지원합니다. 이 섹션에서는 **superfastcode** 프로젝트를 사용하여 프로세스를 설명하며, 단계는 **superfastcode2** 프로젝트에서도 동일합니다.

1. **솔루션 탐색기**에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**, **디버그** 탭을 차례로 선택한 다음, **디버그** > **네이티브 코드 디버깅 사용** 옵션을 선택합니다.

    > [!Tip]
    > 네이티브 코드 디버깅을 사용하면 프로그램이 완료되었을 때 일반적인 **계속하려면 아무 키나 누르세요.** 일시 중지를 제공하지 않고 Python 출력 창이 바로 사라질 수 있습니다. 강제로 일시 중지하려면 네이티브 코드 디버깅을 사용할 때 **디버그** 탭의 **실행** > **인터프리터 인수** 필드에 `-i` 옵션을 추가합니다. 이 인수는 코드가 마무리된 후에 Python 인터프리터를 대화형 모드로 전환하며, 이때 **Ctrl**+**Z** > **Enter** 키를 눌러 종료할 때까지 대기합니다. 또는 Python 코드를 수정하지 않으려면 프로그램의 끝에 `import os` 및 `os.system("pause")` 문을 추가할 수 있습니다. 이 코드는 원래 일시 중지 프롬프트를 복제합니다.

1. **파일** > **저장**을 선택하여 속성 변경 내용을 저장합니다.

1. Visual Studio 도구 모음에서 빌드 구성을 **디버그**로 설정합니다.

    ![빌드 구성을 디버그로 설정](media/cpp-set-debug.png)

1. 일반적으로 디버거에서 코드를 실행하는 데 더 많은 시간이 걸리기 때문에 *.py* 파일의 `COUNT` 변수를 약 5배 작은 값으로 변경하는 것이 좋습니다(예: `500000`에서 `100000`으로 변경).

1. C++ 코드에서는 `tanh_impl` 메서드의 첫 줄에 중단점을 설정한 다음 디버거를 시작합니다(**F5** 또는 **디버그** > **디버깅 시작**). 해당 코드가 호출되면 디버거가 중지합니다. 중단점이 적중되지 않는 경우 구성이 **디버그**로 설정되어 있는지, 프로젝트를 저장했는지 확인합니다(디버거를 시작할 때 자동으로 수행되지 않음).

    ![C++ 코드의 중단점에서 중지](media/cpp-debugging.png)

1. 이때 C++ 코드를 단계별로 실행하고 변수를 검사하는 등의 작업을 수행할 수 있습니다. 이러한 기능은 [C++ 및 Python 디버그](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)에 자세히 설명되어 있습니다.

## <a name="alternative-approaches"></a>대체 방법

아래 표에 설명된 대로 다른 방법으로 Python 확장을 만들 수 있습니다. CPython 및 PyBind11에 대한 처음 두 항목은 이 문서에서 이미 설명했습니다.

| 방법 | 연도 | 담당자 | 장점 | 단점 |
| --- | --- | --- | --- | --- |
| CPython용 C/C++ 확장 모듈 | 1991 | 표준 라이브러리 | [광범위한 설명서 및 자습서](https://docs.python.org/3/c-api/). 전체 제어. | 컴파일, 이식성, 참조 관리. 높은 C 지식. |
| [PyBind11](https://github.com/pybind/pybind11)(C++에 권장됨) | 2015 |  | 기존 C++ 코드의 Python 바인딩을 만드는 간단한 헤더 전용 라이브러리. 약간의 종속성. PyPy 호환성. | 더 새롭고 완성도 낮음. C++11 기능 사용 빈도 높음. 몇 가지 지원되는 컴파일러(Visual Studio 포함). |
| Cython(C에 권장됨) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python과 유사. 높은 완성도. 고성능. | 컴파일, 새 구문 및 새 도구 체인. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | 모든 C++ 컴파일러와 작동. | 대규모의 복잡한 라이브러리 모음으로 이전 컴파일러에 대한 많은 대안을 포함. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 컴파일 안 함, 광범위한 가용성. | 번거로운 C 구조체 액세스 및 변경과 오류 발생 가능성. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 한 번에 여러 언어에 대한 바인딩 생성. | Python이 유일한 대상일 경우 과도한 오버헤드. |
| cffi | 2013 | [cryptography](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | 간편한 통합, PyPy 호환성. | 더 새롭고 완성도 낮음. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | C++를 사용한 cffi와 유사합니다. | 최신 기능이며, VS 2017에서는 몇 가지 문제가 발생할 수 있습니다. |

## <a name="see-also"></a>참조

이 연습에서 완료된 샘플은 [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension)(GitHub)에서 찾을 수 있습니다.
