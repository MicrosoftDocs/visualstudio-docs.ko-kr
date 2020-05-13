---
title: 관리 코드 디버그 | Microsoft Docs
description: Visual Studio 디버거를 사용하여 C# 또는 Visual Basic 디버그
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e5495bb1f531db00d43e04cce9f5f771c88cc1a7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679195"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>빠른 시작: Visual Studio 디버거를 사용하여 C# 또는 Visual Basic으로 디버그

Visual Studio 디버거는 앱을 디버그하도록 돕는 여러 가지 강력한 기능을 제공합니다. 이 항목에는 기본 기능 중 일부에 대해 알아보는 빠른 방법을 제공합니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **콘솔**을 입력하고 **템플릿**을 선택한 다음, **새 콘솔 앱(.NET Core) 프로젝트 만들기**를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에 **.NET Core**를 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. **MyDbgApp**과 같은 이름을 입력하고 **확인**을 클릭합니다.
    ::: moniker-end

     **콘솔 앱(.NET Core)** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **.NET 데스크톱 개발** 및 **.NET Core** 워크로드를 선택한 다음, **수정**을 선택합니다.

    Visual Studio가 프로젝트를 생성합니다.

1. *Program.cs* 또는 *Module1.vb*에서 다음 코드로 바꿉니다.

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    이 코드로 바꿉니다.

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic에서는 시작 개체가 `Sub Main`으로 설정되었는지 확인합니다(**속성 &gt; 애플리케이션 &gt; 시작 개체**).

## <a name="set-a-breakpoint"></a>중단점 설정

*중단점*은 변수의 값, 메모리의 동작 또는 코드 분기의 실행 여부를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타내는 표식입니다. 디버깅의 가장 기본적인 기능입니다.

1. 중단점을 설정하려면 `doWork` 함수 호출의 왼쪽 여백을 클릭합니다(또는 코드 줄을 선택하고 **F9** 키를 누릅니다).

    ![중단점 설정](../debugger/media/dbg-qs-set-breakpoint-csharp.png "중단점 설정")

2. 이제 **F5** 키를 누릅니다(또는 **디버그 > 디버깅 시작** 선택).

    ![중단점 도달](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "중단점 도달")

    디버거가 중단점을 설정한 위치에서 일시 중지됩니다. 디버거 및 앱 실행이 일시 중지된 명령문은 노란색 화살표로 표시됩니다. `doWork` 함수 호출이 있는 줄이 아직 실행되지 않았습니다.

    > [!TIP]
    > 루프 또는 재귀에 중단점이 있는 경우 또는 자주 한 단계씩 실행하는 많은 중단점이 있는 경우 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)을 사용하여 특정 조건이 충족되는 경우에만 코드가 일시 중단되도록 합니다. 조건부 중단점은 시간을 절약하고 재현하기 어려운 문제를 쉽게 디버그할 수 있도록 할 수 있습니다.

## <a name="navigate-code"></a>코드 탐색

디버거를 계속하도록 지시하는 다양한 명령이 있습니다. Visual Studio 2017부터 사용할 수 있는 유용한 코드 탐색 명령을 보여줍니다.

중단점에서 일시 중지하는 동안 녹색의 **실행하려면 클릭** 단추 ![실행하려면 클릭](../debugger/media/dbg-tour-run-to-click.png "RunToClick")이 나타날 때까지 `c1.AddLast(20)` 명령문을 마우스로 가리킨 다음, **실행하려면 클릭** 단추를 누릅니다.

![실행하려면 클릭](../debugger/media/dbg-qs-run-to-click-csharp.png "실행하려면 클릭")

앱은 실행, `doWork` 호출을 계속하고, 단추를 클릭한 코드 줄에서 일시 중지합니다.

코드를 단계별로 실행하는 데 사용되는 일반적인 키보드 명령은 **F10** 및 **F11**을 포함합니다. 자세한 지침은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="inspect-variables-in-a-datatip"></a>datatip에서 변수 검사

1. 현재 코드 줄에서(노란색 실행 포인터에 의해 표시됨) 마우스로 `c1` 개체를 마우스로 가리켜 datatip을 표시합니다.

    ![datatip 보기](../debugger/media/dbg-qs-data-tip-csharp.png "datatip 보기")

    datatip은 `c1` 변수의 현재 값을 보여주고 이를 통해 해당 속성을 검사할 수 있습니다. 디버깅할 때 예상하지 않은 값이 표시되는 경우 이전 또는 호출하는 코드 줄에 버그가 있을 가능성이 큽니다.

2. datatip을 확장하여 `c1` 개체의 현재 속성 값을 확인합니다.

3. 코드를 실행하는 동안 `c1`의 값을 계속해서 볼 수 있도록 datatip을 고정하려면 작은 고정 아이콘을 클릭합니다. (고정된 datatip을 편리한 위치로 이동할 수 있습니다.)

## <a name="edit-code-and-continue-debugging"></a>코드를 편집하며 디버그 계속하기

디버깅 세션 중 코드에서 테스트하려는 변경을 식별하는 경우 해당 작업도 수행할 수 있습니다.

1. `c2.First.Value`의 두 번째 인스턴스를 클릭하고 `c2.First.Value`를 `c2.Last.Value`로 변경합니다.

2. **F10**(또는 **디버그 > 프로시저 단위 실행**)을 몇 번 눌러 디버거를 진행하고 편집된 코드를 실행합니다.

    ![편집하며 계속하기](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "편집하며 계속하기")

    **F10**은 디버거를 한 번에 하나의 명령문씩 진행하지만 단계별로 실행하는 대신 함수를 실행합니다(건너뛰는 코드가 여전히 실행됨).

편집하며 계속하기 사용 및 기능 제한에 대한 자세한 내용은 [편집하며 계속하기](../debugger/edit-and-continue.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 자습서에서는 디버거를 시작하고, 코드를 단계별로 실행하며, 변수를 검사하는 방법을 알아보았습니다. 더 많은 정보에 대한 링크와 함께 디버거 기능에 대해 개략적으로 살펴보는 것이 좋습니다.

> [!div class="nextstepaction"]
> [디버거 소개](../debugger/debugger-feature-tour.md)
