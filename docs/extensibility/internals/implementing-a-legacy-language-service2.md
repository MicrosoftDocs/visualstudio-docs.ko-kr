---
title: 레거시 언어 서비스 구현2 | 마이크로 소프트 문서
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
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707669"
---
# <a name="implementing-a-legacy-language-service"></a>레거시 언어 서비스 구현
MPF(관리되는 패키지 프레임워크)를 사용하여 언어 서비스를 구현하려면 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스에서 클래스를 파생하고 다음과 같은 추상메서드 및 속성을 구현해야 합니다.

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 속성

  이러한 메서드 및 속성 구현에 대한 자세한 내용은 아래 의 해당 섹션을 참조하십시오.

  추가 기능을 지원하려면 언어 서비스가 MPF 언어 서비스 클래스 중 하나에서 클래스를 파생해야 할 수 있습니다. 예를 들어 추가 메뉴 명령을 지원하려면 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스에서 클래스를 파생하고 여러 명령 처리 방법을 <xref:Microsoft.VisualStudio.Package.ViewFilter> 재정의해야 합니다(자세한 내용은 참조). 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService> 다양한 클래스의 새 인스턴스를 만들기 위해 호출되는 여러 메서드를 제공하며 클래스의 인스턴스를 제공하기 위해 적절한 만들기 메서드를 재정의합니다. 예를 들어 자신의 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스의 인스턴스를 반환하려면 클래스의 메서드를 재정의해야 합니다. 자세한 내용은 "사용자 지정 클래스 인스턴스화" 섹션을 참조하십시오.

  언어 서비스는 여러 곳에서 사용되는 자체 아이콘을 제공할 수도 있습니다. 예를 들어 IntelliSense 완료 목록이 표시되면 목록의 각 항목에 연결된 아이콘이 있을 수 있으며 해당 항목에는 메서드, 클래스, 네임스페이스, 속성 또는 언어에 필요한 모든 항목으로 표시할 수 있습니다. 이러한 아이콘은 모든 IntelliSense 목록, **탐색 모음**및 오류 **목록** 작업 창에서 사용됩니다. 자세한 내용은 아래의 "언어 서비스 이미지" 섹션을 참조하십시오.

## <a name="getlanguagepreferences-method"></a>GetLanguage환경 설정 방법
 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 항상 클래스의 동일한 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 인스턴스를 반환합니다. 언어 서비스에 대한 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 추가 기본 설정이 필요하지 않은 경우 기본 클래스를 사용할 수 있습니다. MPF 언어 서비스 클래스는 최소한 기본 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스가 있다고 가정합니다.

### <a name="example"></a>예제
 이 예제에서는 메서드의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 일반적인 구현을 보여 주입니다. 이 예제에서는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 기본 클래스를 사용합니다.

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

## <a name="getscanner-method"></a>겟스캐너 방법
 이 메서드는 토큰 <xref:Microsoft.VisualStudio.Package.IScanner> 및 해당 형식 및 트리거를 가져오는 데 사용되는 선 지향 파서 또는 스캐너를 구현하는 개체의 인스턴스를 반환합니다. 이 스캐너는 색상화를 위해 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스에서 사용되지만 스캐너는 토큰 유형 및 트리거를 보다 복잡한 구문 분석 작업의 전주곡으로 사용할 수도 있습니다. <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스를 구현하는 클래스를 제공해야 하며 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스에서 모든 메서드를 구현해야 합니다.

### <a name="example"></a>예제
 이 예제에서는 메서드의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 일반적인 구현을 보여 주입니다. 클래스는 `TestScanner` 인터페이스를 <xref:Microsoft.VisualStudio.Package.IScanner> 구현합니다(표시되지 않음).

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

## <a name="parsesource-method"></a>구문 분석 소스 방법
 여러 가지 이유로 원본 파일을 구문 분석합니다. 이 메서드는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 특정 구문 분석 작업에서 예상 되는 것을 설명 하는 개체가 지정 됩니다. 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 토큰 기능 및 범위를 결정 하는 더 복잡 한 파서를 호출 합니다. 이 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드는 IntelliSense 작업과 중괄호 일치를 지원하는 데 사용됩니다. 이러한 고급 작업을 지원하지 않더라도 여전히 유효한 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체를 반환해야 하며 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 인터페이스를 구현하고 해당 인터페이스에서 모든 메서드를 구현하는 클래스를 만들어야 합니다. 모든 메서드에서 null 값을 반환할 수 있지만 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체 자체는 null 값이 아니어야 합니다.

