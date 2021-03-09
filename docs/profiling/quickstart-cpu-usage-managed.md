---
title: CPU 사용량 현황 데이터 분석(C#, Visual Basic)
description: CPU 사용량 진단 도구를 사용하여 C# 및 Visual Basic에서 앱 성능 측정
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7fc8eeccdb020d07ff48965d9eb3d5df1dafa7da
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683545"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>빠른 시작: Visual Studio에서 CPU 사용량 현황 데이터 분석(C#, Visual Basic)

Visual Studio는 애플리케이션에서 성능 문제를 분석할 수 있도록 여러 강력한 기능을 제공합니다. 이 항목에는 기본 기능 중 일부에 대해 알아보는 빠른 방법을 제공합니다. 여기에서는 높은 CPU 사용량으로 인한 성능 병목 상태를 식별하는 도구를 살펴봅니다. 진단 도구는 ASP.NET을 포함한 Visual Studio의 .NET 개발 및 네이티브/C++ 개발에 사용할 수 있습니다.

진단 허브에서는 진단 세션을 실행하고 관리할 수 있는 여러 가지 다른 옵션을 제공합니다. 여기서 설명한 **CPU 사용량** 도구로 필요한 데이터를 얻지 못할 경우 [다른 프로파일링 도구](../profiling/profiling-feature-tour.md)로 유용한 다른 종류의 정보를 얻을 수 있습니다. 많은 경우 메모리, UI 렌더링 또는 네트워크 요청 시간 등 CPU가 아닌 곳에서 애플리케이션의 성능 병목 현상이 발생할 수 있습니다. 성능 프로파일러는 이러한 종류의 데이터를 기록 및 분석하기 위한 다른 여러 옵션을 제공합니다. 디버거에 통합된 또 다른 프로파일링 도구인 [PerfTips](../profiling/perftips.md)를 사용해도 코드를 단계별로 실행하여 특정 함수 또는 코드 블록이 완료되는 데 소요되는 시간을 확인할 수 있습니다.

Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다. Windows 7 이상에서 사후 평가 도구인 [성능 프로파일러](../profiling/profiling-feature-tour.md)를 사용할 수 있습니다.

## <a name="create-a-project"></a>프로젝트 만들기

1. Visual Studio를 열고 프로젝트를 만듭니다.

   ::: moniker range="vs-2017"
   상단 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

   **새 프로젝트** 대화 상자의 왼쪽 창에서 **C#** 또는 **Visual Basic** 을 확장한 후 **.NET Core** 를 선택합니다. 가운데 창에서 **콘솔 앱(.NET Core)** 을 선택합니다. 그런 다음, 프로젝트 이름을 *MyProfilerApp* 으로 지정합니다.

   **콘솔 앱(.NET Core)** 템플릿 프로젝트가 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Open Visual Studio 설치 관리자** 링크를 선택합니다. Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음 **수정** 을 선택합니다.
   ::: moniker-end
   ::: moniker range="vs-2019"
   시작 창이 열려 있지 않으면 **파일** > **시작 창** 을 선택합니다.

   시작 창에서 **새 프로젝트 만들기** 를 선택합니다.

   **새 프로젝트 만들기** 창에서 검색 상자에 *콘솔* 을 입력합니다. 그런 다음, 언어 목록에서 **C#** 또는 **Visual Basic** 을 선택한 후 플랫폼 목록에서 **Windows** 를 선택합니다.

   언어 및 플랫폼 필터를 적용한 후 .NET Core용 **콘솔 앱** 템플릿을 선택한 후, **다음** 을 선택합니다.

   > [!NOTE]
   > **콘솔 앱** 템플릿이 표시되지 않으면 **새 프로젝트를 만들기** 창에서 설치할 수 있습니다. **원하는 항목을 찾을 수 없나요?** 메시지에서 **추가 도구 및 기능 설치** 링크를 선택합니다. 그런 다음, Visual Studio 설치 관리자에서 **.NET Core 플랫폼 간 개발** 워크로드를 선택합니다.

   **새 프로젝트 구성** 창의 **프로젝트 이름** 상자에 *MyProfilerApp* 을 입력합니다. 그리고 **다음** 을 선택합니다.

   권장되는 대상 프레임워크(.NET Core 3.1) 또는 .NET 5를 선택한 후 **만들기** 를 선택합니다.

   ::: moniker-end

   Visual Studio에서 새 프로젝트를 엽니다.

2. *Program.cs* 를 열고 모든 코드를 다음 코드로 바꿉니다.

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic에서는 시작 개체가 `Sub Main`으로 설정되었는지 확인합니다(**속성** > **애플리케이션** > **시작 개체**).

## <a name="step-1-collect-profiling-data"></a>1단계: 프로파일링 데이터 수집

1. 먼저 `Main` 함수의 이 코드 줄에서 앱에 중단점을 설정합니다.

    `for (int i = 0; i < 200; i++)`

    또는 Visual Basic의 경우

    `For i As Integer = 0 To 199`

    코드 줄의 왼쪽 여백을 클릭하여 중단점을 설정합니다.

2. 다음으로 `Main` 함수 끝의 닫는 중괄호에서 두 번째 중단점을 설정합니다.

     ![프로파일링을 위한 중단점 설정](../profiling/media/quickstart-cpu-usage-breakpoints.png "프로파일링을 위한 중단점 설정")

    두 개의 중단점을 설정하여, 분석하려는 코드 부분으로 데이터 수집을 제한할 수 있습니다.

3. 사용자가 닫지 않았다면 **진단 도구** 창이 이미 표시되어 있을 것입니다. 창을 다시 표시하려면 **디버그** > **Windows** > **진단 도구 표시** 를 클릭합니다.

4. **디버그** > **디버깅 시작** 을 클릭합니다(또는 도구 모음의 **시작** 또는 **F5** 키 누름).

     앱 로드가 완료되면 진단 도구의 **요약** 보기가 나타납니다.

5. 디버거가 일시 중지되면 **CPU 프로필 기록** 을 선택한 다음 **CPU 사용량** 탭을 열어 CPU 사용량 데이터 수집을 사용하도록 설정합니다.

     ![진단 도구에서 CPU 프로파일을 사용하도록 설정](../profiling/media/quickstart-cpu-usage-summary.png "진단 도구에서 CPU 프로파일을 사용하도록 설정")

     데이터 수집을 사용하는 경우 기록 단추에 빨간색 원이 표시됩니다.

     **CPU 프로필 기록** 을 선택하면 Visual Studio가 함수와 함수 실행 소요 시간을 기록하기 시작하며 샘플링 세션의 특정 부분에 초점을 맞출 수 있는 타임라인 그래프도 제공합니다. 애플리케이션이 중단점에서 중단되었을 때 이 수집 데이터를 보기만 하면 됩니다.

6. 두 번째 중단점까지 앱을 실행하려면 **F5** 키를 누릅니다.

     이제 구체적으로 두 개의 중단점 사이에서 실행되는 코드 영역에 대한 애플리케이션의 성능 데이터가 제공됩니다.

     프로파일러는 스레드 데이터 준비를 시작합니다. 끝날 때까지 기다립니다.

     CPU 사용량 도구는 **CPU 사용량** 탭에 보고서를 표시합니다.

     이 시점에서 데이터 분석을 시작할 수 있습니다.

## <a name="step-2-analyze-cpu-usage-data"></a>2단계: CPU 사용량 데이터 분석

CPU 사용량 아래의 함수 목록을 검사하고, 가장 많은 작업을 수행하는 함수를 확인한 다음, 각 함수를 자세히 살펴보는 방식으로 데이터 분석을 시작하는 것이 좋습니다.

1. 함수 목록에서 가장 많은 작업을 수행하는 함수를 검사합니다.

     ![진단 도구 CPU 사용량 탭](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > 함수는 가장 많은 작업을 수행하는 것부터 나열됩니다(호출 순서가 아님). 따라서 가장 오래 실행된 함수를 빠르게 식별할 수 있습니다.

2. 함수 목록에서 `ServerClass::GetNumber` 함수를 두 번 클릭합니다.

    함수를 두 번 클릭하면 **호출자/호출 수신자** 뷰가 왼쪽 창에 열립니다.

    ![진단 도구 호출자/호출 수신자 뷰](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    이 뷰에서는 선택한 함수가 제목 및 **현재 함수** 상자에 표시됩니다(이 예제의 경우 `GetNumber`). 현재 함수를 호출한 함수는 **호출 함수** 아래 왼쪽에 표시되고, 현재 함수에 의해 호출된 함수는 오른쪽의 **호출된 함수** 상자에 표시됩니다. 두 상자 중 하나를 선택하여 현재 함수를 변경할 수 있습니다.

    이 뷰는 함수를 완료하는 데 걸린 총 시간(ms) 및 전체 앱 실행 시간의 백분율을 표시합니다.

    **함수 본문** 은 또한 호출 함수 및 호출된 함수에 사용된 시간을 제외하고 함수 본문에 사용된 총 시간(및 시간의 백분율)을 표시합니다. 이 그림에서는 2863ms 중 2856ms가 함수 본문에 사용되었고 남은 시간(20ms 미만)은 이 함수에 의해 호출된 외부 코드에 사용되었습니다. 실제 값은 환경에 따라 달라집니다.

    > [!TIP]
    > **함수 본문** 의 값이 높으면 함수 자체 내에서 성능 병목 현상이 있는 것일 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [메모리 사용 분석](../profiling/memory-usage.md)으로 성능 병목 상태를 확인합니다.
- [CPU 사용량 분석](../profiling/cpu-usage.md)은 CPU 사용량 도구에 대한 더 상세한 정보를 제공합니다.
- 디버거를 연결하지 않고 또는 실행 중인 앱을 대상으로 지정하여 CPU 사용량을 분석합니다. 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)의 [디버깅을 사용하지 않고 프로파일링 데이터 수집](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 프로파일링](../profiling/index.yml)
- [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)
