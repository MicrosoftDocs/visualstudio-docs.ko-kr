---
title: 그래픽 이벤트 목록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5c4e8f39ff77779985536e53d98ddc2785b109b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301100"
---
# <a name="graphics-event-list"></a>그래픽 이벤트 목록
Visual Studio Graphics Analyzer의 그래픽 이벤트 목록을 사용하여 게임 또는 앱의 프레임 렌더링 중 기록된 Direct3D 이벤트를 살펴봅니다.

 이벤트 목록은 다음과 같습니다.

 ![이름에 "Index"가 있는 이벤트 목록입니다.](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>이벤트 목록 사용
 이벤트 목록에서 이벤트를 선택하면 다른 그래픽 분석 도구에 표시되는 정보에 반영됩니다. 이러한 다른 도구와 함께 이벤트 목록을 사용하면 렌더링 문제를 자세히 검사하여 원인을 확인할 수 있습니다. 다른 그래픽 분석 도구와 이벤트 목록을 함께 사용하여 렌더링 문제를 해결할 수 있는 방법에 대해 자세히 알아보려면 [예제](graphics-diagnostics-examples.md)를 참조하세요.

 수천 개의 이벤트가 포함되어 있을 수 있는 복잡한 프레임을 둘러보려면 이벤트 목록의 기능을 효율적으로 사용할 수 있어야 합니다. 이벤트 목록을 효율적으로 사용하고 자신에게 가장 잘 맞는 보기를 선택하며 검색 기능을 사용하여 이벤트 목록을 필터링하려면 링크를 따라가 이벤트와 연결된 Direct3D 개체에 대해 좀 더 자세히 알아보고 화살표 단추를 사용하여 그리기 호출 간에 신속하게 이동합니다.

### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12의 색으로 구분된 이벤트
 Direct3D 12는 다른 하드웨어 기능에 해당하는 여러 큐를 표시합니다. Direct3D 12의 특정 그래픽 이벤트와 연결된 큐를 쉽게 식별하도록 Direct3D 12 앱의 캡처 작업을 수행할 때 이벤트 목록의 이벤트는 큐에 따라 색으로 구분됩니다.

|Direct3D 12 큐|색|
|-----------------------|-----------|
|렌더링 큐|녹색|
|컴퓨팅 큐|노랑|
|복사 큐|주황|

 Direct3D 11은 여러 큐를 표시하지 않으므로 Direct3D 11 앱의 캡처 작업을 수행할 대 이벤트 목록의 이벤트가 색으로 구분되지 않습니다.

### <a name="event-list-views"></a>이벤트 목록 보기
 이벤트 목록은 워크플로 및 기본 설정을 지원하기 위해 다양한 방법으로 그래픽 이벤트를 구성하는 두 가지 다른 보기를 지원합니다. 첫 번째 뷰는 *GPU 작업 뷰*로, 이벤트 및 해당 연결 상태를 계층적으로 구성합니다. 두 번째 보기는 *타임라인 보기* 로, 이벤트를 단순 목록에 연대순으로 구성합니다.

 **GPU 작업** 뷰는 캡처된 이벤트 및 해당 상태를 계층적으로 표시합니다. 계층 구조의 최상위는 그리기 호출, 지우기, 표시 및 보기 처리 작업과 같은 이벤트로 구성됩니다. 이벤트 목록에서 그리기 호출을 확장하여 그리기 호출 시 최신이었던 디바이스 상태를 표시하고 각 상태 종류를 더욱 확장하여 값을 설정하는 이벤트를 표시할 수 있습니다. 이 수준에서는 이전 프레임에서 특정 상태를 설정했는지 여부와 마지막 그리기 호출 후 두 번 이상 설정되었는지 확인할 수 있습니다.

 **타임라인** 뷰는 캡처된 각 이벤트를 연대순으로 표시합니다. 이벤트 목록을 구성하는 이 방법은 이전 버전의 Visual Studio와 동일합니다.

##### <a name="to-change-the-event-list-view-mode"></a>이벤트 목록 보기 모드를 변경하려면

- **그래픽 이벤트 목록** 창의 이벤트 목록 위에 **뷰** 드롭다운이 있어서 **타임라인** 뷰 또는 **GPU 작업** 뷰 중에서 선택할 수 있습니다.

### <a name="filtering-events"></a>이벤트 필터링
 **그래픽 이벤트 목록** 창의 오른쪽 맨 위 모퉁이에 있는 검색 상자를 사용하여 이름에 특정 키워드가 포함된 이벤트만 포함하도록 이벤트 목록을 필터링할 수 있습니다. 이전 그림에서처럼 `Vertex`와 같은 키워드 하나를 지정하거나 `Draw;Primitive`와 같이 세미콜론으로 구분된 목록을 사용하여 여러 키워드를 지정할 수 있습니다. 그러면 이름에 `Draw` 또는 `Primitive` 가 포함된 이벤트를 찾게 됩니다. 검색어는 공백을 구분합니다. 예를 들어 `VSSet` 와 `VS Set` 는 다른 검색어입니다. 따라서 검색어는 주의 깊게 입력해야 합니다.

### <a name="moving-between-draw-calls"></a>그리기 호출 간에 이동
 `Draw` 호출 검사는 특히 중요하므로 **그래픽 이벤트 목록** 창의 왼쪽 맨 아래 모퉁이에 있는 **다음 그리기 호출로 이동** 및 **이전 그리기 호출로 이동** 단추를 사용하여 그리기 호출을 찾으면 그리기 호출 간에 신속하게 이동할 수 있습니다.

### <a name="links-to-graphics-objects"></a>그래픽 개체에 대한 링크
 특정 그래픽 이벤트를 파악하려면 현재 Direct3D 상태 또는 이벤트에서 참조하는 Direct3D 개체에 대한 추가 정보가 필요할 수 있습니다. 자세한 내용을 보기 위해 따라갈 수 있는 이러한 정보에 대한 링크를 많은 이벤트에서 제공합니다.

## <a name="kinds-of-events-and-event-markers"></a>이벤트 및 이벤트 표식의 종류
 이벤트 목록에 표시되는 이벤트는 일반 이벤트, 그리기 이벤트, 사용자 정의 이벤트 그룹 및 사용자 정의 이벤트 표식, 이렇게 4가지 범주로 구성됩니다. 일반 이벤트를 제외한 각 이벤트는 이벤트가 속한 범주를 나타내는 아이콘과 함께 표시됩니다.

|아이콘|이벤트 설명|
|----------|-----------------------|
|(아이콘 없음)|일반 이벤트<br /> 사용자 정의 이벤트, 사용자 정의 이벤트 그룹 또는 그리기 이벤트가 아닌 모든 이벤트입니다.|
|![그리기 이벤트 아이콘](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|그리기 이벤트<br /> 캡처된 프레임 중 발생한 그리기 이벤트를 표시합니다.|
|![사용자 정의 이벤트 마커 아이콘](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|사용자 정의 이벤트 그룹<br /> 앱에서 정의한 것처럼 그룹 관련 이벤트입니다.|
|![사용자 정의 이벤트 마커 아이콘](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|사용자 정의 이벤트 표식<br /> 앱에서 정의한 것처럼 특정 위치를 표시합니다.|

## <a name="marking-user-defined-events-in-your-app"></a>앱에서 사용자 정의 이벤트 표시
 사용자 정의 이벤트는 앱에 고유합니다. 이러한 이벤트를 사용하여 앱에서 발생한 중요한 이벤트를 그래픽 이벤트 목록의 이벤트와 연관시킬 수 있습니다. 예를 들어 사용자 정의 이벤트 그룹을 만들어 관련 이벤트(예: 사용자 인터페이스를 렌더링하는 이벤트)를 그룹 또는 계층 구조로 그룹화하여 이벤트 목록을 보다 쉽게 찾을 수 있습니다. 또는 특정 종류의 개체를 그릴 때 표식을 만들어 이벤트 목록에서 그래픽 이벤트를 쉽게 찾을 수 있습니다.

 앱에서 그룹 및 표식을 만들려면 다른 Direct3D 디버깅 도구에서 사용하도록 Direct3D에서 제공하는 것과 동일한 API를 사용합니다. 이러한 API는 경우에 따라 Direct3D 버전 간에 변경되지만 기본 기능은 동일합니다.

### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12의 사용자 정의 이벤트
 Direct3D 12에서 그룹 및 표식을 만들려면 이 섹션에 설명된 API를 사용합니다. 아래 표에서는 명령 큐나 명령 목록에서 이벤트를 표시할지에 따라 사용할 수 있는 API를 간략히 설명합니다.

|API 설명|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|사용자 정의 이벤트 가용성 확인|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|이벤트 그룹 시작|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|이벤트 그룹 종료|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|이벤트 표식 만들기|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 이하의 사용자 정의 이벤트
 Direct3D 11 이하에서 그룹 및 표식을 만들려면 이 섹션에 설명된 API를 사용합니다. 아래 표에서는 Direct3D 11의 여러 버전 및 Direct3D 이전 버전에서 사용할 수 있는 API를 간략히 설명합니다.

|API 설명|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](/windows/win32/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) (Direct3D 11.1)|D3DPerf_ API 패밀리(Direct3D 11.0 및 이전)|
|---------------------| - | - | - |
|이벤트 그룹 시작|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|이벤트 그룹 종료|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|이벤트 표식 만들기|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 사용 중인 Direct3D 버전에서 지원하는 API 중 하나를 사용할 수 있습니다. 예를 들어 Direct3D 11.1 API를 대상으로 하는 경우 `SetMarker` 또는 `D3DPerf_SetMarker` 를 사용하여 이벤트 표식을 만들 수 있지만 `SetMarkerInt` 는 Direct3D 11.2에서만 사용할 수 있으므로 사용하지 마세요. 그리고 다른 버전의 Direct3D를 지원하는 API를 동일한 앱에서 함께 사용할 수 있습니다.

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>리소스 기록
Visual Studio 2017 이상에는 **리소스 기록** 창이 포함되어 있습니다.  **이벤트 목록** 창에서 항목 옆의 조사식 아이콘 ![조사식 아이콘](media/gfx_watch.png)을 선택하면 아래와 같은 **리소스 기록** 창이 표시됩니다.

![리소스 기록](media/gfx_diag_resource_history.png)

이 창을 사용하여 이벤트 목록에서 선택한 항목의 기록을 볼 수 있습니다.  위쪽의 드롭다운을 사용하여 기록을 볼 다른 항목을 선택할 수 있습니다.  창의 위쪽 절반에는 **프레임 설정 이벤트**가 포함되어 있습니다.  이러한 이벤트는  만들기 형식 범주에 속하며 일반적으로 리소스를 초기화하고 만드는 호출입니다.  창의 아래쪽 절반에는 **프레임 이벤트** 섹션이 있습니다.  이러한 이벤트는 리소스를 사용하는 동안 발생하는 일반적인 읽기 및 쓰기 이벤트입니다.

| Column | 설명 |
|-----------| - |
| **Type** | 항목의 형식을 보여 줍니다(일반적으로  만들기,  읽기 및  쓰기). |
| **보기** | 해당 시점에서 리소스의 썸네일을 표시합니다.  해당 시점에서 리소스의 세부 정보 보기를 열려면 썸네일을 두 번 클릭합니다. |
| **Event** | 이벤트를 생성한 메서드 호출을 보여 줍니다.  각 항목에 대한 추가 기록은 적절한 줄에서 조사식 아이콘 ![조사식 아이콘](media/gfx_watch.png)을 선택하여 볼 수 있습니다.  또한 위 스크린샷의 `m_commandList` 같이 파란색 텍스트로 그려진 모든 항목을 선택하여 자세한 내용을 확인할 수 있습니다. |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>참조
- [연습: 디바이스 상태로 인해 누락된 개체](walkthrough-missing-objects-due-to-device-state.md)