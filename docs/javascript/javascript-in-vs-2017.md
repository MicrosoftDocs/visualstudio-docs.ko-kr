---
title: JavaScript
ms.date: 01/15/2019
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 74dca14c-5071-416f-a92b-d09f95e3dfb8
caps.latest.revision: 1
author: bowdenk7
ms.author: wilkelly
manager: jillfra
ms.openlocfilehash: 2a0d3657843dcf282e5c9aab8609efe5f9611965
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234958"
---
# <a name="javascript-in-visual-studio-2017"></a>Visual Studio 2017의 JavaScript

JavaScript는 Visual Studio의 고급 언어입니다. Visual Studio IDE에서 JavaScript 코드를 작성할 때 대부분 또는 모든 표준 편집 지원(코드 조각, IntelliSense 등)을 사용할 수 있습니다. 여러 애플리케이션 형식 및 서비스에 대해 JavaScript 코드를 작성할 수 있습니다.

> [!NOTE]
> 모든 Microsoft의 JavaScript API 참조(500개 이상의 페이지)를 docs.microsoft.com에서 MDN 사본으로 리디렉션하여 [MDN 웹 문서](https://developer.mozilla.org/en-US/)를 웹의 원스톱, 초연 개발 리소스로 만들려는 커뮤니티 차원의 노력에 동참하였습니다. 자세한 내용은 이 [공지](https://blogs.windows.com/msedgedev/2018/06/26/chakra-docs-mdn-web-docs/)를 참조하세요.

## <a name="ES6"></a> ECMAScript 2015(ES6) 이상 지원

Visual Studio에서는 이제 ECMAScript 2015/2016 등의 ECMAScript 언어 업데이트 구문을 지원합니다.

### <a name="what-is-ecmascript-2015"></a>ECMAScript 2015란?

JavaScript는 여전히 프로그래밍 언어로 발전을 거듭하고 있으며 [TC39](https://www.ecma-international.org/memento/tc39-m.htm)는 업데이트를 담당하는 위원회입니다.
ECMAScript 2015는 새롭고 유용한 구문과 기능을 제공하는 JavaScript 언어의 업데이트입니다. ES6 기능을 자세히 살펴보려면 [이](http://es6-features.org/#Constants) 참조 사이트를 확인하세요.

Visual Studio에서는 ECMAScript 2015 지원 외에도 ECMAScript 2016을 지원하며, ECMAScript의 이후 버전이 릴리스되면 해당 버전도 지원합니다. TC39와 ECMAScript의 최신 변경 사항을 계속 받으려면 [github](https://github.com/tc39)이 작업을 따르세요.

### <a name="transpile-javascript"></a>JavaScript 트랜스파일

JavaScript에는 최신 ES6+ 언어 기능을 사용하면 생산성을 높일 수 있기에 해당 기능을 사용하고 싶지만, 런타임 환경(종종 브라우저)에서 아직 이러한 기능을 지원하지 않는다는 일반적인 문제가 있습니다. 즉, 어떤 브라우저에서 어떤 기능을 지원하는지 계속 추적하는 번거로운 작업을 수행하거나 ES6+ 코드를 대상 런타임에서 이해하는 버전(일반적으로 ES5)으로 변환하는 방법이 필요합니다. 런타임에서 이해하는 버전으로 코드를 변환하는 작업은 일반적으로 "트랜스파일"이라고 합니다.

TypeScript의 주요 기능 중 하나는 생산성을 높이도록 코드를 작성하면서 여전히 모든 플랫폼에서 코드를 실행할 수 있도록 ES6+ 코드를 ES5 또는 ES3로 소스 간 컴파일(transpile)하는 기능입니다. [!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]의 JavaScript에서는 TypeScript와 같은 언어 서비스를 사용하므로 ES6+에서 ES5로의 소스 간 컴파일을 활용할 수 있습니다.

트랜스파일을 설정하기 전에 어느 정도 구성 옵션을 이해해야 합니다.
TypeScript는 `tsconfig.json` 파일을 통해 구성됩니다.
해당 파일이 없는 경우 일부 기본값이 사용됩니다.
호환성 때문에 JavaScript 파일만(그리고 선택적으로 `.d.ts` 파일) 있는 컨텍스트에서는 이러한 기본값이 서로 다릅니다.
JavaScript 파일을 컴파일하려면 `tsconfig.json` 파일을 추가하고 해당 옵션의 일부를 명시적으로 설정해야 합니다.

tsconfig 파일에 대한 필수 설정은 다음과 같습니다.

- `allowJs`: JavaScript 파일이 인식되려면 이 값을 `true`로 설정해야 합니다. 기본값은 `false`입니다. TypeScript는 JavaScript로 컴파일되고 컴파일러는 방금 컴파일한 파일을 포함하지 않아야 하기 때문입니다.
- `outDir`: 내보낸 JavaScript 파일이 검색된 후 프로젝트에 포함되지 않도록 하려면 이 값을 프로젝트에 포함되지 않은 위치로 설정해야 합니다(`exclude` 참조).
- `module`: 모듈을 사용할 경우 이 설정은 내보낸 코드에서 사용해야 하는 모듈 형식을 컴파일러에 알립니다(예: Browserify와 같은 노드 또는 bundler의 경우 `commonjs`).
- `exclude`: 이 설정은 프로젝트에 포함하지 않을 폴더를 나타냅니다.
출력 위치 및 `node_modules` 또는 `temp`와 같은 프로젝트 이외 폴더를 이 설정에 추가해야 합니다.
- `enableAutoDiscovery`: 이 설정을 통해 이전에 설명한 대로 정의 파일을 자동으로 검색 및 다운로드할 수 있습니다.
- `compileOnSave`: 이 설정은 언제든 소스 파일이 Visual Studio에서 저장되면 다시 컴파일해야 하는 경우 컴파일러에 알립니다.
- `typeAcquisition`: 이 설정값 집합을 통해 자동 형식 인식의 동작([이 섹션](/visualstudio/ide/javascript-intellisense#Auto)에서 자세히 설명)을 제어합니다.

JavaScript 파일을 CommonJS 모듈로 변환하고 `./out` 폴더에 두려면 다음 `tsconfig.json` 파일을 사용할 수 있습니다.

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typeAcquisition": {
    "enable": true
  }
}
```

설정이 적용되어 있으며 소스 파일(`./app.js`)이 있고 다음과 같이 여러 ECMAScript 2015 언어 기능이 포함된 경우:

```js
import {Subscription} from 'rxjs/Subscription';  // ES6 import

class Foo {  // ES6 Class
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;  // ES6 template string
    }
}

export let sqr = x => x * x;  //ES6 export, let, and arrow function
export default Subscription;  //ES6 default export
```

다음과 같이 표시되는 ECMAScript 5(기본값)를 대상으로 지정하는 `./out/app.js`로 파일을 내보냅니다.

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
```

## <a name="better-intellisense"></a>더 우수한 IntelliSense

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]의 JavaScript IntelliSense는 이제 매개 변수 및 멤버 목록에 대한 훨씬 더 많은 정보를 표시합니다. 이 새로운 정보는 코드를 더 잘 이해하도록 내부에서 정적 분석으로 사용하는 TypeScript 언어 서비스를 통해 제공됩니다. [여기](/visualstudio/ide/javascript-intellisense/)에서 새 IntelliSense 환경과 작동 방식에 대해 자세히 알아볼 수 있습니다.

## <a name="JSX"></a> JSX 구문 지원

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]의 JavaScript에서는 JSX 구문을 다양하게 지원합니다. JSX는 JavaScript 파일 내에서 HTML 태그를 허용하는 구문 집합입니다.

다음 그림은 `comps.tsx` TypeScript 파일에 정의된 React 구성 요소 및 `app.jsx` 파일에서 사용된 이 구성 요소를 보여준 다음, JSX 식 내에서 완료 및 문서화를 위해 IntelliSense를 통해 완료합니다.
여기에는 TypeScript가 필요하지 않습니다. 이 특정 예제에는 일부 TypeScript 코드도 포함됩니다.

![JSX 구문](../javascript/media/js-react.png)

> [!NOTE]
> JSX 구문을 React 호출로 변환하려면 `"jsx": "react"` 설정을 `compilerOptions` 파일의 `tsconfig.json`에 추가해야 합니다.

빌드 시 `./out/app.js'에서 만들어진 JavaScript 파일에는 다음 코드가 포함됩니다.

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

## <a name="configure-your-javascript-project"></a>JavaScript 프로젝트 구성

언어 서비스는 정적 분석을 통해 구현됩니다. 즉, IntelliSense 결과를 반환하고 다른 편집 기능을 제공하기 위해 실제로 소스 코드를 실행하지 않고도 소스 코드를 분석할 수 있습니다.
따라서 프로젝트 컨텍스트에 포함된 파일의 수량과 크기가 클수록 분석 중에 사용되는 메모리와 CPU가 커집니다.
따라서 프로젝트 형태와 관련된 몇 가지 기본 가정이 있습니다.

- `package.json` 및 `bower.json`는 프로젝트에서 사용하는 종속 항목을 나열하고 기본적으로 ATA(자동 형식 인식)에 포함되어 있습니다.
- 최상위 수준 `node_modules` 폴더에는 라이브러리 소스 코드가 포함되고, 해당 콘텐츠는 기본적으로 프로젝트 컨텍스트에서 제외됩니다.
- 다른 모든 `.js`, `.jsx`, `.ts` 및 `.tsx` 파일은 *고유* 소스 파일 중 하나일 가능성이 크므로 프로젝트 컨텍스트에 포함되어야 합니다.

대부분의 경우 프로젝트를 열기만 하면 기본 프로젝트 구성을 사용하여 멋진 경험을 할 수 있습니다. 그러나 대규모이거나 폴더 구조가 다른 프로젝트인 경우 고유 원본 파일에만 더욱 집중할 수 있도록 언어 서비스를 추가로 구성하는 것이 좋습니다.

### <a name="override-defaults"></a>기본값 덮어쓰기

프로젝트 루트에 `tsconfig.json` 파일을 추가하여 기본 구성을 재정의할 수 있습니다.
`tsconfig.json`에는 프로젝트 컨텍스트를 조작할 수 있는 여러 다른 옵션이 있습니다.
몇 가지 옵션은 아래 나열되어 있지만, 사용 가능한 전체 옵션 집합은 [스키마 저장소를 참조하세요](http://json.schemastore.org/tsconfig).

## <a name="important-tsconfigjson-options"></a>중요한 `tsconfig.json` 옵션

```json
{
  "compilerOptions": {
    "allowJs": true,          // include .js and .jsx in project context (defaults to only .ts and .tsx)
    "noEmit": true            // turns off downlevel compiler
  },
  "files": [],                // list of explicit files to include in the project context. Highest priority.
  "include": [],              // list of folders or glob patterns to include in the project context.
  "exclude": [],              // list of folders or glob patterns to exclude. Overridden by files array.
  "typeAcquisition": {
    "enable": true,           // Defaulted to "false" with a tsconfig. Enables better IntelliSense in JS.
    "include": [ "jquery" ],  // Specific libs to fetch .d.ts files that weren't picked up by ATA
    "exclude": [ "node" ]     // Specific libs to not fetch .d.ts files for
  }
}
```

### <a name="example-project-configuration"></a>예제 프로젝트 구성

다음과 같이 설정된 프로젝트가 제공됩니다.

- 프로젝트의 소스 파일은 `wwwroot/js`에 있음
- 프로젝트의 lib 파일은 `wwwroot/lib`에 있음
- `bootstrap`, `jquery`, `jquery-validation` 및 `jquery-validation-unobtrusive`는 `bower.json`에 나열됨
- `kendo-ui`가 lib 폴더에 수동으로 추가됨

![폴더 구조](../javascript/media/js-folderstructure.png)

다음 `tsconfig.json`을 사용하여 언어 서비스에서 `js` 폴더의 소스 파일만 분석하지만 여전히 `.d.ts` 폴더의 라이브러리를 위해 `lib` 파일을 가져와 사용하도록 할 수 있습니다.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "noEmit": true
  },
  "exclude": ["wwwroot/lib"],  //ignore lib folders, we will get IntelliSense via ATA
  "typeAcquisition": {
    "enable": true,
    "include": [ "kendo-ui" ]  //kendo-ui wasn't added via bower, so we need to list it here
  }
}
```

## <a name="troubleshooting-the-javascript-language-service-has-been-disabled-for-the-following-projects"></a>문제 해결 다음 프로젝트에 대해 JavaScript 언어 서비스를 사용할 수 없습니다.
대규모의 콘텐츠가 있는 JavaScript 프로젝트를 열 때 "JavaScript 언어 서비스가 다음 프로젝트에서 비활성화됩니다."라는 메시지가 표시될 수 있습니다. 대규모의 JavaScript 원본이 있는 가장 일반적인 이유는 20MB 프로젝트 제한을 초과하는 소스 코드를 사용하여 라이브러리를 포함하기 때문입니다.

프로젝트를 간단히 최적화하려면 프로젝트 루트에 `tsconfig.json` 파일을 추가하여 언어 서비스가 무시해도 되는 파일을 알 수 있도록 합니다. 아래 샘플을 사용하여 라이브러리가 저장된 가장 일반적인 디렉터리를 제외합니다.

```json
{
  "compilerOptions": {
    "allowJs": true,
    "allowSyntheticDefaultImports": true,
    "maxNodeModuleJsDepth": 2,
    "noEmit": true,
    "skipLibCheck": true
  },
  "exclude": [
    "**/bin",
    "**/bower_components",
    "**/jspm_packages",
    "**/node_modules",
    "**/obj",
    "**/platforms"
  ]
}
```

필요하다면 디렉터리를 더 추가합니다. "공급 업체" 또는 "wwwroot/lib" 디렉터리를 포함하는 몇 가지 예제입니다.

> [!NOTE]
> 컴파일러 속성 `disableSizeLimit`는 20MB 검사 한계를 비활성화하는 데도 사용할 수 있습니다. 제한을 사용하지 않도록 설정하면 언어 서비스가 중단될 수 있기 때문에 이 속성을 사용할 때 특별한 예방 조치를 취해야 합니다.

## <a name="notable-changes-from-visual-studio-2015"></a>Visual Studio 2015의 주요 변경 내용

[!include[vs_dev15](../../docs/misc/includes/vs_dev15_md.md)]에서 완전히 새로운 언어 서비스를 제공하므로, 이전 환경에 없거나 다른 동작이 몇 가지 있습니다.
가장 주목할 만한 변경 내용으로는 VSDoc를 JSDoc로 대체, 사용자 지정 `.intellisense.js` 확장 제거 및 특정 코드 패턴에 제한된 IntelliSense가 포함됩니다.

### <a name="no-more-references-or-_referencesjs"></a>더 이상 `///<references/>` 또는 `_references.js` 없음

이전에는 언제든 IntelliSense 범위에 있는 파일을 이해하기가 매우 복잡했습니다. 어떤 경우 모든 파일을 범위에 두는 것이 바람직하고, 다른 경우에는 바람직하지 않으므로, 수동 참조 관리를 포함하는 복잡한 구성이 생성됩니다. 앞으로는 더 이상 참조 관리에 대해 고려할 필요가 없으므로 슬래시 3개로 이루어진 참조 주석이나 `_references.js` 파일이 필요하지 않습니다.

IntelliSense 작동 방식에 대한 자세한 내용은 [JavaScript IntelliSense](/visualstudio/ide/javascript-intellisense/) 페이지를 참조하세요.

### <a name="vsdoc"></a>VSDoc

VSDocs라고도 하는 XML 문서 주석은 이전에 IntelliSense 결과를 향상하는 데 사용할 추가 데이터로 소스 코드를 데코레이트하는 데 사용할 수 있었습니다.
VSDoc는 이제 더 쉽게 작성할 수 있고 JavaScript의 표준으로 승인되는 [JSDoc](https://jsdoc.app/about-getting-started.html)를 위해 더 이상 지원되지 않습니다.

### <a name="intellisensejs-extensions"></a>`.intellisense.js` 확장

이전에는 타사 라이브러리용으로 사용자 지정 완료 결과를 추가할 수 있는 [IntelliSense 확장](https://msdn.microsoft.com/library/hh874692.aspx)을 작성할 수 있었습니다.
이러한 확장은 작성하기가 매우 어렵고 설치하여 참조하는 작업음 번거로우므로, 새 언어 서비스에서는 앞으로 이러한 파일을 지원하지 않습니다.
쉬운 대안으로서 TypeScript 정의 파일을 작성하여 이전 `.intellisense.js` 확장과 동일한 IntelliSense 이점을 제공할 수 있습니다.
선언(`.d.ts`) 파일 작성에 대한 자세한 내용은 [여기](http://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)에서 알아볼 수 있습니다.

### <a name="unsupported-patterns"></a>지원되지 않는 패턴

새 언어 서비스는 실행 엔진이 아니라 정적 분석을 통해 구현되므로(차이점에 대한 정보는 [이 문제](https://github.com/Microsoft/TypeScript/issues/4789) 참조) 더 이상 감지되지 않는 JavaScript 패턴이 몇 가지 있습니다.
가장 일반적인 패턴은 “expando” 패턴입니다.
현재 언어 서비스에서는 선언 후에 추가된 속성이 있는 개체에서 IntelliSense를 제공할 수 없습니다.
다음은 그 예입니다.

```js
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense won't show properties a or b
```

개체를 만드는 동안 속성을 선언하여 이 문제를 임시로 해결할 수 있습니다.

```js
var obj = {
    "a": 10,
    "b": "hello world"
}
obj. // IntelliSense shows properties a and b
```

또한 다음과 같이 JSDoc 주석을 추가할 수 있습니다.

```js
/**
 * @type {{a: number, b: string}}
 */
var obj = {};
obj.a = 10;
obj.b = "hello world";
obj. // IntelliSense shows properties a and b
```
