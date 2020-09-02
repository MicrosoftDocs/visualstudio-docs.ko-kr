---
title: 'IPropertyProxyEESide:: GetManagedViewerCreationData | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714958"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
해당 뷰어를 인스턴스화하기 위해이 속성 형식의 뷰어에 대 한 정보를 검색 합니다.

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
제한이 이 개체를 보유 하는 어셈블리의 이름을 반환 합니다.

`assemBytes`\
제한이 이 개체의 어셈블리 바이트를 포함 하는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체를 반환 합니다. 바이트를 사용할 수 없는 경우 null 값입니다.

`assemPdb`\
제한이 `IEEDataStorage` 이 개체에 대 한 기호 저장소 정보를 포함 하는 개체를 반환 합니다. 기호 저장소를 사용할 수 없는 경우에는 null 값입니다.

`className`\
제한이 이 개체를 포함 하는 클래스 이름을 반환 합니다.

`alr`\
제한이 어셈블리의 위치를 나타내는 [Assemblylocresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) 열거형의 값을 반환 합니다.

`replacementOk`\
제한이 는 `TRUE` 이 개체의 값을 변경할 수 있는 경우 0이 아닌 값을 반환 하 고, `FALSE` 개체가 읽기 전용인 경우에는 0 ()을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 형식 시각화 도우미에서 관리 되는 뷰어를 인스턴스화하기 위해 사용 됩니다.

## <a name="see-also"></a>추가 정보
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
