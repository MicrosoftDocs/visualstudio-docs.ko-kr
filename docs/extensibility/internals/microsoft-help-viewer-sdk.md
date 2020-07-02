---
title: Microsoft 도움말 뷰어 SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f79ead04e1c8a77ba605d4463bf8b2009f7ce71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536190"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft 도움말 뷰어 SDK

이 문서에는 Visual Studio 도움말 뷰어 통합자를 위한 다음과 같은 작업이 포함 되어 있습니다.

- 토픽 만들기 (F1 지원)

- 도움말 뷰어 콘텐츠-브랜딩 패키지 만들기

- 아티클 집합 배포

- Visual Studio 셸에 도움말 추가 (통합 또는 격리)

- 추가 리소스

## <a name="create-a-topic-f1-support"></a>토픽 만들기 (F1 지원)

이 섹션에서는 표시 된 항목의 구성 요소에 대 한 개요, 토픽 요구 사항, 토픽을 만드는 방법에 대 한 간단한 설명 (F1 지원 요구 사항 포함) 및 마지막으로 렌더링 된 결과가 포함 된 예제 항목을 제공 합니다.

**도움말 뷰어 항목 개요**

항목을 렌더링 하기 위해 호출 하는 경우 도움말 뷰어는 항목 XHTML과 함께 설치 또는 마지막 업데이트 시 토픽에 연결 된 브랜딩 패키지 요소를 가져오고, 두 항목을 결합 된 콘텐츠 보기 (브랜딩 데이터 + 토픽 데이터)로 결합 합니다.  브랜딩 패키지에는 로고, 콘텐츠 동작 지원 및 브랜딩 텍스트 (저작권 등)가 포함 되어 있습니다.  브랜딩 패키지 요소에 대 한 자세한 내용은 아래의 "브랜딩 패키지 만들기"를 참조 하세요.  항목에 연결 된 브랜딩 패키지가 없는 경우 도움말 뷰어는 도움말 뷰어 응용 프로그램 루트 Branding_en (.mshc)에 있는 대체 (fallback) 브랜딩 패키지를 사용 합니다.

**도움말 뷰어 토픽 요구 사항**

도움말 뷰어 내에서 올바르게 렌더링 되려면 원시 토픽 콘텐츠가 W3C Basic 1.1 XHTML 이어야 합니다.

토픽에는 일반적으로 다음 두 섹션이 포함 되어 있습니다.

- 메타 데이터 (콘텐츠 메타 데이터 참조 참조): 항목에 대 한 데이터 (예: 고유 ID, 키워드 값, 항목 TOC ID, 부모 노드 ID 등)입니다.

- 본문 내용: 지원 되는 콘텐츠 동작 (축소 가능 영역, 코드 조각 등)을 포함 하는 W3C Basic 1.1 XHTML과 호환 됩니다. 전체 목록은 아래와 같습니다.

Visual Studio 브랜딩 패키지 지원 컨트롤:

- 링크

- CodeSnippet

- CollapsibleArea

- 상속 된 멤버

- LanguageSpecificText

지원 되는 언어 문자열 (대/소문자 구분 안 함):

- javascript

- csharp 또는 c #

- cplusplus 또는 visualc + + 또는 c + +

- jscript

- microsoft.visualbasic 또는 vb

- f # 또는 fsharp.core 또는 fs

- 기타-언어 이름을 나타내는 문자열입니다.

**도움말 뷰어 항목 만들기**

ContosoTopic4.htm 이라는 새 XHTML 문서를 만들고 title 태그 (아래)를 포함 합니다.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

다음으로, 데이터를 추가 하 여 토픽을 표시 하는 방법 (자체 브랜드 또는 not), F1에 대해이 항목을 참조 하는 방법,이 항목이 TOC 내에 존재 하는 방법, 해당 ID (다른 토픽에서 링크 참조) 등을 정의 합니다. 지원 되는 메타 데이터의 전체 목록은 아래의 "콘텐츠 메타 데이터" 표를 참조 하세요.

- 이 경우 Visual Studio 도움말 뷰어 브랜딩 패키지의 변형 인 고유한 브랜딩 패키지를 사용 합니다.

- IDE 속성 모음에서 제공 된 F1 값과 일치 하는 F1 meta 이름 및 값 ("ContosoTopic4")을 추가 합니다. 자세한 내용은 F1 지원 섹션을 참조 하십시오. Ide에서 f1 키를 선택할 때이 항목을 표시 하기 위해 IDE 내에서 F1 호출에 일치 하는 값입니다.

- 토픽 ID를 추가 합니다. 다른 토픽에서이 항목에 연결 하는 데 사용 하는 문자열입니다. 이 항목의 도움말 뷰어 ID입니다.

- TOC의 경우이 항목의 부모 노드를 추가 하 여이 토픽 TOC 노드가 표시 되는 위치를 정의 합니다.

- TOC의 경우이 항목의 노드 순서를 추가 합니다. 부모 노드에 `n` 자식 노드가 여러 개 있는 경우이 항목의 위치를 자식 노드의 순서로 정의 합니다. 예를 들어이 항목은 4 개 자식 항목의 숫자 4입니다.

예제 메타 데이터 섹션:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**항목 본문**

항목의 본문 (머리글 및 바닥글 제외)에는 페이지 링크, 메모 섹션, 축소 가능한 영역, 코드 조각, 언어별 텍스트의 섹션이 포함 됩니다.  제공 된 항목의 해당 영역에 대 한 자세한 내용은 브랜딩 섹션을 참조 하세요.

1. 토픽 제목 태그를 추가 합니다.`<div class="title">Contoso Topic 4</div>`

2. 참고 섹션 추가:`<div class="alert"> add your table tag and text </div>`

3. 축소 가능한 영역 추가:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 코드 조각을 추가 합니다.`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 코드 언어 관련 텍스트 추가: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` `devLangnu=` 다른 언어를 입력할 수 있습니다. 예를 들어 `devLangnu="Fortran"` 는 코드 조각 DisplayLanguage = 포트란 인 경우 포트란을 표시 합니다.

