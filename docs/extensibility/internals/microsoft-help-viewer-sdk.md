---
title: 마이크로소프트 도움말 뷰어 SDK | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707147"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft 도움말 뷰어 SDK

이 문서에는 Visual Studio 도움말 뷰어 통합자에 대한 다음 작업이 포함되어 있습니다.

- 토픽 만들기(F1 지원)

- 도움말 뷰어 콘텐츠 브랜딩 패키지 만들기

- 문서 집합 배포

- Visual Studio 셸에 도움말 추가(통합 또는 격리)

- 추가 리소스

## <a name="create-a-topic-f1-support"></a>토픽 만들기(F1 지원)

이 섹션에서는 제시된 주제의 구성 요소, 주제 요구 사항, 주제를 만드는 방법에 대한 간단한 설명(F1 지원 요구 사항 포함) 및 마지막으로 렌더링된 결과가 있는 예제 항목에 대한 개요를 제공합니다.

**뷰어 주제 개요 도움말**

렌더링을 위해 토픽이 호출되면 도움말 뷰어는 XHTML 항목과 함께 설치 또는 마지막 업데이트 시 주제와 연관된 브랜딩 패키지 요소를 얻고 두 요소를 결합하여 제시된 콘텐츠 보기(브랜딩 데이터 + 토픽 데이터)를 생성합니다.  브랜딩 패키지에는 로고, 콘텐츠 행동 지원 및 브랜딩 텍스트(저작권 등)가 포함되어 있습니다.  브랜딩 패키지 요소에 대한 자세한 내용은 아래의 "브랜딩 패키지 만들기"를 참조하십시오.  주제와 관련된 브랜딩 패키지가 없는 경우 도움말 뷰어는 도움말 뷰어 응용 프로그램 루트(Branding_en-US.mshc)에 있는 대체 브랜딩 패키지를 사용합니다.

**뷰어 주제 요구 사항 도움말**

도움말 뷰어 내에서 올바르게 렌더링되려면 원시 토픽 콘텐츠가 W3C Basic 1.1 XHTML이어야 합니다.

토픽에는 일반적으로 다음 두 섹션이 포함되어 있습니다.

- 메타데이터(콘텐츠 메타데이터 참조 참조 참조): 토픽에 대한 데이터(예: 토픽 고유 ID, 키워드 값, 토픽 TOC ID, 상위 노드 ID 등)

- 본문 콘텐츠: 지원되는 콘텐츠 동작(축소 가능 영역, 코드 조각 등)을 포함하는 W3C Basic 1.1 XHTML을 준수합니다. 전체 목록은 다음과 같습니다).

비주얼 스튜디오 브랜딩 패키지 지원 컨트롤:

- 링크

- 코드스니펫

- 접이식 영역

- 상속된 멤버

- 언어특정텍스트

지원되는 언어 문자열(대/소문자 구분 아님):

- javascript

- c샤프 또는 c #

- cplusplus 또는 비주얼 ++ 또는 c ++

- Jscript

- 비주얼 베이직 또는 VB

- f # 또는 샤프 또는 FS

- 기타 - 언어 이름을 나타내는 문자열

**도움말 뷰어 항목 만들기**

ContosoTopic4.htm이라는 새 XHTML 문서를 만들고 제목 태그(아래)를 포함합니다.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

다음으로, 주제를 제시하는 방법(자체 브랜드 화 여부), F1에 대해 이 주제를 참조하는 방법, TOC 내에 이 주제가 있는 위치, 해당 ID(다른 토픽에 의한 링크 참조용) 등을 정의하는 데이터를 추가합니다. 지원되는 메타데이터의 전체 목록은 아래의 "콘텐츠 메타데이터" 표를 참조하십시오.

- 이 경우 Visual Studio 도움말 뷰어 브랜딩 패키지의 변형인 자체 브랜딩 패키지를 사용합니다.

- IDE 속성 가방에 제공된 F1 값과 일치하는 F1 메타 이름 및 값("Microsoft.Help.F1" 콘텐츠=" ContosoTopic4")을 추가합니다. 자세한 내용은 F1 지원 섹션을 참조하십시오. 이 값은 IDE 내에서 F1 호출과 일치하여 IDE에서 F1을 선택할 때 이 항목을 표시합니다.

- 주제 ID를 추가합니다. 이 항목에 연결하는 데 다른 항목에서 사용되는 문자열입니다. 이 항목의 도움말 뷰어 ID입니다.

- TOC의 경우 이 토픽의 상위 노드를 추가하여 이 토픽 TOC 노드가 표시되는 위치를 정의합니다.

- TOC의 경우 이 항목의 노드 순서를 추가합니다. 상위 노드에 `n` 자식 노드 수가 있는 경우 이 항목의 자식 노드 순서로 정의합니다. 예를 들어 이 항목은 하위 항목 4개 중 4번입니다.

메타데이터 섹션 예제:

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

**주제 본문**

주제의 본문(헤더 및 바닥글 제외)에는 페이지 링크, 메모 섹션, 축소 가능한 영역, 코드 조각 및 언어별 텍스트 섹션이 포함됩니다.  제시된 주제의 해당 영역에 대한 자세한 내용은 브랜딩 섹션을 참조하세요.

1. 주제 제목 태그 추가:`<div class="title">Contoso Topic 4</div>`

2. 메모 섹션 추가:`<div class="alert"> add your table tag and text </div>`

3. 축소 가능한 영역 추가:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. 코드 조각 추가:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. 코드 언어별 텍스트 `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` 추가: `devLangnu=` 다른 언어를 입력할 수 있습니다. 예를 들어 `devLangnu="Fortran"` 코드 스니펫 DisplayLanguage = 포트란이 포트란을 표시할 때 포트란을 표시합니다.

