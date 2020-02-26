---
title: '7단계: 양식에 대화 상자 구성 요소 추가'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9697bf6cf84c2a74daac2017b4f63d52a7019b6
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579284"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7단계: 양식에 대화 상자 구성 요소 추가

이 단계에서, 그림 파일을 열고 배경색을 선택할 수 있도록 앱을 설정하려면 <xref:System.Windows.Forms.OpenFileDialog> 구성 요소 및 <xref:System.Windows.Forms.ColorDialog> 구성 요소를 양식에 추가합니다.

구성 요소는 몇 가지 점에서 컨트롤과 비슷합니다. **도구 상자**를 사용하여 구성 요소를 폼에 추가하고 **속성** 창을 사용하여 구성 요소의 속성을 설정합니다. 그러나 컨트롤과 달리 구성 요소를 폼에 추가할 때는 실제로 폼에 표시되는 항목이 추가되지 않습니다. 대신 코드를 사용하여 트리거할 수 있는 특정 동작이 제공됩니다. 예를 들어 **파일 열기** 대화 상자를 여는 것은 바로 구성 요소입니다.

## <a name="to-add-dialog-components-to-your-form"></a>폼에 대화 상자 구성 요소를 추가하려면

1. **Windows Forms 디자이너**(**Form1.cs[디자인]** )을 선택하고 **도구 상자**에서 **대화 상자** 그룹을 엽니다.

    > [!NOTE]
    > **도구 상자**의 **대화 상자** 그룹에는 파일을 열거나 닫고, 폴더를 찾아보고, 글꼴과 색을 선택하는 데 사용할 수 있는 많은 유용한 대화 상자를 여는 구성 요소가 있습니다. 이 프로젝트에서 다음과 같은 두 개의 대화 상자 구성 요소를 사용합니다. OpenFileDialog 및 ColorDialog

1. **openFileDialog1**이라는 구성 요소를 폼에 추가하려면 **OpenFileDialog**를 두 번 클릭합니다. **colorDialog1**이라는 구성 요소를 폼에 추가하려면 **도구 상자**에서 **ColorDialog**를 두 번 클릭합니다. 다음 자습서 단계에서는 이 구성 요소가 사용됩니다. **Windows Forms 디자이너**의 맨 아래(**사진 뷰어** 양식 바로 아래)에서 다음 이미지와 같이 두 대화 상자 구성 요소 각각에 대한 아이콘이 포함된 영역을 볼 수 있습니다.

     ![대화 상자 구성 요소](../ide/media/express_dialogsadded.png)<br>***대화 상자*** *구성 요소*

1. **Windows Forms 디자이너** 아래쪽의 이 영역에서 **openFileDialog1** 아이콘을 선택합니다. 다음 두 가지 속성을 설정합니다.

    - 다음과 같이 **필터** 속성을 설정합니다(복사하여 붙여 넣을 수 있음).

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **제목** 속성을 다음으로 설정합니다. **그림 파일 선택**

         **필터** 속성 설정은 **그림 선택** 파일 대화 상자에 표시되는 파일 형식을 지정합니다.

    > [!TIP]
    > 다른 애플리케이션에서 **파일 열기** 대화 상자의 예제를 보려면 **메모장**이나 **그림판**을 열고 메뉴 모음에서 **파일** > **열기**를 선택합니다. 파일 이름 옆에 파일 형식을 선택할 수 있는 드롭다운 목록이 있는지 확인합니다. <br/><br/>**OpenFileDialog** 구성 요소의 **필터** 속성을 사용하여 앱에서 이러한 값을 설정했습니다. 또한 **속성** 창에서 굵게 표시된 **제목** 및 **필터** 속성도 살펴봅니다. IDE에서는 굵은 글꼴을 사용하여 기본값에서 변경된 속성을 표시합니다.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[8단계: 그림 표시 단추 이벤트 처리기를 위한 코드 작성](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** 을 참조하세요.

* 이전 자습서 단계로 돌아가려면 [6단계: 단추 컨트롤 이름 지정](../ide/step-6-name-your-button-controls.md)을 참조하세요.

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
