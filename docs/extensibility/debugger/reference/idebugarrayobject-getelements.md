---
title: 'IDebugArrayObject:: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736244"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
배열의 모든 요소에 대 한 열거자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 모든 요소에 대해 열거를 허용 하는 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 대신 [Getcount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) 및 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) 메서드를 사용 하 여 요소를 반복 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
