---
description: 이 필드에 대 한 사용자 지정 특성이 있는지 여부를 확인 하 고, 있는 경우 특성 정보를 반환 합니다.
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00f7e23b280ef92e9883f68f203bd790f5e4d815
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077566"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
이 필드에 대 한 사용자 지정 특성이 있는지 여부를 확인 하 고, 있는 경우 특성 정보를 반환 합니다.

## <a name="syntax"></a>구문

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 사용자 지정 특성을 지원 하기 위해 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 **Idebugcustomattributequery** 인터페이스의 메서드를 보여 줍니다.

|메서드|Description|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|사용자 지정 특성이 이름으로 존재 하는지 여부를 확인 합니다.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|지정 된 사용자 지정 특성에 대 한 특성 정보를 가져옵니다.|

 **Idebugcustomattributequery** 메서드 외에도 `IDebugCustomAttributeQuery2` 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|이 필드에 연결 된 모든 사용자 지정 특성에 대 한 열거자를 가져옵니다.|

## <a name="remarks"></a>설명
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 메서드는이 필드에 대해 정의 된 모든 사용자 지정 특성에 대 한 열거자를 반환할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
