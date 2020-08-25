---
title: Mac용 Visual Studio 테스트 도구
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: acf34677e8d9b477512763be3c43bb9df0c53c46
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88201793"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 테스트 도구

Mac용 Visual Studio 테스트 도구를 사용하면 사용자와 팀이 수준 높은 코드를 개발하고 유지할 수 있습니다. 단위 테스트는 MSTest(Microsoft 단위 테스트 프레임워크), xUnit 또는 NUnit을 사용하여 작성하고 실행할 수 있습니다.

## <a name="creating-tests"></a>테스트 생성
테스트를 시작하려면 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 프로젝트...** 메뉴를 선택하여 솔루션에 새 테스트 프로젝트를 만들면 됩니다. 그런 다음 대화 상자의 왼쪽에 있는 테스트 카테고리 중 하나를 선택합니다(예: **웹 및 콘솔 > 테스트** 범주). 생성하려는 테스트 프로젝트의 유형을 선택하고 다음을 클릭합니다. 표시되는 대화 상자의 안내에 따르면 새 테스트 프로젝트가 솔루션에 추가됩니다.

![웹 및 콘솔 > 테스트 섹션을 선택하여 xUnit, MSTest 및 NUnit 프로젝트가 표시된 새 프로젝트 대화 상자](media/create-new-test-project.PNG)

> [!NOTE]
> .NET Core 애플리케이션의 유닛 테스트 및 단위 테스트 프레임워크 선택에 관한 자세한 내용은 [.NET Core 및 .NET Standard의 유닛 테스트](https://docs.microsoft.com/dotnet/core/testing/?pivots=xunit) 설명서를 참조하세요.

## <a name="running-tests"></a>테스트 실행
**단위 테스트** 창은 단위 테스트를 실행하는 데 사용되고 **보기 > 패드 > 단위 테스트** 메뉴를 사용하여 엽니다. 솔루션의 단위 테스트는 자동으로 검색되어 이 창에 표시됩니다. 여기서 모든 테스트 또는 선택한 테스트 세트를 실행할 수 있습니다.

![테스트 실행 또는 중지를 위한 단위 테스트 및 도구 모음의 목록을 보여 주는 테스트 창](media/test-window.PNG)

단위 테스트가 포함된 C# 클래스를 편집하는 경우 테스트 클래스 또는 테스트 메서드를 마우스 오른쪽 단추로 클릭한 후 **테스트 실행** 또는 **테스트 디버그** 메뉴를 선택하여 테스트를 실행할 수 있습니다. **테스트 실행** 메뉴 항목을 선택하면 테스트 창에서 테스트가 실행됩니다. **테스트 디버그** 메뉴를 선택하면 동일한 작업이 수행되고 코드 문제를 해결할 수 있도록 디버거가 연결됩니다.

![마우스 오른쪽 단추 메뉴 클릭으로 테스트 실행 및 테스트 디버그 옵션이 표시된 편집기](media/run-tests-context-menu.PNG)

테스트를 실행하는 동안 **테스트 결과** 창이 표시되며, 여기서 성공하거나 실패한 테스트와 해당 테스트 실행의 출력을 검토할 수 있습니다.

![실패한 테스트 하나와 개수(통과 테스트 21개 및 실패한 테스트 1개)를 보여 주는 테스트 결과 창](media/test-results-window.PNG)

## <a name="see-also"></a>참고 항목

- [.NET Core 및 .NET Standard의 유닛 테스트](/dotnet/core/testing)
- [유닛 테스트 시작(Windows의 Visual Studio)](/visualstudio/test/getting-started-with-unit-testing)
- [단위 테스트 기본 사항(Windows의 Visual Studio)](/visualstudio/test/unit-test-basics)
