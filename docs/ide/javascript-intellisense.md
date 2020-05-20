---
title: JavaScript IntelliSense
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2459c9ab7b6dc6e49bbbe86729d25a2adb5bdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593722"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense

Visual Studio에서는 즉시 사용 가능한 강력한 JavaScript 편집 환경을 제공합니다. TypeScript 기반 언어 서비스로 제공되는 Visual Studio는 더 다양한 IntelliSense, 최신 JavaScript 기능 지원 및 정의로 이동, 리팩터링 등의 향상된 생산성 기능을 제공합니다.

> [!NOTE]
> Visual Studio 2017부터 JavaScript 언어 서비스에는 새로운 언어 서비스용 엔진("Salsa"라고 함)이 사용됩니다. 자세한 내용은 이 문서에 포함되어 있고 이 [블로그 게시물](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/)을 참조할 수도 있습니다. 새 편집 환경은 일반적으로 Visual Studio Code에도 적용됩니다. 자세한 내용은 [VS 코드 문서](https://code.visualstudio.com/docs/languages/javascript)를 참조하세요.

Visual Studio의 일반 IntelliSense 기능에 대한 자세한 내용은 [IntelliSense 사용](../ide/using-intellisense.md)을 참조하세요.

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Visual Studio 2017의 JavaScript 언어 서비스의 새로운 기능

Visual Studio 2017부터 JavaScript IntelliSense는 매개 변수 및 멤버 목록에 대한 더 많은 정보를 표시합니다. 이 새로운 정보는 코드를 더 잘 이해하도록 내부에서 정적 분석으로 사용하는 TypeScript 언어 서비스를 통해 제공됩니다.

TypeScript는 여러 소스를 사용하여 이 정보를 구성합니다.

- [형식 유추 기반 IntelliSense](#TypeInference)
- [JSDoc 기반 IntelliSense](#JsDoc)
- [TypeScript 선언 파일 기반 IntelliSense](#TsDeclFiles)
- [형식 정의의 자동 획득](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>형식 유추 기반 IntelliSense

JavaScript에서는 일반적으로 명시적 형식 정보를 사용할 수 없습니다. 다행히도 주변 코드 컨텍스트가 있는 경우 일반적으로 형식을 쉽게 알아낼 수 있습니다.
이 프로세스를 형식 유추라고 합니다.

일반적으로 변수 또는 속성의 형식은 초기화에 사용된 값 또는 가장 최근 값 할당의 형식입니다.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

함수의 반환 형식은 return 문에서 유추할 수 있습니다.

함수 매개 변수의 경우 현재 유추가 없지만 JSDoc 또는 TypeScript *.d.ts* 파일을 사용하여 이 문제를 해결할 수 있습니다(이후 섹션 참조).

또한 다음에 대한 특수 유추가 있습니다.

- "ES3-style" 클래스 - 프로토타입 속성에 대한 생성자 함수 및 할당을 사용하여 지정됩니다.
- CommonJS-style 모듈 패턴 - `exports` 개체의 속성 할당 또는 `module.exports` 속성에 대한 할당으로 지정됩니다.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>JSDoc 기반 IntelliSense

형식 유추에서 원하는 형식 정보(또는 지원 문서 정보)가 제공되지 않으면 JSDoc 주석을 통해 명시적으로 형식 정보를 제공할 수 있습니다.  예를 들어 부분적으로 선언된 개체에 특정 형식을 제공하려면 다음과 같이 `@type` 태그를 사용할 수 있습니다.

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

설명한 것처럼 함수 매개 변수는 유추되지 않습니다. 그러나 JSDoc `@param` 태그를 사용하여 함수 매개 변수에 형식을 추가할 수도 있습니다.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

현재 지원되는 JsDoc 주석은 [JavaScript에서 JSDoc 지원](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript)을 참조합니다.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>TypeScript 선언 파일 기반 IntelliSense

JavaScript 및 TypeScript는 이제 같은 언어 서비스에 기반을 두므로 더 다양한 방법으로 조작할 수 있습니다. 예를 들어 JavaScript IntelliSense는 *.d.ts* 파일에 선언된 값에 대해 제공될 수 있고([TypeScript 설명서](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html) 참조), TypeScript에 선언된 인터페이스 및 클래스 등의 형식은 JsDoc 주석에서 형식으로 사용할 수 있습니다.

다음 내용은 `JsDoc` 태그를 사용하는 같은 프로젝트에서 인터페이스를 통해 이 형식 정보를 JavaScript 파일에 제공하는 TypeScript 정의 파일의 간단한 예제입니다.

![TypeScript 정의 파일](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>형식 정의의 자동 획득

TypeScript 환경에서 가장 인기 있는 JavaScript 라이브러리에는 *.d.ts* 파일을 통해 설명되는 API가 있고 해당 정의의 가장 일반적인 리포지토리는 [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)에 있습니다.

기본적으로 Salsa 언어 서비스는 어떤 JavaScript 라이브러리가 사용 중인지 검색하고, 더 다양한 IntelliSense를 제공하기 위해 라이브러리를 설명하는 해당 *.d.ts* 파일을 자동으로 다운로드하여 참조합니다. 파일은 *%LOCALAPPDATA%\Microsoft\TypeScript*의 사용자 폴더 아래에 있는 캐시에 다운로드됩니다.

> [!NOTE]
> *tsconfig.json* 구성 파일을 사용할 경우 이 기능은 기본적으로 **사용되지 않지만** 아래 추가로 설명된 대로 사용되도록 설정할 수 있습니다.

현재 자동 검색은 npm에서 다운로드된 종속성(*package.json* 파일 읽기 수행), Bower(*bower.json* 파일 읽기 수행) 및 대략 상위 400개의 가장 인기 있는 JavaScript 라이브러리 목록과 일치하는 프로젝트의 느슨한 파일에 적용됩니다. 예를 들어 프로젝트에 *jquery-1.10.min.js*가 있는 경우 더 나은 편집 환경을 제공하기 위해 *jquery.d.ts* 파일이 페치 및 다운로드됩니다. 이 *.d.ts* 파일은 프로젝트에 영향을 미치지 않습니다.

자동 획득을 사용하지 않으려면 다음 설명대로 구성 파일을 추가하여 기능을 사용하지 않도록 설정합니다. 사용할 정의 파일을 직접 프로젝트 내에 수동으로 배치할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [IntelliSense 사용](../ide/using-intellisense.md)
- [JavaScript 지원(Mac용 Visual Studio)](/visualstudio/mac/javascript)
