---
title: Node.js REPL 사용
description: Visual Studio는 Node.js 런타임과의 상호 작용 지원을 제공합니다.
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8b2bbbdf478f27f936d4897f2ff773baa4cca1d6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285006"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Node.js 대화형 창 사용

Visual Studio용 Node.js 도구에는 설치된 Node.js 런타임에 대한 대화형 창이 포함되어 있습니다. 이 창에서 JavaScript 코드를 입력하고 결과를 즉시 확인할 수 있을 뿐만 아니라 npm 명령을 실행하여 현재 프로젝트와 상호 작용할 수 있습니다. 대화형 창은 REPL(**R**ead/**E**valuate/**P**rint **L**oop)로도 알려져 있습니다.

## <a name="open-the-interactive-window"></a>대화형 창 열기

솔루션 탐색기에서 Node.js 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **Node.js 대화형 창 열기**를 선택하여 대화형 창을 열 수 있습니다.

![프로젝트 컨텍스트 메뉴의 Node.js 대화형 창](../javascript/media/interactivewindow-open-from-project.png)

Node.js 대화형 창을 여는 기본 바로 가기 키는 **[CTRL] + K, N**입니다. 또는 **보기** > **Windows** > **Node.js 대화형 창**을 선택하여 도구 모음에서 창을 열 수 있습니다.

## <a name="use-the-repl"></a>REPL 사용

일단 열리면 명령을 입력할 수 있습니다.

![Node.js 대화형 창](../javascript/media/interactivewindow.png)

대화형 창에는 몇 가지 기본 제공 명령이 있습니다. 이 명령은 선언하는 모든 JavaScript 함수와 구분하기 위해 점 접두사로 시작합니다. 다음 명령이 지원됩니다.

**.cls, .clear** 편집기 창의 내용을 지워서 기록 및 실행 컨텍스트를 그대로 유지합니다.

**.help** 지정된 명령 또는 사용 가능한 모든 명령과 키 바인딩에 대한 도움말을 표시합니다(지정되지 않은 경우).

**.info** 현재 사용되는 Node.js 실행 파일에 대한 정보를 표시합니다.

**.npm** npm 명령을 실행합니다. 솔루션에 프로젝트가 둘 이상 포함된 경우 `.npm [projectname] <npm arguments>`를 사용하여 대상 프로젝트를 지정합니다.

**.reset** 실행 환경을 초기 상태로 다시 설정하고 기록을 보관합니다.

**.save** 현재 REPL 세션을 파일에 저장합니다.