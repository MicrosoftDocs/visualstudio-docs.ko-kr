---
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727172"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
`this` `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 메서드를 포함 하는 개체의 (in) 포인터를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>매개 변수
`ppClass`\
제한이 "This" 포인터를 나타내는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 개체 지향 언어에서 일반적으로 클래스의 현재 인스턴스화에 대 한 암시적 포인터가 있습니다. 이를 `this` c #/c + + 및에서와 같이 `Me` 이라고 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
