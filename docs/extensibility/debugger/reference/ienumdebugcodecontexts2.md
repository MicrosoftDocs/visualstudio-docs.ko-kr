---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717276"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
이 인터페이스는 디버그 세션과 관련 된 코드 컨텍스트 또는 특정 프로그램 또는 문서를 열거 합니다.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는이 인터페이스를 구현 하 여 프로그램의 특정 텍스트 위치에 대 한 코드 컨텍스트 목록 또는 특정 문서 컨텍스트의 코드 컨텍스트 목록을 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 를 호출 하 여 프로그램의 소스 문서에서 특정 텍스트 위치의 코드 컨텍스트 목록을 나타내는이 인터페이스를 가져옵니다.

 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) 를 호출 하 여 특정 소스 문서의 모든 코드 컨텍스트 목록을 나타내는이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IEnumDebugCodeContexts2` .

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|열거형 시퀀스에서 지정 된 수의 코드 컨텍스트를 검색 합니다.|
|[skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|열거형 시퀀스에서 지정 된 수의 코드 컨텍스트를 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|열거자의 코드 컨텍스트 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 를 호출 하 여 다음 문을 설정 하거나 소스 파일에 대 한 디스어셈블리를 표시할 때 사용자가 선택할 수 있는 코드 컨텍스트 목록을 채웁니다. 예를 들어 c + + 스타일 템플릿의 인스턴스가 여러 개 있는 경우 여러 코드 컨텍스트가 발생할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
