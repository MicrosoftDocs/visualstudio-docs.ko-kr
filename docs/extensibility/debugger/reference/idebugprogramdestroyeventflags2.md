---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722498"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
디버그 세션을 종료할 때 디버그 엔진이 UI의 기본 동작을 재정의할 수 있도록 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 합니다.

## <a name="syntax"></a>Syntax

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 디버그 엔진에 의해 구현 됩니다. 프로세스의 수명 동안 여러 프로그램을 만들고 삭제할 수 있는 호스트에 유용 합니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramDestroyEventFlags2` .

|메서드|설명|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|프로그램 소멸 플래그를 검색 합니다.|

## <a name="remarks"></a>설명
 UI의 기본 동작은 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 모든 프로그램이 프로그램 제거 이벤트를 보낸 후 디자인 모드로 돌아갑니다. 이 인터페이스를 사용 하면 디버그 엔진에서 해당 동작을 변경할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