6. 페이지 링크 추가:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> 참고: 지원되지 않는 새 "표시 언어"(예: F#, 코볼, 포트란) 코드 조각의 코드 색상은 단색입니다.

**뷰어 도움말 주제 예제** 이 코드는 메타데이터, 코드 조각, 축소 가능한 영역 및 언어별 텍스트를 정의하는 방법을 보여 줍니다.

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

Visual Studio에서 F1을 선택하면 IDE 내의 커서 배치에서 제공된 값이 생성되고 제공된 값(커서 위치에 따라)이 포함된 "속성 백"이 채워집니다. 커서가 기능 x를 초과하면 피쳐 x가 활성/초점 상태이며 속성 가방에 값을 채웁니다.  F1이 선택되면 속성 가방이 채워지고 Visual Studio F1 코드가 고객 기본 도움말 소스가 로컬 또는 온라인인지 확인한 다음 사용자 설정(온라인이 기본값)에 따라 적절한 문자열을 만듭니다. 또는 매개 변수 목록에 키워드가 있는 MSDN URL입니다.

다중 값 문자열이라고 하는 F1에 대해 세 개의 문자열이 반환되면 첫 번째 용어를 사용하여 히트를 찾고 발견하면 완료됩니다. 그렇지 않은 경우 다음 문자열로 이동합니다.  주문이 중요합니다. 다중 값 키워드의 표시는 가장 짧은 문자열에 가장 긴 문자열이어야 합니다.  다중 값 키워드의 경우 이를 확인하려면 선택한 키워드가 포함된 온라인 F1 URL 문자열을 확인하십시오.

Visual Studio 2012에서는 의도적으로 온라인과 오프라인을 구분하여 사용자의 설정이 온라인용인 경우 Visual Studio 2010에 있는 도움말 라이브러리 에이전트를 통해 라우팅하는 대신 MSDN의 온라인 쿼리 서비스에 직접 F1 요청을 전달했습니다. 그런 다음 "설치된 공급업체 콘텐츠 = true"의 상태를 사용하여 해당 컨텍스트에서 다른 작업을 수행할지 여부를 결정합니다. true이면 고객을 지원하려는 항목에 따라 이 구문 분석 및 라우팅 논리를 수행합니다. 거짓이면 MSDN으로 이동합니다. 사용자의 설정이 Local인 경우 모든 호출은 로컬 도움말 엔진으로 이동합니다.

F1 흐름 다이어그램:

![F1 흐름](../../extensibility/internals/media/f1flow.png "F1플로우")

도움말 뷰어 기본 도움말 콘텐츠 원본이 온라인으로 설정된 경우(브라우저에서 시작):

- 비주얼 스튜디오 파트너(VSP) 기능은 F1 속성 가방(레지스트리에 있는 접두사에 대한 속성 가방 접두사.키워드 및 온라인 URL)에 값을 내보냅니다: F1은 브라우저에 VSP URL+ 매개변수를 보냅니다.

- Visual Studio 기능(언어 편집기, Visual Studio 특정 메뉴 항목 등): F1은 브라우저에 Visual Studio URL을 보냅니다.

도움말 뷰어 기본 도움말 콘텐츠 원본이 로컬 도움말로 설정된 경우(도움말 뷰어에서 시작):

- VSP는 F1 속성 가방과 로컬 저장소 인덱스 간의 키워드 일치(즉, 속성 가방 접두사.키워드 = 로컬 저장소 인덱스에 있는 값) 기능이 일치합니다.

- Visual Studio 기능(VSP가 Visual Studio 기능에서 내보낸 속성 가방을 재정의하는 옵션 없음): F1은 도움말 뷰어에서 Visual Studio 항목을 렌더링합니다.

공급업체 도움말 콘텐츠에 대한 F1 대체를 사용하도록 설정하려면 다음 레지스트리 값을 설정합니다. F1 대체는 도움말 뷰어가 온라인으로 F1 도움말 콘텐츠를 찾도록 설정되어 있고 공급업체 콘텐츠가 사용자의 하드 드라이브에 로컬로 설치된다는 것을 의미합니다. 도움말 뷰어는 기본 설정이 온라인 도움말인 경우에도 콘텐츠에 대한 로컬 도움말을 확인해야 합니다.

1. 도움말 2.3 레지스트리 키 아래에 **VendorContent** 값을 설정합니다.

   - 32비트 운영 체제의 경우:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "공급 업체 콘텐츠"=dword:00000001

   - 64비트 운영 체제의 경우:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\마이크로소프트\도움말\v2.3\카탈로그\VisualStudio15

        "공급 업체 콘텐츠"=dword:00000001

2. 도움말 2.3 레지스트리 키 아래에 파트너 네임스페이스를 등록합니다.

   - 32비트 운영 체제의 경우:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\도움말\v2.3\파트너<em> \\<네임스페이스\></em>

      "위치"="오프라인"

   - 64비트 운영 체제의 경우:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\마이크로소프트\도움말\v2.3\파트너<em> \\<네임스페이스\></em>

      "위치"="오프라인"

**기본 네이티브 네임스페이스 구문 분석**

기본 네이티브 네임스페이스 구문 분석 기능을 설정하려면 레지스트리에서 다음 이름인 BaseNativeNamespaces의 이름으로 새 DWORD를 추가하고 해당 값을 1로 설정합니다(지원하려는 카탈로그 키 아래).  예를 들어 Visual Studio 카탈로그를 사용하려는 경우 경로에 키를 추가할 수 있습니다.

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\마이크로소프트\도움말\v2.3\카탈로그\VisualStudio15

헤더/METHOD 형식의 F1 키워드가 발생하면 '/' 문자가 구문 분석되어 다음 구문이 생성됩니다.

- 헤더: 레지스트리에 등록하는 데 사용할 수 있는 네임스페이스가 됩니다.

- 메소드: 이 키워드는 통과되는 키워드가 됩니다.

예를 들어 사용자 지정 라이브러리라는 사용자 지정 라이브러리와 MyTestMethod라는 메서드가 주어지면 F1 `CustomLibrary/MyTestMethod`요청이 들어오면 .

그런 다음 사용자는 CustomLibrary를 파트너 하이브 아래에 있는 네임스페이스로 등록하고 원하는 위치 키를 제공할 수 있으며 쿼리에 전달된 키워드는 MyTestMethod입니다.

**IDE에서 도움말 디버깅 도구 사용**

다음 레지스트리 키 와 값을 추가합니다.

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\15.0\동적 도움말**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\16.0\동적 도움말**

::: moniker-end

값: 소매 데이터에 디버그 출력 표시: 예

IDE에서 도움말 메뉴 항목에서 **도움말 컨텍스트 디버그를**선택합니다.

**콘텐츠 메타데이터**

다음 표에서 괄호 사이에 나타나는 모든 문자열은 인식된 값으로 대체해야 하는 자리 표시자입니다. 예를 들어 \<메타 이름="Microsoft.Help.Locale" 콘텐츠="[언어 코드]" /> "[언어 코드]"는 "en-us"와 같은 값으로 대체되어야 합니다.

| 속성(HTML 표현) | 설명 |
| - | - |
| \<메타 이름="Microsoft.Help.Locale" 콘텐츠="[언어 코드]" /> | 이 항목에 대한 로캘을 설정합니다. 이 태그가 토픽에서 사용되는 경우 한 번만 사용해야 하며 다른 Microsoft 도움말 태그 위에 삽입해야 합니다. 이 태그를 사용하지 않으면 토픽의 본문 텍스트가 지정된 경우 제품 로캘과 연결된 단어 분리기를 사용하여 인덱싱됩니다. 그렇지 않으면 en-us 단어 분리기가 사용됩니다. 이 태그는 ISOC RFC 4646을 준수합니다. Microsoft 도움말이 올바르게 작동하는지 확인하려면 일반 언어 특성 대신 이 속성을 사용합니다. |
| \<메타 이름="Microsoft.Help.TopicLocale" 콘텐츠="[언어 코드]" /> | 다른 로캘도 사용되는 경우 이 항목에 대한 로캘을 설정합니다. 이 태그가 토픽에서 사용되는 경우 한 번만 사용해야 합니다. 카탈로그에 두 개 이상의 언어로 된 콘텐츠가 포함된 경우 이 태그를 사용합니다. 카탈로그의 여러 토픽에는 동일한 ID가 있을 수 있지만 각 토픽로컬은 고유한 TopicLocale를 지정해야 합니다. 카탈로그의 로캘과 일치하는 TopicLocale를 지정하는 항목은 목치표에 표시되는 토픽입니다. 그러나 토픽의 모든 언어 버전은 검색 결과에 표시됩니다. |
| \<제목>[제목]\</제목> | 이 항목의 제목을 지정합니다. 이 태그는 필수이며 토픽에서 한 번만 사용해야 합니다. 토픽의 본문에 제목 \<div> 섹션이 포함되어 있지 않으면 이 제목은 토픽과 목차의 테이블에 표시됩니다. |
| \<메타 이름=" Microsoft.Help.키워드" 콘텐츠="[aKeywordPhrase]"/> | 도움말 뷰어의 인덱스 창에 표시되는 링크의 텍스트를 지정합니다. 링크를 클릭하면 토픽이 표시됩니다. 토픽에 대해 여러 인덱스 키워드를 지정하거나 이 주제에 대한 링크가 인덱스에 표시되지 않도록 하려면 이 태그를 생략할 수 있습니다. 이전 버전의 도움말의 "K" 키워드는 이 속성으로 변환할 수 있습니다. |
| \<메타 이름="Microsoft.Help.Id" 콘텐츠="[TopicID]"/> | 이 항목의 식별자를 설정합니다. 이 태그는 필수이며 토픽에서 한 번만 사용해야 합니다. ID는 동일한 로캘 설정이 있는 카탈로그의 토픽 간에 고유해야 합니다. 다른 항목에서는 이 ID를 사용하여 이 항목에 대한 링크를 만들 수 있습니다. |
| \<메타 이름="Microsoft.Help.F1" 콘텐츠="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | 이 항목에 대한 F1 키워드를 지정합니다. 토픽에 대해 여러 F1 키워드를 지정하거나 응용 프로그램 사용자가 F1을 누를 때 이 주제를 표시하지 않으려면 이 태그를 생략할 수 있습니다. 일반적으로 하나의 F1 키워드만 토픽에 지정됩니다. 이전 버전의 도움말의 "F" 키워드를 이 속성으로 변환할 수 있습니다. |
| \<메타 이름="설명" 콘텐츠="[주제 설명]" /> | 이 항목의 내용에 대한 간략한 요약을 제공합니다. 이 태그가 토픽에서 사용되는 경우 한 번만 사용해야 합니다. 이 속성은 쿼리 라이브러리에서 직접 액세스합니다. 인덱스 파일에 저장되지 않습니다. |
| 메타 이름="Microsoft.Help.TocParent" 콘텐츠="[parent_Id]"/> | 목식표에서 이 항목의 상위 항목을 지정합니다. 이 태그는 필수이며 토픽에서 한 번만 사용해야 합니다. 값은 부모의 Microsoft.Help.Id. 토픽은 목저 테이블에 하나의 위치만 가질 수 있습니다. "-1"은 TOC 루트의 토픽 ID로 간주됩니다. 에서 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]해당 페이지는 도움말 뷰어 홈 페이지입니다. 이것은 우리가 특히 상위 수준에 표시 되도록 일부 항목에 TocParent=-1을 추가 하는 동일한 이유입니다. 도움말 뷰어 홈 페이지는 시스템 페이지이므로 대체할 수 없습니다. VSP가 ID가 있는 페이지를 추가하려고 하면 콘텐츠 세트에 추가될 수 있지만 도움말 뷰어는 항상 시스템 페이지를 사용합니다. |
| \<메타 이름="Microsoft.Help.TocOrder" 콘텐츠="[양수 정수]"/> | 목조에서 이 항목이 피어 토픽을 기준으로 표시되는 위치를 지정합니다. 이 태그는 필수이며 토픽에서 한 번만 사용해야 합니다. 이 값은 정수입니다. 낮은 값의 정수를 지정하는 토픽은 더 높은 값의 정수를 지정하는 항목 위에 나타납니다. |
| \<메타 이름="Microsoft.Help.Product" 콘텐츠="[제품 코드]"/> | 이 항목에서 설명하는 제품을 지정합니다. 이 태그가 토픽에서 사용되는 경우 한 번만 사용해야 합니다. 이 정보는 도움말 인덱서에 전달되는 매개 변수로 제공될 수도 있습니다. |
| \<메타 이름="Microsoft.Help.ProductVersion" 콘텐츠="[버전 번호]"/> | 이 항목에서 설명하는 제품의 버전을 지정합니다. 이 태그가 토픽에서 사용되는 경우 한 번만 사용해야 합니다. 이 정보는 도움말 인덱서에 전달되는 매개 변수로 제공될 수도 있습니다. |
| \<메타 이름="Microsoft.Help.Category" 콘텐츠="[문자열]"/> | 콘텐츠의 하위 섹션을 식별 하기 위해 제품에 의해 사용 됩니다. 토픽에 대해 여러 하위 섹션을 식별하거나 링크가 하위 섹션을 식별하지 않으려면 이 태그를 생략할 수 있습니다. 이 태그는 토픽이 이전 버전의 도움말에서 변환될 때 TargetOS 및 TargetFrameworkMoniker의 특성을 저장하는 데 사용됩니다. 콘텐츠의 형식은 속성 이름:특성값입니다. |
| \<메타 이름="Microsoft.Help.TopicVersion 콘텐츠="[토픽 버전 번호]"/> | 카탈로그에 여러 버전이 있는 경우 이 버전의 항목을 지정합니다. Microsoft.Help.Id 고유하다고 보장할 수는 없으므로 카탈로그에 .NET Framework 3.5에 대한 토픽과 .NET Framework 4에 대한 항목이 모두 동일한 Microsoft.Help.Id 있는 경우와 같은 버전의 토픽이 카탈로그에 있는 경우 이 태그가 필요합니다. |
| \<메타 이름="자체 브랜드" 콘텐츠="[TRUE 또는 FALSE]"/> | 이 항목에서 도움말 라이브러리 관리자 시작 브랜딩 패키지를 사용하는지 또는 주제와 관련된 브랜딩 패키지를 사용하는지 여부를 지정합니다. 이 태그는 TRUE 또는 FALSE여야 합니다. TRUE인 경우 관련 토픽의 브랜딩 패키지는 도움말 라이브러리 관리자가 시작될 때 설정된 브랜딩 패키지를 재정의하여 다른 콘텐츠의 렌더링과 다른 경우에도 주제가 의도한 대로 렌더링되도록 합니다. FALSE인 경우 도움말 라이브러리 관리자가 시작될 때 설정된 브랜딩 패키지에 따라 현재 항목이 렌더링됩니다. 기본적으로 도움말 라이브러리 관리자는 SelfBranded 변수가 TRUE로 선언되지 않는 한 자체 브랜딩을 false로 가정합니다. 따라서 메타 이름="SelfBranded" 콘텐츠="FALSE"/> 선언할 \<필요가 없습니다. |

