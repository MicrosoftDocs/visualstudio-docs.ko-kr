---
title: IntelliSense
description: Mac용 Visual Studio에서 IntelliSense 사용에 대한 정보
author: cobey
ms.author: cobey
ms.date: 08/16/2019
ms.openlocfilehash: 07ef1d6292e4ac88ca616d0f35e3fd831cacc649
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75405814"
---
# <a name="intellisense"></a>IntelliSense

IntelliSense는 코드 작성 및 편집 환경을 개선하는 데 도움이 되는 여러 가지 기능을 제공합니다. 예를 들어 코드 완성 외에도 IntelliSense 엔진은 멤버 목록, 매개 변수 정보 및 요약 정보를 제공합니다.

Mac용 Visual Studio에서 IntelliSense는 핵심 편집기 서비스에서 제공되며 C#, XAML, F#, JavaScript 등 다양한 언어로 지원됩니다. 또한 Mac용 Visual Studio는 아직 프로젝트로 가져오지 않은 라이브러리의 완성을 표시하는 기능과 같은 고급 IntelliSense 기능도 제공합니다.

## <a name="code-completion"></a>코드 완성

지원되는 파일(예: C# 코드 파일) 내에서 입력하는 경우 현재 입력 중인 문자열에 대한 유효한 환성이 완성 목록에 표시되고 입력함에 따라 업데이트됩니다. 또한 텍스트를 삭제하는 경우 지정된 문자열을 완성하기 위한 더 광범위한 가능성을 포함하도록 목록이 다시 자동으로 업데이트됩니다. 

또한 완성 창은 형식별로 포함된 완성을 필터링하기 위한 지원을 제공합니다. 예를 들어 클래스 또는 대리자와 같은 형식만 표시하도록 목록의 멤버를 제한할 수 있습니다. 이 필터링 프로세스는 필터링되는 형식을 나타내는 특정 아이콘을 클릭하거나 지정된 형식과 일치하는 바로 가기 키를 통해 사용하도록 설정할 수 있습니다. 완성 창의 아래쪽에 있는 아이콘은 다음과 같습니다.

| 아이콘                         | 속성          | 키워드    | 바로 가기 키 |
| -----------------------------|---------------| -----------|--------|
| ![클래스 아이콘](media/classes-icon.png)  | class         | `class`    |  ⌥C
| ![상수 아이콘](media/constant-icon.png) | constant      | `const`    |  ⌥O
| ![대리자 아이콘](media/delegate-icon.png) | 대리자      | `delegate` |  ⌥D
| ![열거형 아이콘](media/enums-icon.png)    | enum          | `enum`     |  ⌥E
| ![이벤트 아이콘](media/event-icon.png)    | 이벤트         |            |  ⌥V
| ![필드 아이콘](media/fields-icon.png)   | 필드         |            |  ⌥F
| ![인터페이스 아이콘](media/interface-icon.png)| 인터페이스     | `interface`|  ⌥I
| ![키워드 아이콘](media/keyword-icon.png)  | 키워드(keyword)       |            |  ⌥K
| ![메서드 아이콘](media/method-icon.png)   | method        |            |  ⌥M
| ![네임스페이스 아이콘](media/namespace-icon.png)| 네임스페이스     | `namespace`|  ⌥N
| ![속성 아이콘](media/props-icon.png)    | 속성      |            |  ⌥P
| ![코드 조각 아이콘](media/snippet-icon.png)  | 코드 조각       | `class`    |  ⌥S
| ![구조체 아이콘](media/struct-icon.png)   | structure     | `struct`   |  ⌥S

아이콘을 클릭하거나 해당하는 바로 가기 키를 누르면 완성 목록은 필터 세트에 정의된 형식으로만 제한됩니다.  

![IntelliSense 형식 필터링](media/intellisense-typefiltering.gif)

## <a name="parameter-window"></a>매개 변수 창

IntelliSense의 다른 기능은 해당하는 경우 매개 변수 목록을 제공하는 기능입니다. 매개 변수 목록은 호출되는 코드의 메서드 시그니처에 대한 세부 정보를 제공합니다. 시그니처 내의 위쪽/아래쪽 화살표를 클릭하면 사용 가능한 각 매개 변수 시그니처를 순환하여 사용자 필요에 가장 적합한 시그니처를 결정할 수 있습니다. 허용되는 데이터 형식의 세부 정보 외에도 XML 주석을 통해 대상 메서드에 정의된 대로 설명이 있을 수 있습니다.

![매개 변수 목록](media/intellisense-parameter.png)

매개 변수를 입력하면 현재 편집 중인 매개 변수는 굵게 표시되며 비활성 매개 변수는 표준 가중치를 포함합니다. 


## <a name="triggering-completion-window-and-parameter-window"></a>완성 창 및 매개 변수 창 트리거

완성 창은 소스 파일 내에서 입력할 때 자동으로 트리거됩니다. 그러나 바로 가기 `control-space`를 사용하여 완성 창을 트리거할 수도 있습니다. 이 키 조합을 사용하면 현재 캐럿 위치에 완성 목록이 표시됩니다. 

`control-shift-space`를 입력하여 매개 변수 창의 모양을 수동으로 트리거할 수도 있습니다. 캐럿이 매개 변수 목록에 대해 유효한 위치에 있으면 매개 변수 목록이 캐럿 위치 근처에 나타납니다.

## <a name="see-also"></a>참고 항목

- [빠른 작업(Windows의 Visual Studio)](/visualstudio/ide/quick-actions)
- [코드 리팩터링(Windows의 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
