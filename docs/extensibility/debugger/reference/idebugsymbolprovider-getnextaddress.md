---
description: 메서드에서 지정 된 디버그 주소 다음에 오는 디버그 주소를 가져옵니다.
title: 'Idebug Provider:: GetNextAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d177d03daef4f8d3344941658b85f71551af126b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168415"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
메서드에서 지정 된 디버그 주소 다음에 오는 디버그 주소를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 지정 된 디버그 주소입니다.

`fStatementOnly`\
진행 TRUE 이면 디버그 주소를 단일 문으로 제한 합니다.

`ppAddress`\
제한이 다음 디버그 주소를 반환 합니다.

## <a name="return-value"></a>반환 값
 `HRESULT`일반적으로 S_OK 유효한를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
