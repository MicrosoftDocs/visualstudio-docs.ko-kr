---
title: 멤버 및 연결 표시 간 변경(클래스 디자이너)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f706acfbaee7c6170f74bc655f9172ff6bdd3b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592271"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>방법: 클래스 디자이너에서 멤버 표시와 연결 표시 간 변경

**클래스 디자이너**에서 클래스 다이어그램이 두 형식 사이의 연결 관계를 나타내는 방법을 멤버 표기법에서 연결 표기법으로, 또는 그 반대로 변경할 수 있습니다. 형식 연결 선으로 표시된 멤버는 형식이 어떻게 관련되어 있는지 효과적으로 시각화하여 보여 주는 경우가 많습니다.

> [!NOTE]
> 연결 관계는 멤버 속성 또는 필드로 나타낼 수 있습니다. 멤버 표기법을 연결 표기법으로 변경하려면 한 형식에 다른 형식의 멤버가 있어야 합니다. 연결 표기법을 멤버 표기법으로 변경하려면 두 형식이 형식 연결 선으로 연결되어 있어야 합니다. 자세한 내용은 [방법: 형식 간의 연결 만들기](how-to-create-associations-between-types.md)를 참조하세요. 프로젝트에 클래스 다이어그램이 여러 개 있는 경우 한 다이어그램에서 연결 관계 표시 방법을 변경하면 변경 내용이 해당 다이어그램에만 영향을 줍니다. 다른 다이어그램의 연결 관계 표시 방법을 변경하려면 해당 다이어그램을 열거나 표시하고 변경 단계를 수행합니다.

## <a name="to-change-member-notation-to-association-notation"></a>멤버 표기법을 연결 표기법으로 변경하려면

1. 솔루션 탐색기의 프로젝트 노드에서 클래스 다이어그램(.cd) 파일을 엽니다.

2. 클래스 다이어그램의 형식 도형에서 해당 연결을 나타내는 멤버 속성 또는 필드를 마우스 오른쪽 단추로 클릭하고 **형식 연결로 표시**를 선택합니다.

    > [!TIP]
    > 형식 도형에 속성 또는 필드가 표시되지 않는 경우 도형의 구획이 축소된 상태일 수 있습니다. 형식 도형을 확장하려면 구획 이름을 두 번 클릭하거나 형식 도형을 마우스 오른쪽 단추로 클릭하고 **확장**을 선택합니다.

    형식 도형의 구획에서 멤버가 사라지고 두 형식을 연결하는 형식 연결 선이 나타납니다. 형식 연결 선은 속성 또는 필드 이름으로 레이블이 지정됩니다.

## <a name="to-change-association-notation-to-member-notation"></a>연결 표기법을 멤버 표기법으로 변경하려면

클래스 다이어그램에서 형식 연결 선을 마우스 오른쪽 단추로 클릭하고 **속성으로 표시** 또는 **필드로 표시**를 적절하게 선택합니다. 형식 연결 선이 사라지고 다이어그램의 해당 형식 도형 내 적합한 구획에 속성이 표시됩니다.

## <a name="see-also"></a>참고 항목

- [방법: 형식 간에 상속 만들기](how-to-create-inheritance-between-types.md)
- [방법: 형식 간의 상속 보기](how-to-view-inheritance-between-types.md)
- [형식 및 관계 보기](designing-and-viewing-classes-and-types.md)
- [방법: 컬렉션 연결 시각화](how-to-visualize-a-collection-association.md)
