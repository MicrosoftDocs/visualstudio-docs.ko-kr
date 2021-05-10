---
title: 코드 메트릭-순환 복잡성
ms.date: 5/7/2021
description: Visual Studio의 코드 메트릭에 대 한 순환 복잡성 메트릭에 대해 알아봅니다.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682575"
---
# <a name="code-metrics---cyclomatic-complexity"></a>코드 메트릭-순환 복잡성

코드 메트릭을 사용 하는 경우 가장 잘 이해 되지 않는 항목 중 하나는 순환 복잡성으로 보입니다. 기본적으로 순환 복잡성을 사용 하는 경우 숫자가 높고 숫자가 낮을수록 좋습니다. 순환 복잡성을 사용 하 여 코드에서 오류를 생성 하는 정도를 표시 하는 것은 물론, 지정 된 코드가 테스트, 유지 관리 또는 문제 해결을 수행할 수 있는 정도를 파악할 수 있습니다. 개략적인 수준에서 소스 코드에서 결정 한 수를 계산 하 여 순환 복잡성의 가치를 확인 합니다. 이 문서에서는 개념을 신속 하 게 이해 하기 위해 순환 복잡성의 간단한 예를 사용 하 여 시작 하 고 실제 사용량과 권장 한도에 대 한 추가 정보를 확인 합니다. 마지막으로,이 주제를 심층적으로 파악 하는 데 사용할 수 있는 인용 섹션이 있습니다.

## <a name="example"></a>예제

