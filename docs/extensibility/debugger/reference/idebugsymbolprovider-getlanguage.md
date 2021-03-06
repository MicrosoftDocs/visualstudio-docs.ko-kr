---
description: 이 메서드는 디버그 주소에서 코드를 컴파일하는 데 사용 된 언어를 가져옵니다.
title: 'Idebug Provider:: GetLanguage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e7bcf2bd16212767fc8eff6106cdb3602bc293c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086991"
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

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 디버그 엔진은이 메서드를 호출 하 여 올바른 식 계산기를 선택 하는 데 필요한 정보를 가져옵니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
