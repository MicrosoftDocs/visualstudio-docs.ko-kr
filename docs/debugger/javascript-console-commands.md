---
title: JavaScript 콘솔 명령 | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: reference
helpviewer_keywords:
- JavaScript Console commands [UWP apps]
- JavaScript debugging, console [UWP apps]
- debugging JavaScript, console [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
- cordova
ms.openlocfilehash: b30b59b95b09cac8308474b2b2963f9b96d58146
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731705"
---
# <a name="javascript-console-commands-in-visual-studio"></a>Visual Studio의 JavaScript 콘솔 명령

명령을 사용하여 Visual Studio의 JavaScript 콘솔 창에서 메시지를 보내고 다른 작업을 수행할 수 있습니다. 이 창을 사용하는 방법을 보여 주는 예제는 [빠른 시작: JavaScript 디버그](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017)를 참조하세요. 이 항목의 정보는 Node.js 앱, UWP 앱 및 Visual Studio Tools for Apache Cordova를 사용하여 만든 앱에 적용됩니다.

JavaScript 콘솔 창이 닫혀 있는 경우 Visual Studio에서 디버그하는 동안 **디버그** > **창** > **JavaScript 콘솔**을 선택하여 콘솔 창을 열 수 있습니다.

> [!NOTE]
> 디버깅 세션 중에 창을 사용할 수 없는 경우 프로젝트의 디버그 속성에서 디버거 형식이 **Script** 로 설정되었는지 확인하세요.

Microsoft Edge 개발자 도구에서 콘솔을 사용하는 방법에 관한 내용은 [이 항목](/microsoft-edge/devtools-guide)을 참조하세요.

## <a name="console-object-commands"></a>콘솔 개체 명령

다음 표는 JavaScript 콘솔 창에서 사용할 수 있거나 코드에서 콘솔로 메시지를 보내는 데 사용할 수 있는 `console` 개체 명령에 대한 구문을 보여줍니다. 이 개체는 여러 폼을 제공하므로 원하는 경우 정보 메시지와 오류 메시지를 구분할 수 있습니다.

로컬 개체의 명명된 콘솔과 혼동되지 않도록 해야 하는 경우 `window.console.[command]` 에서 긴 명령을 사용하면 됩니다.

> [!TIP]
> 이전 버전의 Visual Studio는 전체 명령 집합을 지원하지 않습니다. 지원되는 명령에 대한 정보를 신속하게 얻으려면 콘솔 개체에서 IntelliSense를 사용하세요.

|명령|설명|예제|
|-------------|-----------------|-------------|
|`assert(expression, message)`|`expression` 이 **false**가 되면 메시지를 보냅니다.|`console.assert((x == 1), "assert message: x != 1");`|
|`clear()`|콘솔 창에서 스크립트 오류 메시지를 비롯한 메시지를 지우고 콘솔 창에 나타나는 스크립트도 지웁니다. 콘솔 입력 프롬프트에 입력한 스크립트는 지우지 않습니다.|`console.clear();`|
|`count(title)`|count 명령이 콘솔 창에 호출된 횟수를 보냅니다. 계산되는 각 호출은 `title`(선택 사항)으로 고유하게 식별됩니다.<br /><br /> 콘솔 창의 기존 항목은 `title` 매개 변수(있는 경우)로 식별되고 count 명령으로 업데이트됩니다. 새 항목이 만들어지지 않습니다.|`console.count();`<br /><br /> `console.count("inner loop");`|
|`debug(message)`|콘솔 창에 `message` 를 보냅니다.<br /><br /> 이 명령은 console.log와 동일합니다.<br /><br /> 명령을 사용하여 전달된 개체는 문자열 값으로 전환됩니다.|`console.debug("logging message");`|
|`dir(object)`|지정한 개체를 콘솔 창에 보내고 개체 시각화 도우미에 표시합니다. 시각화 도우미를 사용하여 콘솔 창에서 속성을 검사할 수 있습니다.|`console.dir(obj);`|
|`dirxml(object)`|지정한 XML 노드 `object` 를 콘솔 창에 보내고 XML 노드 트리로 표시합니다.|`console.dirxaml(xmlNode);`|
|`error(message)`|콘솔 창에 `message` 를 보냅니다. 메시지 텍스트는 빨간색이며 이 텍스트 앞에 오류 기호가 옵니다.<br /><br /> 명령을 사용하여 전달된 개체는 문자열 값으로 전환됩니다.|`console.error("error message");`|
|`group(title)`|콘솔 창에 전송된 메시지의 그룹화를 시작하고 `title` (선택 사항)을 그룹 레이블로 보냅니다. 그룹은 중첩될 수 있고 콘솔 창이 트리 뷰에 나타납니다.<br /><br /> 그룹* 명령을 사용하면 구성 요소 모델이 사용 중인 경우와 같은 일부 시나리오에서 콘솔 창 출력을 더욱 쉽게 볼 수 있습니다.|`console.group("Level 2 Header");` <br /> `console.log("Level 2");` <br /> `console.group();` <br /> `console.log("Level 3");` <br /> `console.warn("More of level 3");` <br /> `console.groupEnd();` <br /> `console.log("Back to level 2");` <br /> `console.groupEnd();` <br /> `console.debug("Back to the outer level");`|
|`groupCollapsed(title)`|콘솔 창에 전송된 메시지의 그룹화를 시작하고 `title` (선택 사항)을 그룹 레이블로 보냅니다. `groupCollapsed` 를 사용하여 전송된 그룹은 기본적으로 축소된 뷰에 나타납니다. 그룹은 중첩될 수 있고 콘솔 창이 트리 뷰에 나타납니다.|사용 방법은 `group` 명령과 동일합니다.<br /><br /> `group` 명령의 예를 참조하세요.|
|`groupEnd()`|현재 그룹을 종료합니다.<br /><br /> 요구 사항:<br /><br /> Visual Studio 2013|`group` 명령의 예를 참조하세요.|
|`info(message)`|콘솔 창에 `message` 를 보냅니다. 메시지 앞에 정보 기호가 옵니다.|`console.info("info message");`<br /><br /> 추가 예제는 이 항목의 뒷부분에 나오는 [Formatting console.log output](#ConsoleLog) 을 참조하세요.|
|`log(message)`|콘솔 창에 `message` 를 보냅니다.<br /><br /> 개체를 전달하는 경우 이 명령은 해당 개체를 콘솔 창으로 보내고 개체 시각화 도우미에 표시합니다. 시각화 도우미를 사용하여 콘솔 창에서 속성을 검사할 수 있습니다.|`console.log("logging message");`|
|`msIsIndependentlyComposed(element)`|웹 앱에서 사용됩니다. JavaScript를 사용하는 UWP 앱에서는 지원되지 않습니다.|지원되지 않습니다.|
|`profile(reportName)`|웹 앱에서 사용됩니다. JavaScript를 사용하는 UWP 앱에서는 지원되지 않습니다.|지원되지 않습니다.|
|`profileEnd()`|웹 앱에서 사용됩니다. JavaScript를 사용하는 UWP 앱에서는 지원되지 않습니다.|지원되지 않습니다.|
|`select(element)`|`element` DOM 탐색기 [에서 지정한 HTML](../debugger/quickstart-debug-html-and-css.md)를 선택합니다.|console.select(요소);|
|`time (name)`|선택적 `name` 매개 변수에서 식별하는 타이머를 시작합니다. `console.timeEnd`와 함께 사용할 경우 `time` 과 `timeEnd`사이에 경과된 시간을 계산하고 `name` 문자열을 접두사로 사용하여 결과(단위: ms)를 콘솔에 보냅니다. 성능을 측정하기 위한 앱 코드 계측을 활성화하는 데 사용됩니다.|`console.time("app start");  app.start();  console.timeEnd("app start");`|
|`timeEnd(name)`|선택적 `name` 매개 변수에서 식별하는 타이머를 중지합니다. `time` 콘솔 명령을 참조하세요.|`console.time("app start"); app.start(); console.timeEnd("app start");`|
|`trace()`|스택 추적을 콘솔 창에 보냅니다. 추적에는 파일 이름, 줄 번호 및 열 번호 등의 정보와 완전한 호출 스택이 포함됩니다.|`console.trace();`|
|`warn(message)`|앞에 경고 기호가 오는 `message` 를 콘솔 창에 보냅니다.<br /><br /> 명령을 사용하여 전달된 개체는 문자열 값으로 전환됩니다.|`console.warn("warning message");`|

## <a name="miscellaneous-commands"></a>기타 명령
다음 명령은 JavaScript 콘솔 창에서도 사용할 수 있습니다(코드에서는 사용할 수 없음).

|명령|설명|예제|
|-------------|-----------------|-------------|
|`$0`, `$1`, `$2`, `$3`, `$4`|콘솔 창에 지정된 요소를 반환합니다. `$0`은 DOM 탐색기에서 현재 선택한 요소를 반환하고 `$1`은 DOM 탐색기에서 이전에 선택한 요소를 반환하며 이전에 선택한 네 번째 요소까지 이런 식으로 반환됩니다.|$3|
|`$(id)`|ID별로 요소를 반환합니다. `document.getElementById(id)`에 대한 바로 가기 명령입니다. 여기서 `id` 는 요소 ID를 나타내는 문자열입니다.|`$("contenthost")`|
|`$$(selector)`|CSS 선택기 구문을 사용하여 지정된 선택기와 일치하는 요소의 배열을 반환합니다. `document.querySelectorAll()`에 대한 바로 가기 명령입니다.|`$$(".itemlist")`|
|`cd()`<br /><br /> `cd(window)`|식 계산 컨텍스트를 페이지의 기본 최상위 창에서 지정된 프레임의 창으로 변경할 수 있습니다. 매개 변수 없이 `cd()` 를 호출하면 컨텍스트가 최상위 창에 반환됩니다.|`cd();`<br /><br /> `cd(myframe);`|
|`select(element)`|[DOM 탐색기](../debugger/quickstart-debug-html-and-css.md)에서 지정된 요소를 선택합니다.|`select(document.getElementById("element"));`<br /><br /> `select($("element"));`<br /><br /> `select($1);`|
|`dir(object)`|지정된 개체에 대한 시각화 도우미를 반환합니다. 시각화 도우미를 사용하여 콘솔 창에서 속성을 검사할 수 있습니다.|`dir(obj);`|

## <a name="checking-whether-a-console-command-exists"></a>콘솔 명령이 있는지 여부 확인
특정 명령을 사용하기 전에 이 명령이 있는지 여부를 확인할 수 있습니다. 이 예에서는 `console.log` 명령의 존재 유무를 확인합니다. `console.log` 가 있는 경우 코드에서 호출합니다.

```javascript
if (console && console.log) {
    console.log("msg");
}

```

## <a name="examining-objects-in-the-javascript-console-window"></a>JavaScript 콘솔 창에서 개체 검사
JavaScript 콘솔 창을 사용하면 범위 내에 있는 개체와 상호 작용할 수 있습니다. 콘솔 창에서 범위 외부의 개체를 검토하려면 코드에서 `console.log` , `console.dir`또는 기타 명령을 사용하세요. 또는 개체가 범위 내에 있는 경우 코드에 중단점을 설정(**중단점** > **Insert 중단점**)하여 콘솔 창에서 이 개체와 상호 작용할 수 있습니다.

## <a name="formatting-consolelog-output"></a><a name="ConsoleLog"></a> console.log 출력 서식 지정
여러 인수를 `console.log`에 전달하는 경우 콘솔은 인수를 배열로 처리하고 출력을 연결합니다.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";

console.log(user.first, user.last);
// Output:
// Fred Smith

```

`console.log`는 출력 서식을 지정하기 위한 "printf" 대체 패턴도 지원합니다. 첫 번째 인수에 대체 패턴을 사용하는 경우 추가 인수는 사용되는 순서로 지정된 패턴을 바꾸는 데 사용됩니다.

 다음과 같은 대체 패턴이 지원됩니다.

- %s - 문자열 %i - 정수 %d - 정수 %f - 부동 %o - 개체 %b - 이진 %x - 16진수 %e - 지수

  다음은 `console.log`에 대체 패턴을 사용하는 몇 가지 예제입니다.

```javascript
var user = new Object();
user.first = "Fred";
user.last = "Smith";
user.age = 10.01;
console.log("Hi, %s %s!", user.first, user.last);
console.log("%s is %i years old!", user.first, user.age);
console.log("%s is %f years old!", user.first, user.age);

// Output:
// Hi, Fred Smith!
// Fred is 10 years old!
// Fred is 10.01 years old!
```

## <a name="see-also"></a>참조
- [빠른 시작: JavaScript 디버그](../debugger/quickstart-debug-javascript-using-the-console.md?view=vs-2017)
- [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md?view=vs-2017)
