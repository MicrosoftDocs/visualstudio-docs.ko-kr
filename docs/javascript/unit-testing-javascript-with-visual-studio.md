---
title: 유닛 테스트 JavaScript 및 TypeScript
description: Visual Studio는 Visual Studio용 Node.js 도구를 사용하는 지원 유닛 테스트 JavaScript 및 TypeScript 코드를 제공합니다.
ms.date: 03/18/2021
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dc44e39223fd252ae8c4130a1b358aa6af981119
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671510"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Visual Studio의 유닛 테스트 JavaScript 및 TypeScript

명령 프롬프트로 전환하지 않고도 인기 있는 몇 가지 JavaScript 프레임워크를 사용하여 Visual Studio에서 단위 테스트를 작성하고 실행할 수 있습니다. Node.js 및 ASP.NET Core 프로젝트 모두 지원됩니다.

지원되는 프레임워크는 다음과 같습니다.
* Mocha([mochajs.org](https://mochajs.org/))
* Jasmine([Jasmine.github.io](https://jasmine.github.io/))
* Tape([github.com/substack/tape](https://github.com/substack/tape))
* Jest([jestjs.io](https://jestjs.io/))
* Export Runner(이 프레임워크는 Visual Studio용 Node.js 도구로 한정됨)

ASP.NET Core 및 JavaScript 또는 TypeScript에 대해서는 [ASP.NET Core에 대한 단위 테스트 작성](#write-unit-tests-for-aspnet-core)을 참조하세요.

원하는 프레임워크가 지원되지 않는 경우 [단위 테스트 프레임워크에 대한 지원 추가](#addingFramework)에서 지원 추가에 대한 정보를 참조하세요.

## <a name="write-unit-tests-in-a-nodejs-project"></a>Node.js 프로젝트에서 단위 테스트 작성

단위 테스트를 프로젝트에 추가하기 전에 사용하려는 프레임워크가 프로젝트에서 로컬로 설치되어 있는지 확인합니다. 이는 [npm 패키지 설치 창](npm-package-management.md#npmInstallWindow)을 사용하여 손쉽게 수행할 수 있습니다.

단위 테스트를 프로젝트에 추가하는 기본 방법은 프로젝트에 *테스트* 폴더를 만들고 프로젝트 속성에서 테스트 루트로 설정하는 것입니다. 또한 사용하려는 테스트 프레임워크를 선택해야 합니다.

![테스트 루트 및 테스트 프레임워크 설정](../javascript/media/unit-test-project-properties.png)

**새 항목 추가** 대화 상자를 사용하여 프로젝트에 간단한 빈 테스트를 추가할 수 있습니다. JavaScript 및 TypeScript는 모두 동일한 프로젝트에서 지원됩니다.

![새 단위 테스트 추가](../javascript/media/unit-test-add-new-item.png)

Mocha 단위 테스트의 경우 다음 코드를 사용합니다.

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

프로젝트 속성에서 단위 테스트 옵션을 설정하지 않은 경우 **속성** 창에서 **테스트 프레임워크** 속성이 단위 테스트 파일에 대해 올바른 테스트 프레임워크로 설정되어 있는지 확인해야 합니다. 이는 단위 테스트 파일 템플릿에서 자동으로 수행됩니다.

![테스트 프레임워크](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> 단위 테스트 옵션은 개별 파일에 대한 설정에 대해 우선적으로 적용됩니다.

테스트 탐색기를 연 후(**테스트** > **Windows** > **테스트 탐색기** 선택), Visual Studio가 검색하고 테스트가 표시됩니다. 테스트가 처음에 표시되지 않을 경우 프로젝트를 다시 빌드하여 목록을 새로 고칩니다.

![테스트 탐색기](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> TypeScript의 경우 테스트 탐색기는 단위 테스트를 찾을 수 없으므로 *tsconfig.json* 에서 `outdir` 또는 `outfile` 옵션을 사용하지 않습니다.

## <a name="run-tests-nodejs"></a>테스트 실행(Node.js)

Visual Studio 또는 명령줄에서 테스트를 실행할 수 있습니다.

### <a name="run-tests-in-visual-studio"></a>Visual Studio에서 테스트 실행

::: moniker range=">=vs-2019"
테스트 탐색기에서 **모두 실행** 링크를 클릭하여 테스트를 실행할 수 있습니다. 또는 하나 이상의 테스트 또는 그룹을 선택하고, 마우스 오른쪽 단추를 클릭하고, 바로 가기 메뉴에서 **실행** 을 선택하여 테스트를 실행할 수 있습니다. 백그라운드에서 테스트가 실행되고 테스트 탐색기에서 결과를 자동으로 업데이트하고 보여 줍니다. 또한 마우스 오른쪽 단추를 클릭하고 **디버그** 를 선택하여 선택한 테스트를 디버그할 수도 있습니다.
::: moniker-end
::: moniker range="vs-2017"
테스트 탐색기에서 **모두 실행** 링크를 클릭하여 테스트를 실행할 수 있습니다. 또는 하나 이상의 테스트 또는 그룹을 선택하고, 마우스 오른쪽 단추를 클릭하고, 바로 가기 메뉴에서 **선택한 테스트 실행** 을 선택하여 테스트를 실행할 수 있습니다. 백그라운드에서 테스트가 실행되고 테스트 탐색기에서 결과를 자동으로 업데이트하고 보여 줍니다. 또한 **선택한 테스트 디버그** 를 선택하여 선택한 테스트를 디버깅할 수도 있습니다.
::: moniker-end

TypeScript의 경우 생성된 JavaScript 코드에 대해 단위 테스트를 실행합니다.

> [!NOTE]
> 대부분 TypeScript 시나리오에서는 TypeScript 코드에서 중단점을 설정하고, 테스트 탐색기에서 테스트를 마우스 오른쪽 단추로 클릭한 다음, **디버그** 를 선택하여 단위 테스트를 디버그할 수 있습니다. 소스 맵을 사용하는 몇 가지 시나리오와 같은 더 복잡한 시나리오에서는 TypeScript 코드에서 중단점에 적중하는 것이 어려울 수 있습니다. 해결 방법으로 `debugger` 키워드를 사용해 보세요.

> [!NOTE]
> 현재 테스트 프로파일링 또는 코드 검사를 지원하지 않습니다.

### <a name="run-tests-from-the-command-line"></a>명령줄에서 테스트 실행

다음 명령을 사용하여 Visual Studio용 [개발자 명령 프롬프트](../ide/reference/command-prompt-powershell.md)에서 테스트를 실행할 수 있습니다.

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

이 명령은 다음과 유사한 출력 결과를 표시합니다.

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> *vstest.console.exe* 를 찾을 수 없음을 나타내는 오류가 발생하는 경우 일반적인 명령 프롬프트가 아니라 개발자 명령 프롬프트를 열었는지 확인합니다.

## <a name="write-unit-tests-for-aspnet-core"></a>ASP.NET Core에 대한 단위 테스트 작성

1. ASP.NET Core 프로젝트를 만들고 TypeScript 지원을 추가합니다.

   예제 프로젝트는 [TypeScript를 사용하여 ASP.NET Core 앱 만들기](../javascript/tutorial-aspnet-with-typescript.md)를 참조하세요. 유닛 테스트를 지원하려면 표준 ASP.NET Core 프로젝트 템플릿으로 시작하는 것이 좋습니다.

   npm TypeScript 패키지 대신 NuGet 패키지를 사용하여 TypeScript 지원을 추가합니다.

1. NuGet 패키지 [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)를 설치합니다.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드** 를 선택합니다.

   *.csproj* 파일은 Visual Studio에서 열어야 합니다.

1. *.csproj* 파일의 `PropertyGroup` 요소에 다음 요소를 추가합니다.

   이 예제에서는 Mocha를 테스트 프레임워크로 지정합니다. Jest, Tape 또는 Jasmine을 대신 지정할 수 있습니다.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot` 요소는 단위 테스트가 프로젝트 루트의 *tests* 폴더에 있도록 지정합니다.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 다시 로드** 를 선택합니다.

1. npm 패키지 관리 문서의 [ASP.NET Core 프로젝트](../javascript/npm-package-management.md#aspnet-core-projects) 아래에 설명된 대로 npm 지원을 추가합니다.

   이렇게 하려면 npm 지원을 위해 Node.js 런타임을 설치하고 프로젝트 루트에 *package.json* 을 추가해야 합니다.

1. *package.json* 의 종속성 아래에서 원하는 npm 패키지를 추가합니다.

   예를 들어 mocha인 경우 다음을 사용할 수 있습니다.

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Jest 같은 일부 유닛 테스트 프레임워크에는 추가 npm 패키지가 필요합니다. Jest의 경우 다음 JSON을 사용합니다.

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > 일부 시나리오에서는 [여기](https://github.com/aspnet/Tooling/issues/479)에 설명된 알려진 문제로 인해 npm 노드가 솔루션 탐색기에 표시되지 않을 수 있습니다. npm 노드를 표시해야 하는 경우 프로젝트를 언로드(프로젝트를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드** 선택)했다가 프로젝트를 다시 로드하여 npm 노드가 다시 나타나도록 할 수 있습니다.

1. 테스트에 코드를 추가합니다.

   [TypeScript를 사용하여 ASP.NET Core 앱 만들기](tutorial-aspnet-with-typescript.md)에 설명된 예제를 사용하는 경우 *scripts* 폴더에 있는 *library.ts* 파일의 끝에 다음 코드를 추가합니다.

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   TypeScript의 경우 생성된 JavaScript 코드에 대해 단위 테스트를 실행합니다.

1. 프로젝트 루트의 *tests* 폴더에 단위 테스트를 추가합니다.

   예를 들어 테스트 프레임워크(이 예제에서는 Mocha 또는 Jest)와 일치하는 올바른 설명서 탭을 선택하여 다음 코드를 사용할 수 있습니다. 이 코드는 `getData`라는 함수를 테스트합니다.

   # <a name="mocha"></a>[모카](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[Jest](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. 테스트 탐색기를 열면(**테스트** > **Windows** > **테스트 탐색기** 선택) Visual Studio에서 테스트를 검색하여 표시합니다. 테스트가 처음에 표시되지 않을 경우 프로젝트를 다시 빌드하여 목록을 새로 고칩니다.

   ![테스트 탐색기 테스트 검색](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > TypeScript의 경우 테스트 탐색기에서 단위 테스트를 찾을 수 없으므로 *tsconfig.json* 에서 `outfile` 옵션을 사용하지 마세요. `outdir` 옵션은 사용할 수 있지만 `package.json` 및 `tsconfig.json` 같은 구성 파일이 프로젝트 루트에 있어야 합니다.

## <a name="run-tests-aspnet-core"></a>테스트 실행(ASP.NET Core)

::: moniker range=">=vs-2019"
테스트 탐색기에서 **모두 실행** 링크를 클릭하여 테스트를 실행할 수 있습니다. 또는 하나 이상의 테스트 또는 그룹을 선택하고, 마우스 오른쪽 단추를 클릭하고, 바로 가기 메뉴에서 **실행** 을 선택하여 테스트를 실행할 수 있습니다. 백그라운드에서 테스트가 실행되고 테스트 탐색기에서 결과를 자동으로 업데이트하고 보여 줍니다. 또한 마우스 오른쪽 단추를 클릭하고 **디버그** 를 선택하여 선택한 테스트를 디버그할 수도 있습니다.
::: moniker-end
::: moniker range="vs-2017"
테스트 탐색기에서 **모두 실행** 링크를 클릭하여 테스트를 실행할 수 있습니다. 또는 하나 이상의 테스트 또는 그룹을 선택하고, 마우스 오른쪽 단추를 클릭하고, 바로 가기 메뉴에서 **선택한 테스트 실행** 을 선택하여 테스트를 실행할 수 있습니다. 백그라운드에서 테스트가 실행되고 테스트 탐색기에서 결과를 자동으로 업데이트하고 보여 줍니다. 또한 **선택한 테스트 디버그** 를 선택하여 선택한 테스트를 디버깅할 수도 있습니다.
::: moniker-end

TypeScript의 경우 생성된 JavaScript 코드에 대해 단위 테스트를 실행합니다.

![테스트 탐색기 결과](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> 대부분 TypeScript 시나리오에서는 TypeScript 코드에서 중단점을 설정하고, 테스트 탐색기에서 테스트를 마우스 오른쪽 단추로 클릭한 다음, **디버그** 를 선택하여 단위 테스트를 디버그할 수 있습니다. 소스 맵을 사용하는 몇 가지 시나리오와 같은 더 복잡한 시나리오에서는 TypeScript 코드에서 중단점에 적중하는 것이 어려울 수 있습니다. 해결 방법으로 `debugger` 키워드를 사용해 보세요.

> [!NOTE]
> 현재 테스트 프로파일링 또는 코드 검사를 지원하지 않습니다.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>단위 테스트 프레임워크에 대한 지원 추가

JavaScript를 사용하여 검색 및 실행 논리를 구현하여 추가 테스트 프레임워크에 대한 지원을 추가할 수 있습니다. 테스트 프레임워크의 이름이 있는 폴더를 다음에서 추가하여 수행할 수 있습니다.

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

이 폴더는 다음 두 함수를 내보내는 동일한 이름의 JavaScript 파일을 포함해야 합니다.

* `find_tests`
* `run_tests`

`find_tests` 및 `run_tests` 구현에 대한 모범 예제는 다음에서 Mocha 단위 테스트 프레임워크를 위한 구현을 참조하세요.

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

사용 가능한 테스트 프레임워크의 검색이 Visual Studio 시작 시 발생합니다. Visual Studio가 실행되는 동안 프레임워크가 추가되는 경우 프레임워크를 검색하도록 Visual Studio를 다시 시작합니다. 단, 구현을 변경하는 경우에는 다시 시작할 필요가 없습니다.

## <a name="unit-tests-in-net-framework"></a>.NET Framework의 단위 테스트

단위 테스트는 Node.js 및 ASP.NET Core 프로젝트에서만 작성하도록 제한되지 않습니다. TestFramework 및 TestRoot 속성을 C# 또는 Visual Basic 프로젝트에 추가하면 해당 테스트가 열거되고 테스트 탐색기 창을 사용하여 실행할 수 있습니다.

이렇게 하려면 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드** 를 선택한 후 **프로젝트 편집** 을 선택합니다. 그런 다음, 프로젝트 파일에서 다음 두 요소를 속성 그룹에 추가합니다.

> [!IMPORTANT]
> 요소를 추가하는 속성 그룹에는 조건이 지정되지 않아야 합니다.
> 조건이 지정되면 예기치 않은 동작이 발생할 수 있습니다.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

다음으로, 지정한 테스트 루트 폴더에 테스트를 추가하면 테스트 탐색기 창에서 실행할 수 있습니다. 처음에 표시되지 않는 경우 프로젝트를 다시 빌드해야 할 수 있습니다.

## <a name="unit-test-net-core-and-net-standard"></a>.NET Core 및 .NET Standard 단위 테스트

위의 속성 외에도 NuGet 패키지 [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)를 설치하고 속성을 설정해야 합니다.

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

일부 테스트 프레임워크에는 테스트 검색을 위한 추가 npm 패키지가 필요할 수 있습니다. 예를 들어 jest는 jest-editor-support npm 패키지를 필요로 합니다. 필요한 경우 특정 프레임워크에 대한 설명서를 확인합니다.
