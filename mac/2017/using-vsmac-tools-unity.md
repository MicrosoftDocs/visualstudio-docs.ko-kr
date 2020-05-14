---
title: Mac용 Visual Studio Tools for Unity 사용
description: 이 가이드에서는 Mac용 Visual Studio Tools for Unity 확장을 사용하는 방법을 설명합니다.
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79306706"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Mac용 Visual Studio Tools for Unity 사용

이 섹션에서는 Mac용 Visual Studio Tools for Unity의 통합 및 생산성 기능을 사용하는 방법과 Unity 개발을 위해 Mac용 Visual Studio 디버거를 사용하는 방법에 대해 배워 봅니다.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 Unity 스크립트 열기

Mac용 Visual Studio가 [Unity의 외부 스크립트 편집기로 설정](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac)되면 Unity 편집기에서 스크립트를 열 때 Mac용 Visual Studio가 자동으로 실행되거나 전환되고, 선택한 스크립트가 열립니다.

또는 Unity의 **Assets**(자산) 메뉴에서 **Open C# Project(C# 프로젝트 열기)** 를 선택하여 소스 편집기에 열린 스크립트가 없는 상태로 Mac용 Visual Studio를 열 수 있습니다.

![C# 프로젝트 열기](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Unity 설명서 액세스

Mac용 Visual Studio Tools for Unity에는 Unity API 설명서에 액세스하는 바로 가기가 포함되어 있습니다. Mac용 Visual Studio에서 Unity API 문서에 액세스하려면 알아보려는 Unity API 위에 커서를 놓고 **⌘ command+'** 를 누릅니다.

## <a name="intellisense-for-unity-messages"></a>Unity 메시지에 대한 IntelliSense
Unity 엔진은 MonoBehaviour 스크립트에 메시지를 전송하므로 개발자는 OnMouseDown, OnTriggerEnter 등의 메시지에 반응하는 코드를 작성할 수 있습니다. 이러한 메시지는 기본 MonoBehaviour 클래스의 가상 메서드가 아니므로 MonoDevelop와 같은 일부 IDE에는 Unity 메시지에 대한 코드 완성 기능이 없습니다.

그러나 Mac용 Visual Studio Tools for Unity는 IntelliSense 기능을 Unity 메시지로 확장합니다. 따라서 MonoBehaviour 스크립트에서 Unity 메시지를 쉽게 구현하고 Unity API를 원활하게 학습할 수 있습니다. Unity 메시지에 대해 IntelliSense를 사용하는 방법은 다음과 같습니다.

1. MonoBehaviour에서 파생된 클래스 본문 안에서 새 줄에 커서를 놓습니다.

2. `OnTriggerEnter`와 같은 Unity 메시지 이름을 입력합니다.

3. 글자 “**ont**”를 입력하면 IntelliSense 제안 목록이 나타납니다.

   ![IntelliSense 사용](media/using-vsmac-tools-unity-image2.png)

4. 세 가지 방법으로 목록의 선택 항목을 변경할 수 있습니다.

   * **위쪽** 및 **아래쪽** 화살표 키를 사용합니다.

   * 원하는 항목을 마우스로 클릭합니다.

   * 원하는 항목의 이름을 계속 입력합니다.

5. IntelliSense에서는 다음과 같은 방법으로 필요한 매개 변수를 모두 포함하는 선택한 Unity 메시지를 삽입할 수 있습니다.

   * **Tab** 키를 누릅니다.

   * **Return** 키를 누릅니다.

   * 선택한 항목을 두 번 클릭합니다.

   ![IntelliSense에서 Unity 메시지 삽입](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>새 Unity 파일 및 폴더 추가

언제든지 Unity 편집기에서 Unity 프로젝트에 새 파일을 추가할 수 있지만, Mac용 Visual Studio를 사용하면 Visual Studio 내에서 Unity 스크립트, 셰이더 및 폴더를 손쉽게 새로 만들 수 있습니다.

### <a name="add-a-new-c-monobehaviour-script"></a>새 C# MonoBehaviour 스크립트 추가

새 C# MonoBehaviour 스크립트를 추가하려면 솔루션 패드에서 **자산 폴더** 또는 하위 디렉터리 중 하나를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 MonoBehaviour**를 선택합니다.

![새 MonoBehaviour 추가](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>새 Unity 셰이더 추가

새 Unity 셰이더를 추가하려면 솔루션 패드에서 **자산 폴더** 또는 하위 디렉터리를 마우스 오른쪽 버튼으로 클릭하고 **추가 > 새 셰이더**를 선택합니다.

### <a name="add-a-new-folder"></a>새 폴더 추가

새 폴더를 추가하려면 솔루션 패드에서 **자산 폴더** 또는 하위 디렉터리를 마우스 오른쪽 버튼으로 클릭하고 **추가 > 새 폴더**를 선택합니다.

이러한 추가는 Unity 편집기의 Project(프로젝트) 창에 반영됩니다.

### <a name="to-rename-a-file-or-folder"></a>파일 또는 폴더 이름 바꾸기
솔루션 패드에서 이름을 바꿀 항목을 **마우스 오른쪽 단추로 클릭**하고 **이름 바꾸기...** 를 선택합니다.

> [!NOTE]
> Mac용 Visual Studio의 새 Unity 프로젝트에 스크립트가 없으며 솔루션 패드에 자산 폴더가 표시되지 않은 경우 Unity 편집기에서 첫 번째 C# 스크립트를 추가하세요.

## <a name="unity-debugging"></a>Unity 디버깅

Mac용 Visual Studio로 Unity 프로젝트를 디버그할 수 있습니다.

### <a name="start-debugging"></a>디버깅 시작

디버깅을 시작하려면

1. **재생** 단추를 클릭하거나 **Command+Return** 또는 **F5** 키를 눌러 Visual Studio를 Unity에 연결합니다.

   ![Visual Studio에서 [재생] 클릭](media/using-vsmac-tools-unity-image5.png)

2. Unity로 전환하고 **Play**(플레이) 단추를 클릭하여 편집기에서 게임을 실행합니다.

   ![Unity에서 Play([플레이]) 클릭](media/using-vsmac-tools-unity-image6.png)

3. Visual Studio에 연결된 Unity 편집기에서 게임을 실행하면 중단점에 도달할 때 게임 실행이 일시 중지되고 게임이 중단점에 도달한 코드 줄이 Mac용 Visual Studio에 표시됩니다.

### <a name="stop-debugging"></a>디버깅 중지

디버깅을 중지하려면

1. Mac용 Visual Studio에서 **중지** 단추를 클릭하거나 **Shift+Command+Return**을 누릅니다.

   ![Visual Studio에서 [중지] 클릭](media/using-vsmac-tools-unity-image7.png)

Mac용 Visual Studio의 디버깅에 대한 자세한 내용은 [Using the debugger](debugging.md)(디버거 사용)를 참조하세요.
