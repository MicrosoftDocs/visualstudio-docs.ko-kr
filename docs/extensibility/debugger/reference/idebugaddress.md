---
description: 이 인터페이스는 항목의 주소를 나타냅니다.
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f49107e4d06fa828d059ebd9916ca254882ff0a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154966"
---
# <a name="idebugaddress"></a>IDebugAddress
이 인터페이스는 항목의 주소를 나타냅니다. 기호 처리기에 의해 반환 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는이 인터페이스를 구현 하 여 개체의 주소를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 많은 인터페이스에서 많은 메서드는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|개체와 해당 위치를 설명 하는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 구조체를 검색 합니다.|

## <a name="remarks"></a>설명
 기호 공급자는 특정 범위 (예: 함수, 메서드 또는 클래스) 내에서 개체와 해당 위치를 나타내기 위해이 인터페이스를 반환 합니다. 이 인터페이스는에서 반환 되 고 기호 공급자 및 식 계산기의 다양 한 메서드에 전달 됩니다. 일반적으로 기호 공급자는이 인터페이스의 내용을 해석 해야 하는 유일한 엔터티입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
