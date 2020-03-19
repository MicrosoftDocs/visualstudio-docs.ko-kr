---
title: npm 패키지 관리
description: Visual Studio를 통해 Node.js 패키지 관리자(npm)를 사용하여 패키지를 관리할 수 있습니다.
ms.custom: seodec18
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
ms.openlocfilehash: de92c3f1f0d0e29d1ba2dfaf5d536a42e636be2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307222"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Visual Studio에서 npm 패키지 관리

npm을 사용하면 Node.js 애플리케이션에서 사용할 패키지를 설치하고 관리할 수 있습니다. npm에 익숙하지 않고 자세히 알아보려면 [npm 설명서](https://docs.npmjs.com/)로 이동합니다.

Visual Studio를 사용하면 쉽게 npm과 상호 작용하고 UI를 통해 또는 직접 npm 명령을 실행할 수 있습니다. 다음 메서드를 사용할 수 있습니다.
* [솔루션 탐색기에서 패키지 설치](#npmInstallWindow)
* [솔루션 탐색기에서 설치된 패키지 관리](#solutionExplorer)
* [Node.js 대화형 창에서 `.npm` 명령 사용](#interactive)

이러한 기능은 함께 작동하며 프로젝트 시스템 및 프로젝트의 *package.json* 파일과 동기화됩니다.

> [!Important]
> NPM에는 프로젝트 루트의 *node_modules* 폴더 및 *package.json*이 필요합니다. 앱의 폴더 구조가 다른 경우 Visual Studio를 사용하여 npm 패키지를 관리하려면 폴더 구조를 업데이트해야 합니다.

> [!NOTE]
> 기존 NPM 프로젝트의 경우 **기존 Node.js 코드에서** 솔루션 템플릿을 사용합니다.

## <a name="npmInstallWindow"></a> 솔루션 탐색기에서 패키지 설치

Npm 패키지를 설치하는 가장 쉬운 방법은 npm 패키지 설치 창을 통해서 하는 것입니다. 이 창에 액세스하려면 프로젝트에서 **npm** 노드를 마우스 오른쪽 단추로 클릭하고 **새 npm 패키지 설치**를 선택합니다.

![솔루션 탐색기에서 새 npm 패키지 설치](../javascript/media/solution-explorer-install-package.png)

이 창에서 패키지를 검색, 옵션 지정 및 설치할 수 있습니다.

![npm 패키지 검색](../javascript/media/search-package.png)

* **종속성 유형** - **표준**, **개발** 및 **선택적** 패키지 간에 선택합니다. 표준은 패키지가 런타임 종속성임을 지정하지만 개발은 패키지가 개발 중에만 필요함을 지정합니다.
* **package.json에 추가** - 이 옵션은 사용되지 않습니다.
* **선택한 버전** - 설치하려는 패키지의 버전을 선택합니다.
* **기타 npm 인수** - 다른 표준 npm 인수를 지정합니다. 예를 들어 `@~0.8`과 같은 버전 값을 입력하여 버전 목록에서 사용할 수 없는 특정 버전을 설치할 수 있습니다.

출력 창의 npm 탭에서 설치 진행률을 볼 수 있습니다. 다소 시간이 걸릴 수 있습니다.

> [!TIP]
> 원하는 범위로 검색 쿼리를 추가하여 범위가 지정된 패키지를 검색할 수 있습니다(예: `@types/mocha`를 입력하여 mocha에 대한 TypeScript 정의 파일을 찾음). 또한 TypeScript에 대한 형식 정의를 설치할 때 npm 인수 필드에 `@ts2.6`을 추가하여 대상이 되는 TypeScript 버전을 지정할 수 있습니다.

## <a name="solutionExplorer"></a>솔루션 탐색기에서 설치된 패키지 관리

npm 패키지는 솔루션 탐색기에 표시됩니다. **npm** 노드 아래에 있는 항목은 *package.json* 파일의 종속성을 모방합니다.

![npm 패키지 검색](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>패키지 상태
* ![설치된 패키지](../javascript/media/installed-npm.png) - package.json에 설치 및 나열
* ![외부 패키지](../javascript/media/extraneous-npm.png) - 설치되었지만 package.json에 명시적으로 나열되지 않음
* ![누락된 패키지](../javascript/media/missing-npm.png) - 설치되지 않았지만 package.json에 나열됨

패키지 노드 또는 **npm** 노드를 마우스 오른쪽 단추로 클릭하여 다음 작업 중 하나를 수행합니다.
* **package.json**에 나열된 *누락된 패키지 설치*
* 최신 버전으로 **패키지 업데이트**
* **package.json**에서 *패키지 제거* 및 제거

## <a name="interactive"></a>Node.js 대화형 창에서 명령 사용

Node.js 대화형 창에서 `.npm` 명령을 사용하여 npm 명령을 실행할 수도 있습니다. 창을 열려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Node.js 대화형 창 열기**를 선택합니다.

창에서 다음과 같은 명령을 사용하여 패키지를 설치할 수 있습니다.

`.npm install azure@4.2.3`

 > [!Tip]
 > 기본적으로 npm은 프로젝트의 홈 디렉터리에서 실행됩니다. 솔루션에 여러 프로젝트가 있는 경우 프로젝트의 이름 또는 경로를 대괄호로 지정합니다.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 프로젝트에 package.json 파일이 없는 경우 `.npm init -y`를 사용하여 기본 항목이 있는 새 package.json 파일을 만듭니다.
