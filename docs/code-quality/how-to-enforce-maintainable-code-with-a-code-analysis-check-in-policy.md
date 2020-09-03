---
title: 코드 분석 체크 인 정책 사용
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 883b5e231036c446c1cbf1fbc2fc125a01b3de62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371861"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>방법: 코드 분석 체크 인 정책을 사용 하 여 유지 가능한 코드 적용

개발자는 코드 메트릭 도구를 사용 하 여 코드의 복잡성 및 유지 관리를 측정할 수 있지만 체크 인 정책의 일부로 코드 메트릭을 호출할 수 없습니다. 그러나 코드 메트릭 표준을 사용 하 여 코드의 호환성을 확인 하 고 체크 인 정책을 통해 규칙을 적용 하는 코드 분석 규칙을 사용 하도록 설정할 수 있습니다. 코드 메트릭에 대 한 자세한 내용은 [코드 메트릭 값](../code-quality/code-metrics-values.md)을 참조 하세요.

코드 분석 체크 인 정책을 통해 유지 관리할 수 있는 코드를 적용 하기 위해 상속, 클래스 결합, 유지 관리 인덱스 및 복잡성 규칙의 깊이를 사용 하도록 설정할 수 있습니다. 이러한 규칙 중 4 개는 코드 분석 정책 편집기의 "유지 관리 규칙" 범주 아래에 있습니다.

Team Foundation에 대 한 버전 제어 관리자는 체크 인 정책 요구 사항에 코드 분석 유지 관리 규칙을 추가할 수 있습니다. 이러한 체크 인 정책을 사용 하려면 체크 인을 시작 하기 전에 개발자가 이러한 규칙 변경에 따라 코드 분석을 실행 해야 합니다.

## <a name="to-open-the-code-analysis-policy-editor"></a>코드 분석 정책 편집기를 열려면

1. **팀 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **프로젝트 설정**을 클릭 한 다음 **소스 제어**를 클릭 합니다.

     **소스 제어** 대화 상자가 나타납니다.

2. 체크 인 **정책** 탭에서 **추가**를 클릭 합니다.

     **체크 인 정책 추가** 대화 상자가 나타납니다.

3. 체크 인 **정책** 목록에서 **코드 분석** 확인란을 선택 하 고 **확인**을 클릭 합니다.

     **코드 분석 정책 편집기** 대화 상자가 나타납니다.

## <a name="to-enable-code-analysis-maintainability-rules"></a>코드 분석 유지 관리 규칙을 사용 하려면

1. **코드 분석 정책 편집기** 대화 상자의 **규칙 설정**에서 **유지 관리 규칙** 노드를 확장 합니다.

2. 다음 규칙의 확인란을 선택 합니다.

   - 상속 깊이: **CA1501 AvoidExcessiveInheritance** : 5 수준 이상으로 경고

   - 복잡성: **CA1502 AvoidExcessiveComplexity** : 25 이상의 경고

   - 유지 관리 인덱스: **CA1505 AvoidUnmaintainableCode** : 20 미만의 경고

   - 클래스 결합: **CA1506 AvoidExcessiveClassCoupling** : 클래스의 경우 80 이상, 메서드의 경우 30 개 이상에 대 한 경고

     또한 성공적인 빌드를 방지 하는 규칙 위반을 원하는 경우 규칙 설명 옆에 있는 **경고를 오류로 처리** 확인란을 선택 합니다.

3. **확인**을 클릭합니다. 이제 새 체크 인 정책이 이후 체크 인에 적용 됩니다.

## <a name="see-also"></a>추가 정보

- [코드 메트릭 값](../code-quality/code-metrics-values.md)
- [코드 분석 체크 인 정책 만들기 및 사용](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)
