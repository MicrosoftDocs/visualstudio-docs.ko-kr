---
title: 아이디버그프로그램제공자2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721699"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
이 등록된 인터페이스를 사용하면 세션 디버그 관리자(SDM)가 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) 인터페이스를 통해 "게시된" 프로그램에 대한 정보를 얻을 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
디버그 엔진(DE)은 디버깅 중인 프로그램에 대한 정보를 제공하기 위해 이 인터페이스를 구현합니다. 이 인터페이스는 `metricProgramProvider` [디버깅을 위한 SDK 도우미에](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)설명된 대로 메트릭을 사용하여 레지스트리의 DE 섹션에 등록됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
레지스트리에서 가져온 `CoCreateInstance` 프로그램 `CLSID` 공급자와 COM의 함수를 호출합니다. 예제를 참조하십시오.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|방법|설명|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|다양한 방법으로 필터링된 실행 중인 프로그램에 대한 정보를 가져옵니다.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|특정 프로세스 ID가 지정된 프로그램 노드를 가져옵니다.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|콜백을 설정하여 특정 종류의 프로세스와 관련된 공급자 이벤트를 감시합니다.|
|[Setlocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|DE에 필요한 언어별 리소스에 대한 로캘을 설정합니다.|

## <a name="remarks"></a>설명
일반적으로 프로세스는 이 인터페이스를 사용하여 해당 프로세스에서 실행 중인 프로그램에 대해 알아보십시오.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
