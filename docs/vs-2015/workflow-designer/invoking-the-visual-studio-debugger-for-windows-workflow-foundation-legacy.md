---
title: Windows Workflow Foundation에 대 한 디버거 호출 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658988"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation 호출(레거시)
이 항목에서는 레거시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 [!INCLUDE[wf](../includes/wf-md.md)] 디버거를 사용하여 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 일반적으로 레거시 워크플로를 디버깅하는 과정은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램을 디버깅하는 과정과 같습니다. 다음 방법으로 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation을 시작할 수 있습니다.

- **디버그** 메뉴에서 **프로세스에 연결** 을 선택 하 여 사용 가능한 프로세스에서 실행 중인 워크플로 인스턴스를 선택 합니다.

- **F5** 키를 눌러 워크플로 인스턴스 실행을 시작 하거나 중단점이 적중 된 후에도 계속 실행 되도록 합니다.

## <a name="stepping-through-code"></a>단계별 코드 실행
 디버거는 가장 일반적인 디버깅 절차 중 하나인, 한 번에 한 줄씩 코드를 실행하는 단계별 실행을 지원합니다. 단계별 코드 실행 명령에는 세 가지가 있습니다.

- 한 **단계씩**코드 실행: **F11**키를 사용 하 여 작업을 한 단계씩 실행 할 수 있습니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다. **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**또는 **ReplicatorActivity**작업에 대해 디자이너에서 코드 처리기를 한 단계씩 실행할 수 없습니다. 이러한 활동과 연결된 처리기를 디버깅하려면 코드에 명시적인 중단점을 넣어야 합니다.

- **프로시저 아웃**: **Shift + F11**을 사용 하 여 활동을 프로시저에서 수행할 수 있습니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **프로시저 단위**실행: **F10**키를 사용 하 여 활동을 프로시저 단위로 실행 할 수 있습니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. **CodeActivity** 활동과 같은 비 복합를 프로시저 단위로 실행 하는 경우 디버거는 활동 및 관련 된 처리기를 실행 하 고 다음 활동에서 중단 합니다. 실행되는 활동이 복합 활동 중 마지막 자식 활동인 경우, 실행 후에 디버거는 부모 활동에서 중단합니다.

## <a name="attaching-to-a-process"></a>프로세스에 연결
 프로세스에 연결 하 여 워크플로를 디버깅 하려면 **프로세스에 연결** 대화 상자의 **사용 가능한 프로세스** 목록 상자에서 사용 가능한 프로세스를 선택 합니다. **자동: 워크플로 코드가** **연결 대상** 텍스트 상자에 표시 되지 않는 경우 **선택**을 클릭 합니다. **코드 형식 선택** 대화 상자에서 **다음 코드 형식 디버깅** 을 클릭 하 고 **워크플로**를 선택 합니다. 그런 다음 **확인** 을 클릭 하 고 **연결**을 클릭 합니다.

## <a name="debugging-with-f5"></a>F5 키를 사용한 디버깅
 워크플로 호스트 응용 프로그램과 워크플로 DLL이 다른 Visual Studio 프로젝트에 있는 경우 (예: 워크플로 활동 라이브러리를 사용 하는 경우) **F5 키**를 사용 하 여 워크플로를 디버깅 하려면 워크플로 dll 프로젝트를 visual studio 솔루션 시작 프로젝트로 설정 해야 합니다. 또한 워크플로 DLL 프로젝트의 **시작 외부 프로그램** 속성에서 호스트 응용 프로그램에 대 한 경로를 설정 해야 합니다.

 솔루션 탐색기에서 시작 프로젝트를 설정 하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 선택 합니다. **시작 외부 프로그램** 속성에서 호스트에 대 한 경로를 설정 하려면 솔루션 탐색기에서 워크플로 프로젝트의 **속성** 노드를 두 번 클릭 하 고 **디버그** 탭을 선택 합니다. **시작 작업**에서 **시작 외부 프로그램** 을 선택 하 고 디버그 하려는 워크플로를 호스트 하는 .exe 파일의 경로를 입력 합니다.

 호스트 애플리케이션이 시작 프로젝트로 설정되는 경우 Visual Studio 디버거만 디버깅을 위해 호출됩니다. [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation은 호출되지 않습니다. Visual Studio 디버거가 사용되는 경우 C# 또는 Visual Basic 코드 중단점만 적중됩니다. 워크플로 디자이너에 설정된 중단점은 적중되지 않습니다. 예를 들어 디자이너에서 <xref:System.Workflow.Activities.ParallelActivity> 활동에 대해 설정한 중단점은 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation이 사용되는 경우에 적중되지만 Visual Studio 디버거 사용 시에는 적중되지 않습니다.

## <a name="see-also"></a>관련 항목
 [방법: 워크플로에 중단점 설정 (레거시)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)