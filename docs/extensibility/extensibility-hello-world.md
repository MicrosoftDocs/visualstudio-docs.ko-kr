---
title: 안녕하세요 세계 확장 자습서 | 마이크로 소프트 문서
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711658"
---
# <a name="create-your-first-extension-hello-world"></a>첫 번째 확장 프로그램 만들기: 안녕하세요 월드

이 Hello World 예제에서는 Visual Studio에 대한 첫 번째 확장을 만드는 단계를 안내합니다. 이 자습서에서는 Visual Studio에 새 명령을 추가하는 방법을 보여 주십입니다.

이 과정에서 다음 방법을 배웁니다.

* **[확장성 프로젝트 만들기](#create-an-extensibility-project)**
* **[사용자 지정 명령 추가](#add-a-custom-command)**
* **[소스 코드 수정](#modify-the-source-code)**
* **[스크립트를 실행합니다.](#run-it)**

이 예제에서는 Visual C#을 사용하여 "Say Hello World"라는 사용자 지정 메뉴 단추를 추가합니다. 다음과 같이 보입니다.

![안녕하세요 세계 명령](media/hello-world-say-hello-world.png)

> [!NOTE]
> 이 문서는 Windows의 Visual Studio에 적용됩니다. Mac용 비주얼 스튜디오의 경우 [Mac용 시각적 스튜디오에서 확장성 연습을](/visualstudio/mac/extending-visual-studio-mac-walkthrough)참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항

시작하기 전에 필요한 VSIX 템플릿과 샘플 코드를 포함하는 **Visual Studio 확장 개발** 워크로드를 설치했는지 확인합니다.

> [!NOTE]
> 모든 버전의 Visual Studio(커뮤니티, 전문가 또는 엔터프라이즈)를 사용하여 Visual Studio 확장성 프로젝트를 만들 수 있습니다.

## <a name="create-an-extensibility-project"></a>확장성 프로젝트 만들기

::: moniker range="vs-2017"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

2단계. 오른쪽 상단의 검색 상자에서 "vsix"를 입력하고 Visual C# **VSIX 프로젝트를**선택합니다. 대화 상자 하단에 **이름에** 대해 "HelloWorld"를 입력하고 **확인을**선택합니다.

![새 프로젝트](media/hello-world-new-project.png)

이제 시작 하기 페이지 와 일부 샘플 리소스가 표시 됩니다.

이 자습서를 떠나 다시 돌아와야 하는 경우 **최근** 섹션의 시작 **페이지에서** 새 HelloWorld 프로젝트를 찾을 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다. "vsix"를 검색하고 Visual C# **VSIX 프로젝트를** 선택한 다음 **다음**.

2단계. **프로젝트 이름에** 대해 "HelloWorld"를 입력하고 **만들기를**선택합니다.

![새 프로젝트](media/hello-world-new-project-2019.png)

이제 **솔루션 탐색기에서**HelloWorld 프로젝트가 표시됩니다.

::: moniker-end

## <a name="add-a-custom-command"></a>사용자 지정 명령 추가

1단계. *.vsixmanifest* 매니페스트 파일을 선택하면 설명, 작성자 및 버전과 같이 변경할 수 있는 옵션을 확인할 수 있습니다.

2단계. 솔루션이 아닌 프로젝트를 마우스 오른쪽 단추로 클릭합니다. 컨텍스트 메뉴에서 **추가**를 선택한 다음 **새 항목**입니다.

3단계. **확장성** 섹션을 선택한 다음 **명령을**선택합니다.

4단계. 아래쪽의 **이름** 필드에 *Command.cs*같은 파일 이름을 입력합니다.

![사용자 지정 명령](media/hello-world-vsix-command.png)

새 명령 파일은 **솔루션 탐색기에서**볼 수 있습니다. **리소스** 노드에서 명령과 관련된 다른 파일을 찾을 수 있습니다. 예를 들어 이미지를 수정하려는 경우 PNG 파일이 여기에 있습니다.

## <a name="modify-the-source-code"></a>소스 코드 수정

이 시점에서 명령 및 Button 텍스트는 자동으로 생성되며 그리 흥미롭지 않습니다. 변경하려는 경우 VSCT 파일 및 CS 파일을 수정할 수 있습니다.

* VSCT 파일은 명령의 이름을 바꿀 수 있을 뿐만 아니라 Visual Studio 명령 시스템에서 명령의 위치를 정의할 수 있는 곳입니다. VSCT 파일을 탐색할 때 VSCT 코드의 각 섹션이 제어하는 내용을 설명하는 주석을 확인할 수 있습니다.

* CS 파일은 클릭 처리기와 같은 작업을 정의할 수 있는 곳입니다.

::: moniker range="vs-2017"

1단계. **솔루션 탐색기에서**새 명령에 대한 VSCT 파일을 찾습니다. 이 경우 *CommandPackage.vsct*라고 합니다.

![명령 패키지 vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

1단계. **솔루션 탐색기에서**확장명 VS 패키지에 대한 VSCT 파일을 찾습니다. 이 경우 *HelloWorldPackage.vsct라고*합니다.

::: moniker-end

2단계. 매개 `ButtonText` 변수를 `Say Hello World!`로 변경합니다.

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

3단계. **솔루션 탐색기로** 돌아가 *서 Command.cs* 파일을 찾습니다. 메서드에서 `Execute` 문자열을 `message` 에서 `string.Format(..)` 로 `Hello World!`변경합니다.

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

변경 내용을 각 파일에 저장해야 합니다.

## <a name="run-it"></a>스크립트를 실행합니다.

이제 Visual Studio 실험 인스턴스에서 소스 코드를 실행할 수 있습니다.

1단계. **F5를** 눌러 **디버깅 시작 명령을 실행합니다.** 이 명령은 프로젝트를 빌드하고 디버거를 시작하여 **실험 인스턴스라는**Visual Studio의 새 인스턴스를 시작합니다.

::: moniker range="vs-2017"

Visual Studio 제목 표시줄에 **실험 인스턴스라는** 단어가 표시됩니다.

![실험 인스턴스 제목 표시줄](media/hello-world-exp-instance.png)

::: moniker-end

2단계. **실험 인스턴스의** **도구** 메뉴에서 **인사 세계를 클릭합니다!**.

![최종 결과](media/hello-world-final-result.png)

이 경우 **Hello World를** 제공하는 화면 중앙에 있는 대화 상자가 새 사용자 지정 명령의 출력을 볼 수 있습니다! 메시지가 표시됩니다.

## <a name="next-steps"></a>다음 단계

이제 Visual Studio 확장성 작업의 기본 을 알았으니 여기에서 자세히 알아볼 수 있습니다.

* 샘플, 자습서 - [비주얼 스튜디오 확장을 개발하기 시작합니다.](starting-to-develop-visual-studio-extensions.md) 및 확장 프로그램 게시
* [비주얼 스튜디오 2017 SDK의 새로운 기능](what-s-new-in-the-visual-studio-2017-sdk.md) - 비주얼 스튜디오 2017의 새로운 확장성 기능
* [비주얼 스튜디오 2019 SDK의 새로운 기능](whats-new-visual-studio-2019-sdk.md) - 비주얼 스튜디오 2019의 새로운 확장성 기능
* [비주얼 스튜디오 SDK 내부](internals/inside-the-visual-studio-sdk.md) - 비주얼 스튜디오 확장성에 대한 자세한 내용 알아보기
