---
title: IDebug표현문맥상 2::GetName | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 500d5c1788e837a27b4affada50ecc59db122e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729670"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
평가 컨텍스트의 이름을 검색합니다.

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
【아웃】 평가 컨텍스트의 이름을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이름은 이 평가 컨텍스트에 대한 설명입니다. 일반적으로 이 정확한 평가 컨텍스트를 참조하는 식 계산기에서 구문 분석할 수 있는 것입니다. 예를 들어 C++에서 이름은 다음과 같습니다.

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>참조
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