6. 페이지 링크 추가:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 참고: 지원 되지 않는 새 "표시 언어" (예: F #, Cobol, 포트란)의 경우 코드 조각에서 코드 색 지정은 단색입니다.

**예제 도움말 뷰어 항목** 코드는 메타 데이터, 코드 조각, 축소 가능한 영역 및 언어별 텍스트를 정의 하는 방법을 보여 줍니다.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1 지원**

Visual Studio에서 F1 키를 선택 하면 IDE 내에서 커서를 배치 하 여 제공 된 값이 생성 되 고 "속성 모음"이 커서 위치에 기반 하 여 제공 된 값으로 채워집니다. 커서가 x 기능을 사용 하는 경우에는 기능 x가 활성 상태이 고 포커스가 있을 때 속성 모음을 값으로 채웁니다.  F1 키를 선택 하면 속성 모음이 채워지고 Visual Studio F1 코드는 고객의 기본 도움말 원본이 로컬 또는 온라인 인지 확인 합니다 (온라인이 기본값). 그런 다음 사용자 설정 (온라인)-셸 실행을 기반으로 적절 한 문자열을 만듭니다. 로컬 도움말이 기본값 인 경우에는 속성 모음에서 로컬 도움말 뷰어 + 키워드에 대 한 매개 변수를 사용 합니다 (exe 시작 매개 변수에 대 한 도움말 관리자 가이드 참조). 또는 매개 변수 목록에서 키워드를 사용 하는 MSDN URL

다중 값 문자열 이라고 하는 F1에 대해 3 개의 문자열을 반환 하는 경우 첫 번째 용어를 사용 하 고 적중 항목을 찾은 후 완료 되 면 완료 됩니다. 그렇지 않은 경우 다음 문자열로 이동 합니다.  순서가 중요 합니다. 다중값 키워드의 프레젠테이션은 가장 짧은 문자열에 가장 긴 문자열 이어야 합니다.  다중 값 키워드의 경우이를 확인 하려면 온라인 F1 URL 문자열을 확인 합니다. 여기에는 선택한 키워드가 포함 됩니다.

Visual Studio 2012에서 의도적으로 온라인 및 오프 라인 간에 더 강력한 분할을 만들었습니다. 따라서 사용자 설정이 온라인 인 경우 Visual Studio 2010에 있던 도움말 라이브러리 에이전트를 통해 라우팅하는 대신 F1 요청을 MSDN의 온라인 쿼리 서비스로 직접 전달 합니다. 그런 다음 "공급 업체 콘텐츠 설치 됨 = true" 상태를 사용 하 여 해당 컨텍스트에서 다른 작업을 수행할지 여부를 결정 합니다. True 이면 고객에 대 한 지원 대상에 따라이 구문 분석 및 라우팅 논리를 수행 합니다. False 이면 MSDN으로 이동 하면 됩니다. 사용자 설정이 Local 인 경우 모든 호출은 로컬 도움말 엔진으로 이동 합니다.

F1 흐름 다이어그램:

![F1 흐름](../../extensibility/internals/media/f1flow.png "F1flow")

도움말 뷰어 기본 도움말 콘텐츠 원본이 온라인으로 설정 된 경우 (브라우저에서 시작):

- VSP (Visual Studio Partner) 기능은 F1 속성 모음 (속성 모음 접두사. 키워드 및 레지스트리에서 찾은 접두사의 온라인 URL)에 값을 내보냅니다. F1 키를 누르면 VSP URL + 매개 변수가 브라우저에 전송 됩니다.

- Visual Studio 기능 (언어 편집기, Visual Studio 특정 메뉴 항목 등): F1 키를 누르면 Visual Studio URL이 브라우저에 전송 됩니다.

도움말 뷰어 기본 도움말 콘텐츠 원본이 로컬 도움말로 설정 된 경우 (도움말 뷰어에서 시작):

- .VSP 기능 F1 속성 모음과 로컬 저장소 인덱스 (즉, 속성 모음 접두사. keyword = 로컬 저장소 인덱스에 있는 값) 간에 키워드가 일치 하는 경우 F1 키를 누르면 도움말 뷰어에서 항목이 렌더링 됩니다.

- Visual Studio 기능 (VSP에서 Visual Studio 기능에서 내보낸 속성 모음을 재정의 하는 옵션 없음): F1 도움말 뷰어에서 Visual Studio 항목을 렌더링 합니다.

공급 업체 도움말 콘텐츠에 대해 F1 대체를 사용 하도록 설정 하려면 다음 레지스트리 값을 설정 합니다. F1 대체 (Fallback)는 도움말 뷰어가 F1 도움말 콘텐츠를 온라인으로 찾도록 설정 되어 있으며, 공급 업체 콘텐츠가 사용자의 하드 드라이브에 로컬로 설치 되어 있음을 의미 합니다. 도움말 뷰어는 온라인 도움말에 대 한 기본 설정인 경우에도 콘텐츠에 대 한 로컬 도움말을 확인 해야 합니다.

1. Help 2.3 레지스트리 키 아래에서 **VendorContent** 값을 설정 합니다.

   - 32 비트 운영 체제의 경우:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword: 00000001

   - 64 비트 운영 체제의 경우:

        HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = dword: 00000001

2. Help 2.3 레지스트리 키 아래에 partner 네임 스페이스를 등록 합니다.

   - 32 비트 운영 체제의 경우:

      HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.3\Partner<em> \\<네임 \> 스페이스</em>

      "location" = "offline"

   - 64 비트 운영 체제의 경우:

      HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em> \\<네임 \> 스페이스</em>

      "location" = "offline"

**기본 네이티브 네임 스페이스 구문 분석**

기본 네이티브 네임 스페이스 구문 분석을 켜려면 레지스트리의 새 DWORD를 이름: BaseNativeNamespaces에 추가 하 고 해당 값을 1 (지원 하려는 카탈로그 키 아래)로 설정 합니다.  예를 들어 Visual Studio 카탈로그를 사용 하려는 경우 다음 경로에 키를 추가할 수 있습니다.

HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Format 헤더/메서드에서 F1 키워드를 발견 하면 '/' 문자가 구문 분석 되어 다음 구문이 생성 됩니다.

- 헤더:는 레지스트리에 등록 하는 데 사용할 수 있는 네임 스페이스가 됩니다.

- 메서드:이는 전달 되는 키워드가 됩니다.

예를 들어 CustomLibrary 라는 사용자 지정 라이브러리와 MyTestMethod 라는 메서드가 지정 된 경우 F1 요청이 들어오면로 형식이 지정 됩니다 `CustomLibrary/MyTestMethod` .

그런 다음 사용자는 CustomLibrary를 파트너 hive 아래에 네임 스페이스로 등록 하 고 원하는 위치 키를 제공할 수 있으며 쿼리에 전달 되는 키워드는 MyTestMethod가 됩니다.

**IDE에서 도움말 디버깅 도구 사용**

다음 레지스트리 키 및 값을 추가 합니다.

::: moniker range="vs-2017"

**HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\15.0\Dynamic 도움말**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\16.0\Dynamic 도움말**

::: moniker-end

값: 소매 데이터에서 디버그 출력 표시: 예

IDE의 도움말 메뉴 항목에서 **디버그 도움말 컨텍스트**를 선택 합니다.

**콘텐츠 메타 데이터**

다음 표에서 대괄호 사이에 표시 되는 모든 문자열은 인식 된 값으로 바꾸어야 하는 자리 표시자입니다. 예를 들어에서 \<meta name="Microsoft.Help.Locale" content="[language code]" /> "[언어 코드]"는 "en-us"와 같은 값으로 바꾸어야 합니다.

| 속성 (HTML 표시) | 설명 |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | 이 항목에 대 한 로캘을 설정 합니다. 이 태그가 토픽에서 사용 되는 경우 한 번만 사용 해야 하며 다른 Microsoft 도움말 태그 위에 삽입 해야 합니다. 이 태그를 사용 하지 않으면 제품 로캘과 연결 된 단어 분리기 (지정 된 경우)를 사용 하 여 항목의 본문 텍스트가 인덱싱됩니다. 그렇지 않으면 en-us 단어 분리기가 사용 됩니다. 이 태그는 ISOC RFC 4646을 준수 합니다. Microsoft 도움말이 제대로 작동 하도록 하려면 일반 언어 특성 대신이 속성을 사용 합니다. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | 다른 로캘이 사용 될 때이 항목에 대 한 로캘을 설정 합니다. 이 태그가 토픽에서 사용 되는 경우 한 번만 사용 해야 합니다. 카탈로그에 둘 이상의 언어로 된 콘텐츠가 포함 된 경우이 태그를 사용 합니다. 카탈로그의 여러 항목은 동일한 ID를 가질 수 있지만 각 항목은 고유한 TopicLocale를 지정 해야 합니다. 카탈로그의 로캘과 일치 하는 TopicLocale를 지정 하는 항목은 목차에 표시 되는 항목입니다. 그러나 항목의 모든 언어 버전은 검색 결과에 표시 됩니다. |
| \< title>제목과\</title> | 이 항목의 제목을 지정 합니다. 이 태그는 필수 이며 항목에서 한 번만 사용 해야 합니다. 토픽 본문에 제목 섹션이 포함 되어 있지 않은 경우에는 \<div> 이 제목이 토픽 및 목차에 표시 됩니다. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | 도움말 뷰어의 인덱스 창에 표시 되는 링크 텍스트를 지정 합니다. 링크를 클릭 하면 항목이 표시 됩니다. 토픽에 대해 여러 인덱스 키워드를 지정 하거나이 항목에 대 한 링크가 인덱스에 표시 되지 않도록 하려면이 태그를 생략할 수 있습니다. 이전 버전 도움말의 "K" 키워드를이 속성으로 변환할 수 있습니다. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | 이 항목에 대 한 식별자를 설정 합니다. 이 태그는 필수 이며 항목에서 한 번만 사용 해야 합니다. ID는 동일한 로캘 설정을 가진 카탈로그의 토픽에서 고유 해야 합니다. 다른 항목에서는이 ID를 사용 하 여이 항목에 대 한 링크를 만들 수 있습니다. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | 이 항목에 대 한 F1 키워드를 지정 합니다. 토픽에 대해 여러 F1 키워드를 지정 하거나 응용 프로그램 사용자가 F1 키를 누를 때이 항목을 표시 하지 않으려면이 태그를 생략할 수 있습니다. 일반적으로 토픽에는 하나의 F1 키워드만 지정 됩니다. 이전 버전의 도움말에서 "F" 키워드를이 속성으로 변환할 수 있습니다. |
| \< meta name="Description" content="[topic description]" /> | 이 항목의 내용에 대 한 간략 한 요약을 제공 합니다. 이 태그가 토픽에서 사용 되는 경우 한 번만 사용 해야 합니다. 이 속성은 쿼리 라이브러리에서 직접 액세스 합니다. 인덱스 파일에 저장 되지 않습니다. |
| meta name = "Microsoft. Help. TocParent" content = "[parent_Id]"/> | 목차의이 항목에 대 한 부모 항목을 지정 합니다. 이 태그는 필수 이며 항목에서 한 번만 사용 해야 합니다. 값은 부모의 Microsoft.Help.Id입니다. 토픽의 목차에는 하나의 위치만 있을 수 있습니다. "-1"은 TOC 루트의 토픽 ID로 간주 됩니다. 에서 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 이 페이지는 도움말 뷰어 홈 페이지입니다. 이는 특정 항목에 TocParent =-1을 추가 하 여 최상위 수준에 표시 되도록 하는 것과 같은 이유입니다. 도움말 뷰어 홈 페이지는 시스템 페이지 이므로 대체 불가능 합니다. VSP에서 ID가-1 인 페이지를 추가 하려고 하면 콘텐츠 집합에 추가 될 수 있지만 도움말 뷰어는 항상 시스템 페이지-도움말 뷰어 홈을 사용 합니다. |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | 이 항목의 목차에서 피어 항목을 기준으로 표시 되는 위치를 지정 합니다. 이 태그는 필수 이며 항목에서 한 번만 사용 해야 합니다. 이 값은 정수입니다. 하위 값 정수를 지정 하는 토픽은 상위 값 정수를 지정 하는 토픽 위에 표시 됩니다. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | 이 항목에서 설명 하는 제품을 지정 합니다. 이 태그가 토픽에서 사용 되는 경우 한 번만 사용 해야 합니다. 이 정보는 도움말 인덱서에 전달 되는 매개 변수로 제공 될 수도 있습니다. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | 이 항목에서 설명 하는 제품의 버전을 지정 합니다. 이 태그가 토픽에서 사용 되는 경우 한 번만 사용 해야 합니다. 이 정보는 도움말 인덱서에 전달 되는 매개 변수로 제공 될 수도 있습니다. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | 제품에서 콘텐츠의 하위 섹션을 식별 하는 데 사용 됩니다. 토픽의 여러 하위 섹션을 식별 하거나, 링크를 통해 하위 섹션을 식별 하지 않으려면이 태그를 생략할 수 있습니다. 이 태그는 이전 버전의 도움말에서 토픽을 변환할 때 TargetOS 및 TargetFrameworkMoniker에 대 한 특성을 저장 하는 데 사용 됩니다. 콘텐츠 형식은 AttributeName: AttributeValue입니다. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | 카탈로그에 여러 버전이 있을 경우이 항목의 버전을 지정 합니다. Microsoft.Help.Id은 고유성이 보장 되지 않기 때문에 카탈로그에 여러 버전의 항목이 있는 경우 (예: 카탈로그에 .NET Framework 3.5에 대 한 토픽 및 .NET Framework 4에 대 한 항목이 포함 되어 있고 둘 다 동일한 Microsoft.Help.Id 경우)이 태그가 필요 합니다. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | 이 항목에서 도움말 라이브러리 관리자 시작 브랜딩 패키지를 사용할지 아니면 항목에 해당 하는 브랜딩 패키지를 사용할지를 지정 합니다. 이 태그는 TRUE 또는 FALSE 여야 합니다. TRUE 인 경우 관련 항목에 대 한 브랜딩 패키지는 도움말 라이브러리 관리자가 시작 될 때 설정 된 브랜딩 패키지를 재정의 하 여 항목이 다른 콘텐츠의 렌더링과 다른 경우에도 의도 한 대로 렌더링 되도록 합니다. FALSE 이면 도움말 라이브러리 관리자가 시작 될 때 설정 된 브랜딩 패키지에 따라 현재 항목이 렌더링 됩니다. 기본적으로 SelfBranded 변수가 TRUE로 선언 되지 않은 경우 도움말 라이브러리 관리자는 자체 브랜딩을 false로 가정 합니다. 따라서를 선언할 필요가 없습니다 \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>브랜딩 패키지 만들기

Visual studio 릴리스는 Visual Studio 파트너를 위한 격리 된 셸 및 통합 셸을 비롯 한 다양 한 Visual Studio 제품을 포함 합니다.  이러한 각 제품에는 제품에 고유한 특정 수준의 토픽 기반 도움말 콘텐츠 브랜딩 지원이 필요 합니다.  예를 들어, Visual Studio 토픽은 일관 된 브랜드 프레젠테이션을 포함 해야 하는 반면, ISO 셸을 래핑하는 SQL Studio에는 각 항목에 대 한 고유한 도움말 콘텐츠 브랜딩이 필요 합니다.  통합 셸 파트너는 자신의 토픽 브랜딩을 유지 하면서 해당 도움말 항목이 부모 Visual Studio 제품 도움말 콘텐츠 내에 포함 되도록 할 수 있습니다.

브랜딩 패키지는 도움말 뷰어를 포함 하는 제품에 의해 설치 됩니다.  Visual Studio 제품의 경우:

- 대체 (fallback) 브랜딩 패키지 Branding_ (.mshc)는 도움말 뷰어 \<locale> 언어 팩에서 도움말 뷰어 2.3 앱 루트 (예: C:\Program files (x86) \Microsoft Help Viewer\v2.3)에 설치 됩니다.  제품 브랜딩 패키지가 설치 되지 않았거나 (콘텐츠가 설치 되지 않음) 설치 된 브랜딩 패키지가 손상 된 경우에 사용 됩니다.  앱 루트 대체 (fallback) 브랜딩 패키지를 사용 하는 경우 Visual Studio 요소 (로고 및 피드백)는 무시 됩니다.

- 콘텐츠 패키지 서비스에서 Visual Studio 콘텐츠가 설치 될 때 브랜딩 패키지 (최초 콘텐츠 설치 시나리오의 경우)도 설치 됩니다.  브랜딩 패키지에 대 한 업데이트가 있는 경우 업데이트는 다음 콘텐츠 업데이트 또는 추가 패키지 설치 작업을 수행할 때 설치 됩니다.

Microsoft 도움말 뷰어는 토픽 메타 데이터를 기반으로 토픽의 브랜딩을 지원 합니다.

- 여기서 토픽 메타 데이터는 자체 브랜드 = true를 정의 하 고 항목을 있는 그대로 렌더링 합니다. (브랜딩 만큼) 아무 작업도 수행 하지 않습니다.

- 토픽 메타 데이터는 자체 브랜드 = false를 정의 하 고 TopicVendor 메타 데이터 값과 연결 된 브랜딩 패키지를 사용 합니다.

- 토픽 메타 데이터에서 name = "TopicVendor" content =를 정의 하는 경우 \< branding package name in vendor MSHA> 콘텐츠 값에 정의 된 브랜딩 패키지를 사용 합니다.

- Visual Studio 카탈로그 내에는 브랜딩 패키지의 우선 순위가 적용 됩니다.  첫 번째 Visual Studio 기본 브랜딩이 적용 된 후 토픽 메타 데이터에 정의 되어 있고 연결 된 브랜딩 패키지 (설치 msha에 정의 된 대로)에서 지원 되는 경우 공급 업체에서 정의한 브랜딩이 재정의로 적용 됩니다.

일반적으로 브랜딩 요소는 세 가지 주요 범주로 나뉩니다.

- Header 요소 (예를 들어 피드백 링크, 조건부 고 지 사항 텍스트, 로고)

- 콘텐츠 동작 (예를 들어, 컨트롤 텍스트 요소 및 코드 조각 요소 확장/축소)

- 바닥글 요소 (예: 저작권)

브랜드 요소로 간주 되는 항목은 (이 사양에 자세히 설명 되어 있습니다.)

- 카탈로그/제품 로고 (예: Visual Studio)

- 피드백 링크 및 전자 메일 요소

- 고 지 사항 텍스트

- 저작권 텍스트

Visual Studio 도움말 뷰어 브랜딩 패키지의 지원 파일은 다음과 같습니다.

- 그래픽 (로고, 아이콘 등)

- Branding.js-콘텐츠 동작을 지 원하는 스크립트 파일

- Branding.xml-카탈로그 내용에서 일관 되 게 사용 되는 문자열입니다.  참고: branding.xml의 Visual Studio 지역화 텍스트 요소에 대해 _locID = ""를 포함 합니다. \<unique value>

- 브랜딩. 프레젠테이션 일관성을 위한 css 스타일 정의

- 인쇄. 일관 된 인쇄 된 프레젠테이션을 위한 css 스타일 정의

위에서 설명한 것 처럼 브랜딩 패키지는 토픽에 연결 됩니다.

- 메타 데이터에 SelfBranded = false가 정의 되 면 토픽은 카탈로그 브랜딩 패키지를 상속 합니다.

- 또는 SelfBranded = false 인 경우 MSHA에 정의 된 고유한 브랜딩 패키지가 있고 콘텐츠가 설치 될 때 사용할 수 있습니다.

사용자 지정 브랜딩 패키지 (.VSP content, SelfBranded = True)를 구현 하는 .Vsps의 경우 계속 하는 한 가지 방법은 대체 브랜딩 패키지 (도움말 뷰어와 함께 설치 됨)로 시작 하 고 파일의 이름을 적절 하 게 변경 하는 것입니다.  \<locale>.Mshc 파일은 파일 확장명이. .mshc로 변경 된 zip 파일 이므로 .mshc를 .zip으로 변경 하 고 내용을 추출 하기만 하면 됩니다. Branding_  아래에서 브랜딩 패키지 요소를 확인 하 고 적절 하 게 수정 합니다. 예를 들어, 로고를 VSP 로고로 변경 하 고 Branding.xml 파일의 로고에 대 한 참조를 변경 하 고, VSP 별 특성 등을 업데이트 Branding.xml 합니다.

모든 수정 작업이 완료 되 면 원하는 브랜딩 요소를 포함 하는 zip 파일을 만들고 확장을. .mshc로 변경 합니다.

사용자 지정 브랜딩 패키지를 연결 하려면 콘텐츠 .mshc (토픽 포함)와 함께 브랜딩 .mshc 파일에 대 한 참조를 포함 하는 MSHA를 만듭니다.  기본 MSHA를 만드는 방법은 아래 "MSHA"를 참조 하십시오.

Branding.xml 파일에는 토픽에이 포함 되어 있을 때 토픽의 특정 항목을 일관 되 게 렌더링 하는 데 사용 되는 요소의 목록이 포함 되어 있습니다 \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Branding.xml 파일의 Visual Studio 요소 목록은 다음과 같습니다.  이 목록은 사용자가 자신의 제품 브랜딩 요구를 충족 하기 위해 이러한 요소 (예: 로고, 피드백 및 저작권)를 수정 하는 ISO 셸를 위한 템플릿으로 사용 하기 위한 것입니다.

참고: "{n}"에 의해 확인 된 변수에는 코드 종속성이 있습니다. 이러한 값을 제거 하거나 변경 하면 오류가 발생 하 고 응용 프로그램의 작동이 중단 될 수 있습니다. 지역화 식별자 (예: _locID = "codesnippet. n")는 Visual Studio 브랜딩 패키지에 포함 되어 있습니다.

**Branding.xml**

| | |
| - | - |
| 기능: | **CollapsibleArea** |
| 사용: | 축소 콘텐츠 컨트롤 텍스트 확장 |
| **요소** | **값** |
| ExpandText | Expand |
| CollapseText | 축소 |
| 기능: | **CodeSnippet** |
| 사용: | 코드 조각 컨트롤 텍스트입니다.  참고: "중단 없는" 공간이 있는 코드 조각 콘텐츠가 공백으로 변경 됩니다. |
| **요소** | **값** |
| CopyToClipboard | 클립보드로 복사 |
| ViewColorizedText | 색 보기 |
| CombinedVBTabDisplayLanguage | Visual Basic (샘플) |
| VBDeclaration | 선언 |
| VBUsage | 사용 |
| 기능: | **사용자 의견, 바닥글 및 로고** |
| 사용: | 고객이 전자 메일을 통해 현재 항목에 대 한 피드백을 제공할 수 있도록 피드백 컨트롤을 제공 합니다.  콘텐츠의 저작권 텍스트입니다.  로고 정의. |
| **요소** | **값 (이러한 문자열은 콘텐츠 도입자 요구를 충족 하도록 수정할 수 있습니다.)** |
| 저작권이 | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>\</a>Microsoft에이 항목에 대 한 사용자 의견을 보냅니다. |
| No-results-found-feedbacklink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| 기능: | **고지 사항** |
| 사용: | 기계 번역 콘텐츠에 대 한 대/소문자 관련 대/소문자 집합입니다. |
| **요소** | **값** |
| MT_Editable | 이 문서는 기계 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| MT_NonEditable | 이 문서는 기계 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| MT_QualityEditable | 이 문서는 수동으로 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| MT_QualityNonEditable | 이 문서는 수동으로 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| MT_BetaContents | 이 문서는 예비 릴리스에 대해 기계 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| MT_BetaRecycledContents | 이 문서는 예비 릴리스에 대해 수동으로 번역 되었습니다. 인터넷에 연결 되어 있는 경우 "온라인에서이 항목 보기"를 선택 하면이 페이지를 편집 가능 모드에서 원본 영어 콘텐츠와 함께 볼 수 있습니다. |
| 기능: | **LinkTable** |
| 사용: | 온라인 항목 링크에 대 한 지원 |
| **요소** | **값** |
| LinkTableTitle | 테이블 연결 |
| TopicEnuLinkText | \</a>컴퓨터에서 사용할 수 있는이 항목의 영어 버전을 확인 합니다. |
| TopicOnlineLinkText | 온라인으로이 항목 보기 \<a href="{0}" {1}>\</a> |
| OnlineText | 온라인 |
| 기능: | **비디오 오디오 컨트롤** |
| 사용: | 비디오 콘텐츠의 표시 요소 및 텍스트 |
| **요소** | **값** |
| Multimedian이상 지원 됨 | 콘텐츠를 지원 하려면 Internet Explorer 9 이상이 설치 되어 있어야 합니다 {0} . |
| 비디오 텍스트 | 비디오 표시 |
| 텍스트 텍스트 | 오디오 스트리밍 |
| OnlineVideoLinkText | \<p>이 항목과 관련 된 비디오를 보려면 여기를 클릭 {0} \<a href="{1}"> {2} \</a> 하세요.\</p> |
| OnlineAudioLinkText | \<p>이 항목과 연결 된 오디오를 수신 하려면 여기를 클릭 {0} \<a href="{1}"> {2} \</a> 하세요.\</p> |
| 기능: | **콘텐츠가 설치 되지 않은 컨트롤** |
| 사용: | contentnotinstalled.htm 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| ContentNotInstalledTitle | 컴퓨터에서 콘텐츠를 찾을 수 없습니다. |
| ContentNotInstalledDownloadContentText | \<p>컴퓨터에 콘텐츠를 다운로드 하려면 \<a href="{0}" {1}> 관리 탭을 클릭 \</a> 합니다.\</p> |
| ContentNotInstalledText | \<p>컴퓨터에 콘텐츠가 설치 되어 있지 않습니다. 로컬 도움말 콘텐츠 설치는 관리자에 게 문의 하십시오.\</p> |
| 기능: | **항목을 찾을 수 없음 컨트롤** |
| 사용: | topicnotfound.htm 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| TopicNotFoundTitle | 컴퓨터에서 요청한 항목을 찾을 수 없습니다. |
| TopicNotFoundViewOnlineText | \<p>요청한 항목을 컴퓨터에서 찾을 수 없지만 온라인에서 항목을 볼 수 있습니다 \<a href="{0}" {1}> \</a> .\</p> |
| TopicNotFoundDownloadContentText | \<p>유사한 항목에 대 한 링크를 보려면 탐색 창을 참조 하거나, \<a href="{0}" {1}> [관리] 탭을 클릭 \</a> 하 여 컴퓨터에 콘텐츠를 다운로드 하십시오.\</p> |
| TopicNotFoundText | \<p>요청한 항목을 컴퓨터에서 찾을 수 없습니다.\</p> |
| 기능: | **항목 손상 된 컨트롤** |
| 사용: | topiccorrupted.htm 렌더링에 사용 되는 텍스트 요소 (문자열) |
| **요소** | **값** |
| TopicCorruptedTitle | 요청한 항목을 표시할 수 없습니다. |
| TopicCorruptedViewOnlineText | \<p>도움말 뷰어에서 요청한 항목을 표시할 수 없습니다. 항목의 내용 또는 기본 시스템 종속성에 오류가 있을 수 있습니다.\</p> |
| 기능: | **홈 페이지 컨트롤** |
| 사용: | 도움말 뷰어 최상위 노드 콘텐츠의 표시를 지 원하는 텍스트입니다. |
| **요소** | **값** |
| HomePageTitle | 도움말 뷰어 홈 |
| HomePageIntroduction | \<p>Microsoft 도구, 제품, 기술 및 서비스를 사용 하는 모든 사용자에 게 필수적인 정보 원본인 Microsoft 도움말 뷰어를 시작 합니다. 도움말 뷰어를 사용 하면 방법 및 참조 정보, 샘플 코드, 기술 문서 등에 액세스할 수 있습니다. 필요한 콘텐츠를 찾으려면 목차를 찾아보거나 전체 텍스트 검색을 사용 하거나 키워드 인덱스를 사용 하 여 콘텐츠를 탐색 합니다.\</p> |
| HomePageContentInstallText | \<p>\<br />\<a href="{0}" {1}>콘텐츠 관리 \</a> 탭을 사용 하 여 다음 작업을 수행할 수 \<ul> \<li> 있습니다. 컴퓨터에 콘텐츠를 추가 합니다. \</li> \<li> 로컬 콘텐츠에 대 한 업데이트를 확인 합니다. \</li> \<li> 컴퓨터에서 콘텐츠를 제거 합니다.\</li>\</ul>\</p> |
| HomePageInstalledBooks | 설치 된 서적 |
| HomePageNoBooksInstalled | 컴퓨터에서 콘텐츠를 찾을 수 없습니다. |
| HomePageHelpSettings | 도움말 콘텐츠 설정 |
| HomePageHelpSettingsText | \<p>현재 설정은 로컬 도움말입니다. 도움말 뷰어에는 컴퓨터에 설치한 콘텐츠가 표시 됩니다. \<br /> 도움말 콘텐츠의 소스를 변경 하려면 Visual Studio 메뉴 모음에서 \<span style="{0}"> 도움말, 도움말 기본 설정 지정을 선택 \</span> 합니다.\<br />\</p> |
| 200Mb | MB |

**branding.js**

branding.js 파일에는 Visual Studio 도움말 뷰어 브랜딩 요소에 사용 되는 JavaScript가 포함 되어 있습니다.  다음은 브랜딩 요소 및 지원 JavaScript 함수 목록입니다.  이 파일에 대해 지역화할 모든 문자열은이 파일의 맨 위에 있는 "지역화할 수 있는 문자열" 섹션에 정의 되어 있습니다.  branding.js 파일 내에서 loc 문자열에 대해 ICL 파일이 생성 되었습니다.

|**브랜딩 기능**|**JavaScript 함수**|**설명**|
|-|-|-|
|Var ...||변수 정의|
|사용자 코드 언어 가져오기|setUserPreferenceLang|인덱스 #에 코드 언어 매핑|
|쿠키 값 설정 및 가져오기|getCookie, setCookie||
|상속 된 멤버|changeMembersLabel|상속 된 멤버 확장/축소|
|When SelfBranded = False|onLoad|쿼리 문자열을 읽어 인쇄 요청 인지 확인 합니다.  모든 codesnippets를 설정 하 여 사용자의 기본 설정 탭에 집중 합니다.  인쇄 요청 인 경우 isPrinterFriendly를 true로 설정 합니다. 고대비 모드를 확인 합니다.|
|코드 조각|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|축소 가능한 모든 컨트롤 개체를 목록에 씁니다.|
||CA_Click|축소할 수 있는 영역의 상태를 기준으로, 표시할 이미지 및 텍스트를 정의 합니다.|
|로고에 대 한 대비 지원|Is블랙 배경 ()|배경이 검은색 인지 여부를 확인 하기 위해 호출 됩니다.  고대비 모드의 경우에만 정확 합니다.|
||isHighContrast()|색이 지정 된 범위를 사용 하 여 고대비 모드 검색|
||onHighContrast (검정)|고대비가 검색 되 면 호출 됩니다.|
|.LST 기능|||
||addToLanSpecTextIdSet (id)||
||updateLST (currentLang)||
||getDevLangFromCodeSnippet (lang)||
|멀티미디어 기능|캡션 (시작, 끝, 텍스트, 스타일)||
||findAllMediaControls(normalizedId)||
||getActivePlayer (normalizedId)||
||captionsOnOff (id)||
||toSeconds (t)||
||getAllComments (노드)||
||styleRectify (styleName, styleValue)||
||showCC (id)||
||부제목 (id)||

**HTM 파일**

브랜딩 패키지에는 콘텐츠 사용자에 게 유용한 정보를 제공 하는 기능을 지 원하는 HTM 파일 집합이 포함 되어 있습니다. 예를 들어, 설치 되는 콘텐츠 집합을 설명 하는 섹션과 항목의 로컬 항목에서 항목을 찾을 수 없는 경우 사용자에 게 알려 주는 페이지가 포함 된 홈 페이지가 있습니다. 이러한 HTM 파일은 제품 별로 수정할 수 있습니다.  ISO 셸 공급 업체는 기본 브랜딩 패키지를 사용 하 여 이러한 페이지의 동작과 콘텐츠를 요구 사항에 맞게 변경할 수 있습니다.  이러한 파일은 브랜딩 태그가 branding.xml 파일에서 해당 콘텐츠를 가져오기 위해 각 브랜딩 패키지를 참조 합니다.

|**최근에 사용한 파일**|**사용**|**표시 된 콘텐츠 원본**|
|-|-|-|
|homepage.htm|현재 설치 된 콘텐츠를 표시 하는 페이지 및 해당 콘텐츠에 대 한 사용자에 게 제공 되는 기타 모든 메시지입니다.  이 파일에는이 콘텐츠를 로컬 콘텐츠 TOC의 맨 위에 배치 하는 추가 메타 데이터 특성 "Microsoft.Help.Id" content = "-1"이 있습니다.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, 태그\<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, 태그\<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, 태그\<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|책을 설치 하지 않은 경우 제목 섹션 Branding.xml 태그 \<HomePageInstalledBooks> , 응용 프로그램에서 생성 된 데이터 \<HomePageNoBooksInstalled> 입니다.|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|제목 섹션 Branding.xml 태그 \<HomePageHelpSettings> , 섹션 텍스트 \<HomePageHelpSettingsText> 입니다.|
|topiccorrupted.htm|항목이 로컬 집합에 있지만 어떤 이유로 든 표시할 수 없는 경우 (손상 된 콘텐츠)||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, 태그\<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, 태그\<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|로컬 콘텐츠 집합에 항목이 없거나 온라인에서 사용할 수 없는 경우||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, 태그\<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, 태그\<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, 태그\<TopicNotFoundText>|
|contentnotinstalled.htm|제품에 대 한 로컬 콘텐츠가 설치 되어 있지 않은 경우||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, 태그\<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, 태그\<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, 태그\<ContentNotInstalledText>|

**CSS 파일**

Visual Studio 도움말 뷰어 브랜딩 패키지에는 일관성 있는 Visual Studio 도움말 콘텐츠 프레젠테이션을 지 원하는 두 개의 css 파일이 포함 되어 있습니다.

- SelfBranded = false 인 렌더링을 위한 css 요소를 포함 합니다.

- 프린터인-SelfBranded = false 인 렌더링을 위한 css 요소를 포함 합니다.

브랜딩 .css 파일에는 Visual Studio 토픽 프레젠테이션 정의가 포함 되어 있습니다. 즉, 패키지 서비스의 .mshc Branding_에 포함 된에 포함 된 내용이 \<locale> 변경 될 수 있습니다.

**그래픽 파일**

Visual Studio 콘텐츠는 Visual Studio 로고 및 기타 그래픽을 표시 합니다.  Visual Studio 도움말 뷰어 브랜딩 패키지의 전체 그래픽 파일 목록은 아래와 같습니다.

|**최근에 사용한 파일**|**사용**|**예**|
|-|-|-|
|clear.gif|축소 가능한 영역을 렌더링 하는 데 사용 됩니다.||
|footer_slice.gif|바닥글 프레젠테이션||
|info_icon.gif|정보를 표시할 때 사용 됩니다.|고지 사항|
|online_icon.gif|이 아이콘은 온라인 링크와 연결 됩니다.||
|tabLeftBD.gif|코드 조각 컨테이너를 렌더링 하는 데 사용 됩니다.||
|tabRightBD.gif|코드 조각 컨테이너를 렌더링 하는 데 사용 됩니다.||
|vs_logo_bk.gif|Branding.xml 태그에 정의 된 일반 대비 로고 참조에 사용 \<LogoFileName> 됩니다.  Visual Studio 제품의 경우 로고 이름이 vs_logo_bk.gif 됩니다.||
|vs_logo_wh.gif|Branding.xml 태그에 정의 된 일반적인 고품질 로고 참조에 사용 \<LogoFileNameHC> 됩니다.  Visual Studio 제품의 경우 로고 이름이 vs_logo_wh.gif 됩니다.||
|ccOff.png|캡션 그래픽||
|ccOn.png|캡션 그래픽||
|ImageSprite.png|축소 가능한 영역을 렌더링 하는 데 사용 됩니다.|확장 또는 축소 그래픽|

## <a name="deploy-a-set-of-topics"></a>항목 집합 배포

MSHA 파일과 토픽을 포함 하는 cab 또는 MSHCs 집합으로 구성 된 도움말 뷰어 콘텐츠 배포 집합을 만드는 간단한 자습서입니다. MSHA는 cab 또는 .MSHC 파일 집합을 설명 하는 XML 파일입니다. 도움말 뷰어는 MSHA를 읽어 콘텐츠 목록을 가져올 수 있습니다 (. CAB 또는. .MSHC files)를 로컬 설치에 사용할 수 있습니다.

이는 도움말 뷰어 MSHA의 기본 XML 스키마를 설명 하는 입문에 불과합니다.  이 간략 한 개요 및 샘플 HelpContentSetup에 대 한 예제 구현이 있습니다.

이 입문의 목적을 위해 MSHA의 이름은 HelpContentSetup. msha (확장명이 인 모든 이름일 수 있습니다. MSHA). HelpContentSetup. msha (아래 예제)에는 사용 가능한 cab 또는 MSHCs 목록이 포함 되어 있어야 합니다.  파일 형식은 MSHA 내에서 일치 해야 합니다 (MSHA 및 CAB 파일 형식의 조합을 지원 하지 않음). 각 CAB 또는 .mshc에 대해 ... \<div class="package"> \</div> (아래 예제 참조)가 있어야 합니다.

참고: 아래 구현 예제에서는 브랜딩 패키지를 포함 했습니다. 필요한 Visual Studio 콘텐츠 렌더링 요소 및 콘텐츠 동작을 얻기 위해이를 포함 하는 것이 중요 합니다.

샘플 HelpContentSetup. msha 파일: ("content set name 1" 및 "content set name 2" 등을 파일 이름으로 바꿉니다.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. "C:\SampleContent"와 같은 로컬 폴더를 만듭니다.

2. 이 예제에서는 .MSHC 파일을 사용 하 여 항목을 포함 합니다.  .MSHC는 파일 확장명이 .zip에서로 변경 된 zip입니다. .MSHC.

3. 아래 HelpContentSetup. msha를 텍스트 파일로 만들고 (메모장을 사용 하 여 파일을 만든 후) 위의 설명 된 폴더에 저장 합니다 (1 단계 참조).

"브랜딩" 클래스가 있으며 고유 합니다. 브랜딩 .mshc 설치 된 콘텐츠에 브랜딩이 포함 되 고 MSHCs에 포함 된 콘텐츠 동작에 브랜딩 패키지에 포함 된 적절 한 지원 요소가 포함 되도록이 입문에 포함 됩니다. 이렇게 하지 않으면 시스템이 리핑한 (설치 된) 콘텐츠의 일부가 아닌 지원 항목을 찾을 때 오류가 발생 합니다.

Visual Studio 브랜딩 패키지를 가져오려면 C:\Program Files (x86) \Microsoft Help Viewer\v2.3\의 Branding_en-.mshc 파일을 작업 폴더에 복사 합니다.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**요약**

위의 단계를 사용 하 고 확장 하면 .Vsps에서 Visual Studio 도움말 뷰어에 대 한 콘텐츠 집합을 배포할 수 있습니다.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Visual Studio 셸에 도움말 추가 (통합 및 격리)

**소개**

이 연습에서는 Visual Studio Shell 응용 프로그램에 도움말 콘텐츠를 통합 한 다음 배포 하는 방법을 보여 줍니다.

**요구 사항**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 격리 된 셸 재배포 가능 패키지](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**개요**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]셸은 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 응용 프로그램의 기반으로 사용할 수 있는 IDE의 버전입니다. 이러한 응용 프로그램에는 사용자가 만든 확장과 함께 격리 셸이 포함 되어 있습니다. SDK에 포함 된 격리 된 셸 프로젝트 템플릿을 사용 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 하 여 확장을 빌드합니다.

격리 된 셸 기반 응용 프로그램 및 해당 도움말을 만드는 기본 단계는 다음과 같습니다.

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ISO 셸 재배포 가능 패키지 (Microsoft 다운로드)를 다운로드 합니다.

2. Visual Studio에서이 연습의 뒷부분에서 설명 하는 Contoso Help extension과 같은 Isolated 셸을 기반으로 하는 도움말 확장을 만듭니다.

3. 확장 및 ISO 셸 재배포 가능 패키지를 배포 MSI (응용 프로그램 설치)로 래핑합니다. 이 연습에는 설치 단계가 포함 되지 않습니다.

Visual Studio 콘텐츠 저장소를 만듭니다. 통합 셸 시나리오의 경우 다음과 같이 Visual Studio12를 제품 카탈로그 이름으로 변경 합니다.

- C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15. 폴더 만들기

- CatalogType.xml 라는 파일을 만들고 폴더에 추가 합니다. 파일에는 다음 코드 줄이 포함 되어야 합니다.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

레지스트리에서 콘텐츠 저장소를 정의 합니다. 통합 셸에서 VisualStudio15을 제품 카탈로그 이름으로 변경 합니다.

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   키: LocationPath 문자열 값: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   키: CatalogName 문자열 값: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 설명서

**프로젝트 만들기**

격리 된 셸 확장을 만들려면 다음을 수행 합니다.

1. Visual Studio의 **파일**에서 **새 프로젝트**를 선택 하 고 **기타 프로젝트 형식** 에서 **확장성**을 선택한 다음 **Visual Studio Shell 격리**를 선택 합니다. 프로젝트 이름 `ContosoHelpShell` )을 사용 하 여 Visual Studio 격리 셸 템플릿을 기반으로 하는 확장성 프로젝트를 만듭니다.

