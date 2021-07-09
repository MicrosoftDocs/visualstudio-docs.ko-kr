---
title: Python용 C++ 확장명 작성
description: 이 문서에서는 혼합 모드 디버깅을 비롯하여 Visual Studio, CPython, PyBind11을 사용하여 Python용 C++ 확장을 만드는 방법을 안내합니다.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973442"
---
# <a name="create-a-c-extension-for-python"></a>Python용 C++ 확장 만들기

C++(또는 C)로 작성된 모듈은 Python 인터프리터의 기능을 확장하는 데 일반적으로 사용됩니다. 또한 하위 수준 운영 체제 기능에 액세스할 수 있도록 설정하는 데도 사용됩니다. 

모듈은 다음과 같은 세 가지 기본 형식으로 제공됩니다.

- **가속기 모듈**: Python은 해석된 언어이기 때문에 성능 향상을 위해 C++로 가속기 모듈을 작성할 수 있습니다.
- **래퍼 모듈**: 이러한 모듈은 기존 C/C++ 인터페이스를 Python 코드에 노출하거나 Python에서 사용하기 쉬운 보다 “Python” 최적화된 API를 노출합니다.
- **하위 수준 시스템 액세스 모듈**: `CPython` 런타임, 운영 체제, 기본 하드웨어의 하위 수준 기능에 액세스하도록 이러한 모듈을 만들 수 있습니다.

이 문서에서는 쌍곡 탄젠트를 계산하고 Python 코드에서 호출하는 `CPython`용 C++ 확장 모듈을 빌드하는 방법을 안내합니다. C++에서 동일한 루틴을 구현할 경우의 관련된 성능 향상을 보여 주기 위해 Python에서 먼저 루틴을 구현합니다.

이 문서에서는 Python에서 C++ 확장을 사용할 수 있도록 하는 두 가지 방법도 보여 줍니다.

