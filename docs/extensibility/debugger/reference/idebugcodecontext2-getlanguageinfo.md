---
title: 아이디버그코드컨텍스트2::겟랭정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 465cc07b3ca75835afe0737fb22ba403acc4098b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734235"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
이 코드 컨텍스트에 대한 언어 정보를 가져옵니다.

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
【인, 아웃】 "C++"와 같은 언어 이름이 포함된 문자열을 반환합니다.

`pguidLanguage`\
【인, 아웃】 코드 컨텍스트의 언어에 대한 GUID를 반환합니다(예: `guidCPPLang`.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 매개 변수 중 하나 이상이 null이 아닌 값을 반환해야 합니다.

## <a name="see-also"></a>참조
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
