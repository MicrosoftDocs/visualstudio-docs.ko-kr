---
title: 아이디버그문서체크섬2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731902"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
디버그 문서에 대한 체크섬을 나타내고 구성 요소 간에 체크섬을 전달할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 노출하는 모든 구성 요소에서 구현할 수 있습니다. 그러나 주로 디버그 엔진에 의해 구현되므로 기호 파일(*.pdb)에 포함된 체크섬을 IDE로 다시 전달하고 소스를 찾을 때 사용할 수 있습니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugDocumentChecksum2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|사용할 최대 바이트 수가 주어지면 문서 체크섬 및 알고리즘 식별자를 검색합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
