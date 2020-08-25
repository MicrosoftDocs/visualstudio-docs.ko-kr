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
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 981f18857beb83ef2a4902f50985ca8e9f7ed901
ms.sourcegitcommit: 8e5b0106061bb43247373df33d0850ae68457f5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88507958"
---
# <a name="tutorial-extend-a-simple-c-console-app"></a>자습서: 간단한 C# 콘솔 앱 확장

이 자습서에서는 첫 부분에서 만든 콘솔 앱을 Visual Studio를 사용해 확장하는 방법을 알아봅니다. 여러 프로젝트를 관리하고 타사 패키지를 참조하는 등의 일상적인 개발 작업에 필요한 Visual Studio의 일부 기능에 대해 알아봅니다.

이 시리즈의 [첫 부분](tutorial-console.md)을 완료했다면 Calculator 콘솔 앱이 이미 있습니다.  1부를 건너뛰려면 먼저 GitHub 리포지토리에서 프로젝트를 열어 시작하면 됩니다. C# Calculator 앱은 [vs-tutorial-samples 리포지토리](https://github.com/MicrosoftDocs/vs-tutorial-samples)에 있습니다. [자습서: 리포지토리에서 프로젝트 열기](../tutorial-open-project-from-repo.md)의 단계에 따라 시작하세요.

## <a name="add-a-new-project"></a>새 프로젝트 추가

실제 코드에는 솔루션에서 함께 작업하는 많은 프로젝트가 포함되어 있습니다. 이제 Calculator 앱에 다른 프로젝트를 추가해 보겠습니다. 이 프로젝트는 Calculator 함수 일부를 제공하는 클래스 라이브러리입니다.

1. Visual Studio에서 최상위 메뉴 명령 **File** > **Add** > **New Project** 사용하여 새 프로젝트를 추가할 수 있습니다. 하지만 기존 프로젝트 이름(“프로젝트 노드”라고 함)을 마우스 오른쪽 단추로 클릭하고 프로젝트의 바로 가기 메뉴(상황에 맞는 메뉴)를 열 수도 있습니다. 이 바로 가기 메뉴에는 프로젝트에 기능을 추가하는 여러 방법이 있습니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. C# 프로젝트 템플릿 **클래스 라이브러리(.NET Standard)** 를 선택합니다.

   ![클래스 라이브러리 프로젝트 템플릿 선택 스크린샷](media/vs-2019/calculator2-add-project-dark.png)

1. 프로젝트 이름 **CalculatorLibrary**를 입력하고 **만들기**를 선택합니다. Visual Studio에서 새 프로젝트를 만들어 솔루션에 추가합니다.

   ![CalculatorLibrary 클래스 라이브러리 프로젝트가 추가된 솔루션 탐색기의 스크린샷](media/vs-2019/calculator2-solution-explorer-with-class-library-dark2.png)

1. *Class1.cs*를 사용하는 대신 파일 이름을 **CalculatorLibrary.cs**로 바꿉니다. **솔루션 탐색기**에서 이 이름을 클릭하여 이름을 바꾸거나, 이름을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택하거나, **F2** 키를 누르면 됩니다.

   파일에서 `Class1` 참조의 이름을 바꿀지 묻는 메시지가 나타날 수도 있습니다. 이후 단계에서 코드를 바꿀 예정이므로 여기서 어떤 선택을 해도 괜찮습니다.

1. 첫 번째 프로젝트가 새 클래스 라이브러리에서 제공된 API를 사용할 수 있도록 이제 프로젝트 참조를 추가해야 합니다.  첫 번째 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 참조 추가**를 선택합니다.

   ![프로젝트 참조 추가 메뉴 항목의 스크린샷](media/vs-2019/calculator2-add-project-reference-dark.png)

   **참조 관리자** 대화 상자가 나타납니다. 이 대화 상자에서는 다른 프로젝트에 참조를 추가할 수 있고 프로젝트에 필요한 어셈블리 및 COM DLL을 추가할 수도 있습니다.

   ![참조 관리자 대화 상자의 스크린샷](media/vs-2019/calculator2-ref-manager-dark.png)

