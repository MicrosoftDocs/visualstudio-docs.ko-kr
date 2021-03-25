---
description: 사용자 지정 특성이 이름으로 존재 하는지 여부를 확인 합니다.
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 646fe46f9d83a320423136b8601ee56b3f4ac583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077592"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
사용자 지정 특성이 이름으로 존재 하는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>매개 변수
`pszCustomAttributeName`\
진행 찾을 사용자 지정 특성의 이름을 포함 하는 문자열입니다.

## <a name="return-value"></a>반환 값
 이 필드에 사용자 지정 특성이 정의 되어 있으면 S_OK을 반환 하 고, 그렇지 않으면 S_FALSE을 반환 합니다.

## <a name="remarks"></a>설명
 사용자 지정 특성과 연결 된 특성 바이트를 가져오려면 [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
