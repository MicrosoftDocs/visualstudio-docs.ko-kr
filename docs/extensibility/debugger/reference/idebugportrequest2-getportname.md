---
title: 아이디버그포트요청2:겟포트네임 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724817"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
포트의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>매개 변수
`pbstrPortName`\
【아웃】 포트 의 이름을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스는 일반적으로 디버그 패키지(클라이언트)에서 포트 공급자(서버)로 전달되어 포트에 대한 연결을 얻습니다. 디버그 패키지와 포트 공급자 모두 포트에 대한 가능한 선택 사항을 알고 있습니다. 간단한 문자열이 포트를 설명할 수 `IDebugPortRequest2::GetPortName` 있는 경우 메서드에 연결하기에 충분한 정보가 있습니다. 그렇지 않으면 클라이언트에서 추가 인터페이스를 제공할 수 있으며, 이 `IDebugPortRequest2::QueryInterface`인터페이스는 서버에서 을 사용하여 가져올 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
