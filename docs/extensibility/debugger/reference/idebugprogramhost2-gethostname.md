---
description: 이 프로그램의 호스팅 프로세스에 대 한 제목, 이름 또는 파일 이름을 가져옵니다.
title: 'IDebugProgramHost2:: GetHostName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4574bee7fb5a7f3ed125a73361de6fc9c3bcbfc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149524"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
이 프로그램의 호스팅 프로세스에 대 한 제목, 이름 또는 파일 이름을 가져옵니다.

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
진행 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 열거형의 값입니다.

`pbstrHostName`\
제한이 호스팅 프로세스의 요청 된 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드의 일반적인 구현에서는 `dwType` 매개 변수가 무시 되 고 호스트 컴퓨터의 이름이 반환 됩니다. 또 다른 가능한 구현은 `dwType` [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) 메서드 호출에 매개 변수를 전달 하 여 이름을 가져오는 것입니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
