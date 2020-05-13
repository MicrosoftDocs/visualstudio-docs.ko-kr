---
title: 아이디버그프로퍼피티3:GetCustom뷰어카운트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16cb623f58668362e5e308e1d66dfd6ca7c0fb8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721188"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
이 속성에 사용할 수 있는 사용자 지정 뷰어 수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCustomViewerCount(
    ULONG* pcelt
);
```

```csharp
int GetCustomViewerCount(
    out uint pcelt
);
```

## <a name="parameters"></a>매개 변수
`pcelt`\
【아웃】 이 속성에 사용할 수 있는 사용자 지정 뷰어 수입니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
형식 시각화 도우미를 지원 하기 위해이 메서드는 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) 메서드에 호출을 전달 합니다. 식 계산기에서 이 속성의 형식에 대한 사용자 지정 뷰어도 지원하는 경우 이 메서드는 반환된 값에 사용자 지정 뷰어 수를 추가합니다.

유형 시각화 도우미와 사용자 지정 뷰어 간의 차이점에 대한 자세한 내용은 [유형 시각화 도우미 및 사용자 지정 뷰어를](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)참조하십시오.

## <a name="example"></a>예제
다음 예제에서는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 노출 하는 **CProperty** 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)
{
    if (pcelt == NULL)
    {
        return E_POINTER;
    }

    if (GetVisualizerService())
    {
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);
    }
    else
    {
        return E_NOTIMPL;
    }
}
```

## <a name="see-also"></a>참조
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
