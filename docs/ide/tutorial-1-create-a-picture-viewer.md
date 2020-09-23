---
title: '자습서 1: 사진 뷰어 만들기'
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44fe22aa1d4549d1daba4324349160afcd3133ba
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811216"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>자습서 1: 사진 뷰어 만들기

이 자습서에서는 파일에서 그림을 로드하여 창에 표시하는 앱을 빌드합니다. 또한 **Windows Forms 디자이너**를 사용하여 단추와 그림 상자 같은 컨트롤을 양식에 끌어오고, 해당 속성을 설정하고, 컨테이너를 사용하여 양식의 크기를 자연스럽게 조정하는 방법을 알아봅니다. 코드 작성을 시작합니다.

> [!NOTE]
> 이 자습서는 C#과 Visual Basic을 모두 다루고 있으므로 사용 중인 프로그래밍 언어와 관련된 정보를 참조하세요.

이 자습서에서는 다음 작업을 단계별로 안내합니다.

* 새 프로젝트를 만듭니다.

* 애플리케이션을 테스트(디버깅)합니다.

* 확인란과 단추 같은 기본 컨트롤을 폼에 추가합니다.

* 레이아웃을 사용하여 양식에 컨트롤을 배치합니다.

* 폼에 **파일 열기** 및 **색** 대화 상자를 추가합니다.

* IntelliSense 및 코드 조각을 사용하여 코드를 작성합니다.

* 이벤트 처리기 메서드를 작성합니다.

완료되면 앱은 다음 이미지와 유사하게 표시됩니다.

![이 자습서에서 만드는 그림 뷰어 앱](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>자습서 링크

|제목|설명|
|-----------|-----------------|
|[1단계: Windows Forms 앱 프로젝트 만들기](../ide/step-1-create-a-windows-forms-application-project.md)|Windows Forms 앱 프로젝트 만들기로 시작합니다.|
|[2단계: 그림 뷰어 앱 실행](../ide/step-2-run-your-program.md)|이전 단계에서 만든 Windows Forms 앱 프로젝트를 실행합니다.|
|[3단계: 양식 속성 설정](../ide/step-3-set-your-form-properties.md)|**속성** 창을 사용하여 폼의 모양을 변경합니다.|
|[4단계: TableLayoutPanel 컨트롤을 사용하여 양식 레이아웃](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|폼에 `TableLayoutPanel` 컨트롤을 추가합니다.|
|[5단계: 양식에 컨트롤 추가](../ide/step-5-add-controls-to-your-form.md)|`PictureBox` 컨트롤 및 `CheckBox` 컨트롤과 같은 컨트롤을 폼에 추가합니다. 폼에 단추를 추가합니다.|
|[6단계: 단추 컨트롤 이름 지정](../ide/step-6-name-your-button-controls.md)|단추의 이름을 더 의미 있는 이름으로 변경합니다.|
|[7단계: 양식에 대화 상자 구성 요소 추가](../ide/step-7-add-dialog-components-to-your-form.md)|`OpenFileDialog` 구성 요소 및 `ColorDialog` 구성 요소를 폼에 추가합니다.|
|[8단계: 그림 표시 단추 이벤트 처리기를 위한 코드 작성](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense 도구를 사용하여 코드를 작성합니다.|
|[9단계: 코드 검토, 주석 처리 및 테스트](../ide/step-9-review-comment-and-test-your-code.md)|코드를 검토하고 테스트합니다. 필요한 경우 주석을 추가합니다.|
|[10단계: 추가 단추 및 확인란에 대한 코드 작성](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense를 사용하여 다른 단추와 확인란이 작동하도록 코드를 작성합니다.|
|[11단계: 앱을 실행하고 다른 기능을 사용해 보세요.](../ide/step-11-run-your-program-and-try-other-features.md)|앱을 실행하고 배경색을 설정합니다. 색, 글꼴 및 테두리 변경과 같은 다른 기능을 사용해 봅니다.|

또한 유용한 비디오 학습 자료가 무료로 제공됩니다. C# 프로그래밍에 대한 자세한 내용은 [C# 기초: 완전 초보자를 위한 개발](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)을 참조하세요. Visual Basic의 프로그래밍에 대한 자세한 내용은 [Visual Basic 기초: 완전 초보자를 위한 개발](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)을 참조하세요.

## <a name="next-steps"></a>다음 단계

자습서를 시작하려면 **[1단계: Windows Forms 애플리케이션 프로젝트 만들기](../ide/step-1-create-a-windows-forms-application-project.md)** 로 시작합니다.

## <a name="see-also"></a>참조

* [추가 C# 자습서](../get-started/csharp/index.yml)
* [Visual Basic 자습서](../get-started/visual-basic/index.yml)
* [C++ 자습서](/cpp/get-started/tutorial-console-cpp)