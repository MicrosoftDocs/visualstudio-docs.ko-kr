---
description: 이 인터페이스는 IDebugObject 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다.
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eece06d64a4eeefefe4e132295f20e40a032434b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224631"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 이 인터페이스는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다.

## <a name="syntax"></a>구문

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는이 인터페이스를 구현 하 여 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 인터페이스를 구현 하는 개체 집합을 제공 합니다. 이는 [Getcount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 메서드가 있으므로 표준 COM 열거형이 아닙니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
- [Getelements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|열거형에서 다음 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체 집합을 검색 합니다.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|지정 된 수의 항목을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|열거형을 첫 번째 항목으로 다시 설정 합니다.|
|[원본과](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|현재 열거형의 복사본을 검색 합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|열거형의 항목 수를 검색 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스를 사용 하면 디버그 엔진이 배열의 개체 집합을 열거할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
