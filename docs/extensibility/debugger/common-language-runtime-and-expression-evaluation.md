---
title: 공통 언어 런타임 및 표현식 평가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739115"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>공통 언어 런타임 및 표현식 평가
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 공통 언어 런타임(CLR)을 대상으로 하는 시각적 기본 및 C#(C-sharp로 발음됨)과 같은 컴파일러는 나중에 네이티브 코드로 컴파일되는 MSIL(Microsoft 중간 언어)을 생성합니다. CLR은 결과 코드를 디버깅하는 DE(디버그 엔진)를 제공합니다. 고유한 프로그래밍 언어를 Visual Studio IDE에 통합하려는 경우 MSIL에 컴파일하도록 선택할 수 있으므로 사용자 고유의 DE를 작성할 필요가 없습니다. 그러나 프로그래밍 언어의 컨텍스트 내에서 식을 평가할 수 있는 식 평가기(EE)를 작성해야 합니다.

## <a name="discussion"></a>토론
 컴퓨터 언어 표현식은 일반적으로 데이터 개체 집합과 이를 조작하는 데 사용되는 연산자 집합을 생성하기 위해 구문 분석됩니다. 예를 들어" 표현식 "A+B"는 데이터 개체 "A" 및 "B"에 추가 연산자(+)를 적용하기 위해 구문 분석되어 다른 데이터 개체가 생성될 수 있습니다. 데이터 개체, 연산자 및 해당 연결의 총 집합은 트리의 노드에 있는 연산자와 분기의 데이터 개체와 함께 트리로 프로그램에 가장 자주 표시됩니다. 트리 형식으로 세분화된 식을 구문 분석된 트리라고도 합니다.

 식을 구문 분석하면 각 데이터 개체를 평가하기 위해 심볼 공급자(SP)가 호출됩니다. 예를 들어 둘 이상의 메서드에서 "A"가 모두 정의된 경우 "어느 A?" A의 값을 확인하기 전에 응답해야합니다. SP에서 반환하는 대답은 "다섯 번째 스택 프레임의 세 번째 항목" 또는 "이 메서드에 할당된 정적 메모리의 시작 을 넘어 50바이트인 A"와 같습니다.

 프로그램 자체에 대 한 MSIL을 생산 하는 것 외에도 CLR 컴파일러는 프로그램 DataBase *(.pdb)* 파일에 기록 된 매우 설명 적인 디버깅 정보를 생성할 수 있습니다. 독점 언어 컴파일러가 CLR 컴파일러와 동일한 형식으로 디버그 정보를 생성하는 한 CLR의 SP는 해당 언어의 명명된 데이터 개체를 식별할 수 있습니다. 명명된 데이터 개체가 식별되면 EE는 바인더 개체를 사용하여 데이터 개체를 해당 개체의 값을 보유하는 메모리 영역에 연결(또는 바인딩)합니다. 그런 다음 DE는 데이터 개체에 대한 새 값을 얻거나 설정할 수 있습니다.

 독점 컴파일러는 네임스페이스의 `ISymbolWriter` `System.Diagnostics.SymbolStore`.NET Framework에 정의된 인터페이스를 호출하여 CLR 디버깅 정보를 제공할 수 있습니다. MSIL에 컴파일하고 이러한 인터페이스를 통해 디버그 정보를 작성함으로써 독점 컴파일러는 CLR DE 및 SP를 사용할 수 있습니다. 이렇게 하면 독점 언어를 Visual Studio IDE에 통합하는 것이 크게 간소화됩니다.

 CLR DE가 고유의 EE를 호출하여 식을 평가하면 DE는 SP 및 바인더 개체에 대한 인터페이스를 사용하여 EE를 제공합니다. 따라서 CLR 기반 디버그 엔진을 작성하면 적절한 식 계산기 인터페이스를 구현하기만 하면 됩니다. CLR은 바인딩 및 기호 처리를 처리합니다.

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