### <a name="example"></a>예제
 이 예제에서는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드와 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스의 최소한의 구현을 보여 주며, 언어 서비스가 실제로 고급 기능을 지원하지 않고 컴파일하고 작동할 수 있도록 하기에 충분합니다.

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
 이 속성은 언어 서비스의 이름을 반환합니다. 이 이름은 언어 서비스가 등록되었을 때 와 같아야 합니다. 이 이름은 여러 위치에서 사용되며, 그 중 가장 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 눈에 띄는 이름은 레지스트리에 액세스하는 데 이름이 사용되는 클래스입니다. 이 속성에서 반환되는 이름은 레지스트리 항목 및 키 이름에 대한 레지스트리에서 사용되기 때문에 지역화되어서는 안 됩니다.

### <a name="example"></a>예제
 이 예제에서는 속성의 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 가능한 구현을 보여 주며 있습니다. 여기에 있는 이름은 하드 코딩되어 있습니다: 언어 서비스 등록에 사용할 수 있도록 리소스 파일에서 실제 이름을 가져와야 [합니다(레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)참조).

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
 지정된 클래스의 다음 메서드를 재정의하여 각 클래스의 고유한 버전의 인스턴스를 제공할 수 있습니다.

### <a name="in-the-languageservice-class"></a>언어 서비스 클래스에서

|방법|반환된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|텍스트 보기에 사용자 지정 추가를 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|사용자 지정 문서 속성을 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|**탐색 모음을**지원합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|코드 조각 템플릿의 함수를 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|코드 조각을 지원하려면(이 메서드는 일반적으로 재정의되지 않음).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|구조의 사용자 지정을 <xref:Microsoft.VisualStudio.Package.ParseRequest> 지원하려면(이 메서드는 일반적으로 재정의되지 않음).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|소스 코드 서식 지정, 주석 문자 지정 및 메서드 서명 사용자 지정을 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|추가 메뉴 명령을 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|구문 강조 표시를 지원하려면 (이 메서드는 일반적으로 재정의되지 않음).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|언어 기본 설정에 대한 액세스를 지원합니다. 이 메서드는 구현해야 하지만 기본 클래스의 인스턴스를 반환할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|줄에서 토큰 유형을 식별하는 데 사용되는 파서를 제공합니다. 이 메서드는 구현되어야 하며 <xref:Microsoft.VisualStudio.Package.IScanner> 파생되어야 합니다.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|전체 소스 파일 전체에서 기능 및 범위를 식별하는 데 사용되는 파서를 제공합니다. 이 메서드는 구현되어야 하며 클래스 버전의 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 인스턴스를 반환해야 합니다. 지원하려는 모든 구문 강조 표시 <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (메서드에서 반환 된 파서가 필요)인 경우 메서드가 모두 null <xref:Microsoft.VisualStudio.Package.AuthoringScope> 값을 반환하는 클래스 버전을 반환하는 것 외에는이 메서드에서 아무 것도 할 수 없습니다.|

### <a name="in-the-source-class"></a>소스 클래스에서

|방법|반환된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense 완료 목록의 표시를 사용자 지정하려면(이 메서드는 일반적으로 재정의되지 않음).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|오류 목록 작업 목록에서 마커를 지원하기 위한 작업 목록; 특히 파일을 열고 오류를 일으킨 줄로 이동하지 않는 기능을 지원합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense 매개 변수 정보 도구 팁의 표시를 사용자 정의합니다.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|주석 코드 지원.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|구문 분석 작업 중에 정보를 수집합니다.|

### <a name="in-the-authoringscope-class"></a>작성 범위 클래스에서

|방법|반환된 클래스|설명|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|멤버 또는 형식과 같은 선언 목록을 제공합니다. 이 메서드는 구현해야 하지만 null 값을 반환할 수 있습니다. 이 메서드가 유효한 개체를 반환하는 경우 개체는 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스 버전의 인스턴스여야 합니다.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|지정된 컨텍스트에 대한 메서드 서명 목록을 제공합니다. 이 메서드는 구현해야 하지만 null 값을 반환할 수 있습니다. 이 메서드가 유효한 개체를 반환하는 경우 개체는 <xref:Microsoft.VisualStudio.Package.Methods> 클래스 버전의 인스턴스여야 합니다.|

## <a name="language-service-images"></a>언어 서비스 이미지
 언어 서비스 전체에서 사용할 아이콘 목록을 제공하려면 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 재정의하고 <xref:System.Windows.Forms.ImageList> 포함된 아이콘을 반환합니다. 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스는 기본 아이콘 집합을 로드합니다. 아이콘이 필요한 위치에 정확한 이미지 인덱스를 지정하므로 사용자 고유의 이미지 목록을 정렬하는 방법은 전적으로 사용자의 선택입니다.

### <a name="images-used-in-intellisense-completion-lists"></a>인텔리센스 완성 목록에 사용된 이미지
 IntelliSense 완료 목록의 경우 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> 이미지 인덱스를 제공하려는 경우 재정의해야 하는 클래스 메서드의 각 항목에 대해 이미지 인덱스가 지정됩니다. <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 메서드에서 <xref:Microsoft.VisualStudio.Package.CompletionSet> 반환 되는 값은 클래스 생성자에 제공 하는 이미지 목록에 인덱스이며 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 메서드에서 <xref:Microsoft.VisualStudio.Package.LanguageService> 반환 된 동일한 이미지 목록입니다 <xref:Microsoft.VisualStudio.Package.CompletionSet> (다른 이미지 <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> 목록을 제공 <xref:Microsoft.VisualStudio.Package.Source> 하려면 클래스의 메서드를 재정의 하는 경우 사용할 이미지 목록을 변경할 수 있습니다).

### <a name="images-used-in-the-navigation-bar"></a>탐색 모음에 사용된 이미지
 **탐색 모음에는** 유형 및 멤버 목록이 표시되며 빠른 탐색에 사용되어 아이콘이 표시될 수 있습니다. 이러한 아이콘은 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 메서드에서 가져오며 탐색 **모음에**대해 특별히 재정의할 수 없습니다. 콤보 상자의 각 항목에 사용되는 인덱스는 콤보 상자를 나타내는 목록이 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스의 메서드에 채워지면 지정됩니다(레거시 언어 서비스의 탐색 모음 [지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)참조). 이러한 이미지 인덱스는 일반적으로 <xref:Microsoft.VisualStudio.Package.Declarations> 클래스의 버전을 통해 파서에서 어떻게 든 가져옵니다. 인덱스를 얻는 방법은 전적으로 당신에게 달려 있습니다.

### <a name="images-used-in-the-error-list-task-window"></a>오류 목록 작업 창에 사용된 이미지
 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드 파마서(레거시 [언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)참조)에 오류가 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 발생하고 해당 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 오류를 클래스의 메서드에 전달할 때마다 **오류 목록** 작업 창에 오류가 보고됩니다. 아이콘은 작업 창에 나타나는 각 항목과 연결될 수 있으며 해당 아이콘은 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 메서드에서 반환된 동일한 이미지 목록에서 제공됩니다. MPF 클래스의 기본 동작은 오류 메시지가 있는 이미지를 표시하지 않는 것입니다. 그러나 클래스에서 클래스를 파생 하 고 메서드를 <xref:Microsoft.VisualStudio.Package.Source> 재정의 하 <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> 여이 동작을 재정의할 수 있습니다. 이 메서드에서는 새 <xref:Microsoft.VisualStudio.Package.DocumentTask> 개체를 만듭니다. 해당 개체를 반환하기 전에 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> <xref:Microsoft.VisualStudio.Package.DocumentTask> 개체의 속성을 사용하여 이미지 인덱스를 설정할 수 있습니다. 이것은 다음과 같은 예제와 같습니다. `TestIconImageIndex` 모든 아이콘을 나열하고 이 예제와 관련된 열거형입니다. 언어 서비스에서 아이콘을 식별하는 다른 방법이 있을 수 있습니다.

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
 기본 MPF 언어 서비스 클래스와 함께 제공되는 기본 이미지 목록에는 보다 일반적인 언어 요소와 연결된 여러 아이콘이 포함되어 있습니다. 이러한 아이콘의 대부분은 공용, 내부, 친구, 보호, 개인 및 바로 가기의 액세스 개념에 해당하는 여섯 가지 변형 집합으로 정렬됩니다. 예를 들어 메서드가 공용인지 보호된지 비공개인지에 따라 메서드에 대해 다른 아이콘을 가질 수 있습니다.

 다음 열거형은 각 아이콘 집합에 대한 일반적인 이름을 지정하고 관련 인덱스를 지정합니다. 예를 들어 열거형에 따라 보호된 메서드의 이미지 인덱스를 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`로 지정할 수 있습니다. 이 열거형의 이름을 원하는 대로 변경할 수 있습니다.

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
