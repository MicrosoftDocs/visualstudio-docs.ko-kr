---
title: 사용자 지정 추출 규칙 코딩(웹 성능 테스트)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d29bb2d0bfa1bbea7d0dd8dedbb17f9704a9c66d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810629"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>웹 성능 테스트에 대한 사용자 지정 추출 규칙 코딩

사용자 고유의 추출 규칙을 만들 수 있습니다. 이렇게 하려면 추출 규칙 클래스에서 사용자 고유의 규칙을 파생시킵니다. 추출 규칙은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 기본 클래스에서 파생됩니다.

> [!NOTE]
> 사용자 지정 유효성 검사 규칙을 만들 수도 있습니다. 자세한 내용은 [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)를 참조합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>사용자 지정 추출 규칙을 만들려면

1. 웹 성능 테스트를 포함하는 테스트 프로젝트를 엽니다.

2. (선택 항목) 추출 규칙을 저장할 별도의 클래스 라이브러리 프로젝트를 만듭니다.

    > [!IMPORTANT]
    > 테스트가 포함되어 있는 프로젝트에 클래스를 만들 수 있습니다. 그러나 규칙을 다시 사용하려면 규칙을 저장할 별도의 클래스 라이브러리 프로젝트를 만드는 것이 좋습니다. 별도의 프로젝트를 만드는 경우 이 절차의 선택 항목 단계를 수행해야 합니다.

3. (선택 항목) 클래스 라이브러리 프로젝트에서 Microsoft.VisualStudio.QualityTools.WebTestFramework dll에 대한 참조를 추가합니다.

4. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 클래스에서 파생되는 클래스를 만듭니다. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*> 멤버를 구현합니다.

5. (선택 항목) 새 클래스 라이브러리 프로젝트를 빌드합니다.

6. (선택 항목) 테스트 프로젝트에서 사용자 지정 추출 규칙을 포함하는 클래스 라이브러리 프로젝트에 대한 참조를 추가합니다.

7. 테스트 프로젝트에서 웹 성능 테스트를 **웹 성능 테스트 편집기**에서 엽니다.

8. 사용자 지정 추출 규칙을 추가하려면 웹 성능 테스트 요청을 마우스 오른쪽 단추로 클릭하고 **추출 규칙 추가**를 선택합니다.

     **추출 규칙 추가** 대화 상자가 나타납니다. **규칙 선택** 목록에 미리 정의된 유효성 검사 규칙과 함께 사용자 지정 유효성 검사 규칙이 표시됩니다. 사용자 지정 추출 규칙을 선택한 다음, **확인**을 선택합니다.

9. 웹 성능 테스트를 실행합니다.

## <a name="example"></a>예제

다음 코드에서는 사용자 지정 추출 규칙의 구현을 보여 줍니다. 이 추출 규칙에서는 지정한 입력 필드에서 값을 추출합니다. 이 예제를 출발점으로 삼아 사용자 지정 추출 규칙을 직접 만들 수 있습니다.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

<xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 메서드에는 추출 규칙의 핵심 기능이 포함되어 있습니다. 위 예제에서 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> 메서드는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs>를 사용하여 이 추출 규칙이 적용되는 요청이 생성하는 응답을 제공합니다. 응답에는 응답 내 모든 태그가 들어 있는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>가 포함됩니다. 입력 태그는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> 외부로 필터링됩니다. 각 입력 태그는 `Name` 속성에 사용자가 입력한 값과 같은 값을 가지는 `name`이라는 특성에 대해 검사됩니다. 일치하는 특성을 가진 태그가 발견되면 `value` 특성이 있는 경우 이 특성에 포함된 값을 추출하려고 시도합니다. 이 특성이 있으면 태그의 이름과 값이 추출되어 웹 성능 테스트 컨텍스트에 추가되고 추출 규칙이 전달됩니다.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
