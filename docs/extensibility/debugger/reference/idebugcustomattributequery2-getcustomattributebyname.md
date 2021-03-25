---
description: 사용자 지정 특성의 이름이 지정 된 경우 사용자 지정 특성 바이트를 가져옵니다.
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dd8b1793bad585dd808ebd812b610cd68aabc129
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077605"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
사용자 지정 특성의 이름이 지정 된 경우 사용자 지정 특성 바이트를 가져옵니다.

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
진행 검색할 사용자 지정 특성의 이름을 포함 하는 문자열입니다.

`ppBlob`\
[in, out] 사용자 지정 특성 바이트로 채워진 배열입니다.

`pdwLen`\
[in, out] 배열에 반환할 최대 바이트 수를 지정 `ppBlob` 하 고 배열에 실제로 기록 되는 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK 반환 하거나 사용자 지정 특성이 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 `ppBlob`사용할 수 있는 특성 바이트 수를 반환 하려면 매개 변수를 null 값으로 설정 합니다. 그런 다음 배열을 할당 하 고이 배열을 `ppBlob` 매개 변수에 전달 합니다.

 특성 바이트는 사용자 지정 특성의 원시 데이터를 나타냅니다.

 `ppBlob`및 `pdwLen` 매개 변수가 null 값으로 설정 된 경우이 메서드를 사용 하 여 사용자 지정 특성이 있는지 여부를 확인할 수 있습니다. 그러나 보다 쉬운 대안은 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) 메서드를 호출 하는 것입니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
