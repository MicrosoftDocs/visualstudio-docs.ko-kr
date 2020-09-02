---
title: 'IDebugBinder3:: GetTypeArguments | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f7b6038013370ad85a665d9899d367e621aa991
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192278"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]
이 메서드는이 개체와 연결 된 인수 형식의 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

#### <a name="parameters"></a>매개 변수

 `skip`

 진행 인수 형식을 가져오기 전에 건너뛸 필드 수입니다.

 `count`

 진행 반환할 인수 필드의 수입니다 (도 배열의 크기를 지정 `ppFields` ).

 `ppFields`

 [in, out] 이 메서드가 반환 될 때 채워질 필드의 배열입니다.

 `pFetched`

 제한이 실제로 반환 된 인수 형식 필드의 수입니다 (선택 사항).

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 인수 형식의 수는 [Gettypeargumentcount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)를 사용 하 여 미리 가져올 수 있습니다.

## <a name="see-also"></a>관련 항목

- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)