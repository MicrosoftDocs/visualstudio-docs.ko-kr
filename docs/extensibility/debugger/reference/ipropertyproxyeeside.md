---
title: 아이프로퍼프록시사이드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714854"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
이 인터페이스는 연결된 개체의 데이터를 보는 메서드를 제공합니다. 이 인터페이스는 형식 시각화 도우미에 대 한 지원의 일부입니다.

## <a name="syntax"></a>구문

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 계산기는 형식 시각화 도우미를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 얻으려면 [GetPropertyProxy를](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 호출합니다. [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에서 [쿼리 인터페이스를](/cpp/atl/queryinterface) 호출하여 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 메서드는 이 인터페이스에 의해 구현됩니다.

|방법|설명|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|개체의 데이터에 액세스할 수 있도록 데이터 원본 공급자를 초기화합니다.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|개체의 어셈블리에 대한 정보를 검색합니다.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|개체의 초기 데이터를 가져옵니다.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|기존 데이터 저장소의 복사본을 만듭니다.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|기존 데이터 저장소에 대한 참조를 만듭니다.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|이 개체를 포함하는 어셈블리의 컨텍스트에서 특정 어셈블리에 대한 정보를 검색합니다.|

## <a name="remarks"></a>설명
 형식 시각화 도우미는 이 인터페이스를 사용하여 이 인터페이스가 속한 개체와 연결된 값에 액세스합니다. 데이터는 데이터의 읽기 전용 보기를 제공하는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스를 통해 액세스됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
