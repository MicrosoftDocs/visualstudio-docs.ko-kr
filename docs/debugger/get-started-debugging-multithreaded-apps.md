---
title: 다중 스레드 애플리케이션을 디버그하는 방법 알아보기
description: Visual Studio에서 병렬 스택 및 병렬 조사식 창을 사용하여 디버그
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30fd29357ab8b42ea6a8baa6412f9ccf7eafed28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350513"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>다중 스레드 애플리케이션 디버깅 시작(C#, Visual Basic, C++)

Visual Studio는 다중 스레드 애플리케이션을 디버그하는 데 도움이 되는 여러 도구와 사용자 인터페이스 요소를 제공합니다. 이 자습서에서는 스레드 마커, **병렬 스택** 창, **병렬 조사식** 창, 조건부 중단점 및 필터 중단점을 사용하는 방법을 보여줍니다. 이 자습서를 완료하면 다중 스레드 애플리케이션을 디버깅하는 Visual Studio 기능을 익힐 수 있습니다.

다음 두 토픽에서는 다른 다중 스레드 디버깅 도구 사용에 대한 추가 정보를 제공합니다.

- **디버그 위치** 도구 모음 및 **스레드** 창을 사용하려면 [연습: 다중 스레드 애플리케이션 디버그](../debugger/how-to-use-the-threads-window.md)를 참조하세요.

- <xref:System.Threading.Tasks.Task>(관리 코드) 및 동시성 런타임(C++)을 사용하는 샘플은 [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)를 참조하세요. 대부분의 다중 스레드 애플리케이션 유형에 적용되는 일반적인 디버깅 팁은 해당 토픽과 이 토픽을 모두 읽어보세요.

먼저 다중 스레드 애플리케이션 프로젝트가 필요 합니다. 예를 들면 다음과 같습니다.

## <a name="create-a-multithreaded-app-project"></a>다중 스레드 앱 프로젝트 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

   ::: moniker range=">=vs-2019"

   시작 창이 열려 있지 않으면 **파일** > **시작 창**을 선택합니다.

   시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 다음으로, 언어 목록에서 **C#** , **C++** 또는 **Visual Basic**을 선택한 다음, 플랫폼 목록에서 **Windows**를 선택합니다. 

   언어 및 플랫폼 필터를 적용한 후에는 **콘솔 앱(.NET Core)** 또는 C++인 경우 **콘솔 앱**을 선택하고, **다음**을 선택합니다.

   > [!NOTE]
   > 올바른 템플릿이 표시되지 않으면 **도구** > **도구 및 기능 가져오기...** 로 이동합니다. 그러면 Visual Studio 설치 관리자가 열립니다. **.NET 데스크톱 개발*** 또는 **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

   **새 프로젝트 구성** 창의 **프로젝트 이름** 상자에 *MyThreadWalkthroughApp*을 입력합니다. 그런 다음, **만들기**를 선택합니다.

   ::: moniker-end
   ::: moniker range="vs-2017"
   메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 다음을 선택합니다.

   - C# 앱인 경우 **Visual C#** 아래에서 **Windows 데스크톱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Framework)** 을 선택합니다.
   - Visual Basic 앱인 경우 **Visual Basic** 아래에서 **Windows 데스크톱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Framework)** 을 선택합니다.
   - C++ 앱인 경우 **Visual C++** 아래에서 **Windows 데스크톱**을 선택한 다음, **Windows 콘솔 애플리케이션**을 선택합니다.

   **콘솔 앱(.NET Core)** 또는 C++인 경우 **콘솔 앱** 프로젝트 템플릿이 표시되지 않으면 **도구** > **도구 및 기능 가져오기...** 로 이동합니다. 그러면 Visual Studio 설치 관리자가 열립니다. **.NET 데스크톱 개발*** 또는 **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

   그런 다음, *MyThreadWalkthroughApp*과 같은 이름을 입력하고 **확인**을 클릭합니다.

   **확인**을 선택합니다.
   ::: moniker-end

   새 콘솔 프로젝트가 나타납니다. 프로젝트가 만들어지면 소스 파일이 나타납니다. 선택한 언어에 따라 소스 파일 이름이 *Program.cs*, *MyThreadWalkthroughApp.cpp* 또는 *Module1.vb*입니다.

