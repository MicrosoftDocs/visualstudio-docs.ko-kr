---
title: 클래스 디자이너 사용
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80668f3b999d9e022de3d22abb383f2dbd10730a
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507913"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Class Designer를 사용하여 클래스와 형식 디자인 및 보기

Visual Studio에서 **클래스 디자이너**를 사용하여 코드의 클래스와 기타 형식을 디자인, 시각화 및 리팩터링할 수 있습니다. C#, Visual Basic 또는 C++ 프로젝트에서 클래스를 만들고 편집하려면 클래스 다이어그램을 사용합니다. 또한 클래스 다이어그램을 사용하여 프로젝트 구조를 더 잘 이해하거나 코드를 다시 구성할 수 있습니다.

## <a name="what-you-can-do-with-class-diagrams"></a>클래스 다이어그램을 사용하여 할 수 있는 작업

- **디자인**: 클래스 다이어그램을 편집하여 프로젝트의 코드를 편집합니다. 새 요소를 추가하고 원치 않는 요소는 삭제할 수 있습니다. 변경 내용은 코드에 반영됩니다.

- **시각화**: 다이어그램에서 프로젝트의 클래스를 확인하여 프로젝트 구조를 이해합니다. 가장 중요한 프로젝트 세부 내용에 집중할 수 있도록 다이어그램을 사용자 지정할 수 있습니다. 나중에 데모 또는 설명서에 사용할 수 있도록 다이어그램을 저장합니다.

- **리팩터링**: 메서드를 재정의하고, 식별자 이름을 바꾸고, 매개 변수를 리팩터링하고, 인터페이스 및 추상 클래스를 구현합니다.

## <a name="view-types-and-relationships"></a>형식 및 관계 보기

클래스 다이어그램은 구성 구성원 및 이들 간의 관계 등 형식의 세부 정보를 표시합니다. 이러한 엔터티의 시각화는 코드에 대한 동적 뷰입니다. 즉, 디자이너에서 형식을 편집하고 엔터티의 소스 코드에 반영된 편집 내용을 확인할 수 있습니다. 마찬가지로, 클래스 다이어그램은 코드 파일에 대한 변경 사항과 동기화되어 유지됩니다.

> [!NOTE]
> 프로젝트가 클래스 다이어그램을 포함하는 경우 그리고 프로젝트가 다른 프로젝트에 있는 형식을 참조하는 경우 해당 형식에 대한 프로젝트를 빌드할 때까지 클래스 다이어그램은 참조 형식을 표시하지 않습니다. 마찬가지로 다이어그램은 해당 엔터티에 대한 프로젝트를 다시 작성할 때까지 외부 엔터티의 코드에 대한 변경 내용을 표시합니다.

## <a name="class-diagram-workflow"></a>클래스 다이어그램 워크플로

클래스 다이어그램은 프로젝트의 클래스 구조를 이해하는 데 도움이 됩니다. 이 프로젝트는 다른 개발자가 만들었거나 자신이 직접 만든 프로젝트를 다시 시작해야 할 수도 있습니다. 클래스 다이어그램을 사용하여 프로젝트 정보를 사용자 지정하고 다른 사용자와 공유 및 제공할 수 있습니다.

프로젝트 정보를 제공하는 첫 단계에서는 보여 주려는 정보를 표시하는 클래스 다이어그램을 만듭니다. 자세한 내용은 [클래스 다이어그램 추가](how-to-add-class-diagrams-to-projects.md)를 참조하세요. 개별 프로젝트 보기, 선택한 프로젝트 형식 하위 집합 또는 선택한 형식의 멤버 하위 집합을 표시하는 데 사용할 수 있는 여러 클래스 다이어그램을 프로젝트에 대해 만들 수 있습니다.

각 클래스 다이어그램에 표시되는 내용을 정의할 수 있을 뿐 아니라 정보가 표시되는 방식도 변경할 수 있습니다. 자세한 내용은 [방법: 클래스 다이어그램 사용자 지정](how-to-customize-class-diagrams.md)을 참조하세요.

하나 이상의 클래스 다이어그램을 미세 조정한 후 Microsoft Office 문서에 복사하고 인쇄하거나 이미지 파일로 내보낼 수 있습니다. 자세한 내용은 [방법: 클래스 다이어그램 요소를 Microsoft Office 문서에 복사](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [방법: 클래스 다이어그램 인쇄](how-to-print-class-diagrams.md) 및 [방법: 클래스 다이어그램을 이미지로 내보내기](how-to-export-class-diagrams-as-images.md)를 참조하세요.

> [!NOTE]
> 클래스 디자이너는 소스 파일 위치를 추적하지 않으므로 프로젝트 구조를 변경하거나 프로젝트에서 소스 파일을 이동하면 클래스 디자이너가 해당 형식을 찾지 못할 수 있습니다(특히 소스 형식이 typedef, 기본 클래스 또는 연결 형식인 경우). **클래스 디자이너에서 이 형식을 표시할 수 없습니다.** 와 같은 오류가 발생할 수 있습니다. 이러한 오류가 발생하면 수정되거나 위치가 변경된 소스 코드를 클래스 다이어그램으로 끌어서 다시 표시합니다.

## <a name="see-also"></a>참고 항목

- [코드 편집기의 기능](../writing-code-in-the-code-and-text-editor.md)
- [솔루션 전체의 종속성 매핑](../../modeling/map-dependencies-across-your-solutions.md)
