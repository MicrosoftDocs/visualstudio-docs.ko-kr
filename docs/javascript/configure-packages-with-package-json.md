---
title: package.json을 포함하는 npm 패키지 구성
description: package.json을 사용하여 npm 패키지 버전 지정
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 652ff7b0380fc03a3f9c8155a2f8696d9dfee5b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67692366"
---
# <a name="packagejson-configuration"></a>package.json configuration

많은 npm 패키지가 포함된 Node.js 앱을 개발하는 경우 하나 이상의 패키지가 업데이트되면 프로젝트를 빌드할 때 경고 또는 오류가 발생하는 것이 드문 일은 아닙니다. 경우에 따라서는 버전이 결과와 충돌하거나 패키지 버전이 사용되지 않습니다. 여기에 [package.json](https://docs.npmjs.com/files/package.json) 파일을 구성하고 경고 또는 오류가 표시될 때 어떤 상황인지 이해하는 데 도움이 되는 몇 가지 유용한 팁이 나와 있습니다. 이것이 *package.json*에 대한 완벽한 가이드는 아니며 npm 패키지 버전 관리에만 초점을 맞추고 있습니다.

npm 패키지 버전 관리 시스템에는 엄격한 규칙이 있습니다. 버전 형식은 다음과 같습니다.

```
[major].[minor].[patch]
```

5\.2.1 버전의 앱에 패키지가 있다고 가정해 보겠습니다. 주 버전은 5, 부 버전은 2, 패치는 1입니다.

* 주 버전 업데이트에서 패키지에는 이전 버전과 호환되지 않는 새로운 기능 즉, 호환성이 손상되는 변경이 포함됩니다.
* 부 버전 업데이트에서는 새 기능이 패키지에 추가되었으며 이전 패키지 버전과 호환됩니다.
* 패치 업데이트에는 하나 이상의 버그 수정이 포함됩니다. 버그 수정은 항상 이전 버전과 호환됩니다.

일부 npm 패키지 기능에는 종속성이 포함되므로 주목할 가치가 있습니다. 예를 들어 webpack을 포함하는 TypeScript 컴파일러 패키지(ts-loader)의 새 기능을 사용하려면 webpack npm 패키지 및 webpack-cli 패키지도 업데이트해야 합니다.

npm에서는 패키지 버전 관리에 도움이 되도록 *package.json*에서 사용할 수 있는 몇 가지 표기법을 지원합니다. 앱에서 사용하려는 패키지 업데이트 유형을 제어하려면 이러한 표기법을 사용할 수 있습니다.

React를 사용 중이고 **react** 및 **react-dom** npm 패키지를 포함해야 한다고 가정해 보겠습니다. *package.json* 파일에서 여러 방법으로 이를 지정할 수 있습니다. 예를 들어 패키지의 정확한 버전을 사용하도록 다음과 같이 지정할 수 있습니다.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

위 표기법을 사용하면 npm에서 항상 정확하게 지정된 버전(16.4.2)을 가져옵니다.

패치 업데이트(버그 수정)로 업데이트를 제한하는 특수 표기법을 사용할 수 있습니다. 이 예제에서:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

패치된 패키지만 업데이트하도록 물결표 (~) 문자를 사용하여 npm에 알립니다. 그러면 npm이 react 16.4.2를 16.4.3(또는 16.4.4 등)으로 업데이트할 수 있지만 주 버전 또는 부 버전에 대한 업데이트는 허용되지 않습니다. 따라서 16.4.2는 16.5.0으로 업데이트되지 않습니다.

또한 캐럿(^) 기호를 사용하면 해당 npm이 부 버전 번호를 업데이트하도록 지정할 수도 있습니다.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

이 표기법을 사용하여 npm은 react 16.4.2를 16.5.0(또는 16.5.1, 16.6.0 등)으로 업데이트할 수 있지만 주 버전에 대한 업데이트는 허용되지 않습니다. 따라서 16.4.2는 17.0.0으로 업데이트되지 않습니다.

npm이 패키지를 업데이트하는 경우 *package-lock.json* 파일이 생성되며 이 파일에는 중첩된 모든 패키지를 포함하여 앱에서 사용되는 실제 npm 패키지 버전이 나열됩니다. *package.json*에서 앱에 대한 직접 종속성을 제어하는 할 때는 중첩된 종속성(특정 npm 패키지에 필요한 다른 npm 패키지)을 제어하지 않습니다. 사용자는 다른 개발자 및 테스터가 중첩된 패키지를 포함하여 사용자가 사용 중인 정확한 패키지를 사용하는지 확인해야 하는 경우 개발 주기에서 *package-lock.json* 파일을 사용할 수 있습니다. 자세한 내용은 [package-lock.json](https://docs.npmjs.com/files/package-lock.json) npm 설명서를 참조하세요.

Visual Studio에서는 *package-lock.json* 파일이 프로젝트에 추가되지 않지만 프로젝트 폴더에서는 찾을 수 있습니다.