순환 복잡성은 "소스 코드 함수에서 의사 결정 논리의 양" [NIST235](#nist235)을 측정 하는 것으로 정의 됩니다. 간단히 말해서, 코드에서 수행 해야 하는 더 많은 결정이 더 복잡해 집니다.

작동 하 고 있는 것을 확인해 보겠습니다. **솔루션에 대 한 코드 메트릭을 분석 > 계산** 으로 이동 하 여 새 콘솔 응용 프로그램을 만들고 즉시 코드 메트릭을 계산 합니다.

![순환 복잡성 예 1](media/cyclomatic-complexity-example-1.png)

순환 복잡성은 2 (가능한 가장 낮은 값)입니다. 의사 결정 코드가 아닌 코드를 추가 하는 경우 복잡성이 변경 되지 않습니다.

![순환 복잡성 예 2](media/cyclomatic-complexity-example-2.png)

결정을 추가 하면 순환 복잡성 값이 1로 증가 합니다.

![순환 복잡성 예 3](media/cyclomatic-complexity-example-3.png)

4 개의 결정을 내리는 switch 문으로 if 문을 변경 하면 원래 2에서 6으로 이동 합니다.

![순환 복잡성 예제 4](media/cyclomatic-complexity-example-4.png)

(가상의) 더 큰 코드 베이스를 살펴보겠습니다.

![순환 복잡성 예제 5](media/cyclomatic-complexity-example-5.png)

Products_Related 클래스로 드릴다운할 때 대부분의 항목의 값은 1이지만 두 항목의 복잡성은 5입니다. 그 자체로는 큰 문제가 아닐 수 있지만, 대부분의 다른 멤버가 동일한 클래스에 1이 있는 경우 해당 두 항목을 더 자세히 살펴보고 해당 항목에 무엇이 있는지 확인해야 합니다. 항목을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **소스 코드로 이동을** 선택하여 이 작업을 수행할 수 있습니다. 를 자세히 `Product.set(Product)` 살펴보세요.

![순환 복잡성 예제 6](media/cyclomatic-complexity-example-6.png)

if 문을 모두 지정하면 순환 복잡성이 5인 이유를 확인할 수 있습니다. 이 시점에서 허용되는 복잡성 수준이라고 결정하거나 복잡성을 줄이기 위해 리팩터로 사용할 수 있습니다.

## <a name="the-magic-number"></a>매직 넘버

이 업계의 많은 메트릭과 마찬가지로 모든 조직에 맞는 정확한 순환 복잡성 제한은 없습니다. 그러나 [NIST235는](#nist235) 10이라는 제한이 좋은 시작점임을 나타냅니다.

"제한으로 사용할 정확한 수는 다소 많이 남아 있습니다. McCabe에서 제안한 원래 제한인 10은 상당한 지원 증거를 가지고 있지만 15까지의 제한도 성공적으로 사용되었습니다. 10개 이상의 제한은 숙련된 직원, 공식 디자인, 최신 프로그래밍 언어, 구조적 프로그래밍, 코드 연습 및 포괄적인 테스트 계획과 같은 일반적인 프로젝트에 비해 운영상의 이점이 여러 개 있는 프로젝트에 예약되어야 합니다. 즉, 조직은 10보다 큰 복잡성 한도를 선택할 수 있지만, 조직이 수행하는 작업을 알고 있고 더 복잡한 모듈에 필요한 추가 테스트 작업을 수행하려는 경우에만 선택할 수 있습니다." [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>순환 복잡성 및 줄 번호

코드 줄 자체를 살펴보는 것만으로도 코드 품질을 매우 광범위하게 예측할 수 있습니다. 함수에서 코드의 줄 수가 많을 수록 오류가 있을 가능성이 높습니다 .이 경우에는 몇 가지 기본 사항이 있습니다. 그러나 순환 복잡성을 코드 줄과 결합 하면 오류 발생 가능성을 훨씬 명확 하 게 파악할 수 있습니다.

NASA의 소프트웨어 보증 기술 센터 (SATC)에서 설명 하는 대로:

"SATC에서 가장 효과적인 평가가 크기와 (순환) 복잡성의 조합을 발견 했습니다. 복잡성이 높고 크기가 큰 모듈은 안정성이 낮습니다. 크기와 복잡성이 낮은 모듈은 매우 간결한 코드 이므로 변경 하거나 수정 하기가 쉽지 않기 때문에 안정성 위험이 있습니다. " [SATC](#satc)

## <a name="code-analysis"></a>코드 분석

코드 분석에는 유지 관리 규칙의 범주가 포함 되어 있습니다. 자세한 내용은 [유지 관리 규칙](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings)을 참조 하세요. 레거시 코드 분석을 사용 하는 경우 확장 된 디자인 지침 규칙 집합에는 유지 관리 영역이 포함 됩니다.

![순환 복잡성 디자인 지침 규칙 집합](media/cyclomatic-complexity-design-guidelines.png)

유지 관리 영역 내에는 복잡성을 위한 규칙이 있습니다.

![순환 복잡성 유지 관리 규칙](media/cyclomatic-complexity-maintainability-rule.png)

이 규칙은 순환 복잡성이 25에 도달할 때 경고를 발생 하므로 과도 한 복잡성을 방지 하는 데 도움이 될 수 있습니다. 규칙에 대 한 자세한 내용은 [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) 를 참조 하세요.

## <a name="putting-it-all-together"></a>모두 함께 배치

맨 아래 줄은 복잡성이 높으면 유지 관리 하 고 문제를 해결할 수 있는 오류가 발생할 확률이 높아집니다. 복잡성이 높은 함수를 좀 더 자세히 살펴보고 덜 복잡 하 게 만들기 위해 리팩터링 해야 하는지 결정 합니다.

## <a name="citations"></a>인용

### <a name="mccabe5"></a>MCCABE5

McCabe, T. and A. Watson (1994), Software Complexity (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). 구조적 테스트: 순환 복잡성 메트릭을 사용하는 테스트 방법론(NIST 특별 게시 500-235). 2011년 5월 14일 McCabe Software 웹 사이트에서 검색: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

1998년, 1998년. 소프트웨어 메트릭 및 안정성(소프트웨어 안정성 엔지니어링에 대한 IEEE International Symposium의 절차) 검색: 2011년 5월 14일, 작성자: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)