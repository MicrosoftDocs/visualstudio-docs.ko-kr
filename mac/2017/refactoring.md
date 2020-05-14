---
title: 코드 리팩터링
description: 소스 분석을 사용하면 Mac용 Visual Studio에서 코드를 간편하게 재구성할 수 있습니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985243"
---
# <a name="refactoring"></a>리팩터링

코드를 리팩터링하면 코드의 전반적인 동작을 변경하지 않으면서 기존의 코드를 재정렬 및 재구성하고 명확하게 나타낼 수 있습니다.

리팩터링은 안정성이 더 높은 코드베이스를 제공하므로 본인이나 코드를 참조할 수 있는 다른 개발자 혹은 사용자가 더 쉽게 사용하고 읽고 유지 관리할 수 있습니다.

Mac용 Visual Studio는 Microsoft의 오픈 소스 .NET 컴파일러 플랫폼인 Roslyn과 통합되어 더 많은 리팩터링 작업을 수행할 수 있도록 합니다.

## <a name="renaming"></a>이름 바꾸기

*이름 바꾸기* 리팩터링 명령은 모든 코드 식별자(예: 클래스 이름, 속성 이름)에 사용하여 해당 식별자와 일치하는 항목을 찾아 변경할 수 있습니다. 기호의 이름을 바꾸려면 기호를 마우스 오른쪽 버튼으로 클릭한 다음 **리팩터링 > 이름 바꾸기** 또는 **Cmd+R** 키 바인딩을 선택하세요.

![메뉴 항목 이름 바꾸기](media/refactoring-renaming1.png)

이렇게 하면 기호와 기호에 대한 모든 참조가 강조 표시됩니다. 새 이름을 입력하면 코드 내의 모든 참조가 자동으로 변경되며, **Enter**를 눌러 이름 바꾸기가 완료되었음을 알릴 수 있습니다.

![이름 바꾸기 및 식별자](media/refactoring-renaming2.png)

## <a name="context-actions"></a>컨텍스트 작업

컨텍스트 작업을 통해 C# 코드를 검사하고 가능한 리팩터링 옵션을 전부 확인할 수 있습니다.

**해결** 및 **리팩터링** 컨텍스트 항목이 사용 가능한 모든 컨텍스트 작업을 제공하는 하나의 *빠른 수정...* 항목으로 결합되었습니다.

![컨텍스트 항목 표시](media/refactoring-context-action.png)

컨텍스트 작업을 마우스로 가리키면 코드에서 추가하거나 제거할 내용을 미리 볼 수 있습니다.

또는 코드의 원하는 위치에서 **Option+Enter**를 눌러도 됩니다.

![Option Enter 컨텍스트 항목](media/refactoring-image2a.png)

이러한 옵션을 사용하도록 설정하려면 *Mac용 Visual Studio > 기본 설정 > 텍스트 편집기 > 소스 분석*에서 **열린 파일의 소스 분석 사용**을 선택해야 합니다.

![소스 분석을 사용하도록 설정](media/refactoring-options.png)

100개 이상의 작업이 제시될 수 있습니다. 이러한 작업은 **Mac용 Visual Studio > 기본 설정 > 소스 분석 > C# > 코드 동작**으로 이동하고 작업 옆의 상자를 선택하거나 선택 해제하여 사용 여부를 설정할 수 있습니다.

![C# 소스 분석 작업](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>일반적인 컨텍스트 작업

가장 자주 사용되는 컨텍스트 작업 중 일부는 아래에 설명되어 있습니다.

#### <a name="extract-method"></a>메서드 추출

메서드 추출 리팩터링 작업을 사용하면 기존 멤버에서 선택한 코드를 추출하여 새 메서드를 만들 수 있습니다. 이 작업은 다음 두 가지를 수행합니다.

* 선택한 코드를 포함하는 새 메서드를 만듭니다.
* 선택한 코드가 있는 곳에서 새 메서드를 호출합니다.

##### <a name="example"></a>예제

1. 다음 코드를 추가합니다.

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. `double volume = (baseArea * height) / 3;` 줄을 강조 표시하고 마우스 오른쪽 단추로 클릭한 다음 **리팩터링 > 메서드 추출**을 선택합니다.

3. 화살표 키를 사용하여 코드 내에서 새 메서드를 배치할 위치를 선택합니다.

#### <a name="encapsulate-field"></a>필드 캡슐화

필드 캡슐화 작업을 통해 기존 필드로부터 속성을 만들고 새로 만든 속성을 참조하도록 코드를 업데이트할 수 있습니다. 필드를 캡슐화하는 속성을 만들면 공용 필드에 직접 액세스할 수 없도록 하여 다른 개체가 필드를 수정할 수 없습니다.

이 작업은 다음을 수행합니다.

* 액세스 한정자를 비공개로 변경합니다.
* 필드에 getter 및 setter를 생성합니다(단, 필드가 읽기 전용이 아니어야 하며, 읽기 전용인 경우에는 getter만 생성).

## <a name="source-analysis"></a>소스 분석

소스 분석을 수행하면 가능한 오류 및 스타일 위반을 밑줄 표시하고 자동 수정을 컨텍스트 작업으로 제공하여 코드를 즉시 분석합니다.

텍스트 편집기의 오른쪽에 있는 스크롤 막대를 보면 언제든지 모든 파일의 소스 분석 결과를 모두 확인할 수 있습니다.

![소스 분석 사이드바](media/refactoring-image4a.png)

상단의 원을 클릭하면 심각도가 가장 높은 문제부터 순서대로 표시된 상태에서 각 제안을 반복할 수 있습니다. 개별 결과나 줄을 마우스로 가리키면 문제가 표시되며, 이 문제는 컨텍스트 작업을 통해 수정할 수 있습니다.

![소스 분석 항목](media/refactoring-image5.png)

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>참고 항목

- [빠른 작업(Windows의 Visual Studio)](/visualstudio/ide/quick-actions)
- [코드 리팩터링(Windows의 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)