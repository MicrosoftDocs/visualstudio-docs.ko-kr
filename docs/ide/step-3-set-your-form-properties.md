---
title: '3단계: 양식 속성 설정'
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579860"
---
# <a name="step-3-set-your-form-properties"></a>3단계: 양식 속성 설정

이제 **속성** 창을 사용하여 폼의 모양을 변경합니다.

## <a name="how-to-set-your-form-properties"></a>양식 속성을 설정하는 방법

1. **Windows Forms 디자이너**가 열려 있는지 확인합니다. Visual Studio IDE(통합 개발 환경)에서 **Form1.cs[디자인]** 탭(또는 Visual Basic의 **Form1.vb[디자인]** 탭)을 선택합니다.

1. **Form1** 폼 내부의 아무 곳이나 선택하여 해당 폼을 선택합니다. **속성** 창에 선택한 폼의 속성이 표시됩니다. 폼에는 다양한 속성이 있습니다. 예를 들어 전경색, 배경색, 폼의 맨 위에 표시되는 제목 텍스트 및 기타 속성을 설정할 수 있습니다.

   > [!NOTE]
   > **속성** 창이 나타나지 않으면 도구 모음에서 사각형 **디버깅 중지** 단추를 선택하여 앱을 중지하거나 창을 닫습니다. 앱이 중지되었는데도 **속성** 창이 나타나지 않는 경우 메뉴 모음에서 **보기** > **속성 창**을 차례로 선택합니다.

1. 폼을 선택한 후 **속성** 창에서 **텍스트** 속성을 찾습니다. 목록을 정렬 방법에 따라 아래로 스크롤해야 할 수도 있습니다. **텍스트**를 선택하고 **사진 뷰어**를 입력한 다음, **Enter** 키를 선택합니다.  이제 양식의 제목 표시줄에 **사진 뷰어**라는 텍스트가 표시되고 **속성** 창이 다음 스크린샷과 같이 표시됩니다.

    ![속성 창](../ide/media/express_edittextproperty.png)<br>
   ***속성*** *창*

   > [!NOTE]
   > 속성은 **항목별** 뷰 또는 **사전순** 뷰로 정렬할 수 있는데, **속성** 창에 있는 단추를 사용하면 이러한 두 뷰 간에 전환할 수 있습니다. 이 자습서에서는 **사전순** 뷰에서 속성을 더 쉽게 찾을 수 있습니다.

1. **Windows Forms 디자이너**로 돌아갑니다. 폼의 오른쪽 아래에 있는 흰색의 작은 사각형인 끌기 핸들을 선택합니다. 끌기 핸들은 다음과 같이 생겼습니다.

    ![끌기 핸들](../ide/media/express_bottomrt_drag.png)<br>
   *끌기 핸들*

    핸들을 끌어 폼의 너비와 높이를 늘립니다.

1. **속성** 창을 살펴보면 **크기** 속성이 변경되었음을 알 수 있습니다. **크기** 속성은 폼의 크기를 조정할 때마다 변경됩니다. 폼의 핸들을 끌어 폼의 크기를 이 프로젝트에 적합한 크기인 약 **550, 350**(정확할 필요는 없음)으로 조정합니다. 또는 **크기** 속성에 값을 직접 입력한 다음, **Enter** 키를 선택할 수도 있습니다.

1. 앱을 다시 실행합니다. 앱을 실행하려면 다음 방법 중 하나를 사용할 수 있습니다.

   - **F5** 키를 선택합니다.

   - 메뉴 모음에서 **디버그** > **디버깅 시작**을 차례로 선택합니다.

   - 도구 모음에서 **디버깅 시작** 단추를 선택하면 다음과 같이 표시됩니다.

      ![디버깅 도구 모음 시작 단추](../ide/media/express_icondebug.png)<br>
     ***디버깅 시작*** *도구 모음 단추*

     이전과 마찬가지로 IDE에 의해 앱이 빌드되고 실행되며 창이 나타납니다.

1. 다음 단계로 이동하기 전에 앱을 중지합니다. 이는 IDE가 앱이 실행 중일 때 앱을 변경하는 것을 허용하지 않기 때문입니다. 앱을 중지하려면 다음 방법 중 하나를 사용할 수 있습니다.

   - 도구 모음에서 **디버깅 중지** 단추를 선택합니다.

   - 메뉴 모음에서 **디버그** > **디버깅 중지**를 차례로 선택합니다.

   - 키보드를 사용하여 **Shift**+**F5**를 누릅니다.

   - **그림 뷰어** 창의 위쪽 모퉁이에 있는 **X** 단추를 선택합니다.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[4단계: TableLayoutPanel 컨트롤을 사용하여 양식 레이아웃](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)** 을 참조하세요.

* 이전 자습서 단계로 돌아가려면 [2단계: 그림 뷰어 앱을 실행합니다](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
