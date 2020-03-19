---
title: 솔루션이나 프로젝트 없이 Visual Studio에서 JavaScript 코드 작성
titleSuffix: ''
description: Visual Studio는 프로젝트 파일이나 솔루션 파일에 대한 종속성 없이 코드 작성을 지원
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 288cb11d3e6ae3917f5fcc6ec9ed242549908576
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888649"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>솔루션이나 프로젝트 없이 Visual Studio에서 JavaScript 및 TypeScript 코드 개발

Visual Studio 2017부터 [프로젝트 또는 솔루션 없이 코드 개발](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 통해 코드의 폴더를 열고 IntelliSense, 검색, 리팩터링, 디버깅 등과 같은 다양한 편집기 지원 작업을 즉시 시작할 수 있습니다. 이러한 기능 외에도 Visual Studio용 Node.js 도구는 TypeScript 파일 작성, npm 패키지 관리 및 npm 스크립트를 실행하기 위한 지원이 추가되었습니다.

시작하려면 도구 모음에서 **파일** > **열기** > **폴더**를 선택합니다. 솔루션 탐색기는 폴더에 있는 모든 파일을 표시하며 파일을 열어 편집을 시작할 수 있습니다. 백그라운드에서 Visual Studio는 npm, 빌드 및 디버그 기능을 사용하도록 파일을 인덱싱합니다.

> [!IMPORTANT]
> npm 통합을 포함하여 이 문서에서 설명하는 많은 기능에는 Visual Studio 2017 버전 15.8 이상이 필요합니다.

## <a name="npm-integration"></a>npm 통합

열린 폴더에 *package.json* 파일이 있는 경우 *package.json*을 마우스 오른쪽 단추로 클릭하여 npm에 해당하는 컨텍스트 메뉴(바로 가기 메뉴)를 표시할 수 있습니다.

![솔루션 탐색기의 npm 메뉴](../javascript/media/solution-explorer-npm-ctx.png)

바로 가기 메뉴에서 프로젝트 파일을 사용할 때 [npm 패키지 관리](npm-package-management.md)와 동일한 방법으로 npm으로 설치된 패키지를 관리할 수 있습니다.

또한 이 메뉴를 사용하면 `scripts`package.json*의*  요소에 정의된 스크립트를 실행할 수도 있습니다. 이러한 스크립트는 `PATH` 환경 변수에서 사용할 수 있는 Node.js 버전을 사용합니다. 스크립트는 새 창에서 실행됩니다. 이는 빌드를 실행하거나 스크립트를 실행하는 좋은 방법입니다.

## <a name="build-and-debug"></a>빌드 및 디버그

### <a name="packagejson"></a>package.json
폴더의 *package.json*에 `main` 요소를 지정하는 경우 **package.json**의 오른쪽 클릭 바로 가기 메뉴에서 *디버그* 명령을 사용할 수 있습니다.
이를 클릭하면 *node.exe*가 지정된 스크립트를 인수로 시작합니다.

### <a name="javascript-files"></a>JavaScript 파일
파일을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **디버그**를 선택하여 JavaScript 파일을 디버깅할 수 있습니다. 그러면 *node.exe*가 해당 JavaScript 파일을 인수로 시작합니다.

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript 파일 및 tsconfig.json
폴더에 *tsconfig.json*이 없으면 TypeScript 파일을 마우스 오른쪽 단추로 클릭하여 해당 파일을 빌드하고 디버깅할 수 있는 바로 가기 메뉴 명령을 볼 수 있습니다. 이러한 명령을 사용하면 *tsc.exe*를 기본 옵션으로 사용하여 빌드하거나 디버깅합니다. (디버그하려면 파일을 빌드해야 합니다.)

> [!NOTE]
> TypeScript 코드를 작성할 때 `C:\Program Files (x86)\Microsoft SDKs\TypeScript`에 설치된 최신 버전을 사용합니다.

폴더에 *tsconfig.json* 파일이 있으면 TypeScript 파일을 마우스 오른쪽 단추로 클릭하여 해당 TypeScript 파일을 디버깅할 수 있는 메뉴 명령을 볼 수 있습니다. 옵션은 `outFile`tsconfig.json*에 지정된* 이 없는 경우에만 나타납니다. `outFile`을 지정하면 *tsconfig.json*을 마우스 오른쪽 단추로 클릭하고 올바른 옵션을 선택하여 해당 파일을 디버깅할 수 있습니다. `tsconfig.json` 파일은 컴파일러 옵션을 지정할 수 있는 빌드 옵션도 제공합니다.

> [!NOTE]
> *tsconfig.json*에 대한 자세한 내용은 [tsconfig.json TypeScript Handbook 페이지](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)에서 찾을 수 있습니다.

## <a name="unit-tests"></a>단위 테스트
*package.json*에 테스트 루트를 지정하면 Visual Studio에서 단위 테스트 통합을 설정할 수 있습니다.

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test Runner는 사용할 테스트 프레임워크를 결정할 수 있도록 로컬에 설치된 패키지를 열거합니다.
지원되는 프레임워크가 전혀 인식되지 않으면 Test Runner가 기본값으로 *ExportRunner*를 지정합니다. 기타 지원되는 프레임워크는 다음과 같습니다.
* Mocha([mochajs.org](https://mochajs.org/))
* Jasmine([Jasmine.github.io](https://jasmine.github.io/))
* Tape([github.com/substack/tape](https://github.com/substack/tape))
* Jest([jestjs.io](https://jestjs.io/))

테스트 탐색기를 연 후(**테스트** > **Windows** > **테스트 탐색기** 선택), Visual Studio가 검색하고 테스트가 표시됩니다.

> [!NOTE]
> 첫 번째로 빌드해야 하는 TypeScript에 애플리케이션이 작성되는 경우 Test Runner는 테스트 루트의 JavaScript 파일만 열거합니다.
