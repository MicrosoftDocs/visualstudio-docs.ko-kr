---
title: IPropertyProxyEESide | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714854"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
이 인터페이스는 연결 된 개체에 대 한 데이터를 볼 수 있는 메서드를 제공 합니다. 이 인터페이스는 형식 시각화 도우미에 대 한 지원의 일부입니다.

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 식 계산기는 형식 시각화 도우미를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getpropertyproxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 를 호출 하 여이 인터페이스를 가져옵니다. [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 하 여 [ipropertyproxyprovider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스에 의해 구현 되는 메서드는 다음과 같습니다.

|메서드|설명|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|개체의 데이터에 액세스할 수 있도록 데이터 소스 공급자를 초기화 합니다.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|개체의 어셈블리에 대 한 정보를 검색 합니다.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|개체에 대 한 초기 데이터를 가져옵니다.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|기존 데이터 저장소의 복사본을 만듭니다.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|기존 데이터 저장소에 대 한 참조를 만듭니다.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|이 개체를 포함 하는 어셈블리의 컨텍스트에서 특정 어셈블리에 대 한 정보를 검색 합니다.|

## <a name="remarks"></a>설명
 형식 시각화 도우미는이 인터페이스를 사용 하 여이 인터페이스가 포함 된 개체와 연결 된 값에 액세스 합니다. 데이터는 데이터에 대 한 읽기 전용 뷰를 제공 하는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 인터페이스를 통해 액세스 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
