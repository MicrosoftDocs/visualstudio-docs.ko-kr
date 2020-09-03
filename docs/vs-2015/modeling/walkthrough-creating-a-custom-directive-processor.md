---
title: '연습: 사용자 지정 지시문 프로세서 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
ms.assetid: b8f35a36-14e1-4467-8f5f-e01402af14d5
caps.latest.revision: 76
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 208089e4a9caeea5f8b56cdf694b7aaa602228ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659315"
---
# <a name="walkthrough-creating-a-custom-directive-processor"></a>연습: 사용자 지정 지시문 프로세서 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지시문 프로세서 * *생성 된 변환 클래스*에 코드를 추가 하 여 작업 합니다. *텍스트 템플릿에서* *지시문* 을 호출 하는 경우 텍스트 템플릿에 작성 하는 나머지 코드는 지시문이 제공 하는 기능에 의존할 수 있습니다.

 사용자 고유의 사용자 지정 지시문 프로세서를 작성할 수 있으며, 이 프로세서를 사용하여 텍스트 템플릿을 사용자 지정할 수 있습니다. 사용자 지정 지시문 프로세서를 만들려면 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>에서 상속하는 클래스를 만듭니다.

 이 연습에서 수행할 작업은 다음과 같습니다.

- 사용자 지정 지시문 프로세서 만들기

- 지시문 프로세서 등록

- 지시문 프로세서 테스트

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 사항이 필요합니다.

- Visual Studio 2010

- Visual Studio 2010 SDK

## <a name="creating-a-custom-directive-processor"></a>사용자 지정 지시문 프로세서 만들기
 이 연습에서는 사용자 지정 지시문 프로세서를 만듭니다. XML 파일을 읽어 <xref:System.Xml.XmlDocument> 변수에 저장하고 속성을 통해 노출하는 사용자 지정 지시문을 추가합니다. "지시문 프로세서 테스트" 단원에서는 텍스트 템플릿에서 이 속성을 사용하여 XML 파일에 액세스합니다.

 사용자 지정 지시문 호출은 다음과 같습니다.

 `<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`

 사용자 지정 지시문 프로세서는 생성된 변환 클래스에 변수와 속성을 추가합니다. 작성하는 지시문은 <xref:System.CodeDom> 클래스를 사용하여 엔진이 생성된 변환 클래스에 추가하는 코드를 만듭니다. <xref:System.CodeDom> 클래스는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 지시문의 `language` 매개 변수에 지정된 언어에 따라 Visual C# 또는 `template`으로 코드를 만듭니다. 지시문 프로세서의 언어와 지시문 프로세서에 액세스하는 텍스트 템플릿의 언어는 일치하지 않아도 됩니다.

 지시문이 만드는 코드는 다음과 같습니다.

```csharp
private System.Xml.XmlDocument document0Value;

public virtual System.Xml.XmlDocument Document0
{
  get
  {
    if ((this.document0Value == null))
    {
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);
    }
    return this.document0Value;
  }
}
```

```vb
Private document0Value As System.Xml.XmlDocument

Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument
    Get
        If (Me.document0Value Is Nothing) Then
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)
        End If
        Return Me.document0Value
    End Get
End Property
```

#### <a name="to-create-a-custom-directive-processor"></a>사용자 지정 지시문 프로세서를 만들려면

