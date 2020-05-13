---
title: Python 검색 경로를 적용하는 방법
description: Visual Studio는 시스템 전체 변수 사용을 피하기 위해 환경 및 프로젝트에 대한 검색 경로를 지정하는 보다 구체적인 방법을 제공합니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 37ce9d7b1853dfecc9e0ec33ca08c3c3fa0571e0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62428440"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio에서 Python 검색 경로를 사용하는 방법

일반적인 Python 사용에서 `PYTHONPATH` 환경 변수(또는 `IRONPYTHONPATH` 등)는 모듈 파일에 대한 기본 검색 경로를 제공합니다. 즉, `from <name> import...` 또는 `import <name>` 문을 사용하는 경우 Python은 다음 위치에서 일치하는 이름을 순서대로 검색합니다.

1. Python의 기본 제공 모듈입니다.
1. 실행 중인 Python 코드를 포함하는 폴더입니다.
1. 적용 가능한 환경 변수에 정의된 “모듈 검색 경로” 입니다. (코어 Python 설명서의 [모듈 검색 경로](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) 및 [환경 변수](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) 참조)

그러나 Visual Studio에서는 변수가 전체 시스템에 대해 설정된 경우에도 검색 경로 환경 변수를 무시합니다. 실제로 이렇게 무시되는 이유는 엄밀히 말해 전체 시스템에 대해 설정되었고, 따라서 자동으로 해결할 수 없는 다음과 같은 특정 질문이 제기되기 *때문입니다*. 참조된 모듈이 Python 2.7 또는 Python 3.6용인가요? 이 모듈이 표준 라이브러리 모듈을 재정의하게 되는가? 개발자가 이 동작을 알고 있는가 아니면 악의적인 하이재킹 시도인가?

따라서 Visual Studio에서는 환경 및 프로젝트 모두에서 검색 경로를 직접 지정하는 방법을 제공합니다. Visual Studio에서 실행하거나 디버그하는 코드는 `PYTHONPATH` 값으로 검색 경로(및 기타 동등한 변수)를 받습니다. Visual Studio는 검색 경로를 추가하여 해당 위치의 라이브러리를 검사하고 필요한 경우(Visual Studio 2017 버전 15.5 및 이전 버전) 라이브러리에 대한 IntelliSense 데이터베이스를 빌드합니다(라이브러리 수에 따라 데이터베이스를 구성하는 데 다소 시간이 걸릴 수 있음).

검색 경로 추가하려면 **솔루션 탐색기**로 이동하여 프로젝트 노드를 확장하고, **검색 경로**를 마우스 오른쪽 단추로 클릭하여 **검색 경로에 폴더 추가**를 선택합니다.

::: moniker range="vs-2017"
![솔루션 탐색기의 검색 경로에서 검색 경로 명령에 폴더 추가](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![솔루션 탐색기의 검색 경로에서 검색 경로 명령에 폴더 추가](media/search-paths-command-2019.png)
::: moniker-end

이 명령은 포함할 폴더를 선택할 수 있는 브라우저를 표시합니다.

`PYTHONPATH` 환경 변수에 원하는 폴더가 이미 포함되어 있는 경우 **검색 경로에 PYTHONPATH 추가**를 편리한 바로 가기로 사용합니다.

검색 경로에 폴더를 추가하면 Visual Studio에서는 프로젝트와 연결된 모든 환경에 대해 해당 경로를 사용합니다. (환경이 Python 3을 기반으로 하고 Python 2.7 모듈에 검색 경로를 추가하려는 경우 오류가 표시될 수 있습니다.)

*.zip* 또는 *.egg* 확장명이 있는 파일도 **검색 경로에 Zip 보관 파일 추가** 명령를 선택하여 검색 경로로 추가할 수 있습니다. 폴더와 마찬가지로 이러한 폴더의 내용을 검색하고 IntelliSense에 제공합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [프로젝트의 인터프리터 선택](selecting-a-python-environment-for-a-project.md)
- [종속성에 대해 requirements.txt 사용](managing-required-packages-with-requirements-txt.md)
- [Python 환경 창 참조](python-environments-window-tab-reference.md)
