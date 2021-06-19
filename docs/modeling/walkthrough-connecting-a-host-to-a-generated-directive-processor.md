---
title: 생성된 지시문 프로세서에 호스트 연결
description: 지시문 프로세서를 호출하는 텍스트 템플릿을 지원하게 사용자 지정 호스트를 확장하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ed51688e5b65e34d7067963dbf7b839b1f022768
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388323"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>연습: 생성된 지시문 프로세서에 호스트 연결

텍스트 템플릿을 처리하는 호스트를 직접 작성할 수 있습니다. 기본 사용자 지정 호스트는 [연습: 사용자 지정 텍스트 템플릿 호스트 만들기에](../modeling/walkthrough-creating-a-custom-text-template-host.md)설명되어 있습니다. 해당 호스트를 확장하여 여러 출력 파일 생성과 같은 함수를 추가할 수 있습니다.

이 연습에서는 지시문 프로세서를 호출하는 텍스트 템플릿을 지원하게 사용자 지정 호스트를 확장합니다. 도메인별 언어를 정의하면 도메인 모델에 대한 *지시문 프로세서가* 생성됩니다. 지시문 프로세서를 사용하면 사용자가 모델에 액세스하는 템플릿을 더 쉽게 작성할 수 있어 템플릿에서 어셈블리 및 가져오기 지시문을 작성할 필요가 줄어듭니다.

> [!NOTE]
> 이 연습은 [연습: 사용자 지정 텍스트 템플릿 호스트 만들기를](../modeling/walkthrough-creating-a-custom-text-template-host.md)기반으로 합니다. 먼저 해당 연습을 수행합니다.

이 연습에는 다음 작업이 포함됩니다.

- 를 사용하여 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 도메인 모델을 기반으로 하는 지시문 프로세서를 생성합니다.

- 사용자 지정 텍스트 템플릿 호스트를 생성된 지시문 프로세서에 연결

- 생성된 지시문 프로세서를 통해 사용자 지정 호스트를 테스트합니다.

## <a name="prerequisites"></a>필수 조건

DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

| 구성 요소 | 링크 |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

또한 연습: 사용자 지정 텍스트 템플릿 [호스트 만들기에서](../modeling/walkthrough-creating-a-custom-text-template-host.md)만든 사용자 지정 텍스트 템플릿 변환이 있어야 합니다.

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Domain-Specific 언어 도구를 사용하여 지시문 프로세서 생성

이 연습에서는 Domain-Specific 언어 디자이너 마법사를 사용하여 DSLMinimalTest 솔루션에 대한 도메인별 언어를 만듭니다.

1. 다음과 같은 특징이 있는 도메인별 언어 솔루션을 만듭니다.

   - 이름: DSLMinimalTest

   - 솔루션 템플릿: 최소 언어

   - 파일 확장명: min

   - 회사 이름: Fabrikam

   도메인별 언어 솔루션을 만드는 방법에 대한 자세한 내용은 [방법: Domain-Specific 언어 솔루션 만들기를 참조하세요.](../modeling/how-to-create-a-domain-specific-language-solution.md)

2. **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

   > [!IMPORTANT]
   > 이 단계에서는 지시문 프로세서를 생성하고 레지스트리에 해당 키를 추가합니다.

3. **디버그** 메뉴에서 **디버깅 시작** 을 클릭합니다.

    Visual Studio 두 번째 인스턴스가 열립니다.

4. 실험적 빌드의 **솔루션 탐색기** **sample.min** 파일을 두 번 클릭합니다.

    디자이너에서 파일이 열립니다. 모델에는 ExampleElement1 및 ExampleElement2라는 두 개의 요소와 이들 간의 링크가 있습니다.

5. Visual Studio 두 번째 인스턴스를 닫습니다.

6. 솔루션을 저장한 다음 Domain-Specific 언어 디자이너를 닫습니다.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>지시문 프로세서에 사용자 지정 텍스트 템플릿 호스트 연결

지시문 프로세서를 생성한 후 지시문 프로세서와 연습: 사용자 지정 텍스트 템플릿 호스트 만들기에서 만든 [사용자 지정 텍스트 템플릿 호스트를 연결합니다.](../modeling/walkthrough-creating-a-custom-text-template-host.md)

1. CustomHost 솔루션을 엽니다.

