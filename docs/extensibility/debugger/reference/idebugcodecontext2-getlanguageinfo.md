---
description: 이 코드 컨텍스트의 언어 정보를 가져옵니다.
title: 'IDebugCodeContext2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dccf0c34b6483ad85cc7bfd9cff7078cc20524f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164125"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
이 코드 컨텍스트의 언어 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>매개 변수
`pbstrLanguage`\
[in, out] "C + +"와 같은 언어의 이름을 포함 하는 문자열을 반환 합니다.

`pguidLanguage`\
[in, out] 코드 컨텍스트의 언어에 대 한 GUID를 반환 합니다 (예:) `guidCPPLang` .

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 하나 이상의 매개 변수는 null이 아닌 값을 반환 해야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
