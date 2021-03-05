---
description: 서버가 호출자에 대해 로컬 인지 여부를 확인 합니다.
title: 'IDebugCoreServer3:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 61cb67fd350fe74f12b69596675e009b01794ef4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163072"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
서버가 호출자에 대해 로컬 인지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Return Value
 `S_OK`서버가 로컬 인지 여부를 나타내는을 반환 합니다. `S_FALSE`서버가 msvsmon.exe의 인스턴스에서 실행 되는 경우 (일반적으로 원격 디버깅에 사용 됨)을 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
