---
title: 로컬의 가치 변경 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739141"
---
# <a name="change-the-value-of-a-local"></a>로컬 값 변경
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 계산기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 새 값이 **Locals** 창의 값 필드에 입력되면 디버그 패키지는 문자열을 입력된 대로 식 계산기(EE)에 전달합니다. EE는 단순 값 또는 식을 포함할 수 있는 이 문자열을 평가하고 결과 값을 연결된 로컬에 저장합니다.

 다음은 로컬 값을 변경하는 프로세스에 대한 개요입니다.

1. 사용자가 새 값을 입력한 후 Visual Studio는 로컬과 연결된 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체에서 [SetValueAsString을](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 호출합니다.

2. `IDebugProperty2::SetValueAsString`은 다음 작업을 수행합니다.

   1. 값을 생성 하는 문자열을 평가 합니다.

   2. 연결된 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 개체를 바인딩하여 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체를 가져옵니다.

   3. 값을 일련의 바이트로 변환합니다.

   4. [SetValue를](../../extensibility/debugger/reference/idebugobject-setvalue.md) 호출하여 디버깅 중인 프로그램이 메모리에 액세스할 수 있도록 값의 바이트를 메모리에 넣습니다.

3. 비주얼 스튜디오는 **지역 주민** 표시를 새로 고칩니다(자세한 내용은 [지역 주민 표시 참조).](../../extensibility/debugger/displaying-locals.md)

   이 프로시저는 **로컬** 자체와 연결된 `IDebugProperty2` 개체 대신 `IDebugProperty2` 사용되는 로컬 값과 연결된 개체를 제외하고 Watch 창에서 변수값을 변경하는 데도 사용됩니다.

## <a name="in-this-section"></a>섹션 내용
 [변화하는 값의 샘플 구현](../../extensibility/debugger/sample-implementation-of-changing-values.md) MyCEE 샘플을 사용하여 값을 변경하는 프로세스를 단계별로 진행합니다.

## <a name="see-also"></a>참조
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [지역 주민 표시](../../extensibility/debugger/displaying-locals.md)
