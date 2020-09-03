---
title: 'IDebugObject2:: IsUserData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726096"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
개체가 사용자 데이터를 나타내는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>매개 변수
`pfUser`\
제한이 `TRUE`는 개체가 사용자 데이터를 나타내는 경우 0이 아닌 값을 반환 하 고 그렇지 않으면 0 ()을 반환 `FALSE` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 사용자 데이터는 JustMyCode로 지정 된 모듈의 일부인 모든 개체입니다 (모듈을 사용자 코드로 표시 하 고 따라서 스택 추적에 표시 되는 사용자 구성 옵션).

## <a name="see-also"></a>추가 정보
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