2. **프로젝트** 메뉴에서 **참조 추가** 를 클릭합니다.

     **.NET** 탭이 표시된 **참조 추가** 대화 상자가 열립니다.

3. 다음 참조를 추가합니다.

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. Program.cs 또는 Module1.vb의 맨 위에 다음 코드 줄을 추가합니다.

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. 속성에 대한 코드를 찾아 `StandardAssemblyReferences` 다음 코드로 대체합니다.

    > [!NOTE]
    > 이 단계에서는 호스트에서 지원할 생성된 지시문 프로세서에 필요한 어셈블리에 대한 참조를 추가합니다.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. 함수에 대한 코드를 찾아 `ResolveDirectiveProcessor` 다음 코드로 대체합니다.

    > [!IMPORTANT]
    > 이 코드에는 연결하려는 생성된 지시문 프로세서의 이름에 대한 하드 코드된 참조가 포함되어 있습니다. 이 작업을 보다 일반적으로 쉽게 만들 수 있습니다. 이 경우 레지스트리에 나열된 모든 지시문 프로세서를 찾아 일치 항목 찾기를 시도합니다. 이 경우 호스트는 생성된 지시문 프로세서에서 작동합니다.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. **파일** 메뉴에서 **모두 저장** 을 클릭합니다.

8. **빌드** 메뉴에서 **솔루션 빌드** 를 클릭합니다.

## <a name="test-the-custom-host-with-the-directive-processor"></a>지시문 프로세서를 통해 사용자 지정 호스트 테스트

사용자 지정 텍스트 템플릿 호스트를 테스트하려면 먼저 생성된 지시문 프로세서를 호출하는 텍스트 템플릿을 작성해야 합니다. 그런 다음 사용자 지정 호스트를 실행하고 텍스트 템플릿의 이름을 전달한 다음 지시문이 올바르게 처리되었는지 확인합니다.

### <a name="create-a-text-template-to-test-the-custom-host"></a>사용자 지정 호스트를 테스트하는 텍스트 템플릿 만들기

1. 텍스트 파일을 만들고 이름을 로 `TestTemplateWithDP.tt` 지정합니다. 메모장과 같은 텍스트 편집기를 사용하여 파일을 만들 수 있습니다.

2. 텍스트 파일에 다음을 추가합니다.

    > [!NOTE]
    > 텍스트 템플릿의 프로그래밍 언어는 사용자 지정 호스트의 프로그래밍 언어와 일치할 필요가 없습니다.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. 코드에서 를 \<YOUR PATH> 첫 번째 절차에서 만든 디자인별 언어의 Sample.min 파일 경로로 대체합니다.

4. 파일을 저장하고 닫습니다.

### <a name="test-the-custom-host"></a>사용자 지정 호스트 테스트

1. 명령 프롬프트 창을 엽니다.

2. 사용자 지정 호스트에 대한 실행 가능한 파일의 경로를 입력하고 Enter 키를 누르지 않습니다.

     예를 들어 다음과 같이 입력합니다.

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > 주소를 입력하는 대신 Windows 탐색기 CustomHost.exe 파일로 이동한 다음 파일을 명령 프롬프트 창으로 끌 수 있습니다.

3. 공백을 입력합니다.

4. 텍스트 템플릿 파일의 경로를 입력한 다음 Enter 키를 누릅니다.

     예를 들어 다음과 같이 입력합니다.

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > 주소를 입력하는 대신 Windows 탐색기 TestTemplateWithDP.txt 파일로 이동한 다음 파일을 명령 프롬프트 창으로 끌 수 있습니다.

     사용자 지정 호스트 애플리케이션이 실행되고 텍스트 템플릿 변환 프로세스가 시작됩니다.

5. **Windows 탐색기** 파일 TestTemplateWithDP.txt 포함된 폴더를 찾습니다.

     폴더에는 파일 TestTemplateWithDP1.txt 포함되어 있습니다.

6. 이 파일을 열어 텍스트 템플릿 변환의 결과를 확인합니다.

     생성된 텍스트 출력의 결과가 나타나고 다음과 같이 표시됩니다.

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>참조

- [연습: 사용자 지정 텍스트 템플릿 호스트 만들기](../modeling/walkthrough-creating-a-custom-text-template-host.md)
