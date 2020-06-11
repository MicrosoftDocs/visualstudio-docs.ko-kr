---
title: 디버거 소개
description: Visual Studio 디버거를 사용하여 애플리케이션 디버깅 시작
ms.custom: ''
ms.date: 04/08/2019
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffaeff850c739cd81569a88ae980acf837c413c1
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184213"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>먼저 Visual Studio 디버거 살펴보기

이 항목에서는 Visual Studio에서 제공 하는 디버거 도구를 소개 합니다. Visual Studio 컨텍스트에서 *애플리케이션을 디버그*하는 경우는 일반적으로 디버거가 연결된 상태에서(즉 디버거 모두에서) 애플리케이션이 실행되고 있음을 의미합니다. 이렇게 하면 디버거는 실행되는 동안 코드에서 수행하는 작업을 확인할 수 있는 여러 가지 방법을 제공합니다. 코드를 단계별로 실행하고, 변수에 저장된 값을 살펴보고, 변수에 대한 조사식을 설정하여 값이 변경되는 경우를 확인하며, 코드의 실행 경로 등을 검사할 수 있습니다. 처음으로 코드를 디버그한 경우 이 항목를 계속 진행하기 전에 먼저 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)을 참조하는 것이 좋습니다.

여기에 설명된 기능은 C#, C++, Visual Basic, JavaScript 및 Visual Studio에서 지원하는 다른 언어(언급한 경우 제외)에 적용할 수 있습니다.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>중단점 설정 및 디버거 시작

디버그하려면 앱 프로세스에 연결된 디버거로 앱을 시작해야 합니다. **F5**(**디버그 > 디버깅 시작**)는 디버그 작업을 수행하는 가장 일반적인 방법입니다. 그러나 지금 앱 코드를 검사할 중단점을 설정하지 않았으므로 먼저 중단점을 설정한 다음, 디버깅을 시작합니다. 중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다.

코드 편집기에 파일이 열려 있는 경우 코드 줄의 왼쪽 여백을 클릭하여 중단점을 설정할 수 있습니다.

![중단점 설정](../debugger/media/dbg-tour-set-a-breakpoint.gif "중단점 설정")

**F5** 키(**디버그 > 디버깅 시작**) 또는 디버그 도구 모음에서 **디버깅 시작** 단추 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작")를 누르면 디버거에 발생되는 첫 번째 중단점에서 디버거가 실행됩니다. 앱이 아직 실행되고 있지 않으면 F5 키를 사용하여 디버거를 시작하고 첫 번째 중단점에서 중지합니다.

중단점은 자세히 검사하려는 코드 줄 또는 코드 섹션을 아는 경우 유용한 기능입니다.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a><a name="navigate"></a> 한 단계 실행 명령을 사용하여 디버거에서 코드 탐색

앱 코드를 더욱 빠르게 탐색할 수 있으므로 대부분의 명령에 대한 바로 가기 키를 제공합니다. (메뉴 명령과 같은 해당 명령이 괄호 안에 표시됩니다.)

디버거가 연결된 상태로 앱을 시작하려면 **F11**(**디버그 > 한 단계씩 코드 실행**)을 누릅니다. F11 키는 **한 단계씩 코드 실행** 명령으로서 한 번에 하나의 명령문씩 앱을 실행합니다. F11 키로 앱을 시작하는 경우 디버거는 실행되는 첫 번째 명령문에서 중단됩니다.

![F11 한 단계씩 코드 실행](../debugger/media/dbg-tour-f11.png "F11 한 단계씩 코드 실행")

노란색 화살표는 디버거가 일시 중지한 명령문을 나타내며, 동일한 지점에서 앱 실행을 일시 중단하기도 합니다(이 명령문은 아직 실행되지 않음).

F11 키는 실행 흐름을 가장 자세히 검사할 수 있는 좋은 방법입니다. (코드를 통해 더 빨리 이동하기 위해 몇 가지 다른 옵션도 표시합니다.) 기본적으로 디버거는 사용자 코드가 아닌 코드를 건너뜁니다(자세한 내용은 [내 코드만](../debugger/just-my-code.md)을 참조하세요).

