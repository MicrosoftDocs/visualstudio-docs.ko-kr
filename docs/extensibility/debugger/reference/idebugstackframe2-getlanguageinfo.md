---
title: 아이디버그스택프레임2::겟랭정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cefb4bdd9d0c85311c63e6a988956301a6c2cc14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719708"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

이 스택 프레임과 연결된 언어를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>매개 변수

`pbstrLanguage`\
【아웃】 이 스택 프레임과 연결된 메서드를 구현하는 언어의 이름을 반환합니다.

`pguidLanguage`\
【아웃】 언어의 `GUID` 반환합니다. 예를 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 들어 언어의 경우 다음을 반환할 수 있습니다.

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Return Value

 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
