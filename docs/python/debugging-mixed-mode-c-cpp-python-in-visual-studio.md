---
title: Python에 대한 혼합 모드 디버깅
description: 환경 간의 단계별 실행, 값 보기 및 식 계산을 포함하여 Visual Studio에서 C++ 및 Python을 동시에 디버그합니다.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bc90d659a32c14f92e1eff058dd22d4a17d0b1cb
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/06/2020
ms.locfileid: "75679002"
---
# <a name="debug-python-and-c-together"></a>Python과 C++ 함께 디버그

대부분의 일반 Python 디버거는 Python 코드만 디버그할 수 있습니다. 그러나 실제로 Python은 고성능 또는 플랫폼 API를 직접 호출하는 기능이 필요한 시나리오에서 C 또는 C++와 함께 사용됩니다. (연습은 [Python용 C++ 확장 만들기](working-with-c-cpp-python-in-visual-studio.md)를 참조하세요.)

Visual Studio에서는 Python 및 네이티브 C/C++에 대한 통합된 동시 혼합 모드 디버깅을 제공합니다. Visual Studio 설치 관리자에서 **Python 개발** 작업에 대해 **Python 네이티브 개발 도구** 옵션을 선택합니다.

> [!Note]
> 혼합 모드 디버깅은 Visual Studio 2015 및 이전 버전의 Visual Studio용 Python 도구 1.x 에서 사용할 수 없습니다.

이 문서에 설명된 대로 혼합 모드 디버깅 기능에는 다음 항목이 포함됩니다.

- 결합된 호출 스택
- Python 코드와 네이티브 코드 간 단계
- 두 가지 코드 형식의 중단점
- 네이티브 프레임에서 개체의 Python 표현과 Python 프레임에서 개체의 네이티브 표현 보기
- Python 프로젝트 또는 C++ 프로젝트의 컨텍스트 내에서 디버깅

![Visual Studio에서 Python에 대한 혼합 모드 디버깅](media/mixed-mode-debugging.png)

