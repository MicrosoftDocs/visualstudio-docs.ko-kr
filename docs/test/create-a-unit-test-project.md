---
title: 단위 테스트 프로젝트 만들기
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 313083090c94c94f4e196e87f3bf6cf6df36e118
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565255"
---
# <a name="create-a-unit-test-project"></a>단위 테스트 프로젝트 만들기

단위 테스트는 종종 테스트 중인 코드의 구조를 반영합니다. 예를 들어 프로젝트의 각 코드 프로젝트에 대해 단위 테스트 프로젝트를 만들 수 있습니다. 테스트 프로젝트는 프로덕션 코드와 동일한 솔루션에 있거나 개별 솔루션에 있을 수 있습니다. 한 솔루션에 여러 개의 테스트 프로젝트를 포함할 수 있습니다.

> [!NOTE]
> 네이티브 코드의 단위 테스트 위치와 테스트 프로젝트 구조는 이 문서에서 설명하는 구조와 다를 수 있습니다. 자세한 내용은 [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)을 참조하세요.

## <a name="to-create-a-unit-test-project"></a>단위 테스트 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택하거나 **Ctrl**+**Shift**+**N**을 누릅니다.

::: moniker range="vs-2017"

2. **새 프로젝트** 대화 상자에서 **설치됨** 노드를 확장하고 테스트 프로젝트에 사용하려는 언어를 선택한 후 **테스트**를 선택합니다.

3. 사용하려는 테스트 프레임워크에 대한 프로젝트 템플릿(예를 들어 **MSTest 테스트 프로젝트** 또는 **NUnit 테스트 프로젝트**)를 선택합니다. 프로젝트 이름을 지정한 다음 **확인**을 선택합니다.

   ![Visual Studio 2017의 테스트 프로젝트 템플릿](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **새 프로젝트 만들기** 페이지에서 **단위 테스트**를 검색 상자에 입력합니다. 사용하려는 테스트 프레임워크에 대한 프로젝트 템플릿(예를 들어 **MSTest 테스트 프로젝트** 또는 **NUnit 테스트 프로젝트**)를 선택한 후 **다음**을 선택합니다.

   ![Visual Studio 2019의 테스트 프로젝트 템플릿](media/vs-2019/test-project-templates.png)

3. **새 프로젝트 구성** 페이지에서 프로젝트의 이름을 입력한 다음, **만들기**를 선택합니다.

::: moniker-end

4. 단위 테스트 프로젝트에서 테스트 중인 코드에 대한 참조를 추가합니다. 동일한 솔루션의 코드 프로젝트에 대한 참조를 추가하려면:

   1. **솔루션 탐색기**에서 테스트 프로젝트를 선택합니다.

   2. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.

   3. **참조 관리자**에서 **프로젝트** 아래에 있는 **솔루션** 노드를 선택합니다. 테스트하려는 코드 프로젝트를 선택한 다음, **확인**을 선택합니다.

   테스트하려는 코드가 다른 위치에 있는 경우 참조 추가에 대한 자세한 내용은 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

다음 섹션 중 하나를 참조하십시오.

**단위 테스트 작성**

- [코드 단위 테스트](../test/unit-test-your-code.md)

- [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)

- [단위 테스트에서 MSTest 프레임워크 사용](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**단위 테스트 실행**

- [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)
