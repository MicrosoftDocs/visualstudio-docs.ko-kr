---
title: 아이프로퍼프로퍼런스프로퍼런스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714788"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
이 인터페이스는 개체의 데이터를 보고 변경할 수 있는 프록시 인터페이스를 제공합니다.

## <a name="syntax"></a>구문

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 식 평가기(EE)는 EE의 형식 시각화 도우미 지원의 일부로 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 구현하는 동일한 개체에서 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugProperty3` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 인터페이스는 `IPropertyProxyProvider` 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|속성 프록시 인터페이스를 검색하여 개체의 데이터를 봅니다.|

## <a name="remarks"></a>설명
 EE는 이 인터페이스를 구현하지만 [GetPropertyProxy의](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 구현은 일반적으로 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)에 의해 처리됩니다. IEEVisualizerService 인터페이스 를 가져오는 방법에 대한 자세한 내용은 [데이터 시각화 및 보기를](../../../extensibility/debugger/visualizing-and-viewing-data.md) 참조하십시오.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)