|   |   |
|---|---|
| ![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 시청") | Visual Studio로 네이티브 C 모듈을 빌드, 테스트 및 디버그하는 방법에 대한 소개는 [심층 분석: 네이티브 모듈 만들기](https://youtu.be/D9RlT06a1EI) (youtube.com, 9분 09초)를 시청하세요. 이 동영상은 Visual Studio 2015 및 2017 모두에 적용됩니다. |

## <a name="enable-mixed-mode-debugging-in-a-python-project"></a>Python 프로젝트에서 혼합 모드 디버깅 사용

1. **솔루션 탐색기**에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고, **속성**, **디버그** 탭을 차례로 선택한 다음, **네이티브 코드 디버깅 사용**을 선택합니다. 이 옵션을 사용하면 모든 디버깅 세션에서 혼합 모드를 사용할 수 있습니다.

    ![네이티브 코드 디버깅 사용](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]
    > 네이티브 코드 디버깅을 사용하면 프로그램이 완료되었을 때 일반적인 **계속하려면 아무 키나 누르세요.** 일시 중지를 제공하지 않고 Python 출력 창이 바로 사라질 수 있습니다. 강제로 일시 중지하려면 네이티브 코드 디버깅을 사용할 때 **디버그** 탭의 **실행** > **인터프리터 인수** 필드에 `-i` 옵션을 추가합니다. 이 인수는 코드가 마무리된 후에 Python 인터프리터를 대화형 모드로 전환하며, 이때 **Ctrl**+**Z** > **Enter** 키를 눌러 종료할 때까지 대기합니다.

1. 혼합 모드 디버거를 기존 프로세스에 연결하는 경우(**디버그** > **프로세스에 연결**), **선택** 단추를 사용하여 **코드 형식 선택** 대화 상자를 엽니다. 그런 후 **다음 코드 형식 디버깅** 옵션을 설정하고 목록에서 **네이티브** 및 **Python**을 모두 선택합니다.

    ![네이티브 및 Python 코드 형식 선택](media/mixed-mode-debugging-code-type.png)

    코드 형식 설정은 영구적이므로 나중에 다른 프로세스에 연결할 때 혼합 모드 디버깅을 사용하지 않으려면 **Python** 코드 형식의 선택을 취소합니다.

    **네이티브**에 추가하거나 대신하여 다른 코드 형식을 선택할 수 있습니다. 예를 들어 관리되는 애플리케이션에서 CPython을 호스트하고, 그 결과로 네이티브 확장 모듈을 사용하며, 이 세 가지를 모두 디버그하려는 경우 결합된 호출 스택 및 세 가지 모두의 런타임 간 단계별 실행을 포함한 통합된 디버깅 환경을 위해 **Python**, **네이티브** 및 **관리되는 애플리케이션**을 모두 검사할 수 있습니다.

1. 처음으로 혼합 모드에서 디버깅을 시작하면 **Python 기호 필요** 대화 상자가 표시될 수 있습니다([혼합 모드 디버깅 기호](debugging-symbols-for-mixed-mode-c-cpp-python.md) 참조). 기호는 지정된 Python 환경에 한 번만 설치해야 합니다. Visual Studio 설치 관리자(Visual Studio 2017 이상)를 통해 Python 지원을 설치하면 기호가 자동으로 포함됩니다.

1. 디버깅할 때 사용 가능한 표준 Python 자체의 소스 코드를 만들려면 [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)를 방문하여 버전에 적합한 보관 파일을 다운로드하여 폴더로 추출합니다. 그런 다음 메시지가 표시되는 시점과 관계없이 Visual Studio가 해당 폴더에 있는 특정 파일을 가리키도록 합니다.

## <a name="enable-mixed-mode-debugging-in-a-cc-project"></a>C/C++ 프로젝트에서 혼합 모드 디버깅 사용

Visual Studio(2017 15.5 이상 버전)는 C/C++ 프로젝트에서 혼합 모드 디버깅을 지원합니다(예: [python.org에 설명된 대로 다른 애플리케이션에 Python이 포함](https://docs.python.org/3/extending/embedding.html)되는 경우). 혼합 모드 디버깅을 사용하려면 **Python/네이티브 디버깅**을 실행하도록 C/C++ 프로젝트를 구성합니다.

1. **솔루션 탐색기**에서 C/C++ 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
1. **디버깅** 탭을 선택하고, **실행할 디버거**에서 **Python/네이티브 디버깅**을 선택하고, **확인**을 선택합니다.

    ![C/C++ 프로젝트에서 Python/네이티브 디버거를 선택합니다.](media/mixed-mode-debugging-select-cpp-debugger.png)

> [!Note]
> **Python/네이티브 디버깅**을 선택할 수 있는 옵션이 없는 경우 먼저 VS 설치 관리자를 사용하여 **Python 네이티브 개발 도구**를 설치해야 합니다. 이 설치 관리자는 Python 개발 워크로드에서 옵션으로 찾을 수 있습니다. 자세한 내용은 [Windows의 Visual Studio에서 Python 지원 설치 방법](installing-python-support-in-visual-studio.md)을 참조하세요.

이 메서드를 사용하면 디버거를 연결할 수 없는 자식 *python.exe* 프로세스를 생성하기 때문에 *py.exe* 시작 관리자 자체를 디버그할 수 없습니다. 인수를 사용하여 *python.exe*를 직접 시작하려면 **Python/네이티브 디버깅** 속성에서 **명령** 옵션을 변경(이전 이미지에 표시)하여 전체 경로를 *python.exe*로 지정한 다음, **명령 인수**에서 인수를 지정합니다.

### <a name="attaching-the-mixed-mode-debugger"></a>혼합 모드 디버거 연결

모든 이전 버전의 Visual Studio의 경우 C/C++ 프로젝트가 네이티브 디버거만을 사용하기 때문에 Visual Studio에서 Python 프로젝트를 시작할 때 직접 혼합 모드 디버깅을 사용할 수 있습니다. 그러나 디버거를 별도로 연결할 수 있습니다.

1. 디버그하지 않고 C++ 프로젝트를 시작합니다(**디버그** > **디버깅하지 않고 시작** 또는 **Ctrl**+**F5**).
1. **디버그** > **프로세스에 연결**을 선택합니다. 대화 상자가 나타나면 해당하는 프로세스를 선택한 다음, **선택** 단추를 사용하여 **코드 형식 선택** 대화 상자를 엽니다. 여기서 **Python**을 선택할 수 있습니다.

    ![디버거 연결 시 디버깅 형식으로 Python 선택](media/mixed-mode-debugging-attach-type.png)

1. **확인**을 선택하여 이 대화 상자를 닫고 **연결**을 선택하여 디버거를 시작합니다.
1. 디버거를 연결하기 전에 디버그할 Python 코드를 호출하지 않도록 C++ 앱에서 적합한 일시 중지 또는 지연을 도입해야 할 수 있습니다.

## <a name="mixed-mode-specific-features"></a>혼합 모드의 특정 기능

- [결합된 호출 스택](#combined-call-stack)
- [Python 코드와 네이티브 코드 간 단계](#step-between-python-and-native-code)
- [네이티브 코드에서 PyObject 값 보기](#pyobject-values-view-in-native-code)
- [Python 코드에서 네이티브 값 보기](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>결합된 호출 스택

**호출 스택** 창에는 네이티브 프레임과 Python 스택 프레임 사이에 표시된 전환으로 두 프레임이 모두 인터리브되어 있습니다.

![혼합 모드 디버깅과 결합된 호출 스택](media/mixed-mode-debugging-call-stack.png)

**도구** > **옵션** > **디버깅** > **일반** > **내 코드만 사용** 옵션이 설정된 경우 전환은 전환 방향을 지정하지 않고 **[외부 코드]** 로 표시됩니다.

호출 프레임을 두 번 클릭하면 활성 상태가 되고, 가능한 경우 해당 원본 코드가 열립니다. 원본 코드를 사용할 수 없으면 프레임이 여전히 활성 상태로 있고 지역 변수를 검사할 수 있습니다.

### <a name="step-between-python-and-native-code"></a>Python 코드와 네이티브 코드 간 단계

**한 단계씩 코드 실행**(**F11**) 또는 **프로시저 나가기**(**Shift**+**F11**) 명령을 사용할 때 혼합 모드 디버거는 코드 형식 간 변경 내용을 올바르게 처리합니다. 예를 들어 Python에서 C로 구현된 형식의 메서드를 호출할 때 해당 메서드에 대한 호출을 단계별로 실행하면 메서드를 구현하는 네이티브 함수의 시작 부분에서 중지합니다. 마찬가지로 네이티브 코드에서 일부 Python API 함수를 호출하면 Python 코드가 호출됩니다. 예를 들어 원래 Python에서 정의된 함수 값에 대해 단계별로 `PyObject_CallObject`를 실행하면 Python 함수의 시작 부분에서 중지합니다. 또한 Python에서 네이티브로의 단계별 실행은 [ctypes](https://docs.python.org/3/library/ctypes.html)를 통해 Python에서 호출된 네이티브 함수에 대해서도 지원됩니다.

### <a name="pyobject-values-view-in-native-code"></a>네이티브 코드에서 PyObject 값 보기

네이티브(C 또는 C++) 프레임이 활성 상태이면 디버거 **로컬** 창에 지역 변수가 표시됩니다. 네이티브 Python 확장 모듈에서 이러한 변수 중 다수는 `PyObject` 형식(`_object`에 대한 형식 정의임)이거나 몇 가지 다른 기본 Python 형식(아래 목록 참조)입니다. 혼합 모드 디버깅에서 이러한 값은 **[Python 보기]** 라는 레이블이 지정된 추가 자식 노드를 나타냅니다. 이 노드가 확장되면 동일한 개체를 참조하는 지역 변수가 Python 프레임워크에 있었던 경우에 표시한 것과 동일한 변수의 Python 표현을 보여 줍니다. 이 노드의 자식 항목은 편집할 수 있습니다.

![지역 창에서 Python 보기](media/mixed-mode-debugging-python-view.png)

이 기능을 사용하지 않도록 설정하려면 **로컬** 창에서 아무 곳이나 마우스 오른쪽 단추를 클릭하고 **Python** > **Python 보기 노드 표시** 메뉴 옵션을 설정/해제합니다.

![지역 창에서 Python 보기 활성화](media/mixed-mode-debugging-enable-python-view.png)

**[Python 보기]** 노드를 보여주는 C 형식(사용 가능한 경우):

- `PyObject`
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

사용자가 직접 작성하는 형식의 **[Python 보기]** 는 자동으로 표시되지 않습니다. Python 3.x용 확장을 작성할 때 모든 개체에는 궁극적으로 위 형식 중 하나의 `ob_base` 필드가 있고, 이로 인해 **[Python 보기]** 가 표시되기 때문에 이는 일반적으로 문제가 되지 않습니다.

그러나 Python 2.x의 경우 각 개체 형식은 일반적으로 헤더를 인라인 필드의 컬렉션으로 선언하고, C/C++ 코드의 형식 시스템 수준에서 사용자 지정 작성 형식과 `PyObject` 사이에는 관련이 없습니다. 이러한 사용자 지정 형식에 대해 **[Python 보기]** 노드를 사용하도록 설정하려면 [Python 도구 설치 디렉터리](installing-python-support-in-visual-studio.md#install-locations)에서 *PythonDkm.natvis* 파일을 편집하고 C 구조체 또는 C++ 클래스의 XML에 다른 요소를 추가합니다.

대체(및 더 나은) 옵션은 [PEP 3123](https://www.python.org/dev/peps/pep-3123/)를 따르고 `PyObject_HEAD` 대신 명시적인 `PyObject ob_base;` 필드를 사용하는 것이지만, 이전 버전과의 호환성을 위해 항상 가능하지는 않습니다.

### <a name="native-values-view-in-python-code"></a>Python 코드에서 네이티브 값 보기

이전 섹션과 마찬가지로 Python 프레임이 활성 상태로 있을 때 **로컬** 창에서 네이티브 값에 대해 **[C++ 보기]** 를 사용하도록 설정할 수 있습니다. 이 기능은 기본적으로 사용되지 않으므로 **로컬** 창을 마우스 오른쪽 단추로 클릭하고 **Python** > **C++ 보기 노드 표시** 메뉴 옵션을 설정/해제하여 설정합니다.

![지역 창에서 C++ 보기 활성화](media/mixed-mode-debugging-enable-cpp-view.png)

**[C++ 보기]** 노드는 네이티브 프레임에서 표시하는 것과 동일한 값에 대한 기본 C/C++ 구조의 표현을 제공합니다. 예를 들어 이 노드는 Python 정수(Long)에 대해 `_longobject`(형식 정의가 `PyLongObject`임)의 인스턴스를 보여 주며, 사용자가 직접 작성한 네이티브 클래스의 형식을 추론하려고 합니다. 이 노드의 자식 항목은 편집할 수 있습니다.

![지역 창에서 C++ 보기](media/mixed-mode-debugging-cpp-view.png)

개체의 자식 필드가 `PyObject` 형식이거나 지원되는 다른 형식 중 하나인 경우 **[Python 보기]** 표현 노드(이러한 표현이 사용 가능한 경우)를 사용하므로 링크가 Python에 직접 제공되지 않는 개체 그래프를 탐색할 수 있습니다.

Python 개체 메타데이터를 사용하여 개체 형식을 결정하는 **[Python 보기]** 노드와 달리 **[C++ 보기]** 에는 비슷한 방식으로 신뢰할 수 있는 메커니즘이 없습니다. 일반적으로 Python 값(즉, `PyObject` 참조)이 있다고 가정하면 어떤 C/C++ 구조에서 이를 지원하는지 확인할 수 없습니다. 혼합 모드 디버거에서는 함수 포인터 형식을 가진 개체 형식의 여러 필드(예: `ob_type` 필드로 참조되는 `PyTypeObject`)를 보고 해당 형식을 추측하려고 합니다. 이러한 함수 포인터 중 하나에서 해결할 수 있는 함수를 참조하고 해당 함수에서 `PyObject*`보다 구체적인 형식의 `self` 매개 변수를 갖는 경우 해당 형식이 지원 형식으로 간주됩니다. 예를 들어 지정된 개체의 `ob_type->tp_init`에서 다음 함수를 가리키는 경우가 있습니다.

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

이 경우 디버거에서 개체의 C 형식이 `FobObject`임을 올바르게 추론할 수 있습니다. `tp_init`에서 더 정밀하게 형식을 확인할 수 없는 경우 다른 필드로 이동합니다. 이러한 필드 중 하나에서 형식을 추론할 수 없는 경우 **[C++ 보기]** 노드는 해당 개체를 `PyObject` 인스턴스로 표시합니다.

작성된 사용자 지정 형식에 대해 항상 유용한 표현을 얻으려면, 형식을 등록할 때 하나 이상의 특수 함수를 등록하고 강력한 형식의 `self` 매개 변수를 사용하는 것이 좋습니다. 대부분의 형식은 자연스럽게 이러한 요구 사항을 충족합니다. 그렇지 않은 경우 일반적으로 `tp_init`가 이 용도로 사용하기에 가장 편리한 항목입니다. 디버거 형식 유추를 사용하도록 설정하기 위해서만 존재하는 형식에 대한 더미 구현인 `tp_init`는 위의 코드 샘플에서와 같이 즉시 0을 반환할 수 있습니다.

## <a name="differences-from-standard-python-debugging"></a>표준 Python 디버깅과의 차이점

혼합 모드 디버거는 몇 가지 추가 기능을 도입하지만 다음과 같이 일부 Python 관련 기능이 부족하다는 점에서 [표준 Python 디버거](debugging-python-in-visual-studio.md)와 완전히 다릅니다.

- 지원되지 않는 기능: 조건부 중단점, **대화형 디버그** 창 및 플랫폼 간 원격 디버깅
- **직접 실행** 창: 사용 가능하지만 여기서 나열하는 모든 제한을 포함하여 기능의 하위 집합이 제한됩니다.
- 지원되는 Python 버전: CPython 2.7 및 3.3+만 해당.
- Visual Studio Shell: Visual Studio Shell에서 Python을 사용하는 경우(예: 통합 설치 관리자를 사용하여 설치한 경우) Visual Studio에서 C++ 프로젝트를 열 수 없으며 C++ 파일에 대한 편집 환경은 기본 텍스트 편집기의 환경입니다. 그러나 C/C++ 디버깅 및 혼합 모드 디버깅은 셸에서 원본 코드, 네이티브 코드 단계별 실행 및 디버거 창의 C++ 식 계산을 통해 완벽하게 지원됩니다.
- 개체 보기 및 확장: **로컬** 및 **조사식** 디버거 도구 창에서 Python 개체를 볼 때 혼합 모드 디버거는 개체의 구조만 표시합니다. 속성을 자동으로 평가하거나 계산된 특성을 표시하지 않습니다. 컬렉션의 경우 기본 제공 컬렉션 형식(`tuple`, `list`, `dict`, `set`)에 대한 요소만 표시합니다. 일부 기본 제공 컬렉션 형식에서 상속되지 않는 한 사용자 지정 컬렉션 형식은 컬렉션으로 시각화되지 않습니다.
- 식 계산: 아래 참조

### <a name="expression-evaluation"></a>식 계산

표준 Python 디버거를 사용하면, 디버그된 프로세스가 I/O 작업 또는 다른 유사한 시스템 호출에서 차단되지 않는 한, 코드의 어느 지점에서 일시 중지될 때 **조사식** 및 **직접 실행** 창에서 임의의 Python 식을 계산할 수 있습니다. 혼합 모드 디버깅에서 임의의 식은 Python 코드에서 중지된 경우, 중단점 이후 또는 단계별로 코드를 실행한 후에만 계산할 수 있습니다. 중단점이나 단계별 실행 작업이 발생한 스레드에서만 식을 계산할 수 있습니다.

네이티브 코드 또는 위의 조건이 적용되지 않는 Python 코드(예: 프로시저 나가기 작업 후 또는 다른 스레드)에서 중지되면, 식 계산은 현재 선택된 프레임의 범위에서 지역 변수 및 전역 변수에 액세스하고, 필드에 액세스하며, 리터럴을 사용하여 기본 제공 컬렉션 형식을 인덱싱하는 것으로 제한됩니다. 예를 들어 다음 식은 모든 컨텍스트에서 계산될 수 있습니다(모든 식별자에서 적절한 형식의 기존 변수와 필드를 참조하는 경우).

```python
foo.bar[0].baz['key']
```

또한 혼합 모드 디버거는 이러한 식을 다르게 확인합니다. 모든 멤버 액세스 작업은 개체(예: `__dict__` 또는 `__slots__`에 있는 항목이나 `tp_members`을 통해 Python에 제공되는 네이티브 구조체의 필드)의 직접적 요소인 필드만 조회하며, `__getattr__`, `__getattribute__` 또는 설명자 논리를 무시합니다. 마찬가지로 모든 인덱싱 작업은 `__getitem__`을 무시하고 컬렉션의 내부 데이터 구조에 직접 액세스합니다.

일관성을 위해 이 이름 확인 체계는 현재 중지 지점에서 임의의 식을 허용하는지 여부와 관계없이 제한된 식 계산에 대한 제약 조건과 일치하는 모든 식에 사용됩니다. 모든 기능을 제공하는 계산기를 사용할 수 있을 때 적절한 Python 의미 체계를 강제로 적용하려면 식을 괄호로 묶습니다.

```python
(foo.bar[0].baz['key'])
```
