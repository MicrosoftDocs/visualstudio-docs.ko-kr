---
title: 이데버그프로그램파괴이벤트플래그2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722498"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
디버그 세션을 종료할 때 디버그 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 엔진이 UI의 기본 동작을 재정의할 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 디버그 엔진에 의해 구현됩니다. 프로세스의 수명 동안 여러 프로그램을 만들고 파괴할 수 있는 호스트에 유용합니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugProgramDestroyEventFlags2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|프로그램이 플래그를 삭제검색합니다.|

## <a name="remarks"></a>설명
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI의 기본 동작은 모든 프로그램이 프로그램 삭제 이벤트를 보낸 후 디자인 모드로 돌아가는 것입니다. 이 인터페이스를 사용하면 디버그 엔진이 해당 동작을 변경할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
