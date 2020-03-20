---
title: '11단계: 사진 뷰어 앱을 실행하고 다른 기능 사용해 보기'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579892"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>11단계: 사진 뷰어 앱을 실행하고 다른 기능 사용해 보기

사진 뷰어 앱이 완성되어 실행할 준비가 되었습니다. 앱을 실행하고 <xref:System.Windows.Forms.PictureBox>의 배경색을 설정할 수 있습니다. 더 자세한 내용을 알아보려면 양식의 색의 변경하고, 단추와 확인란을 사용자 지정하고, 양식의 속성을 변경하여 애플리케이션을 향상합니다.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>앱을 실행하고 배경색을 설정하는 방법

1. **F5** 키를 선택하거나 메뉴 모음에서 **디버그** > **디버깅 시작**을 선택합니다.

1. 그림을 열기 전에 **배경색 설정** 단추를 선택합니다. **색** 대화 상자가 열립니다.

     ![색 대화 상자](../ide/media/express_colordialog.png)<br/>
***색*** 대화 상자 

1. PictureBox 배경색으로 설정할 색을 선택합니다. `backgroundButton_Click()`(또는 `BackgroundButton_Click()`) 메서드가 어떤 식으로 작동하는지 자세히 살펴봅니다.

    > [!NOTE]
    > **파일 열기** 대화 상자에 URL을 붙여넣어 인터넷에서 그림을 로드할 수 있습니다. 배경색이 보이도록 배경이 투명한 이미지를 찾아 봅니다.

1. **그림 지우기** 단추를 선택하여 그림을 지웁니다. 그런 다음 **닫기** 단추를 선택하여 앱을 종료합니다.

## <a name="try-other-features"></a>기타 기능 사용

* **BackColor** 속성을 사용하여 폼과 단추의 색을 변경합니다.

* **Font** 및 **ForeColor** 속성을 사용하여 단추와 확인란을 사용자 지정합니다.

* 폼의 **FormBorderStyle** 및 **ControlBox** 속성을 변경합니다.

* 폼의 **AcceptButton** 및 **CancelButton** 속성을 사용하여 사용자가 **Enter** 키나 **Esc** 키를 선택하면 단추가 자동으로 선택되도록 만듭니다. 사용자가 **Enter** 키를 선택하면 **파일 열기** 대화 상자가 열리고 **Esc** 키를 선택하면 이 대화 상자가 닫히도록 앱을 설정합니다.

## <a name="next-steps"></a>다음 단계

자세히 알아보려면 계속 다음 자습서를 사용하세요.

> [!div class="nextstepaction"]
> [자습서 2: 시간이 지정된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md)

이전 자습서 단계로 돌아가려면 [10단계: 추가 단추 및 확인란에 대한 코드 작성](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)을 참조하세요.

## <a name="see-also"></a>참조

* [추가 C# 자습서](/visualstudio/get-started/csharp/)
* [추가 Visual Basic 자습서](/visualstudio/get-started/visual-basic/)
* [C++ 자습서](/cpp/get-started/tutorial-console-cpp)
