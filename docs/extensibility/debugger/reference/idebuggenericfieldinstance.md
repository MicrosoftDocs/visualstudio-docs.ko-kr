---
title: 아이디버그제네릭필드인스턴스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9723c146ecb5096ea6f3635a3d5cae5c48e573e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728118"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
관리 되는 코드 제네릭 형식에 대 한 필드의 인스턴스를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericFieldInstance : IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|이 인스턴스에 대한 형식 매개 변수 인수를 검색합니다.|
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|이 인스턴스에 대한 형식 매개 변수 인수 수를 반환합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
