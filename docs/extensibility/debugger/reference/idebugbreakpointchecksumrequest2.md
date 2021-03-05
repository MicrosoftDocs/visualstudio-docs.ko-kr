---
description: 중단점 요청에 대 한 문서 체크섬을 나타냅니다.
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6bb0bdd70d2d4d1d56e341bc8f21ef1127433219
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173712"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
중단점 요청에 대 한 문서 체크섬을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 패키지에서 구현 되 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 고 디버그 엔진에서 사용 됩니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugBreakpointChecksumRequest2` .

|메서드|설명|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|사용할 체크섬 알고리즘의 고유 식별자가 지정 된 경우 중단점 요청에 대 한 문서 체크섬을 검색 합니다.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|이 문서에 체크섬을 사용할 수 있는지 여부를 확인 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