>[!NOTE]
> 속성 및 연산자(기본 동작)를 자동으로 프로시저 단위로 실행하는 경우 알림을 받을 것인지 묻는 대화 상자가 관리 코드에 표시됩니다. 나중에 설정을 변경하려는 경우 **디버깅** 아래의 **도구 > 옵션** 메뉴에서 **속성 및 연산자를 프로시저 단위로 실행** 설정을 비활성화합니다.

## <a name="step-over-code-to-skip-functions"></a>함수를 건너뛰도록 코드를 프로시저 단위로 실행

함수 또는 메서드 호출인 코드 줄에 있는 경우 F11 키 대신에 **F10** 키(**디버그 > 프로시저 단위로 실행**)를 누를 수 있습니다.

F10 키는 앱 코드의 함수 또는 메서드를 한 단계씩 실행하지 않고 디버거를 진행합니다(코드는 계속 실행되고 있음). F10 키를 눌러 관심이 없는 코드를 건너뛸 수 있습니다. 이러한 방식으로 관심이 많은 코드에 빨리 다가갈 수 있습니다.

## <a name="step-into-a-property"></a>속성을 한 단계씩 코드 실행

앞서 설명한 대로 기본적으로 디버거는 관리되는 속성 및 필드를 건너뛰지만 **한 단계씩 코드 실행** 명령을 통해 이 동작을 재정의할 수 있습니다.

속성 또는 필드를 마우스 오른쪽 단추로 클릭하고 **한 단계씩 코드 실행**을 선택한 다음, 사용 가능한 옵션 중 하나를 선택합니다.

![한 단계씩 코드 실행](../debugger/media/dbg-tour-step-into-specific.png "한 단계씩 코드 실행")

이 예제에서 **한 단계씩 코드 실행**은 `Path.set`에 대한 코드로 안내합니다.

![한 단계씩 코드 실행](../debugger/media/dbg-tour-step-into-specific-2.png "한 단계씩 코드 실행")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>마우스를 사용하여 신속하게 코드의 지점까지 실행

디버거에서 **실행하려면 클릭**(여기까지 실행) 단추 ![실행하려면 클릭](../debugger/media/dbg-tour-run-to-click.png "RunToClick")가 왼쪽에 표시될 때까지 코드 줄 위로 마우스를 가져갑니다.

![실행하려면 클릭](../debugger/media/dbg-tour-run-to-click-2.png "실행하려면 클릭")

> [!NOTE]
> **실행하려면 클릭**(여기까지 실행) 단추는 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]부터 사용할 수 있습니다.

**실행하려면 클릭**(여기까지 실행) 단추를 클릭합니다. 디버거는 클릭한 코드 줄로 이동합니다.

이 단추 사용은 임시 중단점 설정과 비슷합니다. 이 명령은 앱 코드의 표시 지역 내에서 신속하게 살펴보는 데 유용합니다. 열려 있는 모든 파일에서 **실행하려면 클릭**을 사용할 수 있습니다.

## <a name="advance-the-debugger-out-of-the-current-function"></a>현재 함수에서 디버거 진행

경우에 따라 디버깅 세션을 계속 진행할 수 있지만 현재 함수까지 디버거를 진행하는 것이 좋습니다.

**Shift + F11** 키(또는 **디버그 > 프로시저 나가기**)를 누릅니다.

이 명령은 현재 함수가 반환될 때까지 앱 실행을 다시 시작하고 디버거를 진행시킵니다.

## <a name="run-to-cursor"></a>커서까지 실행

디버거에서 일시 중지되지 않고 코드를 편집하는 경우 앱의 코드 줄을 마우스 오른쪽 단추로 클릭하고 **커서까지 실행**을 선택합니다. 이 명령은 디버깅을 시작하고 현재의 코드 줄에서 임시 중단점을 설정합니다.

![커서까지 실행](../debugger/media/dbg-tour-run-to-cursor.png "커서까지 실행")

중단점을 설정한 경우 디버거는 적중하는 첫 번째 중단점에서 일시 중지됩니다.

