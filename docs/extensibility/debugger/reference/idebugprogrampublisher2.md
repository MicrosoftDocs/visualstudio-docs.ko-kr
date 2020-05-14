---
title: 아이디버그프로그램출판사2 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721531"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
이 인터페이스를 사용하면 DE(디버그 엔진) 또는 사용자 지정 포트 공급자가 디버깅을 위해 프로그램을 등록할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
Visual Studio는 여러 프로세스에서 디버깅할 수 있도록 디버깅 중인 프로그램을 등록하기 위해 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
이 `CLSID_ProgramPublisher` 인터페이스를 `CoCreateInstance` 얻으려면 COM의 함수를 호출합니다(예제 참조). DE 또는 사용자 지정 포트 공급자는 이 인터페이스를 사용하여 디버깅 중인 프로그램을 나타내는 프로그램 노드를 등록합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|프로그램 노드를 DEs 및 세션 디버그 관리자(SDM)에서 사용할 수 있도록 합니다.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|프로그램 노드를 더 이상 사용할 수 없도록 제거합니다.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|DS 및 SDM에서 프로그램을 사용할 수 있도록 합니다.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|프로그램을 제거하여 더 이상 사용할 수 없도록 합니다.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|디버거가 있음을 나타내는 플래그를 설정합니다.|

## <a name="remarks"></a>설명
이 인터페이스를 사용하면 DEs 및 세션 디버그 관리자(SDM)에서 사용할 수 있도록 프로그램 및 프로그램 노드(즉, "게시")를 사용할 수 있습니다. 게시된 프로그램 및 프로그램 노드에 액세스하려면 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스를 사용합니다. 이것이 Visual Studio가 프로그램이 디버깅되고 있음을 인식할 수 있는 유일한 방법입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제
이 예제에서는 프로그램 게시자를 인스턴스화하고 프로그램 노드를 등록하는 방법을 보여 주며 있습니다. 이 [자습서에서](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae)가져온 것입니다.

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

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
