---
title: IDebug표현평가자::세트레지스트리루트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11e7cd69ed3f1e1b23cc0f2f03f3fd2cf912d308
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729418"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
이 메서드는 레지스트리 루트를 설정합니다. 나란히 디버깅하는 데 사용됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetRegistryRoot ( 
   LPCOLESTR ustrRegistryRoot
);
```

```csharp
int SetRegistryRoot(
   string ustrRegistryRoot
);
```

## <a name="parameters"></a>매개 변수
`ustrRegistryRoot`\
【인】 새 레지스트리 루트입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 지정된 레지스트리 루트는 일반적으로 식 계산기를 처음 인스턴스화하고 특정 버전의 Visual Studio에 대한 레지스트리 키를 가리키는 경우 설정됩니다(HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y,* *X.Y는* 버전 번호).

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
