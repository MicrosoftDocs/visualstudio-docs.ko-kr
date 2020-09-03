---
title: '7단계: 폼에 대화 상자 구성 요소 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40b90096f768a7dd836507c83dff935261a99a25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851137"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7단계: 폼에 대화 상자 구성 요소 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 단계에서, 그림 파일을 열고 배경색을 선택할 수 있도록 프로그램을 설정하려면 **OpenFileDialog** 구성 요소 및 **ColorDialog** 구성 요소를 폼에 추가합니다.

 구성 요소는 몇 가지 점에서 컨트롤과 비슷합니다. 도구 상자를 사용하여 구성 요소를 폼에 추가하고 **속성** 창을 사용하여 구성 요소의 속성을 설정합니다. 그러나 컨트롤과 달리 구성 요소를 폼에 추가할 때는 실제로 폼에 표시되는 항목이 추가되지 않습니다. 대신 코드를 사용하여 트리거할 수 있는 특정 동작이 제공됩니다. 예를 들어 **파일 열기** 대화 상자를 여는 것은 바로 구성 요소입니다.

 ![비디오에 연결](../data-tools/media/playvideo.gif "링크 playvideo 보려면") 이 항목의 비디오 버전을 보려면 [자습서 1: Visual Basic에서 사진 뷰어 만들기-비디오 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) 또는 [자습서 1: c #에서 사진 뷰어 만들기-비디오 3](https://msdn.microsoft.com/vcsharp/gg278411.aspx)을 참조 하세요. 이러한 비디오에서는 이전 버전의 Visual Studio를 사용하므로 일부 메뉴 명령과 기타 사용자 인터페이스 요소가 약간 다를 수 있습니다. 그러나 개념 및 절차는 Visual Studio의 현재 버전에서 비슷하게 작동합니다.

### <a name="to-add-dialog-components-to-your-form"></a>폼에 대화 상자 구성 요소를 추가하려면

1. Windows Forms 디자이너 (Form1.cs [Design] 또는 form1.vb [Design])를 선택 하 고 도구 상자에서 **대화** 상자 그룹을 엽니다.

    > [!NOTE]
    > 도구 상자의 **대화 상자** 그룹에는 파일을 열거나 닫고, 폴더를 찾아보고, 글꼴과 색을 선택하는 데 사용할 수 있는 많은 유용한 대화 상자를 여는 구성 요소가 있습니다. 이 프로젝트에서는 **OpenFileDialog** 및 **ColorDialog**의 두 가지 대화 상자 구성 요소를 사용 합니다.

2. **openFileDialog1**이라는 구성 요소를 폼에 추가하려면 **OpenFileDialog**를 두 번 클릭합니다. **ColorDialog1** 이라는 구성 요소를 폼에 추가 하려면 도구 상자에서 **ColorDialog** 를 두 번 클릭 합니다. (다음 자습서 단계에서이 항목을 사용 합니다.) 다음 그림과 같이 사용자가 추가한 두 대화 상자 구성 요소 각각에 대 한 아이콘이 있는 Windows Forms 디자이너 (그림 뷰어 폼 아래)의 맨 아래에 영역이 표시 됩니다.

     ![대화 상자 구성 요소](../ide/media/express-dialogsadded.png "Express_DialogsAdded") 대화 상자 구성 요소

3. Windows Forms 디자이너 아래쪽에 있는 영역에서 **openFileDialog1** 아이콘을 선택 합니다. 다음 두 가지 속성을 설정합니다.

    - 다음과 같이 **필터** 속성을 설정합니다(복사하여 붙여 넣을 수 있음).

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **제목** 속성을 **그림 파일 선택**으로 설정합니다.

         **필터** 속성 설정은 **그림 선택** 파일 대화 상자에 표시되는 파일 형식을 지정합니다.

    > [!NOTE]
    > 다른 애플리케이션에서 **파일 열기** 대화 상자의 예제를 보려면 메모장이나 그림판을 열고 메뉴 모음에서 **파일**, **열기**를 선택합니다. 맨 아래에 있는 **파일 형식** 드롭다운 목록을 살펴봅니다. 이러한 값은 단순히 **OpenFileDialog** 구성 요소의 **필터** 속성을 사용하여 설정했습니다. 또한 **속성** 창에서 굵게 표시된 **제목** 및 **필터** 속성도 살펴봅니다. IDE에서는 굵은 글꼴을 사용하여 기본값에서 변경된 속성을 표시합니다.

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동 하려면 [8 단계: 그림 단추 이벤트 처리기 표시를 위한 코드 작성](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)을 참조 하세요.

- 이전 자습서 단계로 돌아가려면 [6 단계: 단추 컨트롤 이름](../ide/step-6-name-your-button-controls.md)표시를 참조 하세요.
