---
title: 아이디버그타입필드빌더2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed34284e373a7d96761aabe5a7f179367649bc0f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718296"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
배열 형식을 만들 수 있도록 **IDebugTypeFieldBuilder를** 확장합니다.

## <a name="syntax"></a>구문

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 기호 공급자로부터 얻을 수 있습니다.

## <a name="methods"></a>메서드
 이 인터페이스는 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) 인터페이스의 메서드 외에도 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|지정된 형식 및 크기의 배열을 만듭니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
