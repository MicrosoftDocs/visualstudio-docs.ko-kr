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
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905936"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>자습서-첫 번째 확장 만들기: Hello World

이 Hello World 예제는 Visual Studio에 대 한 첫 번째 확장을 만드는 과정을 안내 합니다. 이 자습서에서는 Visual Studio에 새 명령을 추가 하는 방법을 보여 줍니다.

이 과정에서 다음 작업을 수행 하는 방법을 배웁니다.

* **[확장성 프로젝트 만들기](#create-an-extensibility-project)**
* **[사용자 지정 명령 추가](#add-a-custom-command)**
* **[소스 코드 수정](#modify-the-source-code)**
* **[스크립트를 실행합니다.](#run-it)**

이 예제에서는 Visual c #을 사용 하 여 "말한 Hello World!" 이라는 사용자 지정 메뉴 단추를 추가 합니다. 이는 다음과 같습니다.

![Hello World 명령](media/hello-world-say-hello-world.png)

> [!NOTE]
> 이 문서는 Windows의 Visual Studio에 적용 됩니다. Mac용 Visual Studio [Mac용 Visual Studio의 확장성 연습](/visualstudio/mac/extending-visual-studio-mac-walkthrough)을 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항

시작 하기 전에 필요한 VSIX 템플릿 및 샘플 코드를 포함 하는 **Visual Studio 확장 개발** 워크 로드를 설치 했는지 확인 합니다.

> [!NOTE]
> 모든 버전의 Visual Studio (Community, Professional 또는 Enterprise)를 사용 하 여 Visual Studio 확장성 프로젝트를 만들 수 있습니다.

## <a name="create-an-extensibility-project"></a>확장성 프로젝트 만들기

::: moniker range="vs-2017"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

2단계. 오른쪽 위에 있는 검색 상자에 "vsix"를 입력 하 고 Visual c # **Vsix 프로젝트**를 선택 합니다. 대화 상자의 맨 아래에 있는 **이름** 에 "HelloWorld"를 입력 하 고 **확인을**선택 합니다.

![새 프로젝트](media/hello-world-new-project.png)

이제 시작 페이지와 몇 가지 샘플 리소스가 표시 됩니다.

이 자습서를 종료 하 고 다시 시작 해야 하는 경우 **최근** 섹션의 **시작 페이지** 에서 새 HelloWorld 프로젝트를 찾을 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다. "Vsix"를 검색 하 고 Visual c # **Vsix 프로젝트** 를 선택한 후 **다음**을 선택 합니다.

2단계. **프로젝트 이름** 에 "HelloWorld"를 입력 하 고 **만들기**를 선택 합니다.

![새 프로젝트](media/hello-world-new-project-2019.png)

이제 **솔루션 탐색기**에서 HelloWorld 프로젝트가 표시 됩니다.

::: moniker-end

## <a name="add-a-custom-command"></a>사용자 지정 명령 추가

1단계. *Source.extension.vsixmanifest* 매니페스트 파일을 선택 하는 경우에는 설명, 작성자 및 버전과 같은 어떤 옵션을 변경할 수 있는지 확인할 수 있습니다.

2단계. 솔루션이 아닌 프로젝트를 마우스 오른쪽 단추로 클릭 합니다. 상황에 맞는 메뉴에서 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

3단계: **확장성** 섹션을 선택 하 고 **명령**을 선택 합니다.

4단계. 아래쪽에 있는 **이름** 필드에 *Command.cs*와 같은 파일 이름을 입력 합니다.

![사용자 지정 명령](media/hello-world-vsix-command.png)

새 명령 파일은 **솔루션 탐색기**에서 볼 수 있습니다. **리소스** 노드에서 명령과 관련 된 다른 파일을 찾을 수 있습니다. 예를 들어 이미지를 수정 하려는 경우 PNG 파일이 여기에 표시 됩니다.

## <a name="modify-the-source-code"></a>소스 코드 수정

이 시점에서 명령 및 단추 텍스트는 자동으로 생성 되며 매우 흥미롭습니다. 변경 하려는 경우 VSCT 파일 및 CS 파일을 수정할 수 있습니다.

* VSCT 파일은 명령의 이름을 바꾸고 Visual Studio 명령 시스템에서 이동 하는 위치를 정의할 수 있는 위치입니다. VSCT 파일을 탐색할 때 VSCT 코드의 각 섹션에 대해 설명 하는 주석이 표시 됩니다.

* CS 파일은 클릭 처리기와 같은 동작을 정의할 수 있는 위치입니다.

::: moniker range="vs-2017"

1단계. **솔루션 탐색기**에서 새 명령의 vsct 파일을 찾습니다. 이 경우에는 *Commandpackage. vsct*라고 합니다.

![명령 패키지 vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **솔루션 탐색기**에서 확장 VS 패키지용 vsct 파일을 찾습니다. 이 경우 *HelloWorldPackage*가 호출 됩니다.

::: moniker-end

2단계. `ButtonText`매개 변수를로 변경 `Say Hello World!` 합니다.

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

3단계: **솔루션 탐색기** 로 돌아가서 *Command.cs* 파일을 찾습니다. `Execute`메서드에서 문자열을 `message` 에서 `string.Format(..)` 로 변경 `Hello World!` 합니다.

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

각 파일에 대 한 변경 내용을 저장 해야 합니다.

## <a name="run-it"></a>스크립트를 실행합니다.

이제 Visual Studio 실험적 인스턴스에서 소스 코드를 실행할 수 있습니다.

1단계. **F5** 키를 눌러 **디버깅 시작** 명령을 실행 합니다. 이 명령은 프로젝트를 빌드하고 디버거를 시작 하 여 **실험적 인스턴스**라는 새 Visual Studio 인스턴스를 시작 합니다.

::: moniker range="vs-2017"

Visual Studio 제목 표시줄에 **실험적 인스턴스** 라는 단어가 표시 됩니다.

![실험적 인스턴스 제목 표시줄](media/hello-world-exp-instance.png)

::: moniker-end

2단계. **실험적 인스턴스의** **도구** 메뉴에서 **Hello World!** 를 클릭 합니다.

![최종 결과](media/hello-world-final-result.png)

새 사용자 지정 명령의 출력 (이 경우 화면 가운데에 Hello World를 제공 하는 대화 상자)이 표시 됩니다 **.** 반환됩니다.

## <a name="next-steps"></a>다음 단계

이제 Visual Studio 확장성 사용에 대 한 기본 사항을 배웠으므로 여기에서 자세히 알아볼 수 있습니다.

* [Visual Studio 확장 개발](starting-to-develop-visual-studio-extensions.md) -샘플, 자습서를 시작 합니다. 및 확장 게시
* [Visual studio 2017 SDK의 새로운](what-s-new-in-the-visual-studio-2017-sdk.md) 기능-visual studio 2017의 새로운 확장성 기능
* [Visual studio 2019 SDK의 새로운](whats-new-visual-studio-2019-sdk.md) 기능-visual studio 2019의 새로운 확장성 기능
* [Visual STUDIO SDK 내부](internals/inside-the-visual-studio-sdk.md) -Visual studio 확장성에 대 한 자세한 정보
