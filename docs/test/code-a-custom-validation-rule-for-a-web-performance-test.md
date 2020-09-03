---
title: 웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bdf7f7f8f5bfcc7f8403740bea924c967bf3964
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288873"
---
# <a name="code-a-custom-validation-rule-for-a-web-performance-test"></a>웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩

사용자의 고유한 유효성 검사 규칙을 만들 수 있습니다. 그러려면 유효성 검사 규칙 클래스에서 사용자의 규칙 클래스를 파생시킵니다. 유효성 검사 규칙은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 기본 클래스에서 파생됩니다.

> [!NOTE]
> 사용자 지정 추출 규칙을 만들 수도 있습니다. 자세한 내용은 [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)를 참조합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-custom-validation-rules"></a>사용자 지정 유효성 검사 규칙을 만들려면

1. 웹 성능 테스트를 포함하는 테스트 프로젝트를 엽니다.

2. (선택 항목) 유효성 검사 규칙을 저장할 별도의 클래스 라이브러리 프로젝트를 만듭니다.

    > [!IMPORTANT]
    > 테스트가 포함되어 있는 프로젝트에 클래스를 만들 수 있습니다. 그러나 규칙을 다시 사용하려면 규칙을 저장할 별도의 클래스 라이브러리 프로젝트를 만드는 것이 좋습니다. 별도의 프로젝트를 만드는 경우 이 절차의 선택 항목 단계를 수행해야 합니다.

3. (선택 항목) 클래스 라이브러리 프로젝트에서 Microsoft.VisualStudio.QualityTools.WebTestFramework DLL에 대한 참조를 추가합니다.

4. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 클래스에서 파생되는 클래스를 만듭니다. <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*> 멤버를 구현합니다.

5. (선택 항목) 새 클래스 라이브러리 프로젝트를 빌드합니다.

6. (선택 항목) 테스트 프로젝트에서 사용자 지정 유효성 검사 규칙을 포함하는 클래스 라이브러리 프로젝트에 대한 참조를 추가합니다.

7. 테스트 프로젝트에서 웹 성능 테스트를 **웹 성능 테스트 편집기**에서 엽니다.

8. 웹 성능 테스트 요청에 사용자 지정 유효성 검사 규칙을 추가하려면 요청을 마우스 오른쪽 단추로 클릭하고 **유효성 검사 규칙 추가**를 선택합니다.

     **유효성 검사 규칙 추가** 대화 상자가 나타납니다. **규칙 선택** 목록에 미리 정의된 유효성 검사 규칙과 함께 사용자 지정 유효성 검사 규칙이 표시됩니다. 사용자 지정 유효성 검사 규칙을 선택한 다음, **확인**을 선택합니다.

9. 웹 성능 테스트를 실행합니다.

## <a name="example"></a>예제

다음 코드에서는 사용자 지정 유효성 검사 규칙의 구현을 보여 줍니다. 이 유효성 검사 규칙은 미리 정의된 필요한 태그 유효성 검사 규칙의 동작을 모방합니다. 이 예제를 출발점으로 삼아 사용자 지정 유효성 검사 규칙을 직접 만들 수 있습니다.

> [!WARNING]
> 사용자 지정 유효성 검사기에 대한 코드에서 public 속성은 null 값이 아니어야 합니다.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurrences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurrences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [웹 성능 테스트에 대한 사용자 지정 추출 규칙 코딩](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
