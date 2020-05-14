---
title: 이넘디버그코드컨텍스트2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717276"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
이 인터페이스는 디버그 세션 또는 특정 프로그램 또는 문서와 관련된 코드 컨텍스트를 개과연합니다.

## <a name="syntax"></a>구문

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE(디버그 엔진)는 프로그램의 특정 텍스트 위치에 대한 코드 컨텍스트 목록 또는 특정 문서 컨텍스트에 대한 코드 컨텍스트 목록을 나타내기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 프로그램의 원본 문서에서 특정 텍스트 위치에 대한 코드 컨텍스트 목록을 나타내는 이 인터페이스를 얻으려면 [EnumCodeContexts를](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 호출합니다.

 특정 소스 문서의 모든 코드 컨텍스트 목록을 나타내는 이 인터페이스를 가져오려면 [EnumCodeContexts를](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IEnumDebugCodeContexts2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|열거 시퀀스에서 지정된 수의 코드 컨텍스트를 검색합니다.|
|[건너뛸](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|열거 시퀀스에서 지정된 수의 코드 컨텍스트를 건너뜁니다.|
|[다시 설정](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|열거 순서를 시작 부분으로 재설정합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|현재 열거체와 동일한 열거 상태를 포함하는 열거형 을 만듭니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|열거형의 코드 컨텍스트 수를 가져옵니다.|

## <a name="remarks"></a>설명
 Visual Studio는 [EnumCodeContexts를](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) 호출하여 다음 문을 설정하거나 소스 파일에 대한 디스어셈블리를 표시할 때 사용자가 선택할 수 있는 코드 컨텍스트 목록을 채웁니다. 예를 들어 C++스타일 템플릿의 인스턴스가 여러 개인 경우 여러 코드 컨텍스트가 발생할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
