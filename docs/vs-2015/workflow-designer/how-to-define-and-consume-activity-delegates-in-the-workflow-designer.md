---
title: '방법: 워크플로 디자이너에서 작업 대리자 정의 및 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603861"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용
[!INCLUDE[net_v45](../includes/net-v45-md.md)] 에는 활동에 대 한 새로운 기본 디자이너가 포함 되어 있습니다 <xref:System.Activities.Statements.InvokeDelegate> . 이 디자이너는 <xref:System.Activities.ActivityDelegate> 또는 <xref:System.Activities.ActivityAction> 같은 <xref:System.Activities.ActivityFunc%601>에서 파생되는 작업에 대리자를 할당하는 데 사용할 수 있습니다.

### <a name="define-an-activity-delegate"></a>작업 대리자 정의

1. 에서 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **파일**, **새로 만들기**, **프로젝트**를 선택 합니다. 왼쪽에서 **워크플로** 노드를 선택 하 고 오른쪽에 있는 **워크플로 콘솔 응용 프로그램** 템플릿을 선택 합니다. 원하는 경우 프로젝트 이름을로, **확인**을 클릭 합니다.

2. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **새 항목**...을 차례로 선택 합니다. 왼쪽에서 **워크플로** 노드를 선택 하 고 오른쪽에 있는 **활동** 템플릿을 선택 합니다. 새 활동의 이름을 **Myforeach. .xaml** 으로 만들고 **확인을**클릭 합니다. Workflow Designer에서 활동이 열립니다.

3. Workflow designer에서 **인수** 탭을 클릭 합니다.

4. **인수 만들기**를 클릭합니다. 새 인수 **항목**의 이름을로 합니다.

5. **인수 형식** 열에서 **배열 [T]** 를 선택 합니다.

6. 유형 브라우저에서  **개체**를 선택 합니다. **확인**을 클릭합니다.

7. **인수 만들기** 를 다시 클릭 합니다. 새 인수 **본문**의 이름을로 합니다. 새 인수에 대 한 **방향** 열에서 **속성**을 선택 합니다.

8. 인수 형식 열에서 **형식 찾아보기** ...를 선택 합니다.

9. 유형 브라우저의 **유형 이름** 필드에 **activityaction** 을 입력 합니다. 트리 뷰에서 **Activityaction \<T> ** 을 선택 합니다. 인수에 **Activityaction \<Object> ** 유형을 할당 하는 데 나타나는 드롭다운에서 **개체** 를 선택 합니다.

10. 활동을 <xref:System.Activities.Statements.While> 도구 상자의 **제어 흐름** 섹션에서 디자이너 화면으로 끌어 옵니다.

11. <xref:System.Activities.Statements.While>활동을 선택 하 고 **변수** 탭을 선택 합니다.

12. **변수 만들기**를 선택 합니다. 새 변수 **인덱스**의 이름을로 합니다.

13. **변수 형식** 열에서 **Int32**를 선택 합니다. **범위** 는 **While**으로, **기본** 열은 비워 둡니다.

14. 활동의 **Condition** 속성 <xref:System.Activities.Statements.While> 을 **인덱스 < 항목. Length;** 로 설정 합니다.

15. 활동을 <xref:System.Activities.Statements.InvokeDelegate> 도구 상자의 **기본 형식** 섹션에서 활동의 **본문** 으로 끌어 놓습니다 <xref:System.Activities.Statements.While> .

16. 대리자 드롭다운에서 **본문** 을 선택 합니다.

17. 활동에 대 한 **속성** 표에서 ...를 <xref:System.Activities.Statements.InvokeDelegate> 클릭 하 **…** 여 단추 **를 클릭** 합니다.

18. 인수 **명명 된 인수의** **값** 열에 **항목 [Index]** 를 입력 합니다. **확인** 을 클릭 하 여 **DelegateArguments** 대화 상자를 닫습니다.

19. <xref:System.Activities.Statements.Assign> 활동을 <xref:System.Activities.Statements.InvokeDelegate> 활동 아래의 가로선으로 끌어 놓습니다. <xref:System.Activities.Statements.Assign>활동이 만들어지고 활동은 <xref:System.Activities.Statements.Sequence> **Myforeach** 활동의 **Body** 섹션에 두 활동을 포함 하도록 자동으로 생성 됩니다. **본문** 섹션에는 단일 활동만 포함할 수 있으므로 시퀀스가 필요 합니다. 새 <xref:System.Activities.Statements.Sequence> 활동을 자동으로 만드는 기능은 [!INCLUDE[net_v45](../includes/net-v45-md.md)]의 새 기능입니다.

20. 활동의 **to** 속성을 <xref:System.Activities.Statements.Assign> **index**로 설정 합니다. **Assign** 활동의 **Value** 속성을 **인덱스 + 1**로 설정 합니다.

    이제 사용자 지정 **Myforeach** 활동은 **항목** 컬렉션을 통해 전달 된 각 값에 대해 임의의 활동을 한 번 호출 하 고 컬렉션의 값을 활동의 입력으로 사용 합니다.

### <a name="use-the-custom-activity-in-a-workflow"></a>워크플로에서 사용자 지정 활동 사용

1. **Ctrl + Shift + B**를 눌러 프로젝트를 빌드합니다.

2. **솔루션 탐색기**의 디자이너에서 **workflow1.vb** 를 엽니다.

3. 도구 상자에서 **Myforeach** 활동을 디자이너 화면으로 끌어 옵니다. 활동은 프로젝트와 같은 이름을 사용하여 도구 상자의 한 섹션에 있게 됩니다.

4. **Myforeach** 활동의 **Items** 속성을 **새 개체 [] {1, "abc"} (** 으)로 설정 합니다.

5. <xref:System.Activities.Statements.WriteLine>도구 상자의 **기본 형식** 섹션에서 **Myforeach** 활동의 **Delegate: Body** 섹션으로 활동을 끌어 옵니다.

6. 활동의 **Text** 속성을 <xref:System.Activities.Statements.WriteLine> **인수 ToString ()** 으로 설정 합니다.

   워크플로가 실행되면 콘솔에 다음이 표시됩니다.

   **1** 
    **abc**