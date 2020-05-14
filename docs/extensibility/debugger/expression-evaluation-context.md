---
title: 표현식 평가 컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738741"
---
# <a name="expression-evaluation-context"></a>식 평가 컨텍스트
디버깅에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **식 평가 컨텍스트**:

- 식 평가에 대 한 컨텍스트를 나타냅니다. 일반적으로 평가 컨텍스트는 변수, 매개 변수, 함수 및 메서드를 평가하는 어휘 범위에 해당합니다. 예를 들어 스택 프레임과 연결된 식 평가 컨텍스트는 지역 변수, 메서드 매개 변수 및 클래스 멤버(해당하는 경우)를 평가하기 위한 컨텍스트를 제공합니다.

- 프로그램이 중단점에서 중지된 경우 존재합니다. 식 자체는 지정된 컨텍스트 내에서 바인딩 및 평가할 준비가 된 구문 분석식을 나타내는 데이터 구조입니다.

     더 자세히 설명은 [ParseText 메서드를](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 사용하여 만들어집니다. 식을 평가할 때 변수 또는 인수의 이름과 형식과 해당 값을 포함하는 인쇄 가능한 문자열을 생성합니다. 이 문자열은 Watch 창 또는 IDE의 로컬 창에 표시됩니다.

     `BSTR` [IDebugExpressionContext2 인터페이스와 IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스가 주어지면 DE버그 엔진(DE)은 식을 구문 분석하여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 만들 수 있습니다. 인터페이스가 `IDebugExpression2` 주어지면 DE는 동기 식 또는 비동기 식 평가를 통해 값을 얻을 수 있습니다. 이 값은 변수 또는 인수의 이름 및 유형과 함께 표시를 위해 IDE로 전송됩니다.

## <a name="see-also"></a>참조
- [표현식 평가 인터페이스](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