2. 솔루션 탐색기의 ContosoHelpShellUI 프로젝트에 있는 리소스 파일 폴더에서 ApplicationCommands. vsct를 엽니다. 이 줄이 주석 처리 되었는지 확인 합니다 ("No_Help" 검색).`<!-- <define name="No_HelpMenuCommands"/> -->`

3. F5 키를 선택 하 여 컴파일하고 **디버그**를 실행 합니다. 격리 된 셸 IDE의 실험적 인스턴스에서 **도움말** 메뉴를 선택 합니다. 도움말 **보기**, **도움말 콘텐츠 추가 및 제거**및 **도움말 기본 설정 명령 설정이** 표시 되는지 확인 합니다.

4. 솔루션 탐색기의 ContosHelpShell 프로젝트에 있는 Shell 사용자 지정 폴더에서 ContosoHelpShell. .pkgdef를 엽니다. Contoso Help catalog를 정의 하려면 다음 줄을 추가 합니다.

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. 솔루션 탐색기의 ContosHelpShell 프로젝트에 있는 Shell 사용자 지정 폴더에서 ContosoHelpShell .pkgdef를 엽니다. F1 도움말을 사용 하려면 다음 줄을 추가 합니다.

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. 솔루션 탐색기의 ContosoHelpShell 솔루션에 대 한 상황에 맞는 메뉴에서 **속성** 메뉴 항목을 선택 합니다. **구성 속성**에서 **Configuration Manager**를 선택 합니다. **구성** 열에서 모든 "Debug" 값을 "Release"로 변경 합니다.

