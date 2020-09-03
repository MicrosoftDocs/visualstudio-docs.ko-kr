---
title: IEEDataStorage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718181"
---
# <a name="ieedatastorage"></a>IEEDataStorage
이 인터페이스는 바이트 배열을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기 (EE)는이 인터페이스를 구현 하 여 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 통해 데이터를 검색 하 고 변경 하기 위해 형식 시각화 도우미에서 사용 되는 바이트 배열을 나타냅니다. EE는 일반적으로이 인터페이스를 구현 하 여 외부 형식 시각화 도우미를 지원 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스의 메서드는 `IPropertyProxyEESide` 모두이 인터페이스를 반환 합니다. [Getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 를 호출 하 여 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스를 가져옵니다. [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하 여 [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IEEDataStorage`인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|제공 된 버퍼에 지정 된 수의 데이터 바이트를 검색 합니다.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|사용 가능한 데이터 바이트 수를 검색 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 형식 시각화 도우미에서 특정 개체에 의해 저장 된 데이터에 액세스 하는 데 사용 됩니다. 데이터는 바이트 배열로 처리 되므로 형식 시각화 도우미가 사용자에 게 제공 하는 데 필요한 방식으로 해당 데이터를 조작할 수 있습니다.

 사용자 지정 뷰어는 원하는 경우에도이 인터페이스를 사용할 수 있습니다. 일반적으로 사용자 지정 뷰어는 사용자 지정 인터페이스인 [Getmemorybytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 또는 [getmemorybytes](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (문자열 기반 데이터의 경우)를 사용 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