## <a name="create-a-branding-package"></a>브랜딩 패키지 만들기

Visual Studio 릴리스에는 Visual Studio 파트너를 위한 격리 및 통합 셸을 비롯한 다양한 Visual Studio 제품이 포함됩니다.  이러한 각 제품에는 제품에 고유한 주제 기반 도움말 콘텐츠 브랜딩 지원이 필요합니다.  예를 들어 Visual Studio 항목에는 일관된 브랜드 프레젠테이션이 있어야 하지만 ISO 셸을 래핑하는 SQL Studio에는 각 주제에 대한 고유한 도움말 콘텐츠 브랜딩이 필요합니다.  통합 된 쉘 파트너는 자신의 주제 브랜딩을 유지하면서 부모 Visual Studio 제품 도움말 콘텐츠 내에 도움말 주제를 원할 수 있습니다.

브랜딩 패키지는 도움말 뷰어가 포함된 제품에 의해 설치됩니다.  비주얼 스튜디오 제품의 경우:

- 대체 브랜딩 패키지(Branding_\<로캘>.mshc)는 도움말 뷰어 2.3 앱 루트(예: C:\프로그램 파일(x86)\Microsoft 도움말 뷰어 뷰어\v2.3)에 도움말 뷰어 언어 팩에 설치됩니다.  제품 브랜딩 패키지가 설치되지 않았거나(콘텐츠가 설치되지 않음) 설치된 브랜딩 패키지가 손상된 경우에 사용됩니다.  앱 루트 대체 브랜딩 패키지를 사용할 때 Visual Studio 요소(로고 및 피드백)는 무시됩니다.

