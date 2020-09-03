---
title: 'IDebugThread2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718764"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
스레드의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
제한이 스레드의 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 검색 된 이름은 항상 표시할 수 있는 이름이 며이 이름은 스레드를 설명 합니다. 스레드 이름은 명명 된 스레드를 지 원하는 런타임 아키텍처에서 파생 될 수도 있고, 디버그 엔진에서 파생 된 이름일 수도 있습니다. 또는 [Setthreadname](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) 메서드를 호출 하 여 스레드 이름을 설정할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
