---
title: 디버거 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202351"
---
# <a name="getting-started-with-the-debugger"></a>디버거 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거는 모든 언어에서 쉽게 사용할 수 있습니다. 여기서는 간단한 C# 프로그램을 디버그하는 방법을 보여 주겠지만 C++ 및 JavaScript와 같은 다른 언어의 코드에 동일한 단계를 적용할 수 있습니다.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> 기본 c # 프로젝트 디버그  
 간단한 c # 콘솔 응용 프로그램 (**파일/새로 만들기/프로젝트**, **Visual c #** 을 차례로 선택 하 고 **콘솔 응용 프로그램**선택)부터 시작 해 보겠습니다. 이전에 Visual Studio로 작업 한 적이 없는 경우 [연습: 간단한 응용 프로그램 만들기](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)를 참조 하세요. **Main** 메서드는 정수 변수에 1을 10 번 추가 하 고 결과를 콘솔에 출력 합니다.  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 **디버그** 구성에서이 코드를 빌드합니다. 이 구성은 기본적으로 설정되어 있습니다. 구성에 대 한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조 하세요.  
  
 **디버그/디버깅 시작** 을 클릭 하거나 도구 모음에서 **시작** 또는 **F5 키**를 눌러 디버거에서이 코드를 실행 합니다. 애플리케이션이 거의 즉시 종료되므로 콘솔 창에 무엇인가 인쇄되었는지 여부는 사실 알 수 없습니다.  
  
 중단점을 설정한 다음 미리 단계별로 실행하면 콘솔 창을 보기에 충분한 시간 동안 실행을 중지할 수 있습니다. 중단점을 설정 하려면 줄에 커서를 놓고 `Console.WriteLine` **디버그/새 중단점/함수 중단점**을 클릭 하거나 같은 줄에서 왼쪽 여백을 클릭 하면 됩니다. 중단점은 다음과 같은 모습입니다.  
  
 ![중단점 설정](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 중단점에 대 한 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)을 참조 하세요.  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> 변수 검사  
 디버깅에는 특정 지점에서 원하는 값을 포함 하지 않는 변수를 찾는 경우가 종종 있습니다. 변수를 검사할 수 있는 몇 가지 방법이 나와 있습니다.  
  
 다시 디버그를 시작합니다. `Console.WriteLine` 코드가 실행되기 전에 실행이 중지됩니다. 미리 단계별로 실행 되도록 할 수 있습니다 ( **디버그/프로시저 단위** 실행 또는 **F10**키 클릭). 이 경우 한 **단계씩 코드 실행** (**F11**)을 선택 하 고 동일한 결과를 얻을 수 있습니다. 이러한 차이점은 나중에 설명 하겠습니다. 메서드의 마지막 중괄호로 묶인 선이 노란색으로 변해야 합니다. 콘솔 창을 봅니다. **10**이 표시 되어야 합니다.  
  
 **Testint** 변수를 마우스로 가리켜 데이터 팁의 현재 값을 볼 수 있습니다.  
  
 ![DBG&#95;기본 사항&#95;데이터&#95;팁](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 코드 창 바로 아래에 **자동**, **지역**및 **조사식** 창이 표시 됩니다. 이러한 창에는 실행 당시의 변수에 대한 현재 값이 표시됩니다. **자동** 및 **지역** 창에는 모두 값이 **10**인 **testint** 가 표시 됩니다.  
  
 ![디버그할 때의 자동 창](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 이러한 창에 대 한 자세한 내용은 [자동 및 지역 창](../debugger/autos-and-locals-windows.md)을 참조 하세요.  
  
 프로그램을 진행함에 따라 변수 값이 어떻게 변경되는지 살펴보겠습니다. 줄에 중단점을 설정 `testInt += 1;` 하 고 디버깅을 다시 시작 합니다. **지역** 및 **자동** 창에서 **testint** 는 **0**이 고 **i** 는 **1**입니다. 디버깅을 계속할 때 (**디버그/계속**또는 도구 모음에서 **계속** 또는 **F5**) **testint** 의 값이 **1**, **2**등으로 변경 된 것을 볼 수 있습니다. 이러한 변경 내용을 확인 하려면 중단점 (**디버그/중단점 설정/해제**또는 여백에서 클릭)을 제거 하 고 디버깅을 계속 합니다. 모든 중단점을 제거 하려면 **디버그/모든 중단점 삭제**를 클릭 하거나 **CTRL + SHIFT + F9**를 클릭 하 고 **모든 중단점을 제거**하 시겠습니까? 라는 대화 상자에서 **예** 를 클릭 합니다.  
  
## <a name="stepping-into-and-over-function-calls"></a>함수 호출을 한 단계씩 코드 실행 및 프로시저 단위 실행  
 디버거 (한 단계씩 코드**실행)에서**코드를 실행 하거나 디버거에서 함수를 건너뛰고 (**프로시저 단위**실행) 코드를 실행 하 여 더 관심이 있는 코드를 빠르게 가져올 수 있습니다 (함수 코드는 여전히 실행 됨). 동일한 디버깅 세션에서 두 메서드 간을 전환할 수 있습니다.  
  
 한 단계씩 **코드** 실행 및 **프로시저 단위 실행**간의 차이점을 보려면 다른 메서드에 의해 호출 되는 메서드를 추가 해야 합니다. C# 애플리케이션에 메서드를 추가하고 Main 메서드에서 호출합니다. 코드는 다음과 비슷합니다.  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Main 메서드에서 `Method1();` 호출에 중단점을 설정하고 디버그를 시작합니다. 실행이 중단 되 면 **디버그/한 단계씩 코드** 실행을 클릭 하거나 도구 모음에서 한 단계씩 **코드** 실행 또는 **F11**키를 누릅니다. Method1()의 첫 번째 중괄호에서 실행이 다시 중단됩니다.  
  
 ![한 단계씩 코드 실행](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 디버깅을 중지 하 고 다시 시작 하 고, 중단점에서 실행이 중단 되 면 **디버그/프로시저 단위** 실행 (또는 도구 모음에서 **프로시저 단위** 실행 또는 **F10**)을 클릭 합니다. 실행이 `Console.WriteLine("end");`에서 다시 중단됩니다.  
  
 디버거를 사용 하 여 코드를 탐색 하는 방법에 대해 자세히 알아보려면 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)을 참조 하세요.
