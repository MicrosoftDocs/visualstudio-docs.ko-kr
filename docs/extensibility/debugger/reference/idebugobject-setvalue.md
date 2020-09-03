---
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726363"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
연속 된 일련의 바이트에서 개체의 값을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>매개 변수
`pValue`\
진행 새 값을 나타내는 바이트 배열입니다.

`nSize`\
진행 값의 크기 (바이트)입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 배열의 값은이 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체로 복사 되어 기존 값을 대체 합니다. 새 값의 크기는 기존 값 보다 크거나 작을 수 있습니다. 이 `IDebugObject` 는 null 참조일 수 없습니다.

## <a name="see-also"></a>추가 정보
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
