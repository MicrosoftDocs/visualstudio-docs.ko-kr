---
title: '방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)'
ms.date: 05/08/2018
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a6c1e996d820724138b6bf38c6440193a4c26b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588839"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>방법: 프로젝트에 클래스 다이어그램 추가

클래스와 기타 형식을 디자인, 편집 및 리팩터링하려면 C#, Visual Basic 또는 C++ 프로젝트에 클래스 다이어그램을 추가합니다. 프로젝트에서 각기 다른 코드 부분을 표시하려면 여러 클래스 다이어그램을 프로젝트에 추가합니다.

여러 앱 간에 코드를 공유하는 프로젝트에서는 클래스 다이어그램을 만들 수 없습니다. UML 클래스 다이어그램을 만들려면 [Visual Studio에서 UML 모델링 프로젝트 및 다이어그램 만들기](../../modeling/what-s-new-for-design-in-visual-studio.md)를 참조하세요.

## <a name="install-the-class-designer-component"></a>클래스 디자이너 구성 요소 설치

**클래스 디자이너** 구성 요소를 설치하지 않은 경우 다음 단계에 따라 설치합니다.

1. Windows 시작 메뉴에서 **Visual Studio 설치 관리자**를 열거나 Visual Studio의 메뉴 막대에서 **도구** > **도구 및 기능 가져 오기**를 선택합니다.

   **Visual Studio 설치 관리자**가 열립니다.

1. **개별 구성 요소** 탭을 선택한 다음, **코드 도구** 범주까지 아래로 스크롤합니다.

1. **클래스 디자이너**를 선택하고 **수정**을 선택합니다.

   ![Visual Studio 설치 관리자의 클래스 디자이너 구성 요소](media/class-designer-component.png)

   **클래스 디자이너** 구성 요소가 설치를 시작합니다.

## <a name="add-a-blank-class-diagram-to-a-project"></a>프로젝트에 빈 클래스 다이어그램 추가

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭한 다음, **추가** > **새 항목**을 선택합니다. 또는 **Ctrl**+**Alt**+**A** 키를 누릅니다.

   **새 항목 추가** 대화 상자가 열립니다.

2. **공통 항목** > **일반**을 확장한 다음, 템플릿 목록에서 **클래스 다이어그램**을 선택합니다. Visual C++ 프로젝트의 경우 **유틸리티** 범주에서 **클래스 다이어그램** 템플릿을 찾습니다.

   > [!NOTE]
   > **클래스 다이어그램** 템플릿이 보이지 않으면 [단계를 따라](#install-the-class-designer-component) Visual Studio용 **클래스 디자이너** 구성 요소를 설치합니다.

   클래스 디자이너에 클래스 다이어그램이 열립니다. 이 다이어그램은 **솔루션 탐색기**에 확장명이 *.cd*인 파일로 나타납니다. **도구 상자**에서 도형과 선을 다이어그램으로 끌어올 수 있습니다.

여러 클래스 다이어그램을 추가하려면 이 절차의 단계를 반복합니다.

## <a name="add-a-class-diagram-based-on-existing-types"></a>기존 형식을 기반으로 클래스 다이어그램 추가

**솔루션 탐색기**에서 클래스 파일의 상황에 맞는 메뉴(마우스 오른쪽 단추로 클릭)를 열고 **클래스 다이어그램 보기**를 선택합니다.

또는

**클래스 뷰**에서 네임스페이스 또는 형식 상황에 맞는 메뉴를 연 다음, **클래스 다이어그램 보기**를 선택합니다.

> [!TIP]
> **클래스 뷰**가 열려 있지 않으면 **보기** 메뉴에서 **클래스 뷰**를 엽니다.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>클래스 다이어그램에 전체 프로젝트의 내용을 표시하려면

**솔루션 탐색기**나 클래스 뷰에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **보기**, **클래스 다이어그램 보기**를 차례로 선택합니다.

자동으로 채워진 클래스 다이어그램이 만들어집니다.

> [!NOTE]
> .NET Core 프로젝트에서는 아직 클래스 디자이너를 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

- [방법: 클래스 디자이너를 사용하여 형식 만들기](how-to-create-types.md)
- [방법: 기존 형식 보기](how-to-view-existing-types.md)
- [클래스와 형식 디자인 및 보기](designing-and-viewing-classes-and-types.md)
