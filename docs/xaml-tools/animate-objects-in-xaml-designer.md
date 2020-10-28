---
title: XAML 디자이너에서 개체에 애니메이션 효과 주기
titleSuffix: Blend for Visual Studio
description: 타임 라인과 키프레임이 있는 storyboard를 사용 하 여 XAML 디자이너에서 개체에 애니메이션 효과를 주는 Blend for Visual Studio에서 애니메이션을 만드는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: how-to
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2c1c4100921430daa0faa0daba3c3c3f5328fb3d
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796331"
---
# <a name="animate-objects-in-xaml-designer"></a>XAML 디자이너에서 개체에 애니메이션 효과 주기

예를 들어 Blend for Visual Studio를 사용하면 개체를 이동하거나 페이드 인 및 페이드 아웃하는 짧은 애니메이션을 쉽게 만들 수 있습니다.

애니메이션을 만들려면 *스토리보드* 가 필요합니다. 스토리보드에는 하나 이상의 *타임 라인* 이 포함됩니다. 타임라인에서 *키 프레임* 을 설정하여 속성 변경 내용을 표시합니다. 그런 다음 애니메이션을 실행하면 Blend for Visual Studio가 지정된 기간 동안 속성 변경 내용을 보간합니다. 따라서 부드러운 전환이 가능해집니다. 비시각적 속성을 비롯하여 개체에 속하는 모든 속성에 애니메이션 효과를 적용할 수 있습니다.

다음 이미지는 **Storyboard1** 이라는 스토리보드를 보여 줍니다. 타임라인에는 사각형의 X 및 Y 위치를 표시하는 키 프레임이 포함됩니다. 이 애니메이션을 실행하면 사각형이 특정 위치에서 다른 위치로 부드럽게 이동합니다.

![Blend for Visual Studio의 애니메이션용 스토리보드](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>애니메이션 만들기

1. 스토리보드를 만들려면 **개체 및 타임라인** 창에서 **스토리보드 옵션** 단추를 선택한 후 **새로 만들기** 를 선택합니다.

   ![Blend for Visual Studio에서 스토리보드 추가](media/new-storyboard.png)

2. **스토리보드 만들기 리소스** 대화 상자에서 스토리지보드의 이름을 입력합니다.

3. 디자인 뷰의 **자산** 패널에서 페이지 왼쪽 아래에 사각형을 추가합니다.

   ![XAML 디자이너의 자산 패널에 있는 사각형](media/add-rectangle.PNG)

4. **개체 및 타임라인** 창에서 노란색 시간 포인터를 **3** 초로 이동합니다.

   ![타임라인의 시간 표시기](media/timeline-indicator.PNG)

5. 페이지의 디자인 뷰에서 사각형을 페이지의 오른쪽으로 끌어 놓습니다.

6. **재생** 을 누르면 사각형이 페이지의 왼쪽에서 오른쪽으로 이동합니다.

시점에 따라 사각형의 다른 변경 내용으로 재생합니다. 예를 들어 채우기 색을 변경하거나 속성 창에서 방향을 대칭 이동할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [Blend for Visual Studio를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
