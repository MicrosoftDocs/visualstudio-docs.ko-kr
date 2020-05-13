---
title: Python 코드 리팩터링
description: Visual Studio를 사용하면 식별자의 이름을 바꾸고, 메서드를 추출하고, 가져오기를 추가하고, 사용하지 않는 가져오기를 제거하여 Python 코드를 쉽게 리팩터링할 수 있습니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db1a551e20c597f98052471910bcb696c878675f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62429900"
---
# <a name="refactor-python-code"></a>Python 코드 리팩터링

Visual Studio는 Python 소스 코드를 자동으로 변환하고 정리하는 몇 가지 명령을 제공합니다.

- [이름 바꾸기](#rename)는 선택한 클래스, 메서드 또는 변수의 이름을 바꿉니다.
- [메서드 추출](#extract-method)은 선택한 코드에서 새 메서드를 만듭니다.
- [가져오기 추가](#add-import)는 누락된 가져오기를 추가하는 스마트 태그를 제공합니다
- [사용하지 않는 가져오기 제거](#remove-unused-imports)는 사용하지 않는 가져오기를 제거합니다.

## <a name="rename"></a>이름 바꾸기

1. 이름을 바꿀 식별자를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택하거나, 해당 식별자에 캐럿을 배치하고 **편집** > **리팩터링** > **이름 바꾸기** 메뉴 명령(**F2**)을 선택합니다.
2. **이름 바꾸기** 대화 상자가 표시되면 식별자의 새 이름을 입력하고 **확인**을 선택합니다.

   ![새 식별자 이름에 대한 프롬프트 이름 바꾸기](media/code-refactor-rename-1.png)

3. 다음 대화 상자에서 이름 바꾸기를 적용할 코드의 파일과 인스턴스를 선택합니다. 특정 인스턴스를 선택하여 해당 변경 내용을 미리 봅니다.

   ![대화 상자의 이름을 변경하여 변경 내용을 적용할 위치 선택](media/code-refactor-rename-2.png)

4. **적용**을 선택하여 원본 코드 파일을 변경합니다. 이 작업은 실행 취소할 수 있습니다.

## <a name="extract-method"></a>메서드 추출

1. 별도의 메서드로 추출할 코드 줄이나 식을 선택합니다.
2. **편집** > **리팩터링** > **메서드 추출** 메뉴 명령을 선택하거나, **Ctrl**+**R** > **M**을 입력합니다.
3. 표시되는 대화 상자에서 새 메서드 이름을 입력하고 추출할 위치를 지정한 다음 클로저 변수를 선택합니다. 클로저로 선택되지 않은 변수는 메서드 인수로 변환됩니다.

   ![메서드 추출 대화 상자](media/code-refactor-extract-method-1.png)

4. **확인**을 선택하고, 이에 따라 코드가 수정됩니다.

   ![메서드 추출 결과](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>가져오기 추가

형식 정보가 없는 식별자에 캐럿을 배치하면 Visual Studio에서 명령에 필요한 `import` 또는 `from ... import` 문을 추가하는 스마트 태그(코드 왼쪽의 전구 모양 아이콘)를 제공합니다.

![가져오기 스마트 태그 추가](media/code-refactor-add-import-1.png)

Visual Studio에서는 현재 프로젝트 및 표준 라이브러리의 최상위 패키지 및 모듈에 대해 `import` 완성 기능뿐만 아니라 하위 모듈 및 하위 패키지와 모듈 멤버에 대한 `from ... import` 완성 기능도 제공합니다. 완성 기능에는 함수, 클래스, 내보낸 데이터 등이 포함됩니다. 두 옵션 중 하나를 선택하면 다른 가져오기 후에 문을 파일의 맨 위에 추가하거나 동일한 모듈을 이미 가져온 경우 기존 `from ... import` 문에 해당 문을 추가합니다.

![가져오기 추가 결과](media/code-refactor-add-import-2.png)

Visual Studio는 모듈에서 실제로 정의되지 않은 멤버(예: 다른 모듈로 가져왔지만 가져오기를 수행하는 모듈의 자식이 아닌 모듈)를 필터링하려고 합니다. 예를 들어 많은 모듈에서 `import sys` 대신 `from xyz import sys`를 사용하므로 해당 모듈에 `sys`를 제외하는 `__all__` 멤버가 없더라도 다른 모듈에서 `sys` 가져오기 완성이 표시되지 않습니다.

마찬가지로 Visual Studio는 다른 모듈이나 기본 제공 네임스페이스에서 가져온 함수를 필터링합니다. 예를 들어 모듈이 `settrace` 모듈에서 `sys` 함수를 가져오는 경우 이론적으로는 해당 모듈에서 가져올 수 있습니다. 그러나 `import settrace from sys`를 직접 사용하는 것이 가장 좋으므로 Visual Studio는 해당 문을 구체적으로 제공합니다.

마지막으로, 일반적으로 제외되는 모듈에 포함될 다른 값이 있는 경우(예: 모듈에서 이름에 값이 할당되었기 때문에) Visual Studio에서 여전히 가져오기를 제외합니다. 이 동작은 값이 다른 모듈에 정의되어 있으므로 해당 값을 내보내지 않아야 한다고 가정합니다. 따라서 추가 할당은 내보낼 수 없는 더미 값이 될 수도 있습니다.

## <a name="remove-unused-imports"></a>사용하지 않는 가져오기 제거

코드를 작성할 때 전혀 사용되지 않는 모듈에 대해 `import` 문으로 끝나는 것은 쉽습니다. Visual Studio는 코드를 분석하므로 문이 나타나는 위치 아래의 범위 내에서 가져온 이름을 사용하는지 확인하여 `import` 문이 필요한지를 자동으로 결정할 수 있습니다.

편집기의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 **모든 범위** 또는 **현재 범위**에서 제거할 수 있는 옵션을 제공하는 **가져오기 제거**를 선택합니다.

![가져오기 제거 메뉴](media/code-refactor-remove-imports-1.png)

그러면 Visual Studio에서 코드를 적절하게 변경합니다.

![가져오기 제거 결과](media/code-refactor-remove-imports-2.png)

Visual Studio는 제어 흐름을 설명하지 않습니다. `import` 문 앞에 이름을 사용하면 이름이 실제로 사용된 것처럼 처리됩니다. 또한 Visual Studio는 `from __future__` 문뿐만 아니라 모든 `from ... import *` 가져오기, 즉 클래스 정의 내에서 수행되는 가져오기도 무시합니다.