**커서까지 실행**을 선택한 코드 줄에 도달할 때까지 **F5** 키를 누릅니다.

이 명령은 코드를 편집하고, 신속하게 임시 중단점을 설정하는 동시에 디버거를 시작하려는 경우에 유용합니다.

> [!NOTE]
> 디버깅 중에 **호출 스택** 창에서 **커서까지 실행**을 사용할 수 있습니다.

## <a name="restart-your-app-quickly"></a>앱을 빠르게 다시 시작

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "앱 다시 시작") 단추를 클릭합니다(**Ctrl+Shift+F5**).

**다시 시작**을 누르면 앱을 중지하고 디버거를 다시 시작하는 것에 비해 시간이 절약됩니다. 디버거가 코드를 실행하여 적중한 첫 번째 중단점에서 일시 중지합니다.

디버거를 중지하고 코드 편집기로 다시 돌아가려는 경우 **다시 시작** 대신 빨간색 중지 ![디버깅 중지](../debugger/media/dbg-tour-stop-debugging.png "디버그하는 동안 진단 도구 사용") 단추를 누를 수 있습니다.

## <a name="edit-your-code-and-continue-debugging-c-vb-c-xaml"></a>코드를 편집하고 디버깅 계속하기(C#, VB, C++, XAML)

Visual Studio에서 지원되는 대부분의 언어에서 디버깅 세션 중에 코드를 편집하고 디버깅을 계속할 수 있습니다. 이 기능을 사용하려면 디버거에서 일시 중지된 동안 커서를 사용하여 코드를 클릭하고 편집을 수행한 후 **F5**, **F10** 또는 **F11**을 눌러 디버깅을 계속합니다.

