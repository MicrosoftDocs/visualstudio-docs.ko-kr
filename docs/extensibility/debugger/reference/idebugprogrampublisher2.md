---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721531"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
이 인터페이스는 디버그 엔진 (DE) 또는 사용자 지정 포트 공급자가 디버깅을 위해 프로그램을 등록할 수 있도록 합니다.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
Visual Studio는이 인터페이스를 구현 하 여 여러 프로세스에서 디버그할 수 있도록 디버깅 중인 프로그램을 등록 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
을 사용 하 여 COM의 함수를 호출 `CoCreateInstance` `CLSID_ProgramPublisher` 하 여이 인터페이스를 가져옵니다 (예제 참조). DE 또는 사용자 지정 포트 공급자는이 인터페이스를 사용 하 여 디버깅 중인 프로그램을 나타내는 프로그램 노드를 등록 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|프로그램 노드를 DEs 및 세션 디버그 관리자 (SDM)에서 사용할 수 있도록 설정 합니다.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|프로그램 노드를 더 이상 사용할 수 없도록 제거 합니다.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|DEs 및 SDM에서 프로그램을 사용할 수 있도록 합니다.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|프로그램을 더 이상 사용할 수 없도록 제거 합니다.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|디버거가 있음을 나타내는 플래그를 설정 합니다.|

## <a name="remarks"></a>설명
이 인터페이스는 DEs 및 세션 디버그 관리자 (SDM)에서 사용할 수 있도록 프로그램 및 프로그램 노드를 사용할 수 있도록 합니다 (즉, "게시"). 게시 된 프로그램 및 프로그램 노드에 액세스 하려면 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 사용 합니다. Visual Studio에서 프로그램을 디버그 하는 것을 인식할 수 있는 유일한 방법입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예
이 예제에서는 프로그램 게시자를 인스턴스화하고 프로그램 노드를 등록 하는 방법을 보여 줍니다. 이는 자습서의 [프로그램 노드 게시](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)에서 가져옵니다.

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
