---
title: 'IDebugExpressionEvaluator:: SetRegistryRoot | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729418"
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
이 메서드는 레지스트리 루트를 설정 합니다. 병렬 디버깅에 사용 됩니다.

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
진행 새 레지스트리 루트입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 지정 된 레지스트리 루트는 일반적으로 식 계산기가 처음 인스턴스화될 때 설정 되 고 특정 버전의 Visual Studio에 대 한 레지스트리 키를 가리킵니다 HKEY_LOCAL_MACHINE ( \\ 예 \Software\microsoft\visualstudio*x. y*는 버전 번호). *X.Y*

## <a name="see-also"></a>추가 정보
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
