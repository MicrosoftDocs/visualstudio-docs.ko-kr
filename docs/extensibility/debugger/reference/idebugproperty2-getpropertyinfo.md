---
title: 'IDebugProperty2:: GetPropertyInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ec1c3e29e0dbb6ca069dec696e6645a159ec7e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721372"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
속성을 설명 하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPropertyInfo ( 
   DEBUGPROP_INFO_FLAGS dwFields,
   DWORD                nRadix,
   DWORD                dwTimeout,
   IDebugReference2**   rgpArgs,
   DWORD                dwArgCount,
   DEBUG_PROPERTY_INFO* pPropertyInfo
);
```

```cpp
int GetPropertyInfo ( 
   enum_DEBUGPROP_INFO_FLAGS dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_PROPERTY_INFO[]     pPropertyInfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
진행 구조체에서 채울 필드를 지정 하는 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 열거형 값의 조합입니다 `pPropertyInfo` .

`nRadix`\
진행 숫자 정보의 서식을 지정 하는 데 사용할 기 수입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

`rgpArgs`\
[in, out] 나중에 사용 하도록 예약 되어 있습니다. 을 null 값으로 설정 합니다.

`dwArgCount`\
진행 나중에 사용 하도록 예약 되어 있습니다. 을 0으로 설정 합니다.

`pPropertyInfo`\
제한이 속성에 대 한 설명과 함께 채워지는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
