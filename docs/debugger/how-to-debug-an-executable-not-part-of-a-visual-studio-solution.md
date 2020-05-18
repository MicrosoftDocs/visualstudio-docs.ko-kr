---
title: Visual Studio 솔루션의 일부가 아닌 앱 디버깅
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
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557905"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio 솔루션의 일부가 아닌 앱 디버깅(C++, C#, Visual Basic, F#)

Visual Studio 솔루션의 일부가 아닌 앱( *.exe* 파일)을 디버그해야 할 수 있습니다. [오픈 폴더](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 프로젝트이거나 사용자 또는 다른 사용자가 Visual Studio 외부에서 앱을 만들었거나 다른 위치에서 앱을 가져온 것일 수 있습니다.

- Visual Studio의 오픈 폴더 프로젝트(프로젝트 또는 솔루션 파일이 없음)의 경우 [코드 실행 및 디버그](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) 또는 C++의 경우 [launch.vs.json을 사용하여 디버깅 매개 변수 구성](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson)을 참조하세요.

- Visual Studio에 없는 앱을 디버그하는 일반적인 방법은 Visual Studio 외부에서 앱을 시작한 다음, Visual Studio 디버거에서 **프로세스에 연결**을 사용하여 연결하는 것입니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

   앱에 연결하려면 몇 초 정도 걸리는 수동 단계가 필요합니다. 이러한 지연 때문에 연결은 시작 문제나 사용자 입력을 기다리지 않고 신속하게 완료되는 앱을 디버그하는 데는 도움이 되지 않습니다.

   이러한 경우 앱에 대한 Visual Studio EXE 프로젝트를 만들거나 기존 C#, Visual Basic 또는 C++ 솔루션으로 가져올 수 있습니다. 모든 프로그래밍 언어가 EXE 프로젝트를 지원하는 것은 아닙니다.

>[!IMPORTANT]
>앱에 연결하든 아니면 Visual Studio 솔루션에 추가하든 Visual Studio에서 빌드되지 않은 앱에 대한 디버깅 기능은 제한적입니다.
>
>소스 코드가 있는 경우 코드를 Visual Studio 프로젝트로 가져오는 것이 가장 좋습니다. 그런 다음 앱의 디버그 빌드를 실행합니다.
>
>소스 코드가 없고 앱이 호환 가능한 형식으로 [디버그 정보](../debugger/how-to-set-debug-and-release-configurations.md)를 포함하지 않는 경우 사용 가능한 디버깅 기능은 매우 적습니다.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>기존 앱에 대한 새 EXE 프로젝트를 만들려면

1. Visual Studio에서 **파일** > **열기** > **프로젝트**를 선택합니다.

1. **프로젝트 열기** 대화 상자에서 **파일 이름** 옆의 드롭다운에서 **모든 프로젝트 파일**을 선택합니다(아직 선택하지 않은 경우).

1. *.exe* 파일로 이동하여 선택하고 **열기**를 선택합니다.

   이 파일은 새로운 임시 Visual Studio 솔루션에 표시됩니다.

1. **디버그** 메뉴에서 **디버깅 시작** 같은 실행 명령을 선택하여 앱 디버깅을 시작합니다.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>기존 Visual Studio 솔루션으로 앱을 가져오려면

1. Visual Studio에서 C++, C# 또는 Visual Basic 솔루션이 열린 상태에서 **파일** > **추가** > **기존 프로젝트**를 선택합니다.

1. **프로젝트 열기** 대화 상자에서 **파일 이름** 옆의 드롭다운에서 **모든 프로젝트 파일**을 선택합니다(아직 선택하지 않은 경우).

1. *.exe* 파일로 이동하여 선택하고 **열기**를 선택합니다.

   이 파일은 현재 솔루션에 새 프로젝트로 표시됩니다.

1. 새 파일을 선택하고 **디버그** 메뉴에서 **디버깅 시작** 같은 실행 명령을 선택하여 앱 디버깅을 시작합니다.

### <a name="see-also"></a>참조
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [디버거 보안](../debugger/debugger-security.md)
- [DBG 파일](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))