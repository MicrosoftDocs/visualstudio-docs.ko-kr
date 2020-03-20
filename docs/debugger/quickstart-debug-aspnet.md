---
title: ASP.NET Core 디버그
description: Visual Studio 디버거를 사용하여 ASP.NET Core 디버그
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: bbe3d23301f0853626a930855acf4b595c6a2923
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75847881"
---
# <a name="quickstart-debug-aspnet-core-with-the-visual-studio-debugger"></a>빠른 시작: Visual Studio 디버거를 사용하여 ASP.NET Core 디버그

Visual Studio 디버거는 앱을 디버그하도록 돕는 여러 가지 강력한 기능을 제공합니다. 이 항목에는 기본 기능 중 일부에 대해 알아보는 빠른 방법을 제공합니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기

1. Visual Studio를 엽니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **asp.net**을 입력하고 **템플릿**을 선택한 다음, **새 ASP.NET Core 웹 애플리케이션 만들기**를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에 **웹**을 선택한 다음, 가운데 창에서 **ASP.NET Core 웹 애플리케이션**을 선택합니다. **MyDbgApp**과 같은 이름을 입력하고 **확인**을 클릭합니다.

    표시되는 대화 상자의 가운데 창에서 **웹 애플리케이션**을 선택한 다음, **확인**을 클릭합니다.

    ![웹 애플리케이션 선택](../debugger/media/dbg-qs-aspnet-choose-web-app.png)
    ::: moniker-end

    **ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 후 **수정**을 선택합니다.

    Visual Studio가 프로젝트를 생성합니다.

1. 솔루션 탐색기에서 About.cshtml.cs(Pages/About.cshtml 아래)를 열고 다음 코드를 바꿉니다.

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    이 코드로 바꿉니다.

    ```csharp
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>중단점 설정

*중단점*은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타내는 표식입니다. 디버깅의 가장 기본적인 기능입니다.

1. 중단점을 설정하려면 `doWork` 함수의 왼쪽 여백을 클릭합니다(또는 코드 줄을 선택하고 **F9** 키를 누릅니다).

    ![중단점 설정](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    중단점은 여는 중괄호(`{`)의 왼쪽으로 설정되어 있습니다.

1. 이제 **F5** 키를 누릅니다(또는 **디버그 > 디버깅 시작** 선택).

1. 웹 페이지가 로드되면 웹 페이지의 맨 위에서 **정보** 링크를 클릭합니다.

    디버거가 중단점을 설정한 위치에서 일시 중지됩니다. 디버거 및 앱 실행이 일시 중지된 명령문은 노란색 화살표로 표시됩니다. `doWork` 함수 선언 뒤의 여는 중괄호(`{`)가 있는 줄은 아직 실행되지 않았습니다.

    ![중단점 도달](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > 루프 또는 재귀에 중단점이 있는 경우 또는 자주 한 단계씩 실행하는 많은 중단점이 있는 경우 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)을 사용하여 특정 조건이 충족되는 경우에만 코드가 일시 중단되도록 합니다. 이는 시간을 절약하고 재현하기 어려운 문제를 쉽게 디버그할 수 있도록 할 수 있습니다.

## <a name="navigate-code"></a>코드 탐색

디버거를 계속하도록 지시하는 다양한 명령이 있습니다. Visual Studio 2017부터 사용할 수 있는 유용한 코드 탐색 명령을 보여줍니다.

중단점에서 일시 중지하는 동안 녹색의 **실행하려면 클릭** 단추 ![실행하려면 클릭](../debugger/media/dbg-tour-run-to-click.png)이 나타날 때까지 `return c2` 명령문을 마우스로 가리킨 다음, **실행하려면 클릭** 단추를 누릅니다.

![실행하려면 클릭](../debugger/media/dbg-qs-run-to-click-aspnet.png)

앱은 실행을 계속하고, 단추를 클릭한 코드 줄에서 일시 중지합니다.

코드를 단계별로 실행하는 데 사용되는 일반적인 키보드 명령은 **F10** 및 **F11**을 포함합니다. 자세한 지침은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="inspect-variables-in-a-datatip"></a>datatip에서 변수 검사

1. 현재 코드 줄에서(노란색 실행 포인터에 의해 표시됨) 마우스로 `c2` 개체를 마우스로 가리켜 datatip을 표시합니다.

    ![datatip 보기](../debugger/media/dbg-qs-data-tip-aspnet.png)

    datatip은 `c2` 변수의 현재 값을 보여주고 이를 통해 해당 속성을 검사할 수 있습니다. 디버깅할 때 예상하지 않은 값이 표시되는 경우 이전 또는 호출하는 코드 줄에 버그가 있을 가능성이 큽니다.

2. datatip을 확장하여 `c2` 개체의 현재 속성 값을 확인합니다.

3. 코드를 실행하는 동안 `c2`의 값을 계속해서 볼 수 있도록 datatip을 고정하려면 작은 고정 아이콘을 클릭합니다. (고정된 datatip을 편리한 위치로 이동할 수 있습니다.)

## <a name="edit-code-and-continue-debugging"></a>코드를 편집하며 디버그 계속하기

디버깅 세션 중 코드에서 테스트하려는 변경을 식별하는 경우 해당 작업도 수행할 수 있습니다.

1. `OnGet` 메서드에서 `result.First.Value`의 두 번째 인스턴스를 클릭하고 `result.First.Value`를 `result.Last.Value`로 변경합니다.

1. **F10**(또는 **디버그 > 프로시저 단위 실행**)을 몇 번 눌러 디버거를 진행하고 편집된 코드를 실행합니다.

    ![편집하며 계속하기](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "편집하며 계속하기")

    **F10**은 디버거를 한 번에 하나의 명령문씩 진행하지만 단계별로 실행하는 대신 함수를 실행합니다(건너뛰는 코드가 여전히 실행됨).

편집하며 계속하기 사용 및 기능 제한에 대한 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 디버거를 시작하고, 코드를 단계별로 실행하며, 변수를 검사하는 방법을 알아보았습니다. 더 많은 정보에 대한 링크와 함께 디버거 기능에 대해 개략적으로 살펴보는 것이 좋습니다.

> [!div class="nextstepaction"]
> [디버거 소개](../debugger/debugger-feature-tour.md)
