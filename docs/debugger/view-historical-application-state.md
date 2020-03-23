---
title: IntelliTrace를 사용하여 이전 앱 상태 보기
description: 스냅샷 만들기 및 IntelliTrace 뒤로 이동으로 스냅샷을 보는 방법을 알아봅니다
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83d444cb5e3345d79ca6e1422982c0ecd37e4287
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67825521"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Visual Studio(Visual Studio Enterprise)에서 IntelliTrace 뒤로 이동을 사용하여 이전 앱 상태 검사

IntelliTrace 뒤로 이동은 모든 중단점 및 디버거 단계 이벤트에서 애플리케이션의 스냅샷을 자동으로 생성합니다. 기록된 스냅샷을 통해 이전 중단점 또는 단계로 돌아가서 애플리케이션의 과거 상태를 볼 수 있습니다. IntelliTrace 뒤로 이동을 사용하면 이전 애플리케이션 상태를 보고 싶지만 디버깅을 다시 시작하거나 원하는 앱 상태를 다시 만들지 않으려는 경우에 시간을 절약할 수 있습니다.

IntelliTrace 뒤로 이동은 Visual Studio Enterprise 2017 버전 15.5 이상부터 제공되며 Windows 10 1주년 업데이트 이상이 필요합니다. 기능은 현재 ASP.NET, WinForms, WPF, 관리 콘솔 앱 및 관리 클래스 라이브러리 디버깅에 지원됩니다. Visual Studio 2017 Enterprise 버전 15.7부터 ASP.NET Core 및 .NET Core에도 기능이 지원됩니다. Visual Studio 2017 Enterprise 버전 15.9 미리 보기 2부터 Windows를 대상으로 하는 네이티브 앱에도 기능이 지원됩니다. UWP 애플리케이션 디버깅은 현재 지원되지 않습니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * IntelliTrace 이벤트 및 스냅샷 사용
> * 뒤로 이동 및 앞으로 이동 명령을 사용하여 이벤트 이동
> * 이벤트 스냅샷 보기

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>IntelliTrace 이벤트 및 스냅샷 모드를 사용하도록 설정

1. Visual Studio Enterprise에서 프로젝트를 엽니다.

1. **도구** > **옵션** > **IntelliTrace**설정을 열고, 옵션 **IntelliTrace 이벤트 및 스냅샷**을 선택합니다.

    Visual Studio 2017 Enterprise 버전 15.9 미리 보기 2부터 이 옵션은 **IntelliTrace 스냅샷(관리 및 네이티브)** 입니다.

    ![IntelliTrace 이벤트 및 스냅샷 모드를 사용하도록 설정](../debugger/media/intellitrace-enable-snapshots.png "IntelliTrace 이벤트 및 스냅샷 모드를 사용하도록 설정")