- 콘텐츠 패키지 서비스에서 Visual Studio 콘텐츠를 설치하면 브랜딩 패키지도 설치됩니다(처음으로 콘텐츠 설치 시나리오).  브랜딩 패키지에 대한 업데이트가 있는 경우 다음 콘텐츠 업데이트 또는 추가 패키지 설치 작업이 수행될 때 업데이트가 설치됩니다.

Microsoft 도움말 뷰어는 주제 메타데이터를 기반으로 하는 주제의 브랜딩을 지원합니다.

- 토픽 메타데이터가 자체 브랜드 = true를 정의하는 경우 토픽을 있는 것처럼 렌더링하고 브랜딩에 관해서는 아무 것도 하지 않습니다.

- 토픽 메타데이터가 자체 브랜드 = false를 정의하는 경우 TopicVendor 메타데이터 값과 연결된 브랜딩 패키지를 사용합니다.

- 토픽 메타데이터가 이름="Microsoft.Help.TopicVendor"\< 콘텐츠= 공급업체 MSHA> 브랜딩 패키지 이름을 정의하는 경우 콘텐츠 값에 정의된 브랜딩 패키지를 사용합니다.

- Visual Studio 카탈로그에는 브랜딩 패키지의 우선 순위 응용 프로그램이 있습니다.  첫 번째 Visual Studio 기본 브랜딩이 적용된 다음 토픽 메타데이터에 정의되고 관련 브랜딩 패키지(설치 msha에 정의된 대로)로 지원되는 경우 공급업체 정의 브랜딩이 재정의로 적용됩니다.

브랜딩 요소는 일반적으로 세 가지 주요 범주로 나뉩니다.

- 헤더 요소(예: 피드백 링크, 조건부 고지 사항 텍스트, 로고 포함)

- 콘텐츠 동작(예: 확장/축소 컨트롤 텍스트 요소 및 코드 조각 요소 포함)

- 바닥글 요소(예: 저작권)

브랜드 요소로 간주되는 항목은 다음과 같습니다(이 사양에 자세히 설명되어 있음).

- 카탈로그/제품 로고(예: 비주얼 스튜디오)

- 피드백 링크 및 전자 메일 요소

- 고지 사항 텍스트

- 저작권 텍스트

Visual Studio 도움말 뷰어 브랜딩 패키지의 지원 파일은 다음과 같습니다.

- 그래픽(로고, 아이콘 등)

- 브랜딩.js - 콘텐츠 동작을 지원하는 스크립트 파일

- Branding.xml - 카탈로그 콘텐츠 간에 일관되게 사용되는 문자열입니다.  참고: branding.xml의 Visual Studio 지역화 텍스트 요소에는\<_locID=" 고유 값> 포함

- 브랜딩.css - 프레젠테이션 일관성을 위한 스타일 정의

- 인쇄.css - 일관된 인쇄 프레젠테이션을 위한 스타일 정의

위에서 언급했듯이 브랜딩 패키지는 다음 주제와 관련이 있습니다.

- SelfBranded = false가 메타데이터에 정의된 경우 토픽은 카탈로그 브랜딩 패키지를 상속합니다.

- 또는 SelfBranded = false이고 MSHA에 정의된 고유한 브랜딩 패키지가 있고 콘텐츠가 설치될 때 사용할 수 있는 경우

사용자 지정 브랜딩 패키지(VSP 콘텐츠, SelfBranded=True)를 구현하는 VSP의 경우 한 가지 방법은 대체 브랜딩 패키지(도움말 뷰어와 함께 설치됨)로 시작하여 파일 이름을 적절하게 변경하는 것입니다.  Branding_\<로캘>.mshc 파일은 파일 확장번호가 .mshc로 변경된 zip 파일이므로 .mshc에서 .zip으로 확장을 변경하고 내용을 추출하기만 하면 됩니다.  패키지 요소를 브랜딩하고 적절하게 수정하려면 아래를 참조하십시오(예: VSP 로고로 로고 변경 및 Branding.xml 파일의 로고 참조, VSP 세부 사항당 Branding.xml 업데이트 등).

모든 수정이 완료되면 원하는 브랜딩 요소가 포함된 zip 파일을 만들고 확장을 .mshc로 변경합니다.

사용자 지정 브랜딩 패키지를 연결하려면 콘텐츠 mshc(항목 포함)와 함께 브랜딩 mshc 파일에 대한 참조가 포함된 MSHA를 만듭니다.  기본 MSHA를 만드는 방법은 아래 "MSHA"를 참조하십시오.

Branding.xml 파일에는 주제에 메타 이름="Microsoft.Help.SelfBranded" 콘텐츠="false"/> 포함되어 \<있는 경우 주제의 특정 항목을 일관되게 렌더링하는 데 사용되는 요소 목록이 포함되어 있습니다.  Branding.xml 파일의 비주얼 스튜디오 요소 목록은 다음과 같습니다.  이 목록은 ISO Shell 채택자를 위한 템플릿으로 사용되며, 여기서 이러한 요소(예: 로고, 피드백 및 저작권)를 수정하여 자체 제품 브랜딩 요구 사항을 충족합니다.

참고: "{n}"으로 표시된 변수에는 코드 종속성이 있으므로 이러한 값을 제거하거나 변경하면 오류가 발생하고 응용 프로그램 충돌이 발생할 수 있습니다. 지역화 식별자(예: _locID="codesnippet.n")는 Visual Studio 브랜딩 패키지에 포함됩니다.

