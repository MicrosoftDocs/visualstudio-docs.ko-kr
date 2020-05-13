---
title: IDebug 기호공급자직접::GetMethodFromAddress | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a062056f4a61521966417e9923a17f6d85b991a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718949"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
지정된 디버그 주소에서 메서드에 대한 정보를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
【인】 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시되는 디버그 주소입니다.

`pGuid`\
【아웃】 모듈의 고유 식별자입니다.

`pAppID`\
【아웃】 응용 프로그램 도메인의 식별자입니다.

`pTokenClass`\
【아웃】 포함된 클래스를 나타내는 토큰입니다.

`pTokenMethod`\
【아웃】 모듈을 나타내는 토큰입니다.

`pdwOffset`\
【아웃】 매개 변수의 시작부터 바이트로 `pAddress` 오프셋됩니다.

`pdwVersion`\
【아웃】 메서드의 버전 번호입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
