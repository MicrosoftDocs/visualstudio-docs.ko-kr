---
description: 이 메서드는이 서비스에서 인식 하는 형식 시각화 도우미의 목록을 반환 합니다.
title: 'IEEVisualizerService:: GetCustomViewerList | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0bd9c633c6b65bbd597619f9fd30487a734d9004
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222902"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
이 메서드는이 서비스에서 인식 하는 형식 시각화 도우미의 목록을 반환 합니다.

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
진행 건너뛸 시각화 도우미의 수입니다.

`celRequested`\
진행 검색할 시각화 도우미 수 (배열의 크기도 지정 `rgViewers` )입니다.

`rgViewers`\
[in, out] 채워질 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조체의 배열입니다.

`pceltFetched`\
제한이 실제로 검색 된 시각화 도우미 수입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 는 형식 시각화 도우미에 대 한 지원의 일부로이 메서드에 요청을 전달 합니다. 식 계산기가 동일한 형식에 대 한 사용자 지정 뷰어를 제공 하는 경우 해당 사용자 지정 뷰어에 대 한 적절 한 채우기 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 구조를 목록에 추가할 수 있습니다. [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 가 이러한 추가 뷰어를 반영 하는지 확인 합니다.

 시각화 도우미와 뷰어 간의 차이점에 대 한 자세한 내용은 [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
