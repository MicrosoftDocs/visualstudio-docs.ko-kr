---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd4f85bfdfb58baff3301c2d858f52933f16d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958598"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
포트를 선택 하기 위한 사용자 지정 UI를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 포트 공급자에 의해 구현 됩니다. 포트 공급자는 CLSID로 노출 하 고 `metricPortPickerCLSID` 노출 된 CLSID에서 메트릭을 가리켜 포트 선택기를 정의 합니다.

## <a name="methods"></a>메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPortPicker` .

|메서드|Description|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|사용자가 포트를 선택할 수 있는 지정 된 대화 상자를 표시 합니다.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|서비스 공급자를 설정 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll
