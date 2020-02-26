---
title: '2단계: 그림 뷰어 앱 실행'
ms.date: 09/06/2019
ms.assetid: 9a8fe90e-c97b-4e98-b6c8-0c6b3962c49d
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8204f2a32a1bb29203c75af55aa383141f17853f
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579410"
---
# <a name="step-2-run-your-picture-viewer-app"></a>2단계: 그림 뷰어 앱 실행

Windows Forms 앱 프로젝트를 만들 때 실제로 실행하는 프로그램을 빌드합니다. 이 자습서에서 그림 뷰어 앱은 아직 많은 작업을 수행하지 않고&mdash; 지금은 제목 표시줄에 **Form1**이 표시된 빈 창을 표시합니다.

앱을 실행하는 방법은 다음과 같습니다. 

1. 다음 방법 중 하나를 선택합니다.

    - **F5** 키를 선택합니다.

    - 메뉴 모음에서 **디버그** > **디버깅 시작**을 차례로 선택합니다.

    - 도구 모음에서 **디버깅 시작** 단추를 선택하면 다음과 같이 표시됩니다.

      ![디버깅 도구 모음 시작 단추](../ide/media/express_icondebug.png)<br>
      ***디버깅 시작*** *도구 모음 단추*

1. Visual Studio에서 앱이 실행되고 **Form1** 창이 표시됩니다. 다음 스크린샷은 방금 빌드한 앱을 보여 줍니다. 앱이 실행 중이며, 더 많은 기능이 추가될 예정입니다.

     ![Windows Forms 앱 실행 중](../ide/media/express_firstrun.png)<br>
***Windows Forms 앱***, *실행 중*

1. Visual Studio IDE(통합 개발 환경)로 돌아가서 새 도구 모음을 살펴봅니다. 애플리케이션을 실행하면 추가 단추가 도구 모음에 나타납니다. 이러한 단추를 사용하면 앱 중지 및 시작과 같은 작업을 수행할 수 있으며 발생할 수 있는 모든 오류(버그)를 추적할 수 있습니다. 이 예제에서는 앱을 시작하고 중지하는 데에만 이를 사용하도록 합니다.

     ![디버깅 도구 모음](../ide/media/express_debugtoolbar.png)<br>
***디버깅*** *도구 모음*

1. 다음 메서드 중 하나를 사용해서 앱을 중지합니다.

    - 도구 모음에서 **디버깅 중지** 단추를 선택합니다.

    - 메뉴 모음에서 **디버그** > **디버깅 중지**를 차례로 선택합니다.

    - 키보드를 사용하여 **Shift**+**F5**를 누릅니다.

    - **Form1** 창의 위쪽 모퉁이에 있는 **X** 단추를 선택합니다.

    > [!NOTE]
    > IDE 안에서 앱을 실행할 때는 주로 애플리케이션에서 버그(오류)를 찾고 수정하는 작업을 수행하기 때문에 IDE 안에서 프로그램을 실행하는 것을 디버깅이라고 합니다. 이 앱은 크기가 작고 아직 아무것도 실제로 수행하지는 않지만 마찬가지로 실제 프로그램입니다. 다른 프로그램도 동일한 절차에 따라 실행하고 디버깅합니다. 디버깅에 대한 자세한 내용은 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

* 다음 자습서 단계로 이동하려면 **[3단계: 양식 속성 설정](../ide/step-3-set-your-form-properties.md)** 을 참조하세요.

* 이전 자습서 단계로 돌아가려면 [1단계: Windows Forms 앱 프로젝트 만들기](../ide/step-1-create-a-windows-forms-application-project.md)를 참조하세요.

## <a name="see-also"></a>참조

* [자습서 2: 시간이 지정된 수학 퀴즈 만들기](tutorial-2-create-a-timed-math-quiz.md)
* [자습서 3: 맞추기 게임 만들기](tutorial-3-create-a-matching-game.md)
