---
description: 메타 데이터 가져오기 정보를 검색 합니다.
title: 'Idebug심볼 Providerdirect:: GetMetaDataImport | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52bc940485a99c545bc4450412a6aa4b3f8b104a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081297"
---
# <a name="idebugsymbolproviderdirectgetmetadataimport"></a>IDebugSymbolProviderDirect::GetMetaDataImport
메타 데이터 가져오기 정보를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMetaDataImport (
    GUID*      guid,
    DWORD      appID,
    IUnknown** ppImport
);
```

```csharp
int GetMetaDataImport (
    Guid       guid,
    uint       appID,
    out object ppImport
);
```

## <a name="parameters"></a>매개 변수
`guid`\
진행 모듈에 대 한 고유 식별자입니다.

`appID`\
진행 응용 프로그램 도메인의 식별자입니다.

`ppImport`\
제한이 메타 데이터 가져오기 정보를 포함 하는 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
