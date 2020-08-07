---
title: npm을 사용하여 TypeScript 코드 컴파일 및 빌드
description: Visual Studio에서 TypeScript를 컴파일하고 빌드하는 방법을 알아봅니다.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d7bd89f8e7840db8615c74170bb5cb9998aeb678
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87454621"
---
# <a name="compile-typescript-code-nodejs"></a>TypeScript 코드 컴파일(Node.js)

Visual Studio 설치 관리자에서 기본적으로 제공하는 TypeScript SDK를 사용하거나 npm을 사용하여 프로젝트에 TypeScript 지원을 추가할 수 있습니다. Visual Studio 2019에서 개발된 프로젝트의 경우 다양한 플랫폼과 환경에 대한 이식성을 높이려면 TypeScript npm 패키지를 사용하는 것이 좋습니다.

ASP.NET Core 프로젝트의 경우 [NuGet 패키지](../javascript/compile-typescript-code-nuget.md)를 사용하는 것을 권장합니다.

## <a name="add-typescript-support-using-npm"></a>npm을 사용하여 TypeScript 지원 추가

[TypeScript npm 패키지](https://www.npmjs.com/package/typescript)는 TypeScript 지원을 추가합니다. TypeScript 2.1 이상용 npm 패키지가 프로젝트에 설치되면 해당 버전의 TypeScript 언어 서비스가 편집기에 로드됩니다.

1. [지침에 따라](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json) Node.js 개발 워크로드 및 Node.js 런타임을 설치합니다.

   가장 간단하게 Visual Studio와 통합하려면 Node.js TypeScript 템플릿(예: 빈 Node.js 웹 애플리케이션 템플릿) 중 하나를 사용하여 프로젝트를 만들면 됩니다. 또는 Visual Studio에 포함된 Node.js JavaScript 템플릿을 사용하고 여기에 설명된 지침을 따르거나 [오픈 폴더](../javascript/develop-javascript-code-without-solutions-projects.md) 프로젝트를 사용하세요.

1. 프로젝트에 아직 포함되지 않은 경우 [TypeScript npm 패키지](https://www.npmjs.com/package/typescript)를 설치합니다.

   솔루션 탐색기(오른쪽 창)의 프로젝트 루트에서 *package.json*을 엽니다. 나열된 패키지는 솔루션 탐색기의 npm 노드 아래에 있는 패키지에 해당합니다. 자세한 내용은 [npm 패키지 관리](../javascript/npm-package-management.md)를 참조하세요.

   Node.js 프로젝트의 경우 명령줄 또는 IDE를 사용하여 TypeScript npm 패키지를 설치할 수 있습니다. IDE를 사용하여 설치하려면 솔루션 탐색기에서 npm 노드를 마우스 오른쪽 단추로 클릭하여 **새 npm 패키지 설치**를 선택하고 **TypeScript**를 검색한 다음 패키지를 설치합니다.

   패키지 설치 진행률을 확인하려면 **출력** 창의 **npm** 옵션을 선택합니다. 설치된 패키지는 솔루션 탐색기의 **npm** 노드 아래에 표시됩니다.

1. 프로젝트에 아직 포함되지 않은 경우 프로젝트 루트에 *.tsconfig* 파일을 추가합니다. 파일을 추가하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목**을 선택합니다. **TypeScript JSON 구성 파일**을 선택하고 **추가**를 클릭합니다.

   Visual Studio가 프로젝트 루트에 *tsconfig.json* 파일을 추가합니다. 이 파일을 사용하여 TypeScript 컴파일러에 대한 [옵션을 구성](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)할 수 있습니다.

1. *tsconfig.json*을 열고 업데이트해 원하는 컴파일러 옵션을 설정합니다.

   다음은 간단한 *tsconfig.json* 파일 예제입니다.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   이 예제에 대한 설명:
   - 포함은 TypeScript(*.ts) 파일을 찾을 수 있는 위치를 컴파일러에 알려줍니다.
   - *outDir* 옵션은 TypeScript 컴파일러에 의해 트랜스파일된 일반 JavaScript 파일의 출력 폴더를 지정합니다.
   - *sourceMap* 옵션은 컴파일러에서 *sourceMap* 파일을 생성할지 여부를 나타냅니다.

   이전 구성은 TypeScript 구성에 대한 기본 사항만 제공합니다. 다른 옵션에 대한 자세한 내용은 [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)을 참조하세요.

## <a name="build-the-application"></a>애플리케이션 빌드

1. TypeScript( *.ts*) 또는 TypeScript JSX( *.tsx*) 파일을 프로젝트에 추가한 다음 TypeScript 코드를 추가합니다. 간단한 TypeScript 예제를 보려면 다음을 사용합니다.

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. *package.json*에서 다음 스크립트를 사용하여 Visual Studio 빌드 및 정리 명령에 대한 지원을 추가합니다.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   webpack과 같은 타사 도구를 사용하여 빌드해야 하는 경우 명령줄 빌드 스크립트를 *package.json* 파일에 추가할 수 있습니다.

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   React에서 webpack을 사용하는 예제 및 webpack 구성 파일의 예제는 [Node.js 및 React를 사용하여 웹앱 만들기](../javascript/tutorial-nodejs-with-react-and-jsx.md)를 참조하세요.

   TypeScript에서 Vue를 사용하는 예제는 [Vue.js 애플리케이션 만들기](/javascript/create-application-with-vuejs)를 참조하세요.

1. 시작 페이지, Node.js 런타임 경로, 애플리케이션 포트, 런타임 인수 같은 옵션을 구성해야 하는 경우 솔루션 탐색기의 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

   >[!NOTE]
   > 타사 도구를 구성하면 Node.js 프로젝트는 **도구** > **옵션** > **프로젝트 및 솔루션** > **웹 패키지 관리** > **외부 웹 도구**에 구성된 경로를 사용하지 않습니다. 이러한 설정은 다른 프로젝트 형식에 사용됩니다.

1. **빌드 > 솔루션 빌드**를 선택합니다.

   앱은 실행할 때 자동으로 빌드되지만, 빌드 프로세스 도중 발생하는 작업을 살펴보겠습니다.

   소스 맵을 생성한 경우 *outDir* 옵션에 지정된 폴더를 열고 생성된 *js 파일과 생성된 *js.map 파일을 찾습니다.

   소스 맵 파일은 [디버깅](../javascript/debug-nodejs.md)에 필요합니다.

## <a name="automate-build-tasks"></a>빌드 작업 자동화

Visual Studio에서 작업 실행기 탐색기를 사용하여 npm 및 webpack 같은 타사 도구에 대한 작업을 자동화할 수 있습니다.

- [npm 작업 실행기](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) - *package.json*에 정의된 npm 스크립트에 대한 지원을 추가합니다. Yarn을 지원합니다.
- [webpack 작업 실행기](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) - webpack에 대한 지원을 추가합니다.