1. Visual Studio에서 CustomDP라는 C# 또는 Visual Basic 클래스 라이브러리 프로젝트를 만듭니다.

    > [!NOTE]
    > 둘 이상의 컴퓨터에 지시문 프로세서를 설치하려면 VSIX([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension) 프로젝트를 사용하고 .pkgdef 파일을 확장에 포함하는 것이 좋습니다. 자세한 내용은 [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md)를 참조 하세요.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - **VisualStudio \* 입니다. 0**

    - **VisualStudio \* . 인터페이스입니다. 0**

3. **Class1** 의 코드를 다음 코드로 바꿉니다. 이 코드에서는 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 클래스에서 상속하는 CustomDirectiveProcessor 클래스를 정의하고 필요한 메서드를 구현합니다.

    ```csharp
    using System;
    using System.CodeDom;
    using System.CodeDom.Compiler;
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    using System.Text;
    using System.Xml;
    using System.Xml.Serialization;
    using Microsoft.VisualStudio.TextTemplating;

    namespace CustomDP
    {
        public class CustomDirectiveProcessor : DirectiveProcessor
        {
            //this buffer stores the code that is added to the
            //generated transformation class after all the processing is done
            //---------------------------------------------------------------------
            private StringBuilder codeBuffer;

            //Using a Code Dom Provider creates code for the
            //generated transformation class in either Visual Basic or C#.
            //If you want your directive processor to support only one language, you
            //can hard code the code you add to the generated transformation class.
            //In that case, you do not need this field.
            //--------------------------------------------------------------------------
            private CodeDomProvider codeDomProvider;

            //this stores the full contents of the text template that is being processed
            //--------------------------------------------------------------------------
            private String templateContents;

            //These are the errors that occur during processing. The engine passes
            //the errors to the host, and the host can decide how to display them,
            //for example the host can display the errors in the UI
            //or write them to a file.
            //---------------------------------------------------------------------
            private CompilerErrorCollection errorsValue;
            public new CompilerErrorCollection Errors
            {
                get { return errorsValue; }
            }

            //Each time this directive processor is called, it creates a new property.
            //We count how many times we are called, and append "n" to each new
            //property name. The property names are therefore unique.
            //-----------------------------------------------------------------------------
            private int directiveCount = 0;

            public override void Initialize(ITextTemplatingEngineHost host)
            {
                //we do not need to do any initialization work
            }

            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)
            {
                //the engine has passed us the language of the text template
                //we will use that language to generate code later
                //----------------------------------------------------------
                this.codeDomProvider = languageProvider;
                this.templateContents = templateContents;
                this.errorsValue = errors;

                this.codeBuffer = new StringBuilder();
            }

            //Before calling the ProcessDirective method for a directive, the
            //engine calls this function to see whether the directive is supported.
            //Notice that one directive processor might support many directives.
            //---------------------------------------------------------------------
            public override bool IsDirectiveSupported(string directiveName)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                return false;
            }

            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    string fileName;

                    if (!arguments.TryGetValue("FileName", out fileName))
                    {
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");
                    }

                    if (string.IsNullOrEmpty(fileName))
                    {
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");
                    }

                    //Now we add code to the generated transformation class.
                    //This directive supports either Visual Basic or C#, so we must use the
                    //System.CodeDom to create the code.
                    //If a directive supports only one language, you can hard code the code.
                    //--------------------------------------------------------------------------

                    CodeMemberField documentField = new CodeMemberField();

                    documentField.Name = "document" + directiveCount + "Value";
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentField.Attributes = MemberAttributes.Private;

                    CodeMemberProperty documentProperty = new CodeMemberProperty();

                    documentProperty.Name = "Document" + directiveCount;
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentProperty.Attributes = MemberAttributes.Public;
                    documentProperty.HasSet = false;
                    documentProperty.HasGet = true;

                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };

                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);
                    documentProperty.GetStatements.Add(ifThen);

                    CodeStatement s = new CodeMethodReturnStatement(fieldName);
                    documentProperty.GetStatements.Add(s);

                    CodeGeneratorOptions options = new CodeGeneratorOptions();
                    options.BlankLinesBetweenMembers = true;
                    options.IndentString = "    ";
                    options.VerbatimOrder = true;
                    options.BracingStyle = "C";

                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))
                    {
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);
                    }

                }//end CoolDirective

                //One directive processor can contain many directives.
                //If you want to support more directives, the code goes here...
                //-----------------------------------------------------------------
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    //code for SuperCoolDirective goes here...
                }//end SuperCoolDirective

                //Track how many times the processor has been called.
                //-----------------------------------------------------------------
                directiveCount++;

            }//end ProcessDirective

            public override void FinishProcessingRun()
            {
                this.codeDomProvider = null;

                //important: do not do this:
                //the get methods below are called after this method
                //and the get methods can access this field
                //-----------------------------------------------------------------
                //this.codeBuffer = null;
            }

            public override string GetPreInitializationCodeForProcessingRun()
            {
                //Use this method to add code to the start of the
                //Initialize() method of the generated transformation class.
                //We do not need any pre-initialization, so we will just return "".
                //-----------------------------------------------------------------
                //GetPreInitializationCodeForProcessingRun runs before the
                //Initialize() method of the base class.
                //-----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetPostInitializationCodeForProcessingRun()
            {
                //Use this method to add code to the end of the
                //Initialize() method of the generated transformation class.
                //We do not need any post-initialization, so we will just return "".
                //------------------------------------------------------------------
                //GetPostInitializationCodeForProcessingRun runs after the
                //Initialize() method of the base class.
                //-----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetClassCodeForProcessingRun()
            {
                //Return the code to add to the generated transformation class.
                //-----------------------------------------------------------------
                return codeBuffer.ToString();
            }

            public override string[] GetReferencesForProcessingRun()
            {
                //This returns the references that we want to use when
                //compiling the generated transformation class.
                //-----------------------------------------------------------------
                //We need a reference to this assembly to be able to call
                //XmlReaderHelper.ReadXml from the generated transformation class.
                //-----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    this.GetType().Assembly.Location
                };
            }

            public override string[] GetImportsForProcessingRun()
            {
                //This returns the imports or using statements that we want to
                //add to the generated transformation class.
                //-----------------------------------------------------------------
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml
                //from the generated transformation class.
                //-----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    "CustomDP"
                };
            }
        }//end class CustomDirectiveProcessor

        //-------------------------------------------------------------------------
        // the code that we are adding to the generated transformation class
        // will call this method
        //-------------------------------------------------------------------------
        public static class XmlReaderHelper
        {
            public static XmlDocument ReadXml(string fileName)
            {
                XmlDocument d = new XmlDocument();

                using (XmlTextReader reader = new XmlTextReader(fileName))
                {
                    try
                    {
                        d.Load(reader);
                    }
                    catch (System.Xml.XmlException e)
                    {
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);
                    }
                }
                return d;
            }
        }//end class XmlReaderHelper
    }//end namespace CustomDP
    ```

    ```vb
    Imports System
    Imports System.CodeDom
    Imports System.CodeDom.Compiler
    Imports System.Collections.Generic
    Imports System.Globalization
    Imports System.IO
    Imports System.Text
    Imports System.Xml
    Imports System.Xml.Serialization
    Imports Microsoft.VisualStudio.TextTemplating

    Namespace CustomDP

        Public Class CustomDirectiveProcessor
        Inherits DirectiveProcessor

            'this buffer stores the code that is added to the
            'generated transformation class after all the processing is done
            '---------------------------------------------------------------
            Private codeBuffer As StringBuilder

            'Using a Code Dom Provider creates code for the
            'generated transformation class in either Visual Basic or C#.
            'If you want your directive processor to support only one language, you
            'can hard code the code you add to the generated transformation class.
            'In that case, you do not need this field.
            '--------------------------------------------------------------------------
            Private codeDomProvider As CodeDomProvider

            'this stores the full contents of the text template that is being processed
            '--------------------------------------------------------------------------
            Private templateContents As String

            'These are the errors that occur during processing. The engine passes
            'the errors to the host, and the host can decide how to display them,
            'for example the host can display the errors in the UI
            'or write them to a file.
            '---------------------------------------------------------------------
            Private errorsValue As CompilerErrorCollection
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection
                Get
                    Return errorsValue
                End Get
            End Property

            'Each time this directive processor is called, it creates a new property.
            'We count how many times we are called, and append "n" to each new
            'property name. The property names are therefore unique.
            '--------------------------------------------------------------------------
            Private directiveCount As Integer = 0

            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)

                'we do not need to do any initialization work
            End Sub

            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)

                'the engine has passed us the language of the text template
                'we will use that language to generate code later
                '----------------------------------------------------------
                Me.codeDomProvider = languageProvider
                Me.templateContents = templateContents
                Me.errorsValue = errors

                Me.codeBuffer = New StringBuilder()
            End Sub

            'Before calling the ProcessDirective method for a directive, the
            'engine calls this function to see whether the directive is supported.
            'Notice that one directive processor might support many directives.
            '---------------------------------------------------------------------
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                Return False
            End Function

            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    Dim fileName As String

                    If Not (arguments.TryGetValue("FileName", fileName)) Then
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")
                    End If

                    If String.IsNullOrEmpty(fileName) Then
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")
                    End If

                    'Now we add code to the generated transformation class.
                    'This directive supports either Visual Basic or C#, so we must use the
                    'System.CodeDom to create the code.
                    'If a directive supports only one language, you can hard code the code.
                    '--------------------------------------------------------------------------

                    Dim documentField As CodeMemberField = New CodeMemberField()

                    documentField.Name = "document" & directiveCount & "Value"
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentField.Attributes = MemberAttributes.Private

                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()

                    documentProperty.Name = "Document" & directiveCount
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentProperty.Attributes = MemberAttributes.Public
                    documentProperty.HasSet = False
                    documentProperty.HasGet = True

                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}

                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)
                    documentProperty.GetStatements.Add(ifThen)

                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)
                    documentProperty.GetStatements.Add(s)

                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()
                    options.BlankLinesBetweenMembers = True
                    options.IndentString = "    "
                    options.VerbatimOrder = True
                    options.BracingStyle = "VB"

                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)

                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)
                    End Using

                End If  'CoolDirective

                'One directive processor can contain many directives.
                'If you want to support more directives, the code goes here...
                '-----------------------------------------------------------------
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    'code for SuperCoolDirective goes here
                End If 'SuperCoolDirective

                'Track how many times the processor has been called.
                '-----------------------------------------------------------------
                directiveCount += 1
            End Sub 'ProcessDirective

            Public Overrides Sub FinishProcessingRun()

                Me.codeDomProvider = Nothing

                'important: do not do this:
                'the get methods below are called after this method
                'and the get methods can access this field
                '-----------------------------------------------------------------
                'Me.codeBuffer = Nothing
            End Sub

            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String

                'Use this method to add code to the start of the
                'Initialize() method of the generated transformation class.
                'We do not need any pre-initialization, so we will just return "".
                '-----------------------------------------------------------------
                'GetPreInitializationCodeForProcessingRun runs before the
                'Initialize() method of the base class.
                '-----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String

                'Use this method to add code to the end of the
                'Initialize() method of the generated transformation class.
                'We do not need any post-initialization, so we will just return "".
                '------------------------------------------------------------------
                'GetPostInitializationCodeForProcessingRun runs after the
                'Initialize() method of the base class.
                '-----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetClassCodeForProcessingRun() As String

                'Return the code to add to the generated transformation class.
                '-----------------------------------------------------------------
                Return codeBuffer.ToString()
            End Function

            Public Overrides Function GetReferencesForProcessingRun() As String()

                'This returns the references that we want to use when
                'compiling the generated transformation class.
                '-----------------------------------------------------------------
                'We need a reference to this assembly to be able to call
                'XmlReaderHelper.ReadXml from the generated transformation class.
                '-----------------------------------------------------------------
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}
            End Function

            Public Overrides Function GetImportsForProcessingRun() As String()

                'This returns the imports or using statements that we want to
                'add to the generated transformation class.
                '-----------------------------------------------------------------
                'We need CustomDP to be able to call XmlReaderHelper.ReadXml
                'from the generated transformation class.
                '-----------------------------------------------------------------
                Return New String() {"System.Xml", "CustomDP"}
            End Function
        End Class 'CustomDirectiveProcessor

        '--------------------------------------------------------------------------
        ' the code that we are adding to the generated transformation class
        ' will call this method
        '--------------------------------------------------------------------------
        Public Class XmlReaderHelper

            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument

                Dim d As XmlDocument = New XmlDocument()

                Using reader As XmlTextReader = New XmlTextReader(fileName)

                    Try
                        d.Load(reader)

                    Catch e As System.Xml.XmlException

                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)
                    End Try
                End Using

                Return d
            End Function
        End Class 'XmlReaderHelper

    End Namespace
    ```

4. 의 경우에 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 만 **프로젝트** 메뉴를 열고 **customdp 속성**을 클릭 합니다. **응용 프로그램** 탭의 **루트 네임 스페이스**에서 기본값인를 삭제 `CustomDP` 합니다.

5. **파일** 메뉴에서 **모두 저장**을 클릭합니다.

6. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

### <a name="build-the-project"></a>프로젝트 빌드
 프로젝트를 빌드합니다. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

## <a name="registering-the-directive-processor"></a>지시문 프로세서 등록
 의 텍스트 템플릿에서 지시문을 호출 하려면 먼저 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 지시문 프로세서에 대 한 레지스트리 키를 추가 해야 합니다.

> [!NOTE]
> 둘 이상의 컴퓨터에 지시문 프로세서를 설치하려면 어셈블리와 함께 .pkgdef 파일이 포함된 VSIX([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension)를 정의하는 것이 좋습니다. 자세한 내용은 [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md)를 참조 하세요.

 지시문 프로세서에 대한 키는 다음 위치의 레지스트리에 있습니다.

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

 64비트 시스템의 레지스트리 위치는 다음과 같습니다.

```
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

 이 단원에서는 사용자 지정 지시문 프로세서에 대한 키를 동일한 위치의 레지스트리에 추가합니다.

> [!CAUTION]
> 레지스트리를 올바르게 편집하지 않으면 시스템을 심각하게 손상시킬 수 있습니다. 따라서 레지스트리를 변경하기 전에 컴퓨터에 있는 중요한 데이터를 백업해야 합니다.

#### <a name="to-add-a-registry-key-for-the-directive-processor"></a>지시문 프로세서에 대한 레지스트리 키를 추가하려면

1. `regedit`시작 메뉴 또는 명령줄을 사용 하 여 명령을 실행 합니다.

2. **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ \* .0 \ .0\ texttemplating\directiveprocessors**위치로 이동 하 여 노드를 클릭 합니다.

    64 비트 시스템에서 **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\visualstudio \\ \* \ .0\ texttemplating\directiveprocessors를 사용 합니다.**

3. CustomDirectiveProcessor라는 새 키를 추가합니다.

   > [!NOTE]
   > 이것은 사용자 지정 지시문의 Processor 필드에서 사용할 이름입니다. 이 이름은 지시문의 이름, 지시문 프로세서 클래스의 이름 또는 지시문 프로세서 네임스페이스와 일치하지 않아도 됩니다.

4. 새 문자열의 이름으로 CustomDP.CustomDirectiveProcessor 값을 가진 Class라는 새 문자열 값을 추가합니다.

5. 이 연습의 앞부분에서 만든 CustomDP.dll의 경로와 같은 값을 가진 CodeBase라는 새 문자열 값을 추가합니다.

    예를 들어 경로는와 같을 수 있습니다 `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll` .

    레지스트리 키의 값은 다음과 같습니다.

   |   Name    |  형식  |                                   데이터                                   |
   |-----------|--------|--------------------------------------------------------------------------|
   | (기본값) | REG_SZ |                             (값 설정 안 됨)                              |
   |   클래스   | REG_SZ |                    CustomDP.CustomDirectiveProcessor                     |
   | CodeBase  | REG_SZ | <strong>\<Path to Your Solution></strong>CustomDP\bin\Debug\CustomDP.dll |

    GAC에 어셈블리를 배치한 경우 값은 다음과 같습니다.

   |   Name    |  형식  |               데이터                |
   |-----------|--------|-----------------------------------|
   | (기본값) | REG_SZ |          (값 설정 안 됨)          |
   |   클래스   | REG_SZ | CustomDP.CustomDirectiveProcessor |
   | 어셈블리  | REG_SZ |           CustomDP.dll            |

6. Visual Studio를 다시 시작합니다.

## <a name="testing-the-directive-processor"></a>지시문 프로세서 테스트
 지시문 프로세서를 테스트하려면 지시문 프로세서를 호출하는 텍스트 템플릿을 작성해야 합니다.

 이 예제에서 텍스트 템플릿은 지시문을 호출하고 클래스 파일에 대한 문서가 포함된 XML 파일의 이름을 전달합니다. 자세한 내용은 [XML 문서 주석](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)을 참조 하세요.

 그런 다음 텍스트 템플릿은 지시문이 만드는 <xref:System.Xml.XmlDocument> 속성을 사용하여 XML을 탐색하고 문서 주석을 인쇄합니다.

#### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>지시문 프로세서 테스트에 사용할 XML 파일을 만들려면

1. `DocFile.xml`텍스트 편집기 (예: 메모장)를 사용 하 여 라는 텍스트 파일을 만듭니다.

    > [!NOTE]
    > 원하는 위치에 이 파일을 만들 수 있습니다(예: C:\Test\DocFile.xml).

2. 텍스트 파일에 다음을 추가합니다.

    ```
    <?xml version="1.0"?>
    <doc>
        <assembly>
            <name>xmlsample</name>
        </assembly>
        <members>
            <member name="T:SomeClass">
                <summary>Class level summary documentation goes here.</summary>
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>
            </member>
            <member name="F:SomeClass.m_Name">
                <summary>Store for the name property</summary>
            </member>
            <member name="M:SomeClass.#ctor">
                <summary>The class constructor.</summary>
            </member>
            <member name="M:SomeClass.SomeMethod(System.String)">
                <summary>Description for SomeMethod.</summary>
                <param name="s">Parameter description for s goes here</param>
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>
            </member>
            <member name="M:SomeClass.SomeOtherMethod">
                <summary>Some other method.</summary>
                <returns>Return results are described through the returns tag.</returns>
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>
            </member>
            <member name="M:SomeClass.Main(System.String[])">
                <summary>The entry point for the application.</summary>
                <param name="args">A list of command line arguments</param>
            </member>
            <member name="P:SomeClass.Name">
                <summary>Name property</summary>
                <value>A value tag is used to describe the property value</value>
            </member>
        </members>
    </doc>
    ```

3. 파일을 저장하고 닫습니다.

#### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>텍스트 템플릿을 만들어 지시문 프로세서를 테스트하려면

1. Visual Studio에서 TemplateTest라는 C# 또는 Visual Basic 클래스 라이브러리 프로젝트를 만듭니다.

2. TestDP.tt라는 새 텍스트 템플릿 파일을 추가합니다.

3. TestDP.tt의 **사용자 지정 도구** 속성이로 설정 되어 있는지 확인 `TextTemplatingFileGenerator` 합니다.

4. TestDP.tt의 내용을 다음 텍스트로 변경합니다.

    > [!NOTE]
    > <문자열을 `YOUR PATH>` DocFile.xml 파일의 경로로 바꾸어야 합니다.

     텍스트 템플릿의 언어는 지시문 프로세서의 언어와 일치하지 않아도 됩니다.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".txt" #>

    <#  //This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  //Uncomment this line if you want to see the generated transformation class. #>
    <#  //System.Diagnostics.Debugger.Break(); #>

    <#  //This will use the results of the directive processor. #>
    <#  //The directive processor has read the XML and stored it in Document0. #>
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);

            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
            }
            WriteLine("");
        }
    #>

    <#  //You can call the directive processor again and pass it a different file. #>
    <# //@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>

    <#  //To use the results of the second directive call, use Document1. #>
    <#
        //XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");

        //...
    #>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".txt" #>

    <#  'This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  'Uncomment this line if you want to see the generated transformation class. #>
    <#  'System.Diagnostics.Debugger.Break() #>

    <#  'This will use the results of the directive processor. #>
    <#  'The directive processor has read the XML and stored it in Document0. #>
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes

            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)

            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
            Next

            WriteLine("")
        Next
    #>

    <#  'You can call the directive processor again and pass it a different file. #>
    <# '@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>

    <#  'To use the results of the second directive call, use Document1. #>
    <#
        'node = Document1.DocumentElement.SelectSingleNode("members")

        '...
    #>
    ```

    > [!NOTE]
    > 이 예제에서 `Processor` 매개 변수의 값은 `CustomDirectiveProcessor`입니다. `Processor` 매개 변수의 값은 프로세서의 레지스트리 키 이름과 일치해야 합니다.

5. **파일** 메뉴에서 **모두 저장**을 클릭합니다.

#### <a name="to-test-the-directive-processor"></a>지시문 프로세서를 테스트하려면

1. **솔루션 탐색기**에서 TestDP.tt을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

     사용자의 경우 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 기본적으로 TestDP.txt **솔루션 탐색기** 에 표시 되지 않을 수 있습니다. 프로젝트에 할당 된 모든 파일을 표시 하려면 **프로젝트** 메뉴를 열고 **모든 파일 표시**를 클릭 합니다.

2. **솔루션 탐색기**에서 TestDP.txt 노드를 확장 한 다음 TestDP.txt를 두 번 클릭 하 여 편집기에서 엽니다.

     생성된 텍스트 출력이 나타납니다. 출력은 다음과 비슷합니다.

    ```
       Name:  T:SomeClass
    summary:  Class level summary documentation goes here.
    remarks:  Longer comments can be associated with a type or member through the remarks tag

       Name:  F:SomeClass.m_Name
    summary:  Store for the name property

       Name:  M:SomeClass.#ctor
    summary:  The class constructor.

       Name:  M:SomeClass.SomeMethod(System.String)
    summary:  Description for SomeMethod.
      param:  Parameter description for s goes here
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.

       Name:  M:SomeClass.SomeOtherMethod
    summary:  Some other method.
    returns:  Return results are described through the returns tag.
    seealso:  Notice the use of the cref attribute to reference a specific method

       Name:  M:SomeClass.Main(System.String[])
    summary:  The entry point for the application.
      param:  A list of command line arguments

       Name:  P:SomeClass.Name
    summary:  Name property
      value:  A value tag is used to describe the property value
    ```

## <a name="adding-html-to-generated-text"></a>생성된 텍스트에 HTML 추가
 사용자 지정 지시문 프로세서를 테스트한 후 생성된 텍스트에 HTML을 추가할 수 있습니다.

#### <a name="to-add-html-to-the-generated-text"></a>생성된 텍스트에 HTML을 추가하려면

1. TestDP.tt의 코드를 다음 코드로 바꿉니다. HTML이 강조 표시되어 있습니다. 문자열을 `YOUR PATH` DocFile.xml 파일의 경로로 바꾸어야 합니다.

    > [!NOTE]
    > 추가 오픈 \<# and close #> 태그는 HTML 태그에서 문 코드를 분리 합니다.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".htm" #>

    <#  //this will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  //uncomment this line if you want to see the generated transformation class #>
    <#  //System.Diagnostics.Debugger.Break(); #>

    <html><body>

    <#  //this will use the results of the directive processor #>
    <#  //the directive processor has read the XML and stored it in Document0#>
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
    #>
    <h3>
    <#
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);
    #>
    </h3>
    <#
            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
    #>
    <br/>
    <#
            }
        }
    #>
    </body></html>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".htm" #>

    <#  'this will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  'uncomment this line if you want to see the generated transformation class #>
    <#  'System.Diagnostics.Debugger.Break() #>

    <html><body>

    <#  'this will use the results of the directive processor #>
    <#  'the directive processor has read the XML and stored it in Document0#>
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes
    #>
    <h3>
    <#
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)
    #>
    </h3>
    <#
            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
    #>
    <br/>
    <#
            Next
        Next
    #>
    </body></html>
    ```

2. **파일** 메뉴에서 **TestDP.txt저장 **을 클릭 합니다.

3. 브라우저에서 출력을 보려면 **솔루션 탐색기**에서 TestDP.htm를 마우스 오른쪽 단추로 클릭 하 고 **브라우저에서 보기**를 클릭 합니다.

     출력은 HTML 형식이 적용된 것을 제외하고 원래 텍스트와 동일합니다. 각 항목 이름이 굵게 표시됩니다.
