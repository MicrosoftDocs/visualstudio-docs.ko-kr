---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725599"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
이 인터페이스는 포인터 형식을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는이 인터페이스를 구현 하 여 포인터를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 가를 반환 하는 경우에는 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서이 인터페이스를 가져옵니다 `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 및 인터페이스의 메서드 외에도 `IDebugField` `IDebugContainerField` 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|포인터의 대상을 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.|

## <a name="remarks"></a>설명
 C/c + +에서 포인터는 배열 표기법에 사용 되는 경우 컨테이너가 될 수 있습니다. 예를 들어, 지정 된에 `char *pString` `pString` 는에 대 한 포인터 형식이 `char` 있습니다. `pString[3]` 에는 `char` 해당 컨테이너의 네 번째 요소를 참조 하는에 대 한 포인터인 컨테이너의 형식이 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
