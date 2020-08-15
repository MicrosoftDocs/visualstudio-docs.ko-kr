---
title: 레거시 언어 Service2 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df44b92cdf311689397a062b127d4c3e514a15e6
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238701"
---
# <a name="implementing-a-legacy-language-service-2"></a>레거시 언어 서비스 구현 2
MPF (관리 되는 패키지 프레임 워크)를 사용 하 여 언어 서비스를 구현 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.LanguageService> 다음 추상 메서드 및 속성을 구현 해야 합니다.

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 속성

  이러한 메서드 및 속성을 구현 하는 방법에 대 한 자세한 내용은 아래 해당 섹션을 참조 하세요.

  추가 기능을 지원 하기 위해 언어 서비스는 MPF 언어 서비스 클래스 중 하나에서 클래스를 파생 해야 할 수 있습니다. 예를 들어 추가 메뉴 명령을 지원 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.ViewFilter> 몇 가지 명령 처리 메서드를 재정의 해야 합니다 (자세한 내용은 참조 <xref:Microsoft.VisualStudio.Package.ViewFilter> ). <xref:Microsoft.VisualStudio.Package.LanguageService>클래스는 다양 한 클래스의 새 인스턴스를 만들기 위해 호출 되는 여러 메서드를 제공 하며, 적절 한 생성 메서드를 재정의 하 여 클래스의 인스턴스를 제공 합니다. 예를 들어 클래스의 메서드를 재정의 하 여 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 고유한 클래스의 인스턴스를 반환 해야 <xref:Microsoft.VisualStudio.Package.ViewFilter> 합니다. 자세한 내용은 "사용자 지정 클래스 인스턴스화" 섹션을 참조 하세요.

  언어 서비스는 다양 한 위치에서 사용 되는 고유한 아이콘을 제공할 수도 있습니다. 예를 들어 IntelliSense 완성 목록이 표시 되 면 목록의 각 항목에는 해당 항목을 메서드, 클래스, 네임 스페이스, 속성 또는 해당 언어에 필요한 것으로 표시 하 여 해당 항목에 연결 된 아이콘이 있을 수 있습니다. 이러한 아이콘은 모든 IntelliSense 목록, **탐색 모음**및 **오류 목록** 작업 창에서 사용 됩니다. 자세한 내용은 아래의 "언어 서비스 이미지" 섹션을 참조 하세요.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 메서드
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>메서드는 항상 클래스의 동일한 인스턴스를 반환 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . <xref:Microsoft.VisualStudio.Package.LanguagePreferences>언어 서비스에 대 한 추가 기본 설정이 필요 하지 않은 경우 기본 클래스를 사용할 수 있습니다. MPF 언어 서비스 클래스는 적어도 기본 클래스의 존재를 전제로 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

### <a name="example"></a>예
 이 예제에서는 메서드의 일반적인 구현을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> . 이 예제에서는 기본 클래스를 사용 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>GetScanner 메서드
 이 메서드는 <xref:Microsoft.VisualStudio.Package.IScanner> 토큰 및 해당 형식 및 트리거를 가져오는 데 사용 되는 줄 기반 파서 또는 스캐너를 구현 하는 개체의 인스턴스를 반환 합니다. 이 스캐너는 <xref:Microsoft.VisualStudio.Package.Colorizer> 더 복잡 한 구문 분석 작업에 대 한 prelude으로 토큰 형식 및 트리거를 가져오기 위해 사용 될 수도 있지만, 색 지정을 위해 클래스에서 사용 됩니다. 인터페이스를 구현 하는 클래스를 제공 하 <xref:Microsoft.VisualStudio.Package.IScanner> 고 인터페이스의 모든 메서드를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.IScanner> .

### <a name="example"></a>예
 이 예제에서는 메서드의 일반적인 구현을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> . `TestScanner`클래스는 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스 (표시 되지 않음)를 구현 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>ParseSource 메서드
 여러 가지 원인에 따라 소스 파일을 구문 분석 합니다. 이 메서드에는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 특정 구문 분석 작업에서 예상 되는 항목을 설명 하는 개체가 제공 됩니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>메서드는 토큰 기능 및 범위를 결정 하는 더 복잡 한 파서를 호출 합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>메서드는 중괄호 일치를 비롯 하 여 IntelliSense 작업을 지 원하는 데 사용 됩니다. 이러한 고급 작업을 지원 하지 않는 경우에도 유효한 개체를 반환 해야 하며이 경우 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 인터페이스를 구현 하는 클래스를 만들고 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 해당 인터페이스의 모든 메서드를 구현 해야 합니다. 모든 메서드에서 null 값을 반환할 수 있지만 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체 자체는 null 값이 아니어야 합니다.

### <a name="example"></a>예
 이 예제에서는 최소한의 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> 고급 기능을 지원 하지 않고 언어 서비스를 컴파일 및 작동 시킬 수 있는 메서드 및 클래스의 최소 구현을 보여 줍니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Name 속성
 이 속성은 언어 서비스의 이름을 반환 합니다. 언어 서비스를 등록할 때 지정 된 이름과 같아야 합니다. 이 이름은 여러 위치에서 사용 되며, 가장 두드러진 것은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 이름이 레지스트리에 액세스 하는 데 사용 되는 클래스입니다. 레지스트리 항목 및 키 이름에 대해 레지스트리에 사용 되므로이 속성에서 반환 된 이름은 지역화 되지 않아야 합니다.

### <a name="example"></a>예
 이 예제에서는 속성의 가능한 한 가지 구현을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> . 여기에 표시 되는 이름은 하드 코드 되어 있습니다. 언어 서비스를 등록 하는 데 사용할 수 있도록 실제 이름을 리소스 파일에서 가져와야 합니다 ( [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)참조).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>사용자 지정 클래스 인스턴스화
 지정 된 클래스의 다음 메서드를 재정의 하 여 각 클래스의 고유한 버전 인스턴스를 제공할 수 있습니다.

### <a name="in-the-languageservice-class"></a>LanguageService 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|텍스트 보기에 대 한 사용자 지정 추가를 지원 하려면입니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|사용자 지정 문서 속성을 지원 하려면입니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|**탐색 모음**을 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|코드 조각 템플릿에서 함수를 지원 하려면|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|코드 조각을 지원 하기 위해이 메서드는 일반적으로 재정의 되지 않습니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|구조체의 사용자 지정을 지원 하려면 <xref:Microsoft.VisualStudio.Package.ParseRequest> (일반적으로이 메서드는 재정의 되지 않음)|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|소스 코드 서식 지정, 주석 문자 지정 및 메서드 시그니처 사용자 지정을 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|추가 메뉴 명령을 지원 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|구문 강조 표시를 지원 하기 위해이 메서드는 일반적으로 재정의 되지 않습니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|언어 기본 설정에 대 한 액세스를 지원 합니다. 이 메서드는 구현 되어야 하지만 기본 클래스의 인스턴스를 반환할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|줄에서 토큰 유형을 식별 하는 데 사용 되는 파서를 제공 합니다. 이 메서드는 구현 되어야 하며 <xref:Microsoft.VisualStudio.Package.IScanner> 에서 파생 되어야 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|전체 소스 파일 전체에서 기능 및 범위를 식별 하는 데 사용 되는 파서를 제공 합니다. 이 메서드는 구현 되어야 하며 클래스 버전의 인스턴스를 반환 해야 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> . 지원 하려는 모든 것이 구문 강조 표시 (메서드에서 반환 된 파서가 필요 함) 인 경우에는 메서드가 <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 모두 null 값을 반환 하는 클래스 버전을 반환 하는 것 외에는이 메서드에서 아무것도 수행할 수 없습니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> .|

### <a name="in-the-source-class"></a>원본 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense 완성 목록의 표시를 사용자 지정 하는 경우 (일반적으로이 메서드는 재정의 되지 않음)|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|오류 목록 작업 목록에 있는 지원 표식 특히 파일 열기 이상의 기능을 지원 하 고 오류를 일으킨 줄로 이동 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense 매개 변수 정보 도구 설명의 표시를 사용자 지정 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|지원 주석 코드를 작성 합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|구문 분석 작업을 수행 하는 동안 정보를 수집 합니다.|

### <a name="in-the-authoringscope-class"></a>의 기관 클래스

|메서드|반환 된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|멤버 또는 형식과 같은 선언 목록을 제공 합니다. 이 메서드는 구현 되어야 하지만 null 값을 반환할 수 있습니다. 이 메서드가 유효한 개체를 반환 하는 경우 개체는 해당 버전의 클래스 인스턴스여야 합니다 <xref:Microsoft.VisualStudio.Package.Declarations> .|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|지정 된 컨텍스트에 대 한 메서드 시그니처의 목록을 제공 합니다. 이 메서드는 구현 되어야 하지만 null 값을 반환할 수 있습니다. 이 메서드가 유효한 개체를 반환 하는 경우 개체는 해당 버전의 클래스 인스턴스여야 합니다 <xref:Microsoft.VisualStudio.Package.Methods> .|

