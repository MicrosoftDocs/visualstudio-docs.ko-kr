---
title: IDebugAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2ceb87277460f65e52c35f02e7fbbd01da1101a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736521"
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 변수의 숫자 별칭을 나타냅니다. 별칭은 단순히 변수에 대 한 다른 이름입니다.

## <a name="syntax"></a>Syntax

```
IDebugAlias : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기 (EE)는이 인터페이스를 구현 하 여 변수에 대 한 숫자 별칭을 지원 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
- [Createalias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) 는 특정 개체에 대 한 별칭을 만듭니다. 별칭을 검색 하려면 [Findalias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) 또는 [getallaliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)를 사용 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 메서드는 인터페이스에 정의 되어 `IDebugAlias` 있습니다.

|메서드|설명|
|------------|-----------------|
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|이 별칭이 참조 하는 개체를 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|별칭 이름을 가져옵니다.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|`ICorDebugValue`이 개체에 대 한 관리 코드 정보에 대 한 액세스를 제공 하는 인터페이스를 검색 합니다 (관리 코드에만 해당).|
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|이 별칭을 더 이상 사용 하지 않는 것으로 표시 합니다.|

## <a name="remarks"></a>설명
 별칭은 문자열 형식의 10 진수이 고 뒤에 # 문자가 옵니다 (예: 1001 #).

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)
- [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)
- [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
