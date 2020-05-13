---
title: 다중 스레드 응용 프로그램 디버깅에 대 한 자세한 정보
description: Visual Studio의 병렬 스택 및 병렬 조사식 창을 사용 하 여 디버그
ms.custom: ''
ms.date: 02/14/2020
ms.topic: conceptual
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
ms.openlocfilehash: f280a93022342fd9ca4dcae5cdac1de919fe1657
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416409"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>다중 스레드 응용 프로그램 디버깅 시작C#(, Visual Basic C++,)

Visual Studio는 다중 스레드 응용 프로그램을 디버깅 하는 데 도움이 되는 여러 도구 및 사용자 인터페이스 요소를 제공 합니다. 이 자습서에서는 스레드 마커, **병렬 스택** 창, **병렬 조사식** 창, 조건부 중단점 및 필터 중단점을 사용 하는 방법을 보여 줍니다. 이 자습서를 완료 하면 다중 스레드 응용 프로그램 디버깅을 위한 Visual Studio 기능을 익힐 수 있습니다.

이 두 항목에서는 다른 다중 스레드 디버깅 도구 사용에 대 한 추가 정보를 제공 합니다.

- **디버그 위치** 도구 모음과 **스레드** 창을 사용 하려면 [연습: 다중 스레드 응용 프로그램 디버그](../debugger/how-to-use-the-threads-window.md)를 참조 하세요.

- 사용 하는 샘플에 대 한 <xref:System.Threading.Tasks.Task> (관리 코드) (c + +), 동시성 런타임에서 참조 및 [연습: 병렬 애플리케이션 디버그](../debugger/walkthrough-debugging-a-parallel-application.md). 대부분의 다중 스레드 응용 프로그램 유형에 적용 되는 일반적인 디버깅 팁은 해당 항목과이 항목을 모두 읽습니다.

먼저 다중 스레드 응용 프로그램 프로젝트가 필요 합니다. 예제는 다음과 같습니다.

## <a name="create-a-multithreaded-app-project"></a>다중 스레드 응용 프로그램 프로젝트 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

   ::: moniker range=">=vs-2019"

   시작 창이 열려 있지 않으면 **파일** > **시작 창**을 선택합니다.

   시작 창에서 **새 프로젝트 만들기**를 선택합니다.

   **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔*을 입력합니다. 그런 다음 언어 **C#** 목록 **C++** 에서, 또는 **Visual Basic** 를 선택 하 고 플랫폼 목록에서 **Windows** 를 선택 합니다. 

   언어 및 플랫폼 필터를 적용 한 후 **콘솔 앱 (.net Core)** 또는 C++ **콘솔 앱** 템플릿을 선택 하 고 **다음**을 선택 합니다.

   > [!NOTE]
   > 올바른 템플릿이 표시 되지 않으면 **도구** > 도구 **및 기능 가져오기**...로 이동 하 여 Visual Studio 설치 관리자를 엽니다. **.NET 데스크톱 개발*** 또는 **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

   **새 프로젝트 구성** 창에서 **프로젝트 이름** 상자에 *MyThreadWalkthroughApp* 를 입력 하거나 입력 합니다. 그런 다음, **만들기**를 선택합니다.

   ::: moniker-end
   ::: moniker range="vs-2017"
   메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 다음을 선택 합니다.

   - 앱의 경우 **시각적 C#개체** 에서 **Windows 데스크톱**을 선택한 다음 가운데 창에서 **콘솔 앱 (.NET Framework)** 을 선택 합니다. C#
   - Visual Basic 앱의 경우 **Visual Basic**에서 **Windows 데스크톱**을 선택한 다음 가운데 창에서 **콘솔 앱 (.NET Framework)** 을 선택 합니다.
   - 앱의 경우 **시각적 개체 C++** 에서 **windows 데스크톱**을 선택한 다음 **windows 콘솔 응용 프로그램**을 선택 합니다. C++

   **콘솔 앱 (.Net Core)** 또는 C++ **콘솔 앱** 프로젝트 템플릿에 대 한가 표시 되지 않으면 도구 > 도구 **및 기능 가져오기** **...로 이동** 하 여 Visual Studio 설치 관리자를 엽니다. **.NET 데스크톱 개발*** 또는 **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

   그런 다음 *MyThreadWalkthroughApp* 와 같은 이름을 입력 하 고 **확인**을 클릭 합니다.

   **확인**을 선택합니다.
   ::: moniker-end

   새 콘솔 프로젝트가 나타납니다. 프로젝트를 만든 후에 소스 파일이 표시 됩니다. 선택한 언어에 따라 소스 파일을 *Program.cs*, *MyThreadWalkthroughApp*또는 *Module1*이라고 합니다.

1. 소스 파일에 표시 되는 코드를 삭제 하 고 아래에서 적절 한 예제 코드 목록으로 바꿉니다.

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

1. (Visual Basic에만 해당) 솔루션 탐색기 (오른쪽 창)에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **응용 프로그램** 탭에서 **시작 개체** 를 **단순**으로 변경 합니다.

## <a name="debug-the-multithreaded-app"></a>다중 스레드 응용 프로그램 디버그

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

1. `Thread.Sleep` 또는 `std::this_thread::sleep_for` 문의 왼쪽 여백에서 마우스 왼쪽 단추를 클릭 하 여 새 중단점을 삽입 합니다.

    여백에서 빨간색 원은 중단점이이 위치에 설정 되어 있음을 나타냅니다.

2. **디버그** 메뉴에서 **디버깅 시작** (**F5**)을 선택 합니다.

    Visual Studio는 솔루션을 빌드하고 디버거가 연결 된 상태에서 실행 되기 시작 하면 앱이 중단점에서 중지 합니다.

3. 소스 코드 편집기에서 중단점이 포함 된 줄을 찾습니다.

### <a name="ShowThreadsInSource"></a>스레드 마커 검색  

1. 디버그 도구 모음에서 **소스의 스레드 표시** 단추를 ![소스의 스레드 표시](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")로 선택 합니다.

2. **F11** 키를 한 번 눌러 디버거를 한 줄의 코드 줄로 이동 합니다.

3. 창 왼쪽의 여백을 확인합니다. 이 줄에는 두 개의 꼬아진 스레드와 유사한 *스레드 마커* 아이콘 ![스레드 마커가](../debugger/media/dbg-thread-marker.png "ThreadMarker") 표시 됩니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    스레드 표식은 중단점에 의해 부분적으로 숨겨진 것일 수 있습니다.

4. 스레드 마커에 포인터를 올려 놓습니다. 중지 된 각 스레드의 이름과 스레드 ID 번호를 알려 주는 DataTip이 표시 됩니다. 이 경우 이름이 `<noname>`될 수 있습니다.

5. 스레드 마커를 선택 하 여 바로 가기 메뉴에서 사용할 수 있는 옵션을 표시 합니다.

### <a name="ParallelStacks"></a>스레드 위치 보기

**병렬 스택** 창에서 스레드 뷰와 (작업 기반 프로그래밍) 작업 뷰의 사이를 전환 하 고 각 스레드에 대 한 호출 스택 정보를 볼 수 있습니다. 이 앱에서는 스레드 뷰를 사용할 수 있습니다.

1. **디버그** > **Windows** > **병렬 스택**을 선택 하 여 **병렬 스택** 창을 엽니다. 다음과 유사한 항목이 표시 됩니다. 정확한 정보는 각 스레드, 하드웨어 및 프로그래밍 언어의 현재 위치에 따라 달라 집니다.

    ![병렬 스택 창](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    이 예제에서는 왼쪽에서 오른쪽으로 관리 코드에 대 한 다음 정보가 표시 됩니다.

    - 주 스레드 (왼쪽)가 `Thread.Start`에서 중지 되었습니다. 여기서 중지 지점은 스레드 마커 아이콘 ![스레드 표식](../debugger/media/dbg-thread-marker.png "ThreadMarker")으로 표시 됩니다.
    - 두 스레드가 `ServerClass.InstanceMethod`를 입력 했으며, 그 중 하나는 현재 스레드 (노란색 화살표)이 고 다른 스레드는 `Thread.Sleep`에서 중지 되었습니다.
    - 새 스레드 (오른쪽)도 시작 되지만 `ThreadHelper.ThreadStart`에서 중지 됩니다.

2. **병렬 스택** 창의 항목을 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴에서 사용할 수 있는 옵션을 확인 합니다.

    이러한 오른쪽 클릭 메뉴에서 다양 한 작업을 수행할 수 있지만이 자습서에서는 **병렬 조사식** 창 (다음 섹션)에 이러한 세부 정보를 더 많이 표시 합니다.

    > [!NOTE]
    > 각 스레드에 대 한 정보가 포함 된 목록 뷰를 보려면 **스레드** 창을 대신 사용 합니다. [연습: 다중 스레드 응용 프로그램 디버그를](../debugger/how-to-use-the-threads-window.md)참조 하세요.

### <a name="set-a-watch-on-a-variable"></a>변수에 조사식 설정

1. **디버그** > **Windows** ** > 병렬 조사식 > ** **병렬 조사식 1**을 선택 하 여 **병렬 조사식** 창을 엽니다.

2. `<Add Watch>` 텍스트 (또는 네 번째 열의 빈 머리글 셀)가 표시 되는 셀을 선택 하 고 `data`을 입력 합니다.

    각 스레드에 대 한 데이터 변수 값이 창에 표시 됩니다.

3. `<Add Watch>` 텍스트 (또는 5 번째 열의 빈 머리글 셀)가 표시 되는 셀을 선택 하 고 `count`을 입력 합니다.

    각 스레드에 대 한 `count` 변수의 값이 창에 표시 됩니다. 이 많은 정보가 아직 표시 되지 않으면 **F11** 키를 눌러 디버거에서 스레드의 실행을 진행 합니다.

    ![병렬 조사식 창](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 창에 있는 행 중 하나를 마우스 오른쪽 단추로 클릭 하면 사용 가능한 옵션이 표시 됩니다.

### <a name="flag-and-unflag-threads"></a>스레드에 플래그 지정 및 스레드의 플래그 해제
스레드에 플래그를 지정 하 여 중요 한 스레드를 추적 하 고 다른 스레드를 무시할 수 있습니다.

1. **병렬 조사식** 창에서 **shift** 키를 누른 채 여러 행을 선택 합니다.

2. 마우스 오른쪽 단추를 클릭 하 고 **플래그**를 선택 합니다.

    선택한 모든 스레드에 플래그가 지정 됩니다. 이제 플래그가 지정 된 스레드만 표시 하도록 필터링 할 수 있습니다.

3. **병렬 조사식** 창에서 플래그가 지정 된 스레드만 **표시** 단추를 선택 하 여 ![플래그가 지정 된 스레드를 표시](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")합니다.

    플래그가 지정 된 스레드만 목록에 표시 됩니다.

    > [!TIP]
    > 일부 스레드에 플래그를 지정 하면 코드 편집기에서 코드 줄을 마우스 오른쪽 단추로 클릭 하 고 **커서에 플래그가 지정 된 스레드 실행을**선택할 수 있습니다. 플래그가 지정 된 모든 스레드가 도달할 코드를 선택 해야 합니다. Visual Studio는 선택한 코드 줄에서 스레드를 일시 중지 하 여 [스레드를 고정 및 재개](#bkmk_freeze)하 여 실행 순서를 보다 쉽게 제어할 수 있습니다.

4. **플래그가 지정 된 스레드만 표시** 단추를 다시 선택 하 여 **모든 스레드 모드 표시** 로 다시 전환 합니다.

5. 스레드의 플래그를 해제 하려면 **병렬 조사식** 창에서 하나 이상의 플래그가 지정 된 스레드를 마우스 오른쪽 단추로 클릭 하 고 **플래그**해제를 선택 합니다.

### <a name="bkmk_freeze"></a>스레드 실행 중지 및 재개

> [!TIP]
> 스레드를 중지 및 재개 (일시 중단 및 다시 시작) 하 여 스레드가 작업을 수행 하는 순서를 제어할 수 있습니다. 이를 통해 교착 상태 및 경합 상태와 같은 동시성 문제를 해결할 수 있습니다.

1. **병렬 조사식** 창에서 모든 행을 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **중지**를 선택 합니다.

    두 번째 열에는 각 행에 대해 일시 중지 아이콘이 표시 됩니다. 일시 중지 아이콘은 스레드가 고정 되어 있음을 나타냅니다.

2. 행을 하나만 선택 하 여 다른 모든 행의 선택을 취소 합니다.

3. 행을 마우스 오른쪽 단추로 클릭 하 고 **재개**를 선택 합니다.

    일시 중지 아이콘은이 행에서 사라지고 스레드가 더 이상 고정 되어 있지 않음을 나타냅니다.

4. 코드 편집기로 전환 하 고 **F11**키를 누릅니다. 고정 되지 않은 스레드만 실행 됩니다.

    앱에서 몇 가지 새 스레드를 인스턴스화할 수도 있습니다. 모든 새 스레드는 플래그가 해제 되며 고정 되지 않습니다.

### <a name="bkmk_follow_a_thread"></a>조건부 중단점이 있는 단일 스레드 팔 로우

디버거의 단일 스레드 실행을 따르는 것이 유용할 수 있습니다. 이 작업을 수행 하는 한 가지 방법은 관심 없는 스레드를 고정 하는 것입니다. 일부 시나리오에서는 특정 버그를 재현 하기 위해 다른 스레드를 동결 하지 않고 단일 스레드를 수행 해야 할 수 있습니다. 다른 스레드를 동결 하지 않고 스레드를 따르려면 관심이 있는 스레드를 제외 하 고 코드를 중단 하지 않아야 합니다. [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)을 설정 하 여이 작업을 수행할 수 있습니다.

스레드 이름 또는 스레드 ID와 같은 다른 조건에 중단점을 설정할 수 있습니다. 각 스레드에 고유한 것으로 알고 있는 데이터에 대 한 조건을 설정 하는 것이 유용할 수 있습니다. 이 시나리오는 특정 스레드 보다 특정 데이터 값에 더 관심이 있는 일반적인 디버깅 시나리오입니다.

1. 이전에 만든 중단점을 마우스 오른쪽 단추로 클릭 하 고 **조건**을 선택 합니다.

2. **중단점 설정** 창에서 조건 식에 대 한 `data == 5`를 입력 합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 특정 스레드에 더 관심이 있으면 조건에 스레드 이름 또는 스레드 ID를 사용 합니다. **중단점 설정** 창에서이 작업을 수행 하려면 **조건식**대신 **필터** 를 선택 하 고 필터 팁을 따릅니다. 디버거를 다시 시작할 때 스레드 Id가 변경 되므로 앱 코드에서 스레드의 이름을 지정할 수 있습니다.

3. **중단점 설정** 창을 닫습니다.

4. ![응용](../debugger/media/dbg-tour-restart.png "RestartApp") 프로그램 다시 시작 단추를 선택 하 여 디버깅 세션을 다시 시작 합니다.

    데이터 변수의 값이 5 인 스레드에서 코드를 중단 합니다. **병렬 조사식** 창에서 현재 디버거 컨텍스트를 나타내는 노란색 화살표를 찾습니다.

5. 이제 코드를 프로시저 단위로 실행 (**F10**) 하 고 한 단계씩 코드 실행 (**F11**) 한 다음 단일 스레드 실행을 따라갈 수 있습니다.

    중단점 조건이 스레드에 대해 고유 하 고 디버거가 다른 스레드의 다른 중단점에 도달 하지 않는 한 (사용 하지 않도록 설정 해야 할 수 있음), 다른 스레드로 전환 하지 않고 코드를 프로시저 단위로 실행 하 고 코드를 한 단계씩 실행 할 수 있습니다.

    > [!NOTE]
    > 디버거를 진행 하면 모든 스레드가 실행 됩니다. 그러나 다른 스레드 중 하나가 중단점에 도달 하지 않으면 디버거는 다른 스레드의 코드를 중단 하지 않습니다.

## <a name="see-also"></a>참고 항목

- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [방법: 병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md)
- [방법: 병렬 조사식 창 사용](../debugger/how-to-use-the-parallel-watch-window.md)