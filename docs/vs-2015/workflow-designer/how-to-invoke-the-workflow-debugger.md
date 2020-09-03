---
title: '방법: 워크플로 디버거 호출 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e702b402d5350641aa01d341106634efe5f6c6c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849264"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>방법: 워크플로 디버거 호출
일반적으로 워크플로 디버깅은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램의 디버깅과 동일합니다. 다음과 같은 방법으로 워크플로 디버거를 시작할 수 있습니다.

- **디버그** 메뉴에서 **프로세스에 연결** 을 선택 하 여 워크플로 인스턴스에 대해 실행 중인 호스트 프로세스를 선택 합니다. 이 절차는 관리 코드의 호스트 프로세스에 연결하는 절차와 동일합니다.

- **F5** 키를 눌러 워크플로 인스턴스 실행을 시작 하거나 중단점이 적중 된 후에도 계속 실행 되도록 합니다.

- 원격 디버깅을 사용합니다. 원격 디버깅 사용에 대 한 자세한 내용은 [방법: 원격 디버깅 사용](https://msdn.microsoft.com/library/febz73k0.aspx)을 참조 하세요.

    > [!NOTE]
    > 워크플로 응용 프로그램에서 x86 아키텍처를 대상으로 하 고 64 비트 운영 체제를 실행 하는 컴퓨터에서 호스트 되는 경우 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 가 원격 컴퓨터에 설치 되지 않았거나 워크플로 응용 프로그램의 대상이 **모든 CPU**로 변경 되지 않으면 원격 디버깅이 작동 하지 않습니다.

### <a name="stepping-through-code"></a>단계별 코드 실행

- 한 **단계씩**코드 실행: **F11**키를 사용 하 여 작업을 한 단계씩 실행 할 수 있습니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다.

- **프로시저 아웃:** **Shift + F11**을 사용 하 여 활동을 프로시저 외부로 수행할 수 있습니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **프로시저 단위**실행: **F10**키를 사용 하 여 활동을 프로시저 단위로 실행 할 수 있습니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. <xref:System.Activities.Statements.Assign> 활동과 같은 비복합 활동을 프로시저 단위로 실행할 경우 디버거는 해당 활동 및 그와 연결된 처리기를 실행하고 다음 활동에서 중단합니다. 실행할 활동이 복합 활동 중 마지막 자식 활동인 경우, 디버거는 활동 실행 후 부모 활동에서 중단합니다.

### <a name="debugging-with-f5"></a>F5 키를 사용한 디버깅

- 워크플로 콘솔 응용 프로그램 프로젝트를 빌드하는 경우에는 **F5** 키를 눌러 응용 프로그램 및 워크플로에 대 한 디버깅을 시작 하면 됩니다. 활동 라이브러리를 자체적으로 빌드하려는 경우 시작 프로젝트인 실행 가능 호스트 애플리케이션이 있어야 합니다. **솔루션 탐색기**에서 시작 프로젝트를 설정 하려면 호스트의 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 **시작 프로젝트로 설정**을 선택 합니다.

## <a name="see-also"></a>관련 항목
 [방법: 워크플로에 중단점 설정](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [워크플로 디자이너 사용 하 여 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
