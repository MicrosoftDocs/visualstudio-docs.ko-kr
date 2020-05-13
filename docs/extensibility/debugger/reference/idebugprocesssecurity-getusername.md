---
title: IDebugProcess보안::GetuserName | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723249"
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
【아웃】 사용자 이름을 포함하는 문자열입니다.

## <a name="return-value"></a>Return Value
 메서드가 성공하면 `S_OK`가 반환되고, 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 `GetUserName`은 프로세스 에 **연결** 대화 상자의 **사용자 이름** 열에 표시되는 사용자 이름을 반환합니다. **프로세스에 연결** 대화 상자를 보려면 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] IDE(통합 개발 환경)의 **도구** 메뉴에서 **프로세스에 연결함을** 클릭합니다.

## <a name="see-also"></a>참조
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
