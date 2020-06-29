---
title: GPU 사용량 | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aa4cce032a5eb80a11568a83c1166b5690bd688
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85279884"
---
# <a name="gpu-usage"></a>GPU 사용량

Visual Studio 성능 및 진단 허브의 GPU 사용량 도구를 사용하여 Direct3D 앱의 개략적인 하드웨어 사용량을 더 잘 이해할 수 있습니다. 앱의 성능이 CPU에 의존하는지 아니면 GPU에 더 의존하는지를 확인하고 플랫폼 하드웨어를 더 효율적으로 사용할 수 있는 방법에 대해 통찰을 얻을 수 있습니다. GPU 사용량은 Direct3D 12, Direct3D 11 및 Direct3D 10을 사용하는 앱을 지원합니다. Direct2D, OpenGL 등 다른 그래픽 API는 지원하지 않습니다.

**GPU 사용량 보고서** 창의 모양은 다음과 같습니다.

![CPU 및 GPU 타임라인을 사용한 GPU 사용량 보고서의 스크린샷](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>요구 사항

그래픽 진단 요구 사항 외에 GPU 사용량 도구를 사용하려면 다음이 필요합니다.

- 필수적인 타이밍 계측을 지원하는 GPU 및 드라이버

  > [!NOTE]
  > 지원되는 하드웨어 및 드라이버에 대한 자세한 내용은 이 문서 끝에 있는 [하드웨어 및 드라이버 지원](#hwsupport)을 참조하세요.

그래픽 진단 요구 사항에 대한 자세한 내용은 [시작하기](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)를 참조하세요.

## <a name="use-the-gpu-usage-tool"></a>GPU 사용량 도구 사용

GPU 사용량 도구에서 앱을 실행하면 Visual Studio에서 진단 세션을 만듭니다. 이 세션은 앱의 렌더링 성능과 GPU 사용량에 대한 개략적인 정보를 그래프에서 실시간으로 보여줍니다.

GPU 사용량 도구를 시작하려면

1. 주 메뉴에서 **디버그** > **성능 및 진단**을 선택합니다(또는 키보드에서 Alt+F2 키를 누름).

2. **성능 및 진단** 허브에서 **GPU 사용량** 옆에 있는 상자를 선택합니다. 선택적으로 사용하려는 다른 도구 옆에 있는 확인란을 선택합니다. 다수의 성능 및 진단 도구를 동시에 실행하여 앱 성능을 보다 자세히 확인할 수 있습니다.

    ![GPU 사용량이 선택된 성능 및 진단 허브의 스크린샷](media/gpuusageselected.png "GPU 사용량 선택됨")

   > [!NOTE]
   > 일부 성능 및 진단 도구는 동시에 사용할 수 없습니다.

3. **성능 및 진단** 허브의 맨 아래에 있는 **시작** 단추를 선택하여 선택한 도구 아래의 앱을 실행합니다.

실시간으로 표시되는 개략적인 정보에는 프레임 타이밍, 프레임 속도 및 GPU 사용량이 포함됩니다. 이러한 정보는 개별적으로 그래프에 표시되지만 모두 공통 시간 단위를 사용하여 관계를 쉽게 이해할 수 있습니다.

**프레임 시간(ms)** 및 **초당 프레임(FPS)** 그래프에는 각각 초당 60fps 및 30fps의 성능 목표를 보여주는 두 개의 빨간색 가로줄이 있습니다. 프레임 시간 그래프에서 그래프가 선 아래에 있으면 앱이 성능 목표를 초과하는 것이고 그래프가 선 위에 있으면 목표에 미달하는 것입니다. 초당 프레임 그래프의 경우 반대입니다. 즉, 그래프가 선 위에 있으면 앱이 성능 목표를 초과하는 것이고 그래프가 선 아래에 있으면 목표에 미달하는 것입니다. 기본적으로 이러한 그래프를 사용하여 앱 성능을 개략적으로 파악하고, 조사가 필요한 속도 저하를 식별합니다. 예를 들어 프레임 속도가 갑자기 떨어지거나 GPU 사용률에 급증하는 경우 추가 조사가 필요할 수 있습니다.

GPU 사용량 도구에서 앱이 실행 중일 때 진단 세션은 GPU에서 실행된 그래픽 이벤트에 대한 자세한 정보를 수집합니다. 이 정보를 사용하여 앱이 하드웨어를 사용하는 방식에 대한 보다 세부적인 보고서를 생성합니다. 수집된 정보에서 이 보고서를 생성하는 데는 다소 시간이 걸리기 때문에, 진단 세션에서 정보 수집이 완료된 후에만 보고서를 생성할 수 있습니다.

성능 또는 사용률 문제를 보다 면밀하게 검토하려면 보고서를 생성할 수 있도록 성능 정보 수집을 중지합니다.

GPU 사용량 보고서를 생성하고 보려면 다음 절차를 따릅니다.

1. 진단 세션 창 아랫부분에서 **수집 중지** 링크를 선택하거나 왼쪽 위 모서리에 있는 **중지**를 선택합니다.

   ![진단 세션 창 스크린샷](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. 보고서의 윗부분에서 조사하려는 문제가 표시된 그래프의 섹션을 선택합니다. 선택 범위는 길이가 최대 3초입니다. 더 길면 시작 부분부터 잘립니다.

   ![진단 세션 창 스크린샷](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. 선택 범위의 자세한 타임라인을 보려면 보고서 아래 부분에 있는 **해당 범위의 GPU 사용량을 자세히 보려면 여기를 클릭...** 메시지에서 **세부 정보 보기** 링크를 선택합니다.

   ![범위가 선택된 진단 세션 창의 스크린샷](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

이 선택 영역을 선택하면 보고서가 포함된 새 탭 문서가 열립니다. GPU 사용량 보고서를 사용하면 CPU에서 그래픽 이벤트가 시작된 시간, 이벤트가 GPU에 도착한 시간, GPU가 실행하는 데 걸린 시간 등을 확인할 수 있습니다. 이러한 정보는 병목 현상 및 코드 병렬 처리를 개선해야 할 부분 등을 식별하는 데 도움이 됩니다.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>GPUView 또는 Windows Performance Analyzer로 내보내기

Visual Studio 2017부터 [GPUView](/windows-hardware/drivers/display/using-gpuview) 및 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)를 사용하여 이 데이터를 열 수 있습니다. 진단 세션의 오른쪽 아래 모서리에 있는 **GpuView에서 열기** 또는 **WPA에서 열기** 링크를 선택하기만 하면 됩니다.

![링크가 강조 표시된 진단 세션 창의 스크린샷](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>GPU 사용량 보고서 사용

GPU 사용량 보고서의 윗부분에는 CPU 처리 작업, GPU 렌더링 작업 및 GPU 복사 작업에 대한 타임라인이 표시됩니다. 이러한 타임라인은 디스플레이의 vsync를 나타내는 연회색 세로 막대로 나뉩니다. 이 막대의 빈도는 GPU 사용량 데이터를 수집하는 디스플레이 중 하나(**디스플레이** 드롭다운 목록을 사용하여 선택)의 새로 고침 빈도와 일치합니다.

디스플레이의 새로 고침 빈도가 앱의 성능 목표보다 높을 수 있으므로, vsync와 앱에서 달성할 프레임 속도가 1:1의 관계가 되지 않을 수 있습니다. 성능 목표를 충족하기 위해 앱은 모든 처리를 완료하고, 렌더링을 수행하고, 대상 프레임 속도에서 `Present()`를 호출해야 합니다. 그러나 렌더링된 프레임은 `Present()` 후 다음 vsync까지 표시되지 않습니다.

GPU 사용량 보고서의 하단에는 보고서 기간 동안 발생한 그래픽 이벤트가 나열됩니다. 이벤트를 선택하면 관련 타임라인에서 해당 이벤트에 마커가 표시됩니다. 일반적으로 CPU 스레드의 이벤트가 하나의 API 호출을 표시하는 반면 GPU 타임라인 중 하나의 다른 이벤트는 GPU가 작업을 완료하는 시기를 표시합니다. 마찬가지로, 타임라인에서 이벤트를 선택하면 보고서에서는 보고서 하단에서 해당하는 그래픽 이벤트를 강조 표시합니다.

보고서의 상단에서 타임라인이 축소되면 시간이 가장 많이 걸리는 이벤트만 표시됩니다. 기간이 더 짧은 이벤트를 보려면 Ctrl 키를 누른 채로 포인팅 디바이스의 휠을 움직이거나 상단 패널의 왼쪽 아래 모서리에 있는 크기 조정 컨트롤을 사용하여 타임라인을 확대합니다. 타임라인 패널의 콘텐츠를 끌어 기록된 이벤트를 이동할 수도 있습니다.

원하는 항목을 찾을 수 있도록 프로세스 이름, 스레드 ID 및 이벤트 이름에 따라 GPU 사용량 보고서를 필터링합니다. vysnc 선을 결정하는 디스플레이 새로 고침 빈도를 선택할 수도 있습니다. 앱에서 [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) 인터페이스를 사용하여 렌더링 명령을 그룹화하는 경우 이벤트를 계층적으로 정렬할 수 있습니다.

 자세한 내용은 다음과 같습니다.

|필터 컨트롤|설명|
|--------------------|-----------------|
|**Process**|관심 있는 프로세스의 이름입니다. 진단 세션 도중에 GPU를 사용한 모든 프로세스가 이 드롭다운 목록에 포함됩니다. 이 프로세스와 연결된 색은 타임라인에 나오는 스레드 작업의 색입니다.|
|**스레드**|관심 있는 스레드 ID입니다. 다중 스레드 앱에서 이 정보를 사용하면 관심 있는 프로세스에 속한 특정 스레드를 격리시킬 수 있습니다. 선택한 스레드와 관련 있는 이벤트는 각 타임라인에서 강조 표시됩니다.|
|**표시**|새로 고침 빈도가 표시되는 디스플레이의 번호입니다. 일부 드라이버는 여러 개의 실제 디스플레이를 하나의 대형 가상 디스플레이로 표현되도록 구성할 수 있습니다. 컴퓨터에 여러 디스플레이가 연결되었더라도 목록에 디스플레이가 하나만 표시될 수 있습니다.|
|**필터**|관심 있는 키워드입니다. 보고서 하단에 나오는 이벤트에는 키워드 전체 또는 일부와 일치하는 이벤트만 포함됩니다. 여러 키워드를 세미콜론(;)으로 구분하여 지정할 수 있습니다.|
|**계층 정렬**|사용자 표식을 통해 정의된 이벤트 계층 구조를 유지하는지 아니면 무시하는지 나타내는 확인란입니다.|

GPU 사용량 보고서 하단에 있는 이벤트 목록에는 각 이벤트의 세부 정보가 표시됩니다.

|Column|설명|
|------------|-----------------|
|**이벤트 이름**|그래픽 이벤트의 이름입니다. 이벤트는 일반적으로 CPU 스레드 타임라인의 이벤트 및 GPU 타임라인 이벤트에 해당합니다. 이벤트 이름은 GPU 사용량에서 이벤트의 이름을 확인할 수 없는 경우 이벤트 이름은 *unattributed*가 될 수 있습니다. 자세한 내용은 이 표 다음에 나오는 참고 사항을 참조하세요.|
|**CPU 시작(ns)**|Direct3D API 호출을 통해 이벤트가 CPU에서 시작된 시간입니다. 이 시간은 앱이 시작된 시간을 기준으로 나노초 단위로 측정됩니다.|
|**GPU 시작(ns)**|이벤트가 GPU에서 시작된 시간입니다. 이 시간은 앱이 시작된 시간을 기준으로 나노초 단위로 측정됩니다.|
|**GPU 지속 시간(ns)**|GPU에서 이벤트가 완료되는 데 걸린 시간(나노초 단위)입니다.|
|**프로세스 이름**|이벤트가 발생한 앱의 이름입니다.|
|**스레드 ID**|이벤트가 발생한 스레드 ID입니다.|

> [!IMPORTANT]
> GPU 또는 드라이버가 필수 계측 기능을 지원하지 않는 경우 모든 이벤트는 *unattributed*로 표시됩니다. 이 문제가 발생하는 경우 GPU 드라이버를 업데이트한 후 다시 시도해 봅니다. 자세한 내용은 이 문서의 끝에 있는 [하드웨어 및 드라이버 지원](#hwsupport)을 참조하세요.

## <a name="gpu-usage-settings"></a>GPU 사용량 설정

앱이 시작되자마자 정보 수집을 시작하는 대신 프로파일링 정보 수집을 연기하도록 GPU 사용량 도구를 구성할 수 있습니다. 프로파일링 정보의 크기가 상당히 클 수 있으므로, 이 작업은 앱 성능 저하가 당분간 나타나지 않을 것임을 알고 있는 경우에 유용합니다.

앱 시작 이후 프로파일링을 연기하려면

1. 주 메뉴에서 **디버그** > **성능 및 진단**을 선택합니다(또는 키보드에서 Alt+F2 키를 누름).

2. **성능 및 진단** 허브에서 **GPU 사용량** 옆에 있는 **설정** 링크를 선택합니다.

3. **일반** 속성 페이지의 **GPU 프로파일링 구성** 아래에서 **앱 시작 시 프로파일링 시작** 확인란의 선택을 취소하여 프로파일링을 연기합니다.

   ![수집 옵션을 보여 주는 개체 속성 페이지의 스크린샷](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> 지금은 Direct3D 12 앱에 대한 프로파일링을 연기할 수 없습니다.

GPU 사용량 도구에서 앱을 실행하면 GPU 사용량 도구 창 하단에서 추가 링크를 사용할 수 있습니다. 프로파일링 정보 수집을 시작하려면 **자세한 GPU 사용량 데이터를 추가로 수집하기 시작합니다.** 메시지에서 **시작** 링크를 선택합니다.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> 하드웨어 및 드라이버 지원

지원되는 GPU 하드웨어 및 드라이버는 다음과 같습니다.

|Vendor|GPU 설명|필요한 드라이버 버전|
|------------|---------------------|-----------------------------|
|Intel®|4세대 Intel® Core Processors(‘Haswell’)<br /><br /> -   Intel® HD Graphics(GT1)<br />-   Intel® HD Graphics 4200(GT2)<br />-   Intel® HD Graphics 4400(GT2)<br />-   Intel® HD Graphics 4600(GT2)<br />-   Intel® HD Graphics P4600(GT2)<br />-   Intel® HD Graphics P4700(GT2)<br />-   Intel® HD Graphics 5000(GT3)<br />-   Intel® Iris™ Graphics 5100(GT3)<br />-   Intel® Iris™ Pro Graphics 5200(GT3e)|(최신 드라이버 사용)|
|AMD®|AMD Radeon™ HD 7000 시리즈 이후 대부분(AMD Radeon™ HD 7350-7670 제외)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU 및 AMD FirePro GPU 가속기 - Graphics Core Next(GCN) 아키텍처<br /><br /> AMD® E 시리즈 및 AMD A 시리즈 Accelerated Processing Unit(APU) - Graphics Core Next(GCN) 아키텍처(‘Kaveri’, ‘Kabini’, ‘Temash’, ‘Beema’, ‘Mullins’) 포함|14.7 RC3 이상|
|NVIDIA®|NVIDIA® GeForce® 400 시리즈 이후 대부분<br /><br /> NVIDIA® GeForce® GPUs, NVIDIA Quadro® GPU 및 NVIDIA® Tesla™ GPU 가속기 - Fermi™, Kepler™ 또는 Maxwell™ 아키텍처|343.37 이상|

 NVIDIA® SLI™ 및 AMD Crossfire™ 등의 다중 GPU 구성은 현재 지원되지 않습니다. NVIDIA® Optimus™ 및 AMD Enduro™ 등의 하이브리드 그래픽 설정이 지원됩니다.
