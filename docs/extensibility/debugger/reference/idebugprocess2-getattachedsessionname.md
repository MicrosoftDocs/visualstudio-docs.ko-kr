---
description: 이 프로세스를 디버깅 하는 세션의 이름을 가져옵니다.
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d83a9d5f89ea06744454b790d988f1881c193b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142546"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
이 프로세스를 디버깅 하는 세션의 이름을 가져옵니다. IDE는 특정 컴퓨터에서 특정 프로세스를 디버깅 하는 사용자에 게이 정보를 표시할 수 있습니다.

> [!NOTE]
> 이 메서드는 더 이상 사용 되지 않으며 구현에서 항상를 반환 해야 `E_NOTIMPL` 합니다.

## <a name="syntax"></a>구문

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>매개 변수
`pbstrSessionName`\

## <a name="return-value"></a>반환 값
 이 메서드는 항상를 반환 해야 합니다 `E_NOTIMPL` .

## <a name="see-also"></a>참고 항목
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
