---
title: 'Idebug심볼 Providerdirect:: GetMetaDataImport | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetMetaDataImport
- IDebugSymbolProviderDirect::GetMetaDataImport
ms.assetid: b51a492c-af00-4b08-93fb-6c19ee4916aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 475ffab931445718d27ae6e1fe1242f6a5a76512
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718971"
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

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
