---
title: 공통 언어 런타임 표현식 계산기 작성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712320"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>공통 언어 런타임 식 계산기 작성
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식 계산기(EE)는 디버깅되는 코드를 생성한 프로그래밍 언어의 구문 및 의미 체계를 처리하는 DE(디버그 엔진)의 일부입니다. 표현식은 프로그래밍 언어의 컨텍스트 내에서 평가되어야 합니다. 예를 들어 일부 언어에서 "A+B"라는 표현은 "A와 B의 합"을 의미합니다. 다른 언어에서 동일한 표현식은 "A 또는 B"를 의미할 수 있습니다. 따라서 Visual Studio IDE에서 디버깅할 개체 코드를 생성하는 각 프로그래밍 언어에 대해 별도의 EE를 작성해야 합니다.

 Visual Studio 디버그 패키지의 일부 측면은 프로그래밍 언어의 컨텍스트에서 코드를 해석해야 합니다. 예를 들어 중단점에서 실행이 중지되면 사용자가 **Watch** 창에 입력한 모든 식을 평가하고 표시해야 합니다. 사용자는 식을 **Watch** 창또는 **즉시** 창에 입력하여 로컬 변수의 값을 변경할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
 [공통 언어 런타임 및 표현식 평가](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) 독점 프로그래밍 언어를 Visual Studio IDE에 통합할 때 독점 언어의 컨텍스트 내에서 식을 평가할 수 있는 EE를 작성하면 디버그 엔진을 작성하지 않고도 Microsoft 중간 언어(MSIL)로 컴파일할 수 있습니다.

 [표현식 계산기 아키텍처](../../extensibility/debugger/expression-evaluator-architecture.md) 필요한 EE 인터페이스를 구현하고 공통 언어 런타임 기호 공급자(SP) 및 바인더 인터페이스를 호출하는 방법에 대해 설명합니다.

 [식 계산기 등록](../../extensibility/debugger/registering-an-expression-evaluator.md) EE는 공통 언어 런타임 및 Visual Studio 런타임 환경을 모두 갖춘 클래스 팩터리로 등록해야 합니다.

 [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md) 식을 평가하는 프로세스에 디버그 엔진(DE), 심볼 공급자(SP), 바인더 개체 및 식 계산기(EE)가 포함되는 방법을 설명합니다.

 [지역 주민 표시](../../extensibility/debugger/displaying-locals.md) 실행이 일시 중지될 때 디버그 패키지가 DE를 호출하여 로컬 변수 및 인수 목록을 얻는 방법을 설명합니다.

 [시계 창 표현식 평가](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Visual Studio 디버그 패키지가 DE를 호출하여 감시 목록에서 각 식의 현재 값을 결정하는 방법을 문서화합니다.

 [로컬 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md) 지역 값을 변경할 때 Locals 창의 각 줄에는 로컬의 이름, 형식 및 현재 값을 제공하는 연결된 개체가 있다고 설명합니다.

 [유형 시각화 도우미 및 사용자 지정 뷰어 구현](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) 형식 시각화 도우미 및 사용자 지정 뷰어를 지원하는 구성 요소에 의해 구현되어야 하는 인터페이스를 설명합니다.

## <a name="see-also"></a>참조
 [비주얼 스튜디오 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
