---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5cfd425e6b992d8d933edd45f27d6fb4c8161a1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891048"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
이 메서드는이 프로세스 및이 프로세스에 포함 된 모든 프로그램에서 편집 하며 계속 하기를 명시적으로 해제 합니다. 사용자 지정 포트 공급자는 항상를 반환 해야 합니다 `E_NOTIMPL` .

## <a name="syntax"></a>구문

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>매개 변수
`reason`\
진행 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 열거형의 값입니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

> [!NOTE]
> 사용자 지정 포트 공급자는 항상를 반환 해야 합니다 `E_NOTIMPL` .

## <a name="remarks"></a>설명
 프로세스에 대해 편집 하며 계속 하기를 사용 하지 않도록 설정 하는 경우 프로세스를 다시 시작 하 여 다시 활성화할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
