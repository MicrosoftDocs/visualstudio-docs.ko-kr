---
title: 코드 메트릭-클래스 결합
ms.date: 1/8/2021
description: Visual Studio의 코드 메트릭에 대 한 클래스 결합 메트릭에 대해 알아봅니다.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666811"
---
# <a name="code-metrics---class-coupling"></a>코드 메트릭-클래스 결합

또한 클래스 커플링은 [CK94](#ck94)에 의해 정의 된 대로 개체 간 이름 결합 (CBO)으로 이동 합니다. 기본적으로 클래스 결합은 단일 클래스에서 사용 하는 클래스의 수를 측정 한 것입니다. 숫자가 높으면 일반적으로이 메트릭에 적합 합니다. 클래스 결합은 소프트웨어 오류를 정확 하 게 예측 하는 것으로 표시 되었으며, 최근 연구에서는 상한 값 9가 가장 효율적인 [S2010](#s2010)을 보여 줍니다.

Microsoft 문서에 따라 클래스 결합은 매개 변수, 지역 변수, 반환 형식, 메서드 호출, 제네릭 또는 템플릿 인스턴스화, 기본 클래스, 인터페이스 구현, 외부 형식에 정의 된 필드 및 특성 데코레이션을 통해 고유 클래스에 대 한 결합을 측정 합니다. 좋은 소프트웨어 디자인은 유형과 메서드가 높은 응집 및 낮은 결합을 가져야 함을 나타냅니다. 높은 결합은 다른 형식에 대 한 많은 상호 종속성으로 인해 재사용 및 유지 관리가 어려운 디자인을 나타냅니다. "

결합 및 응집의 개념은 명확 하 게 관련 되어 있습니다. 항목에 대 한이 토론을 유지 하기 위해 [KKLS2000](#kkls2000)에서 간략 한 정의를 제공 하는 것 외에는 응집에 대해 자세히 설명 하지 않습니다.

"모듈 응집은 모듈의 내부 요소와 밀접 하 게 바인딩된 또는 관련 된 요소를 다른 ' [YC79](#yc79)'로 Constantine 하 여 도입 되었습니다. 모듈은 정확히 하나의 작업 [...]을 나타내고 모든 요소가이 단일 작업에 기여 하는 경우 강력한 응집을 가집니다. 이러한 특성은 코드 대신 디자인의 특성으로 응집을 설명 하 고 재사용 가능, 유지 관리 가능 및 changeability을 예측 하는 데 사용할 수 있는 특성을 설명 합니다. "

## <a name="class-coupling-example"></a>클래스 결합 예제

작업의 클래스 결합을 살펴보겠습니다. 먼저 새 콘솔 응용 프로그램을 만들고, 일부 속성을 가진 Person 이라는 새 클래스를 만든 다음, 코드 메트릭을 즉시 계산 합니다.

![클래스 결합 예 1](media/class-coupling-example-1.png)

이 클래스는 다른 클래스를 사용하지 않으므로 클래스 결합은 0입니다. 이제 Person의 인스턴스를 만들고 속성 값을 설정하는 메서드를 사용하여 PersonStuff라는 다른 클래스를 만듭니다. 코드 메트릭을 다시 계산합니다.

![클래스 결합 예제 2](media/class-coupling-example-2.png)

클래스 결합 값이 어떻게 상승하는지 확인하세요. 또한 설정한 속성 수에 관계없이 클래스 결합 값은 다른 값이 아니라 1씩 상승합니다. 클래스 결합은 사용되는 양에 관계없이 이 메트릭에 대해 각 클래스를 한 번만 측정합니다. 또한 가 `DoSomething()` 1이지만 생성자 에 `PersonStuff()` 값이 0인 것을 볼 수 있나요? 현재 다른 클래스를 사용하는 생성자에는 코드가 없습니다.

다른 클래스를 사용하는 생성자에 코드를 배치하면 어떻게 될까요? 얻을 수 있는 것은 다음과 같습니다.

![클래스 결합 예제 3](media/class-coupling-example-3.png)

이제 생성자에는 다른 클래스를 사용하는 코드가 분명히 있으며 클래스 결합 메트릭은 이 사실을 보여줍니다. 마찬가지로 에 대한 전체 클래스 `PersonStuff()` 결합이 1이고 가 `DoSomething()` 1임을 확인하여 사용하는 내부 코드의 양에 관계없이 하나의 외부 클래스만 사용되고 있음을 보여 드립니다.

다음으로, 다른 새 클래스를 만듭니다. 이 클래스에 이름을 지정하고 그 안에 몇 가지 속성을 만듭니다.

![클래스 결합 예제 - 새 클래스 추가](media/class-coupling-example-add-new-class.png)

이제 클래스 `DoSomething()` 내의 메서드에서 클래스를 사용하고 `PersonStuff` 코드 메트릭을 다시 계산합니다.

![클래스 결합 예제 4](media/class-coupling-example-4.png)

보시는 것처럼 PersonStuff 클래스에 대한 클래스 결합은 최대 2까지 진행되며, 클래스를 드릴다운하면 `DoSomething()` 메서드에 가장 많은 결합이 있지만 생성자는 여전히 1개의 클래스만 사용한다는 것을 알 수 있습니다.  이러한 메트릭을 사용 하 여 지정 된 클래스의 전체 최대 개수를 확인 하 고 멤버 별로 세부 정보를 드릴 다운할 수 있습니다.

## <a name="the-magic-number"></a>매직 넘버입니다.

순환 복잡성과 마찬가지로 모든 조직에 맞는 제한이 없습니다. 그러나 [S2010](#s2010) 는 다음과 같이 제한 9가 최적 임을 의미 합니다.

"따라서 [...] 임계값을 고려 합니다. 가장 효과적입니다. 단일 멤버에 대 한 이러한 임계값은 CBO = 9 [...]. "입니다. (추가 된 강조)

## <a name="code-analysis"></a>코드 분석

코드 분석에는 유지 관리 규칙의 범주가 포함 되어 있습니다. 자세한 내용은 [유지 관리 규칙](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings)을 참조 하세요. 레거시 코드 분석을 사용 하는 경우 확장 된 디자인 지침 규칙 집합에는 유지 관리 영역이 포함 됩니다.

![클래스 결합 확장 디자인 지침 규칙](media/class-coupling-extended-design-guideline-rules.png)

유지 관리 영역 내에는 클래스 결합에 대 한 규칙이 있습니다.

![클래스 결합 규칙](media/class-coupling-maintainability-area-rules.png)

이 규칙은 클래스가 과도 하 게 결합 되었을 때 경고를 발생 합니다. 자세한 내용은 [CA1506: 과도 한 클래스 결합 방지](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)를 참조 하세요.

## <a name="citations"></a>인용

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, c. (1994). Metrics Suite for Object Oriented Design(소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 20, 아니요. 6). 검색: 2011년 5월 14일, University of University of University 웹 사이트: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F., And 생드니, G. (2000). 클래스 응집력 재방문: 산업 시스템에 대한 경험적 연구(Object-Oriented Software Engineering의 정량적 접근 방식 워크샵 진행) 검색: 2011년 5월 20일, 2011년 5월 20일, 2017년 5월 20일 [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Object-Oriented 디자인 복잡성에 대한 CK 메트릭의 경험적 분석: 소프트웨어 결함에 대한 영향(소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 29, 아니요. 4). 검색된 2011년 5월 14일, University of University of University지부의 2011년 5월 14일 웹 사이트 [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). 소프트웨어 엔지니어링의 IEEE 트랜잭션, Vol. 36, 아니요의 Open-Source Systems에서 허용되는 위험 수준의 Object-Oriented 메트릭에 대한 정량적 조사입니다. 2).

### <a name="yc79"></a>YC79

사용자도메인과 2016년 4월 1일, 2016년 10월 12일 구조적 디자인. Prentice Hall, Englewood의 경우 N.J., 1979.