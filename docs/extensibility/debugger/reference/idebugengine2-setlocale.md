---
description: 디버그 엔진 (DE)의 로캘을 설정 합니다.
title: 'IDebugEngine2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54cfd2d9d51cbad414cfb481b88f1e3277500efa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153913"
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
디버그 엔진 (DE)의 로캘을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale( 
   ushort wLangID
);
```

## <a name="parameters"></a>매개 변수
`wLangID`\
진행 언어 로캘을 지정 합니다. 예를 들어 영어의 경우 1033입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 해제에서 반환 된 문자열이 제대로 지역화 되도록 IDE의 로캘 설정을 전파 하기 위해 세션 디버그 관리자 (SDM)에 의해 호출 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
