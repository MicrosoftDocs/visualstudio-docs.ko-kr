---
title: 식 계산 컨텍스트 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738741"
---
# <a name="expression-evaluation-context"></a>식 계산 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅에서 **식 계산 컨텍스트**는 다음과 같습니다.

- 식 계산에 대 한 컨텍스트를 나타냅니다. 일반적으로 평가 컨텍스트는 변수, 매개 변수, 함수 및 메서드를 평가 하는 어휘 범위에 해당 합니다. 예를 들어 스택 프레임과 연결 된 식 계산 컨텍스트는 지역 변수, 메서드 매개 변수 및 클래스 멤버 (해당 하는 경우)를 평가 하기 위한 컨텍스트를 제공 합니다.

- 프로그램이 중단점에서 중지 된 경우에 존재 합니다. 식 자체는 지정 된 컨텍스트 내에서 바인딩 및 평가할 준비가 된 구문 분석 된 식을 나타내는 데이터 구조입니다.

     좀 더 자세히 설명 하면 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 메서드를 사용 하 여 식이 만들어집니다. 식이 계산 될 때 변수 또는 인수의 이름 및 형식과 해당 값이 포함 된 인쇄 가능한 문자열을 생성 합니다. 이 문자열은 IDE의 조사식 창 또는 지역 창에 표시 됩니다.

     `BSTR`및 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스가 제공 되는 경우 디버그 엔진 (DE)은 식을 구문 분석 하 여 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 인터페이스를 만들 수 있습니다. 인터페이스가 지정 된 경우 `IDebugExpression2` DE는 동기 또는 비동기 식 계산을 통해 값을 가져올 수 있습니다. 이 값은 변수 또는 인수의 이름 및 형식과 함께 표시를 위해 IDE에 전송 됩니다.

## <a name="see-also"></a>추가 정보
- [식 계산 인터페이스](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
