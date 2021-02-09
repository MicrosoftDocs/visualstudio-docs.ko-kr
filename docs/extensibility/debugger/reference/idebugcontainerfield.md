---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e7ed9e573236f0bdeff9c9a8433af322a5a5f79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928499"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
이 인터페이스는 다른 기호 또는 형식에 대 한 컨테이너인 기호 또는 형식을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는 컨테이너를 나타내는 모든 인터페이스에 대 한 기본 클래스 이기도 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 많은 인터페이스에서 많은 메서드는이 인터페이스를 반환 합니다. 이 클래스는 모든 컨테이너의 기본 클래스 이므로 [QueryInterface](/cpp/atl/queryinterface)를 사용 하 여이 인터페이스에서 더 특수화 된 인터페이스를 가져올 수 있습니다. 이러한 인터페이스에는 [Idebugarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md), [idebugarrayfield](../../../extensibility/debugger/reference/idebugclassfield.md), [Idebugarrayfield](../../../extensibility/debugger/reference/idebugmethodfield.md)및 [idebugarrayfield](../../../extensibility/debugger/reference/idebugpropertyfield.md)가 포함 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|컨테이너의 필드에 대 한 열거자를 만듭니다.|

## <a name="remarks"></a>설명
 배열 (변수에 대 한 컨테이너), 클래스 (메서드 및 변수의 컨테이너) 및 메서드 (매개 변수 및 지역 변수의 컨테이너)는 모두 컨테이너의 예입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
