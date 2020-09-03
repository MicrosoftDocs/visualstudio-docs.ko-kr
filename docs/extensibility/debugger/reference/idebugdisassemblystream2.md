---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732037"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
이 인터페이스는 명령 스트림을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버그 엔진은 프로그램 코드의 디스어셈블리를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getdisassemblystream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드를 호출 하면이 인터페이스가 반환 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugDisassemblyStream2` .

|메서드|설명|
|------------|-----------------|
|[읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|디스어셈블리 스트림의 현재 위치에서 시작 하는 명령을 읽습니다.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|지정 된 위치에 상대적인 지정 된 수의 명령을 디스어셈블리 스트림에서 읽기 포인터를 이동 합니다.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|특정 코드 컨텍스트의 코드 위치 식별자를 반환 합니다.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|지정 된 코드 위치 식별자에 해당 하는 코드 컨텍스트 개체를 반환 합니다.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|현재 코드 위치를 나타내는 코드 위치 식별자를 반환 합니다.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|이 디스어셈블리 스트림과 연결 된 소스 문서를 가져옵니다.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|이 디스어셈블리 스트림의 범위를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|이 디스어셈블리 스트림의 크기를 가져옵니다.|

## <a name="remarks"></a>설명
 전체 주소 공간을 나타내거나 공간 내의 함수 또는 모듈만을 나타내기 위해 디스어셈블리 스트림을 만들 수 있습니다. 각 명령은 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드를 호출 하 여 반환 되는 [disassemblydata](../../../extensibility/debugger/reference/disassemblydata.md) 구조체로 표현 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
