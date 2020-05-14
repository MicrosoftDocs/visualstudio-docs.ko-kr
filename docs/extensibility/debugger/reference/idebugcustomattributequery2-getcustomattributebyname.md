---
title: IDebug사용자 정의 속성 쿼리2:GetCustom속성 이름 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732568"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
사용자 지정 특성의 이름이 지정된 사용자 지정 특성 바이트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>매개 변수
`pszCustomAttributeName`\
【인】 찾을 사용자 지정 특성의 이름을 포함하는 문자열입니다.

`ppBlob`\
【인, 아웃】 사용자 지정 특성 바이트로 채워진 배열입니다.

`pdwLen`\
【인, 아웃】 `ppBlob` 배열에서 반환할 최대 바이트 수를 지정하고 실제로 배열에 기록된 바이트 수를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 사용자 지정 특성이 없는 경우 S_OK 반환하거나 S_FALSE 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 `ppBlob` 사용 가능한 특성 바이트 수를 반환하려면 매개 변수를 null 값으로 설정합니다. 그런 다음 배열을 할당하고 매개 `ppBlob` 변수에 대해 해당 배열을 전달합니다.

 특성 바이트는 사용자 지정 특성의 원시 데이터를 나타냅니다.

 `ppBlob` 및 `pdwLen` 매개 변수가 null 값으로 설정된 경우 이 메서드를 사용하여 사용자 지정 특성이 존재하는지 확인할 수 있습니다. 그러나 더 쉬운 대안은 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) 메서드를 호출하는 것입니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
