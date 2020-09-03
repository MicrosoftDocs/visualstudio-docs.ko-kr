---
title: Visual Studio extender에 대 한 모니터 당 인식 지원
titleSuffix: ''
description: Visual Studio 2019에서 제공 되는 모니터 당 인식에 대 한 새로운 extender 지원에 대해 알아봅니다.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69585378"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio extender에 대 한 모니터 당 인식 지원

Visual Studio 2019 이전 버전에서는 모니터 당 DPI 인식 (PMA)이 아니라 DPI 인식 컨텍스트가 시스템 인식으로 설정 되었습니다. 시스템 인식에서를 실행 하면 Visual Studio에서 다양 한 크기 조정 요소를 사용 하는 모니터에서 렌더링 하거나 다양 한 디스플레이 구성 (예: 다양 한 창 크기 조정)을 사용 하는 컴퓨터에 원격으로 렌더링 해야 할 때마다 시각적 환경 (예: 흐리게 표시)이 저하 됩니다.

Visual Studio 2019의 DPI 인식 컨텍스트는 환경에서 지원할 때 PMA로 설정 되며, 단일 시스템 정의 구성이 아니라 호스팅된 디스플레이의 구성에 따라 Visual Studio를 렌더링할 수 있습니다. 궁극적으로 PMA 모드를 지 원하는 노출 영역에 대해 항상 선명한 UI로 변환 합니다.

