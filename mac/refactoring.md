---
title: 코드 리팩터링
description: Mac용 Visual Studio 및 빠른 작업을 사용하여 코드를 개선합니다.
author: jmatthiesen
ms.author: jomatthi
ms.date: 07/03/2020
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3892117e5c84a71f258d4e019105fca0a8cf9c5b
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402592"
---
# <a name="refactoring"></a>리팩터링

코드를 리팩터링하면 코드의 전반적인 동작을 변경하지 않으면서 기존의 코드를 재정렬 및 재구성하고 명확하게 나타낼 수 있습니다.

리팩터링은 안정성이 더 높은 코드베이스를 제공하므로 본인이나 코드를 참조할 수 있는 다른 개발자 혹은 사용자가 더 쉽게 사용하고 읽고 유지 관리할 수 있습니다.

Mac용 Visual Studio는 Microsoft의 오픈 소스 .NET 컴파일러 플랫폼인 Roslyn과 통합되어 더 많은 리팩터링 작업을 수행할 수 있도록 합니다.

## <a name="renaming"></a>이름 바꾸기

*이름 바꾸기* 리팩터링 명령은 모든 코드 식별자(예: 클래스 이름, 속성 이름)에 사용하여 해당 식별자와 일치하는 항목을 찾아 변경할 수 있습니다. 기호의 이름을 바꾸려면 기호를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기...** 를 선택하거나 **Cmd(⌘) + R** 키 바인딩을 사용합니다.

![메뉴 항목 이름 바꾸기](media/refactoring-renaming1.png)

이렇게 하면 기호와 기호에 대한 모든 참조가 강조 표시됩니다. 새 이름을 입력하면 코드 내의 모든 참조가 자동으로 변경되고 **Enter**를 눌러 변경 내용을 커밋할 수 있습니다.

![이름 바꾸기 및 식별자](media/refactoring-renaming2.png)

## <a name="quick-actions-and-refactorings"></a>빠른 작업 및 리팩터링

빠른 작업과 리팩터링을 사용하면 단일 작업으로 쉽게 코드를 리팩터링하거나 생성하거나 수정할 수 있습니다.

빠른 작업은 다음에 사용할 수 있습니다.

* 코드 분석기 규칙 위반에 대한 코드 수정 적용
* 코드 분석기 규칙 위반 표시 안 함
* 리팩터링 적용(예: 임시 변수 인라인)
* 코드 생성(예: 지역 변수 도입)

빠른 작업은 전구 ![전구 아이콘](media/quick-actions-light-bulb-icon.png) 또는 스쿠루 드라이버![스크루 드라이버 아이콘](media/quick-actions-screwdriver-icon.png) 아이콘을 사용하거나 커서가 작업을 사용할 수 있는 코드 줄에 있을 때 **옵션(⌥)** +**Enter**를 눌러 적용할 수 있습니다. 오류를 나타내는 빨간 물결 무늬가 있는 경우 오류 전구![오류 전구 아이콘](media/quick-actions-error-light-bulb-icon.png)가 표시되고 Visual Studio에는 해당 오류에 사용할 수 있는 해결 방법이 있습니다.

어떤 언어든지 타사에서 SDK에 포함하는 방식 등을 통해 사용자 지정 진단 및 제안을 제공할 수 있으며 Visual Studio 전구는 이러한 규칙을 기반으로 켜집니다.

### <a name="quick-action-icons"></a>빠른 작업 아이콘
빠른 작업을 사용할 수 있을 때 나타나는 아이콘은 사용 가능한 해결 방법 또는 리팩터링 형식을 나타냅니다. *스크루드라이버* ![스크루드라이버 아이콘](media/quick-actions-screwdriver-icon.png) 아이콘은 코드를 변경하는 데 사용할 수 있는 작업이 있음을 나타내지만 반드시 사용해야 하는 것은 아닙니다. *노란색 전구* ![전구 아이콘](media/quick-actions-light-bulb-icon.png) 아이콘은 코드 개선을 위해 *해야 하는* 작업이 있음을 나타냅니다. *오류 전구* ![오류 전구 아이콘](media/quick-actions-error-light-bulb-icon.png) 아이콘은 코드에서 오류를 수정하는 데 사용할 수 있는 작업이 있음을 나타냅니다.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>전구 또는 스크루드라이버를 표시하려면

- 해결 방법을 사용할 수 있는 경우 오류 위치를 마우스로 가리킬 때 전구가 자동으로 나타납니다.

   ![마우스로 가리킨 전구](media/refactoring-lightbulb-hover.png)

- 빠른 작업 또는 리팩터링을 사용할 수 있는 코드 줄로 캐럿을 옮기면 전구 및 스크루드라이버가 편집기의 왼쪽 여백에 나타납니다.

- **옵션(⌥)** +**Enter**를 눌러 사용 가능한 빠른 작업 및 리팩토링 목록을 어디에서나 볼 수 있습니다.

![컨텍스트 항목 표시](media/refactoring-context-action.png)

컨텍스트 작업을 마우스로 가리키면 코드에서 추가하거나 제거할 내용을 미리 볼 수 있습니다.

![Option Enter 컨텍스트 항목](media/refactoring-image2a.png)

이러한 옵션을 사용하도록 설정하려면 **Mac용 Visual Studio > 기본 설정 > 텍스트 편집기 > 소스 분석**에서 *열린 파일의 소스 분석 사용*을 선택해야 합니다.

![소스 분석을 사용하도록 설정](media/refactoring-options.png)

100개 이상의 작업이 제시될 수 있습니다. 이러한 작업은 **Mac용 Visual Studio > 기본 설정 > 소스 분석 > C# > 코드 동작**으로 이동하고 작업 옆의 상자를 선택하거나 선택 해제하여 사용 여부를 설정할 수 있습니다.

![C# 소스 분석 작업](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>일반적인 빠른 작업

[일반적인 빠른 작업](/visualstudio/ide/common-quick-actions) 문서에서 일반적인 빠른 작업에 대해 자세히 알아볼 수 있습니다.

## <a name="source-analysis"></a>소스 분석

소스 분석을 수행하면 가능한 오류 및 스타일 위반을 밑줄 표시하고 자동 수정을 컨텍스트 작업으로 제공하여 코드를 즉시 분석합니다.

텍스트 편집기의 오른쪽에 있는 스크롤 막대를 보면 언제든지 모든 파일의 소스 분석 결과를 모두 확인할 수 있습니다.

![소스 분석 사이드바](media/refactoring-image4a.png)

상단의 원을 클릭하면 심각도가 가장 높은 문제부터 순서대로 표시된 상태에서 각 제안을 반복할 수 있습니다. 개별 결과나 줄을 마우스로 가리키면 문제가 표시되며, 이 문제는 컨텍스트 작업을 통해 수정할 수 있습니다.

![소스 분석 항목](media/refactoring-image5.png)

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>참조

- [빠른 작업(Windows의 Visual Studio)](/visualstudio/ide/quick-actions)
- [코드 리팩터링(Windows의 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
