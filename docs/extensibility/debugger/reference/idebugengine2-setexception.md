---
description: 디버그 엔진 (DE)에서 지정 된 예외를 처리 하는 방법을 지정 합니다.
title: 'IDebugEngine2:: SetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3a327620ed9eddbba71f84c9950185f7987e8a79
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087914"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
디버그 엔진 (DE)에서 지정 된 예외를 처리 하는 방법을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>매개 변수
`pException`\
진행 예외를 설명 하 고 디버그 하는 방법을 설명 하는 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 구조입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 처음에는 예외를 생성 하는 프로그램을 중지 하는 것을 중지 하는 것을 막을 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
