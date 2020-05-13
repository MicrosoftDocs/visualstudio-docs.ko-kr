---
title: IEE비주얼라이저 서비스::GetCustom뷰어리스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718021"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
이 메서드는 이 서비스에 대해 알고 있는 형식 시각화 도우미 목록을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`celtSkip`\
【인】 건너뛸 시각화 도우미 의 수입니다.

`celRequested`\
【인】 검색할 시각화 도우미 `rgViewers` 수(배열 크기도 지정).

`rgViewers`\
【인, 아웃】 채울 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조의 배열.

`pceltFetched`\
【아웃】 실제로 검색된 시각화 도우미 의 수입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 형식 시각화 도우미에 대 한 지원의 일환으로이 메서드에 요청을 전달 합니다. 식 계산기에서도 동일한 형식에 대한 사용자 지정 뷰어를 제공하는 경우 해당 사용자 지정 뷰어를 목록에 적절하게 채워진 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조를 추가할 수 있습니다. [GetCustomViewerCount이](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 이러한 추가 뷰어를 반영하는지 확인합니다.

 시각화 도우미와 뷰어 간의 차이점에 대한 자세한 내용은 [유형 시각화 도우미 및 사용자 지정 뷰어를](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 참조하세요.

## <a name="see-also"></a>참조
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