**브랜딩.xml**

| | |
| - | - |
| 기능: | **접이식 영역** |
| 사용: | 콘텐츠 컨트롤 텍스트 축소 확장 |
| **요소** | **값** |
| 확장 텍스트 | Expand |
| 텍스트 축소 | 축소 |
| 기능: | **코드스니펫** |
| 사용: | 코드 코드 조각 제어 텍스트입니다.  참고: "비속형" 공간이 있는 코드 스니펫 콘텐츠가 공백으로 변경됩니다. |
| **요소** | **값** |
| 카피토클립보드 | 클립보드로 복사 |
| 뷰컬러텍스트 | 색상보기 |
| 결합VBTab디스플레이언어 | 비주얼 베이직(샘플) |
| VB 선언 | 선언 |
| VBUse | 사용 |
| 기능: | **피드백, 바닥글 및 로고** |
| 사용: | 고객이 전자 메일을 통해 현재 항목에 대한 피드백을 제공할 수 있도록 피드백 컨트롤을 제공합니다.  콘텐츠에 대한 저작권 텍스트입니다.  로고 정의. |
| **요소** | **값(이러한 문자열은 콘텐츠 채택자의 필요를 충족하도록 수정할 수 있습니다.)** |
| 저작권 | © 2013 Microsoft Corporation. All rights reserved. |
| 송신 피드백 | \<href="{0}">{1} 이\<주제에 대한 피드백/> Microsoft에 보냅니다. |
| 피드백 링크 | |
| 로고제목 | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| 로고파일네임 | vs_logo_bk.gif |
| 로고파일네임HC | vs_logo_wh.gif |
| 기능: | **고지 사항** |
| 사용: | 컴퓨터 번역 콘텐츠에 대한 사례별 고지 사항 집합입니다. |
| **요소** | **값** |
| MT_Editable | 이 문서는 기계 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| MT_NonEditable | 이 문서는 기계 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| MT_QualityEditable | 이 문서는 수동으로 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| MT_QualityNonEditable | 이 문서는 수동으로 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| MT_BetaContents | 이 문서는 예비 릴리스를 위해 기계로 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| MT_BetaRecycledContents | 이 문서는 예비 릴리스를 위해 수동으로 번역되었습니다. 인터넷에 연결되어 있는 경우 "이 주제를 온라인으로 보기"를 선택하여 원본 영어 콘텐츠와 함께 편집 가능한 모드에서 이 페이지를 동시에 봅니다. |
| 기능: | **링크 테이블** |
| 사용: | 온라인 주제 링크 지원 |
| **요소** | **값** |
| 링크 테이블 제목 | 링크 테이블 |
| 토픽에누링크텍스트 | 컴퓨터에서 사용할\<수 있는 이 항목의 영어 버전 /a> 봅니다. |
| 토픽온라인링크텍스트 | 이 항목 \<보기 href="{0}">{1} 온라인/>\< |
| 온라인 텍스트 | 온라인 |
| 기능: | **비디오 오디오 제어** |
| 사용: | 비디오 콘텐츠에 대한 요소 및 텍스트 표시 |
| **요소** | **값** |
| 멀티미디어 지원되지 않음 | 콘텐츠를 지원하려면 {0} 인터넷 익스플로러 9 이상을 설치해야 합니다. |
| 비디오 텍스트 | 비디오 표시 |
| 오디오 텍스트 | 오디오 스트리밍 |
| 온라인비디오링크텍스트 | \<p>이 주제와 연관된 {0} \<비디오를 보려면{1}href=" ">{2}여기\</> 클릭합니다. \</p> |
| 온라인오디오링크텍스트 | \<p>이 항목과 연관된 오디오를 들으려면 {0} \<href="{1}">{2}여기\</> 클릭합니다. \</p> |
| 기능: | **콘텐츠가 설치되지 않음 제어** |
| 사용: | 콘텐츠 렌더링에 사용되는 텍스트 요소(문자열)는 설치되지 않았습니다. |
| **요소** | **값** |
| 콘텐츠Not설치제목 | 컴퓨터에서 콘텐츠를 찾을 수 없습니다. |
| 콘텐츠Not설치다운로드콘텐츠텍스트 | \<p>컴퓨터에 \<콘텐츠를 다운로드하려면 href=" {1} \<{0}">> 관리 탭을 클릭합니다. \</p> |
| 콘텐츠Not설치텍스트 | \<p>컴퓨터에 콘텐츠가 설치되어 있지 않습니다. 로컬 도움말 콘텐츠 설치는 관리자에게 문의하십시오. \</p> |
| 기능: | **찾을 수 없는 주제 컨트롤** |
| 사용: | topicnotfound.htm의 렌더링에 사용되는 텍스트 요소(문자열) |
| **요소** | **값** |
| 주제NotFound 타이틀 | 컴퓨터에서 요청된 주제를 찾을 수 없습니다. |
| 주제NotFoundView온라인텍스트 | \<p>요청한 주제는 컴퓨터에서 찾을 수 없지만 \<{0}href=" ">{1} 온라인/a\<> 주제를 볼 수 있습니다. \</p> |
| 주제NotFound다운로드콘텐츠텍스트 | \<p>유사한 주제에 대한 링크에 대한 \<탐색 창{0} {1} 참조 또는 href=" ">> 관리 탭\</a를 클릭하여 컴퓨터에 콘텐츠를 다운로드합니다. \</p> |
| 주제NotFound텍스트 | \<p>요청한 항목이 컴퓨터에서 찾을 수 없습니다. \</p> |
| 기능: | **토픽 손상된 제어** |
| 사용: | 토픽트손상.htm 렌더링에 사용되는 텍스트 요소(문자열) |
| **요소** | **값** |
| 토픽손상된제목 | 요청된 항목을 표시할 수 없습니다. |
| 토픽손상된뷰온라인텍스트 | \<p>도움말 뷰어가 요청된 주제를 표시할 수 없습니다. 토픽의 콘텐츠에 오류가 있거나 기본 시스템 종속성이 있을 수 있습니다. \</p> |
| 기능: | **홈 페이지 컨트롤** |
| 사용: | 도움말 뷰어 최상위 노드 콘텐츠의 표시를 지원하는 텍스트입니다. |
| **요소** | **값** |
| HomePageTitle | 뷰어 홈 도움말 |
| 홈페이지 소개 | \<p>Microsoft 도구, 제품, 기술 및 서비스를 사용하는 모든 사람에게 필수적인 정보 소스인 Microsoft 도움말 뷰어에 오신 것을 환영합니다. 도움말 뷰어를 사용하면 방법 및 참조 정보, 샘플 코드, 기술 문서 등에 액세스할 수 있습니다. 필요한 콘텐츠를 찾으려면 목차를 찾아보거나 전체 텍스트 검색을 사용하거나 키워드 인덱스를 사용하여 콘텐츠를 탐색합니다. \</p> |
| 홈페이지콘텐츠설치텍스트 | \<p \<>br />\<href=" {1} \<{0}>"콘텐츠 관리/> 탭을\<사용하여 \<다음을 수행하십시오: ul>li>컴퓨터에 콘텐츠 추가. \</li \<>li>로컬 콘텐츠에 대한 업데이트를 확인합니다. \</li \<>li>컴퓨터에서 콘텐츠를 제거합니다. \</li \<>/ul \<>/p> |
| 홈페이지설치책 | 설치된 책 |
| 홈페이지노북설치 | 컴퓨터에서 콘텐츠를 찾을 수 없습니다. |
| 홈페이지도움말설정 | 도움말 콘텐츠 설정 |
| 홈페이지도움말설정텍스트 | \<p>현재 설정은 로컬 도움말입니다. 도움말 뷰어에는 컴퓨터에 설치한 콘텐츠가 표시됩니다. \<br />도움말 콘텐츠의 소스를 변경하려면 Visual Studio \<메뉴 모음에서{0}범위 스타일="\<">도움말, 도움말 기본 설정 /범위> 설정합니다. \<br />\</p> |
| 메가바이트 | MB |

**브랜딩.js**

브랜딩.js 파일에는 비주얼 스튜디오 도움말 뷰어 브랜딩 요소에서 사용하는 자바스크립트가 포함되어 있습니다.  다음은 브랜딩 요소 및 지원 JavaScript 기능의 목록입니다.  이 파일에 대해 지역화할 모든 문자열은 이 파일 의 맨 위에 있는 "지역화 가능한 문자열" 섹션에 정의되어 있습니다.  브랜딩.js 파일 내의 loc 문자열에 대해 ICL 파일이 만들어졌습니다.

||||
|-|-|-|
|**브랜딩 기능**|**자바 스크립트 기능**|**설명**|
|Var...||변수 정의|
|사용자 코드 언어 받기|세트사용자 환경 설정랑|인덱스 #을 코드 언어에 매핑합니다.|
|쿠키 값 설정 및 받기|getCookie, 세트쿠키||
|상속된 멤버|변경 멤버 레이블|상속된 멤버 확장/축소|
|셀프 브랜디드=False|Onload|쿼리 문자열을 읽고 인쇄 요청인지 확인합니다.  사용자가 선호하는 탭에 초점을 맞추도록 모든 코드니펫을 설정합니다.  인쇄 요청인 경우 설정은 프린터친화적입니다. 고대비 모드를 선택합니다.|
|코드 스니펫|추가특정텍스트언어태그세트||
||getIndexFromDevLang||
||변경 탭||
||세트코드니펫랭||
||세트전류랭||
||카피토클립보드||
|접이식 영역|추가토접블컨트롤세트|모든 축소 가능한 제어 개체를 목록에 씁니다.|
||CA_Click|축소 가능한 영역의 상태에 따라, 어떤 이미지와 텍스트를 제시할지 정의합니다.|
|로고에 대한 대비 지원|isBlackBackground()|배경이 검은색인지 확인하기 위해 호출됩니다.  고대비 모드에서만 정확합니다.|
||isHighContrast()|컬러 스팬을 사용하여 고대비 모드 감지|
||on하이콘트라스트(블랙)|고대비가 감지될 때 호출|
|LST 기능|||
||addToLanSpecTextIdSet(ID)||
||업데이트LST (현재랭)||
||getDevLangFromCode스니펫 (랭)||
|멀티미디어 기능|캡션(시작, 끝, 텍스트, 스타일)||
||findAllMediaControls(정규화된 Id)||
||getActivePlayer(정규화된 Id)||
||캡션온오프(ID)||
||toSeconds(t)||
||getAllComments(노드)||
||스타일수정(스타일이름, 스타일값)||
||쇼CC(ID)||
||자막(id)||

**HTM 파일**

브랜딩 패키지에는 도움말 콘텐츠 사용자에게 주요 정보를 전달하기 위한 시나리오를 지원하는 HTM 파일 집합(예: 설치된 콘텐츠 집합을 설명하는 섹션이 포함된 홈페이지 및 토픽의 로컬 집합에서 항목을 찾을 수 없는 시기를 사용자에게 알리는 페이지)이 포함되어 있습니다. 이러한 HTM 파일은 제품별 수정할 수 있습니다.  ISO Shell 공급업체는 기본 브랜딩 패키지를 사용하여 이러한 페이지의 동작과 내용을 필요에 따라 변경할 수 있습니다.  이러한 파일은 브랜딩 태그가 branding.xml 파일에서 해당 콘텐츠를 얻으려면 해당 브랜딩 패키지를 참조합니다.

||||
|-|-|-|
|**파일**|**사용**|**표시된 콘텐츠 소스**|
|홈페이지.htm|이 페이지는 현재 설치된 콘텐츠와 해당 콘텐츠에 대해 사용자에게 표시하기에 적합한 다른 메시지를 표시하는 페이지입니다.  이 파일에는 로컬 콘텐츠 TOC의 맨 위에 이 콘텐츠를 배치하는 추가 메타 데이터 속성 "Microsoft.Help.Id" content="-1"이 있습니다.||
||<META_HOME_PAGE_TITLE_ADD />|브랜딩.xml, 태그 \<홈페이지타이틀>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|브랜딩.xml, 태그 \<홈페이지소개>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|브랜딩.xml, 태그 \<홈페이지콘텐츠설치텍스트>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|제목 섹션 Branding.xml 태그\<HomePage설치>, 응용 \<프로그램에서 생성 된 데이터, HomePageNoBooks책이 설치되지 않은 경우> 설치.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|제목 섹션 Branding.xml 태그 \<홈페이지도움말설정 \<>, 섹션 텍스트 홈페이지도움말설정텍스트>.|
|토픽타티드.htm|토픽이 로컬 집합에 있지만 어떤 이유로 표시할 수 없는 경우(손상된 콘텐츠).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|브랜딩.xml, 태그 \<토픽손상된>|
||<TOPIC_CORRUPTED_SECTION_ADD />|브랜딩.xml, 태그 \<토픽손상된뷰온라인텍스트>|
|토픽노드.htm|로컬 콘텐츠 세트에서 주제를 찾을 수 없거나 온라인에서 사용할 수 없는 경우||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|브랜딩.xml, 태그 \<주제NotFound타이틀>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|브랜딩.xml, 태그 \<주제NotFoundView온라인텍스트 \<> + 주제NotFound다운로드콘텐츠텍스트>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|브랜딩.xml, 태그 \<토픽NotFoundText>|
|contentnotinstalled.htm|제품에 대한 로컬 콘텐츠가 설치되어 있지 않은 경우.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|브랜딩.xml, 태그 \<콘텐츠Not설치제목>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|브랜딩.xml, 태그 \<콘텐츠NotInstalled다운로드콘텐츠텍스트>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|브랜딩.xml, 태그 \<콘텐츠Notinstalled텍스트>|

**CSS 파일**

Visual Studio 도움말 뷰어 브랜딩 패키지에는 일관된 Visual Studio 도움말 콘텐츠 프레젠테이션을 지원하는 두 개의 CSS 파일이 포함되어 있습니다.

