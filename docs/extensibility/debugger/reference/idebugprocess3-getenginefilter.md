---
description: 사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 검색 합니다.
title: 'IDebugProcess3:: GetEngineFilter | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77ad90af772bb210402cfd43449350ccf0f02058
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158464"
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
사용 가능한 디버그 엔진에 대 한 고유 식별자 배열을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineFilter(
   GUID_ARRAY *pEngineArray
);
```

```csharp
public int GetEngineFilter(
   out GUID_ARRAY[] pEngineArray
);
```

## <a name="parameters"></a>매개 변수
`pEngineArray`\
제한이 디버그 엔진에 대 한 고유 식별자가 포함 된 구조체에 대 한 참조입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)
