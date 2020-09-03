---
title: 'IDebugDocument2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2af7f4dc01ee3a2fe3fb5026602a0b5d4f766b17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731964"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
여러 형식 중 하나로 문서 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName( 
   GETNAME_TYPE gnType,
   BSTR*        pbstrFileName
);
```

```csharp
int GetName( 
   enum_GETNAME_TYPE gnType,
   out string        pbstrFileName
);
```

## <a name="parameters"></a>매개 변수
`gnType`\
진행 반환할 이름 유형을 결정 하는 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 열거형의 값입니다.

`pbstrFileName`\
제한이 문서 이름을 포함 하는 문자열을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어이 메서드는 문서 이름을 제목으로 반환 하거나 파일 이름 또는 파일 이름의 일부로 반환할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
