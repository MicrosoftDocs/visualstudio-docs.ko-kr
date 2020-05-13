---
title: 레거시 언어 서비스의 사용자 지정 문서 속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708965"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>레거시 언어 서비스의 사용자 지정 문서 속성
문서 속성은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **속성** 창에 표시할 수 있습니다. 프로그래밍 언어에는 일반적으로 개별 소스 파일과 관련된 속성이 없습니다. 그러나 XML은 인코딩, 스키마 및 스타일시트에 영향을 주는 문서 속성을 지원합니다.

## <a name="discussion"></a>토론
 언어에 사용자 지정 문서 속성이 필요한 경우 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스에서 클래스를 파생하고 파생 클래스에 필요한 속성을 구현해야 합니다.

 또한 문서 속성은 일반적으로 원본 파일 자체에 저장됩니다. 이를 위해서는 언어 서비스가 속성 **창에** 표시하기 위해 소스 파일의 속성 정보를 구문 분석하고 **속성** 창의 문서 속성을 변경할 때 원본 파일을 업데이트해야 합니다.

## <a name="customize-the-documentproperties-class"></a>문서 속성 클래스 사용자 지정
 사용자 지정 문서 속성을 지원하려면 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스에서 클래스를 파생하고 필요한 만큼 속성을 추가해야 합니다. 또한 **속성** 창 표시에서 구성 할 사용자 특성을 제공해야합니다. 속성에 `get` 접근자만 있는 경우 **속성** 창에서 읽기 전용으로 표시됩니다. 속성에 모두 `get` `set` 및 접근자가 있는 경우 **속성** 창에서 속성을 업데이트할 수도 있습니다.

### <a name="example"></a>예제
 다음은 <xref:Microsoft.VisualStudio.Package.DocumentProperties>에서 `Filename` `Description`파생된 예제 클래스입니다. 속성이 업데이트되면 클래스의 사용자 <xref:Microsoft.VisualStudio.Package.LanguageService> 지정 메서드를 호출하여 소스 파일에 속성을 작성합니다.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>사용자 지정 문서속성 클래스 인스턴스화
 사용자 지정 문서 속성 클래스를 인스턴스화하려면 클래스의 단일 인스턴스를 <xref:Microsoft.VisualStudio.Package.LanguageService> 반환하려면 클래스 버전의 <xref:Microsoft.VisualStudio.Package.DocumentProperties> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> 메서드를 재정의해야 합니다.

### <a name="example"></a>예제

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>원본 파일의 속성
 문서 속성은 일반적으로 원본 파일에 만해당하므로 값은 원본 파일 자체에 저장됩니다. 이를 위해서는 이러한 속성을 정의하기 위해 언어 파서 또는 스캐너의 지원이 필요합니다. 예를 들어 XML 문서의 속성은 루트 노드에 저장됩니다. 루트 노드의 값은 **속성** 창 값이 변경되고 루트 노드가 편집기에서 업데이트될 때 수정됩니다.

### <a name="example"></a>예제
 이 예제에서는 `Filename` 속성과 `Description` 특수 주석 헤더에 포함된 소스 파일의 처음 두 줄에 다음과 같이 저장합니다.

```
//!Filename = file.testext
//!Description = A sample file
```

 이 예제에서는 원본 파일의 처음 두 줄에서 문서 속성을 얻고 설정하는 데 필요한 두 가지 방법과 사용자가 원본 파일을 직접 수정하는 경우 속성이 업데이트되는 방법을 보여 주십습니다. 여기에 `SetPropertyValue` 표시된 예제의 메서드는 DocumentProperties 사용자 `TestDocumentProperties` 지정 클래스 섹션에 표시된 클래스에서 호출된 *메서드와* 동일합니다.

 이 예제에서는 스캐너를 사용하여 처음 두 줄의 토큰 유형을 결정합니다. 이 예제는 설명용으로만 사용됩니다. 이 상황에 대한 보다 일반적인 방법은 소스 파일을 트리의 각 노드에 특정 토큰에 대한 정보가 포함된 구문 분석 트리로 구문 분석하는 것입니다. 루트 노드에는 문서 속성이 포함됩니다.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
