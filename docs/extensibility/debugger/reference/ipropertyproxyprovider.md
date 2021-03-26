---
description: 이 인터페이스는 개체의 데이터를 보고 변경 하는 프록시 인터페이스를 제공 합니다.
title: IPropertyProxyProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 87bc0bfa11c54f8eade595f6bf0bfaba1fa277ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058094"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
이 인터페이스는 개체의 데이터를 보고 변경 하는 프록시 인터페이스를 제공 합니다.

## <a name="syntax"></a>구문

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기 (EE)는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 구현 하는 것과 동일한 개체에서이 인터페이스를 구현 합니다 .이 인터페이스는 ee의 형식 시각화 도우미 지원의 일부로 구현 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProperty3` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IPropertyProxyProvider`인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|개체에 대 한 데이터를 볼 수 있는 속성 프록시 인터페이스를 검색 합니다.|

## <a name="remarks"></a>설명
 EE는이 인터페이스를 구현 하지만 [getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 구현은 일반적으로 [getpropertyproxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)에 의해 처리 됩니다. IEEVisualizerService 인터페이스를 얻는 방법에 대 한 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)
