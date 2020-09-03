---
title: Workflow Designer로 워크플로 디버깅
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8de1ff9875d175c956a45b87d459d0943e783c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597063"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>워크플로 디자이너를 사용 하 여 워크플로 디버그

**워크플로 디자이너** 는 워크플로 및 사용자 지정 작업을 디버깅 하는 기능을 제공 합니다. 프로세스 및 동작은 기본 Visual Studio 디버거의 프로세스와 유사 합니다.

## <a name="invoke-the-workflow-debugger"></a>워크플로 디버거 호출

일반적으로 워크플로 디버깅은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램의 디버깅과 동일합니다. 다음과 같은 방법으로 워크플로 디버거를 시작할 수 있습니다.

- **디버그** 메뉴에서 **프로세스에 연결** 을 선택 하 여 워크플로 인스턴스에 대해 실행 중인 호스트 프로세스를 선택 합니다. 이 절차는 관리 코드의 호스트 프로세스에 연결하는 절차와 동일합니다.

- **F5** 키를 눌러 워크플로 인스턴스 실행을 시작 하거나 중단점이 적중 된 후에도 계속 실행 되도록 합니다.

- 원격 디버깅을 사용합니다. 원격 디버깅 사용에 대 한 자세한 내용은 [방법: 원격 디버깅 사용](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))을 참조 하세요.

   > [!NOTE]
   > 워크플로 응용 프로그램에서 x86 아키텍처를 대상으로 하 고 64 비트 운영 체제를 실행 하는 컴퓨터에서 호스트 되는 경우 원격 컴퓨터에 Visual Studio가 설치 되어 있지 않거나 워크플로 응용 프로그램의 대상이 **모든 CPU**로 변경 되지 않으면 원격 디버깅이 작동 하지 않습니다.

## <a name="step-through-code"></a>단계별 코드 실행

- **들어가기**: **F11**키를 눌러 활동을 한 단계씩 코드 실행 합니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다.

- **프로시저 아웃:** **Shift**F11 키를 눌러 작업을 실행 + **F11**합니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **프로시저 단위**실행: **F10**키를 눌러 활동을 프로시저 단위로 실행 합니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. <xref:System.Activities.Statements.Assign> 활동과 같은 비복합 활동을 프로시저 단위로 실행할 경우 디버거는 해당 활동 및 그와 연결된 처리기를 실행하고 다음 활동에서 중단합니다. 실행할 활동이 복합 활동 중 마지막 자식 활동인 경우, 디버거는 활동 실행 후 부모 활동에서 중단합니다.

## <a name="debug-with-f5"></a>F5 키를 사용 하 여 디버그

워크플로 콘솔 앱을 빌드하는 경우에는 **F5** 키를 눌러 응용 프로그램 및 워크플로에 대 한 디버깅을 시작 하면 됩니다. 자체에서 작업 라이브러리를 빌드하는 경우 실행 파일 호스트 응용 프로그램을 시작 프로젝트로 지정 해야 합니다. **솔루션 탐색기**에서 시작 프로젝트를 설정 하려면 호스트의 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 선택 합니다.
