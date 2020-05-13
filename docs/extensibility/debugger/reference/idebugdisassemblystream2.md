---
title: 이디버그디스어셈블리스트림2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732037"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
이 인터페이스는 명령 스트림을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진은 프로그램 코드의 분해를 지원하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드에 대 한 호출이 이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugDisassemblyStream2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|디스어셈블리 스트림의 현재 위치에서 시작하는 지침을 읽습니다.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|디스어셈블리 스트림에서 읽기 포인터를 지정된 위치에 대해 지정된 수의 명령을 이동합니다.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|특정 코드 컨텍스트에 대한 코드 위치 식별자를 반환합니다.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|지정된 코드 위치 식별자에 해당하는 코드 컨텍스트 개체를 반환합니다.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|현재 코드 위치를 나타내는 코드 위치 식별자를 반환합니다.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|이 디스어셈블리 스트림과 연결된 원본 문서를 가져옵니다.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|이 디스어셈블리 스트림의 범위를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|이 디스어셈블리 스트림의 크기를 가져옵니다.|

## <a name="remarks"></a>설명
 디스어셈블리 스트림을 만들어 전체 주소 공간 또는 공간 내의 함수 또는 모듈을 나타낼 수 있습니다. 각 명령은 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드에 대한 호출에 의해 반환되는 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조로 표시됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
