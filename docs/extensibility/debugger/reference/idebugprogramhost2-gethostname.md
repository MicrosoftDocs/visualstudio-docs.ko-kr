---
title: 아이디버그프로그램호스트2:GetHostName | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f1bd63d6b53359cf3b86f5e3849cb18bd8367f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722222"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
이 프로그램의 호스팅 프로세스의 제목, 친숙한 이름 또는 파일 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetHostName( 
   DWORD dwType,
   BSTR* pbstrHostName
);
```

```csharp
int GetHostName( 
   uint dwType,
   out string pbstrHostName
);
```

## <a name="parameters"></a>매개 변수
`dwType`\
【인】 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 열거형의 값입니다.

`pbstrHostName`\
【아웃】 호스팅 프로세스의 요청된 이름을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드의 일반적인 구현에서 `dwType` 매개 변수는 무시 되 고 호스트 컴퓨터의 친숙 한 이름이 반환 됩니다. 또 다른 가능한 구현은 `dwType` 이름을 얻기 위해 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) 메서드에 대 한 호출에 매개 변수를 전달 하는 것입니다.

## <a name="see-also"></a>참조
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
