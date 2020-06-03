---
title: 유닛 테스트 JavaScript 및 TypeScript
description: Visual Studio는 Visual Studio용 Node.js 도구를 사용하는 지원 유닛 테스트 JavaScript 및 TypeScript 코드를 제공합니다.
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 4e3e0b1c1579614454580d2f5446b31c718d7f35
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183108"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Visual Studio의 유닛 테스트 JavaScript 및 TypeScript

Visual Studio용 Node.js 도구를 사용하면 명령 프롬프트로 전환하지 않고도 더 인기 있는 JavaScript 프레임워크를 사용하는 단위 테스트를 작성하고 실행할 수 있습니다.

지원되는 프레임워크는 다음과 같습니다.
* Mocha([mochajs.org](https://mochajs.org/))
* Jasmine([Jasmine.github.io](https://jasmine.github.io/))
* Tape([github.com/substack/tape](https://github.com/substack/tape))
* Jest([jestjs.io](https://jestjs.io/))
* Export Runner(이 프레임워크는 Visual Studio용 Node.js 도구로 한정됨)

원하는 프레임워크가 지원되지 않는 경우 [단위 테스트 프레임워크에 대한 지원 추가](#addingFramework)에서 지원 추가에 대한 정보를 참조하세요.

## <a name="write-unit-tests"></a>단위 테스트 작성

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
> 테스트 탐색기는 TypeScript 파일에서 단위 테스트를 찾을 수 없으므로 *tsconfig.json*에서 `outdir` 또는 `outfile` 옵션을 사용하지 않습니다.

## <a name="run-tests"></a>테스트 실행

Visual Studio 2017 또는 명령줄에서 테스트를 실행할 수 있습니다.

### <a name="run-tests-in-visual-studio-2017"></a>Visual Studio 2017에서 테스트 실행

테스트 탐색기에서 **모두 실행** 링크를 클릭하여 테스트를 실행할 수 있습니다. 또는 하나 이상의 테스트 또는 그룹을 선택하고, 마우스 오른쪽 단추를 클릭하고, 바로 가기 메뉴에서 **선택한 테스트 실행**을 선택하여 테스트를 실행할 수 있습니다. 백그라운드에서 테스트가 실행되고 테스트 탐색기에서 결과를 자동으로 업데이트하고 보여 줍니다. 또한 **선택한 테스트 디버그**를 선택하여 선택한 테스트를 디버깅할 수도 있습니다.

> [!Warning]
> 노드 8+를 사용한 단위 테스트 디버깅은 JavaScript 테스트 파일에 대해서만 작동하며, TypeScript 테스트 파일은 중단점을 적중하지 못합니다. 해결 방법으로 `debugger` 키워드를 사용합니다.

> [!NOTE]
> 현재 테스트 프로파일링 또는 코드 검사를 지원하지 않습니다.

### <a name="run-tests-from-the-command-line"></a>명령줄에서 테스트 실행

다음 명령을 사용하여 Visual Studio 2017용 [개발자 명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)에서 테스트를 실행할 수 있습니다.

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
> *vstest.console.exe*를 찾을 수 없음을 나타내는 오류가 발생하는 경우 일반적인 명령 프롬프트가 아니라 개발자 명령 프롬프트를 열었는지 확인합니다.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>단위 테스트 프레임워크에 대한 지원 추가

JavaScript를 사용하여 검색 및 실행 논리를 구현하여 추가 테스트 프레임워크에 대한 지원을 추가할 수 있습니다. 테스트 프레임워크의 이름이 있는 폴더를 다음에서 추가하여 수행할 수 있습니다.

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

이 폴더는 다음 두 함수를 내보내는 동일한 이름의 JavaScript 파일을 포함해야 합니다.

* `find_tests`
* `run_tests`

`find_tests` 및 `run_tests` 구현에 대한 모범 예제는 다음에서 Mocha 단위 테스트 프레임워크를 위한 구현을 참조하세요.

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

사용 가능한 테스트 프레임워크의 검색이 Visual Studio 시작 시 발생합니다. Visual Studio가 실행되는 동안 프레임워크가 추가되는 경우 프레임워크를 검색하도록 Visual Studio를 다시 시작합니다. 단, 구현을 변경하는 경우에는 다시 시작할 필요가 없습니다.

## <a name="unit-tests-in-other-project-types"></a>다른 프로젝트 형식의 단위 테스트
단위 테스트는 Node.js 프로젝트에만 작성하도록 제한되지 않습니다. TestFramework 및 TestRoot 속성을 C# 또는 Visual Basic 프로젝트에 추가하면 해당 테스트가 열거되고 테스트 탐색기 창을 사용하여 실행할 수 있습니다.

이렇게 하려면 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택한 후 **프로젝트 편집**을 선택합니다. 그런 다음, 프로젝트 파일에서 다음 두 요소를 속성 그룹에 추가합니다.

> [!NOTE]
> 요소를 추가하는 속성 그룹에는 조건이 지정되지 않아야 합니다.
> 조건이 지정되면 예기치 않은 동작이 발생할 수 있습니다.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

다음으로, 지정한 테스트 루트 폴더에 테스트를 추가하면 테스트 탐색기 창에서 실행할 수 있습니다. 처음에 표시되지 않는 경우 프로젝트를 다시 빌드해야 할 수 있습니다.

### <a name="unit-test-net-core-and-net-standard"></a>.NET Core 및 .NET Standard 단위 테스트
위의 속성 외에도 NuGet 패키지 [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)를 설치하고 속성을 설정해야 합니다.

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

일부 테스트 프레임워크에는 테스트 검색을 위한 추가 npm 패키지가 필요할 수 있습니다. 예를 들어 jest는 jest-editor-support npm 패키지를 필요로 합니다. 필요한 경우 특정 프레임워크에 대한 설명서를 확인합니다.
