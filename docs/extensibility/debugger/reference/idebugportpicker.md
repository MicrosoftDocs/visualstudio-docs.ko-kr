---
title: 이데버그포트피커 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724840"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
포트를 선택 하기 위한 사용자 지정 된 UI를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스는 포트 공급자에 의해 구현 됩니다. 포트 공급자는 포트 피커를 CLSID로 노출하고 노출된 `metricPortPickerCLSID` CLSID에서 메트릭을 가리켜 포트 선택기를 정의합니다.

## <a name="methods"></a>메서드
 다음 표에서는 의 `IDebugPortPicker`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|사용자가 포트를 선택할 수 있도록 지정된 대화 상자를 표시합니다.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|서비스 공급자를 설정합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll
