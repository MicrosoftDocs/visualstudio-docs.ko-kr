---
title: JavaScript IntelliSense | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962c724e231275c9fa716d6c823b7451292392cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848380"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense를 사용하면 코드를 작성하는 동안 적절한 정보가 제공되므로 코드를 빠르게 작성하면서 오류도 줄일 수 있습니다. JavaScript 편집기에서 클라이언트 스크립트를 작성할 때 IntelliSense에는 현재 컨텍스트를 기준으로 사용할 수 있는 개체, 함수, 속성 및 매개 변수가 나열되므로 사용자는 IntelliSense에서 제공하는 팝업 목록에서 코딩 옵션을 선택하여 코드를 완성할 수 있습니다.

 IntelliSense를 사용하면 다음과 같은 작업을 더욱 쉽게 완료할 수 있습니다.

- 멤버 정보 찾기

- 코드에 언어 요소 직접 삽입

- 코드 편집기를 벗어나지 않고 컨텍스트 유지

- XML 문서 주석 및 JavaScript IntelliSense 확장성을 사용하여 사용자 지정 IntelliSense를 지원합니다.

  이 항목에는 다음과 같은 섹션이 포함되어 있습니다.

- [IntelliSense 컨텍스트 확인](#DeterminingIntelliSenseContext)

- [IntelliSense 정보 처리](#ProcessingIntelliSenseInformation)

- [JavaScript IntelliSense 기능](#Features)

- [JavaScript IntelliSense의 확장성](#Extensibility)

- [JavaScript 유효성 검사](#Validation)

  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]의 IntelliSense 기능에 대한 자세한 내용은 [IntelliSense 사용](../ide/using-intellisense.md)을 참조하세요.

## <a name="determining-intellisense-context"></a><a name="DeterminingIntelliSenseContext"></a> IntelliSense 컨텍스트 확인
 JavaScript IntelliSense는 현재 스크립트 컨텍스트와 관련된 모든 스크립트를 기준으로 코딩 옵션을 제공합니다. 여기에는 현재 파일의 스크립팅 요소뿐만 아니라 스크립트 파일 참조, 어셈블리 스크립트 참조, 서비스 참조, 페이지 연관 참조 등 스크립트에서 직간접으로 참조되는 모든 코드가 포함됩니다.

 현재 스크립트 컨텍스트는 다음과 같은 항목을 기준으로 결정됩니다.

- 활성 문서의 모든 스크립트 블록에서 정의된 기능입니다. 인라인 스크립트 블록은 파일 확장명이 .aspx., .ascx, .master, .html 및 .htm인 파일에서 지원됩니다.

- 다른 스크립트 파일을 가리키는 `src` 특성이 있는 `script` 요소입니다. 대상 스크립트 파일의 파일 확장명은 .js여야 합니다.

- `reference` 지시문을 사용하여 다른 JavaScript 파일을 참조하는 JavaScript 파일입니다.

- 전역 개체, IntelliSense 확장명 또는 지연 로드된 스크립트 파일의 참조 그룹입니다.

- XML Web services에 대한 참조

- 웹 애플리케이션이 AJAX 사용 ASP.NET 애플리케이션인 경우 <xref:System.Web.UI.ScriptManager> 및 <xref:System.Web.UI.ScriptManagerProxy> 컨트롤입니다.

- AJAX 사용 ASP.NET 웹 애플리케이션에서 작업하는 경우 [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]

    > [!NOTE]
    > HTML 요소의 이벤트 처리기 특성에 있는 스크립트나 `href` 특성에 정의되어 있는 스크립트에서는 IntelliSense가 지원되지 않습니다.

## <a name="processing-intellisense-information"></a><a name="ProcessingIntelliSenseInformation"></a> IntelliSense 정보 처리
 JavaScript IntelliSense를 제공하기 위해 언어 서비스는 다음 작업을 수행합니다.

- 활성 문서의 참조와 참조된 파일의 스크립트 참조에 대한 재귀적 검사를 기반으로 하는 종속 JavaScript 파일의 목록을 만듭니다.

- 목록 전체를 검색하여 각 파일의 형식 정보와 기타 관련 데이터를 수집합니다.

- 데이터를 집계하여 형식 정보와 데이터를 IntelliSense에서 사용할 수 있도록 JavaScript Language Service에 전달합니다.

- IntelliSense 목록에 영향을 미칠 수 있는 변경 내용이 있는지 파일을 모니터링하여 필요한 경우 목록을 업데이트합니다. 원격 저장소(예: HTTP를 사용하여 참조된 저장소)의 스크립트는 모니터링되지 않습니다.

## <a name="javascript-intellisense-features"></a><a name="Features"></a> JavaScript IntelliSense의 기능
 JavaScript IntelliSense는 다음과 같은 개체를 지원합니다.

- [DOM(문서 개체 모델) 요소](#HTMLDom)

- [내장 개체](#IntrinsicObjects)

- [사용자 정의 변수, 함수 및 개체](#UserDefined)

- [스크립트 참조](#Script), [참조 지시문](#ReferenceDirectives) 및 [참조 그룹](#ReferenceGroups) 등의 참조를 사용하여 외부 파일에서 정의된 개체입니다.

- Visual Studio를 통해 다운로드된 원격 파일에서 정의된 개체입니다.

- 매개 변수 및 필드 등 [XML 문서 주석](#XMLDocComments)에서 지정된 개체입니다.

- 표준 JavaScript 주석 태그(//)를 사용하여 설명되는 개체입니다. 자세한 내용은 [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md)을 참조하세요.

- [JavaScript IntelliSense 확장성](#Extensibility) 메커니즘을 사용하여 지원되는 개체입니다. 자세한 내용은 [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md)을 참조하세요.

- [ASP.NET AJAX 개체](#ASPNet)

  IntelliSense가 개체의 형식을 확인할 수 없는 경우 활성 문서의 식별자를 사용하여 문 완성 옵션을 제공합니다. 자세한 내용은 [식별자에 대한 문 완성](../ide/statement-completion-for-identifiers.md)을 참조하세요.

### <a name="html-dom-elements"></a><a name="HTMLDom"></a> HTML DOM 요소
 JavaScript IntelliSense는 `body`, `form` 및 `div` 같은 DHTML(Dynamic HTML) DOM 요소에 대한 프로그래밍 참조를 제공합니다. IntelliSense는 현재 문서와 마스터 페이지에 포함된 요소만 표시합니다. 또한 JavaScript IntelliSense는 `window` 및 `document` 개체와 그 멤버를 지원합니다.

### <a name="intrinsic-objects"></a><a name="IntrinsicObjects"></a> 내장 개체
 JavaScript IntelliSense는 네이티브 `Array`, `String`, `Math`, `Date` 및 `Number` 등의 개체에 대한 프로그래밍 참조를 제공합니다. 내장 개체에 대한 자세한 내용은 [표준 기본 제공 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects)를 참조하세요.

### <a name="user-defined-variables-functions-and-objects"></a><a name="UserDefined"></a> 사용자 정의 변수, 함수 및 개체
 JavaScript 파일을 변경하면 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 열린 문서와 참조된 문서를 검색하여 사용 가능한 모든 코드 리소스를 확인합니다. 여기에는 사용자가 만든 변수, 함수 및 개체가 포함됩니다. 그런 후에는 JavaScript IntelliSense에서 해당 리소스를 사용할 수 있습니다.

 사용자 정의 변수, 함수 및 개체에 대한 자세한 내용은 MSDN 웹 사이트에서 [Creating Your Own Objects](https://msdn.microsoft.com/library/202863ha.aspx)(사용자 고유 개체 만들기)를 참조하세요.

### <a name="external-file-references"></a><a name="External"></a> 외부 파일 참조
 코드에 IntelliSense 지원을 달성하기 위해 다양한 형식의 외부 파일 참조를 포함할 수 있습니다. 외부 파일 참조는 스크립트 참조, 참조 지시문이거나 참조 그룹을 사용하여 지정할 수 있습니다.

#### <a name="script-references"></a><a name="Script"></a> 스크립트 참조
 모든 클라이언트 스크립트를 한 페이지에 작성하는 대신 스크립팅 코드를 포함하는 외부 파일을 참조할 수 있습니다. 그렇게 하면 다른 페이지에서도 코드를 쉽게 재사용할 수 있고 브라우저에서 클라이언트 스크립트를 캐시할 수 있습니다.

 ASP.NET AJAX 사용 웹 페이지에서 작업하는 경우가 아니라면 `src` 요소의 여는 태그에서 `script` 특성을 사용하여 외부 스크립트 파일을 참조할 수 있습니다. `src` 특성은 소스 코드나 데이터가 들어 있는 외부 파일의 URL을 지정합니다.

 다음 예제에서는 <`script`> 태그의 `src` 특성을 사용하여 스크립트 파일을 참조하는 태그를 보여 줍니다.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 ASP.NET AJAX 사용 웹 페이지로 작업하는 경우 <xref:System.Web.UI.ScriptReference> 컨트롤의 <xref:System.Web.UI.ScriptManager> 개체를 사용하여 스크립트 파일을 참조할 수 있습니다.

 다음 예제에서는 <xref:System.Web.UI.ScriptReference> 컨트롤의 <xref:System.Web.UI.ScriptManager> 개체를 사용하여 스크립트 파일을 참조하는 태그를 보여 줍니다.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 IntelliSense는 ASP.NET AJAX 웹 애플리케이션에서 어셈블리의 리소스로 포함된 스크립트 파일도 지원합니다. 포함된 스크립트 리소스에 대한 자세한 내용은 [연습: JavaScript 파일을 어셈블리에 리소스로 포함](https://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89)을 참조하세요.

#### <a name="reference-directives"></a><a name="ReferenceDirectives"></a> 참조 지시문
 `reference` 지시문을 사용하면 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 현재 편집하고 있는 스크립트와 다른 스크립트 사이에 관계를 설정할 수 있습니다. `reference` 지시문을 사용하면 현재 스크립트 파일의 스크립팅 컨텍스트에 스크립트 파일을 포함시킬 수 있습니다. 그러면 코드를 작성할 때 외부에서 정의된 함수, 형식 및 필드를 참조할 수 있습니다.

 `reference` 지시문은 XML 주석 형태로 작성합니다. 이 지시문은 파일에서 다른 스크립트보다 먼저 선언해야 합니다. `reference` 지시문은 디스크 기반 스크립트 참조, 어셈블리 기반 스크립트 참조, 서비스 기반 스크립트 참조 또는 페이지 기반 스크립트 참조를 포함할 수 있습니다

 다음 예제에서는 디스크 기반 참조 지시문을 사용하는 예를 보여 줍니다. 첫 번째 예제에서 언어 서비스는 프로젝트 파일(예: .jsproj)을 포함하는 같은 폴더에서 파일을 찾습니다.

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 다음 예제에서는 어셈블리 기반 스크립트에 대한 참조를 만드는 방법을 보여 줍니다.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 다음 예제에서는 서비스 기반 스크립트를 참조하는 방법을 보여 줍니다.

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
> WAP(웹 애플리케이션 프로젝트)의 웹 서비스 파일(.asmx)에 포함된 스크립트에서는 JavaScript IntelliSense가 지원되지 않습니다.

 다음 예제에서는 페이지 기반 스크립트를 참조하는 방법을 보여 줍니다.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 다음 규칙은 `reference` 지시문에 적용됩니다.

- `reference` XML 주석은 다른 스크립트보다 먼저 선언해야 합니다.

- XML 주석 구문에는 슬래시 세 개를 사용해야 합니다. 표준 주석 구문(슬래시 두 개)을 사용하여 만든 참조는 무시됩니다.

- 지시문 하나 당 하나의 파일 또는 리소스만 지정할 수 있습니다.

- 페이지 기반 스크립트에 대한 다중 참조는 허용되지 않습니다.

- 페이지 참조가 지정되면 다른 형식의 참조 지시문은 사용할 수 없습니다.

- 파일 이름에는 상대 경로를 사용합니다. 물결표 연산자(`~`)를 사용하여 애플리케이션 루트에 상대적인 경로를 만들 수 있습니다.

- 절대 경로는 무시됩니다.

- 참조된 페이지의 참조 지시문은 처리되지 않습니다. 즉, 참조 지시문이 페이지에 대해 재귀적으로 해석되지 않고 페이지에서 직접 참조하는 스크립트만 포함됩니다.

#### <a name="reference-groups"></a><a name="ReferenceGroups"></a> 참조 그룹
 미리 정의된 참조 그룹을 사용하여 다른 JavaScript 프로젝트의 범위에 있는 특정 IntelliSense .js 파일을 지정할 수 있습니다. 다음과 같은 참조 그룹 형식을 사용할 수 있습니다.

- 암시적(Windows), JavaScript를 사용하는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱용 이 그룹에 포함된 파일은 지정된 형식의 프로젝트용 코드 편집기에 열려 있는 각 .js 파일의 범위에 있습니다.

- 암시적(웹), HTML5 프로젝트용 이 그룹에 포함된 파일은 이러한 프로젝트 형식용 코드 편집기에 열려 있는 각 .js 파일의 범위에 있습니다.

- 전용 근로자 참조 그룹, HTML5 웹 작업자용 이 그룹에 지정된 파일은 전용 근로자 참조 그룹을 명시적으로 참조하는 .js 파일 범위에 속합니다.

- 일반, 다른 JavaScript 프로젝트 형식용

  대부분의 시나리오에서 참조 그룹을 수정할 필요가 없습니다. 그러나 변경을 하려면 JavaScript 코드 편집기 구성 옵션을 사용하여 참조 그룹에 포함된 파일을 지정할 수 있습니다. 이 기능을 사용하는 방법에 대한 지침은 [옵션, 텍스트 편집기, C#, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)를 참조하세요.

> [!TIP]
> IntelliSense 참조는 일반적으로 전역 개체 및 IntelliSense [확장명](#Extensibility)에 대한 IntelliSense 지원을 제공하기 위해 사용됩니다. 스크립트 로더를 사용하여 런타임에 로드해야 하는 스크립트에도 이 기능을 사용할 수 있습니다.

### <a name="remote-file-references"></a>원격 파일 참조
 원격 파일 또는 라이브러리에 대해 IntelliSense 지원을 제공하기 위해 Visual Studio에 JavaScript 파일에 참조된 원격 JavaScript 파일을 다운로드하라고 지시할 수 있습니다. 이 기능을 사용하는 경우 JavaScript 파일에 참조로 파일을 포함하면 해당 파일이 다운로드됩니다.

> [!NOTE]
> 웹 프로젝트를 제외하고 이 기능은 프로젝트의 컨텍스트 외부에 열려 있는 JavaScript 파일에 대해서만 작동합니다. 웹 프로젝트의 경우 프로젝트에서 참조된 원격 파일이 기본적으로 다운로드됩니다.

 이 기능을 사용하는 방법에 대한 지침은 [옵션, 텍스트 편집기, C#, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md)를 참조하세요.

> [!WARNING]
> 이 기능을 사용하고 코드 편집기의 성능이 저하되면 사용하지 않는 것이 좋습니다.

### <a name="xml-documentation-comments"></a><a name="XMLDocComments"></a> XML 문서 주석
 XML 문서 주석은 코드 요소 스크립트에 추가하는 텍스트 설명입니다. 이러한 텍스트 설명은 주석 처리된 스크립트를 참조할 때 IntelliSense를 통해 표시됩니다. 예를 들어 함수의 매개 변수 및 반환 값에 대한 정보를 제공할 수 있습니다. 참조된 파일, 어셈블리 및 서비스에서만 XML 문서 주석을 사용할 수 있습니다. 자세한 내용은 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 및 [XML 문서 주석 만들기](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)를 참조하세요.

 IntelliSense는 다음과 같은 시나리오에서 XML 문서 주석을 표시할 수 있습니다.

- 다른 .js 파일을 참조하는 .js 파일

- .aspx 파일을 참조하는 .js 파일

- .js 파일을 참조하는 .aspx 파일

  한 .aspx 파일이 다른 .aspx 파일을 참조하는 경우 IntelliSense를 사용할 수 없습니다.

### <a name="aspnet-ajax-objects"></a><a name="ASPNet"></a> ASP.NET AJAX 개체
 ASP.NET AJAX도 JavaScript IntelliSense를 지원합니다. ASP.NET AJAX에는 ECMAScript(JavaScript)에서 사용할 수 있는 표준 형식을 확장하는 클라이언트 프레임워크가 포함됩니다. JavaScript IntelliSense에서 ASP.NET AJAX 개체에 대한 세부 정보를 제공할 수 있도록 하기 위해 [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)] 전체에 XML 문서 주석이 추가되었습니다. 이러한 XML 문서 주석은 ASP.NET AJAX 라이브러리에 들어 있는 형식과 멤버를 사용할 때 표시됩니다.

> [!NOTE]
> 전용 멤버는 JavaScript IntelliSense에서 표시되지 않습니다. ASP.NET AJAX에서 전용 멤버는 밑줄(_)로 시작하는 멤버로 나타납니다.

## <a name="javascript-intellisense-extensibility"></a><a name="Extensibility"></a> JavaScript IntelliSense 확장성
 JavaScript Language Service는 타사 라이브러리를 사용하는 개발자용 IntelliSense 환경을 수정할 수 있는 개체와 함수를 제공합니다. 이러한 기능은 기본 언어 서비스가 고객에게 제공할 모든 정보를 제공할 수 없는 경우에 특히 유용합니다. 자세한 내용은 [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md)을 참조하세요.

## <a name="javascript-validation"></a><a name="Validation"></a> JavaScript 유효성 검사
 JavaScript 스크립트 유효성 검사는 백그라운드에서 계속 이루어집니다. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]가 JavaScript 코드에서 구문 오류를 감지하면 다음과 같은 방법으로 피드백이 제공됩니다.

- 편집기에서 요소에 밑줄 표시. 물결 모양의 빨간색 밑줄은 오류를 나타냅니다. 오류 위에 마우스 포인터를 놓으면 오류를 설명하는 도구 설명이 표시됩니다.

- **오류 목록** 창. **오류 목록** 창에 오류 설명, 오류가 발생한 파일, 줄 및 열 번호, 프로젝트가 표시됩니다. **오류 목록** 창을 표시하려면 **보기** 메뉴에서 **오류 목록**을 클릭합니다.

- 출력 창에는 로드되지 않은 참조가 표시됩니다.

## <a name="see-also"></a>관련 항목
- [IntelliSense 사용](../ide/using-intellisense.md)
- [XML 문서 주석 만들기](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md)
- [식별자 문 완성](../ide/statement-completion-for-identifiers.md)
- [XML 문서 주석](../ide/xml-documentation-comments-javascript.md)
- [About the DHTML Object Model](https://msdn2.microsoft.com/library/ms533022.aspx)(DHTML 개체 모델 정보)
- [구성원 나열](https://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [SRC 특성 &#124; src 속성](https://msdn2.microsoft.com/library/ms534642.aspx)
