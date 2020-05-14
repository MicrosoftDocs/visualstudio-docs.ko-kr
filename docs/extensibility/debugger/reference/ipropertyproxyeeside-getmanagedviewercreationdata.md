---
title: IPropertyProxyEESide::GetManaged뷰어생성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714958"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
해당 뷰어를 인스턴스화하기 위해 이 속성 형식에 대한 뷰어에 대한 정보를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>매개 변수
`assemName`\
【아웃】 이 개체를 보유 하는 어셈블리의 이름을 반환 합니다.

`assemBytes`\
【아웃】 이 개체의 어셈블리 바이트를 포함하는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체를 반환합니다(사용할 수 있는 바이트가 없는 경우 null 값입니다).

`assemPdb`\
【아웃】 이 `IEEDataStorage` 개체에 대한 기호 저장소 정보를 포함하는 개체를 반환합니다(기호 저장소를 사용할 수 없는 경우 null 값입니다).

`className`\
【아웃】 이 개체를 포함하는 클래스 이름을 반환합니다.

`alr`\
【아웃】 [어셈블리LOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) 어셈블리의 위치를 나타내는 값을 반환합니다.

`replacementOk`\
【아웃】 이 개체의`TRUE`값을 변경할 수 있는 경우 0이 아닌 () 반환 합니다. 0`FALSE`( ) 개체가 읽기 전용인 경우

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 형식 시각화 도우미에서 관리되는 뷰어를 인스턴스화하는 데 사용됩니다.

## <a name="see-also"></a>참조
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
