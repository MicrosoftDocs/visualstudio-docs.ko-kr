---
title: IDebugClassField::에이넘인터페이스구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734491"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
이 클래스에서 구현한 인터페이스에 대한 열거형기를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
【아웃】 구현된 인터페이스 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 인터페이스가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 이 클래스에 구현된 인터페이스가 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 열거형의 각 요소는 인터페이스를 설명하는 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체입니다. 관리되지 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 않는 코드는 인터페이스를 불연속 엔터티로 사용하지 않으므로 이 메서드는 항상 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 관리되지 않는 코드에 대한 null 값을 반환합니다.

## <a name="see-also"></a>참조
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