![디버깅 편집하며 계속하기](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

기능 사용 및 기능 제한에 대한 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

디버깅 세션 중 XAML 코드를 수정하려면 [XAML 핫 다시 로드를 사용하여 코드 작성 및 실행 중인 XAML 코드 디버그](../xaml-tools/xaml-hot-reload.md)를 참조하세요.

## <a name="inspect-variables-with-data-tips"></a>데이터 팁을 사용하여 변수 검사

이제 조금 익숙해졌으므로 디버거를 사용하여 앱 상태(변수) 검사를 시작하기에 좋은 시점입니다. 변수를 검사할 수 있는 기능은 디버거의 가장 유용한 기능 중 일부이며, 이를 수행하는 다양한 방법이 있습니다. 종종 문제를 디버그하려고 할 때 변수가 특정 앱 상태에 있다고 예상되는 값을 저장하는지 여부를 확인하려고 합니다.

디버거에서 일시 중지되는 동안 개체 위로 마우스를 가져가면 해당 기본 속성 값이 표시됩니다(이 예제에서 `market 031.jpg` 파일 이름은 기본 속성 값입니다).

![데이터 팁 보기](../debugger/media/dbg-tour-data-tips.gif "데이터 팁 보기")

개체를 확장하여 해당 모든 속성(이 예제의 `FullPath` 속성 같은)을 확인합니다.

디버그할 때 개체의 속성 값을 빨리 확인하려 하는 경우가 많으며, 데이터 팁은 이 작업을 수행하기에 좋은 방법입니다.

> [!TIP]
> 지원되는 언어 대부분에서 디버깅 세션 중에 코드를 편집할 수 있습니다. 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>자동 및 지역 창을 사용하여 변수 검사

디버깅하는 동안 코드 편집기의 맨 아래에 있는 **자동** 창을 살펴봅니다.

![자동 창](../debugger/media/dbg-tour-autos-window.png "자동 창")

**자동** 창에는 변수와 함께 해당 현재 값 및 형식이 표시됩니다. **자동** 창에서는 현재 줄 또는 이전 줄에 사용된 모든 변수를 표시합니다(C++의 창에는 이전 세 개의 코드 줄의 변수가 표시됩니다. 언어별 동작에 대한 설명서를 참조하세요).

> [!NOTE]
> JavaScript에는 **지역** 창이 지원되지만 **자동** 창은 지원되지 않습니다.

다음으로, **지역** 창을 살펴봅니다. **지역** 창에는 현재 범위에 있는 변수가 표시됩니다.

![지역 창](../debugger/media/dbg-tour-locals-window.png "지역 창")

이 예제에서는 `this` 개체 및 개체 `f`가 범위 안에 있습니다. 자세한 내용은 [자동 및 로컬 창에서 변수 검사](../debugger/autos-and-locals-windows.md)를 참조하세요.

## <a name="set-a-watch"></a>조사식 설정

**조사식** 창을 사용하여 주시하려는 변수(또는 식)를 지정할 수 있습니다.

디버깅하는 동안 개체를 마우스 오른쪽 단추로 클릭하고 **조사식 추가**를 선택합니다.

![조사식 창](../debugger/media/dbg-tour-watch-window.png "조사식 창")

이 예제에서 `f` 개체에 조사식을 설정하면 디버거를 통해 이동하면서 해당 값의 변화를 확인할 수 있습니다. 다른 변수 창과 달리 **조사식** 창에는 항상 주시하고 있는 변수가 표시됩니다(범위를 벗어나면 회색으로 표시됩니다).

자세한 내용은 [조사식 및 간략한 조사식 창을 사용하여 조사식 설정](../debugger/watch-and-quickwatch-windows.md) 참조

## <a name="examine-the-call-stack"></a>호출 스택 검사

디버깅하는 동안 **호출 스택** 창을 클릭합니다. 이 창은 기본적으로 오른쪽 아래의 창에서 열립니다.

![호출 스택 검사](../debugger/media/dbg-tour-call-stack.png "호출 스택 검사")

**호출 스택** 창에는 메서드와 함수가 호출되는 순서가 표시됩니다. 맨 위쪽의 줄에는 현재 함수(이 예제에서는 `Update` 메서드)가 표시됩니다. 두 번째 줄에는 `Update`가 `Path.set` 속성 등에서 호출되었음이 표시됩니다. 호출 스택은 앱의 실행 흐름을 검사하고 파악할 수 있는 좋은 방법입니다.

> [!NOTE]
> **호출 스택** 창은 Eclipse와 같은 일부 IDE의 디버그 관점과 비슷합니다.

코드 줄을 두 번 클릭하면 해당 소스 코드를 살펴보고 디버거에서 검사하고 있는 현재 범위를 변경할 수도 있습니다. 이렇게 하면 디버거가 진행되지 않습니다.

또한 **호출 스택** 창에서 오른쪽 클릭 메뉴를 사용하여 다른 작업을 수행할 수도 있습니다. 예를 들어 지정된 함수에 중단점을 삽입하고, **커서까지 실행**을 사용하여 앱을 다시 시작하고, 소스 코드를 검사할 수 있습니다. [방법: 호출 스택 검사](../debugger/how-to-use-the-call-stack-window.md)를 참조하세요.

## <a name="examine-an-exception"></a><a name="exception"></a> 예외 검사

앱에서 예외를 throw하는 경우 디버거는 예외를 throw한 코드 줄로 이동합니다.

![예외 도우미](../debugger/media/dbg-tour-exception-helper.png "예외 도우미")

이 예제에서는 **예외 도우미**에 경로가 올바른 형식이 아니라는 오류 메시지와 `System.Argument` 예외가 표시됩니다. 따라서 메서드 또는 함수 인수에서 오류가 발생한 것을 알 수 있습니다.

이 예제에서는 `DirectoryInfo` 호출이 `value` 변수에 저장된 빈 문자열에서 발생한 오류를 지정했습니다.

예외 도우미는 오류를 디버깅할 수 있는 좋은 기능입니다. 오류 세부 정보 보기와 같은 작업을 수행하고 예외 도우미에서 조사식을 추가할 수도 있습니다. 또는 필요한 경우 특정 예외를 throw하는 것에 대한 조건을 변경할 수 있습니다. 코드의 예외를 처리하는 방법에 대한 자세한 내용은 [디버깅 기법 및 도구](../debugger/write-better-code-with-visual-studio.md)를 참조하세요.

> [!NOTE]
> 예외 도우미(Exception Helper)는 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]부터 예외 도우미(Exception Assistant)를 대체했습니다.

