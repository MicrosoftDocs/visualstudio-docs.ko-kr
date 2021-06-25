---
title: Visual Studio Extenders에 대한 Per-Monitor 인식 지원
titleSuffix: ''
description: Visual Studio 2019에서 사용할 수 있는 모니터별 인식에 대한 새로운 Extender 지원에 대해 알아봅니다.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902048"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio Extenders에 대한 Per-Monitor 인식 지원

2019년 Visual Studio 이전 버전에서는 해당 DPI 인식 컨텍스트가 PMA(모니터별 DPI 인식)가 아닌 시스템 인식으로 설정되었습니다. 시스템 인식에서 실행하면 Visual Studio 다양한 배율로 모니터를 렌더링하거나 다른 디스플레이 구성(예: 다른 Windows 크기 조정)을 사용하여 컴퓨터에 원격으로 렌더링해야 할 때마다 시각적 환경(예: 흐리게 글꼴 또는 아이콘)이 저하되었습니다.

Visual Studio 2019의 DPI 인식 컨텍스트는 환경에서 지원하는 경우 PMA로 설정되며, 단일 시스템 정의 구성이 아닌 호스트되는 디스플레이의 구성에 따라 Visual Studio 렌더링할 수 있습니다. 궁극적으로 PMA 모드를 지원하는 표면 영역에 대해 항상 깔끔한 UI로 변환합니다.