7. 솔루션을 빌드합니다. 그러면 다음 섹션에서 사용 되는 릴리스 폴더에 파일 집합이 만들어집니다.

배포 된 경우로 테스트 하려면 다음을 수행 합니다.

1. Contoso를 배포 하는 컴퓨터에서 다운로드 한 (위) ISO 셸을 설치 합니다.

2. Filefiles \\ (x86)에서 폴더를 만들고 \\ 이름을로 `Contoso` 합니다.

3. ContosoHelpShell release 폴더의 콘텐츠를 \\ filefiles (x86) \Contoso\ 폴더에 복사 합니다.

4. **시작** 메뉴에서 **실행** 을 선택 하 고를 입력 하 여 레지스트리 편집기를 시작 `Regedit` 합니다. 레지스트리 편집기에서 **파일**, **가져오기**를 차례로 선택 합니다. ContosoHelpShell 프로젝트 폴더로 이동 합니다. ContosoHelpShell 하위 폴더에서 ContosoHelpShell를 선택 합니다.

5. 콘텐츠 저장소를 만듭니다.

    ISO Shell-Contoso content store C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 만들기

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]통합 셸의 경우 C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15 폴더를 만듭니다.

6. CatalogType.xml를 만들고 다음을 포함 하는 콘텐츠 저장소 (이전 단계)에를 추가 합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. 다음 레지스트리 키를 추가 합니다.

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath 문자열 값:

    ISO Shell의 경우:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]통합 셸:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    키: CatalogName 문자열 값: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 설명서. ISO 셸에서는 카탈로그의 이름입니다.

