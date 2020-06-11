---
title: '자습서: C# 및 C++ 코드 디버그(혼합 모드)'
description: 혼합 모드 디버깅을 사용하여 .NET Core 또는 .NET Framework 앱에서 네이티브 DLL을 디버그하는 방법 알아보기
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 9f3fd94f8c294dce81bc69011e7d6f5fdd505325
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182640"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>자습서: 동일한 디버깅 세션에서 C# 및 C++ 디버그

Visual Studio를 사용하면 혼합 모드 디버깅이라는 디버깅 세션에서 하나를 초과하는 디버거 형식을 사용하도록 설정할 수 있습니다. 이 자습서에서는 단일 디버깅 세션에서 관리 및 네이티브 코드를 디버그하는 방법을 알아봅니다.

이 자습서에서는 관리 앱에서 네이티브 코드를 디버그하는 방법을 보여주지만 [네이티브 앱에서 관리 코드를 디버그](../debugger/how-to-debug-in-mixed-mode.md)할 수도 있습니다. 디버거는 [Python 및 네이티브 코드](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) 디버깅 및 ASP.NET과 같은 앱 형식에서 스크립트 디버거 사용과 같은 다른 유형의 혼합 모드 디버깅을 지원합니다.

이 자습서에서 다음을 수행합니다.

> [!div class="checklist"]
> * 간단한 네이티브 DLL 만들기
> * DLL을 호출하기 위해 간단한 .NET Core 또는 .NET Framework 앱 만들기
> * 혼합 모드 디버깅 구성
> * 디버거 시작
> * 관리 앱에서 중단점에 도달
> * 네이티브 코드 한 단계씩 실행

## <a name="prerequisites"></a>사전 요구 사항

다음 워크로드를 사용하려면 Visual Studio가 설치되어 있어야 합니다.
- **C++를 사용한 데스크톱 개발**
- 만들려는 앱 형식에 따라 **.NET 데스크톱 개발** 또는 **.NET Core 플랫폼 간 개발**을 사용합니다.

Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 평가판을 설치합니다.

Visual Studio를 설치했지만 필요한 워크로드가 없는 경우 Visual Studio **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Studio 설치 관리자 열기**를 선택합니다. Visual Studio 설치 관리자에서 필요한 워크로드 및 **수정**을 차례로 선택합니다.

## <a name="create-a-simple-native-dll"></a>간단한 네이티브 DLL 만들기

**DLL 프로젝트용 파일을 만들려면:**

1. Visual Studio를 열고 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **빈 프로젝트**를 입력하고 **템플릿**을 선택한 다음, C++용 **빈 프로젝트**를 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다. 그런 다음, **Mixed_Mode_Debugging**과 같은 이름을 입력하고 **만들기**를 클릭합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C++** 아래에 **기타**를 선택한 다음, 가운데 창에서 **빈 프로젝트**를 선택합니다. 그런 다음, **Mixed_Mode_Debugging**과 같은 이름을 입력하고 **확인**을 클릭합니다.
    ::: moniker-end

    **빈 프로젝트** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. Visual Studio 설치 관리자가 시작됩니다. **C++를 사용한 데스크톱 개발** 워크로드를 선택한 다음, **수정** 단추를 선택합니다.

    Visual Studio가 프로젝트를 생성합니다.

1. **솔루션 탐색기**에서 **원본 파일**을 선택한 다음, **프로젝트** > **새 항목 추가**를 선택합니다. 또는 **원본 파일**을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **새 항목** 대화 상자에서 **C++ 파일(.cpp)** 을 선택합니다. **이름** 필드에 **Mixed_Mode.cpp**를 입력한 다음, **추가**를 선택합니다.

    Visual Studio에서는 **솔루션 탐색기**에 새 C++ 파일을 추가합니다.

1. 다음 코드를 *Mixed_Mode.cpp*에 복사합니다.

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. **솔루션 탐색기**에서 **헤더 파일**을 선택한 다음, **프로젝트** > **새 항목 추가**를 선택합니다. 또는 **헤더 파일**을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **새 항목** 대화 상자에서 **헤더 파일(.h)** 을 선택합니다. **이름** 필드에 **Mixed_Mode.h**를 입력한 다음, **추가**를 선택합니다.

   Visual Studio에서는 **솔루션 탐색기**에 새 헤더 파일을 추가합니다.

