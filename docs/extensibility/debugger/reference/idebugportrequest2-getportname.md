---
title: 'IDebugPortRequest2:: GetPortName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 574ea2ecb69c944bdb47ff80d7b4e26db51933da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887161"
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
제한이 포트의 이름을 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스는 일반적으로 포트에 대 한 연결을 얻기 위해 디버그 패키지 (클라이언트)에서 포트 공급자 (서버)로 전달 됩니다. 디버그 패키지와 포트 공급자는 모두 포트에 대해 선택할 수 있는 옵션을 인식 합니다. 간단한 문자열이 포트를 설명할 수 있는 경우 메서드에 충분 한 정보를 사용 하 여 연결을 설정할 수 있습니다 `IDebugPortRequest2::GetPortName` . 그렇지 않으면 클라이언트에서 추가 인터페이스를 제공할 수 있습니다 .이 인터페이스는를 사용 하 여 서버에서 가져올 수 있습니다 `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>참고 항목
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
