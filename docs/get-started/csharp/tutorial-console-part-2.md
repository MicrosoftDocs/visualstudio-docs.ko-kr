---
title: '자습서: 간단한 C# 콘솔 앱 확장'
description: Visual Studio에서 C# 콘솔 앱을 개발하는 방법을 단계별로 알아봅니다.
ms.custom: get-started
ms.date: 07/09/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e5552cc3d84eb0dd2a44943c36ddaa60c827ceb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909322"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>자습서: 간단한 C# 콘솔 앱 확장

이 자습서에서는 첫 부분에서 만든 콘솔 앱을 Visual Studio를 사용해 확장하는 방법을 알아봅니다. 여러 프로젝트를 관리하고 타사 패키지를 참조하는 등의 일상적인 개발 작업에 필요한 Visual Studio의 일부 기능에 대해 알아봅니다.

이 시리즈의 [첫 부분](tutorial-console.md)을 완료했다면 Calculator 콘솔 앱이 이미 있습니다.  1부를 건너뛰려면 먼저 GitHub 리포지토리에서 프로젝트를 열어 시작하면 됩니다. C# Calculator 앱은 [vs-tutorial-samples 리포지토리](https://github.com/MicrosoftDocs/vs-tutorial-samples)에 있습니다. [자습서: 리포지토리에서 프로젝트 열기](../tutorial-open-project-from-repo.md)의 단계에 따라 시작하세요.

## <a name="add-a-new-project"></a>새 프로젝트 추가

실제 코드에는 솔루션에서 함께 작업하는 많은 프로젝트가 포함되어 있습니다. 이제 Calculator 앱에 다른 프로젝트를 추가해 보겠습니다. 이 프로젝트는 Calculator 함수 일부를 제공하는 클래스 라이브러리입니다.

1. Visual Studio에서 최상위 메뉴 명령 **File** > **Add** > **New Project** 사용하여 새 프로젝트를 추가할 수 있습니다. 하지만 기존 프로젝트 이름(“프로젝트 노드”라고 함)을 마우스 오른쪽 단추로 클릭하고 프로젝트의 바로 가기 메뉴(상황에 맞는 메뉴)를 열 수도 있습니다. 이 바로 가기 메뉴에는 프로젝트에 기능을 추가하는 여러 방법이 있습니다. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트** 를 선택합니다.

1. C# 프로젝트 템플릿 **클래스 라이브러리(.NET Standard)** 를 선택합니다.

   ![클래스 라이브러리 프로젝트 템플릿 선택 스크린샷](media/vs-2019/calculator2-add-project-dark.png)

