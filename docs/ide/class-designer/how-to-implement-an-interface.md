---
title: '방법: 인터페이스 구현(클래스 디자이너)'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81b6815dd96894acd574de59c5616371220d2999
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770104"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>방법: 클래스 디자이너에서 인터페이스 구현

**클래스 디자이너**에서는 인터페이스 메서드의 코드를 제공하는 클래스에 인터페이스를 연결하여 클래스 다이어그램에서 인터페이스를 구현할 수 있습니다. **클래스 디자이너**는 인터페이스 구현을 생성하고 인터페이스와 클래스 간의 관계를 상속 관계로 표시합니다. 인터페이스와 클래스 간의 상속 줄을 그리거나 클래스 뷰에서 인터페이스를 끌어와서 인터페이스를 구현할 수 있습니다.

> [!TIP]
> 다른 형식을 만들 때와 동일한 방식으로 인터페이스를 만들 수 있습니다. 인터페이스가 클래스 다이어그램에 표시되지 않는 경우 먼저 표시합니다. 자세한 내용은 [방법: 클래스 디자이너를 사용하여 형식 만들기](how-to-create-types.md) 및 [방법: 기존 형식 보기](how-to-view-existing-types.md)를 참조하세요.

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>상속 선을 그려서 인터페이스를 구현하려면

1. 클래스 다이어그램에서 인터페이스 및 인터페이스를 구현하는 클래스를 표시합니다.

2. 클래스 및 인터페이스에서 상속 선을 그립니다.

     롤리팝이 클래스에 연결되도록 표시되고 인터페이스 이름을 가진 레이블은 상속 관계를 식별합니다. Visual Studio는 모든 인터페이스 멤버에 대한 스텁을 생성합니다.

자세한 내용은 [방법: 형식 간의 상속 만들기](how-to-create-inheritance-between-types.md)를 참조하세요.

## <a name="to-implement-an-interface-from-the-class-view-window"></a>클래스 뷰 창에서 인터페이스를 구현하려면

1. 클래스 다이어그램에서 인터페이스를 구현하려는 클래스를 표시합니다.

2. **클래스 뷰**를 열고 인터페이스를 찾습니다.

    > [!TIP]
    > **클래스 뷰**가 열려 있지 않으면 **보기** 메뉴에서 **클래스 뷰**를 열거나 **Ctrl**+**Shift**+**C** 키를 누릅니다.

3. 다이어그램에서 클래스 도형으로 인터페이스 노드를 끌어옵니다.

     롤리팝이 클래스에 연결되도록 표시되고 인터페이스 이름을 가진 레이블은 상속 관계를 식별합니다. Visual Studio는 모든 인터페이스 멤버에 대한 스텁을 생성합니다. 이 시점에서 인터페이스를 구현합니다.

## <a name="see-also"></a>참고 항목

- [방법: 클래스 디자이너를 사용하여 형식 만들기](how-to-create-types.md)
- [방법: 기존 형식 보기](how-to-view-existing-types.md)
- [방법: 형식 간에 상속 만들기](how-to-create-inheritance-between-types.md)
- [클래스 및 형식 리팩터링](refactoring-classes-and-types.md)