1. 소스 파일에 표시되는 코드를 삭제하고, 아래에 나열된 예제 코드 중 적절한 것으로 바꿉니다.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended. " + data);
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended. " + data)
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. **파일** 메뉴에서 **모두 저장**을 선택합니다.

1. (Visual Basic만 해당) 솔루션 탐색기(오른쪽 창)에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **애플리케이션** 탭에서 **시작 개체**를 **단순**으로 변경합니다.

## <a name="debug-the-multithreaded-app"></a>다중 스레드 앱 디버그

1. 소스 코드 편집기에서 다음 코드 조각 중 하나를 찾습니다.

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. `Thread.Sleep` 또는 `std::this_thread::sleep_for` 문의 왼쪽 여백을 마우스 왼쪽 단추로 클릭하고 새로운 중단점을 삽입합니다.

    여백의 빨간색 원은 이 위치에 중단점이 설정되었음을 나타냅니다.

2. **디버그** 메뉴에서 **디버깅 시작**(**F5**)을 선택합니다.

    Visual Studio가 솔루션을 빌드하고, 디버거가 연결된 상태로 앱이 실행되기 시작하고, 앱이 중단점에서 중지됩니다.

3. 소스 코드 편집기에서 중단점이 포함된 줄을 찾습니다.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>스레드 마커 찾기  

