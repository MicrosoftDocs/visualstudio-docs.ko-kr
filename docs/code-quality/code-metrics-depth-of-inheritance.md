---
title: 코드 메트릭-상속 수준
ms.date: 1/8/2021
description: Visual Studio의 코드 메트릭에 대 한 상속 메트릭의 깊이에 대해 알아봅니다.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1d6ac085463087fc73aac4429488ab475e91c10f
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682579"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>코드 메트릭-상속 수준 (DIT)

이 문서에서는 개체 지향 분석을 위해 특별히 디자인 된 메트릭 중 하나에 대해 알아봅니다. 상속 수준 상속 수준 (DIT (상속 트리)이 라고도 함)은 "노드의 최대 길이를 트리의 트리" [헤드](#ck)"로 정의 합니다. 간단한 예제를 통해이를 확인할 수 있습니다. 새 클래스 라이브러리 프로젝트를 만들고, 코드를 작성 하기 전에 **솔루션에 대 한 코드 메트릭을 분석 > 계산** 을 선택 하 여 코드 메트릭을 계산 합니다.

![상속 수준 예 1](media/depth-of-inheritance-example-1.png)

모든 클래스는에서 상속 하므로 `System.Object` 현재 깊이가 1입니다. 이 클래스에서 상속 하 고 새 클래스를 검사 하는 경우 결과를 볼 수 있습니다.

![상속 수준 예 2](media/depth-of-inheritance-example-2.png)

트리의 노드가 작을수록 ( `Class2` 이 경우) 상속 깊이가 높아집니다 .입니다. 계속 해 서 자식을 만들고 깊이를 원하는 만큼 늘릴 수 있습니다.

## <a name="assumptions"></a>가정

상속 수준은 세 가지 [기본적인 가정에](#ck)따라 예측 됩니다.

1. 계층 구조에서 클래스가 더 심층적으로 상속 되는 메서드의 수가 클수록 해당 동작을 예측 하기 어려워집니다.

2. 더 깊은 트리는 더 많은 클래스와 메서드가 관련 되기 때문에 더 많은 디자인 복잡성을 포함 합니다.

3. 트리의 더 깊은 클래스는 상속 된 메서드를 다시 사용할 가능성이 높습니다.

가정 1과 2는 깊이에 대해 더 높은 수를 갖는 것이 잘못 되었음을 알려 줍니다. 종료 되는 경우 좋은 셰이프입니다. 그러나 가정 3은 높은 수준의 깊이가 잠재적 코드 재사용에 적합 하다는 것을 나타냅니다.

## <a name="analysis"></a>분석

깊이 메트릭을 읽는 방법은 다음과 같습니다.

- 깊이에 대한 낮은 수

  깊이가 낮을수록 복잡성은 줄어들지만 상속을 통해 코드를 다시 사용할 가능성도 줄어듭니다.

- 깊이에 대한 높은 수

  깊이가 높을수록 상속을 통해 코드가 재사용할 가능성이 더 높고 코드에서 오류가 발생할 가능성이 높아질수록 복잡성도 높아질 수 있습니다.

## <a name="code-analysis"></a>코드 분석

코드 분석에는 유지 관리 규칙 범주가 포함됩니다. 자세한 내용은 [유지 관리 규칙 을 참조하세요.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) 레거시 코드 분석을 사용하는 경우 확장 디자인 지침 규칙 집합에는 유지 관리 영역이 포함됩니다.

![상속 디자인 지침 규칙 집합의 깊이](media/depth-of-inheritance-design-guidelines.png)

유지 관리 영역 내에는 상속에 대한 규칙이 있습니다.

![상속 유지 관리 규칙의 깊이](media/depth-of-inheritance-maintainability-rule.png)

이 규칙은 상속 깊이가 6 이상에 도달하면 경고를 발생하므로 과도한 상속을 방지하는 데 도움이 되는 좋은 규칙입니다. 규칙에 대한 자세한 내용은 [CA1501을](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)참조하세요.

## <a name="putting-it-all-together"></a>모두 결합

DIT 값이 높으면 오류 가능성도 높고, 값이 낮으면 오류 가능성이 줄어듭니다. DIT에 대한 높은 값은 상속을 통해 코드가 재사용할 가능성이 더 높음을 나타내며, 값이 낮을수록 상속을 활용하기 위해 코드 재사용이 줄어듭니다. 충분한 데이터가 부족하기 때문에 DIT 값에 대해 현재 허용되는 표준이 없습니다. 최근에 수행한 연구도 이 메트릭 [Shatnawi](#shatnawi)의 표준 숫자로 사용할 수 있는 실행 가능한 숫자를 결정하기에 충분한 데이터를 찾지 못했습니다. 이를 지원하는 경험적 증거도 없지만, 여러 리소스에서 DIT 5 또는 6이 상한이어야 한다고 제안합니다. 예를 들어 를 [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) 참조하세요.

## <a name="citations"></a>인용

### <a name="ck"></a>CK

Chidamber, S. R. & Kemerer, C. F. (1994). Metrics Suite for Object Oriented Design(소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 20, 아니요. 6). 2011년 5월 14일 University of University 웹 사이트에서 검색: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramanyam, R. & Krishnan, M. S. (2003). Object-Oriented 디자인 복잡성에 대한 CK 메트릭의 경험적 분석: 소프트웨어 결함에 대한 영향(소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 29, 아니요. 4). 검색된 2011년 5월 14일, 원래 University of University of일보이루시 웹 사이트에서 입사 [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). 소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 36, 아니요의 Open-Source Systems에서 허용되는 위험 수준의 Object-Oriented 메트릭에 대한 정량적 조사입니다. 2).