- [Python 설명서](https://docs.python.org/3/c-api/)에 설명된 표준 `CPython` 확장을 사용합니다.
- 단순성 때문에 C++11에 권장되는 [PyBind11](https://github.com/pybind/pybind11)을 사용합니다.

이 연습에서 완성된 샘플은 GitHub([python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension))에서 찾을 수 있습니다.

## <a name="prerequisites"></a>필수 조건

- Python 개발 워크로드가 설치된 Visual Studio 2017 이상. 워크로드에는 네이티브 확장에 필요한 C++ 워크로드 및 도구 집합을 제공하는 Python 네이티브 개발 도구가 포함되어 있습니다.

    ![Python 네이티브 개발 도구 옵션이 강조 표시된 Python 개발 옵션 목록의 스크린샷](media/cpp-install-native.png)

    > [!NOTE]
    > **데이터 과학 및 분석 애플리케이션** 워크로드를 설치하면 Python 및 **Python 네이티브 개발 도구** 옵션이 기본적으로 설치됩니다.

설치 옵션에 대한 자세한 내용은 [Visual Studio용 Python 지원 설치](installing-python-support-in-visual-studio.md)를 참조하세요. Python을 별도로 설치하는 경우 설치 관리자의 **고급 옵션** 에서 **디버깅 기호 다운로드** 를 선택해야 합니다. 이 옵션은 Python 코드와 네이티브 코드 간에 혼합 모드 디버깅을 사용하는 데 필요합니다.

## <a name="create-the-python-application"></a>Python 애플리케이션 만들기

1. **파일** > **새로 만들기** > **프로젝트** 를 선택하여 Visual Studio에서 새 Python 프로젝트를 만듭니다. **Python** 을 검색하고 **Python 애플리케이션** 템플릿을 선택한 다음, 이름과 위치를 입력하고 **확인** 을 선택합니다.

1. 프로젝트의 *.py* 파일에서 다음 코드를 붙여넣습니다. [Python 편집 기능](editing-python-code-in-visual-studio.md)의 일부를 경험하려면 코드를 수동으로 입력해 보세요.  

   이 코드는 수학 라이브러리를 사용하지 않고 쌍곡 탄젠트를 계산하며, 네이티브 확장을 사용하여 가속화됩니다.

    > [!Tip]
    > 코드는 순수 Python에서 작성한 후에 C++로 다시 작성하세요. 이렇게 하면 네이티브 코드가 올바른지 더 쉽게 확인할 수 있습니다.

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

1. 결과를 보려면 **디버그** > **디버깅하지 않고 시작** 을 선택하거나 Ctrl+F5를 선택하여 프로그램을 실행합니다. 

   `COUNT` 변수를 조정하여 벤치 마크를 실행할 시간을 변경할 수 있습니다. 이 연습에서는 벤치마크에 약 2초 정도 걸리도록 개수를 설정합니다.

   > [!TIP]
   > 벤치마크를 실행할 때는 항상 **디버그** > **디버깅하지 않고 시작** 을 사용합니다. 그러면 Visual Studio 디버거 내에서 코드를 실행할 때 발생하는 오버헤드를 방지할 수 있습니다.

## <a name="create-the-core-c-projects"></a>핵심 C++ 프로젝트 만들기

이 섹션의 지침에 따라 두 개의 동일한 C++ 프로젝트 *superfastcode* 와 *superfastcode2* 를 만듭니다. 나중에 각 프로젝트에서 서로 다른 방법을 사용하여 Python에 C++ 코드를 노출합니다.

1. **솔루션 탐색기** 에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트** 를 선택합니다. Visual Studio 솔루션에는 Python과 C++ 프로젝트 둘 다 포함될 수 있으며, 이는 Python용 Visual Studio를 사용하는 장점 중 하나입니다.

1. **C++** 에서 검색하고 **빈 프로젝트** 를 선택한 다음, 첫 번째 프로젝트에는 **superfastcode** 를, 두 번째 프로젝트에는 **superfastcode2** 를 지정하고 **확인** 을 선택합니다.

    > [!Tip]
    > 또는 Visual Studio에 설치된 Python 네이티브 개발 도구를 사용하여 Python 확장 모듈 템플릿으로 시작할 수 있습니다. 템플릿에는 여기에 설명된 내용이 이미 많이 포함되어 있습니다. 
    > 
    > 그러나 이 연습에서는 빈 프로젝트로 시작하여 확장 모듈 빌드를 단계별로 보여 줍니다. 프로세스를 이해한 후에는 직접 확장을 작성할 때 템플릿을 사용하여 시간을 절약할 수 있습니다.

1. 새 프로젝트에서 C++ 파일을 만들려면 **소스 파일** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** 을 선택합니다.

1. **C++ 파일** 을 선택하고 *module.cpp* 로 이름을 지정한 다음, **확인** 을 선택합니다.

    > [!Important]
    > 이어지는 다음 단계에서 C++ 속성 페이지를 켜려면 *.cpp* 확장명을 가진 파일이 필요합니다.

1. 주 도구 모음에서 드롭다운 메뉴를 사용하여 다음 중 하나를 수행합니다.

   * 64비트 Python 런타임의 경우 **x64** 구성을 활성화합니다. 
   * 32비트 Python 런타임의 경우 **Win32** 구성을 활성화합니다.

1. **솔루션 탐색기** 에서 C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택한 후 다음을 수행합니다. 

   a. **구성** 에 **활성(디버그)** 을 입력합니다.  
   b. 이전 단계에서 선택한 항목에 따라 **플랫폼** 에 **활성(x64)** 또는 **활성(Win32)** 을 입력합니다.

    > [!NOTE]
    > 직접 프로젝트를 만드는 경우 ‘디버그’ 및 ‘릴리스’ 구성을 모두 구성하는 것이 좋습니다.  이 단원에서는 디버그 구성만 구성하고 CPython의 릴리스 빌드를 사용하도록 설정합니다. 이 구성은 어설션을 포함하여 C++ 런타임의 일부 디버깅 기능을 사용하지 않도록 설정합니다. CPython 디버그 이진 파일(*python_d.exe*)을 사용하려면 다른 설정이 필요합니다.

1. 다음 표에 설명된 대로 속성을 설정합니다.

    ::: moniker range=">=vs-2019"

    | 탭 | 속성 | 값 |
    | --- | --- | --- |
    | **일반** | **대상 이름** | Python의 `from...import` 문에서 참조하려는 모듈의 이름을 지정합니다. Python에 대한 모듈을 정의하는 경우 C++ 코드에서 이 동일한 이름을 사용합니다. 프로젝트의 이름을 모듈 이름으로 사용하려는 경우 기본값 **$\<ProjectName>** 을 그대로 둡니다.  `python_d.exe`의 경우 이름 끝에 `_d`를 추가합니다. |
    | | **구성 유형** | **동적 라이브러리(.dll)** |
    | | **고급** > **대상 파일 확장명** | **.pyd** |
    | | **프로젝트 기본값** > **구성 형식** | **동적 라이브러리(.dll)** |
    | **C/C++** > **일반** | **추가 포함 디렉터리** | 설치에 맞게 Python *include* 폴더를 추가합니다(예: `c:\Python36\include`).  |
    | **C/C++** > **전처리기** | **전처리기 정의** | 있을 경우 **_DEBUG** 값을 **NDEBUG** 로 변경하여 CPython의 디버그되지 않은 버전과 일치시킵니다. *python_d.exe* 를 사용하는 경우 이 값을 변경하지 않고 그대로 유지합니다. |
    | **C/C++** > **코드 생성** | **런타임 라이브러리** | CPython의 디버그되지 않은 버전과 일치시킬 **다중 스레드 DLL(/MD)** 입니다. *python_d.exe* 를 사용하는 경우 이 값을 **다중 스레드 디버그 DLL(/MDd)** 로 유지합니다. |
    | **링커** > **일반** | **추가 라이브러리 디렉터리** | 설치에 맞게 *.lib* 파일을 포함하는 Python *libs* 폴더를 추가합니다(예: *c:\Python36\libs*). *.py* 파일을 포함하는 *Lib* 폴더가 ‘아니라’ *.lib* 파일을 포함하는 *libs* 폴더를 가리켜야 합니다. |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | 탭 | 속성 | 값 |
    | --- | --- | --- |
    | **일반** | **일반** > **대상 이름** | Python의 `from...import` 문에서 참조하려는 모듈의 이름을 지정합니다. Python에 대한 모듈을 정의하는 경우 C++ 코드에서 이 동일한 이름을 사용합니다. 프로젝트의 이름을 모듈 이름으로 사용하려는 경우 기본값 **$\<ProjectName>** 을 그대로 둡니다. `python_d.exe`의 경우 이름 끝에 `_d`를 추가합니다. |
    | | **일반** > **대상 확장명** | **.pyd** |
    | | **프로젝트 기본값** > **구성 형식** | **동적 라이브러리(.dll)** |
    | **C/C++** > **일반** | **추가 포함 디렉터리** | 설치에 맞게 Python *include* 폴더를 추가합니다(예: *c:\Python36\include*).  |
    | **C/C++** > **전처리기** | **전처리기 정의** | 있을 경우 **_DEBUG** 값을 **NDEBUG** 로 변경하여 `CPython`의 디버그되지 않은 버전과 일치시킵니다. `python_d.exe`를 사용하는 경우 이 값을 변경하지 않고 그대로 유지합니다. |
    | **C/C++** > **코드 생성** | **런타임 라이브러리** | `CPython`의 디버그 이외 버전과 일치시키기 위한 **다중 스레드 DLL(/MD)** `python_d.exe`를 사용하는 경우 이 값을 변경하지 않고 그대로 유지합니다. |
    | **링커** > **일반** | **추가 라이브러리 디렉터리** | 설치에 맞게 *.lib* 파일을 포함하는 Python *libs* 폴더를 추가합니다(예: *c:\Python36\libs*). *.py* 파일을 포함하는 *Lib* 폴더가 ‘아니라’ *.lib* 파일을 포함하는 *libs* 폴더를 가리켜야 합니다. |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > **C/C++** 탭이 프로젝트 속성에 표시되지 않으면 프로젝트에 C/C++ 소스 파일로 식별되는 파일이 포함되어 있지 않은 것입니다. 이 상태는 *.c* 또는 *.cpp* 파일 확장명을 사용하지 않고 소스 파일을 만드는 경우에 발생할 수 있습니다. 
    > 
    > 예를 들어 이전의 새 항목 대화 상자에서 실수로 *module.cpp* 대신 *module.coo* 를 입력한 경우 Visual Studio는 파일을 만들지만 C/C++ 속성 탭을 활성화하는 *C/C+ 코드* 로 파일 형식을 설정하지 않습니다. 이러한 잘못된 식별 정보는 *.cpp* 파일 확장명을 사용하여 파일 이름을 바꾸는 경우에도 그대로 유지됩니다. 
    > 
    > 파일 형식을 제대로 설정하려면 **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다. 그런 다음, **파일 형식** 에서 **C/C++ 코드** 를 선택합니다.

1. **확인** 을 선택합니다.

1. 구성(‘디버그’ 및 ‘릴리스’)을 테스트하려면 C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **빌드** 를 선택합니다 . 

   *.pyd* 파일은 C++ 프로젝트 폴더 자체가 아니라 ‘디버그’ 및 ‘릴리스’ 아래의 *solution* 폴더에 있습니다. 

1. C++ 프로젝트의 *module.cpp* 파일에 다음 코드를 추가합니다.

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

1. 아직 수행하지 않았다면 위의 단계를 반복하여 동일한 구성으로 *superfastcode2* 라는 두 번째 프로젝트를 만듭니다.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>C++ 프로젝트를 Python용 확장으로 변환

C++ DLL을 Python용 확장으로 만들려면 먼저 내보낸 메서드를 Python 형식과 상호 작용하도록 수정합니다. 그런 다음 모듈의 메서드 정의와 함께 모듈을 내보내는 함수를 추가해야 합니다.

다음 섹션에서는 CPython 확장과 PyBind11을 사용하여 이러한 단계를 수행하는 방법에 대해 설명합니다.

### <a name="use-cpython-extensions"></a>CPython 확장 사용

이 섹션에 표시된 코드에 대한 자세한 배경 정보는 [Python/C API Reference Manual](https://docs.python.org/3/c-api/index.html)(Python/C API 참조 설명서) 및 특히 [Module Objects](https://docs.python.org/3/c-api/module.html)(모듈 개체) 페이지를 참조하세요. 오른쪽 위 드롭다운 목록에서 Python의 버전을 선택해야 합니다.

1. *module.cpp* 파일 맨 위에 *Python.h* 를 포함합니다.

    ```cpp
    #include <Python.h>
    ```

1. Python 형식(즉, `PyObject*`)을 허용하고 반환하도록 `tanh_impl` 메서드를 수정합니다.

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

1. 특히 `from...import` 문을 사용할 때 Python 코드에서 참조하려는 모듈을 정의하는 구조를 추가합니다. 

   이 코드에서 가져오는 이름은 **구성 속성** > **일반** > **대상 이름** 아래의 프로젝트 속성 값과 일치해야 합니다. 

   다음 예제에서 `"superfastcode"` 모듈 이름은 Python에서 `from superfastcode import fast_tanh`를 사용할 수 있음을 의미하는데, `fast_tanh`이 `superfastcode_methods` 내에 정의되어 있기 때문입니다. *module.cpp* 와 같이 C++ 프로젝트 내부에 있는 파일 이름은 중요하지 않습니다.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Python에서 이름이 `PyInit_<module-name>`인 모듈을 로드할 때 호출하는 메서드를 추가합니다. 여기서 *\<module-name>* 은 C++ 프로젝트의 **일반** > **대상 이름** 속성과 정확히 일치합니다. 즉, 프로젝트에서 빌드되는 *.pyd* 파일의 파일 이름과 일치합니다.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. C++ 프로젝트를 다시 빌드하여 코드를 확인합니다. 오류가 발생할 경우 [문제 해결](#troubleshoot-compiling-failures) 섹션을 참조하세요.

### <a name="use-pybind11"></a>PyBind11 사용

이전 섹션에서 단계를 완료한 경우 C++ 코드에 필요한 모듈 구조체를 만들기 위해 많은 상용구 코드를 사용했음을 알 수 있습니다. PyBind11은 C++ 헤더 파일에서 동일한 결과를 얻지만 훨씬 더 적은 코드를 사용하는 매크로를 통해 프로세스를 간소화합니다. 

이 섹션의 코드에 대한 자세한 내용은 [PyBind11 basics](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)(PyBind11 기본 사항)를 참조하세요.

1. pip(`pip install pybind11` 또는 `py -m pip install pybind11`)를 사용하여 PyBind11을 설치합니다. 

   또는 Python 환경 창을 사용하여 PyBind11을 설치하고 다음 단계에서 **PowerShell에서 열기** 명령을 사용할 수 있습니다.

1. 동일한 터미널에서 `python -m pybind11 --includes` 또는 `py -m pybind11 --includes`를 실행합니다. 

   그러면 프로젝트의 **C/C++**  > **일반** > **추가 포함 디렉터리** 속성에 추가해야 하는 경로 목록이 출력됩니다. `-I` 접두사가 있으면 제거해야 합니다.

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

1. C++ 프로젝트를 빌드하여 코드를 확인합니다. 오류가 발생하는 경우 다음의 솔루션에 대한 “컴파일 오류 문제 해결” 섹션을 참조하세요.

### <a name="troubleshoot-compiling-failures"></a>컴파일 오류 문제 해결

C++ 모듈은 다음과 같은 이유로 컴파일되지 않을 수 있습니다.

- 오류: *Python.h* 를 찾을 수 없습니다(**E1696: “Python.h” 소스 파일을 열 수 없습니다.** 및/또는 **C1083: 포함 파일을 열 수 없습니다. “Python.h” 해당 파일 또는 디렉터리가 없습니다.** ) 

  해결 방법: 프로젝트 속성에서 **C/C++**  > **일반** > **추가 포함 디렉터리** 의 경로가 Python 설치의 *include* 폴더를 가리키는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- 오류: Python 라이브러리를 찾을 수 없습니다. 
 
   해결 방법: 프로젝트 속성에서 **링커** > **일반** > **추가 라이브러리 디렉터리** 의 경로가 Python 설치의 *libs* 폴더를 가리키는지 확인합니다. [핵심 C++ 프로젝트 만들기](#create-the-core-c-projects)의 6단계를 참조하세요.

- 대상 아키텍처와 관련된 링커 오류
   
   해결 방법: C++ 대상의 프로젝트 아키텍처를 Python 설치에 맞게 변경합니다. 예를 들어 C++ 프로젝트에서 Win32를 대상으로 지정하지만 Python 설치가 64비트인 경우, C++ 프로젝트를 x64로 변경합니다.

## <a name="test-the-code-and-compare-the-results"></a>코드를 테스트하고 결과 비교

DLL을 Python 확장으로 구조화했으므로 Python 프로젝트에서 이를 참조하고, 모듈을 가져오고, 해당 메서드를 사용할 수 있습니다.

### <a name="make-the-dll-available-to-python"></a>Python에서 DLL을 사용할 수 있도록 설정

여러 가지 방법으로 Python에서 DLL을 사용할 수 있도록 설정할 수 있습니다. 다음과 같은 두 가지 방법을 고려할 수 있습니다. 

* 첫 번째 방법은 Python 프로젝트와 C++ 프로젝트가 같은 솔루션에 있는 경우에 적용됩니다. 다음을 수행합니다. 

   1. **솔루션 탐색기** 에서 Python 프로젝트의 **참조** 노드를 마우스 오른쪽 단추로 클릭한 다음, **참조 추가** 를 선택합니다. 
   1. 표시되는 대화 상자에서 **프로젝트** 탭을 선택하고 **superfastcode** 와 **superfastcode2** 프로젝트를 모두 선택한 다음, **확인** 을 선택합니다.

      ![“superfastcode” 프로젝트에 참조를 추가하는 방법을 보여 주는 스크린샷](media/cpp-add-reference.png)

* 대체 방법에서는 Python 환경에 모듈을 설치하여 다른 Python 프로젝트에서도 모듈을 사용할 수 있도록 합니다. 자세한 내용은 [**setuptools** 프로젝트 설명서](https://setuptools.readthedocs.io/)를 참조하세요. 다음을 수행합니다.

    1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** 을 선택하여 C++ 프로젝트에서 *setup.py* 라는 파일을 만듭니다. 
    
    1. **C++ 파일(.cpp)** 을 선택하고 파일 이름을 *setup.py* 로 지정한 다음, **확인** 을 선택합니다.
    
       *.py* 확장명을 사용하여 파일 이름을 지정하면 C++ 파일 템플릿을 사용하더라도 Visual Studio에서 Python 파일로 인식합니다. 

       파일이 편집기에 표시되면 확장 메서드에 맞게 다음 코드를 붙여넣습니다.
    
        **`CPython` 확장(superfastcode 프로젝트)의 경우**:
    
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
    
        **`PyBind11`(superfastcode2 프로젝트)의 경우**:
    
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
    
    1. 확장을 빌드하려면 열려 있는 *pyproject.toml* 탭을 마우스 오른쪽 단추로 클릭하고 **전체 경로 복사** 를 선택합니다. 경로에서 *pyproject.toml* 이름을 삭제한 후에 사용합니다.
    
    1. **솔루션 탐색기** 에서 활성 Python 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 관리** 를 선택합니다.
    
        > [!Tip]
        > 패키지를 이미 설치한 경우에는 여기에 나열됩니다. 계속하려면 **X** 를 클릭하여 제거합니다.
    
    1. 검색 상자에 복사한 경로를 붙여넣고 끝에서 *pyproject.toml* 을 삭제한 다음, Enter 키를 선택하여 해당 디렉터리에서 모듈을 설치합니다.
    
        > [!Tip]
        > 권한 오류가 발생하여 설치가 실패하는 경우 끝에 *--user* 를 추가하고 명령을 다시 시도합니다.


### <a name="call-the-dll-from-python"></a>Python에서 DLL 호출

이전 섹션에서 설명한 대로 Python에서 DLL을 사용할 수 있도록 설정했으면 Python 코드에서 `superfastcode.fast_tanh` 및 `superfastcode2.fast_tanh2` 함수를 호출하여 Python 구현과 성능을 비교할 수 있습니다. DLL을 호출하려면 다음을 수행합니다.

1. *.py* 파일에 다음 줄을 추가하여 DLL에서 가져온 메서드를 호출하고 출력을 표시합니다.

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. **디버그** > **디버깅하지 않고 시작** 을 선택하거나 Ctrl+F5를 선택하여 Python 프로그램을 실행합니다.

    > [!NOTE]
    > **디버깅하지 않고 시작** 명령이 비활성화된 경우 **솔루션 탐색기** 에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정** 을 선택합니다.  

    C++ 루틴이 Python 구현보다 대략 5~20배 빠르게 실행되는지 확인합니다. 일반적인 출력은 다음과 같습니다.

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. 차이가 더 분명해지도록 `COUNT` 변수를 늘려 보세요. 

    또한 디버그 빌드는 최적화 수준이 낮고 다양한 오류 검사를 포함하기 때문에 C++ 모듈의 ‘디버그’ 빌드가 ‘릴리스’ 빌드보다 더 느리게 실행됩니다.  언제든지 구성을 전환하여 비교할 수 있지만 릴리스 구성의 경우 앞에서 설정한 속성으로 돌아가 업데이트해야 합니다.

출력에서 보면 PyBind11 확장이 CPython 확장만큼 빠르지 않지만 순수 Python 구현보다는 훨씬 더 빠릅니다. 이러한 차이는 주로 여러 매개 변수, 매개 변수 이름, 키워드 인수를 지원하지 않는 `METH_O` 호출을 사용했기 때문에 발생합니다. PyBind11은 약간 더 복잡한 코드를 생성하여 호출자에게 Python과 더 유사한 인터페이스를 제공합니다. 그러나 테스트 코드는 함수를 500,000번 호출하므로 결과적으로 오버헤드가 더 커질 수 있습니다.

`for` 루프를 네이티브 코드로 이동하여 오버헤드를 더 줄일 수 있습니다. 이 방법에서는 [반복기 프로토콜](https://docs.python.org/c-api/iter.html)(또는 [함수 매개 변수](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)에 대한 PyBind11 `py::iterable` 형식)을 사용하여 각 요소를 처리합니다. Python과 C++ 사이에서 반복되는 전환을 제거하면 시퀀스를 처리하는 데 걸리는 시간을 효과적으로 줄일 수 있습니다.

### <a name="troubleshoot-importing-errors"></a>가져오기 오류 문제 해결

모듈을 가져오려고 할 때 `ImportError` 메시지가 표시되면 다음 방법 중 하나로 해결할 수 있습니다.

* 프로젝트 참조를 통해 빌드하는 경우에는 C++ 프로젝트 속성이 Python 프로젝트에 대해 활성화되는 Python 환경, 특히 *Include* 및 *Library* 디렉터리와 일치하는지 확인합니다.

* 출력 파일의 이름이 *superfastcode.pyd* 인지 확인합니다. 다른 이름이나 확장명을 사용하면 가져올 수 없습니다.

* *setup.py* 파일을 사용하여 모듈을 설치한 경우에는 Python 프로젝트에 대해 활성화되는 Python 환경에서 *pip* 명령을 실행했는지 확인합니다. 솔루션 탐색기에서 Python 환경을 확장하면 *superfastcode* 에 대한 항목이 표시됩니다.

## <a name="debug-the-c-code"></a>C++ 코드 디버그

Visual Studio는 디버깅 Python 및 C++ 코드를 함께 지원합니다. 이 섹션에서는 *superfastcode* 프로젝트를 사용하여 프로세스를 안내합니다. 이 프로세스는 *superfastcode2* 프로젝트에도 동일하게 적용됩니다.

1. **솔루션 탐색기** 에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**, **디버그** 탭을 차례로 선택한 다음, **디버그** > **네이티브 코드 디버깅 사용** 옵션을 선택합니다.

    > [!Tip]
    > 네이티브 코드 디버깅을 사용하면 프로그램이 완료된 후 일반적인 **계속하려면 아무 키나 누르세요.** 일시 중지를 제공하지 않고 Python 출력 창이 바로 닫힐 수 있습니다. 
    >
    > 해결 방법: 네이티브 코드 디버깅을 사용하도록 설정한 후 강제로 일시 중지하려면 **디버그** 탭의 **실행** > **인터프리터 인수** 필드에 `-i` 옵션을 추가하세요. 이 인수는 코드가 실행된 후 Python 인터프리터를 대화형 모드로 전환하며, 이때 Ctrl+Z를 선택한 다음, Enter 키를 선택하여 창을 닫을 때까지 기다립니다. 
    >
    > 또는 Python 코드를 수정하지 않으려면 프로그램의 끝에 `import os` 및 `os.system("pause")` 문을 추가할 수 있습니다. 이 코드는 원본 일시 중지 프롬프트를 복제합니다.

1. **파일** > **저장** 을 선택하여 속성 변경 내용을 저장합니다.

1. Visual Studio 도구 모음에서 빌드 구성을 **디버그** 로 설정합니다.

    ![Visual Studio 도구 모음의 “디버그” 설정 스크린샷](media/cpp-set-debug.png)

1. 일반적으로 디버거에서 코드를 실행하는 데 더 많은 시간이 걸리기 때문에 *.py* 파일의 `COUNT` 변수를 기본값보다 약 5배 작은 값으로 변경하는 것이 좋습니다. 예를 들어 **500000** 에서 **100000** 으로 변경합니다.

1. C++ 코드에서는 `tanh_impl` 메서드의 첫 줄에서 중단점을 설정한 다음, **F5** 키 또는 **디버그** > **디버깅 시작** 을 선택하여 디버거를 시작합니다. 

    디버거는 중단점 코드가 호출되면 중지합니다. 중단점이 적중되지 않으면 구성이 **디버그** 로 설정되어 있는지, 프로젝트를 저장했는지 확인합니다. 이 작업은 디버거를 시작할 때 자동으로 수행되지 않습니다.

    ![중단점이 포함된 C++ 코드의 스크린샷](media/cpp-debugging.png)

1. 중단점에서 C++ 코드를 단계별로 실행하고 변수를 검사하는 등의 작업을 수행할 수 있습니다. 이러한 기능에 대한 자세한 내용은 [Python과 C++ 함께 디버그](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)를 참조하세요.

## <a name="alternative-approaches"></a>대체 방법

다음 표에 설명된 다양한 방법으로 Python 확장을 만들 수 있습니다. 이 문서에서는 처음 두 행인 `CPython` 및 `PyBind11`에 대해 설명합니다.

| 접근 방식 | Vintage | 대표적인 사용 대상 | 
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

이 연습에서 완성된 샘플은 GitHub([python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension))에서 찾을 수 있습니다.
