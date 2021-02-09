---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14bcfb7498ad22156ae18998ebe5958aad1b9026
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928759"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스를 확장 하 여 모듈 및 프로세스 인터페이스를 검색할 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진에서 구현 되 고 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버그 패키지에서 사용 됩니다.

## <a name="methods"></a>메서드
 인터페이스의 메서드 외에도 `IDebugCodeContext2` 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|디버그 모듈의 인터페이스에 대 한 참조를 검색 합니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|디버그 프로세스의 인터페이스에 대 한 참조를 검색 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 구현 하지 않아도 되는 선택적 인터페이스입니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
