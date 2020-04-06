---
title: 아이디버그세팅콜백2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719943"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
디버그 엔진이 메트릭 설정을 원격으로 읽을 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
이 인터페이스는 세션 디버그 관리자의 이벤트 콜백에 의해 구현되고 디버그 엔진에서 사용됩니다. 또한 Dbgmetric[d].lib 대신 로컬로 사용할 수도 있습니다.

## <a name="methods"></a>메서드
다음 표에서는 의 `IDebugSettingsCallback2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|언어 및 공급업체 식별자가 있는 사용 가능한 식 평가기를 학습합니다.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|메트릭이 지정된 식 평가기 로컬 개체를 검색합니다.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|식 계산기의 지정된 메트릭에 해당하는 값을 검색합니다.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|이름 또는 메트릭이 지정된 식 평가기 메트릭 파일을 검색합니다.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|이름지정식 평가기 메트릭에 대한 고유 식별자를 검색합니다.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|이름에서 식 계산기 메트릭의 값 문자열을 검색합니다.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|이름이 지정된 메트릭 값을 검색합니다.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|해당 이름이 지정된 메트릭의 고유 식별자를 검색합니다.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|이름이 지정된 메트릭의 값 문자열을 검색합니다.|

## <a name="requirements"></a>요구 사항
헤더: Msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="example"></a>예제
다음 예제에서는 **IDebugSettingsCallback2** 개체를 매개 변수로 사용 하는 함수를 보여 주다.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
