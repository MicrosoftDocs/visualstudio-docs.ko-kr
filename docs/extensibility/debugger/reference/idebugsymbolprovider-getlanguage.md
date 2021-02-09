---
title: 'Idebug Provider:: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 120434e44819d4c503336dffeaa1c255626270d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880231"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
이 메서드는 디버그 주소에서 코드를 컴파일하는 데 사용 된 언어를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스가 나타내는 주소 개체입니다.

`pguidLanguage`\
제한이 `GUID` 언어를 지정 하는을 반환 합니다.

`pguidLanguageVendor`\
제한이 `GUID` 언어 공급 업체를 지정 하는을 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진은이 메서드를 호출 하 여 올바른 식 계산기를 선택 하는 데 필요한 정보를 가져옵니다.

## <a name="see-also"></a>참고 항목
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
