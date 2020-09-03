---
title: JavaScript IntelliSense 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665760"
---
# <a name="extending-javascript-intellisense"></a>JavaScript IntelliSense 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript IntelliSense 확장성 기능을 사용 하면 타사 라이브러리에 대 한 JavaScript 편집기에서 IntelliSense 결과를 사용자 지정할 수 있습니다. 이러한 라이브러리를 사용 하는 개발자의 경험을 향상 시킬 수 있습니다.

 JavaScript 언어 서비스는 프로젝트에 추가 되는 타사 JavaScript 라이브러리에 대 한 IntelliSense 기능을 제공 합니다. 대부분의 라이브러리에 대해 언어 서비스에서 문 완성 기능을 자동으로 제공 합니다. 다음 그림은 문 완성의 예를 보여 줍니다.

 ![문 완성 예제](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 라이브러리에 표준 JavaScript 주석 태그 (//)의 변수, 함수 및 개체에 대 한 설명이 포함 된 경우 기본적으로 IntelliSense 확장성 기능에서 자동으로 이점을 얻을 수 있습니다 .이 기능은 완성 목록에서 요소의 오른쪽에 표시 되는 팝업 상자에 설명 정보를 제공 하거나 함수 호출에 여는 괄호를 입력 합니다. 팝업 상자의 주석에는 멤버에 대 한 설명이 포함 되어 있습니다. 다음 예에서는 완성 목록의 팝업 상자를 보여 줍니다.

 ![요약 정보 팝업&#45;위쪽 상자의 예](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 개발자 환경을 더욱 향상 시키려면 팝업 상자에서 개발자에 게 형식 정보를 제공 하는 것이 좋습니다. 표준 주석 태그 대신 JavaScript [XML 문서 주석을](../ide/xml-documentation-comments-javascript.md) 사용 하 여 형식 정보를 제공할 수 있습니다. 삼중 슬래시 주석 태그 (///) 및 정의 된 XML 요소 집합을 사용 하 여 XML 문서 주석을 추가 합니다.

 또는 JavaScript IntelliSense 확장성을 사용 하 여 형식 정보를 제공할 수 있습니다. 이 기능을 사용 하면 JavaScript 확장을 만들어 스크립트 컨텍스트에 추가 하 여 IntelliSense 결과를 사용자 지정할 수 있습니다. JavaScript 파일인 확장에서 언어 서비스의 개체에 의해 노출 되는 이벤트를 구독 `intellisense` 합니다. JavaScript IntelliSense 확장성은 라이브러리의 동작 패턴이 JavaScript language service에서 원하는 수준의 IntelliSense 지원을 제공 하지 못하도록 하 고 선언적 XML 문서 주석 대신 필요한 경우 라이브러리에 대해 선호 되는 솔루션입니다. IntelliSense 결과를 사용자 지정 하 여 언어 서비스의 기본 기능을 제한할 수 있는 동작 패턴에 관계 없이 최고 수준의 IntelliSense 환경을 만들 수 있습니다. 자세한 내용은 [식별자에 대한 문 완성](../ide/statement-completion-for-identifiers.md)을 참조하세요.

## <a name="adding-an-extension-to-the-script-context"></a>스크립트 컨텍스트에 확장 추가
 IntelliSense 확장을 실행 하려면 현재 스크립트 컨텍스트에 추가 해야 합니다. 자동 검색 메커니즘을 사용 하 여 자동으로 스크립트 컨텍스트에 확장을 추가 하거나 참조 그룹 또는 참조 지시어를 사용 하 여 수동으로 확장을 스크립트 컨텍스트에 추가할 수 있습니다.

 자동 검색 메커니즘을 사용 하면 언어 서비스에서 *libraryname*.intellisense.js 파일 명명 규칙을 따르는 확장을 자동으로 찾을 수 있으며, 확장명이 적용 되는 라이브러리와 동일한 디렉터리에 있습니다. 예를 들어 jQuery 라이브러리의 유효한 확장은 jQuery.intellisense.js 됩니다. 더 제한적인 jQuery 확장의 경우 jQuery-1.7.1.intellisense.js (버전별 확장) 또는 jQuery.ui.intellisense.js (범위가 지정 된 jQuery 라이브러리의 확장명)와 같은 파일 이름을 사용할 수 있습니다. 지정 된 라이브러리에 대해 둘 이상의 확장을 찾은 경우 가장 제한적인 확장 버전이 사용 됩니다.

 모든 JavaScript 프로젝트 파일에 확장을 사용 하려는 경우 대신 참조 그룹에 확장을 추가 하도록 선택할 수 있습니다. 참조 그룹에는 암시적 참조를 포함 하는 참조 그룹과 전용 작업자 참조를 포함 하는 그룹의 여러 가지 형식이 있습니다. 확장을 추가 하려면 일반적으로 암시적 **(Windows)**, **암시적 (웹)** 등의 암시적 참조 그룹으로 파일을 추가 해야 합니다. 암시적 참조는 코드 편집기에 열려 있는 모든 .js 파일의 범위에 있습니다. 이 메서드를 사용 하는 경우 확장을 보완 하는 파일 및 확장명을 모두 추가 해야 합니다.

 **옵션** 대화 상자의 **IntelliSense** 페이지를 사용 하 여 확장을 참조 그룹으로 추가할 수 있습니다. 메뉴 모음에서 **도구**, **옵션** 을 선택한 다음 **텍스트 편집기**, **JavaScript**, **IntelliSense**, **참조**를 선택 하 여 **IntelliSense** 페이지에 액세스할 수 있습니다. 참조 그룹에 대 한 자세한 내용은 [Javascript intellisense](../ide/javascript-intellisense.md) 및 [옵션, 텍스트 편집기, javascript, IntelliSense를](../ide/reference/options-text-editor-javascript-intellisense.md)참조 하세요.

 특정 파일 집합에 확장을 사용 하려면 참조 지시문을 사용 합니다. 이 메서드를 사용 하는 경우 확장을 보완 하는 확장명 및 파일을 모두 참조 해야 합니다. 참조 지시문 사용에 대 한 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md)를 참조 하세요.

## <a name="handling-intellisense-events"></a>IntelliSense 이벤트 처리
 확장성 기능을 사용 하면 `statementcompletion` 언어 서비스 개체의 이벤트와 같은 이벤트를 구독 하 여 IntelliSense 결과를 사용자 지정할 수 있습니다 `intellisense` . 다음 예제에서는 문 완성의 밑줄로 시작 하는 멤버를 숨기기 위해 language service에서 사용 하는 간단한 확장을 보여 줍니다. 이 코드는 underscorefilter.js에 포함 되어 있으며 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더에 있습니다.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 위의 코드에서 확장은 이벤트 개체의 [TargetName 속성](#TargetName) 및 [대상 속성](#Target) 속성을 확인 `statementcompletion` 하 여 및와 같은 개체를 제외 `this` 하 `window` 고 유효한 문 완성 목록을 식별할 수 있는지 확인 합니다. 완성 목록을 식별할 수 있는 경우 확장은 밑줄로 시작 하는 멤버를 필터링 하 여 문 완성 [항목 속성](#Items) 컬렉션을 업데이트 합니다.

 추가 예제를 보려면 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더를 확인 하세요. 이 폴더의 showPlainComments.js 파일은 표준 JavaScript 주석 태그 (//)에 대해 기본 IntelliSense 지원을 제공 하는 다른 이벤트를 사용 하는 예제를 제공 합니다. underscorefilter.js와 마찬가지로 showPlainComments.js를 작업 확장으로 이미 사용할 수 있으며, 코드에서 변수, 함수 및 개체에 대 한 주석 태그를 사용할 때 결과 IntelliSense 정보를 볼 수 있습니다. 추가 예제는 [코드 예제](#CodeExamples)를 참조 하세요.

> [!WARNING]
> Visual Studio에 포함 된 확장 파일을 수정 하는 경우 JavaScript IntelliSense 또는 확장에서 지 원하는 기능을 사용 하지 않도록 설정할 수 있습니다.

 확장 코드에서를 사용 하 여 다음 이벤트 유형에 대 한 처리기를 만들 수 있습니다 `addEventListener` .

- `statementcompletion`-문 완성 이벤트에 대 한 처리기를 추가 합니다. 문 완성에서는 마침표 (.)와 같은 특수 문자를 입력 한 후 또는를 입력 하거나 CTRL + J를 누를 때 표시 되는 식별자 목록과 같은 특수 문자를 입력 한 후 표시 되는 특정 형식에 대 한 멤버 목록을 제공 합니다. 처리기는 `CompletionEvent` [items 속성](#Items), [Target 속성](#Target), [targetName 속성](#TargetName)및 [scope 속성](#Scope)멤버를 지 원하는 형식의 이벤트 개체를 받습니다.

- `signaturehelp`-IntelliSense 매개 변수 정보에 대 한 처리기를 추가 합니다. 매개 변수 정보는 함수에 필요한 매개 변수의 개수, 이름 및 형식에 대 한 정보를 제공 합니다. 처리기는 다음 멤버를 지 원하는 형식의 이벤트 개체를 받습니다 `SignatureHelpEvent` . [target 속성](#Target), [parentobject 속성](#ParentObject), [functioncomments 속성](#FunctionComments), [functioncomments 속성](#FunctionHelp).

- `statementcompletionhint`-IntelliSense 요약 정보에 대 한 처리기를 추가 합니다. 요약 정보 팝업 상자에는 코드의 식별자에 대 한 전체 선언이 표시 됩니다. 처리기는 `CompletionHintEvent` 다음과 같은 멤버를 [symbolHelp Property](#SymbolHelp)지 원하는 형식의 이벤트 [개체를 받습니다](#CompletionItem).

  문 완성, 매개 변수 정보 및 요약 정보와 같은 IntelliSense 기능을 보여 주는 예제는 [Intellisense 사용](../ide/using-intellisense.md)을 참조 하세요.

> [!NOTE]
> JavaScript에서 요약 정보는 완성 목록 오른쪽에 표시 되는 팝업 상자를 나타냅니다. 빠른 정보를 수동으로 호출할 수 없습니다.

## <a name="intellisense-object"></a><a name="intellisenseObject"></a> intellisense 개체
 다음 표에서는 개체에 사용할 수 있는 함수를 보여 줍니다 `intellisense` . `intellisense`개체는 디자인 타임에만 사용할 수 있습니다.

|함수|Description|
|--------------|-----------------|
|`addEventListener(type, handler);`|IntelliSense 이벤트에 대 한 이벤트 처리기를 추가 합니다.<br /><br /> `type` 는 문자열 값입니다. 유효한 값은 `statementcompletion`, `signaturehelp` 및 `statementcompletionhint`입니다.<br /><br /> `handler` 는 다음 형식 중 하나에 해당 하는 이벤트 개체를 받는 이벤트 처리기 함수입니다.<br /><br /> -   `CompletionEvent`이벤트에 사용 되는 `statementcompletion` 입니다.<br />-   `SignatureHelpEvent`이벤트에 사용 되는 `signaturehelp` 입니다.<br />-   `CompletionHintEvent`이벤트에 사용 되는 `statementcompletionhint` 입니다.<br /><br /> 이 함수를 사용 하는 예제는 [코드 예제](#CodeExamples)를 참조 하세요.|
|`annotate(obj, doc);`|한 개체에서 다른 개체로 문서 주석을 복사 하 여 개체에 대 한 설명서를 지정 합니다.<br /><br /> `obj` 설명서를 복사할 개체를 지정 합니다.<br /><br /> `doc` 문서를 복사할 개체를 지정 합니다.<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제는 [IntelliSense 주석 추가](#Annotations)를 참조 하세요.|
|`getFunctionComments(func);`|지정 된 함수에 대 한 주석을 반환 합니다.<br /><br /> `func` 주석이 반환 되는 함수를 지정 합니다.<br /><br /> 을 `func` 사용 하 여 매개 변수를 설정할 수 있습니다 `completionItem.value` .<br /><br /> 반환 된 `functionComments` 개체에는 `above` , 및 멤버가 포함 `inside` 됩니다. `paramComment` 자세한 내용은 [Functioncomments 속성](#FunctionComments) 속성을 참조 하세요.<br /><br /> `getFunctionComments` 는에서 등록 한 이벤트 처리기 중 하나 에서만 호출할 수 있습니다 `addEventListener` .<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제는 \\ \\ *Visual Studio 설치 경로*\JavaScript\References\showPlainComments.js를 참조 하세요.|
|`logMessage(msg);`|진단 메시지를 출력 창으로 보냅니다.<br /><br /> `msg` 는 메시지를 포함 하는 문자열입니다.<br /><br /> 이 함수를 사용 하는 방법을 보여 주는 예제는 [출력 창로 메시지 보내기](#Logging)를 참조 하세요.|
|`nullWithCompletionsOf(value);`|매개 변수에 전달 된 개체에 의해 완성 목록이 결정 되는 특수 null 값을 반환 합니다 `value` .<br /><br /> `value` 반환 된 값에 대 한 완성 목록을 결정 합니다. `value` 모든 형식일 수 있습니다.<br /><br /> Null 반환 값은 디자인 타임에 null로 처리 되지만 반환 값의 완성 목록은 매개 변수의 완성 목록과 동일 합니다 `value` .<br /><br /> 이 함수를 사용 하는 한 가지 방법은 반환 형식이 런타임에 예측 가능한 경우 반환 값에 대해 IntelliSense를 제공 하는 것 이지만, 반환 값은 `null` 디자인 타임에 있습니다.|
|`redirectDefinition(func, definition);`|매개 변수 도움말 또는 **정의로 이동** 이 요청 된 경우 IntelliSense가 원래 func 함수 대신 제공 된 정의 함수를 사용 하도록 지시 합니다.<br /><br /> `func` 대상 함수를 지정 합니다.<br /><br /> `definition` 매개 변수 정보에 대 한 대상 함수 대신 사용할 함수를 지정 하 고 **정의로 이동**합니다.|
|`setCallContext(func, thisArg);`|지정 된 함수에 대 한 호출 컨텍스트 또는 범위를 설정 합니다.<br /><br /> `func` 범위를 설정할 함수를 지정 합니다.<br /><br /> `thisArg` 는 키워드에서 참조할 수 있는 개체 리터럴입니다 .이 개체 `this` 는 멤버의 새 범위를 지정 합니다. 이 매개 변수에 전달 되는 인수를 포함할 수 있습니다 (예:). `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext``Function.prototype.bind`디자인 타임 IntelliSense 지원에만 사용 된다는 점을 제외 하 고와 유사한 동작을 제공 합니다. 다른 방법으로는 연결할 수 없는 코드에 대 한 호출을 시뮬레이션 해야 하는 경우를 사용 하 여 함수 범위를 설정할 수 있습니다 `setCallContext` . 따라서 함수를 호출 하면 함수 호출에 올바른 범위와 인수가 포함 됩니다.|
|`undefinedWithCompletionsOf(value);`|매개 변수에 전달 된 개체에 의해 완성 목록이 결정 되는 특수 하지 않은 특수 값을 반환 합니다 `value` .<br /><br /> `value` 반환 된 값에 대 한 완성 목록을 결정 합니다. `value` 모든 형식일 수 있습니다.<br /><br /> 정의 되지 않은 반환 값은 디자인 타임에 정의 되지 않은 것으로 처리 되지만 반환 값의 완성 목록은 매개 변수의 완성 목록과 같습니다 `value` .<br /><br /> 이 함수를 사용 하는 한 가지 방법은 반환 형식이 런타임에 예측 가능한 경우 반환 값에 대해 IntelliSense를 제공 하는 것 이지만, 반환 값은 디자인 타임에 정의 되지 않습니다.|
|`version()`|Visual Studio 버전을 반환 합니다.|

## <a name="event-members"></a>이벤트 멤버
 다음 섹션에서는 이벤트 개체에 표시 되는 `statementcompletion` , 및 이벤트에 대해 설명 하는 멤버에 대해 설명 합니다. `signaturehelp` `statementcompletionhint`

### <a name="completionitem-property"></a><a name="CompletionItem"></a> 이상 항목 속성
 요약 정보 팝업 상자가 요청 된 완료 항목 이라고 하는 식별자를 반환 합니다. 이 속성은 이벤트 `statementcompletionhint` 개체 및 이벤트 개체의 [items 속성](#Items) 속성에 사용할 수 있습니다 `statementcompletion` .

 반환 값: `completionItem` object

 개체의 멤버는 다음과 같습니다 `completionItem` .

- `name`. 컬렉션에서 사용 되는 경우 읽기/쓰기 `items` 이 고, 그렇지 않으면 읽기 전용입니다. 완료 항목을 식별 하는 문자열을 반환 합니다.

- `kind`. 컬렉션에서 사용 되는 경우 읽기/쓰기 `items` 이 고, 그렇지 않으면 읽기 전용입니다. 완료 항목의 형식을 나타내는 문자열을 반환 합니다. 가능한 값은 메서드, 필드, 속성, 매개 변수, 변수 및 예약 된 값입니다.

- `glyph`. 컬렉션에서 사용 되는 경우 읽기/쓰기 `items` 이 고, 그렇지 않으면 읽기 전용입니다. 완성 목록에 표시 되는 아이콘을 나타내는 문자열을 반환 합니다. 에 사용할 수 있는 값은 `glyph` vs:*glyphType*형식입니다. 여기서 *glyphType* 는 열거형의 언어 독립적 멤버에 해당 합니다. <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> 예를 들어 `vs:GlyphGroupMethod` 는의 가능한 값 중 하나입니다 `glyph` . `glyph`가 설정 되지 않은 경우 `kind` 속성은 기본 아이콘을 결정 합니다.

- `parentObject`. 읽기 전용입니다. 부모 개체를 반환합니다.

- `value`. 읽기 전용입니다. 완료 항목의 값을 나타내는 개체를 반환 합니다.

- `comments`. 읽기 전용입니다. 필드 또는 변수 위에 있는 주석을 포함 하는 문자열을 반환 합니다.

- `scope`. 읽기 전용입니다. 완료 항목의 범위를 반환 합니다. 가능한 값은 전역, 지역, 매개 변수 및 멤버입니다.

### <a name="items-property"></a><a name="Items"></a> items 속성
 문 완성 항목의 배열을 가져오거나 설정 합니다. 배열의 각 요소는 전 [항목 속성](#CompletionItem) 개체입니다. `items`속성은 이벤트 개체에 사용할 수 있습니다 `statementcompletion` .

 반환 값: array

### <a name="functioncomments-property"></a><a name="FunctionComments"></a> functionComments 속성
 함수에 대 한 설명을 반환 합니다. 이 속성은 이벤트 개체에 사용할 수 있습니다 `signaturehelp` .

 반환 값: `comments` object

 개체의 멤버는 다음과 같습니다 `comments` .

- `above`. 함수 위의 주석을 반환 합니다.

- `inside`. 함수 내에서 일반적으로 VSDoc 형식으로 주석을 반환 합니다.

- `paramComments`. 함수의 각 매개 변수에 대 한 설명을 나타내는 배열을 반환 합니다. 배열의 멤버는 다음과 같습니다.

  - `name`. 매개 변수 이름을 나타내는 문자열을 반환 합니다.

  - `comment`. 매개 변수 주석이 포함 된 문자열을 반환 합니다.

### <a name="functionhelp-property"></a><a name="FunctionHelp"></a> functionHelp 속성
 함수에 대 한 도움말을 반환 합니다. 이 속성은 이벤트 개체에 사용할 수 있습니다 `signaturehelp` .

 반환 값: `functionHelp` object

 개체의 멤버는 다음과 같습니다 `functionHelp` .

- `functionName`. 읽기/쓰기입니다. 함수 이름을 포함 하는 문자열을 반환 합니다.

- `signatures`. 읽기/쓰기입니다. 함수 시그니처의 배열을 가져오거나 설정 합니다. 배열의 각 요소는 `signature` 개체입니다. `signature`과 같은 일부 속성은 `locid` 일반적인 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 특성에 해당 합니다.

  개체의 멤버는 `signature` 다음과 같습니다.

  - `description`. 읽기/쓰기입니다. 함수를 설명 하는 문자열을 반환 합니다.

  - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.

  - `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.

  - `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.

  - `externalid`. 읽기/쓰기입니다. 함수의 멤버 ID를 나타내는 문자열을 반환 합니다.

  - `params`. 읽기/쓰기입니다. 함수에 대 한 매개 변수 배열을 가져오거나 설정 합니다. 매개 변수 배열의 각 요소는 `parameter` 요소의 다음 특성에 해당 하는 속성을 포함 하는 개체입니다 [\<param>](../ide/param-javascript.md) .

    - `name`. 읽기/쓰기입니다. 매개 변수 이름을 나타내는 문자열을 반환 합니다.

    - `type`. 읽기/쓰기입니다. 매개 변수 형식을 나타내는 문자열을 반환 합니다.

    - `elementType`. 읽기/쓰기입니다. 형식이 인 경우 `Array` 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.

    - `description`. 읽기/쓰기입니다. 매개 변수를 설명 하는 문자열을 반환 합니다.

    - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.

    - `optional`. 읽기/쓰기입니다. 매개 변수가 선택적인 지 여부를 나타내는 문자열을 반환 합니다. `true` 매개 변수가 선택적인 지 여부를 나타냅니다. `false` 는 그렇지 않음을 나타냅니다.

  - `returnValue`. 읽기/쓰기입니다. 요소의 다음 특성에 해당 하는 속성을 사용 하 여 반환 값 개체를 가져오거나 설정 합니다 [\<returns>](../ide/returns-javascript.md) .

    - `type`. 읽기/쓰기입니다. 반환 형식을 나타내는 문자열을 반환 합니다.

    - `elementType`. 읽기/쓰기입니다. 형식이 인 경우 `Array` 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.

    - `description`. 읽기/쓰기입니다. 반환 값을 설명 하는 문자열을 반환 합니다.

    - `locid`. 읽기/쓰기입니다. 함수에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.

    - `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.

    - `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.

    - `externalid`. 읽기/쓰기입니다. 함수의 멤버 ID를 나타내는 문자열을 반환 합니다.

### <a name="parentobject-property"></a><a name="ParentObject"></a> parentObject 속성
 멤버 함수의 부모 개체를 반환 합니다. 예를 들어의 `document.getElementByID` 경우 `parentObject` 는 개체를 반환 합니다 `document` . 이 속성은 이벤트 개체에 사용할 수 있습니다 `signaturehelp` .

 반환 값: object

### <a name="target-property"></a><a name="Target"></a> 대상 속성
 마침표 (.) 인 트리거 문자의 왼쪽에 있는 항목을 나타내는 개체를 반환 합니다. 함수의 경우 `target` 매개 변수 정보를 요청 하는 함수를 반환 합니다. 이 속성은 `statementcompletion` 및 이벤트 개체에 사용할 수 있습니다 `signaturehelp` .

 반환 값: object

### <a name="targetname-property"></a><a name="TargetName"></a> targetName 속성
 대상을 나타내는 문자열을 반환 합니다. 예를 들어 "this."의 경우 `targetName` "this"를 반환 합니다. "A. B"의 경우 (커서가 "B" 뒤에 있는 경우)는 `targetName` "b"를 반환 합니다. 이 속성은 이벤트 개체에 사용할 수 있습니다 `statementcompletion` .

 반환 값: 문자열

### <a name="symbolhelp-property"></a><a name="SymbolHelp"></a> 기호 도움말 속성
 요약 정보 팝업 상자가 요청 된 완료 항목을 반환 합니다. 이 속성은 이벤트 개체에 사용할 수 있습니다 `statementcompletionhint` .

 반환 값: `symbolHelp` object

 와 같은 개체의 일부 속성은 `symbolHelp` `locid` 일반적인 [XML 문서 주석](../ide/xml-documentation-comments-javascript.md) 특성에 해당 합니다.

 개체의 멤버는 다음과 같습니다 `symbolHelp` .

- `name`. 읽기/쓰기입니다. 식별자 이름을 포함 하는 문자열을 반환 합니다.

- `symbolType`. 읽기/쓰기입니다. 기호 형식을 나타내는 문자열을 반환 합니다. 가능한 값에는 알 수 없음, 부울, 숫자, 문자열, 개체, 함수, 배열, 날짜 및 Regex가 포함 됩니다.

- `symbolDisplayType`. 읽기/쓰기입니다. 표시할 형식 이름이 들어 있는 문자열을 반환 합니다. `symbolDisplayType`가 설정 되지 않은 경우 `symbolType` 가 사용 됩니다.

- `elementType`. 읽기/쓰기입니다. `symbolType`가 인 경우 `Array` 배열에 있는 요소의 형식을 나타내는 문자열을 반환 합니다.

- `scope`. 읽기/쓰기입니다. 기호의 범위를 나타내는 문자열을 반환 합니다. 가능한 값에는 전역, 지역, 매개 변수 및 멤버가 있습니다.

- `description`. 읽기/쓰기입니다. 기호에 대 한 설명이 포함 된 문자열을 반환 합니다.

- `locid`. 읽기/쓰기입니다. 기호에 대 한 지역화 정보를 포함 하는 문자열 식별자를 반환 합니다.

- `helpKeyword`. 읽기/쓰기입니다. 도움말 키워드를 포함 하는 문자열을 반환 합니다.

- `externalFile`. 읽기/쓰기입니다. 멤버 ID를 포함 하는 파일을 나타내는 문자열을 반환 합니다.

- `externalid`. 읽기/쓰기입니다. 기호의 멤버 ID를 나타내는 문자열을 반환 합니다.

- `functionHelp`. 읽기/쓰기입니다. 가 함수 일 때 정보를 포함할 수 있는 [Functionhelp 속성](#FunctionHelp)을 반환 합니다 `symbolType` .

### <a name="scope-property"></a><a name="Scope"></a> scope 속성
 이벤트의 완료 범위를 반환 합니다. 완료 범위에 사용할 수 있는 값은 전역 및 멤버입니다. 이 속성은 이벤트 개체에 사용할 수 있습니다 `statementcompletion` .

 반환 값: 문자열

## <a name="debugging-intellisense-extensions"></a>IntelliSense 확장 디버깅
 확장은 디버그할 수 없지만 [Intellisense 개체](#intellisenseObject) 함수를 사용 하 여 Visual Studio 출력 창에 정보를 보낼 수 있습니다. 이 함수를 사용 하는 방법을 보여 주는 예제는이 항목의 뒷부분에 나오는 [출력 창로 메시지 보내기](#Logging) 를 참조 하세요. `logMessage`가 작동 하려면 하나 이상의 이벤트 처리기를 확장에 등록 해야 합니다.

## <a name="code-examples"></a><a name="CodeExamples"></a> 코드 예제
 이 섹션에는 IntelliSense 확장성 Api를 사용 하는 방법을 보여 주는 코드 예제가 포함 되어 있습니다. 또한 이러한 Api를 사용 하는 다른 방법도 있습니다. 추가 예제는 \\ \\ *Visual Studio 설치 경로*\JavaScript\References 폴더에서 다음 파일을 참조 하세요. JavaScript 언어 서비스에서 사용 하는 작업 예제입니다.

- underscoreFilter.js. 이 코드는 IntelliSense에서 전용 멤버를 숨깁니다. 이벤트에 대 한 이벤트 처리기가 포함 됩니다 `statementcompletion` .

- showPlainComments.js. 이 코드는 표준 주석에 대해 IntelliSense 지원을 제공 합니다. 여기에는 및 이벤트에 대 한 이벤트 처리기가 포함 됩니다 `signaturehelp` `statementcompletionhint` .

### <a name="adding-intellisense-annotations"></a><a name="Annotations"></a> IntelliSense 주석 추가
 다음 절차에서는 라이브러리를 직접 수정 하지 않고 타사 라이브러리에 대 한 IntelliSense 설명서 지원을 제공 하는 방법을 보여 줍니다. 이렇게 하려면 확장에서를 사용할 수 있습니다 `intellisense.annotate` .

 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.

- demoLib.js은 타사 라이브러리를 나타내는 프로젝트 파일입니다.

- IntelliSense 확장인 demoLib.intellisense.js입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.

- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.

##### <a name="to-add-an-intellisense-annotation"></a>IntelliSense 주석을 추가 하려면

1. demoLib.js에 다음 코드를 추가 합니다.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. demoLib.intellisense.js에 다음 코드를 추가 합니다.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. appCode.js에 다음 코드를 입력합니다. IntelliSense 매개 변수 정보로 표시 되는 확장에서 XML 문서 주석을 볼 수 있습니다.

     ![intellisense.annotate의 사용을 보여 주는 예](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. appCode.js에 다음 코드를 입력합니다. 를 입력 하는 동안 IntelliSense 요약 정보로 표시 된 확장에 표준 설명이 표시 됩니다.

     ![intellisense.annotate의 사용을 보여 주는 예](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="sending-messages-to-the-output-window"></a><a name="Logging"></a> 출력 창로 메시지 보내기
 다음 절차에서는 출력 창에 메시지를 보내는 방법을 보여 줍니다. IntelliSense 확장을 디버그 하는 데 도움이 되는 메시지를 보낼 수 있습니다.

 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.

- exampleLib.js은 타사 라이브러리를 나타내는 프로젝트 파일입니다.

- IntelliSense 확장인 exampleLib.intellisense.js입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.

- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.

##### <a name="to-send-a-message-to-the-output-window"></a>출력 창에 메시지를 보내려면

1. exampleLib.js에 다음 코드를 추가 합니다.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. exampleLib.intellisense.js에 다음 코드를 추가 합니다.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. 출력 창의 다음 **에서 출력 표시** 목록에서 **JavaScript Language Service** 을 선택 합니다. 출력 창을 보려면 보기 메뉴에서 **출력** 을 선택 합니다.

5. appCode.js에 다음 코드를 입력합니다. 을 입력 하면 언어 서비스의 메시지가 출력 창에 표시 됩니다. 출력 창의 첫 번째 메시지는 현재 범위에 대 한 문 완성이 요청 되었음을 나타냅니다.

    ```javascript
    some
    ```

     다음은 표시 되는 출력의 부분 뷰입니다.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. 출력 창에서 **모두 지우기** 단추를 선택 합니다.

7. 다음 코드를 입력합니다. 출력 창의 첫 번째 메시지는 멤버 목록이 요청 되었음을 나타냅니다.

    ```javascript
    someVar.
    ```

     다음은 표시 되는 출력의 부분 뷰입니다.

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="changing-the-intellisense-icons"></a><a name="Icons"></a> IntelliSense 아이콘 변경
 다음 절차에서는 기본적으로 IntelliSense에 표시 되는 아이콘을 변경 하는 방법을 보여 줍니다. 이는 네임 스페이스, 클래스, 인터페이스, 열거형 등의 라이브러리 관련 개념에 대 한 IntelliSense 정보를 제공 하는 경우에 유용할 수 있습니다.

 사용 가능한 아이콘 값은을 참조 하십시오 <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> .

 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.

- exampleLib.js은 타사 라이브러리를 represens 하는 프로젝트 파일입니다.

- IntelliSense 확장인 exampleLib.intellisense.js입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.

- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.

##### <a name="to-change-the-icons"></a>아이콘을 변경 하려면

1. exampleLib.js에 다음 코드를 추가 합니다.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. exampleLib.intellisense.js에 다음 코드를 추가 합니다.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. appCode.js에 다음 코드를 입력합니다. 를 입력 하는 동안 {} c #에서 사용 되는 네임 스페이스의 아이콘이 ""로 변경 된 것을 볼 수 있습니다.

     ![문자 모양 속성의 사용을 보여 주는 예](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. appCode.js에 다음 코드를 입력합니다. 를 입력 하면 Enum1 멤버에 대 한 새 열거 아이콘과 SomeClass1 멤버에 대 한 새 클래스 아이콘이 표시 됩니다.

     ![문자 모양 속성의 사용을 보여 주는 예](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="avoiding-run-time-effects-on-intellisense-results"></a><a name="Overriding"></a> IntelliSense 결과에 대 한 런타임 효과 방지
 JavaScript 언어 서비스는 코드를 실행 하 여 IntelliSense 정보를 동적으로 제공 합니다. 따라서 런타임 동작이 때때로 원하는 결과를 방해할 수 있습니다. 다음 절차에서는 런타임 동작이 잘못 된 IntelliSense를 발생 시킬 때 IntelliSense 결과를 재정의 하는 방법을 보여 줍니다.

 이 예제가 작동하려면 프로젝트에 다음 JavaScript 파일이 필요합니다.

- exampleLib.js은 타사 라이브러리를 나타내는 프로젝트 파일입니다.

- IntelliSense 확장인 exampleLib.intellisense.js입니다. 이 파일은 프로젝트에 포함될 필요는 없지만 exampleLib.js와 같은 폴더에 있어야 합니다.

- 응용 프로그램 코드를 표현하는 프로젝트 파일 appCode.js입니다.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>IntelliSense 결과에 대 한 런타임 효과를 방지 하려면

1. exampleLib.js에 다음 코드를 추가 합니다.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     위의 코드에서 래핑된 함수는의 값을 기반으로 하는 초기 호출을 무시 `count` 하 고 결과를 반환 하지 않습니다.

2. appCode.js의 첫 번째 줄로 다음 참조 지시문을 추가합니다. 여기에 사용된 경로는 같은 폴더에 JavaScript 파일이 있음을 나타냅니다.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. appCode.js에 다음 코드를 입력합니다. 래핑된 함수는 호출 되지 않으므로 `throttled` 함수는 아무 결과도 반환 하지 않으므로 IntelliSense 대신 식별자 목록이 표시 됩니다.

     ![Intellisense 결과를 재정의 하는 예제](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. exampleLib.intellisense.js에 다음 코드를 추가 합니다. 그러면 래핑된 함수에 대해 IntelliSense가 예상 대로 표시 되도록 디자인 타임 동작이 변경 됩니다.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. appCode.js에서 이전에 입력 한 것과 동일한 코드를 입력 하 여 결과를 테스트 합니다. 이번에는 IntelliSense가 원하는 정보를 제공 합니다.

     ![IntelliSense 결과를 재정의하는 예](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>관련 항목
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [식별자에 대 한 JavaScript IntelliSense 문 완성](../ide/statement-completion-for-identifiers.md)
