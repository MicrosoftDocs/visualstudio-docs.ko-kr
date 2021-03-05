---
description: 특정 인터페이스가 클래스에 정의 되어 있는지 여부를 확인 합니다.
title: IDebugClassField::D Oes인터페이스 존재 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173470"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
특정 인터페이스가 클래스에 정의 되어 있는지 여부를 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>매개 변수
`pszInterfaceName`\
진행 찾을 인터페이스 이름을 포함 하는 문자열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 하 고 인터페이스가 없으면 S_FALSE를 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 적용 되는이 메서드는 모든 인터페이스의 열거형을 가져오고 목록에서 일치 하는 인터페이스를 검색 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
