---
title: IEE데이터스토리지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718181"
---
# <a name="ieedatastorage"></a>IEEDataStorage
이 인터페이스는 바이트 배열을 나타냅니다.

## <a name="syntax"></a>구문

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기(EE)는 이 인터페이스를 구현하여 바이트 배열을 나타냅니다(형식 시각화 도우미가 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 통해 데이터를 검색하고 변경하는 데 사용). EE는 일반적으로 외부 형식 시각화 도우미를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 인터페이스의 메서드는 `IPropertyProxyEESide` 모두 이 인터페이스를 반환합니다. [IPropertyProxyESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 얻으려면 [GetPropertyProxy를](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 호출합니다. [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에서 [쿼리 인터페이스를](/cpp/atl/queryinterface) 호출하여 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 인터페이스는 `IEEDataStorage` 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|제공된 버퍼에 지정된 데이터 바이트 수를 검색합니다.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|사용 가능한 데이터 바이트 수를 검색합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 형식 시각화 도우미에서 특정 개체가 보유한 데이터에 액세스하는 데 사용됩니다. 데이터는 바이트 배열로 처리되므로 형식 시각화 도우미가 사용자에게 표시하는 데 필요한 방식으로 데이터를 조작할 수 있습니다.

 사용자 지정 뷰어는 원하는 경우 이 인터페이스를 사용할 수도 있지만 일반적으로 사용자 지정 뷰어는 사용자 지정 인터페이스인 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 또는 [GetStringChars(문자열](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) 지향 데이터)를 사용합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
