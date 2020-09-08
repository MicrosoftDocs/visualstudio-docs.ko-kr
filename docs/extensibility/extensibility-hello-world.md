---
title: Hello World 확장 자습서 | Microsoft Docs
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 796cb53ea5124662c695cce55241794802f042c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905936"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>자습서 - 첫 번째 확장 만들기: Hello World

이 Hello World 예제는 Visual Studio에서 첫 번째 확장을 만드는 과정을 안내합니다. 이 자습서에서는 Visual Studio에 새 명령을 추가하는 방법을 보여 줍니다.

이 과정에서 다음 방법을 알게 됩니다.

* **[확장성 프로젝트 만들기](#create-an-extensibility-project)**
* **[사용자 지정 명령 추가](#add-a-custom-command)**
* **[소스 코드 수정](#modify-the-source-code)**
* **[스크립트를 실행합니다.](#run-it)**

이 예제에서는 Visual C#를 사용하여 “Say Hello World!”라는 사용자 지정 메뉴 단추를 추가합니다. 이는 다음과 같습니다.

![Hello World 명령](media/hello-world-say-hello-world.png)

> [!NOTE]
> 이 문서는 Windows용 Visual Studio에 적용됩니다. Mac용 Visual Studio의 경우 [Mac용 Visual Studio 확장성 연습](/visualstudio/mac/extending-visual-studio-mac-walkthrough)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

시작하기 전에 필요한 VSIX 템플릿 및 샘플 코드를 포함하는 **Visual Studio 확장 개발** 워크로드를 설치했는지 확인합니다.

> [!NOTE]
> 모든 버전의 Visual Studio(Community, Professional 또는 Enterprise)를 사용하여 Visual Studio 확장성 프로젝트를 만들 수 있습니다.

## <a name="create-an-extensibility-project"></a>확장성 프로젝트 만들기

::: moniker range="vs-2017"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

2단계. 오른쪽 상단에 있는 검색 상자에 “vsix”를 입력하고 Visual C# **VSIX 프로젝트**를 선택합니다. 대화 상자의 맨 아래에 있는 **이름**에 “HelloWorld”를 입력하고 **확인**을 선택합니다.

![새 프로젝트](media/hello-world-new-project.png)

이제 시작 페이지와 몇 가지 샘플 리소스가 표시됩니다.

이 자습서를 종료하고 다시 시작해야 하는 경우 **최근** 섹션의 **시작 페이지**에서 새 HelloWorld 프로젝트를 찾을 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다. “vsix”를 검색하고 Visual C# **VSIX 프로젝트** 선택하고 **다음**을 선택합니다.

2단계. **프로젝트 이름**으로 “HelloWorld”를 입력하고 **만들기**를 선택합니다.

![새 프로젝트](media/hello-world-new-project-2019.png)

이제 **솔루션 탐색기**에서 HelloWorld 프로젝트가 표시됩니다.

::: moniker-end

## <a name="add-a-custom-command"></a>사용자 지정 명령 추가

1단계. *.vsixmanifest* 매니페스트 파일을 선택한 경우 설명, 작성자 및 버전과 같은 변경 가능한 옵션이 표시됩니다.

2단계. 솔루션이 아닌 프로젝트를 마우스 오른쪽 단추로 클릭합니다. 바로 가기 메뉴에서 **추가**를 선택하고 **새 항목**을 선택합니다.

3단계. **확장성** 섹션을 선택한 다음 **명령**을 선택합니다.

4단계. 하단에 있는 **이름** 필드에 *Command.cs*와 같은 파일 이름을 입력합니다.

![사용자 지정 명령](media/hello-world-vsix-command.png)

새 명령 파일은 **솔루션 탐색기**에 표시됩니다. **리소스** 노드에서 명령과 관련된 다른 파일을 찾을 수 있습니다. 예를 들어 이미지를 수정하려는 경우 PNG 파일이 여기에 표시됩니다.

## <a name="modify-the-source-code"></a>소스 코드 수정

이 시점에서 명령 및 단추 텍스트는 자동으로 생성되지만 그렇게 흥미롭지는 않습니다. 변경하려는 경우 VSCT 파일 및 CS 파일을 수정할 수 있습니다.

* VSCT 파일에서 명령의 이름을 바꾸고 Visual Studio 명령 시스템에서 이동하는 위치를 정의할 수 있습니다. VSCT 파일을 탐색할 때 VSCT 코드의 각 섹션이 제어하는 것을 설명하는 주석이 표시됩니다.

* CS 파일에서는 클릭 처리기와 같은 동작을 정의할 수 있습니다.

::: moniker range="vs-2017"

1단계. **솔루션 탐색기**에서 새 명령의 VSCT 파일을 찾습니다. 이 경우에는 *CommandPackage.vsct*입니다.

![명령 패키지 vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **솔루션 탐색기**에서 확장 VS 패키지용 VSCT 파일을 찾습니다. 이 경우에는 *HelloWorldPackage.vsct*입니다.

::: moniker-end

2단계. `ButtonText` 매개 변수를 `Say Hello World!`로 변경합니다.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

3단계. **솔루션 탐색기**로 돌아가서 *Command.cs* 파일을 찾습니다. `Execute` 메서드에서 `string.Format(..)`에서 `Hello World!`로 `message` 문자열을 변경합니다.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

각 파일에 대한 변경 내용을 저장해야 합니다.

## <a name="run-it"></a>스크립트를 실행합니다.

이제 Visual Studio 실험적 인스턴스에서 소스 코드를 실행할 수 있습니다.

1단계. **F5**를 눌러 **디버깅 시작** 명령을 실행합니다. 이 명령은 프로젝트를 빌드하고 디버거를 시작하여 **실험적 인스턴스**라는 Visual Studio의 새 인스턴스를 시작합니다.

::: moniker range="vs-2017"

Visual Studio 제목 표시줄에 **실험적 인스턴스**라는 단어가 표시됩니다.

![실험적 인스턴스 제목 표시줄](media/hello-world-exp-instance.png)

::: moniker-end

2단계. **실험적 인스턴스**의 **도구** 메뉴에서 **Say Hello World!** 를 클릭합니다.

![최종 결과](media/hello-world-final-result.png)

새 사용자 지정 명령의 출력을 볼 수 있습니다. 이 경우 화면 중앙에 **Hello World!** 메시지가 표시되는 대화 상자가 반환됩니다.

## <a name="next-steps"></a>다음 단계

이제 Visual Studio 확장성 사용에 대한 기본 사항을 파악했으니 여기에서 더 자세히 알아볼 수 있습니다.

* [Visual Studio 확장 개발 시작](starting-to-develop-visual-studio-extensions.md) - 샘플, 자습서. 및 확장 게시
* [Visual Studio 2017 SDK의 새로운 기능](what-s-new-in-the-visual-studio-2017-sdk.md) - Visual Studio 2017의 새로운 확장성 기능
* [Visual Studio 2019 SDK의 새로운 기능](whats-new-visual-studio-2019-sdk.md) - Visual Studio 2019의 새로운 확장성 기능
* [Visual Studio SDK 기본 사항](internals/inside-the-visual-studio-sdk.md) - Visual Studio 확장성의 세부 정보 학습
