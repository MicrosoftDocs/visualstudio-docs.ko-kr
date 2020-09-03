---
title: IDebugSettingsCallback2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719943"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
디버그 엔진에서 메트릭 설정을 원격으로 읽을 수 있도록 합니다.

## <a name="syntax"></a>Syntax

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
이 인터페이스는 세션 디버그 관리자의 이벤트 콜백에서 구현 되며 디버그 엔진에서 사용 됩니다. Dbgmetric [d] .lib 대신 로컬에서 사용할 수도 있습니다.

## <a name="methods"></a>메서드
다음 표에서는의 메서드를 보여 줍니다 `IDebugSettingsCallback2` .

|메서드|설명|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|언어 및 공급 업체 식별자를 제공 하는 사용 가능한 식 계산기를 열거 합니다.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|메트릭이 지정 된 식 계산기 로컬 개체를 검색 합니다.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|식 계산기의 지정 된 메트릭에 해당 하는 값을 검색 합니다.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|이름 또는 메트릭이 지정 된 식 계산기 메트릭 파일을 검색 합니다.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|이름이 지정 된 식 계산기 메트릭에 대 한 고유 식별자를 검색 합니다.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|이름이 지정 된 식 계산기 메트릭의 값 문자열을 검색 합니다.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|해당 이름이 지정 된 메트릭의 값을 검색 합니다.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|해당 이름이 지정 된 메트릭의 고유 식별자를 검색 합니다.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|이름이 지정 된 메트릭의 값 문자열을 검색 합니다.|

## <a name="requirements"></a>요구 사항
헤더: Msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>예
다음 예제에서는 **IDebugSettingsCallback2** 개체를 매개 변수로 사용 하는 함수를 보여 줍니다.

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
