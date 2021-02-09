---
title: 'IDebugProperty3:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdabe777bf2147dee2b98ca552183ae0e14d16f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888214"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
이 속성과 연결 된 사용자 지정 뷰어 목록을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCustomViewerList(
    ULONG                celtSkip,
    ULONG                celtRequested,
    DEBUG_CUSTOM_VIEWER* rgViewers,
    ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
    uint                  celtSkip,
    uint                  celtRequested,
    DEBUG_CUSTOM_VIEWER[] rgViewers,
    out uint              pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celtSkip`\
진행 건너뛸 뷰어 수입니다.

`celtRequested`\
진행 검색할 뷰어 수 (배열의 크기도 지정 `rgViewers` )입니다.

`rgViewers`\
[in, out] 채워질 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조체의 배열입니다.

`pceltFetched`\
제한이 반환 된 실제 뷰어 수입니다.

## <a name="return-value"></a>Return Value
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
형식 시각화 도우미를 지원 하기 위해이 메서드는 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드에 대 한 호출을 전달 합니다. 식 계산기에서이 속성의 형식에 대 한 사용자 지정 뷰어도 지 원하는 경우이 메서드는 적절 한 사용자 지정 뷰어를 목록에 추가할 수 있습니다.

형식 시각화 도우미와 사용자 지정 뷰어 간의 차이점에 대 한 자세한 내용은 [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 를 참조 하세요.

## <a name="example"></a>예제
다음 예제에서는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 노출 하는 **cproperty** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)
{
    if (NULL == prgViewers)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>참고 항목
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
