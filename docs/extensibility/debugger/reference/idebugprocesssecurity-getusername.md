---
description: 포트 공급자에서 사용자 이름을 가져옵니다.
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a13075b233d5b0fe70b314a4b2d025a2a4c7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076305"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
포트 공급자에서 사용자 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>매개 변수
`pbstrUserName`\
제한이 사용자 이름을 포함 하는 문자열입니다.

## <a name="return-value"></a>반환 값
 메서드가 성공하면 `S_OK`가 반환되고, 그렇지 않은 경우 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 `GetUserName`**프로세스에 연결** 대화 상자의 **사용자 이름** 열에 표시 되는 사용자 이름을 반환 합니다. **프로세스에 연결** 대화 상자를 보려면 IDE (통합 개발 환경)의 **도구** 메뉴에서 **프로세스에 연결** 을 클릭 합니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>참조
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
