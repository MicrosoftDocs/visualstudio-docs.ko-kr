---
title: 'IDebugDynamicFieldCOMPlus:: GetTypeFromTypeDef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypeFromTypeDef
- IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
ms.assetid: 7f6cd3d3-f4da-4893-be91-8dd104be8010
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1af25920f956ca3c5b486003806bd66430fc8b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919943"
---
# <a name="idebugdynamicfieldcomplusgettypefromtypedef"></a>IDebugDynamicFieldCOMPlus::GetTypeFromTypeDef
해당 토큰이 지정 된 형식을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetTypeFromTypeDef(
   ULONG32       ulAppDomainID,
   GUID          guidModule,
   _mdToken      tokClass,
   IDebugField** ppType
);
```

```csharp
int GetTypeFromTypeDef(
   uint            ulAppDomainID,
   Guid            guidModule,
   int             tokClass,
   out IDebugField ppType
);
```

## <a name="parameters"></a>매개 변수
`ulAppDomainID`\
진행 응용 프로그램 도메인의 식별자입니다.

`guidModule`\
진행 모듈의 고유 식별자입니다.

`tokClass`\
진행 형식을 나타내는 토큰입니다.

`ppType`\
제한이 형식을 포함 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)