1. 디버그 도구 모음에서 **소스의 스레드 표시** 단추 ![소스의 스레드 표시](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")를 선택합니다.

2. **F11** 키를 한 번 눌러 디버거 코드를 한 줄 진행합니다.

3. 창 왼쪽의 여백을 확인합니다. 이 줄에는 스레드 두 개가 꼬여 있는 모습의 *스레드 마커* 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")이 표시됩니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    중단점이 스레드 마커의 일부를 가릴 수 있습니다.

4. 스레드 마커에 포인터를 올려 놓습니다. 중지된 각 스레드의 이름과 스레드 ID 번호를 알려주는 DataTip이 나타납니다. 여기서는 이름이 아마도 `<noname>`일 것입니다.

5. 스레드 마커를 선택하면 바로 가기 메뉴에서 사용 가능한 옵션이 표시됩니다.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>스레드 위치 보기

**병렬 스택** 창에서 스레드 보기와 (작업 기반 프로그래밍의 경우) 작업 보기 간에 전환할 수 있으며, 각 스레드의 호출 스택 정보를 볼 수 있습니다. 이 앱에서는 스레드 보기를 사용할 수 있습니다.

1. **디버그** > **Windows** > **병렬 스택**을 선택하여 **병렬 스택** 창을 엽니다. 다음과 비슷한 내용이 표시됩니다. 정확한 정보는 각 스레드의 현재 위치, 하드웨어 및 프로그래밍 언어에 따라 달라집니다.

    ![병렬 스택 창](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    이 예제에서는 관리 코드에 대한 다음 정보가 왼쪽에서 오른쪽으로 표시됩니다.

    - 주 스레드(왼쪽)가 `Thread.Start`에서 중지되었으며, 여기서 중지 지점은 스레드 마커 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")을 표시됩니다.
    - 두 스레드가 `ServerClass.InstanceMethod`를 입력했으며, 그 중 하나는 현재 스레드(노란색 화살표)이고 다른 스레드는 `Thread.Sleep`에서 중지되었습니다.
    - 새 스레드(오른쪽)도 시작되지만, `ThreadHelper.ThreadStart`에서 중지되었습니다.

2. **병렬 스택** 창의 항목을 마우스 오른쪽 단추로 클릭하면 바로 가기 메뉴에서 사용 가능한 옵션이 표시됩니다.

    이러한 오른쪽 클릭 메뉴에서 다양한 작업을 수행할 수 있지만, 이 자습서에서는 **병렬 조사식** 창(다음 섹션)에 이러한 세부 정보를 좀 더 자세히 살펴보겠습니다.

    > [!NOTE]
    > 각 스레드에 대한 정보가 포함된 목록 보기를 보려면 **스레드** 창을 대신 사용합니다. [연습: 다중 스레드 애플리케이션 디버그](../debugger/how-to-use-the-threads-window.md)를 참조하세요.

### <a name="set-a-watch-on-a-variable"></a>변수에 조사식 설정

1. **디버그** > **Windows** > **병렬 조사식** > **병렬 조사식 1**을 선택하여 **병렬 조사식** 창을 엽니다.

2. `<Add Watch>` 텍스트(또는 4번째 열의 빈 헤더 셀)가 표시되는 셀을 선택하고 `data`를 입력합니다.

    각 스레드의 데이터 변수 값이 창에 표시됩니다.

3. `<Add Watch>` 텍스트(또는 5번째 열의 빈 헤더 셀)가 표시되는 셀을 선택하고 `count`를 입력합니다.

    각 스레드의 `count` 변수 값이 창에 표시됩니다. 이 정보가 아직 표시되지 않으면 **F11** 키를 몇 번 눌러 디버거에서 스레드 실행을 진행해 보세요.

    ![병렬 조사식](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow") 창

4. 창에 있는 행 중 하나를 마우스 오른쪽 단추로 클릭하면 사용 가능한 옵션이 표시됩니다.

### <a name="flag-and-unflag-threads"></a>스레드에 플래그 지정 및 스레드의 플래그 해제
스레드에 플래그를 지정하여 중요한 스레드를 추적하고 나머지 스레드를 무시할 수 있습니다.

1. **병렬 조사식** 창에서 **Shift** 키를 누른 상태로 여러 행을 선택합니다.

2. 마우스 오른쪽 단추로 클릭하고 **플래그**를 선택합니다.

    선택한 모든 스레드에 플래그가 지정됩니다. 이제 플래그가 지정된 스레드만 표시하도록 필터링할 수 있습니다.

3. **병렬 조사식** 창에서 **플래그가 지정된 스레드만 표시** 단추 ![플래그가 지정된 스레드 표시](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")를 선택합니다.

    플래그가 지정된 스레드만 목록에 나타납니다.

    > [!TIP]
    > 일부 스레드에 플래그를 지정한 후에는 코드 편집기에서 코드 줄을 마우스 오른쪽 단추로 클릭하고 **플래그 지정된 스레드를 커서까지 실행**을 선택할 수 있습니다. 플래그가 지정된 모든 스레드가 도달할 코드를 선택해야 합니다. Visual Studio는 선택한 코드 줄에서 스레드를 일시 중지하므로, [스레드를 중지 및 재개](#bkmk_freeze)하여 실행 순서를 쉽게 제어할 수 있습니다.

4. **플래그가 지정된 스레드만 표시** 단추를 다시 선택하여 **모든 스레드 표시** 모드로 돌아갑니다.

5. 스레드의 플래그를 해제하려면 **병렬 조사식** 창에서 플래그가 지정된 하나 이상의 스레드를 마우스 오른쪽 단추로 클릭하고 **플래그 해제**를 선택합니다.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> 스레드 실행 중지 및 재개

> [!TIP]
> 스레드를 중지 및 재개(일시 중단 및 다시 시작)하여 스레드가 작업을 수행하는 순서를 제어할 수 있습니다. 이를 통해 교착 상태 및 경합 상태와 같은 동시성 문제를 해결할 수 있습니다.

1. **병렬 조사식** 창에서 모든 행을 선택한 상태로 마우스 오른쪽 단추를 클릭하고 **중지**를 선택합니다.

    두 번째 열에는 각 행의 일시 중지 아이콘이 표시됩니다. 일시 중지 아이콘은 스레드가 중지되었음을 나타냅니다.

2. 행을 하나만 선택하여 나머지 행을 선택 취소합니다.

3. 행을 마우스 오른쪽 단추로 클릭하고 **재개**를 선택합니다.

    일시 중지 아이콘이 이 행에서 사라집니다. 스레드가 더 이상 중지 상태가 아니라는 의미입니다.

4. 코드 편집기로 전환하여 **F11** 키를 누릅니다. 중지되지 않은 스레드만 실행됩니다.

    앱에서 새 스레드 몇 개를 인스턴스화할 수도 있습니다. 새 스레드는 플래그가 해제되며 중지되지 않습니다.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> 조건부 중단점을 사용하여 단일 스레드 팔로우

디버거에서 단일 스레드 실행을 팔로우하면 도움이 될 수 있습니다. 팔로우하는 방법 중 하나는 관심 없는 스레드를 중지하는 것입니다. 특정 버그를 재현해야 하는 경우처럼 다른 스레드를 중지하지 않고 단일 스레드를 팔로우해야 하는 경우가 있습니다. 다른 스레드를 중지하지 않고 스레드를 팔로우하려면 관심이 있는 스레드 외에는 코드를 중단하지 않아야 합니다. 이렇게 하려면 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)을 설정하면 됩니다.

스레드 이름 또는 스레드 ID와 같은 여러 조건에 중단점을 설정할 수 있습니다. 각 스레드에 고유하다는 것을 알고 있는 데이터에 조건을 설정하면 도움이 될 수 있습니다. 이것은 특정 스레드보다 특정 데이터 값에 관심이 더 많은 일반적인 디버깅 시나리오입니다.

1. 앞에서 만든 중단점을 마우스 오른쪽 단추로 클릭하고 **조건**을 선택합니다.

2. **중단점 설정** 창에서 조건식으로 `data == 5`를 입력합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 특정 스레드에 더 관심이 있으면 조건에 스레드 이름 또는 스레드 ID를 사용합니다. **중단점 설정** 창에서 이 작업을 수행하려면 **조건식** 대신 **필터**를 선택하고 필터 팁을 따릅니다. 디버거를 다시 시작할 때 스레드 ID가 변경되므로, 앱 코드에서 스레드 이름을 지정할 수 있습니다.

3. **중단점 설정** 창을 닫습니다.

4. 다시 시작 ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 선택하여 디버깅 세션을 다시 시작합니다.

    데이터 변수 값이 5인 스레드에서 코드가 중단됩니다. **병렬 조사식** 창에서 현재 디버거 컨텍스트를 나타내는 노란색 화살표를 찾습니다.

5. 이제 코드를 프로시저 단위로 실행(**F10**)하고 한 단계씩 코드를 실행(**F11**)한 다음, 단일 스레드 실행을 팔로우할 수 있습니다.

    중단점 조건이 스레드에 대해 고유하고 디버거가 다른 스레드의 다른 중단점에 도달하지 않는 한(다른 중단점을 사용하지 않도록 설정해야 할 수도 있음), 다른 스레드로 전환하지 않고 코드를 프로시저 단위로 실행하고 코드를 한 단계씩 실행할 수 있습니다.

    > [!NOTE]
    > 디버거를 진행하면 모든 스레드가 실행됩니다. 그러나 다른 스레드 중 하나가 중단점에 도달하지 않으면 디버거가 다른 스레드의 코드를 중단하지 않습니다.

## <a name="see-also"></a>참조

- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [방법: 병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md)
- [방법: 병렬 조사식 창 사용](../debugger/how-to-use-the-parallel-watch-window.md)