- Branding.css - 셀프 Branded=false 렌더링을 위한 CSS 요소가 포함되어 있습니다.

- Printer.css - 셀프 Branded=false 렌더링을 위한 css 요소가 포함되어 있습니다.

Branding.css 파일에는 Visual Studio 주제 프레젠테이션에 대한 정의가 포함되어 있습니다(패키지\<서비스의 Branding_ 로캘>.mshc에 포함된 브랜딩.css가 변경될 수 있습니다).

**그래픽 파일**

Visual Studio 콘텐츠에는 Visual Studio 로고와 기타 그래픽이 표시됩니다.  Visual Studio 도움말 뷰어 브랜딩 패키지의 전체 그래픽 파일 목록은 다음과 같습니다.

||||
|-|-|-|
|**파일**|**사용**|**예**|
|clear.gif|접이식 영역을 렌더링하는 데 사용됩니다.||
|footer_slice.gif|바닥글 프리젠 테이션||
|info_icon.gif|정보 표시 시 사용|고지 사항|
|online_icon.gif|이 아이콘은 온라인 링크와 연결됩니다.||
|탭왼쪽BD.gif|코드 코드 조각 컨테이너를 렌더링하는 데 사용됩니다.||
|탭라이트BD.gif|코드 코드 조각 컨테이너를 렌더링하는 데 사용됩니다.||
|vs_logo_bk.gif|Branding.xml 태그 \<LogoFileName> 정의된 일반 대비 로고 참조에 사용됩니다.  Visual Studio 제품의 경우 로고 이름은 vs_logo_bk.gif입니다.||
|vs_logo_wh.gif|Branding.xml 태그 \<LogoFileNameHC> 정의된 일반 높은 로고 참조에 사용됩니다.  Visual Studio 제품의 경우 로고 이름은 vs_logo_wh.gif입니다.||
|ccOff.png|그래픽 캡션||
|ccOn.png|그래픽 캡션||
|이미지스프라이트.png|접이식 영역을 렌더링하는 데 사용됩니다.|그래픽 확장 또는 축소|

## <a name="deploy-a-set-of-topics"></a>항목 집합 배포

이 방법은 MSHA 파일과 주제가 포함된 택시 또는 MSHC 집합으로 구성된 도움말 뷰어 콘텐츠 배포 집합을 만들기 위한 간단하고 빠른 자습서입니다. MSHA는 택시 또는 MSHC 파일 집합을 설명하는 XML 파일입니다. 도움말 뷰어는 MSHA를 읽고 콘텐츠 목록을 가져올 수 있습니다(. CAB 또는 . MSHC 파일)을 로컬 설치에 사용할 수 있습니다.

이것은 도움말 뷰어 MSHA에 대한 매우 기본적인 XML 스키마를 설명하는 프라이머일 뿐입니다.  이 간략한 개요 및 샘플 도움말ContentSetup.msha 아래에는 예제 구현이 있습니다.

이 프라이머의 목적에 대한 MSHA의 이름은 HelpContentSetup.msha입니다 (파일의 이름은 확장과 함께 무엇이든 될 수 있습니다. MSHA)를 참조하십시오. HelpContentSetup.msha(아래 예)에는 사용 가능한 택시 또는 McSHC 목록이 포함되어야 합니다.  파일 형식은 MSHA 내에서 일관되어야 합니다(MSHA 및 CAB 파일 형식의 조합을 지원하지 않음). 각 CAB 또는 MSHC에 \<대해 div 클래스 ="패키지"> 있어야 합니다. \</div>(아래 예제 참조).

참고: 아래 구현 예제에서는 브랜딩 패키지를 포함했습니다. 필요한 Visual Studio 콘텐츠 렌더링 요소 및 콘텐츠 동작을 얻으려면 포함해야 합니다.

샘플 도움말콘텐츠Setup.msha 파일: ("콘텐츠 집합 이름 1" 및 "콘텐츠 집합 이름 2" 등 파일 이름으로 바꿉니다.)

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

1. 로컬 폴더 만들기(예: "C:\SampleContent")

2. 이 예제에서는 MSHC 파일을 사용하여 항목을 포함합니다.  MSHC는 파일 확장번호가 .zip에서 .zip으로 변경된 zip입니다. MSHC.

3. 아래 HelpContentSetup.msha를 텍스트 파일(메모장이 파일을 만드는 데 사용)으로 만들고 위의 표시된 폴더에 저장합니다(1단계 참조).

"브랜딩" 클래스는 존재하며 고유합니다. 브랜딩 mshc는 설치된 콘텐츠에 브랜딩이 있고 MSHCs에 포함된 콘텐츠 동작에는 브랜딩 패키지에 포함된 적절한 지원 요소가 갖도록 이 프라이머에 포함되어 있습니다. 이렇게 하지 않으면 시스템에서 찢어진(설치된) 콘텐츠의 일부가 아닌 지원 항목을 찾을 때 오류가 발생합니다.

Visual Studio 브랜딩 패키지를 얻으려면 C:\프로그램 파일(x86)\Microsoft 도움말 뷰어\v2.3\에서 Branding_en-US.mshc 파일을 작업 폴더에 복사합니다.

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

위의 단계를 사용하고 확장하면 VSP가 Visual Studio 도움말 뷰어에 콘텐츠 집합을 배포할 수 있습니다.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>비주얼 스튜디오 셸에 도움말 추가(통합 및 격리)

**소개**

이 연습에서는 도움말 콘텐츠를 Visual Studio Shell 응용 프로그램에 통합한 다음 배포하는 방법을 보여 줍니다.

