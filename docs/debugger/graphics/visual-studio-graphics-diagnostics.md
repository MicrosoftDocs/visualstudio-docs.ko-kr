---
title: 그래픽 진단 | Microsoft Docs
description: Visual Studio 그래픽 진단은 Direct3D 작업을 기록하고 분석하기 위한 도구 집합입니다. 렌더링 및 성능 문제를 해결하는 데 사용합니다.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40b5a8eed74c4ce216e35c391833dcae80fc7efa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994045"
---
# <a name="visual-studio-graphics-diagnostics"></a>Visual Studio 그래픽 진단
>[!NOTE]
> Visual Studio는 DirectX 12 게임용으로 Windows의 PIX를 권장합니다. [Windows의 PIX](https://aka.ms/PIXonWindows)는 DirectX 12를 완전히 지원하는 성능 조정 및 디버깅 도구입니다. [자세한 정보를 확인](visual-studio-graphics-diagnostics-directx-12.md)하거나 [여기서 다운로드](https://aka.ms/downloadPIX)하세요.

Visual Studio *그래픽 진단* 은 Direct3D 앱의 렌더링 및 성능 문제를 기록한 다음, 분석하기 위한 도구 집합입니다. Windows PC에서 로컬로 실행 중이거나 Windows 디바이스 에뮬레이터 또는 원격 PC나 디바이스에서 실행 중인 앱에서 그래픽 진단을 사용할 수 있습니다.

 그래픽 진단 워크플로에서는 동작을 즉시 분석, 공유 또는 나중에 저장할 수 있도록 먼저 앱이 Direct3D를 사용하는 방법(라이브, 실행 시)에 대한 기록을 캡처합니다. 캡처 세션은 Visual Studio에서 수동으로 또는 캡처 명령줄 도구 **dxcap.exe** 를 사용하여 시작 및 제어할 수 있습니다. 그래픽 진단 캡처 API를 사용하여 프로그래밍 방식으로 캡처 세션을 시작 및 제어할 수도 있습니다.

 캡처 세션이 기록된 후에 Visual Studio *Graphics Analyzer* 에서 언제든지 해당 내용을 재생하고 앱이 사용한 것과 동일한 리소스 및 렌더링 명령을 사용하여 캡처된 프레임을 다시 만들 수 있습니다. 그런 다음, Graphics Analyzer 창에 제공된 도구를 사용하여 캡처된 프레임을 자세히 분석할 수 있습니다. 이러한 도구는 Direct3D API 호출, 리소스, 파이프라인 상태 개체, 파이프라인 단계 또는 캡처된 프레임의 픽셀에 대한 전체 기록을 검사하는 데 사용할 수 있습니다. 이러한 도구를 함께 사용하면 캡처된 프레임에 표시되는 방식부터 시작해서 앱 소스 코드, 셰이더 또는 그래픽 자산의 근본 원인으로 드릴다운하여 렌더링 문제를 직관적으로 탐색할 수 있습니다.

 성능 문제를 진단하려면 *프레임 분석* 도구를 사용하여 캡처된 프레임을 분석할 수 있습니다. 이 도구는 앱이 Direct3D를 사용하는 방식을 자동으로 변경하고 모든 변형을 벤치마킹하여 잠재적인 성능 최적화를 탐색합니다. 이전에는 단순히 차이를 만드는 변경을 찾기 위해 이러한 종류의 변경을 수동으로 수행하고 벤치마킹했을 수 있습니다. 프레임 분석을 사용하면 이미 효과를 알고 있는 변경을 수행하기만 하면 됩니다.

 그래픽 진단은 그래픽이 많은 Direct3D 앱의 모양과 실행을 최적화하는 데 도움이 됩니다.

 [개요](overview-of-visual-studio-graphics-diagnostics.md)로 이동하여 Visual Studio 그래픽 진단에서 제공하는 기능에 대해 자세히 알아보세요.

## <a name="in-this-section"></a>섹션 내용
 [개요 ](overview-of-visual-studio-graphics-diagnostics.md) - 그래픽 진단 워크플로 및 도구에 대해 소개합니다.

 [시작](getting-started-with-visual-studio-graphics-diagnostics.md) - 이 섹션에서는 Visual Studio 그래픽 진단을 설치하는 방법 및 Direct3D 앱과 함께 그래픽 진단을 사용하는 방법을 알아봅니다.

 [그래픽 정보 캡처](capturing-graphics-information.md) - 그래픽 진단을 사용하여 앱의 렌더링 문제를 검사하려면 먼저 앱에서 DirectX를 사용하는 방식에 대한 정보를 기록합니다. 기록 세션 중에는 정상적으로 앱이 실행될 때 관심 있는 프레임을 *캡처*, 즉 선택합니다. 캡처에는 프레임이 렌더링되는 방법에 대한 자세한 정보가 포함됩니다. 나중에 검사하거나 팀의 다른 멤버와 공유할 수 있도록 캡처한 정보를 그래픽 로그 문서로 저장할 수 있습니다.

 [GPU 사용량](../../profiling/gpu-usage.md) - 그래픽 진단을 사용하여 앱을 프로파일링하려면 GPU 사용량 도구를 사용합니다. GPU 사용량을 CPU 사용량 등의 기타 프로파일링 도구와 함께 사용하여 앱의 성능 문제에 영향을 줄 수 있는 CPU 및 GPU 작업을 상호 연결할 수 있습니다.

 [그래픽 로그 문서](graphics-log-document.md) - 기록된 그래픽 로그 검사를 시작하려면 그래픽 로그 문서 창에서 캡처된 프레임 또는 특정 픽셀을 선택합니다. 그러면 영향을 미친 ‘이벤트’(즉 DirectX API 호출)를 자세히 검사할 수 있습니다.

 [프레임 분석](graphics-frame-analysis.md) - 프레임을 선택한 후에는 그래픽 프레임 분석을 사용하여 렌더링 성능을 검사 및 조정합니다.

 [이벤트 목록](graphics-event-list.md) - 프레임을 선택한 후에는 **그래픽 이벤트** 목록을 사용하여 이벤트를 검사해 해당 이벤트가 렌더링 문제와 관련이 있는지 확인합니다.

 [상태](graphics-state.md) - 상태 창은 현재 이벤트 시간에 활성화된 그래픽 상태를 이해하는 데 도움이 됩니다.

 [파이프라인 단계](graphics-pipeline-stages.md) - **그래픽 파이프라인 단계** 창에서는 그래픽 파이프라인의 각 단계에서 현재 선택한 이벤트를 처리하는 방식을 조사합니다. 그러면 렌더링 문제가 처음으로 나타난 부분을 파악할 수 있습니다. 잘못된 변형으로 인해 개체가 나타나지 않는 경우 또는 단계 중 하나에서 다음 단계에서 예상하는 것과 일치하지 않는 출력을 생성하는 경우 파이프라인 단계 검사가 특히 유용합니다.

 [이벤트 호출 스택](graphics-event-call-stack.md) - **그래픽 이벤트 호출 스택** 을 사용하여 현재 선택한 이벤트의 호출 스택을 검사합니다. 그러면 렌더링 문제와 관련이 있는 앱 코드로 이동할 수 있습니다.

 [픽셀 기록](graphics-pixel-history.md) - **그래픽 픽셀 기록** 창을 사용하여 현재 선택한 픽셀이 자신에게 영향을 준 이벤트의 영향을 어떻게 받았는지 분석합니다. 그러면 특정 종류의 렌더링 문제를 일으킨 이벤트 또는 이벤트 조합을 파악할 수 있습니다. 픽셀 셰이더 출력이 잘못되었거나 프레임 버퍼와 잘못 결합되어서 개체가 잘못 렌더링된 경우 또는 픽셀이 프레임 버퍼에 도달하기 전에 버려져 개체가 나타나지 못한 경우 픽셀 기록은 특히 유용합니다.

 [개체 테이블](graphics-object-table.md) - **그래픽 개체 테이블** 을 사용하여 현재 선택한 이벤트에 대해 적용 중인 특정 Direct3D 개체 및 리소스의 속성과 콘텐츠를 검사합니다. 개체 테이블을 사용하면 이벤트 중 활성 상태인 그래픽 디바이스 컨텍스트를 확인하고 상수 버퍼, 꼭짓점 버퍼 및 질감과 같은 그래픽 리소스의 콘텐츠를 검사할 수 있습니다.

 [HLSL 디버거](hlsl-shader-debugger.md) - 현재 선택한 이벤트와 그래픽 파이프라인 단계의 셰이더 코드가 작동하는 방식을 검사하려면 **HLSL 디버거** 를 사용하여 코드를 단계별로 실행하고 변수의 내용을 검토하며 일반적인 다른 디버깅 작업을 수행합니다. 그래픽 파이프라인이 결과를 추가로 처리하는지 또는 앱에서 결과를 다시 읽는지와 상관없이 HLSL 디버거를 사용하여 컴퓨팅 셰이더 코드를 검사할 수 있습니다.

 [명령줄 캡처 도구](command-line-capture-tool.md) - 명령줄 캡처 도구를 통해 Visual Studio 또는 프로그래밍 방식 캡처 기능을 사용하지 않고도 그래픽 정보를 빠르게 캡처하고 재생할 수 있습니다. 특히 자동화 수행 시 또는 테스트 환경에서 명령줄 캡처 도구를 사용할 수 있습니다.

 [예제](graphics-diagnostics-examples.md) - 여러 예제가 그래픽 진단 도구를 함께 사용하여 다양한 종류의 렌더링 문제를 진단하는 방법을 보여 줍니다.

## <a name="related-sections"></a>관련 단원

| 제목 | 설명 |
| - | - |
| [디버거 기능 둘러보기](../debugger-feature-tour.md) | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 디버깅 기능에 대해 소개합니다. |
| [DirectX 그래픽 및 게임](/windows/win32/directx) | DirectX 그래픽 기술에 대해 설명하는 문서를 제공합니다. |
| [Visual Studio의 DirectX 12 지원](visual-studio-graphics-diagnostics-directx-12.md) | Visual Studio의 DirectX 12 지원 알아보기 |
