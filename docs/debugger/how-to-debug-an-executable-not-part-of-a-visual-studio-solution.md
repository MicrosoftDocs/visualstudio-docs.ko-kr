---
title: Visual Studio 솔루션의 일부가 아닌 앱 디버그
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557905"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio 솔루션 (C++, C#, Visual Basic F#)의 일부가 아닌 앱 디버그

Visual Studio 솔루션의 일부가 아닌 앱 ( *.exe* 파일)을 디버그할 수 있습니다. [열려 있는 폴더](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 프로젝트 이거나 사용자 또는 다른 사용자가 Visual Studio 외부에서 앱을 만들었거나 다른 위치에서 앱을 만든 것일 수 있습니다.

- Visual Studio에서 프로젝트 또는 솔루션 파일을 포함 하지 않는 열려 있는 폴더 프로젝트의 경우 [코드 실행 및 디버그](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) 를 참조 하거나,의 경우 C++에는 [시작 및 json을 사용 하 여 디버깅 매개 변수를 구성 합니다.](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson)

- Visual Studio에 없는 응용 프로그램의 경우 디버깅 하는 일반적인 방법은 visual studio 외부에서 응용 프로그램을 시작한 다음 Visual Studio 디버거에서 **프로세스에 연결** 을 사용 하 여 연결 하는 것입니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조 하세요.

   앱에 연결 하려면 몇 초 정도 걸리는 수동 단계가 필요 합니다. 이러한 지연 때문에 연결 하는 것은 시작 문제나 사용자 입력을 기다리지 않고 신속 하 게 완료 되는 앱을 디버그 하는 데 도움이 되지 않습니다.

   이러한 경우 앱에 대 한 Visual Studio EXE 프로젝트를 만들거나 기존 C#, Visual Basic 또는 C++ 솔루션으로 가져올 수 있습니다. 모든 프로그래밍 언어가 EXE 프로젝트를 지원하는 것은 아닙니다.

>[!IMPORTANT]
>앱에 연결 하거나 Visual Studio 솔루션에 추가 하 든 관계 없이 Visual Studio에서 빌드되지 않은 앱에 대 한 디버깅 기능이 제한 됩니다.
>
>소스 코드를 사용 하는 경우에는 코드를 Visual Studio 프로젝트로 가져오는 것이 가장 좋습니다. 그런 다음 응용 프로그램의 디버그 빌드를 실행 합니다.
>
>소스 코드가 없고 앱에 호환 되는 형식의 [디버그 정보가](../debugger/how-to-set-debug-and-release-configurations.md) 없는 경우 사용 가능한 디버깅 기능은 매우 적습니다.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>기존 앱에 대 한 새 EXE 프로젝트를 만들려면

1. Visual Studio에서 **파일** > 선택 하 **여** > **프로젝트**를 엽니다.

1. **프로젝트 열기** 대화 상자에서 **파일 이름**옆의 드롭다운 목록에서 **모든 프로젝트 파일**(아직 선택 하지 않은 경우)을 선택 합니다.

1. *.Exe* 파일로 이동 하 여 선택 하 고 **열기**를 선택 합니다.

   이 파일은 새로운 임시 Visual Studio 솔루션에 표시 됩니다.

1. **디버그** 메뉴에서 **디버깅 시작**과 같은 실행 명령을 선택 하 여 응용 프로그램 디버깅을 시작 합니다.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>기존 Visual Studio 솔루션으로 앱을 가져오려면

1. Visual Studio C++에서 C#, 또는 Visual Basic 솔루션을 열고 **파일** > 선택 하 여 **기존 프로젝트** > **추가** 합니다.

1. **프로젝트 열기** 대화 상자에서 **파일 이름**옆의 드롭다운 목록에서 **모든 프로젝트 파일**(아직 선택 하지 않은 경우)을 선택 합니다.

1. *.Exe* 파일로 이동 하 여 선택 하 고 **열기**를 선택 합니다.

   이 파일은 현재 솔루션에 새 프로젝트로 표시 됩니다.

1. 새 파일을 선택 하 고 **디버그** 메뉴에서 **디버깅 시작**과 같은 실행 명령을 선택 하 여 응용 프로그램 디버깅을 시작 합니다.

### <a name="see-also"></a>참고 항목
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [디버거 보안](../debugger/debugger-security.md)
- [DBG 파일](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))