1. 예외에서 스냅샷 보기에 대한 옵션을 구성하려는 경우 **옵션** 대화 상자에서 **IntelliTrace** > **고급**을 선택합니다.

    이러한 옵션은 Visual Studio 2017 Enterprise 버전 15.7부터 사용할 수 있습니다.

    ![예외에서 스냅샷에 대한 동작 구성](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    이벤트 및 스냅샷을 활성화하는 경우 예외에서 스냅샷 만들기 또한 기본적으로 활성화됩니다. **예외 이벤트에 대한 스냅샷 수집**을 선택 해제하여 예외에서 스냅샷을 비활성화할 수 있습니다. 이 기능이 활성화된 경우 처리되지 않은 예외에 대한 스냅샷이 만들어집니다. 처리되는 예외의 경우 예외가 throw되고 이전에 throw된 예외의 다시 throw가 아닌 경우에만 스냅샷이 만들어집니다. 드롭다운 목록에서 값을 선택하여 예외에서 최대 스냅샷 수를 설정할 수 있습니다. 최대는 앱이 중단 모드를 시작할 때마다 적용됩니다(예: 앱이 중단점에 도달하는 경우).

    > [!NOTE]
    > 스냅샷은 IntelliTrace가 기록하는 예외 이벤트에 대해서만 만들어집니다. 관리 코드의 경우 **도구** > **옵션** > **IntelliTrace 이벤트**를 선택하여 IntelliTrace가 기록하는 이벤트를 지정할 수 있습니다.

1. 프로젝트에서 하나 이상의 중단점을 설정하고 디버깅을 시작하거나(**F5** 키 누름), 코드를 한 단계씩 실행하여 디버깅을 시작합니다(**F10** 또는 **F11**).

    IntelliTrace는 각 디버거 단계, 중단점 이벤트 및 처리되지 않은 예외 이벤트에서 애플리케이션 프로세스의 스냅샷을 만듭니다. 이러한 이벤트는 다른 IntelliTrace 이벤트와 함께 **진단 도구** 창의 **이벤트** 탭에 기록됩니다. 이 창을 열려면 **디버그** > **Windows** > **진단 도구 표시**를 선택합니다.

    카메라 아이콘이 스냅샷을 사용할 수 있는 이벤트 옆에 나타납니다.

    ![스냅샷이 있는 이벤트 탭](../debugger/media/intellitrace-events-tab-with-snapshots.png "중단점 및 단계에 대한 스냅샷이 있는 이벤트 탭")

    성능상의 이유로 단계를 매우 신속하게 실행할 때 스냅샷이 생성되지 않습니다. 카메라 아이콘이 단계 옆에 표시되지 않으면 더 느리게 단계를 실행합니다.

## <a name="navigate-and-view-snapshots"></a>스냅샷 이동 및 보기

1. 디버그 도구 모음의 **뒤로 이동(Alt + [)** 과 **앞으로 이동(Alt + ])** 단추를 사용하여 이벤트 간을 이동합니다.

    이러한 단추는 **진단 도구 창**의 **이벤트** 탭에 나타나는 이벤트를 이동합니다. 이벤트의 앞이나 뒤로 이동하면 선택한 이벤트에 대한 [기록 디버깅](../debugger/historical-debugging.md)이 자동으로 활성화됩니다.

    ![뒤로 이동 및 앞으로 이동 단추](../debugger/media/intellitrace-step-back-icons-description.png "뒤로 이동 및 앞으로 이동 단추")

    뒤로 이동하거나 앞으로 이동할 때 Visual Studio는 기록 디버깅 모드를 시작합니다. 이 모드에서 디버거의 컨텍스트가 선택한 이벤트가 기록된 시간으로 전환됩니다. 또한 Visual Studio는 소스 창에서 해당 코드 줄로 포인터를 이동합니다.

    이 보기의 **호출 스택**, **로컬**, **자동** 및 **조사식** 창에서 값을 검사할 수 있습니다. 변수를 마우스로 가리켜 DataTips를 보고 **즉시 실행** 창에서 식 평가를 수행할 수도 있습니다. 표시되는 데이터는 해당 시점에 수행된 애플리케이션 프로세스 스냅샷의 데이터입니다.

    따라서 예를 들어 중단점에 도달하고 단계를 수행한 경우(**F10**) **뒤로 이동** 단추는 중단점에 해당하는 코드 줄의 기록 모드에 Visual Studio를 배치합니다.

    ![스냅샷을 사용하여 이벤트에 대한 기록 모드 활성화](../debugger/media/intellitrace-historical-mode-with-snapshot.png "스냅샷을 사용하여 이벤트에 대한 기록 모드 활성화")

2. 라이브 실행으로 돌아가려면 **계속(F5)** 을 선택하거나 정보 표시줄의 **라이브 디버깅으로 돌아가기** 링크를 클릭합니다.

3. **이벤트** 탭에서 스냅샷을 볼 수도 있습니다. 이렇게 하려면 스냅샷이 있는 이벤트를 선택하고 **기록 디버깅 활성화**를 클릭합니다.

    ![이벤트에 대한 기록 디버깅 활성화](../debugger/media/intellitrace-activate-historical-debugging.png "이벤트에 대한 기록 디버깅 활성화")

    **다음 명령문 설정** 명령과 달리 스냅샷을 보는 것은 코드를 다시 실행하지 않습니다. 이전에 발생한 시점에서 애플리케이션의 상태에 대한 정적 보기를 제공합니다.

    ![IntelliTrace 뒤로 이동 개요](../debugger/media/intellitrace-step-back-overview.png "IntelliTrace 뒤로 이동 개요")

    Visual Studio에서 변수를 검사하는 방법에 대해 자세히 알아보려면 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="frequently-asked-questions"></a>질문과 대답

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>IntelliTrace 뒤로 이동은 IntelliTrace 이벤트 전용 모드와 어떻게 다른가요?

이벤트 전용 모드의 IntelliTrace를 통해 디버거 단계 및 중단점에서 기록 디버깅을 활성화할 수 있습니다. 그러나 IntelliTrace는 창이 열려 있는 경우 **로컬** 및 **자동** 창에서만 데이터를 캡처하고, 보기에서 확장된 데이터만 캡처합니다. 이벤트 전용 모드에서 종종 변수 및 복잡한 개체의 전체 보기가 없는 경우가 많습니다. 또한 **조사식** 창에서 식 평가 및 데이터 보기는 지원되지 않습니다.

이벤트 및 스냅샷 모드에서 IntelliTrace는 복잡한 개체를 포함하여 애플리케이션 프로세스의 전체 스냅샷을 캡처합니다. 코드 줄에서 중단점에서 중지된 것처럼 동일한 정보를 볼 수 있습니다(또한 이전에 정보를 확장했는지 여부는 중요하지 않음). 스냅샷을 볼 때 식 평가도 지원됩니다.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>이 기능의 성능 영향은 무엇인가요? 

전체 단계별 실행 성능에 미치는 영향은 애플리케이션에 따라 달라집니다. 스냅샷을 만드는 오버헤드는 약 30ms입니다. 스냅샷이 만들어질 때 앱의 프로세스가 포크되고 포크된 복사본이 일시 중단됩니다. 스냅샷을 볼 때 Visual Studio는 프로세스의 포크된 복사본에 연결됩니다. 각 스냅샷의 경우 Visual Studio는 페이지 테이블만 복사하고 페이지를 쓰기 중 복사로 설정합니다. 힙의 개체가 연결된 스냅샷이 있는 디버거 단계 사이로 변경되는 경우 해당 페이지 테이블이 복사되고 최소 메모리 비용이 듭니다. Visual Studio에서 스냅샷을 만들 충분한 메모리가 없는 것을 감지하면 스냅샷을 만들지 않습니다.

## <a name="known-issues"></a>알려진 문제
* Windows 10 가을 크리에이터 업데이트(RS3) 이전의 Windows 버전에서 IntelliTrace 이벤트 및 스냅샷 모드를 사용하고, 애플리케이션의 디버그 플랫폼 대상이 x86으로 설정된 경우 IntelliTrace는 스냅샷을 만들지 않습니다.

    해결 방법:
  * Windows 10 1주년 업데이트(RS1) 및 버전 10.0.14393.2273 이하인 경우 [KB4103720을 설치합니다](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Windows 10 크리에이터 업데이트(RS2) 및 버전 10.0.15063.1112 이하인 경우 [KB4103722를 설치합니다](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Windows 10 가을 크리에이터 업데이트(RS3)로 설치 또는 업그레이드합니다.
  * 또는:
    1. Visual Studio 설치 관리자에서 데스크톱(x86, x64) 구성 요소용 VC++ 2015.3 v140 도구 집합을 설치합니다.
    2. 대상 애플리케이션을 빌드합니다.
    3. 명령줄에서 editbin 도구를 사용하여 대상 실행 파일에 대한 `Largeaddressaware` 플래그를 설정합니다. 예를 들어 경로를 업데이트한 후 다음 명령을 사용할 수 있습니다. "C:\Program Files(x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
    4. 디버깅을 시작하려면 **F5** 키를 누릅니다. 이제 디버거 단계 및 중단점에서 스냅샷이 만들어집니다.

       > [!Note]
       > 실행 파일이 변경 사항으로 다시 빌드될 때마다 `Largeaddressaware` 플래그를 설정해야 합니다.

* 애플리케이션 프로세스의 스냅샷이 지속형 메모리 매핑된 파일을 사용하는 애플리케이션에서 만들어지는 경우 스냅샷이 있는 프로세스는 메모리 매핑된 파일에서 단독 잠금을 보유합니다(부모 프로세스가 해당 잠금을 해제한 후에도). 다른 프로세스를 여전히 읽을 수 있지만 메모리 매핑된 파일에 쓸 수 없습니다.

  해결 방법:
  * 디버깅 세션을 종료하여 모든 스냅샷을 지웁니다.

* 해당 프로세스에 많은 수의 고유 메모리 영역이 있는 애플리케이션을 디버깅할 때(예: 많은 수의 DLL을 로드하는 애플리케이션) 활성화된 스냅샷이 있는 단계별 실행 성능은 영향을 받을 수 있습니다. 이 문제는 Windows의 향후 버전에서 수정될 예정입니다. 이 문제가 발생하는 경우 stepback@microsoft.com으로 문의하세요.

* 이벤트 및 스냅샷 모드에서 **디버그 &gt; IntelliTrace &gt; IntelliTrace 세션 저장**을 사용하여 파일을 저장할 때 스냅샷에서 캡처된 추가 데이터를 .itrace 파일에서 사용할 수 없습니다. 중단점 및 단계 이벤트에서 IntelliTrace 이벤트 전용 모드에서 파일을 저장한 것처럼 동일한 정보가 표시됩니다.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 IntelliTrace 뒤로 이동을 사용하는 방법을 알아보았습니다. 다른 IntelliTrace 기능에 자세히 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [IntelliTrace 기능](../debugger/intellitrace-features.md)
