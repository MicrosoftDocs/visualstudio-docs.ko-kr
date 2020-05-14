---
title: 아이데버그제네릭필드정의 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 019633b62d46f6a8ac68e6f5f4abc888e6986ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728200"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
관리 되는 코드 제네릭 형식에 대 한 필드의 정의 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|형식 인수의 배열이 주어진 필드 인스턴스를 생성합니다.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|매개 변수 수가 지정된 형식 매개 변수를 검색합니다.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|제네릭 필드와 연결된 형식 매개 변수의 수를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
