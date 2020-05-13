---
title: 아이디버그포트공급업체설명2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724361"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
UI가 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 프로세스에 연결 대화 상자의 **전송 정보** 섹션 내에 텍스트를 **표시할 수 있도록 합니다.**

## <a name="syntax"></a>구문

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 포트 공급자에 의해 구현 됩니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugPortSupplierDescription2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[설명 받기](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|포트 공급자에 대한 설명 및 설명 메타데이터를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
