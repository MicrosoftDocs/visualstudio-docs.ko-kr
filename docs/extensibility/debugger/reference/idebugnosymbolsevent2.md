---
description: 시작 된 실행 파일에 대 한 기호를 찾을 수 없음을 사용자에 게 경고 하기 위해 Visual Studio 디버거 UI에 신호를 보냅니다.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a060436575d51710fcef9c444ac843aa56195d0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058406"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]시작 된 실행 파일에 대 한 기호를 찾을 수 없음을 사용자에 게 경고 하도록 디버거 UI에 신호를 보냅니다.

## <a name="syntax"></a>구문

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진에서 구현 되며 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 디버거 UI에서 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
