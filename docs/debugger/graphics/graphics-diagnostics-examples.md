---
title: 그래픽 진단 예제 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4df2fafb523d04a8ec222b10e1ac9ed3aa95454d
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187924"
---
# <a name="graphics-diagnostics-examples"></a>그래픽 진단 예제
다음 예제에서는 DirectX 기반 앱에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그래픽 진단을 사용하여 렌더링 문제를 디버깅하는 방법을 보여줍니다.

## <a name="capturing-graphics-information"></a>그래픽 정보 캡처
 그래픽 진단을 사용하여 앱에서 렌더링 문제를 진단하기 전에 앱 실행 중 앱에서 그래픽 정보를 캡처해야 합니다. 그래픽 정보는 로컬로 실행 중인 앱 또는 원격 컴퓨터 또는 다른 디바이스에서 실행 중인 앱에서 캡처할 수 있습니다. 다음 연습에서는 앱에서 수동으로 또는 프로그래밍 방식으로 그래픽 정보를 캡처할 수 있는 방법을 보여줍니다.

- [연습: 그래픽 정보 캡처](walkthrough-capturing-graphics-information.md)

- [연습: 프로그래밍 방식으로 그래픽 정보 캡처](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>ARM 기반 디바이스에서 그래픽 진단 사용
 그래픽 진단을 사용하면 원격 디버깅을 사용하여 ARM 기반 디바이스에서 Direct3D 앱을 디버깅할 수 있습니다. 자세한 내용은 [방법: ARM 디바이스에서 그래픽 진단 사용](graphics-diagnostics-examples.md)을 참조하세요.

## <a name="playing-back-graphics-information"></a>그래픽 정보 재생
 실행 중인 앱에서 그래픽 정보를 캡처한 다음 캡처된 이벤트를 재생하여 렌더링 문제를 진단할 수 있습니다. 재생하기 위해 개발 컴퓨터를 사용하거나 연결된 원격 컴퓨터 또는 디바이스를 사용할 수 있습니다. 자세한 내용은 [방법: 그래픽 진단 재생 머신 변경](how-to-change-the-graphics-diagnostics-playback-machine.md)을 참조하세요.

## <a name="debugging-missing-objects"></a>누락된 개체 디버깅
 누락된 개체는 그래픽 개발자가 경험할 수 있는 가장 일반적인 렌더링 문제 중 하나입니다. 여러 가지 다른 종류의 오류로 인해 개체가 명백히 사라질 수 있으므로 이러한 종류의 문제는 진단하기 어려울 수 있습니다. 개체 누락에 대한 일반적인 원인에는 잘못 구성된 디바이스 상태, 개체의 기하 도형 변형 문제 또는 잘못 구성된 그래픽 파이프라인이 포함됩니다.

 다음 시나리오에서는 그래픽 진단을 사용하여 개체가 누락된 이유를 확인하고 해당 코드를 찾는 방법을 보여줍니다.

- [연습: 디바이스 상태로 인해 누락된 개체](walkthrough-missing-objects-due-to-device-state.md)

- [연습: 꼭짓점 음영으로 인해 누락된 개체](walkthrough-missing-objects-due-to-vertex-shading.md)

- [연습: 잘못 구성된 파이프라인으로 인해 누락된 개체](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>렌더링 오류 디버깅
 모양이 올바르지 않은 개체(또는 개체)는 그래픽 개발자가 경험할 수 있는 또 다른 일반적인 문제입니다. 이러한 종류의 문제는 잘못된 모양으로 인해 진단이 어려울 수 있습니다. 잘못된 모양과 그 원인은 잘못된 질감 바인딩처럼 매우 명확한 원인에서부터 셰이더 코드의 버그 또는 셰이더 간 예기치 않은 상호 작용과 같이 매우 미묘한 원인에 이르기까지 다양할 수 있습니다. 일부 문제는 여러 오류가 결합하여 발생할 수 있습니다.

 다음은 그래픽 진단을 사용하여 사소한 셰이더 버그로 인해 발생한 그다지 미묘하지 않은 렌더링 문제를 추적하는 방법을 보여줍니다.

- [연습: 음영으로 인한 렌더링 오류 디버그](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>컴퓨팅 셰이더 디버깅
 그래픽 진단을 사용하여 잘못된 결과를 생성한 DirectCompute 계산 셰이더 커널을 디버깅할 수 있습니다. DirectCompute를 사용하면 GPU의 계산 능력을 사용하여 많은 수의 데이터 요소를 함께 계산할 수 있습니다. 일부 문제의 경우 GPU를 활용하면 잘 최적화된 CPU 코드보다 몇 배나 더 빠르게 수행할 수 있습니다. 그러나 기존 디버거는 GPU에서 실행되는 코드를 감지할 수 없습니다. 이런 종류의 코드 디버깅에는 일반적으로 공급업체별 특수 도구가 필요하지만 이러한 도구는 Visual Studio와 잘 통합되지 못할 수 있습니다. GPU 범위 전체에서 보다 일관성 있는 계산 셰이더 디버깅을 수행하기 위해 그래픽 진단에서는 Direct3D 렌더링 이벤트 이외에 DirectCompute Dispatch 이벤트를 캡처합니다. 따라서 친숙한 도구를 사용하여 계산 셰이더 코드의 문제를 디버깅할 수 있습니다.

 계산 셰이더의 버그로 인해 발생하는 시뮬레이션 문제를 디버그하는 방법을 보여 주는 시나리오는 [연습: 그래픽 진단을 사용하여 계산 셰이더 디버그](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)를 참조하세요.