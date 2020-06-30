---
title: '연습: 모델에 액세스하는 텍스트 템플릿 디버깅'
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e33297bba899c1843b8601c031d7669531a1bd3f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546902"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>연습: 모델에 액세스하는 텍스트 템플릿 디버깅
도메인별 언어 솔루션에서 텍스트 템플릿을 수정 하거나 추가 하는 경우 엔진이 템플릿을 소스 코드로 변환 하거나 생성 된 코드를 컴파일할 때 오류가 발생할 수 있습니다. 다음 연습에서는 텍스트 템플릿을 디버깅 하기 위해 수행할 수 있는 몇 가지 작업을 보여 줍니다.

> [!NOTE]
> 일반적인 텍스트 템플릿에 대 한 자세한 내용은 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요. 텍스트 템플릿을 디버그 하는 방법에 대 한 자세한 내용은 [연습: 텍스트 템플릿 디버깅](debugging-a-t4-text-template.md)을 참조 하세요.

## <a name="creating-a-domain-specific-language-solution"></a>도메인별 언어 솔루션 만들기
 이 절차에서는 다음과 같은 특징을 가진 도메인별 언어 솔루션을 만듭니다.

- 이름: DebuggingTestLanguage

- 솔루션 템플릿: 최소 언어

- 파일 확장명: ddd

- 회사 이름: Fabrikam

  도메인별 언어 솔루션을 만드는 방법에 대 한 자세한 내용은 [방법: 도메인별 언어 솔루션 만들기](../modeling/how-to-create-a-domain-specific-language-solution.md)를 참조 하세요.

## <a name="creating-a-text-template"></a>텍스트 템플릿 만들기
 솔루션에 텍스트 템플릿을 추가 합니다.

#### <a name="to-create-a-text-template"></a>텍스트 템플릿을 만들려면

1. 솔루션을 빌드하고 디버거에서 실행을 시작 합니다. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭 한 다음 **디버그** 메뉴에서 **디버깅 시작**을 클릭 합니다. Visual Studio의 새 인스턴스는 디버깅 프로젝트를 엽니다.

2. 이라는 텍스트 파일을 `DebugTest.tt` 디버깅 프로젝트에 추가 합니다.

3. DebugTest.tt의 **사용자 지정 도구** 속성이로 설정 되어 있는지 확인 `TextTemplatingFileGenerator` 합니다.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>텍스트 템플릿에서 모델에 액세스 하는 디버깅 지시문
 텍스트 템플릿의 문과 식에서 모델에 액세스할 수 있으려면 먼저 생성 된 지시문 프로세서를 호출 해야 합니다. 생성 된 지시문 프로세서를 호출 하면 모델의 클래스를 텍스트 템플릿 코드에서 속성으로 사용할 수 있습니다. 자세한 내용은 [텍스트 템플릿에서 모델 액세스](../modeling/accessing-models-from-text-templates.md)를 참조 하세요.

 다음 절차에서는 잘못 된 지시문 이름과 잘못 된 속성 이름을 디버깅 합니다.

#### <a name="to-debug-an-incorrect-directive-name"></a>잘못 된 지시문 이름을 디버깅 하려면

1. DebugTest.tt의 코드를 다음 코드로 바꿉니다.

    > [!NOTE]
    > 코드에 오류가 있습니다. 오류를 디버그 하기 위해이 오류를 소개 합니다.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. **솔루션 탐색기**에서 DebugTest.tt을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

     **오류 목록** 창에 다음 오류가 표시 됩니다.

     **' DebuggingTestLanguageDirectiveProcessor ' 프로세서는 이름이 ' modelRoot ' 인 지시어를 지원 하지 않습니다. 변환이 실행 되지 않습니다.**

     이 경우 지시문 호출에 잘못 된 지시문 이름이 포함 됩니다. `modelRoot`지시문 이름으로를 지정 했지만 올바른 지시문 이름은 `DebuggingTestLanguage` 입니다.

3. **오류 목록** 창에서 오류를 두 번 클릭 하 여 코드로 이동 합니다.

4. 코드를 수정 하려면 지시문 이름을로 변경 `DebuggingTestLanguage` 합니다.

     변경 내용이 강조 표시 됩니다.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. **솔루션 탐색기**에서 DebugTest.tt을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

     이제 시스템에서 텍스트 템플릿을 변환 하 고 해당 출력 파일을 생성 합니다. **오류 목록** 창에 오류가 표시 되지 않습니다.

#### <a name="to-debug-an-incorrect-property-name"></a>잘못 된 속성 이름을 디버깅 하려면

1. DebugTest.tt의 코드를 다음 코드로 바꿉니다.

    > [!NOTE]
    > 코드에 오류가 있습니다. 오류를 디버그 하기 위해이 오류를 소개 합니다.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2. **솔루션 탐색기**에서 DebugTest.tt을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

     **오류 목록** 창이 나타나고 다음 오류 중 하나가 표시 됩니다.

     (C#)

     **변환 컴파일: \<GUID> VisualStudio. GeneratedTextTransformation '에 ' Examplemodel.store.customer '에 대 한 정의가 포함 되어 있지 않습니다.**

     (Visual Basic)

     **변환 컴파일: ' Examplemodel.store.customer '는 ' VisualStudio '의 멤버가 아닙니다 \<GUID> . GeneratedTextTransformation '.**

     이 경우 텍스트 템플릿 코드에 잘못 된 속성 이름이 포함 됩니다. `ExampleModel`속성 이름으로를 지정 했지만 올바른 속성 이름은 `LibraryModel` 입니다. 다음 코드와 같이 제공 매개 변수에서 올바른 속성 이름을 찾을 수 있습니다.

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. 오류 목록 창에서 오류를 두 번 클릭 하 여 코드로 이동 합니다.

4. 코드를 수정 하려면 `LibraryModel` 텍스트 템플릿 코드에서 속성 이름을로 변경 합니다.

     변경 내용은 강조 표시되어 있습니다.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5. **솔루션 탐색기**에서 DebugTest.tt을 마우스 오른쪽 단추로 클릭 한 다음 **사용자 지정 도구 실행**을 클릭 합니다.

     이제 시스템에서 텍스트 템플릿을 변환 하 고 해당 출력 파일을 생성 합니다. **오류 목록** 창에 오류가 표시 되지 않습니다.
