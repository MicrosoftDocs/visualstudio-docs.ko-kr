---
description: 평가 컨텍스트의 이름을 검색 합니다.
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d43af7eeb733aca978a4c3b09fd4f97ca828fe5a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152651"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
평가 컨텍스트의 이름을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
제한이 평가 컨텍스트의 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이름은이 평가 컨텍스트에 대 한 설명입니다. 일반적으로이 정확한 평가 컨텍스트를 참조 하는 식 계산기에서 구문 분석할 수 있는 항목입니다. 예를 들어 c + +에서 이름은 다음과 같습니다.

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>참고 항목
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
