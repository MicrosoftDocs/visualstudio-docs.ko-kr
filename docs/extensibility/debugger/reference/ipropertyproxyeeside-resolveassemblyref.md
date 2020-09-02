---
title: 'IPropertyProxyEESide:: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c54945b0c89fb9608fab6aa70dcc63a7c6ae42df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714882"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
지정 된 관리 되는 어셈블리 참조의 위치를 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>매개 변수
`assemName`\
진행 확인할 어셈블리의 이름입니다.

`assemBytes`\
제한이 참조와 연결 된 어셈블리 바이트를 포함 하는 [Ieedatastorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체를 반환 합니다.

`assemPdb`\
제한이 `IEEDataStorage` 이 참조와 연결 된 기호 저장소 데이터를 포함 하는 개체를 반환 합니다.

`assemLocation`\
제한이 이 참조의 경로 위치를 반환 합니다.

`alr`\
제한이 이 참조의 어셈블리 위치를 나타내는 [Assemblylocresolution](../../../extensibility/debugger/reference/assemblylocresolution.md) 열거형의 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 일반적으로 사용자 지정 식 계산기에 의해 구현 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