## <a name="language-service-images"></a>언어 서비스 이미지
 언어 서비스 전체에서 사용할 아이콘 목록을 제공 하려면 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 클래스의 메서드를 재정의 하 <xref:Microsoft.VisualStudio.Package.LanguageService> 고 아이콘이 포함 된을 반환 합니다 <xref:System.Windows.Forms.ImageList> . 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 기본 아이콘 집합을 로드 합니다. 아이콘이 필요한 위치에 정확한 이미지 인덱스를 지정 하기 때문에 고유한 이미지 목록을 정렬 하는 방법은 전적으로 사용자에 게 달려 있습니다.

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense 완성 목록에 사용 되는 이미지
 IntelliSense 완성 목록의 경우 이미지 인덱스는 클래스의 메서드에서 각 항목에 대해 지정 되며 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> , 이미지 인덱스를 제공 하려는 경우 재정의 해야 합니다. 메서드에서 반환 되는 값은 클래스 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 생성자에 제공 되는 이미지 목록에 대 <xref:Microsoft.VisualStudio.Package.CompletionSet> 한 인덱스이 고, 클래스의 메서드에서 반환 되는 것과 동일한 이미지 목록입니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> . 클래스에서 메서드를 재정의 하 여 <xref:Microsoft.VisualStudio.Package.Source> 다른 이미지 목록을 제공 하는 경우에 사용할 이미지 목록을 변경할 수 있습니다.

### <a name="images-used-in-the-navigation-bar"></a>탐색 모음에 사용 되는 이미지
 **탐색 모음은** 형식 및 멤버 목록을 표시 하 고 빠른 탐색에 사용 되는 아이콘을 표시 합니다. 이러한 아이콘은 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 클래스의 메서드에서 가져오며 <xref:Microsoft.VisualStudio.Package.LanguageService> **탐색 모음**에 대해 구체적으로 재정의할 수 없습니다. 콤보 상자의 각 항목에 사용 되는 인덱스는 콤보 상자를 나타내는 목록이 클래스의 메서드에 채워질 때 지정 됩니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> ( [레거시 언어 서비스의 탐색 모음에 대 한 지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)참조). 이러한 이미지 인덱스는 일반적으로 클래스의 버전을 통해 파서에서 가져옵니다 <xref:Microsoft.VisualStudio.Package.Declarations> . 인덱스를 가져오는 방법은 전적으로 사용자에 게 달려 있습니다.

### <a name="images-used-in-the-error-list-task-window"></a>오류 목록 작업 창에서 사용 되는 이미지
 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>메서드 파서 ( [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)참조)가 오류를 발견 하 고 해당 오류를 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 클래스의 메서드에 전달할 때마다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> **오류 목록** 작업 창에 오류가 보고 됩니다. 작업 창에 표시 되는 각 항목과 아이콘을 연결할 수 있으며, 해당 아이콘은 클래스의 메서드에서 반환 된 것과 동일한 이미지 목록에서 제공 됩니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . MPF 클래스의 기본 동작은 오류 메시지와 함께 이미지를 표시 하지 않는 것입니다. 그러나 클래스에서 클래스를 파생 <xref:Microsoft.VisualStudio.Package.Source> 시키고 메서드를 재정의 하 여이 동작을 재정의할 수 있습니다 <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> . 이 메서드에서는 새 개체를 만듭니다 <xref:Microsoft.VisualStudio.Package.DocumentTask> . 개체를 반환 하기 전에 개체의 속성을 사용 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> 하 여 <xref:Microsoft.VisualStudio.Package.DocumentTask> 이미지 인덱스를 설정할 수 있습니다. 이는 다음 예제와 같습니다. 는 `TestIconImageIndex` 모든 아이콘을 나열 하 고이 예제와 관련 된 열거형입니다. 언어 서비스에서 아이콘을 식별 하는 다른 방법을 사용할 수 있습니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>언어 서비스의 기본 이미지 목록
 기본 MPF 언어 서비스 클래스와 함께 제공 되는 기본 이미지 목록에는 보다 일반적인 언어 요소와 연결 된 여러 아이콘이 포함 되어 있습니다. 이러한 아이콘의 대부분은 공용, 내부, friend, 보호, 개인 및 바로 가기의 액세스 개념에 해당 하는 6 가지 변형 집합으로 정렬 됩니다. 예를 들어, public, protected 또는 private 인지에 따라 메서드에 다른 아이콘을 사용할 수 있습니다.

 다음 열거형은 각 아이콘 집합의 일반적인 이름을 지정 하 고 연결 된 인덱스를 지정 합니다. 예를 들어 열거형을 기반으로 보호 된 메서드에 대 한 이미지 인덱스를로 지정할 수 있습니다 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . 이 열거형의 이름을 원하는 대로 변경할 수 있습니다.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
