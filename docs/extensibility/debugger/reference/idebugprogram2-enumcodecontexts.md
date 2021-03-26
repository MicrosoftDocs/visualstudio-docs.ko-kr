---
description: 소스 파일에서 지정 된 위치에 대 한 코드 컨텍스트 목록을 검색 합니다.
title: 'IDebugProgram2:: EnumCodeContexts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2dbcc3f967f0569efcfc1287ba2b215760ce0b34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076058"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
소스 파일에서 지정 된 위치에 대 한 코드 컨텍스트 목록을 검색 합니다.

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
진행 IDE에 알려진 소스 파일의 추상 위치를 나타내는 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) 개체입니다.

`ppEnum` 제한이 코드 컨텍스트 목록을 포함 하는 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드를 사용 하면 세션 디버그 관리자 (SDM) 또는 IDE에서 소스 파일 위치를 코드 위치에 매핑할 수 있습니다. 소스에서 여러 코드 블록 (예: c + + 템플릿)을 생성 하는 경우 두 개 이상의 코드 컨텍스트가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
