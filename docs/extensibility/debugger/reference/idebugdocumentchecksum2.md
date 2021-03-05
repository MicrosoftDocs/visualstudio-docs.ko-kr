---
description: 디버그 문서에 대 한 체크섬을 나타내며 구성 요소 사이에 체크섬을 전달할 수 있습니다.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b39f381817cd98fd94b1c746cbdccde31e0b1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165568"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
디버그 문서에 대 한 체크섬을 나타내며 구성 요소 사이에 체크섬을 전달할 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 노출 하는 모든 구성 요소에서이 인터페이스를 구현할 수 있습니다. 그러나 주로 기호 파일 (* .pdb)에 포함 된 체크섬을 IDE로 다시 전달 하 고 소스를 찾을 때 사용할 수 있도록 디버그 엔진에서 구현 합니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDocumentChecksum2` .

|메서드|설명|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|사용할 최대 바이트 수를 지정 하 여 문서 체크섬 및 알고리즘 식별자를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