1. **참조 관리자** 대화 상자에서 **CalculatorLibrary** 프로젝트의 확인란을 선택하고 **확인**을 선택합니다.  프로젝트 참조는 **솔루션 탐색기**의 **프로젝트** 노드 아래에 나타납니다.

   ![프로젝트 참조가 있는 솔루션 탐색기의 스크린샷](media/vs-2019/calculator2-solution-explorer-with-project-reference-dark2.png)

1. *Program.cs*에서 `Calculator` 클래스와 모든 해당 코드를 선택하고 **CTRL+X**를 눌러 Program.cs에서 자릅니다. 그리고 **CalculatorLibrary**(*CalculatorLibrary.cs*)에서 코드를 `CalculatorLibrary` 네임스페이스에 붙여넣습니다. 그런 다음, Calculator 클래스 `public`이 코드를 라이브러리 외부에 노출하도록 합니다. 이제 *CalculatorLibrary.cs*의 코드는 다음 코드와 유사합니다.

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

1. 이제 모든 작업의 로그를 추가하고 텍스트 파일에 쓰려 한다고 가정하겠습니다. .NET `Trace` 클래스는 다음과 같은 기능을 제공합니다. (기본 인쇄 디버깅 기술에도 유용합니다.)  Trace 클래스는 System.Diagnostics에 있으므로, using 지시문을 추가하여 시작합니다.

   ```csharp
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

1. 프로그램을 다시 실행하고 완료되면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **파일 탐색기의 폴더 열기**를 선택한 다음 파일 탐색기에서 출력 폴더로 이동합니다. 이 폴더는 *bin/Debug/netcoreapp3.1*일 수도 있습니다. *calculator.log* 파일을 엽니다.

    ```output
    Starting Calculator Log
    Started 7/9/2020 1:58:19 PM
    1 + 2 = 3
    3 * 3 = 9
    ```

## <a name="add-a-nuget-package-write-to-a-json-file"></a>NuGet 패키지 추가: JSON 파일에 쓰기

1. 이제 개체 데이터를 저장하는 데 많이 사용되는 이식 가능한 형식인 JSON 형식으로 작업을 출력하려 한다고 가정하겠습니다. 이 기능을 구현하려면 NuGet 패키지인 Newtonsoft.Json을 참조해야 합니다. NuGet 패키지는 .NET 클래스 라이브러리를 배포하는 주요 수단입니다. **솔루션 탐색기**에서 CalculatorLibrary 프로젝트에 대한 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다.

   ![바로 가기 메뉴의 NuGet 패키지 관리 스크린샷](media/vs-2019/calculator2-manage-nuget-packages-dark2.png)

   NuGet 패키지 관리자가 열립니다.

   ![NuGet 패키지 관리자 스크린샷](media/vs-2019/calculator2-nuget-package-manager-dark.png)

1. Newtonsoft.Json 패키지를 검색하고 **설치**를 선택합니다.

   ![Newtonsoft NuGet 패키지 정보의 스크린샷](media/vs-2019/calculator2-nuget-newtonsoft-json-dark2.png)

   패키지가 다운로드되어 프로젝트에 추가되고 **솔루션 탐색기**의 참조 노드에 새 항목이 표시됩니다.

1. *CalculatorLibrary.cs*의 시작 부분에 Newtonsoft.Json 패키지에 대한 using 지시문을 추가합니다.

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

1. 그리고 *Program.cs*에서 끝에 완료 호출을 추가합니다.

   ```csharp
            // And call to close the JSON writer before return
            calculator.Finish();
            return;
        }
   ```

1. 앱을 빌드하고 실행한 후 완료되면 몇 가지 작업을 입력한 후 ‘n’ 명령을 사용하여 앱을 제대로 닫습니다.  이제 consolelog.json 파일을 열면 다음과 같은 내용이 표시됩니다.

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

## <a name="next-steps"></a>다음 단계

축하합니다. 이 자습서를 마쳤습니다. 자세히 알아보려면 다음 자습서를 계속 진행하세요.

> [!div class="nextstepaction"]
> [추가 C# 자습서 계속 진행](/dotnet/csharp/tutorials/)

> [!div class="nextstepaction"]
> [Visual Studio IDE 개요 계속](/../visual-studio-ide.md)

## <a name="see-also"></a>참조

* [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
* [Visual Studio에서 C# 코드를 디버그하는 방법 알아보기](tutorial-debugger.md)
