---
title: 로컬의 값 변경 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 565ae9f27b9f5a113e51520724f525599ad5eda7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904272"
---
# <a name="change-the-value-of-a-local"></a>로컬의 값 변경
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 **지역** 창의 값 필드에 새 값을 입력 하면 디버그 패키지에서 식 계산기 (EE)에 형식화 된 문자열을 전달 합니다. EE는 단순 값 또는 식을 포함할 수 있는이 문자열을 평가 하 고 결과 값을 연결 된 로컬에 저장 합니다.

 다음은 로컬 값을 변경 하는 프로세스에 대 한 개요입니다.

1. 사용자가 새 값을 입력 하면 Visual Studio는 로컬에 연결 된 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체에서 [Setvalueasstring](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) 을 호출 합니다.

2. `IDebugProperty2::SetValueAsString`는 다음 작업을 수행합니다.

   1. 문자열을 계산 하 여 값을 생성 합니다.

   2. 연결 된 [Idebugfield](../../extensibility/debugger/reference/idebugfield.md) 개체를 바인딩하여 [idebugfield](../../extensibility/debugger/reference/idebugobject.md) 개체를 가져옵니다.

   3. 값을 일련의 바이트로 변환 합니다.

   4. 는 [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) 를 호출 하 여 값의 바이트를 메모리에 저장 하므로 디버깅 중인 프로그램에서 해당 값에 액세스할 수 있습니다.

3. Visual Studio는 **지역** 표시를 새로 고칩니다. 자세한 내용은 [지역](../../extensibility/debugger/displaying-locals.md) 표시를 참조 하세요.

   이 프로시저는 **Watch** `IDebugProperty2` `IDebugProperty2` 로컬 자체와 연결 된 개체 대신 사용 되는 로컬의 값과 연결 된 개체를 제외 하 고 조사식 창에서 변수 값을 변경 하는 데도 사용 됩니다.

## <a name="in-this-section"></a>섹션 내용
 [변경 값의 샘플 구현](../../extensibility/debugger/sample-implementation-of-changing-values.md) MyCEE 샘플을 사용 하 여 값을 변경 하는 과정을 단계별로 실행 합니다.

## <a name="see-also"></a>추가 정보
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [지역 표시](../../extensibility/debugger/displaying-locals.md)
