---
description: 이 스택 프레임과 연결 된 언어를 가져옵니다.
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78d518975ce343407c7acc733bbd094c3f00ab2a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053427"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

이 스택 프레임과 연결 된 언어를 가져옵니다.

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
제한이 이 스택 프레임과 연결 된 메서드를 구현 하는 언어의 이름을 반환 합니다.

`pguidLanguage`\
제한이 언어의를 반환 합니다 `GUID` . 예를 들어 언어의 경우 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 다음이 반환 될 수 있습니다.

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>반환 값

 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