1. 다음 코드를 *Mixed_Mode.h*에 복사합니다.

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. **파일** > **모두 저장**을 선택하거나 **Ctrl**+**Shift**+**S**를 눌러 파일을 저장합니다.

**DLL 프로젝트를 구성 및 빌드합니다.**

1. Visual Studio 도구 모음에서 **디버그** 구성 및 **x86** 또는 **x64** 플랫폼을 선택합니다. 호출 앱이 항상 64비트 모드로 실행되는 .NET Core인 경우 플랫폼으로 **x64**를 선택합니다.

1. **솔루션 탐색기**에서 **Mixed_Mode_Debugging** 프로젝트 노드 및 **속성** 아이콘을 차례로 선택하거나, 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. **속성** 창 맨 위에서 **구성**이 **활성(디버그)** 로 설정되고 **플랫폼**이 도구 모음에서 설정한 것과 동일한 플랫폼 즉, **x64** 또는 **Win32** x86 플랫폼인지 확인합니다.

   > [!IMPORTANT]
   > 플랫폼을 **x86**에서 **x64**로 또는 반대로 전환하는 경우 새 플랫폼의 속성을 다시 구성해야 합니다.

1. 왼쪽 창의 **구성 속성**에서 **링커** > **고급**을 선택하고, **진입점 없음** 옆에 있는 드롭다운 목록에서 **아니오**를 선택합니다. **아니오**로 변경해야 하는 경우 **적용**을 선택합니다.

1. **구성 속성**에서 **일반**을 선택하고 **구성 유형** 옆에 있는 드롭다운 목록에서 **동적 라이브러리(.dll)** 를 선택합니다. **적용** 및 **확인**을 차례로 선택합니다.

   ![네이티브 DLL로 전환](../debugger/media/mixed-mode-set-as-native-dll.png)

1. **솔루션 탐색기**에서 프로젝트를 선택한 다음, **빌드** > **솔루션 빌드**를 선택하고, **F7** 키를 누르거나 프로젝트를 마우스 오른쪽 단추로 클릭하여 **빌드**를 선택합니다.

   프로젝트가 오류 없이 빌드되어야 합니다.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL을 호출하는 간단한 관리 앱 만들기

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    **Esc** 키를 눌러 시작 창을 닫습니다. **Ctrl + Q**를 입력하여 검색 상자를 열고 **콘솔**을 입력하고 **템플릿**을 선택한 다음, **콘솔 앱(.NET Core)** 또는 C#용 **콘솔 앱(.NET Framework)** 을 선택합니다. 표시되는 대화 상자에서 **만들기**를 선택합니다.

    그런 다음, **Mixed_Mode_Calling_App**과 같은 이름을 입력하고 **만들기**를 클릭합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에 **Windows 데스크톱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Framework)** 또는 **콘솔 앱(.NET Core)** 을 선택합니다.

    그런 다음, **Mixed_Mode_Calling_App**과 같은 이름을 입력하고 **확인**을 클릭합니다.
    ::: moniker-end

    **콘솔 앱** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **.NET 데스크톱 개발** 워크로드를 선택한 다음 **수정**을 선택합니다.

    > [!NOTE]
    > 기존 C++ 솔루션에 새 관리형 프로젝트를 추가할 수도 있습니다. 혼합 모드 디버깅 작업을 더 어렵게 만들기 위해 새 솔루션에서 프로젝트를 만듭니다.

   Visual Studio에서는 빈 프로젝트를 만들고 **솔루션 탐색기**에 해당 프로젝트를 표시합니다.

1. *Program.cs*의 모든 코드를 다음 코드로 바꿉니다.

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. 새 코드에서 `[DllImport]`의 파일 경로를 방금 만든 *Mixed_Mode_Debugging.dll*의 파일 경로로 바꿉니다. 힌트에 대한 코드 주석을 참조하세요. *사용자 이름* 자리 표시자를 바꿔야 합니다.

1. **파일** > **Program.cs 저장**을 선택하거나 **Ctrl**+**S**를 눌러 파일을 저장합니다.

## <a name="configure-mixed-mode-debugging"></a>혼합 모드 디버깅 구성

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>.NET Framework 앱에 대한 혼합 모드 디버깅을 구성하려면

