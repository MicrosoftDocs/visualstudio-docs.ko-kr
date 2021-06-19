---
title: 코드 맵 분석기를 사용하여 잠재적 문제 찾기
description: 코드 맵에서 분석기를 실행하여 지나치게 복잡하거나 개선이 필요할 수 있는 코드를 식별하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8817e50ae96a27f6b3b76e28262390271c1fdf4c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388856"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>코드 맵 분석기를 사용하여 잠재적 문제 찾기

코드 맵에서 분석기를 실행하여 지나치게 복잡하거나 개선이 필요한 코드를 식별할 수 있습니다. 예를 들어 다음 분석기를 사용할 수 있습니다.

|**다음을 포함하는 코드 찾기**|**다음 영역을 검사하여 여부 확인**|
|-|-|
|루프 또는 순환 종속성|간소화하고 이러한 주기의 중단 가능 여부를 고려할 수 있습니다.|
|너무 많은 종속성|너무 많은 기능을 수행하고 있거나 이러한 영역 변경의 영향을 확인합니다. 잘 구성된 코드 맵은 최소 개수의 종속성을 표시합니다. 코드 유지 관리, 변경, 테스트 및 다시 사용을 더 용이하게 하려면 보다 명확하게 정의되도록 이러한 영역을 리팩터링할 수 있는지 여부 또는 유사한 기능을 수행하는 코드를 병합할 수 있는지 여부를 고려해야 합니다.|
|종속성 없음|필요하거나, 이 코드를 제거해야 하는지 여부입니다.|

## <a name="analyze-code-maps"></a>코드 맵 분석

맵 도구 모음에서 **레이아웃**  >  **분석기** 를 선택한 다음, 실행하려는 분석기를 선택합니다.

|**분석기**|**다음과 같은 노드 식별**|
|-|-|
|**순환 참조 분석기**|서로 순환 종속성이 있습니다. **참고:**  그룹을 확장할 때 **제네릭** 그룹에 있는 순환 의존성도 맵에 표시되지 않습니다.|
|**허브 분석기 찾기**|많이 연결된 상위 25% 노드에 속합니다.<br /><br /> **맵에서 다른 모든 노드를 숨기려면**<br /><br /> - 맵에 대한 바로 가기 메뉴를 열고 **고급**, 선택 , **선택되지** **않은 숨기기를** 선택합니다.<br />     맵에서 선택되지 않은 노드가 숨겨지고 분석기가 새 노드를 허브로 식별합니다.|
|**참조되지 않은 노드 분석기**|다른 노드의 참조가 없습니다. **주의:**  코드가 사용되지 않는다고 가정하기 전에 이러한 각 사례를 확인합니다. XAML 종속성 및 런타임 종속성과 같은 특정 종속성은 코드에서 정적으로 찾을 수 없습니다.|

코드 맵 분석기는 적용한 후 계속 실행됩니다. 맵을 변경하는 경우 적용된 모든 분석기가 업데이트된 맵 자동으로 다시 처리합니다. 분석기 실행을 중지하려면 맵 도구 모음에서 **레이아웃**  >  **분석기** 를 선택합니다. 선택한 분석기를 끕니다.

> [!TIP]
> 매우 큰 맵이 있는 경우 분석기를 실행할 때 메모리 부족 예외가 발생할 수 있습니다. 이 경우 맵을 편집하여 해당 범위를 줄이거나 더 작은 맵을 생성한 다음 분석기를 실행합니다.

## <a name="see-also"></a>참조

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [디버깅하는 동안 호출 스택의 맵 메서드](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
