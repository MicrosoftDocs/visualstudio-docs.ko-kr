---
description: 시작 된 실행 파일에 대 한 기호를 찾을 수 없음을 사용자에 게 경고 하기 위해 Visual Studio 디버거 UI에 신호를 보냅니다.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859c9c1d07a5f4660f2d13dcffac4f19659a2bc2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149823"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]시작 된 실행 파일에 대 한 기호를 찾을 수 없음을 사용자에 게 경고 하도록 디버거 UI에 신호를 보냅니다.

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진에서 구현 되며 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버거 UI에서 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
