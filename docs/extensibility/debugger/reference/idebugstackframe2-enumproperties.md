---
title: 'IDebugStackFrame2:: EnumProperties | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719904"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
로컬 변수와 같은 스택 프레임과 연결 된 속성에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumProperties ( 
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,
   UINT                      nRadix,
   REFIID                    refiid,
   DWORD                     dwTimeout,
   ULONG*                    pcelt,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumProperties ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,
   uint                        nRadix,
   ref Guid                    refiid,
   uint                        dwTimeout,
   out uint                    pcelt,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`dwFieldSpec`\
진행 열거 된 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체에서 채울 필드를 지정 하는 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 열거형의 플래그 조합입니다.

`nRadix`\
진행 숫자 정보의 서식을 지정 하는 데 사용할 기 수입니다.

`refiid`\
진행 열거 될 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조를 선택 하는 데 사용 되는 필터의 GUID입니다 (예:) `guidFilterLocals` .

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기 하는 최대 시간 (밀리초)입니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

`pcelt`\
제한이 열거 된 속성의 수를 반환 합니다. 이는 [Getcount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) 메서드를 호출 하는 것과 같습니다.

`ppEnum`\
제한이 원하는 속성의 목록을 포함 하는 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 단일 호출로 선택한 모든 속성을 검색할 수 있도록 허용 하므로 [Getdebugproperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) 및 [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 메서드를 순차적으로 호출 하는 것 보다 빠릅니다.

## <a name="see-also"></a>추가 정보
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