이 문서에서 다루는 용어 및 전체 시나리오에 대 한 자세한 내용은 [Windows에서 DPI 데스크톱 응용 프로그램 개발](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 설명서를 참조 하세요.

## <a name="quickstart"></a>빠른 시작

- Visual Studio가 PMA 모드에서 실행 되 고 있는지 확인 합니다 ( **Pma 사용**참조).

- 일반적인 시나리오 집합에서 확장이 제대로 작동 하는지 확인 합니다 ( **PMA 문제에 대 한 확장 테스트**참조).

- 문제가 발견 되 면이 문서에 설명 된 전략/권장 사항을 사용 하 여 문제를 진단 하 고 해결할 수 있습니다. 또한 필요한 Api에 액세스 하려면 프로젝트에 새 [VisualStudio](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 패키지를 추가 해야 합니다.

## <a name="enable-pma"></a>PMA 사용

Visual Studio에서 PMA를 사용 하도록 설정 하려면 다음 요구 사항을 충족 해야 합니다.

- Windows 10 4 월 2018 업데이트 (v1803, RS4) 이상
- .NET Framework 4.8 RTM 이상
- Visual Studio 2019 ( [픽셀 밀도가 다른 화면에 대 한 렌더링 최적화)](../../ide/reference/general-environment-options-dialog-box.md) 옵션 사용

이러한 요구 사항이 충족 되 면 Visual Studio는 프로세스 전체에서 PMA 모드를 자동으로 사용 하도록 설정 합니다.

> [!NOTE]
> Visual Studio (예: 속성 브라우저)의 Windows Forms 콘텐츠는 Visual Studio 2019 버전 16.1 이상이 있는 경우에만 PMA를 지원 합니다.

## <a name="test-your-extensions-for-pma-issues"></a>PMA 문제에 대 한 확장 테스트

Visual Studio는 WPF, Windows Forms, Win32 및 HTML/JS UI 프레임 워크를 공식적으로 지원 합니다. Visual Studio를 PMA 모드로 전환 하면 각 UI 스택이 다르게 동작 합니다. 따라서 UI 프레임 워크에 관계 없이 모든 UI가 PMA 모드를 준수 하는지 확인 하기 위해 테스트 통과를 수행 하는 것이 좋습니다.

다음과 같은 일반적인 시나리오를 확인 하는 것이 좋습니다.

- 응용 프로그램이 실행 되는 동안 단일 모니터 환경의 크기 조정 인수 변경

  이 시나리오는 UI가 동적 Windows DPI 변경에 응답 하는지 테스트 하는 데 도움이 됩니다.

- 연결 된 모니터가 주 복제본으로 설정 되 고 연결 된 모니터가 응용 프로그램이 실행 되는 동안 노트북과 다른 배율 인수를 가진 노트북을 도킹/도킹 해제 합니다.

  이 시나리오는 UI가 디스플레이 DPI 변경에 응답 하 고, 동적으로 추가 또는 제거 되는 디스플레이를 처리 하는 것을 테스트 하는 데 도움이 됩니다.

- 여러 가지 크기 조정 요소를 포함 하는 여러 모니터가 있고 그 사이에 응용 프로그램을 이동 하는 경우

  이 시나리오는 UI가 디스플레이 DPI 변경에 응답 하는지 테스트 하는 데 도움이 됩니다.
    
- 로컬 및 원격 컴퓨터가 기본 모니터에 대해 서로 다른 크기 조정 요소를 사용할 때 컴퓨터에 원격으로 로그인 합니다.

  이 시나리오는 UI가 동적 Windows DPI 변경에 응답 하는지 테스트 하는 데 도움이 됩니다.

UI가 문제를 발생 시킬 수 있는지에 대 한 적절 한 예비 테스트는 코드에서 *VisualStudio*를 활용 하는지, *VisualStudio*를 활용 하는지, 아니면 *Vsui:: cdpihelper* 클래스를 활용 하는지 여부입니다. 이러한 이전 DpiHelper 클래스는 시스템 DPI 인식만 지원 하며, 프로세스가 PMA 인 경우에는 항상 올바르게 작동 하지 않습니다.

이러한 DpiHelpers 일반적인 사용법은 다음과 같습니다.

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

이전 예제에서 창의 논리적 경계를 나타내는 사각형은 장치 단위로 변환 되어 정확한 모니터 포인터를 다시 반환 하기 위해 장치 좌표가 필요한 기본 메서드 MonitorFromPoint에 전달 될 수 있습니다.

### <a name="classes-of-issues"></a>문제의 클래스
Visual Studio에 대해 PMA 모드를 사용 하도록 설정 하면 UI에서 여러 가지 일반적인 방법으로 문제를 복제할 수 있습니다. 대부분의 경우 이러한 문제는 Visual Studio의 지원 되는 UI 프레임 워크에서 발생할 수 있습니다. 또한 이러한 문제는 UI 부분이 혼합 모드 DPI 배율 시나리오에서 호스트 되는 경우에도 발생할 수 있습니다. 자세한 내용은 Windows [설명서](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) 를 참조 하십시오. 

#### <a name="win32-window-creation"></a>Win32 창 만들기
CreateWindow () 또는 CreateWindowEx ()를 사용 하 여 창을 만들 때 일반적인 패턴은 좌표 (0, 0) (기본 표시의 위쪽/왼쪽 모퉁이)에서 창을 만든 다음 최종 위치로 이동 하는 것입니다. 그러나 이렇게 하면 창이 DPI 변경 메시지나 이벤트를 다시 트리거할 다른 UI 메시지나 이벤트를 발생 시킬 수 있으며 결국 원치 않는 동작이 나 렌더링 될 수 있습니다.

#### <a name="wpf-element-placement"></a>WPF 요소 배치
이전 VisualStudio를 사용 하 여 WPF 요소를 이동할 때 요소가 기본이 아닌 DPI에 있을 때마다 왼쪽 위 좌표를 올바르게 계산 하지 못할 수 있습니다.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI 요소 크기 또는 위치 Serialization
UI 크기나 위치 (장치 단위로 저장 된 경우)가에 저장 된 것과 다른 DPI 컨텍스트에서 복원 되는 경우에는 위치 지정 되 고 크기가 잘못 지정 됩니다. 이는 장치 단위에 내재 된 DPI 관계가 있기 때문에 발생 합니다.

#### <a name="incorrect-scaling"></a>잘못 된 크기 조정
기본 DPI에 생성 된 UI 요소는 올바르게 크기를 조정 하지만, DPI가 다른 디스플레이로 이동 하는 경우에는 크기를 조정 하지 않고 해당 콘텐츠가 너무 크거나 작습니다.

#### <a name="incorrect-bounding"></a>잘못 된 경계
크기 조정 문제와 마찬가지로 UI 요소는 주 DPI 컨텍스트에서 해당 범위를 올바르게 계산 하지만 주 DPI로 이동 하는 경우 새 범위를 올바르게 계산 하지 않습니다. 이와 같이 콘텐츠 창이 너무 작거나 너무 커서 호스팅 UI에 비해 빈 공간이 나 클리핑이 발생 합니다.

#### <a name="drag--drop"></a>끌어 놓기 &
혼합 모드 DPI 시나리오 (예: 다른 DPI 인식 모드에서 다양 한 UI 요소 렌더링)가 있을 때마다 끌어서 놓기 좌표는 miscalculated 될 수 있으며 결과적으로 최종 놓기 위치가 잘못 되었습니다.

#### <a name="out-of-process-ui"></a>Out-of-process UI
일부 UI는 out-of-process로 생성 되 고, 만들기 외부 프로세스가 Visual Studio와 다른 DPI 인식 모드에 있으면 이전 렌더링 문제가 발생할 수 있습니다.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>잘못 렌더링 된 Windows Forms 컨트롤, 이미지 또는 레이아웃
모든 Windows Forms 콘텐츠가 PMA 모드를 지원 하지는 않습니다. 따라서 잘못 된 레이아웃이 나 크기 조정으로 렌더링 문제가 발생할 수 있습니다. 이 경우 가능한 해결 방법은 "시스템 인식" DpiAwarenessContext Windows Forms 콘텐츠를 명시적으로 렌더링 하는 것입니다 ( [컨트롤을 특정 DpiAwarenessContext로 강제 적용](#force-a-control-into-a-specific-dpiawarenesscontext)참조).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms 컨트롤 또는 창 표시 안 함
이 문제에 대 한 주요 원인 중 하나는 한 DpiAwarenessContext 있는 컨트롤이 나 창의 부모를 다른 DpiAwarenessContext가 있는 창으로 재지정 하는 것입니다.

다음 이미지는 windows를 부모로 하는 현재 **기본** windows 운영 체제 제한을 보여 줍니다.

![올바른 부모로 동작의 스크린샷](media/PMA-parenting-behavior.PNG)

> [!Note]
> 스레드 호스팅 동작을 설정 하 여이 동작을 변경할 수 있습니다 ( [Dpi_Hosting_Behavior 열거형](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)참조).

따라서 지원 되지 않는 모드 간에 부모-자식 관계를 설정 하는 경우 실패 하 고 컨트롤이 나 창이 예상 대로 렌더링 되지 않을 수 있습니다.

### <a name="diagnose-issues"></a>문제 진단

PMA 관련 문제를 식별 하는 경우 고려해 야 할 여러 요인이 있습니다. 

- UI 또는 API가 논리적 또는 장치 값을 필요로 하나요?
    - WPF UI 및 Api는 일반적으로 논리적 값을 사용 하지만 항상 그렇지는 않습니다.
    - Win32 UI 및 Api는 일반적으로 장치 값을 사용 합니다.

- 값은 어디에 있나요?
    - 다른 UI 또는 API에서 값을 받는 경우는 장치 또는 논리 값을 전달 하는 것입니다.
    - 여러 소스에서 값을 받는 경우에는 모두 동일한 유형의 값을 사용/요구 하거나 변환을 혼합 하 고 일치 시켜야 하나요?

- UI 상수를 사용 하 고 있는 것은 무엇 인가요?

- 수신 하는 값에 대 한 올바른 DPI 컨텍스트의 스레드 입니까?

  혼합 DPI 호스팅을 사용 하도록 변경 하는 경우 일반적으로 올바른 컨텍스트에 코드 경로를 넣어야 하지만 주 메시지 루프 외부에서 수행 된 작업이 나 이벤트 흐름이 잘못 된 DPI 컨텍스트에서 실행 될 수 있습니다.

- DPI 컨텍스트 경계를 교차 하는 값이 있나요?

  끌어서 & drop은 좌표가 DPI 컨텍스트를 교차 시킬 수 있는 일반적인 상황입니다. 창에서 올바른 작업을 시도 하지만 경우에 따라 호스트 UI에서 변환 작업을 수행 하 여 일치 하는 컨텍스트 경계를 확인 해야 할 수도 있습니다.

### <a name="pma-nuget-package"></a>PMA NuGet 패키지
새 DpiAwarness 라이브러리는 [VisualStudio](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet 패키지에서 찾을 수 있습니다.

### <a name="recommended-tools"></a>권장 도구
다음 도구를 통해 Visual Studio에서 지 원하는 여러 가지 UI 스택에서 PMA 관련 문제를 디버그할 수 있습니다.

#### <a name="snoop"></a>스 눕
스 눕는 기본 제공 Visual Studio XAML 도구에 없는 몇 가지 추가 기능을 포함 하는 XAML 디버깅 도구입니다. 또한 스 눕는 WPF UI를 보고 수정할 수 있도록 Visual Studio를 적극적으로 디버그할 필요가 없습니다. 스 눕 두 가지 주요 방법은 논리적 배치 좌표 또는 크기 범위를 확인 하 고 UI의 유효성을 검사 하는 데 적합 한 DPI를 확인 하는 데 유용할 수 있습니다.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML 도구
스 눕와 마찬가지로 Visual Studio의 XAML 도구를 통해 PMA 문제를 진단할 수 있습니다. 오류가 발견 되 면 중단점을 설정 하 고 라이브 시각적 트리 창 뿐만 아니라 디버그 창을 사용 하 여 UI 범위 및 현재 DPI를 검사할 수 있습니다.

## <a name="strategies-for-fixing-pma-issues"></a>PMA 문제를 해결 하기 위한 전략

### <a name="replace-dpihelper-calls"></a>DpiHelper 호출 바꾸기

대부분의 경우 PMA 모드에서 UI 문제를 수정 하면 관리 코드의 호출을 구축으로 대체 하 여 새 *VisualStudio* 클래스에 대 한 호출을 사용 하 여 관리 코드의 호출을 이전 *VisualStudio* 및 *VisualStudio* 로 바꿀 수 있습니다. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

네이티브 코드의 경우 이전 Vsui:: *CDpiHelper* 클래스에 대 한 호출을 새 *Vsui:: cdpihelper* class에 대 한 호출로 바꾸는 것이 적절 합니다. 

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

새 DpiAwareness 및 CDpiAwareness 클래스는 Dpiawareness 클래스와 동일한 단위 변환 도우미를 제공 하지만 추가 입력 매개 변수 (변환 작업에 대 한 참조로 사용할 UI 요소)를 요구 합니다. 새 DpiAwareness/CDpiAwareness 도우미에는 이미지 크기 조정 도우미가 없으며 필요한 경우 [ImageService](../image-service-and-catalog.md) 를 대신 사용 해야 합니다.

관리 되는 DpiAwareness class는 WPF 시각적 개체, Windows Forms 컨트롤 및 Win32 Hwnd 및 HMONITORs (둘 다 IntPtrs 형식)에 대 한 도우미를 제공 하지만, 네이티브 CDpiAwareness 클래스는 HWND 및 HMONITORS 도우미를 제공 합니다.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>잘못 된 DpiAwarenessContext에 표시 되는 대화 상자, 창 또는 컨트롤 Windows Forms
Windows 기본 동작 때문에 다른 DpiAwarenessContexts를 사용 하 여 windows를 성공적으로 부모로 한 후에도 사용자는 다른 DpiAwarenessContexts 크기 조정을 사용 하는 windows로 크기 조정 문제를 계속 볼 수 있습니다. 따라서 사용자는 UI에서 맞춤/흐린 텍스트 또는 이미지 문제를 볼 수 있습니다.

이 솔루션은 응용 프로그램의 모든 창 및 컨트롤에 대해 올바른 DpiAwarenessContext 범위를 설정 하는 것입니다.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>TLMM (최상위 혼합 모드) 대화 상자
모달 대화 상자와 같은 최상위 창을 만들 때 스레드가 창과 핸들을 생성 하기 전에 스레드가 올바른 상태에 있는지 확인 하는 것이 중요 합니다. 네이티브에서 Cdpis38helper를 사용 하 여 스레드를 시스템 인식으로 설정 하거나, 관리 되는에서 Cdpis38helper를 사용 하 여 스레드를 시스템 인식으로 전환할 수 있습니다. (일반적으로 TLMM은 비 WPF 대화 상자/창에서 사용 해야 합니다.)

### <a name="child-level-mixed-mode-clmm"></a>자식 수준 혼합 모드 (CLMM)
기본적으로 자식 창은 부모를 사용 하지 않고 만든 경우 현재 스레드 DPI 인식 컨텍스트를 수신 하거나 부모를 사용 하 여 만들 때 부모의 DPI 인식 컨텍스트를 수신 합니다. 부모와 다른 DPI 인식 컨텍스트를 사용 하 여 자식을 만들려면 원하는 DPI 인식 컨텍스트에 스레드를 추가할 수 있습니다. 그런 다음 부모를 사용 하지 않고 자식을 만들고 부모 창으로 수동으로 재지정 수 있습니다.

#### <a name="clmm-issues"></a>CLMM 문제
주 메시징 루프 또는 이벤트 체인의 일부로 발생 하는 대부분의 UI 계산 작업은 올바른 DPI 인식 컨텍스트에서 이미 실행 되 고 있어야 합니다. 그러나 이러한 주 워크플로 외부에서 좌표 또는 크기 조정 계산이 수행 된 경우 (예: 유휴 시간 작업 중 또는 UI 스레드 외부에서) 현재 DPI 인식 컨텍스트가 잘못 되어 UI 잘못 배치 또는 잘못 된 크기 조정 문제를 발생 시킬 수 있습니다. UI 작업에 대 한 올바른 상태에 스레드를 배치 하면 일반적으로 문제가 해결 됩니다.
 
#### <a name="opt-out-of-clmm"></a>CLMM 옵트아웃 (Opt out)
PMA를 완전히 지원 하기 위해 비 WPF 도구 창이 마이그레이션되는 경우에는 CLMM를 옵트아웃 해야 합니다. 이렇게 하려면 새 인터페이스를 구현 해야 합니다. IVsDpiAware 수 있습니다.

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

관리 되는 언어의 경우이 인터페이스를 구현 하는 가장 좋은 방법은 VisualStudio에서 파생 되는 동일한 클래스에 있는 것입니다. *ToolWindowPane*. C + +의 경우이 인터페이스를 구현 하는 가장 좋은 방법은 vsshell. h에서 *IVsWindowPane* 을 구현 하는 동일한 클래스에 있는 것입니다.

인터페이스에서 Mode 속성에 의해 반환 되는 값은 __VSDPIMODE (관리 되는의 uint로 캐스트)입니다.

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- 인식 하지 못하는 것은 도구 창이 96 DPI를 처리 해야 함을 의미 하며, Windows는 다른 모든 DPIs 크기 조정을 처리 합니다. 콘텐츠가 약간 희미 합니다.
- 시스템은 도구 창이 기본 디스플레이 DPI의 DPI를 처리 해야 함을 의미 합니다. DPI가 일치 하는 디스플레이는 선명 하 게 표시 되지만 DPI가 다르거나 세션 중에 변경 되는 경우 Windows는 크기 조정을 처리 하 고 약간 흐리게 표시 됩니다.
- PerMonitor는 모든 DPI가 변경 될 때마다 도구 창에서 모든 DPIs를 처리 해야 함을 의미 합니다.

> [!NOTE]
> Visual Studio는 PerMonitorV2 인식만 지원 하므로 PerMonitor 열거형 값은 DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2의 Windows 값으로 변환 됩니다.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>특정 DpiAwarenessContext 컨트롤을 강제로 적용 합니다.

PMA 모드를 지원 하도록 업데이트 되지 않은 레거시 UI에는 Visual Studio가 PMA 모드에서 실행 되는 동안 약간의 작업을 수행 해야 할 수 있습니다. 이러한 수정 사항 중 하나는 올바른 DpiAwarenessContext에서 UI를 만들고 있는지 확인 하는 것입니다. UI를 특정 DpiAwarenessContext 적용 하려면 다음 코드를 사용 하 여 DPI 범위를 입력할 수 있습니다.

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
> DpiAwarenessContext는 비 WPF UI 및 최상위 WPF 대화 상자 에서만 작동 합니다. 도구 창 또는 디자이너 내에서 호스팅될 WPF UI를 만들 때 콘텐츠가 WPF UI 트리에 삽입 되는 즉시 현재 프로세스 DpiAwarenessContext 변환 됩니다.

## <a name="known-issues"></a>알려진 문제

### <a name="windows-forms"></a>Windows Forms

새 혼합 모드 시나리오에 맞게 최적화 하기 위해 해당 부모를 명시적으로 설정 하지 않을 때마다 컨트롤과 창을 만드는 방법을 변경 Windows Forms. 이전에는 명시적 부모가 없는 컨트롤은 생성 되는 컨트롤이 나 창에 대 한 임시 부모로 내부 "파킹 창"을 사용 했습니다. 

.NET 4.8 이전에는 창의 만든 시간에 현재 스레드 DPI 인식 컨텍스트에서 DpiAwarenessContext를 가져오는 단일 "파킹 창"이 있었습니다. Unparented 컨트롤은 컨트롤의 핸들이 생성 될 때 파킹 창과 동일한 DpiAwarenessContext를 상속 하며 응용 프로그램 개발자가 최종/예상 부모에 재지정 합니다. 이렇게 하면 "파킹 기간"이 최종 부모 창 보다 더 높은 DpiAwarenessContext 때 타이밍 기반 오류가 발생 합니다.

.NET 4.8 현재 발생 한 모든 DpiAwarenessContext에 대해 "파킹 창"이 있습니다. 그 밖의 주요 차이점은 컨트롤을 만들 때 컨트롤에 사용 되는 DpiAwarenessContext는 핸들이 생성 될 때가 아니라 캐시 된다는 것입니다. 즉, 전반적인 end 동작은 동일 하지만, 타이밍 기반 문제에 사용 되는 항목을 일관 된 문제로 전환할 수 있습니다. 또한 응용 프로그램 개발자가 UI 코드를 작성 하 고 올바르게 범위를 지정 하는 더 결정적 동작을 제공 합니다.