**요구 사항**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [비주얼 스튜디오 2013 고립 쉘 리디스트](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**개요**

[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 셸은 응용 프로그램을 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 기반으로 할 수 있는 IDE 버전입니다. 이러한 응용 프로그램에는 만든 확장과 함께 격리된 셸이 포함됩니다. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK에 포함된 격리된 셸 프로젝트 템플릿을 사용하여 확장을 빌드합니다.

격리된 셸 기반 응용 프로그램 및 해당 도움말을 만들기 위한 기본 단계:

1. 재배포 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 할 수 있는 ISO 셸(Microsoft 다운로드)을 가져옵니다.

2. Visual Studio에서 격리셸을 기반으로 하는 도움말 확장을 만듭니다(예: 이 연습의 왼쪽 에 설명된 Contoso 도움말 확장)

3. 재배포 가능한 확장 및 ISO 셸을 배포 MSI(응용 프로그램 설정)로 래핑합니다. 이 연습에는 설정 단계가 포함되지 않습니다.

Visual Studio 콘텐츠 저장소를 만듭니다. 통합 셸 시나리오의 경우 다음과 같이 Visual Studio12를 제품 카탈로그 이름으로 변경합니다.

- 폴더 C:\프로그램데이터\Microsoft\도움말라이브러리2\카탈로그\VisualStudio15를 만듭니다.

- CatalogType.xml이라는 파일을 만들고 폴더에 추가합니다. 파일에는 다음과 같은 코드 줄이 포함되어야 합니다.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

레지스트리의 콘텐츠 저장소를 정의합니다. 통합 셸의 경우 VisualStudio15를 제품 카탈로그 이름으로 변경합니다.

- HKLM\소프트웨어\Wow6432Node\마이크로소프트\도움말\v2.3\카탈로그\VisualStudio15

   키: 위치 경로 문자열 값: C:\프로그램데이터\마이크로소프트\도움말 라이브러리2\카탈로그\VisualStudio15\

- HKLM\소프트웨어\Wow6432Node\마이크로소프트\도움말\v2.3\카탈로그\VisualStudio15\en-US

   키: 카탈로그 이름 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 문자열 값: 설명서

**프로젝트 만들기**

격리된 셸 확장을 만들려면 다음을 수행합니다.

1. Visual Studio에서 **파일**에서 **새 프로젝트를**선택하고 다른 프로젝트 **유형에서** **확장성을**선택한 다음 **Visual Studio 셸 격리를**선택합니다. 프로젝트 `ContosoHelpShell`이름을 지정하여 Visual Studio 격리셸 템플릿을 기반으로 확장성 프로젝트를 만듭니다.

2. 솔루션 탐색기에서 ContosoHelpShellUI 프로젝트에서 리소스 파일 폴더에서 ApplicationCommands.vsct를 엽니다. 이 줄이 주석이 주석으로 달아나는지 확인합니다("No_Help"을 검색합니다).`<!-- <define name="No_HelpMenuCommands"/> -->`

3. F5 키를 선택하여 **디버그를**컴파일하고 실행합니다. 격리된 셸 IDE의 실험 인스턴스에서 **도움말** 메뉴를 선택합니다. **도움말 보기,** 도움말 **콘텐츠 추가 및 제거**및 도움말 기본 **설정** 설정 명령이 표시되는지 확인합니다.

4. 솔루션 탐색기에서 ContosHelpShell 프로젝트에서 셸 사용자 지정 폴더에서 ContosoHelpShell.pkgdef를 엽니다. Contoso 도움말 카탈로그를 정의하려면 다음 줄을 추가합니다.

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. 솔루션 탐색기에서 ContosHelpShell 프로젝트에서 셸 사용자 지정 폴더에서 ContosoHelpShell.Application.pkgdef를 엽니다. F1 도움말을 사용하려면 다음 줄을 추가합니다.

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

6. 솔루션 탐색기에서 ContosoHelpShell 솔루션의 컨텍스트 메뉴에서 **속성** 메뉴 항목을 선택합니다. **구성 속성에서** **구성 관리자를**선택합니다. **구성** 열에서 모든 "디버그" 값을 "릴리스"로 변경합니다.

7. 솔루션을 빌드합니다. 이렇게 하면 다음 섹션에서 사용할 릴리스 폴더에 파일 집합이 만들어집니다.

배포된 것처럼 테스트하려면 다음을 수행하십시오.

1. Contoso를 배포하는 컴퓨터에서 다운로드한 ISO 셸을 설치합니다.

2. \Program 파일(x86)에서 \\\\폴더를 만들고 `Contoso`이름을 지정합니다.

3. ContosoHelpShell 릴리스 폴더의 내용을 \\\프로그램 파일(x86)\Contoso\ 폴더로 복사합니다.

4. 시작 **메뉴에서** `Regedit` **실행을** 선택하고 를 입력하여 레지스트리 편집기 시작. 레지스트리 편집기에서 **파일**을 선택한 다음 **을 가져옵니다.** ContosoHelpShell 프로젝트 폴더를 찾아봅습니다. ContosoHelpShell 하위 폴더에서 ContosoHelpShell.reg를 선택합니다.

5. 콘텐츠 저장소 만들기:

    ISO 셸의 경우 - Contoso 콘텐츠 저장소 C:\ProgramData\Microsoft\HelpLibrary2\카탈로그\ContosoDev12 만들기

    통합 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 쉘의 경우 폴더 C:\ProgramData\Microsoft\HelpLibrary2\카탈로그\VisualStudio15 를 만듭니다.

6. CatalogType.xml을 만들고 다음을 포함하는 콘텐츠 저장소(이전 단계)에 추가합니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. 다음 레지스트리 키를 추가합니다.

    HKLM\SOFTWARE\Wow6432Node\마이크로소프트\도움말\v2.3\카탈로그\VisualStudio15Key: 위치 경로 문자열 값:

    ISO 쉘의 경우:

    C:프로그램데이터마이크로소프트헬프라이브러리2카탈로그비주얼스튜디오15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]통합 쉘:

    C:프로그램데이터데이터마이크로소프트헬프라이브러리2카탈로그비주얼스튜디오15엔-미국

    키: 카탈로그 이름 [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] 문자열 값: 설명서. ISO 셸의 경우 카탈로그 이름입니다.

8. 콘텐츠(택시 또는 MSHC 및 MSHA)를 로컬 폴더에 복사합니다.

9. 콘텐츠 저장소를 테스트하기 위한 통합 셸 명령줄 예제입니다. ISO Shell의 경우 제품과 일치하도록 카탈로그 및 launchingApp 값을 적절히 변경합니다.

     "C:\프로그램 파일 (x86)\마이크로소프트 도움말 뷰어\v2.3\HlpViewer.exe" /카탈로그이름 VisualStudio15 /helpQuery 방법="페이지&id=ContosoTopic0" /발사App 마이크로소프트, VisualStudio,12.0

10. Contoso 응용 프로그램 루트에서 Contoso 응용 프로그램을 시작합니다. ISO 셸에서 **도움말** 메뉴 항목을 선택하고 **도움말 설정 기본 설정을** 변경하여 **로컬 도움말을 사용합니다.**

11. 셸 내에서 **도움말** 메뉴 항목을 선택한 다음 **도움말 을 봅니다.** 로컬 도움말 뷰어가 시작되어야 합니다. 콘텐츠 관리 탭을 **선택합니다.** **설치 소스에서** **디스크** 옵션 단추를 선택합니다. **단추를** 선택하고 Contoso 콘텐츠가 포함된 로컬 폴더를 찾아봅니다(위의 단계에서 로컬 폴더로 복사). 도움말 콘텐츠설치를 선택합니다. Contoso는 이제 책 선택에 책으로 표시됩니다. **추가를**선택한 다음 **업데이트** 단추(오른쪽 하단 모서리)를 선택합니다.

12. Contoso IDE 내에서 F1 키를 선택하여 F1 기능을 테스트합니다.

## <a name="additional-resources"></a>추가 자료

런타임 API의 경우 [Windows 도움말 API를](/previous-versions/windows/desktop/helpapi/helpapi-portal)참조하십시오.

도움말 API를 활용하는 방법에 대한 자세한 내용은 [도움말 뷰어 코드 예제를](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)참조하십시오.

[개발자 커뮤니티에서](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)기능 제안을 제출할 수 있습니다.
