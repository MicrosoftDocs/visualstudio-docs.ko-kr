---
title: Visual Studio Tools for Unity 사용 | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d1bca9bed18de822de71ca441387adeaefc65ec3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649392"
---
# <a name="use-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity 사용

이 섹션에서는 Visual Studio Tools for Unity의 통합 및 생산성 기능을 사용하는 방법과 Unity 개발을 위해 Visual Studio 디버거를 사용하는 방법에 대해 배워 봅니다.

## <a name="open-unity-scripts-in-visual-studio"></a>Visual Studio에서 Unity 스크립트 열기

Visual Studio가 [Unity의 외부 스크립트 편집기로 설정](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)되면 Unity 편집기에서 스크립트를 열 때 Visual Studio가 자동으로 시작되거나 전환되고, 선택한 스크립트가 열립니다. Unity 프로젝트에서 스크립트를 두 번 클릭하면 됩니다.

또는 Unity의 **Assets**(자산) 메뉴에서 **Open C# Project**(C# 프로젝트 열기)를 선택하여 소스 편집기에 열린 스크립트가 없는 상태로 Visual Studio를 열 수 있습니다.

![C# 프로젝트 열기](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Unity 설명서 액세스

Visual Studio에서 신속하게 Unity 스크립팅 설명서에 액세스할 수 있습니다. Visual Studio Tools for Unity에서 로컬에 있는 API 설명서를 찾지 못하는 경우 온라인으로 찾기를 시도합니다.

- Visual Studio에서 알아보려는 Unity API를 강조 표시하거나 그 위로 커서를 가져간 다음, **Ctrl**+**Alt**+**M**, **Ctrl**+**H**를 누릅니다.

## <a name="intellisense-for-unity-api-messages"></a>Unity API 메시지에 대한 IntelliSense

Intellisense 코드 완성을 사용하면 MonoBehaviour 스크립트에서 Unity API 메시지를 쉽게 구현하고 Unity API를 원활하게 학습할 수 있습니다. Unity 메시지에 대해 IntelliSense를 사용하는 방법은 다음과 같습니다.

1. `MonoBehaviour`에서 파생된 클래스 본문 안에서 새 줄에 커서를 놓습니다.

2. `OnTriggerEnter`와 같은 Unity 메시지 이름을 입력합니다.

3. 글자 “**ontri**”를 입력하면 IntelliSense 제안 목록이 나타납니다.

   ![Using IntelliSense](media/vstu_intellisense1.png)

4. 세 가지 방법으로 목록의 선택 항목을 변경할 수 있습니다.

    - **위쪽** 및 **아래쪽** 화살표 키를 사용합니다.

    - 원하는 항목을 마우스로 클릭합니다.

    - 원하는 항목의 이름을 계속 입력합니다.

5. IntelliSense에서는 다음과 같은 방법으로 필요한 매개 변수를 모두 포함하는 선택한 Unity 메시지를 삽입할 수 있습니다.

    - **Tab** 키를 누릅니다.

    - **Enter** 키를 누릅니다.

    - 선택한 항목을 두 번 클릭합니다.

   ![IntelliSense에서 Unity 메시지 삽입](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Unity MonoBehavior 스크립팅 마법사

MonoBehavior 마법사를 사용하여 모든 Unity API 메서드의 목록을 보고 빈 정의를 빠르게 구현할 수 있습니다. 특히 **메서드 주석 생성** 옵션이 사용하도록 설정하면 Unity API에서 사용 가능한 내용을 학습하는 경우 이 기능이 유용합니다.

MonoBehavior 마법사를 사용하여 빈 MonoBehavior 메서드 정의를 만들려면:

1. Visual Studio에서 메서드를 삽입할 위치에 커서를 놓은 다음, **Ctrl**+**Shift**+**M**을 눌러 MonoBehavior 마법사를 시작합니다.

2. **스크립트 메서드 만들기** 창에서 추가하려는 각 메서드 이름 옆의 확인란을 선택합니다.

3. **Framework 버전** 드롭다운을 사용하여 원하는 버전을 선택합니다.

4. 기본적으로 메서드는 커서의 위치에 삽입됩니다. 또는 **삽입 지점** 드롭다운의 값을 원하는 위치로 변경하여 클래스에 이미 구현된 메서드 뒤에 삽입하도록 선택할 수 있습니다.

5. 마법사가 선택한 방법에 대한 주석을 생성하게 하려면 **메서드 주석 생성** 확인란에 표시합니다. 이러한 주석은 해당 메서드를 호출하는 때가 언제인지, 해당 메서드가 담당하는 역할이 무엇인지 이해할 수 있기 위해 생성합니다.

6. **확인** 단추를 선택하여 마법사를 종료하고 메서드를 코드에 삽입합니다.

   ![monobehavior 마법사 대화 상자입니다.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Unity 프로젝트 탐색기

![Unity 프로젝트 탐색기 창입니다.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity 프로젝트 탐색기는 모든 Unity 프로젝트 파일과 디렉터리를 Unity 편집기와 동일한 방법으로 표시합니다. 이는 Unity 스크립트를 Visual Studio에서 생성된 프로젝트 또는 솔루션으로 구성하는 일반적인 Visual Studio 솔루션 탐색기를 사용하여 Unity 스크립트를 탐색하는 것과 다릅니다.

- 주 Visual Studio 메뉴에서 **보기 > Unity 프로젝트 탐색기**를 선택합니다. 바로 가기 키: **Alt**+**Shift**+**E**

   ![Unity 프로젝트 탐색기 창을 봅니다.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Unity 디버깅

Visual Studio Tools for Unity를 통해 Visual Studio의 강력한 디버거를 사용하여 Unity 프로젝트에 대해 편집기와 게임 스크립트를 모두 디버그할 수 있습니다.

### <a name="debug-in-the-unity-editor"></a>Unity 편집기에서 디버그

#### <a name="start-debugging"></a>디버그 시작

1. **Unity에 연결** 레이블이 지정된 **재생** 단추를 클릭하여 Visual Studio를 Unity에 연결하거나, 바로 가기 키 **F5** 키를 사용합니다.

   ![Visual Studio에서 [재생] 클릭](media/vstu_play-button.png)

2. Unity로 전환하고 **Play**(플레이) 단추를 클릭하여 편집기에서 게임을 실행합니다.

   ![Unity에서 Play([플레이]) 클릭](media/vstu_unity-play-button.png)

3. Visual Studio에 연결된 Unity 편집기에서 게임을 실행하면 중단점에 도달할 때 게임 실행이 일시 중지되고 게임이 중단점에 도달한 코드 줄이 Visual Studio에 표시됩니다.

#### <a name="stop-debugging"></a>디버깅 중지

- Visual Studio에서 **중지** 단추를 클릭하거나, 바로 가기 키 **Shift+F5**를 사용합니다.

  ![Visual Studio에서 [중지] 클릭](media/vstu_stop-debugger.png)

Visual Studio의 디버깅에 대한 자세한 내용은 [Visual Studio 디버거 개요](../debugger/debugger-feature-tour.md)를 참조하세요.

#### <a name="attach-to-unity-and-play"></a>Unity에 연결 및 재생

더욱 편리하게 사용하려면 **Unity에 연결** 단추를 **Unity에 연결 및 재생** 모드로 변경합니다.

1. **Unity에 연결** 단추 옆에 있는 작은 **아래쪽 화살표**를 클릭합니다.

1. 드롭다운 메뉴에서 **Unity에 연결 및 재생**을 선택합니다.

    ![연결 및 재생](media/vstu_attach-and-play.png)

[재생] 단추에는 **Unity에 연결 및 재생** 레이블이 지정됩니다. 이 단추를 클릭하거나 바로 가기 키 **F5** 키를 사용하면 Visual Studio 디버거를 연결할 뿐 아니라 자동으로 Unity 편집기로 전환되고 편집기에서 게임이 실행됩니다.

Visual Studio에서 **중지** 단추를 클릭하거나 바로 가기 키 **Shift**+**F5**를 사용하면 자동으로 Unity 편집기에서 게임이 중지됩니다.

### <a name="debug-unity-player-builds"></a>Unity 플레이어 빌드 디버그

Visual Studio를 사용하여 다양한 Unity 플레이어의 개발 빌드를 디버그할 수 있습니다.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Unity 플레이어에서 스크립트 디버깅 사용

1. Unity에서 **파일 > 빌드 설정**을 선택하여 빌드 설정을 엽니다.

2. [빌드 설정] 창에서 **개발 빌드** 및 **스크립트 디버깅** 확인란을 선택합니다.

   ![디버깅을 위해 Unity 빌드 설정을 구성합니다.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>디버거를 연결할 Unity 인스턴스 선택

- Visual Studio의 주 메뉴에서 **디버그 > Unity 디버거 연결**을 선택합니다.

   ![Unity 디버거를 연결합니다.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Unity 인스턴스 선택** 대화 상자는 연결할 수 있는 각 Unity 인스턴스에 대한 일부 정보를 표시합니다.

   ![연결할 Unity 인스턴스를 선택합니다.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **프로젝트**

   이 Unity의 인스턴스에서 실행되는 Unity 프로젝트의 이름입니다.

   **컴퓨터** 이 Unity가 실행되고 있는 컴퓨터 또는 디바이스의 이름입니다.

   이 Unity의 인스턴스가 Unity 편집기의 일부로 실행되면 **형식** **편집기**이고, 이 Unity의 인스턴스가 독립 실행형 플레이어이면 **플레이어**입니다.

   **포트** 이 Unity의 인스턴스에서 통신하는 데 사용하는 UDP 소켓의 포트 번호입니다.

> [!IMPORTANT]
> Visual Studio Tools for Unity 및 Unity 인스턴스가 UDP 네트워크 소켓을 통해 통신 중이므로 방화벽이 이를 감지할 수 있습니다. 이 경우 VSTU 및 Unity가 통신할 수 있도록  연결 권한을 부여해야 합니다.

### <a name="debug-a-dll-in-your-unity-project"></a>Unity 프로젝트에서 DLL 디버그

많은 Unity 개발자가 개발하는 기능을 쉽게 다른 프로젝트와 공유할 수 있도록 코드 구성 요소를 외부 DLL로 작하고 있습니다. Visual Studio Tools for Unity를 통해 Unity 프로젝트에서 이러한 DDL의 코드를 다른 코드와 함께 원활하게 디버그할 수 있습니다.

> [!NOTE]
> 이때 Visual Studio Tools for Unity는 관리 DLL만 지원합니다. C++에서 작성한 것과 같은 네이티브 코드 DLL의 디버깅은 지원하지 않습니다.

여기에 설명된 시나리오에서는 사용자에게 소스 코드가 있다고 가정합니다. 즉, 자사 코드를 개발 또는 다시 사용하는 중이거나 타사 라이브러리에 대한 소스 코드가 있으며 이를 Unity 프로젝트에서 DLL로 배포하도록 계획 중이라고 가정합니다. 이 시나리오는 소스 코드가 없는 DLL 디버깅에 대해서는 설명하지 않습니다.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Unity 프로젝트에서 사용되는 관리 DLL 프로젝트를 디버그하려면

1. Visual Studio Tools for Unity에서 생성한 Visual Studio 솔루션에 기존 DLL 프로젝트를 추가합니다. 새로운 관리 DLL 프로젝트를 시작하여 Unity 프로젝트에 코드 구성 요소를 포함하는 경우도 더러 있을 수 있습니다. 이러한 경우 새로운 관리 DLL 프로젝트를 Visual Studio 솔루션에 대신 추가할 수 있습니다. 기존 또는 새 프로젝트를 솔루션에 추가하는 방법에 대한 자세한 내용은 [방법: 솔루션에 프로젝트 추가](https://msdn.microsoft.com/library/ff460187.aspx)를 참조하세요.

   ![기존 DLL 프로젝트를 솔루션에 추가합니다.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   두 경우 모두 Visual Studio Tools for Unity에서는 프로젝트 및 솔루션 파일을 다시 생성해야 하는 경우에도 프로젝트 참조를 유지하므로 이러한 단계는 한 번만 수행하면 됩니다.

2. DLL 프로젝트에서 올바른 Unity 프레임워크 프로필을 참조하세요. Visual Studio의 DLL 프로젝트 속성에서 **대상 프레임워크** 속성을 사용 중인 Unity 프레임워크 버전으로 설정합니다. 이는 Unity 전체, 마이크로, 또는 웹 기반 클래스 라이브러리 등 프로젝트가 대상으로 하는 API 호환성과 일치하는 Unity 기반 클래스 라이브러리입니다. 다른 프레임워크 또는 호환성 수준에 있지만 사용 중인 Unity 프레임워크 버전에는 없을 수 있는 프레임워크 메서드를 DLL에서 호출하는 것을 방지합니다.

> [!NOTE]
> 다음은 Unity의 레거시 런타임을 사용하는 경우에만 필요합니다. 새 Unity 런타임을 사용하는 경우에는 해당 전용 3.5 프로필을 더 이상 사용할 필요가 없습니다. Unity 버전과 호환되는 .NET 4.x 프로필을 사용합니다.

   ![DLL의 대상 프레임워크를 Unity 프레임워크로 설정합니다.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Unity 프로젝트의 자산 폴더에 DLL을 복사합니다. Unity에서 자산은 런타임에 로드될 수 있도록 Unity 앱과 함께 배포되고 패키지되는 파일입니다. DLL은 런타임에 연결되므로 DDL을 자산으로 배포해야 합니다. 자산으로 배포하기 위해 Unity 편집기는 Unity 프로젝트에서 자산 폴더 안에 DLL을 배치할 것을 요구합니다. 다음 두 가지 방법으로 이 작업을 수행할 수 있습니다.

   - DLL 프로젝트의 빌드 설정을 수정하여 해당 출력 폴더에서 Unity 프로젝트의 **자산** 폴더로 출력 DLL 및 PDB 파일을 복사하는 빌드 후 작업을 포함합니다.

   - DLL 프로젝트의 빌드 설정을 수정하여 Unity 프로젝트의 **자산** 폴더로 해당 출력 폴더를 설정합니다. DLL 및 PDB 파일은 모두 **자산** 폴더에 배치됩니다.

   PDB 파일은 DLL의 디버깅 기호를 포함하며 DLL 코드를 소스 코드 형태로 매핑하므로 디버깅에 필요합니다. 레거시 런타임을 대상으로 지정하면 Visual Studio Tools for Unity에서는 DLL 및 PDB의 정보를 사용하여 레거시 Unity 스크립팅 엔진에서 사용되는 디버그 기호 형식인 DLL.MDB 파일을 만듭니다. 새 런타임을 대상으로 지정하고 이식 가능한 PDB를 사용하면 새 Unity 런타임이 기본적으로 이식 가능한 PDB를 사용할 수 있으므로 Visual Studio Tools for Unity에서는 기호 변환을 수행하지 않습니다.

   PDB 생성에 대한 자세한 내용은 [여기](../debugger/how-to-set-debug-and-release-configurations.md)에서 확인할 수 있습니다. 새 런타임을 대상으로 지정하는 경우 이식 가능한 PDB를 제대로 생성하려면 “디버깅 정보”가 “이식 가능”으로 설정되어 있는지 확인하세요. 레거시 런타임을 대상으로 지정하는 경우에는 “전체”를 사용해야 합니다.

4. 코드를 디버그합니다. 이제 Unity 프로젝트의 소스 코드와 함께 DLL 소스 코드를 디버그할 수 있으며 중단점 및 단계별 코드 실행 등 익숙한 디버깅 기능을 모두 사용할 수 있습니다.

## <a name="keyboard-shortcuts"></a>바로 가기 키

바로 가기 키를 사용하여 Visual Studio 기능에 대한 Unity 도구에 신속하게 액세스할 수 있습니다. 다음은 사용할 수 있는 바로 가기를 정리한 것입니다.

|명령|바로 가기|바로 가기 명령 이름|
|-------------|--------------|---------------------------|
|MonoBehavior 마법사 열기|**Ctrl**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Unity 프로젝트 탐색기 열기|**Alt**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Unity 설명서 액세스|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Unity 디버거(플레이어 또는 편집기)에 연결|**_기본값 없음_**|**Debug.AttachUnityDebugger**|

기본값이 마음에 들지 않는 경우 바로 가기 키 조합을 변경할 수 있습니다. 변경 방법에 대한 자세한 내용은 [Visual Studio에서 바로 가기 키 식별 및 사용자 지정](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.