**예외 설정** 노드를 확장하여 이 예외 형식을 처리하는 방법에 대한 더 많은 옵션을 확인합니다. 그러나 이 작업을 위해 아무 것도 변경할 필요가 없습니다!

## <a name="configure-debugging"></a>디버깅 구성

프로젝트를 [디버그 또는 릴리스 구성](../debugger/how-to-set-debug-and-release-configurations.md)으로 빌드하도록 구성하거나, 디버그를 위한 프로젝트 속성을 구성하거나, 디버그를 위한 [일반 설정](../debugger/how-to-specify-debugger-settings.md)을 구성할 수 있습니다. 또한 [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) 특성 또는 C/C++의 경우는 [NatVis 프레임워크](create-custom-views-of-native-objects.md)와 같은 기능을 사용하여 사용자 지정 정보를 표시하도록 디버거를 구성할 수 있습니다.

디버깅 속성은 프로젝트 형식마다 고유합니다. 예를 들어, 애플리케이션을 시작할 때 전달할 인수를 지정할 수 있습니다. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하여 프로젝트 관련 속성에 액세스할 수 있습니다. 디버깅 속성은 일반적으로 특정 프로젝트 형식에 따라 **빌드** 또는 **디버그** 탭에 나타납니다.

![프로젝트 속성](../debugger/media/dbg-tour-project-properties.png "프로젝트 속성")

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service에서 라이브 ASP.NET 앱 디버그

**스냅샷 디버거**는 관심이 있는 코드가 실행될 때 프로덕션 상태 앱의 스냅샷을 생성합니다. 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

![스냅샷 디버거 시작](../debugger/media/snapshot-launch.png "스냅샷 디버거 시작")

스냅샷 컬렉션은 Azure App Service에서 실행되는 ASP.NET 애플리케이션에서 사용할 수 있습니다. ASP.NET 애플리케이션은 .NET Framework 4.6.1 이상에서 실행돼야 하며, ASP.NET Core 애플리케이션은 Windows의 .NET Core 2.0 이상에서 실행돼야 합니다.

자세한 내용은 [스냅샷 디버거를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace 뒤로 이동을 사용하여 스냅샷 보기(Visual Studio Enterprise)

**IntelliTrace 뒤로 이동**은 모든 중단점 및 디버거 단계 이벤트에서 애플리케이션의 스냅샷을 자동으로 생성합니다. 기록된 스냅샷을 통해 이전 중단점 또는 단계로 돌아가서 애플리케이션의 과거 상태를 볼 수 있습니다. IntelliTrace 뒤로 이동을 사용하면 이전 애플리케이션 상태를 보고 싶지만 디버깅을 다시 시작하거나 원하는 앱 상태를 다시 만들지 않으려는 경우에 시간을 절약할 수 있습니다.

디버그 도구 모음의 **뒤로 가기**와 **앞으로 가기** 단추를 사용하여 이동하고 스냅샷을 볼 수 있습니다. 이 단추를 사용하여 **진단 도구** 창의 **이벤트** 탭에 나타나는 이벤트를 탐색할 수 있습니다.

![뒤로 이동 및 앞으로 이동 단추](../debugger/media/intellitrace-step-back-icons-description.png  "뒤로 이동 및 앞으로 이동 단추")

자세한 내용은 [IntelliTrace를 사용하여 이전 앱 상태 검사](../debugger/view-historical-application-state.md) 페이지를 참조하세요.

## <a name="debug-performance-issues"></a>성능 문제 디버그

앱이 너무 느리게 실행되거나 너무 많은 메모리를 사용하는 경우 먼저 프로파일링 도구를 사용하여 앱을 테스트해야 할 수 있습니다. CPU 사용량 도구 및 메모리 분석기와 같은 프로파일링 도구에 대한 자세한 내용은 [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 많은 디버거 기능을 간략하게 살펴봤습니다. 중단점과 같은 이러한 기능 중 하나를 더 자세히 살펴보기를 원할 수 있습니다.

> [!div class="nextstepaction"]
> [중단점 사용에 대해 알아보기](../debugger/using-breakpoints.md)
