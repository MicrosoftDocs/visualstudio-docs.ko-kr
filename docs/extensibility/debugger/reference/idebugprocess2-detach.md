---
title: IDebugProcess2::D etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9036ebc44835ab6c3ebd08b9fad4408d9cb97461
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724131"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
프로세스의 모든 프로그램을 분리 하 여이 프로세스에서 디버거를 분리 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 모든 프로그램 및 프로세스는 계속 실행 되지만 더 이상 디버그 세션의 일부가 아닙니다. 분리 작업이 완료 된 후에는이 프로세스 및 해당 프로그램에 대 한 더 이상 디버그 이벤트가 전송 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
