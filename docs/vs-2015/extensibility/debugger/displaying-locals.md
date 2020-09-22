---
title: 지역 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841566"
---
# <a name="displaying-locals"></a>로컬 항목 표시
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 실행은 항상 메서드 컨텍스트 내에서 수행 됩니다 .이 메서드는 포함 하는 메서드나 현재 메서드가 라고도 합니다. 실행이 일시 중지 되 면 Visual Studio는 디버그 엔진 (DE)을 호출 하 여 메서드의 지역 이라는 지역 변수 및 인수 목록을 가져옵니다. Visual Studio는 **지역** 창에 이러한 지역 및 해당 값을 표시 합니다.  
  
 로컬을 표시 하기 위해 DE는 EE에 속하는 [Getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 메서드를 호출 하 고이를 평가 컨텍스트, 즉 SP (기호 공급자), 현재 실행 주소 및 바인더 개체를 제공 합니다. 자세한 내용은 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)를 참조 하세요. 호출에 성공 하면이 `IDebugExpressionEvaluator::GetMethodProperty` 메서드는 현재 실행 주소를 포함 하는 메서드를 나타내는 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환 합니다.  
  
 DE는 [Enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 을 호출 하 여 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 가져옵니다 .이 개체는 지역만 반환 하 고 열거 하 여 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 구조체 목록을 생성 하도록 필터링 됩니다. 각 구조체에는 로컬의 이름, 형식 및 값이 포함 됩니다. 형식 및 값은 표시 하기에 적합 한 형식이 지정 된 문자열로 저장 됩니다. 일반적으로 이름, 형식 및 값은 **지역** 창의 한 줄에 함께 표시 됩니다.  
  
> [!NOTE]
> **간략** 한 조사식 창과 **조사식** 창에는 이름, 값 및 형식 같은 형식의 변수도 표시 됩니다. 그러나 이러한 값은 대신 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 를 호출 하 여 가져옵니다 `IDebugProperty2::EnumChildren` .  
  
## <a name="in-this-section"></a>섹션 내용  
 [로컬 항목의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)  
 예제를 사용 하 여 지역 구현 과정을 단계별로 실행 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)  
 디버그 엔진 (DE)이 식 계산기 (EE)를 호출할 때 세 개의 인수를 전달 하는 방법을 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
