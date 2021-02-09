---
title: 'IDebugProcess2:: Get이상 Processid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetPhysicalProcessId
helpviewer_keywords:
- IDebugProcess2::GetPhysicalProcessId
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2513278c03c2ec2efed14028a78ab1b1b8ce2f63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890164"
---
# <a name="idebugprocess2getphysicalprocessid"></a>IDebugProcess2::GetPhysicalProcessId
시스템 프로세스 식별자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPhysicalProcessId(
   AD_PROCESS_ID* pdwProcessId
);
```

```csharp
int GetPhysicalProcessId(
   AD_PROCESS_ID[] pdwProcessId
);
```

## <a name="parameters"></a>매개 변수
`pdwProcessId`\
제한이 시스템 프로세스 식별자 정보를 사용 하 여 채워지는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
