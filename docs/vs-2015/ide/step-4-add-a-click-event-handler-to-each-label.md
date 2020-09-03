---
title: '4단계: 각 레이블에 클릭 이벤트 처리기 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b78a1757586dfaf6087711eaf1ed6001155a3b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671798"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>4단계: 각 레이블에 클릭 이벤트 처리기 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일치 게임은 다음과 같은 방식으로 진행됩니다.

1. 플레이어가 아이콘이 숨겨져 있는 사각형 중 하나를 선택하면 프로그램에서 아이콘 색을 검은색으로 변경하여 플레이어에게 해당 아이콘을 보여 줍니다.

2. 플레이어가 다른 숨겨진 아이콘을 선택합니다.

3. 아이콘이 일치하면 해당 아이콘이 표시되고 일치하지 않으면 두 아이콘 모두 다시 숨겨집니다.

   프로그램이 이런 방식으로 작동하게 하려면 선택한 레이블의 색을 변경하는 Click 이벤트 처리기를 추가해야 합니다.

### <a name="to-add-a-click-event-handler-to-each-label"></a>각 레이블에 Click 이벤트 처리기를 추가하려면

1. Windows Forms 디자이너에서 폼을 엽니다. 솔루션 탐색기에서 Form1.cs 또는 Form1.vb를 선택합니다. 메뉴 모음에서 **보기**, **디자이너**를 차례로 선택합니다.

2. 첫 번째 레이블 컨트롤을 선택합니다. 그런 다음 Ctrl 키를 누른 상태에서 다른 레이블을 각각 선택합니다. 모든 레이블이 선택되어야 합니다.

3. **속성** 창의 도구 모음에서 **이벤트** 단추를 선택하여 **속성** 창의 **이벤트** 페이지를 표시합니다. 다음 그림과 같이 **Click** 이벤트 위치까지 아래로 스크롤한 후 상자에 **label_Click**을 입력합니다.

     ![Click 이벤트를 표시 하 속성 창](../ide/media/express-labelclick.png "Express_labelClick") Click 이벤트를 표시 하 속성 창

4. Enter 키를 선택합니다. IDE에서 `label_Click()`이라는 Click 이벤트 처리기를 코드에 추가하고 폼의 각 레이블에 후크합니다.

5. 다음과 같이 코드의 나머지 부분을 채워 넣습니다.

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#4)]

    > [!NOTE]
    > 코드를 수동으로 입력하는 대신 `label_Click()` 코드 블록을 복사하여 붙여 넣는 경우에는 기존 `label_Click()` 코드를 대체해야 합니다. 이렇게 하지 않으면 중복된 코드 블록이 남게 됩니다.

    > [!NOTE]
    > `object sender` [자습서 2: 시간이 지정 된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md) 자습서에서 사용 된 것과 동일한 이벤트 처리기의 맨 위를 인식할 수 있습니다. 단일 이벤트 처리기 메서드에 대해 다양한 레이블 컨트롤 Click 이벤트를 후크했으므로 사용자가 선택하는 레이블에 관계없이 동일한 메서드가 호출됩니다. 이벤트 처리기 메서드에서 어떤 레이블이 선택되었는지 알아야 하므로 레이블 컨트롤을 식별하기 위한 **sender**라는 이름을 사용합니다. 메서드의 첫 번째 줄을 보면 단순히 일반 개체가 아니라 레이블 컨트롤임을 명시적으로 나타내고 **clickedLabel**이라는 이름을 사용하여 레이블의 속성 및 메서드에 액세스한다는 것을 알 수 있습니다.

     이 메서드는 먼저 **clickedLabel**이 개체에서 레이블 컨트롤로 변환(캐스팅)되었는지 여부를 확인합니다. 성공적으로 변환되지 않은 경우에는 `null`(C#) 또는 `Nothing`(Visual Basic) 값을 포함하고 메서드의 나머지 코드를 실행하지 않습니다. 다음으로 메서드는 레이블의 **ForeColor** 속성을 사용하여 선택된 레이블의 텍스트 색을 확인합니다. 레이블의 텍스트 색이 검정이면 아이콘이 이미 선택되었음을 의미하며 메서드는 완료됩니다. (문이 수행 하는 작업은 `return` 프로그램에 메서드 실행을 중지 하도록 지시 합니다.) 그렇지 않으면 아이콘이 선택 되지 않은 것 이므로 프로그램에서 레이블의 텍스트 색을 검정으로 변경 합니다.

6. 메뉴 표시줄에서 **파일**, **모두 저장**을 선택하여 진행 상황을 저장한 다음, 메뉴 모음에서 **디버그**, **디버깅 시작**을 선택하여 프로그램을 실행합니다. 파란색 배경의 빈 폼이 나타납니다. 이때 폼의 아무 셀이나 선택하면 아이콘 중 하나를 볼 수 있어야 합니다. 폼에서 다른 위치를 계속 선택해 보십시오. 아이콘을 선택하면 폼에 나타납니다.

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동 하려면 [5 단계: 레이블 참조 추가](../ide/step-5-add-label-references.md)를 참조 하세요.

- 이전 자습서 단계로 돌아가려면 [3 단계: 각 레이블에 임의 아이콘 할당](../ide/step-3-assign-a-random-icon-to-each-label.md)을 참조 하세요.
