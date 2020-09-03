---
title: 레거시 언어 서비스의 사용자 지정 문서 속성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708965"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>레거시 언어 서비스의 사용자 지정 문서 속성
문서 속성은 속성 창에 표시 될 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Properties** . 프로그래밍 언어에는 일반적으로 개별 소스 파일과 연결 된 속성이 없습니다. 그러나 XML은 인코딩, 스키마 및 스타일 시트에 영향을 주는 문서 속성을 지원 합니다.

## <a name="discussion"></a>토론(Discussion)
 사용자 지정 문서 속성을 필요로 하는 언어의 경우 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 파생 클래스에서 필요한 속성을 구현 해야 합니다.

 또한 문서 속성은 일반적으로 소스 파일 자체에 저장 됩니다. 이렇게 하려면 언어 서비스가 **속성 창에** 표시할 소스 파일의 속성 정보를 구문 분석 하 고 **속성** 창에서 문서 속성이 변경 되 면 소스 파일을 업데이트 해야 합니다.

## <a name="customize-the-documentproperties-class"></a>DocumentProperties 클래스 사용자 지정
 사용자 지정 문서 속성을 지원 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 필요한 만큼 속성을 추가 해야 합니다. 또한 **속성** 창 화면에서 구성 하려면 사용자 특성도 제공 해야 합니다. 속성에 접근자만 있으면 `get` **속성** 창에 읽기 전용으로 표시 됩니다. 속성에 및 접근자가 모두 있으면 속성 `get` `set` 창에서 속성을 업데이트할 수도 있습니다. **Properties**

### <a name="example"></a>예
 다음은 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 두 개의 속성 및를 표시 하는에서 파생 된 클래스입니다 `Filename` `Description` . 속성이 업데이트 되 면 클래스의 사용자 지정 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 호출 하 여 소스 파일에 속성을 씁니다.

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

## <a name="instantiate-the-custom-documentproperties-class"></a>사용자 지정 DocumentProperties 클래스 인스턴스화
 사용자 지정 문서 속성 클래스를 인스턴스화하려면 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 단일 인스턴스를 반환 하도록 클래스 버전의 메서드를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.DocumentProperties> .

### <a name="example"></a>예

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

## <a name="properties-in-the-source-file"></a>소스 파일의 속성
 문서 속성은 일반적으로 소스 파일에만 적용 되므로 값은 소스 파일 자체에 저장 됩니다. 이러한 속성을 정의 하려면 언어 파서 또는 스캐너의 지원이 필요 합니다. 예를 들어 XML 문서의 속성은 루트 노드에 저장 됩니다. **속성** 창 값이 변경 되 고 루트 노드가 편집기에서 업데이트 되는 경우 루트 노드의 값이 수정 됩니다.

### <a name="example"></a>예
 이 예제에서는 `Filename` `Description` 다음과 같이 특수 주석 헤더에 포함 된 및 속성을 소스 파일의 처음 두 줄에 저장 합니다.

```
//!Filename = file.testext
//!Description = A sample file
```

 이 예제에서는 소스 파일의 처음 두 줄에서 문서 속성을 가져오고 설정 하는 데 필요한 두 가지 방법과 사용자가 소스 파일을 직접 수정 하는 경우 속성을 업데이트 하는 방법을 보여 줍니다. `SetPropertyValue`여기에 표시 된 예제의 메서드는 `TestDocumentProperties` *DocumentProperties 클래스 사용자 지정* 단원에 표시 된 것과 같은 클래스에서 호출 된 것과 같습니다.

 이 예제에서는 스캐너를 사용 하 여 처음 두 줄의 토큰 형식을 확인 합니다. 이 예는 설명을 위한 목적 으로만 사용 됩니다. 이러한 상황에 대 한 일반적인 방법은 트리의 각 노드에 특정 토큰에 대 한 정보가 들어 있는 구문 분석 트리를 원본 파일에 구문 분석 하는 것입니다. 루트 노드에는 문서 속성이 포함 됩니다.

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

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
