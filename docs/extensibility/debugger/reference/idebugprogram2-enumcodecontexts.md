---
title: 아이디버그프로그램2::에이넘코드컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c22a5ce398e76ee97b2f0448900fd4e38f996615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723043"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
소스 파일에서 지정된 위치에 대한 코드 컨텍스트 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumCodeContexts( 
   IDebugDocumentPosition2*  pDocPos,
   IEnumDebugCodeContexts2** ppEnum
);
```

```csharp
int EnumCodeContexts( 
   IDebugDocumentPosition2     pDocPos,
   out IEnumDebugCodeContexts2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`pDocPos`\
【인】 IDE에 알려진 소스 파일에서 추상적 위치를 나타내는 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 개체입니다.

`ppEnum`【아웃】 코드 컨텍스트 목록을 포함하는 [IEnumDebugCodeCodes2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 방법을 사용하면 세션 디버그 관리자(SDM) 또는 IDE에서 소스 파일 위치를 코드 위치로 매핑할 수 있습니다. 소스가 여러 코드 블록(예: C++ 템플릿)을 생성하는 경우 두 개 이상의 코드 컨텍스트가 반환됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
