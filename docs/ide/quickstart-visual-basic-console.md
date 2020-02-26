---
title: Visual Basic을 사용하여 첫 번째 콘솔 앱 만들기
description: Visual Studio에서 Visual Basic을 사용하여 간단한 Hello World 콘솔 앱을 만드는 방법을 단계별로 알아봅니다.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579502"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>빠른 시작: Visual Studio에서 Visual Basic을 사용하여 첫 번째 콘솔 앱 만들기

Visual Studio IDE(통합 개발 환경)에 대한 소개는 이 5~10분 분량으로 여기서 콘솔에서 실행되는 간단한 Visual Basic 애플리케이션을 만듭니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

## <a name="create-a-project"></a>프로젝트 만들기

먼저 Visual Basic 애플리케이션 프로젝트를 만들어야 합니다. 아무 것도 추가하지 않아도 필요한 모든 템플릿 파일과 함께 프로젝트 형식이 제공됩니다.

::: moniker range="vs-2017"

1. Visual Studio 2017을 엽니다.

2. 상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Basic**을 확장한 후 **.NET Core**를 선택합니다. 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. 프로젝트의 이름을 *HelloWorld*로 지정합니다.

   ![Visual Studio IDE의 새 프로젝트 대화 상자의 콘솔 앱(.NET Core) 프로젝트 템플릿](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     **콘솔 앱(.NET Core)** 템플릿 프로젝트가 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Open Visual Studio 설치 관리자** 링크를 클릭합니다.

   ![새 프로젝트 대화 상자에서 Visual Studio 설치 관리자 열기 링크를 클릭합니다.](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

     ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> 이 빠른 시작의 일부 스크린샷은 어두운 테마를 사용합니다. 어두운 테마를 사용하지 않지만 원하는 경우 [Visual Studio IDE 및 편집기 개인 설정](quickstart-personalize-the-ide.md) 페이지에서 참조하여 방법을 알아봅니다.

1. Visual Studio 2019를 엽니다.

1. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   !['새 프로젝트 만들기' 창 보기](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 그런 다음, 언어 목록에서 **Visual Basic**을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다. 

   언어 및 플랫폼 필터를 적용한 후 **콘솔 앱(.NET Core)** 템플릿을 선택한 후, **다음**을 선택합니다.

   ![콘솔 앱(.NET Framework)에 대한 Visual Basic 템플릿을 선택합니다.](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > **콘솔 앱(.NET Core)** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다.
   >
   > !['새 프로젝트 만들기' 창의 '원하는 항목을 찾을 수 없음' 메시지에서 '추가 도구 및 기능 설치' 링크](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > 그런 다음, Visual Studio 설치 관리자에서 **.NET Core 플랫폼 간 개발** 워크로드를 선택합니다.
   >
   > ![Visual Studio Installer에서 .NET Core 플랫폼 간 개발 워크로드](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > 그런 다음, Visual Studio 설치 관리자에서 **수정** 단추를 선택합니다. 작업 내용을 저장하라는 메시지가 나타날 수 있습니다. 그럴 경우 그렇게 하세요. 다음으로, **계속**을 선택하여 워크로드를 설치합니다. 그런 다음, 이 "[프로젝트 만들기](#create-a-project)" 프로시저의 2단계로 돌아갑니다.

1. **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *WhatIsYourName*을 입력합니다. 그런 다음, **만들기**를 선택합니다.

   !['새 프로젝트 구성' 창에서 프로젝트의 이름을 'WhatIsYourName'으로 지정합니다.](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio에서 새 프로젝트를 엽니다.

::: moniker-end

## <a name="create-the-application"></a>애플리케이션 만들기

Visual Basic 프로젝트 템플릿을 선택하고 프로젝트 이름을 지정한 후에 Visual Studio에서 간단한 "Hello World" 애플리케이션을 만듭니다. <xref:System.Console.WriteLine%2A> 메서드를 호출하여 리터럴 문자열 "Hello World!"를 콘솔 창에 표시합니다.

![템플릿에서 기본 Hello World 코드 보기](../ide/media/vb-console-helloworld-template.png)

IDE에서 **HelloWorld** 단추를 클릭하면 디버그 모드에서 프로그램을 실행할 수 있습니다.

  ![Hello World 단추를 클릭하여 디버그 모드에서 프로그램을 실행합니다.](../ide/media/vb-console-hello-world-button.png)

이렇게 하면 콘솔 창이 잠깐만 표시되었다가 닫힙니다. 단일 문을 실행한 후에 애플리케이션이 종료되도록 `Main` 메서드가 종료되기 때문에 이런 결과가 발생합니다.

### <a name="add-some-code"></a>일부 코드를 추가합니다.

애플리케이션을 일시 중지하고 사용자 입력을 요청하는 코드를 추가해 보겠습니다.

1. <xref:System.Console.WriteLine%2A> 메서드 호출 바로 다음에 아래 코드를 추가합니다.

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    이 키를 누를 때까지 프로그램을 일시 중지합니다.

2. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

   이렇게 하면 프로그램이 IL(중간 언어)로 컴파일됩니다. 이 컴파일 결과는 JIT(Just-In-Time) 컴파일러에 의해 이진 코드로 변환됩니다.

## <a name="run-the-application"></a>애플리케이션 실행

1. 도구 모음에서 **HelloWorld** 단추를 클릭합니다.

   ![Hello World 단추를 클릭하여 도구 모음에서 프로그램을 실행합니다.](../ide/media/vb-console-hello-world-button.png)

2. 콘솔 창을 닫으려면 아무 키나 누릅니다.

   ![Hello World 및 계속하려면 아무 키나 누르세요.를 표시하는 콘솔 창](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>다음 단계

이 빠른 시작을 완료한 것을 축하 드립니다! Visual Basic 및 Visual Studio IDE를 이해하는 데 도움이 되었기를 바랍니다. 자세히 알아보려면 계속 다음 자습서를 사용하세요.

> [!div class="nextstepaction"]
> [Visual Studio에서 Visual Basic 시작하기](../get-started/visual-basic/tutorial-console.md)
