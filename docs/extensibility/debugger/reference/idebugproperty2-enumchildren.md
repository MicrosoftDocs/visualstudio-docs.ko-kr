---
title: 아이디버그프로퍼티2:에넘어린이 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721516"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
속성의 자식 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
【인】 열거된 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체의 필드를 지정하는 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 열거형의 플래그 조합입니다.

`dwRadix`\
【인】 숫자 정보를 서식 지정하는 데 사용할 radix를 지정합니다.

`guidFilter`\
【인】 및 매개 변수와 함께 사용되는 필터의 `DEBUG_PROPERTY_INFO` GUID는 누거할 자식을 선택합니다. `pszNameFilter` `dwAttribFilter` 예를 들어 `guidFilterLocals` 로컬 변수에 대한 필터를 선택합니다.

`dwAttribFilter`\
【인】 [예를](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 들어 `DBG_ATTRIB_METHOD` 이 속성의 자식일 수 있는 모든 메서드에 대해 열거할 개체 유형을 지정하는 DBG_ATTRIB_FLAGS 열거형의 플래그 조합입니다. `guidFilter` 및 `pszNameFilter` 매개 변수와 함께 사용됩니다.

`pszNameFilter`\
【인】 및 매개 변수와 함께 사용되는 필터의 `DEBUG_PROPERTY_INFO` 이름으로 지정할 자식을 선택합니다. `dwAttribFilter` `guidFilter` 예를 들어 이 매개 변수를 "MyX" 필터로 설정하면 "MyX"라는 이름이 있는 모든 자식에 대해 필터가 지정됩니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 최대 시간(밀리초)을 지정합니다. 무기한 `INFINITE` 대기하는 데 사용합니다.

`ppEnum`\
【아웃】 하위 속성 목록을 포함하는 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