8. 콘텐츠 (cab 또는 .MSHC 및 MSHA)를 로컬 폴더에 복사 합니다.

9. 콘텐츠 저장소 테스트에 대 한 예제 통합 셸 명령줄입니다. ISO 셸에서 카탈로그 및 launchingApp 값을 제품 일치에 적합 하 게 변경 합니다.

     "C:\Program Files (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe"/catalogName VisualStudio15/helpQuery method = "page&id = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12.0

10. Contoso 앱 루트에서 Contoso 응용 프로그램을 시작 합니다. ISO Shell 내에서 **도움말** 메뉴 항목을 선택 하 고 **도움말 기본 설정** 지정을 **로컬 도움말 사용**으로 변경 합니다.

11. 셸 내에서 **도움말** 메뉴 항목을 선택 하 고 **도움말을 봅니다**. 로컬 도움말 뷰어를 시작 해야 합니다. **콘텐츠 관리** 탭을 선택 합니다. **설치 원본**에서 **디스크** 옵션 단추를 선택 합니다. **...** 단추를 선택 하 고 위의 단계에서 로컬 폴더에 복사 된 Contoso 콘텐츠를 포함 하는 로컬 폴더로 이동 합니다. HelpContentSetup. msha를 선택 합니다. 이제 Contoso는 책 선택 항목에 책으로 표시 되어야 합니다. **추가**를 선택한 다음 **업데이트** 단추 (오른쪽 아래 모서리)를 선택 합니다.

12. Contoso IDE 내에서 f1 키를 선택 하 여 F1 기능을 테스트 합니다.

## <a name="additional-resources"></a>추가 리소스

런타임 API에 대 한 자세한 내용은 [Windows 도움말 API](/previous-versions/windows/desktop/helpapi/helpapi-portal)를 참조 하세요.

도움말 API를 활용 하는 방법에 대 한 자세한 내용은 [도움말 뷰어 코드 예제](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)를 참조 하세요.

[개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에서 기능 제안을 제출할 수 있습니다.
