---
description: 식 계산기 (EE)를 사용 하 여 디버거의 출력 창에 메시지를 표시 합니다.
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 461003f3bdb83e51e8b5c525895d134b717d8fc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091905"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.

 식 계산기 (EE)를 사용 하 여 디버거의 출력 창에 메시지를 표시 합니다.

## <a name="syntax"></a>구문

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 콜백은 관리 되는 디버그 엔진에 의해 구현 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 식 계산기에서 사용 하 여 디버거의 출력 창에 출력을 보낼 수 있습니다.

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|지정 된 메시지 문자열을 디버거의 출력 창에 보냅니다.|

## <a name="requirements"></a>요구 사항
 헤더: Ee. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