1. 프로젝트 이름 **CalculatorLibrary** 를 입력하고 **만들기** 를 선택합니다. Visual Studio에서 새 프로젝트를 만들어 솔루션에 추가합니다.

   ![CalculatorLibrary 클래스 라이브러리 프로젝트가 추가된 솔루션 탐색기의 스크린샷](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1.cs* 를 사용하는 대신 파일 이름을 **CalculatorLibrary.cs** 로 바꿉니다. **솔루션 탐색기** 에서 이 이름을 클릭하여 이름을 바꾸거나, 이름을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기** 를 선택하거나, **F2** 키를 누르면 됩니다.

   파일에서 `Class1` 참조의 이름을 바꿀지 묻는 메시지가 나타날 수도 있습니다. 이후 단계에서 코드를 바꿀 예정이므로 여기서 어떤 선택을 해도 괜찮습니다.

1. 첫 번째 프로젝트가 새 클래스 라이브러리에서 제공된 API를 사용할 수 있도록 이제 프로젝트 참조를 추가해야 합니다.  첫 번째 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 참조 추가** 를 선택합니다.

   ![프로젝트 참조 추가 메뉴 항목의 스크린샷](media/vs-2019/calculator2-add-project-reference-dark.png)

   **참조 관리자** 대화 상자가 나타납니다. 이 대화 상자에서는 다른 프로젝트에 참조를 추가할 수 있고 프로젝트에 필요한 어셈블리 및 COM DLL을 추가할 수도 있습니다.

   ![참조 관리자 대화 상자의 스크린샷](media/vs-2019/calculator2-ref-manager-dark.png)

1. **참조 관리자** 대화 상자에서 **CalculatorLibrary** 프로젝트의 확인란을 선택하고 **확인** 을 선택합니다.  프로젝트 참조는 **솔루션 탐색기** 의 **프로젝트** 노드 아래에 나타납니다.

   ![프로젝트 참조가 있는 솔루션 탐색기의 스크린샷](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program.cs* 에서 `Calculator` 클래스와 모든 해당 코드를 선택하고 **CTRL+X** 를 눌러 Program.cs에서 자릅니다. 그리고 **CalculatorLibrary**(*CalculatorLibrary.cs*)에서 코드를 `CalculatorLibrary` 네임스페이스에 붙여넣습니다. 그런 다음, Calculator 클래스 `public`이 코드를 라이브러리 외부에 노출하도록 합니다. 이제 *CalculatorLibrary.cs* 의 코드는 다음 코드와 유사합니다.

   ```csharp
   using System;

    namespace CalculatorLibrary
    {
        public class Calculator
        {
            public static double DoOperation(double num1, double num2, string op)
            {
                double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

                // Use a switch statement to do the math.
                switch (op)
                {
                    case "a":
                        result = num1 + num2;
                        break;
                    case "s":
                        result = num1 - num2;
                        break;
                    case "m":
                        result = num1 * num2;
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor.
                        if (num2 != 0)
                        {
                            result = num1 / num2;
                        }
                        break;
                    // Return text for an incorrect option entry.
                    default:
                        break;
                }
                return result;
            }
        }
    }
   ```

1. 첫 번째 프로젝트에 참조가 있지만 Calculator.DoOperation 호출이 해결되지 않는다는 오류가 표시됩니다. 이는 CalculatorLibrary가 차이 네임스페이스에 있어서 정규화된 참조에 대한 `CalculatorLibrary` 네임스페이스를 추가하기 때문입니다.

   ```csharp
   result = CalculatorLibrary.Calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   대신 파일의 시작 부분에 using 지시문을 추가합니다.

   ```csharp
   using CalculatorLibrary;
   ```

   이렇게 변경하면 호출 사이트에서 CalculatorLibrary 네임스페이스를 제거할 수 있지만, 이제 모호성이 생깁니다. 즉, `Calculator`가 CalculatorLibrary의 클래스인지 아니면 Calculator가 네임스페이스인지가 모호합니다.  모호성을 해결하려면 네임스페이스 이름을 `CalculatorProgram`으로 바꿉니다.

   ```csharp
   namespace CalculatorProgram
   ```

## <a name="reference-net-libraries-write-to-a-log"></a>.NET 라이브러리 참조: 로그에 쓰기

1. 이제 모든 작업의 로그를 추가하고 텍스트 파일에 쓰려 한다고 가정하겠습니다. .NET `Trace` 클래스는 다음과 같은 기능을 제공합니다. (기본 인쇄 디버깅 기술에도 유용합니다.)  Trace 클래스는 System.Diagnostics에 있습니다. using 지시문을 추가하여 시작하려면 `StreamWriter` 같은 System.IO 클래스가 필요합니다.

   ```csharp
   using System.IO;
   using System.Diagnostics;
   ```

1. Trace 클래스가 사용되는 방법을 고려할 때, 파일 스트림과 연결된 클래스 참조를 유지해야 합니다. 즉, Calculator는 개체로 더 잘 작동하므로 생성자를 추가해 보겠습니다.

   ```csharp
   public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculator.log");
            Trace.Listeners.Add(new TextWriterTraceListener(logFile));
            Trace.AutoFlush = true;
            Trace.WriteLine("Starting Calculator Log");
            Trace.WriteLine(String.Format("Started {0}", System.DateTime.Now.ToString()));
        }

    public double DoOperation(double num1, double num2, string op)
        {
   ```

1. 그리고 정적 `DoOperation` 메서드를 멤버 메서드로 변경해야 합니다.  로그를 위한 각 계산에 출력도 추가하겠습니다. 그러면 DoOperation이 다음 코드와 같이 보입니다.

   ```csharp
   public double DoOperation(double num1, double num2, string op)
   {
        double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.

        // Use a switch statement to do the math.
        switch (op)
        {
            case "a":
                result = num1 + num2;
                Trace.WriteLine(String.Format("{0} + {1} = {2}", num1, num2, result));
                break;
            case "s":
                result = num1 - num2;
                Trace.WriteLine(String.Format("{0} - {1} = {2}", num1, num2, result));
                break;
            case "m":
                result = num1 * num2;
                Trace.WriteLine(String.Format("{0} * {1} = {2}", num1, num2, result));
                break;
            case "d":
                // Ask the user to enter a non-zero divisor.
                if (num2 != 0)
                {
                    result = num1 / num2;
                    Trace.WriteLine(String.Format("{0} / {1} = {2}", num1, num2, result));
                }
                    break;
            // Return text for an incorrect option entry.
            default:
                break;
        }
        return result;
    }
   ```

1. 이제 Program.cs에서 정적 호출이 빨간색 표시선으로 플래그 지정됩니다. 이 문제를 해결하려면 while 루프 바로 앞에 다음 줄을 추가하여 `calculator` 변수를 만듭니다.

   ```csharp
   Calculator calculator = new Calculator();
   ```

   다음과 같이 `DoOperation`에 대한 호출 사이트를 수정합니다.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

1. 프로그램을 다시 실행하고 완료되면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **파일 탐색기의 폴더 열기** 를 선택한 다음 파일 탐색기에서 출력 폴더로 이동합니다. 이 폴더는 *bin/Debug/netcoreapp3.1* 일 수도 있습니다. *calculator.log* 파일을 엽니다.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>NuGet 패키지 추가: JSON 파일에 쓰기

1. 이제 개체 데이터를 저장하는 데 많이 사용되는 이식 가능한 형식인 JSON 형식으로 작업을 출력하려 한다고 가정하겠습니다. 이 기능을 구현하려면 NuGet 패키지인 Newtonsoft.Json을 참조해야 합니다. NuGet 패키지는 .NET 클래스 라이브러리를 배포하는 주요 수단입니다. **솔루션 탐색기** 에서 CalculatorLibrary 프로젝트에 대한 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리** 를 선택합니다.

   ![바로 가기 메뉴의 NuGet 패키지 관리 스크린샷](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet 패키지 관리자가 열립니다.

   ![NuGet 패키지 관리자 스크린샷](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Newtonsoft.Json 패키지를 검색하고 **설치** 를 선택합니다.

   ![Newtonsoft NuGet 패키지 정보의 스크린샷](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   패키지가 다운로드되어 프로젝트에 추가되고 **솔루션 탐색기** 의 참조 노드에 새 항목이 표시됩니다.

1. *CalculatorLibrary.cs* 의 시작 부분에 System.IO 및 Newtonsoft.Json 패키지에 대한 using 지시문을 추가합니다.

   ```csharp
   using Newtonsoft.Json;
   ```

1. 이제 Calculator의 생성자를 다음 코드로 바꾸고 JsonWriter 멤버 개체를 만듭니다.

   ```csharp
        JsonWriter writer;

        public Calculator()
        {
            StreamWriter logFile = File.CreateText("calculatorlog.json");
            logFile.AutoFlush = true;
            writer = new JsonTextWriter(logFile);
            writer.Formatting = Formatting.Indented;
            writer.WriteStartObject();
            writer.WritePropertyName("Operations");
            writer.WriteStartArray();
        }
   ```

1. `DoOperation` 메서드를 수정하여 JSON 작성기 코드를 추가합니다.

   ```csharp
        public double DoOperation(double num1, double num2, string op)
        {
            double result = double.NaN; // Default value is "not-a-number" which we use if an operation, such as division, could result in an error.
            writer.WriteStartObject();
            writer.WritePropertyName("Operand1");
            writer.WriteValue(num1);
            writer.WritePropertyName("Operand2");
            writer.WriteValue(num2);
            writer.WritePropertyName("Operation");
            // Use a switch statement to do the math.
            switch (op)
            {
                case "a":
                    result = num1 + num2;
                    writer.WriteValue("Add");
                    break;
                case "s":
                    result = num1 - num2;
                    writer.WriteValue("Subtract");
                    break;
                case "m":
                    result = num1 * num2;
                    writer.WriteValue("Multiply");
                    break;
                case "d":
                    // Ask the user to enter a non-zero divisor.
                    if (num2 != 0)
                    {
                        result = num1 / num2;
                        writer.WriteValue("Divide");
                    }
                    break;
                // Return text for an incorrect option entry.
                default:
                    break;
            }
            writer.WritePropertyName("Result");
            writer.WriteValue(result);
            writer.WriteEndObject();

            return result;
        }
   ```

1. 사용자가 작업 데이터 입력을 완료하면 JSON 구문을 마치는 메서드를 추가해야 합니다.

   ```csharp
    public void Finish()
    {
        writer.WriteEndArray();
        writer.WriteEndObject();
        writer.Close();
    }
   ```

1. 그리고 *Program.cs* 에서 끝에 완료 호출을 추가합니다.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. 앱을 빌드하고 실행한 후 완료되면 몇 가지 작업을 입력한 후 ‘n’ 명령을 사용하여 앱을 제대로 닫습니다.  이제 calculatorlog.json 파일을 열면 다음과 같은 내용이 표시됩니다.

   ```json
   {
    "Operations": [
        {
        "Operand1": 2.0,
        "Operand2": 3.0,
        "Operation": "Add",
        "Result": 5.0
        },
        {
        "Operand1": 3.0,
        "Operand2": 4.0,
        "Operation": "Multiply",
        "Result": 12.0
        }
    ]
   }
   ```

## <a name="debug-set-and-hit-a-breakpoint"></a>디버깅: 중단점 설정 및 적중

Visual Studio 디버거는 코드를 단계별로 실행하여 프로그래밍 실수가 있는 정확한 지점을 찾는 데 사용할 수 있는 강력한 도구입니다. 그런 다음 코드에서 무엇을 수정해야 하는지 파악할 수 있습니다. Visual Studio에서는 프로그램을 계속 실행할 수 있도록 임시 변경을 수행할 수 있습니다.

1. *Program.cs* 에서 다음 코드의 왼쪽에 있는 여백을 클릭하거나, 바로 가기 메뉴를 열고 **중단점** > **중단점 삽입** 을 선택하거나, **F9** 키를 누릅니다.

   ```csharp
   result = calculator.DoOperation(cleanNum1, cleanNum2, op);
   ```

   표시되는 빨간색 원은 중단점을 나타냅니다. 중단점을 사용하여 앱을 일시 중지하고 코드를 검사할 수 있습니다. 코드에서 어떤 실행 줄에도 중단점을 설정할 수 있습니다.

   ![중단점 설정 스크린샷](media/vs-2019/calculator-2-debug-set-breakpoint.png)

1. 앱을 빌드하고 실행합니다.

1. 실행 중인 앱에서 계산을 위해 일부 값을 입력합니다.

   - 첫 번째 숫자에 **8** 을 입력합니다.
   - 두 번째 숫자에 **0** 을 입력합니다.
   - 연산자의 경우에는 약간의 즐거움을 위해 **d** 를 입력하겠습니다.

   앱 중단점을 만든 위치에서 일시 중지됩니다. 그러면 코드가 강조 표시되고 왼쪽에 노란색 포인터가 표시됩니다. 강조 표시된 코드는 아직 실행되지 않은 것입니다.

   ![중단점 적중 스크린샷](media/vs-2019/calculator-2-debug-hit-breakpoint.png)

   이제 앱이 일시 중지된 상태에서 애플리케이션 상태를 검사할 수 있습니다.

## <a name="debug-view-variables"></a>디버깅: 변수 보기

1. 강조 표시된 코드에서 `cleanNum1` 및 `op` 같은 변수 위로 마우스를 가져갑니다. DataTips에 표시되는 이러한 변수의 현재 값(각각`8`, `d`)을 볼 수 있습니다.

   ![DataTip 보기 스크린샷](media/vs-2019/calculator-2-debug-view-datatip.png)

   디버그할 때 변수에 필요한 값이 들어있는지 확인하는 것이 문제를 해결하는 데 중요한 경우가 많습니다.

2. 아래쪽 창에서 **지역** 창을 확인합니다. (창이 닫혀 있는 경우 **디버그** > **창** > **지역** 을 선택하여 엽니다.)

   지역 창에서 현재 범위에 있는 각 변수를 해당 값 및 형식과 함께 볼 수 있습니다.

   ![지역 창의 스크린샷](media/vs-2019/calculator-2-debug-locals-window.png)

3. **자동** 창을 확인합니다.

   자동 창은 **지역** 창과 유사하지만 앱이 일시 중지된 현재 코드 줄 바로 앞과 뒤에 있는 변수를 보여 줍니다.

   다음으로, 디버거에서 코드를 문 단위로 실행합니다. 이를 단계별 실행이라고 합니다.

## <a name="debug-step-through-code"></a>디버깅: 단계별 코드 실행

1. **F11** 키(또는 **디버그** > **한 단계씩 코드 실행**)를 누릅니다.

   한 단계씩 코드 실행 명령을 사용하면 앱은 현재 문을 실행하고 다음 실행 문(일반적으로 다음 코드 줄)으로 이동합니다. 왼쪽의 노란색 포인터는 항상 현재 문을 나타냅니다.

   ![한 단계씩 코드 실행 명령의 스크린샷](media/vs-2019/calculator-2-debug-step-into.png)

   방금 `Calculator` 클래스에서 `DoOperation` 메서드를 단계별로 실행했습니다.

1. 프로그램 흐름을 계층적으로 보려면 **호출 스택** 창을 확인합니다. (창이 닫혀 있는 경우 **디버그** > **창** > **호출 스택** 을 선택합니다.)

   ![호출 스택의 스크린샷](media/vs-2019/calculator-2-debug-call-stack.png)

   이 보기에는 현재 메서드 `Calculator.DoOperation`에 노란색 포인터가 표시되어 있고, 두 번째 행에는 *Program.cs* 의 `Main` 메서드에서 이 메서드를 호출한 함수가 표시되어 있습니다. **호출 스택** 창에는 메서드와 함수가 호출되는 순서가 표시됩니다. 또한 이 창의 바로 가기 메뉴에서 **소스 코드로 이동** 등 많은 디버거 기능에 액세스할 수 있습니다.

1. **F10** 키(또는 **디버그** > **프로시저 단위 실행**)를 앱이 `switch` 문에서 일시 중지될 때까지 여러 번 누릅니다.

   ```csharp
   switch (op)
   {
   ```

   프로시저 단위 실행 명령은 현재 문이 함수를 호출하는 경우 디버거가 호출된 함수에서 코드를 실행하고 함수가 반환될 때까지 실행을 일시 중단하지 않는다는 점을 제외하면 한 단계씩 코드 실행 명령과 비슷합니다. 프로시저 단위 실행은 특정 함수에 관심이 없는 경우 코드를 탐색하는 더 빠른 방법입니다.

1. 다음 코드 줄에서 앱이 일시 중지되도록 **F10** 키를 한 번 더 누릅니다.

   ```csharp
   if (num2 != 0)
   {
   ```

   이 코드는 0으로 나누기 사례를 검사합니다. 앱이 계속 실행될 경우 일반 예외(오류)를 throw하지만, 이 버그를 고려하고 콘솔에서 실제 반환된 값 확인과 같이 다른 작업을 수행하려는 경우를 가정해 보겠습니다. 한 가지 옵션은 편집하며 계속하기라는 디버거 기능을 사용하여 코드를 변경한 다음 디버깅을 계속하는 것입니다. 그러나 여기서는 실행 흐름을 일시적으로 수정하는 다른 트릭을 보여줄 것입니다.

## <a name="debug-test-a-temporary-change"></a>디버깅: 임시 변경 내용 테스트

1. 현재 `if (num2 != 0)` 문에서 일시 중지된 노란색 포인터를 선택하여 다음 문으로 끌어 옵니다.

   ```csharp
   result = num1 / num2;
   ```

   이 작업을 수행하면 앱이 `if` 문을 완전히 건너뛰어 0으로 나눌 때 발생하는 결과를 확인할 수 있습니다.

1. **F10** 키를 눌러 코드 줄을 실행합니다.

1. `result` 변수를 마우스로 가리키면 `Infinity` 값이 저장된 것을 볼 수 있습니다.

   C#에서 `Infinity`는 0으로 나눌 때의 결과입니다.

1. **F5** 키(또는 **디버그** > **디버깅 계속**)를 누릅니다.

   수학 연산의 결과로 콘솔에 무한대 기호가 표시됩니다.

1. 'n' 명령을 사용하여 적절하게 앱을 닫습니다.

## <a name="next-steps"></a>다음 단계

축하합니다. 이 자습서를 마쳤습니다. 자세히 알아보려면 다음 자습서를 계속 진행하세요.

> [!div class="nextstepaction"]
> [추가 C# 자습서 계속 진행](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Visual Studio IDE 개요 계속](/../visual-studio-ide.md)

## <a name="see-also"></a>참조

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio에서 C# 코드를 디버그하는 방법 알아보기](tutorial-debugger.md)
