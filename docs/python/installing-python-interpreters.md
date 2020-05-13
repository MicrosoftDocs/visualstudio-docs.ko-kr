---
title: Python 인터프리터 선택 및 설치
description: 설치 관리자를 찾을 위치에 대한 간단한 지침이 포함된 Visual Studio에서 지원되는 Python 인터프리터의 전체 목록입니다.
ms.date: 06/05/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 13290aef7acfe599c7693af4be771c625e713596
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75735820"
---
# <a name="install-python-interpreters"></a>Python 인터프리터 설치

기본적으로 Visual Studio 2017 이상에 Python 개발 워크로드를 설치하면 Python 3(64비트)도 설치됩니다. 필요한 경우 [설치](installing-python-support-in-visual-studio.md)에 설명된 대로 32비트 및 64비트 버전의 Python 2, Python 3와 Miniconda(Visual Studio 2019) 또는 Anaconda 2/Anaconda 3(Visual Studio 2017)를 함께 설치하도록 선택할 수 있습니다.

::: moniker range=">=vs-2019"
또는 **환경 추가** 대화 상자에서 표준 Python 인터프리터를 설치할 수 있습니다. **Python 환경** 창 또는 Python 도구 모음에서 **환경 추가** 명령을 선택하고, **Python 설치** 탭을 선택하고, 설치할 인터프리터를 표시하고, **설치**를 선택합니다.
::: moniker-end

Visual Studio 설치 관리자 외부에서 아래 표에 나열된 인터프리터를 수동으로 설치할 수도 있습니다. 예를 들어 Visual Studio를 설치하기 전에 Anaconda 3을 설치한 경우 Visual Studio 설치 관리자를 통해 다시 설치할 필요가 없습니다. 예를 들어 Visual Studio 설치 관리자에 아직 표시되지 않는 사용 가능한 인터프리터의 최신 버전이 있는 경우에도 인터프리터를 수동으로 설치할 수 있습니다.

::: moniker range=">=vs-2019"
> [!Note]
> Visual Studio는 Python 버전 2.7과 버전 3.5 이상을 지원합니다. Visual Studio를 사용하여 다른 버전의 Python에서 작성된 코드도 편집할 수 있지만, 해당 버전은 공식적으로 지원되지 않으며 IntelliSense, 디버깅 등의 기능이 작동하지 않을 수 있습니다.
::: moniker-end

**Visual Studio 2015 이하**의 경우 인터프리터 중 하나를 수동으로 설치해야 합니다.

Visual Studio(모든 버전)는 레지스트리를 확인하여 각 설치된 Python 인터프리터 및 해당 환경을 자동으로 검색합니다([Windows 레지스트리의 PEP 514 - Python 등록](https://www.python.org/dev/peps/pep-0514/)에 따라). Python 설치는 일반적으로 **HKEY_LOCAL_MACHINE\SOFTWARE\Python**(32비트) 및 **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Python**(64비트) 아래의 **PythonCore**(CPython) 및 **ContinuumAnalytics**(Anaconda)와 같은 배포 노드 내에 있습니다.

Visual Studio가 설치된 환경을 검색하지 않으면 [기존 환경 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)을 참조하세요.

Visual Studio는 [**Python 환경**](managing-python-environments-in-visual-studio.md#the-python-environments-window) 창에서 알려진 모든 환경을 표시하고 기존 인터프리터의 업데이트를 자동으로 검색합니다.

| 인터프리터 | Description |
| --- | --- |
| [CPython](https://www.python.org/) | 가장 널리 사용되는 “기본” 인터프리터로, 32비트 및 64비트 버전 사용이 가능합니다(32비트 권장). 최신 언어 기능, 최대 Python 패키지 호환성, 완전한 디버깅 지원 및 [IPython](https://ipython.org/)과 상호 interop을 포함합니다. [Python 2 또는 Python 3을 사용해야 하나요?](https://wiki.python.org/moin/Python2orPython3)도 참조하세요. Visual Studio 2015 이전 버전은 Python 3.6+를 지원하지 않으며 **Python 버전 3.6이 지원되지 않음**과 같은 오류를 표시할 수 있습니다. 대신 Python 3.5 또는 이전을 사용합니다. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python의 .NET 구현으로, 32비트 및 64비트 버전으로 사용 가능하며 C#/F#/Visual Basic interop, .NET API에 대한 액세스, 표준 Python 디버깅(그러나 C++ 혼합 모드 디버깅은 제외) 및 혼합 IronPython/C# 디버깅을 제공합니다. 하지만 IronPython에서는 가상 환경을 지원하지 않습니다. |
| [Anaconda](https://www.continuum.io) | Python에서 제공하는 개방형 데이터 과학 플랫폼으로, 최신 버전의 CPython과 설치하기 어려운 대부분의 패키지를 포함합니다. 달리 결정할 수 없는 경우 권장됩니다. |
| [PyPy](https://www.pypy.org/) | Python의 고성능 추적 JIT 구현으로, 장기적으로 실행되는 프로그램과 성능 문제를 확인했으나 다른 해결 방법을 찾을 수 없는 상황에 적절합니다. Visual Studio에서 작동하지만 고급 디버깅 기능은 제한적으로 지원됩니다. |
| [Jython](https://www.jython.org/) | JVM(Java Virtual Machine)에서 Python 구현. IronPython과 마찬가지로, Jython에서 실행되는 코드는 Java 클래스 및 라이브러리와 상호 작용할 수 있지만 CPython용으로 작성된 많은 라이브러리는 사용할 수 없습니다. Visual Studio에서 작동하지만 고급 디버깅 기능은 제한적으로 지원됩니다. |

Python 환경에 대한 새로운 검색 양식을 제공하려는 개발자인 경우 [PTVS 환경 검색](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments)(github.com)을 참조하세요.

## <a name="move-an-interpreter"></a>인터프리터 이동

파일 시스템을 사용하여 새 위치로 기존 인터프리터를 이동하는 경우 Visual Studio는 변경 내용을 자동으로 검색하지 않습니다.

- 원래 **Python 환경** 창을 통해 인터프리터의 위치를 지정한 경우 해당 창의 **구성** 탭을 사용하여 새 위치를 식별하도록 환경을 편집합니다. [기존 환경 수동 식별](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)을 참조하세요.

- 설치 관리자 프로그램을 사용하여 인터프리터를 설치한 경우 다음 단계에 따라 새 위치에 인터프리터를 다시 설치합니다.

  1. Python 인터프리터를 원래 위치로 복원합니다.
  2. 설치 관리자를 사용하여 인터프리터를 제거합니다. 그러면 레지스트리 항목이 정리됩니다.
  3. 원하는 위치에 인터프리터를 다시 설치합니다.
  4. Visual Studio를 다시 시작합니다. 그러면 이전 위치 대신 새 위치가 자동 검색됩니다.

이 프로세스를 수행하면 Visual Studio에서 사용하는 인터프리터의 위치를 식별하는 레지스트리 항목이 제대로 업데이트됩니다. 설치 관리자를 사용하면 존재할 수 있는 다른 부작용도 처리됩니다.

## <a name="see-also"></a>참고 항목

- [Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [프로젝트의 인터프리터 선택](selecting-a-python-environment-for-a-project.md)
- [종속성에 대해 requirements.txt 사용](managing-required-packages-with-requirements-txt.md)
- [검색 경로](search-paths.md)
- [Python 환경 창 참조](python-environments-window-tab-reference.md)
