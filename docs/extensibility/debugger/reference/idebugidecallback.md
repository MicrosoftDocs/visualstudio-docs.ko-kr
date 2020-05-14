---
title: 이데버그디콜백 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727832"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Visual Studio 2015에서는 식 계산기 구현 방식이 더 이상 사용되지 않습니다. CLR 식 계산기 구현에 대한 자세한 내용은 [CLR 식 평가기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리식 평가기 샘플을](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)참조하십시오.

 식 계산기(EE)가 디버거의 출력 창에 메시지를 표시할 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 콜백은 관리되는 디버그 엔진에 의해 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 식 계산기에서 디버거의 출력 창에 출력을 보낼 때 사용할 수 있습니다.

## <a name="methods"></a>메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[디스플레이 메시지](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|지정된 메시지 문자열을 디버거의 출력 창으로 보냅니다.|

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