이 문서에서 다루는 용어 및 전체 시나리오에 대한 자세한 내용은 [Windows에서 높은 DPI 데스크톱 애플리케이션 개발](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 설명서를 참조하세요.

## <a name="quickstart"></a>빠른 시작

- Visual Studio PMA 모드에서 실행 중인지 **확인합니다(PMA 사용** 참조).

- 일반적인 시나리오 집합에서 확장이 올바르게 작동하는지 **확인합니다(PMA 문제에 대한 확장 테스트** 참조).

- 문제가 발견되면 이 문서에 설명된 전략/권장 사항을 사용하여 해당 문제를 진단하고 해결할 수 있습니다. 또한 필요한 API에 액세스하려면 프로젝트에 새 [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 패키지를 추가해야 합니다.

## <a name="enable-pma"></a>PMA 사용

Visual Studio PMA를 사용하도록 설정하려면 다음 요구 사항을 충족해야 합니다.

- Windows 10 2018년 4월 업데이트(v1803, RS4) 이상
- .NET Framework 4.8 RTM 이상
- ["픽셀 밀도가 다른 화면에 대한 렌더링 최적화"](../../ide/reference/general-environment-options-dialog-box.md) 옵션이 설정된 Visual Studio 2019

이러한 요구 사항이 충족되면 Visual Studio 프로세스 전체에서 PMA 모드를 자동으로 사용하도록 설정합니다.

> [!NOTE]
> Visual Studio Windows Forms 콘텐츠(예: 속성 브라우저)는 Visual Studio 2019 버전 16.1 이상인 경우에만 PMA를 지원합니다.

## <a name="test-your-extensions-for-pma-issues"></a>PMA 문제에 대한 확장 테스트

Visual Studio WPF, Windows Forms, Win32 및 HTML/JS UI 프레임워크를 공식적으로 지원합니다. Visual Studio PMA 모드로 전환되면 각 UI 스택이 다르게 동작합니다. 따라서 UI 프레임워크에 관계없이 모든 UI가 PMA 모드를 준수하는지 확인하기 위해 테스트 통과를 수행하는 것이 좋습니다.

다음과 같은 일반적인 시나리오의 유효성을 검사하는 것이 좋습니다.

- 애플리케이션이 실행되는 동안 단일 모니터 환경의 배율 변경

  이 시나리오는 UI가 동적 Windows DPI 변경에 응답하고 있는지 테스트하는 데 도움이 됩니다.

- 연결된 모니터가 기본 모니터로 설정되고 연결된 모니터가 애플리케이션이 실행되는 동안 랩톱과 다른 배율 배율로 노트북을 도킹/도킹 해제합니다.

  이 시나리오는 UI가 디스플레이 DPI 변경에 응답하고 동적으로 추가 또는 제거되는 디스플레이를 처리하는지 테스트하는 데 도움이 됩니다.

- 서로 다른 배율 요소를 가진 여러 모니터를 가지고 애플리케이션을 이들 간에 이동합니다.

  이 시나리오는 UI가 디스플레이 DPI 변경에 응답하고 있는지 테스트하는 데 도움이 됩니다.
    
- 로컬 및 원격 컴퓨터에 기본 모니터에 대한 다른 배율 요소가 있는 경우 머신으로 원격 작업

  이 시나리오는 UI가 동적 Windows DPI 변경에 응답하고 있는지 테스트하는 데 도움이 됩니다.

UI에 문제가 있는지 여부에 대한 좋은 예비 테스트는 코드가 *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper,* *Microsoft.VisualStudio.PlatformUI.DpiHelper* 또는 *VsUI::CDpiHelper* 클래스를 활용하는지 여부입니다. 이러한 이전 DpiHelper 클래스는 시스템 DPI 인식만 지원하며 프로세스가 PMA인 경우 항상 제대로 작동하지는 않습니다.

이러한 DpiHelpers의 일반적인 사용법은 다음과 같습니다.

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

이전 예제에서 창의 논리적 범위를 나타내는 사각형은 디바이스 단위로 변환되므로 정확한 모니터 포인터를 반환하기 위해 디바이스 좌표를 예상하는 네이티브 메서드 MonitorFromPoint에 전달될 수 있습니다.

### <a name="classes-of-issues"></a>문제 클래스
VISUAL STUDIO PMA 모드를 사용하도록 설정하면 UI가 여러 가지 일반적인 방법으로 문제를 복제할 수 있습니다. 전부는 아니지만 대부분의 문제는 Visual Studio 지원되는 UI 프레임워크에서 발생할 수 있습니다. 또한 이러한 문제는 UI 부분이 혼합 모드 DPI 크기 조정 시나리오에서 호스트되는 경우에도 발생할 수 있습니다(자세한 내용은 Windows [설명서](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 참조). 

#### <a name="win32-window-creation"></a>Win32 창 만들기
CreateWindow() 또는 CreateWindowEx()를 사용하여 창을 만들 때 일반적인 패턴은 좌표(0,0)(기본 디스플레이의 왼쪽 위/왼쪽 모서리)에서 창을 만든 다음 최종 위치로 이동하는 것입니다. 그러나 이렇게 하면 창에서 DPI 변경된 메시지 또는 이벤트를 트리거할 수 있으며, 이로 인해 다른 UI 메시지 또는 이벤트를 다시 트리거하고 결국 원치 않는 동작 또는 렌더링이 발생할 수 있습니다.

#### <a name="wpf-element-placement"></a>WPF 요소 배치
이전 Microsoft.VisualStudio.Utilities.Dpi.DpiHelper를 사용하여 WPF 요소를 이동할 때 요소가 기본이 아닌 DPI에 있을 때마다 왼쪽 위 좌표가 올바르게 계산되지 않을 수 있습니다.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI 요소 크기 또는 위치의 serialization
UI 크기 또는 위치(디바이스 단위로 저장된 경우)가 저장된 것과 다른 DPI 컨텍스트에서 복원되면 위치가 잘못 배치되고 크기가 잘못 지정됩니다. 이는 디바이스 단위에 내재된 DPI 관계가 있기 때문에 발생합니다.

#### <a name="incorrect-scaling"></a>잘못된 크기 조정
기본 DPI에서 만든 UI 요소는 올바르게 크기 조정됩니다. 그러나 다른 DPI를 사용하여 디스플레이로 이동하면 크기가 조정되지 않고 콘텐츠가 너무 크거나 너무 작습니다.

#### <a name="incorrect-bounding"></a>잘못된 경계
크기 조정 문제와 마찬가지로 UI 요소는 기본 DPI 컨텍스트에서 범위를 올바르게 계산합니다. 그러나 기본이 아닌 DPI로 이동하면 새 범위를 올바르게 계산하지 않습니다. 따라서 콘텐츠 창이 호스팅 UI에 비해 너무 작거나 너무 커서 빈 공간 또는 클리핑이 발생합니다.

#### <a name="drag--drop"></a>끌어서 놓기 &
혼합 모드 DPI 시나리오(예: 서로 다른 DPI 인식 모드에서 렌더링하는 다른 UI 요소) 내의 경우 끌어서 놓기 좌표가 잘못 계산되어 최종 놓기 위치가 올바르지 않게 될 수 있습니다.

#### <a name="out-of-process-ui"></a>Out-of-process UI
일부 UI는 out-of-process로 생성되며, 외부 프로세스 만들기가 Visual Studio 다른 DPI 인식 모드에 있는 경우 이전 렌더링 문제가 발생할 수 있습니다.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>잘못 렌더링된 컨트롤, 이미지 또는 레이아웃 Windows Forms
모든 Windows Forms 콘텐츠가 PMA 모드를 지원하는 것은 아닙니다. 따라서 잘못된 레이아웃 또는 크기 조정으로 인해 렌더링 문제가 발생할 수 있습니다. 이 경우 가능한 해결 방법은 "시스템 인식" DpiAwarenessContext에서 Windows Forms 콘텐츠를 명시적으로 렌더링하는 [것입니다(특정 DpiAwarenessContext에 컨트롤 강제](#force-a-control-into-a-specific-dpiawarenesscontext)적용 참조).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms 컨트롤 또는 창이 표시되지 않음
이 문제의 주요 원인 중 하나는 하나의 DpiAwarenessContext가 있는 컨트롤 또는 창을 다른 DpiAwarenessContext가 있는 창으로 다시 구하려는 개발자입니다.

다음 이미지는 부모 창의 현재 **기본** Windows 운영 체제 제한을 보여줍니다.

![올바른 부모 동작의 스크린샷](media/PMA-parenting-behavior.PNG)

> [!Note]
> 스레드 호스팅 동작을 설정하여 이 동작을 변경할 수 [있습니다(Dpi_Hosting_Behavior 열거형](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)참조).

따라서 지원되지 않는 모드 간에 부모-자식 관계를 설정하면 실패하고 컨트롤 또는 창이 예상대로 렌더링되지 않을 수 있습니다.

### <a name="diagnose-issues"></a>문제 진단

PMA 관련 문제를 식별할 때 고려해야 할 많은 요소가 있습니다. 

- UI 또는 API에 논리적 또는 디바이스 값이 예상됩니까?
    - WPF UI 및 API는 일반적으로 논리 값을 사용합니다(항상 그렇지는 않음).
    - Win32 UI 및 API는 일반적으로 디바이스 값을 사용합니다.

- 값은 어디에서 오는가요?
    - 다른 UI 또는 API에서 값을 받는 경우 디바이스 또는 논리 값을 전달하는 것입니다.
    - 여러 소스에서 값을 수신하는 경우 모두 동일한 형식의 값을 사용/예상하거나 변환을 혼합하고 일치시켜야 합니까?

- UI 상수는 사용 중이며 어떤 형식인가요?

- 스레드가 수신하는 값에 대한 올바른 DPI 컨텍스트에 있나요?

  혼합 DPI 호스팅을 사용하도록 변경하면 일반적으로 코드 경로가 올바른 컨텍스트에 배치됩니다. 그러나 기본 메시지 루프 또는 이벤트 흐름 외부에서 수행된 작업은 잘못된 DPI 컨텍스트에서 실행될 수 있습니다.

- 값이 DPI 컨텍스트 경계를 넘나요?

  끌어서 놓기 & 좌표가 DPI 컨텍스트를 교차할 수 있는 일반적인 상황입니다. Window는 올바른 작업을 수행하려고 하지만 경우에 따라 호스트 UI는 컨텍스트 경계가 일치하도록 변환 작업을 수행해야 할 수 있습니다.

### <a name="pma-nuget-package"></a>PMA NuGet 패키지
새 DpiAwarness 라이브러리는 [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 패키지에서 찾을 수 있습니다.

### <a name="recommended-tools"></a>권장 도구
다음 도구는 Visual Studio 지원하는 일부 다른 UI 스택에서 PMA 관련 문제를 디버그하는 데 도움이 될 수 있습니다.

#### <a name="snoop"></a>스 눕
중단은 기본 제공 Visual Studio XAML 도구에 없는 몇 가지 추가 기능이 있는 XAML 디버깅 도구입니다. 또한 Visual Studio WPF UI를 보고 조정할 수 있도록 능동적으로 디버그할 필요가 없습니다. PmA 문제를 진단하는 데 사용할 수 있는 두 가지 주요 방법은 논리적 배치 좌표 또는 크기 범위의 유효성을 검사하고 UI에 올바른 DPI가 있는지 확인하는 것입니다.
 
#### <a name="visual-studio-xaml-tools"></a>XAML 도구 Visual Studio
이처럼 Visual Studio XAML 도구는 PMA 문제를 진단하는 데 도움이 될 수 있습니다. 가능한 원인이 발견되면 중단점을 설정하고 라이브 시각적 트리 창과 디버그 창을 사용하여 UI 범위 및 현재 DPI를 검사할 수 있습니다.

## <a name="strategies-for-fixing-pma-issues"></a>PMA 문제 해결 전략

### <a name="replace-dpihelper-calls"></a>DpiHelper 호출 바꾸기

대부분의 경우 PMA 모드에서 UI 문제를 해결하면 관리 코드의 호출을 이전 *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* 및 *Microsoft.VisualStudio.PlatformUI.DpiHelper* 클래스로 대체하고 새 *Microsoft.VisualStudio.Utilities.DpiAwareness* 도우미 클래스를 호출하는 것으로 요약됩니다. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

네이티브 코드의 경우 이전 *VsUI::CDpiHelper* 클래스에 대한 호출을 새 *VsUI::CDpiAwareness* 클래스에 대한 호출로 대체해야 합니다. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

새 DpiAwareness 및 CDpiAwareness 클래스는 DpiHelper 클래스와 동일한 단위 변환 도우미를 제공하지만 변환 작업에 대한 참조로 사용할 UI 요소인 추가 입력 매개 변수가 필요합니다. 이미지 크기 조정 도우미는 새 DpiAwareness/CDpiAwareness 도우미에 존재하지 않으며 필요한 경우 [ImageService를](../image-service-and-catalog.md) 대신 사용해야 합니다.

관리되는 DpiAwareness 클래스는 WPF 시각적 개체, Windows Forms 컨트롤 및 Win32 HWND 및 HMONITOR(IntPtrs 형식)에 대한 도우미를 제공하는 반면 네이티브 CDpiAwareness 클래스는 HWND 및 HMONITOR 도우미를 제공합니다.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>잘못된 DpiAwarenessContext에 표시되는 대화 상자, 창 또는 컨트롤 Windows Forms
다른 DpiAwarenessContexts를 가진 창의 성공적인 부모가 된 후에도(Windows 기본 동작으로 인해) DpiAwarenessContexts가 다른 창의 크기가 다르게 조정됨에 따라 크기 조정 문제가 계속 나타날 수 있습니다. 따라서 사용자는 UI에서 맞춤/흐린 텍스트 또는 이미지 문제를 볼 수 있습니다.

솔루션은 애플리케이션의 모든 창 및 컨트롤에 대해 올바른 DpiAwarenessContext 범위를 설정하는 것입니다.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>TLMM(최상위 혼합 모드) 대화 상자
모달 대화 상자와 같은 최상위 창을 만들 때 창(및 핸들)을 만들기 전에 스레드가 올바른 상태인지 확인해야 합니다. 네이티브의 CDpiScope 도우미 또는 관리되는 DpiAwareness.EnterDpiScope 도우미를 사용하여 스레드를 시스템 인식에 배치할 수 있습니다. (TLMM은 일반적으로 비 WPF 대화 상자/창에서 사용해야 합니다.)

### <a name="child-level-mixed-mode-clmm"></a>자식 수준 혼합 모드(CLMM)
기본적으로 자식 창은 부모 없이 만든 경우 현재 스레드 DPI 인식 컨텍스트를 받거나 부모로 만들 때 부모의 DPI 인식 컨텍스트를 받습니다. 부모가 아닌 다른 DPI 인식 컨텍스트를 사용하여 자식을 만들려면 스레드를 원하는 DPI 인식 컨텍스트에 배치할 수 있습니다. 그런 다음 부모 없이 자식 을 만들고 부모 창에 수동으로 다시 부모로 만들 수 있습니다.

#### <a name="clmm-issues"></a>CLMM 문제
기본 메시징 루프 또는 이벤트 체인의 일부로 발생하는 대부분의 UI 계산 작업은 올바른 DPI 인식 컨텍스트에서 이미 실행되고 있어야 합니다. 그러나 좌표 또는 크기 조정 계산이 이러한 주요 워크플로 외부에서 수행되는 경우(예: 유휴 시간 작업 중 또는 UI 스레드에서) 현재 DPI 인식 컨텍스트가 잘못되어 UI가 잘못되거나 크기가 잘못될 수 있습니다. 스레드를 UI 작업의 올바른 상태로 두면 일반적으로 문제가 해결되었습니다.
 
#### <a name="opt-out-of-clmm"></a>CLMM 옵트아웃
WPF가 아닌 도구 창이 PMA를 완전히 지원하도록 마이그레이션되는 경우 CLMM을 옵트아웃해야 합니다. 이렇게 하려면 새 인터페이스 IVsDpiAware를 구현해야 합니다.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

관리되는 언어의 경우 이 인터페이스를 구현하는 가장 좋은 위치는 *Microsoft.VisualStudio.Shell.ToolWindowPane* 에서 파생되는 동일한 클래스에 있습니다. C++의 경우 이 인터페이스를 구현하는 가장 좋은 위치는 vsshell.h에서 *IVsWindowPane을* 구현하는 동일한 클래스에 있습니다.

인터페이스의 Mode 속성에서 반환되는 값은 __VSDPIMODE(관리되는 경우 uint로 캐스팅)입니다.

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- 인식할 수 없음은 도구 창에서 96 DPI를 처리해야 하며 Windows에서 다른 모든 DPI에 대한 크기 조정을 처리한다는 것을 의미합니다. 콘텐츠가 약간 흐려집니다.
- 시스템은 도구 창이 기본 디스플레이 DPI에 대한 DPI를 처리해야 한다는 것을 의미합니다. 일치하는 DPI가 있는 모든 디스플레이는 선명하게 보이지만, 세션 중에 DPI가 다르거나 변경되면 Windows에서 크기 조정을 처리하고 약간 흐리게 표시됩니다.
- PerMonitor는 도구 창이 모든 디스플레이 및 DPI가 변경 될 때마다 모든 DPI를 처리해야 한다는 것을 의미합니다.

> [!NOTE]
> Visual Studio PerMonitorV2 인식만 지원하므로 PerMonitor 열거형 값은 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 Windows 값으로 변환됩니다.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>특정 DpiAwarenessContext에 컨트롤 강제

PMA 모드를 지원하도록 업데이트되지 않는 레거시 UI는 VISUAL STUDIO PMA 모드에서 실행되는 동안에도 약간의 조정이 필요할 수 있습니다. 이러한 수정 중 하나는 UI가 올바른 DpiAwarenessContext에 생성되고 있는지 확인하는 것입니다. UI를 특정 DpiAwarenessContext로 강제 전환하려면 다음 코드를 사용하여 DPI 범위를 입력하면 됩니다.

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> DpiAwarenessContext 강제 강제는 비 WPF UI 및 최상위 WPF 대화 상자에서만 작동합니다. 도구 창 또는 디자이너 내에서 호스트될 WPF UI를 만들 때 콘텐츠가 WPF UI 트리에 삽입되는 즉시 현재 프로세스 DpiAwarenessContext로 변환됩니다.

## <a name="known-issues"></a>알려진 문제

### <a name="windows-forms"></a>Windows Forms

새로운 혼합 모드 시나리오에 최적화하기 위해 Windows Forms 부모가 명시적으로 설정되지 않을 때마다 컨트롤과 창을 만드는 방법을 변경했습니다. 이전에는 명시적 부모가 없는 컨트롤이 생성되는 컨트롤 또는 창에 대한 임시 부모로 내부 "공간 창"을 사용했습니다. 

.NET 4.8 이전에는 창 생성 시 현재 스레드 DPI 인식 컨텍스트에서 DpiAwarenessContext를 얻는 단일 "창"이 있었습니다. 부모 없는 컨트롤은 컨트롤의 핸들을 만들 때 공간 창과 동일한 DpiAwarenessContext를 상속하며 애플리케이션 개발자가 최종/예상 부모로 다시 부모가 됩니다. 이로 인해 "공간 창"에 최종 부모 창보다 더 높은 DpiAwarenessContext가 있는 경우 타이밍 기반 오류가 발생합니다.

.NET 4.8부터 이제 발생한 모든 DpiAwarenessContext에 대한 "공간 창"이 있습니다. 다른 주요 차이점은 컨트롤에 사용되는 DpiAwarenessContext는 핸들이 만들어질 때가 아니라 컨트롤을 만들 때 캐시된다는 것입니다. 즉, 전체 종료 동작은 동일하지만 타이밍 기반 문제였던 것을 일관된 문제로 전환할 수 있습니다. 또한 애플리케이션 개발자가 UI 코드를 작성하고 올바르게 범위 지정하기 위한 보다 결정적인 동작을 제공합니다.
