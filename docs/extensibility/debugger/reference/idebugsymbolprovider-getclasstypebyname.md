---
description: 이 메서드는 정규화 된 클래스 이름을 나타내는 클래스 필드 형식을 가져옵니다.
title: 'Idebug Provider:: GetClassTypeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6439200ce0865fe7e6efd2424be0c5798e02dfa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081362"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
이 메서드는 정규화 된 클래스 이름을 나타내는 클래스 필드 형식을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>매개 변수
`pszClassName`\
진행 클래스 이름입니다.

`nameMatch`\
진행 일치 유형 (예: 대/소문자 구분)을 선택 합니다. [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 열거형의 값입니다.

`ppField`\
제한이 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 인터페이스로 표시 되는 클래스 형식을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