1. **솔루션 탐색기**에서 **Mixed_Mode_Calling_App** 프로젝트 노드 및 **속성** 아이콘을 차례로 선택하거나, 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. 왼쪽 창에서 **디버깅**을 선택하고 **네이티브 코드 디버깅 사용** 확인란을 선택한 다음, 속성 페이지를 닫아 변경 내용을 저장합니다.

    ![혼합된 모드 디버깅 사용](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>.NET Core 앱에 대한 혼합 모드 디버깅을 구성하려면

Visual Studio 2017부터 시작하는 대부분의 Visual Studio 버전에서는 프로젝트 속성 대신 *launchSettings.json* 파일을 사용하여 .NET Core 앱에서 네이티브 코드에 대한 혼합 모드 디버깅을 사용하도록 설정합니다. 이 기능에 대한 UI 업데이트를 추적하려면 이 [GitHub 문제](https://github.com/dotnet/project-system/issues/1125)를 참조하세요.

1. **솔루션 탐색기**에서 **속성**을 확장하고 *launchSettings.json* 파일을 엽니다.

   >[!NOTE]
   >기본적으로 *launchSettings.json*은 *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*에 있습니다. *launchSettings.json*이 존재하지 않는 경우 **솔루션 탐색기**에서 **Mixed_Mode_Calling_App** 프로젝트 및 **속성** 아이콘을 차례로 선택하거나, 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **디버그** 탭에서 임시로 변경하고 프로젝트를 빌드합니다. 이렇게 *launchSettings.json* 파일을 만듭니다. **디버그** 탭에서 변경한 내용을 취소합니다.

1. *launchsettings.json* 파일에서 다음 줄을 추가합니다.

    ```csharp
    "nativeDebugging": true
    ```

    완료된 파일은 다음 예제와 같이 표시됩니다.

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>중단점 설정 및 디버깅 시작

1. C# 프로젝트에서 *Program.cs*를 엽니다. 맨 왼쪽 여백을 클릭하여 줄을 선택하고 **F9**를 누르거나, 줄을 마우스 오른쪽 단추로 클릭하고 **중단점** > **중단점 삽입**을 선택하여 다음과 같은 코드 줄에서 중단점을 설정합니다.

    ```csharp
    int result = Multiply(7, 7);
    ```

    중단점을 설정하는 경우 왼쪽 여백에 빨간색 원이 나타납니다.

1. **F5** 키를 누르고 Visual Studio 도구 모음에서 녹색 화살표를 선택하거나, **디버그** > **디버깅 시작**을 선택하여 디버깅을 시작합니다.

   디버거가 설정한 중단점에서 일시 중지됩니다. 노란색 화살표는 디버거가 현재 일시 중지된 경우를 나타냅니다.

## <a name="step-in-and-out-of-native-code"></a>네이티브 코드에 들어가기 및 나오기

1. 디버깅이 관리 앱에서 일시 중지되는 동안 **F11** 키를 누르거나 **디버그** > **한 단계씩 코드 실행**을 선택합니다.

   디버거가 일시 중지된 경우 *Mixed_Mode.h* 네이티브 헤더 파일이 열리고 노란색 화살표가 표시됩니다.

   ![네이티브 코드 한 단계씩 실행](../debugger/media/mixed-mode-step-into-native-code.png)

1. 이제 중단점을 설정 및 도달하고 네이티브 또는 관리 코드에서 변수를 검사할 수 있습니다.

   - 해당 값을 확인하려면 소스 코드의 변수 위로 마우스를 가져갑니다.

   - **자동** 창 및 **지역** 창에서 변수 및 해당 값을 확인합니다.

   - 디버거에서 일시 중지되는 동안 **조사식** 창 및 **호출 스택** 창을 사용할 수 있습니다.

1. **F11** 키를 눌러 디버거를 한 줄씩 진행합니다.

1. **Shift**+**F11** 키를 누르거나 **디버그** > **나오기**를 선택하여 관리 앱에서 실행을 계속하다가 다시 일시 중지합니다.

1. **F5** 키를 누르거나 녹색 화살표를 선택하여 앱을 계속 디버깅합니다.

지금까지 혼합 모드 디버깅에 대한 자습서를 모두 마쳤습니다.

## <a name="next-step"></a>다음 단계

이 자습서에서는 혼합 모드 디버깅을 사용하여 관리 앱에서 네이티브 코드를 디버그하는 방법을 알아보았습니다. 다른 디버거 기능에 대한 개요는 다음을 참조하세요.

> [!div class="nextstepaction"]
> [디버거 소개](../debugger/debugger-feature-tour.md)
