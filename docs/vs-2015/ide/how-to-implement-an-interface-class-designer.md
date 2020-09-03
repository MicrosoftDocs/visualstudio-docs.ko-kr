---
title: '방법: 인터페이스 구현(클래스 디자이너) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b750830e8263d0016f52a71ad4eac8c6950eda8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651859"
---
# <a name="how-to-implement-an-interface-class-designer"></a>방법: 인터페이스 구현(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 디자이너에서는 인터페이스 메서드의 코드를 제공하는 클래스에 인터페이스를 연결하여 클래스 다이어그램에서 인터페이스를 구현할 수 있습니다. 클래스 디자이너는 인터페이스 구현을 생성하고 인터페이스와 클래스 간의 관계를 상속 관계로 표시합니다. 인터페이스와 클래스 간의 상속 줄을 그리거나 클래스 뷰에서 인터페이스를 끌어와서 인터페이스를 구현할 수 있습니다.

> [!TIP]
> 다른 형식을 만들 때와 동일한 방식으로 인터페이스를 만들 수 있습니다. 인터페이스가 클래스 다이어그램에 표시되지 않는 경우 먼저 표시합니다. 자세한 내용은 [방법: 클래스 디자이너를 사용하여 형식 만들기](../ide/how-to-create-types-by-using-class-designer.md) 및 [방법: 기존 형식 보기(클래스 디자이너)](../ide/how-to-view-existing-types-class-designer.md)를 참조하세요.

### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>상속 선을 그려서 인터페이스를 구현하려면

1. 클래스 다이어그램에서 인터페이스 및 인터페이스를 구현하는 클래스를 표시합니다.

2. 클래스 및 인터페이스에서 상속 선을 그립니다.

    롤리팝이 클래스에 연결되도록 표시되고 인터페이스 이름을 가진 레이블은 상속 관계를 식별합니다. Visual Studio는 모든 인터페이스 멤버에 대한 스텁을 생성합니다.

   자세한 내용은 [방법: 형식 간의 상속 만들기(클래스 디자이너)](../ide/how-to-create-inheritance-between-types-class-designer.md)를 참조하세요.

### <a name="to-implement-an-interface-from-the-class-view-window"></a>클래스 뷰 창에서 인터페이스를 구현하려면

1. 클래스 다이어그램에서 인터페이스를 구현하려는 클래스를 표시합니다.

2. 클래스 뷰를 열고 인터페이스를 찾습니다.

    > [!TIP]
    > 클래스 뷰가 열려 있지 않으면 **보기** 메뉴에서 클래스 뷰를 엽니다. 클래스 뷰에 대한 자세한 내용은 [클래스 및 해당 멤버 보기](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)를 참조하세요.

3. 다이어그램에서 클래스 도형으로 인터페이스 노드를 끌어옵니다.

     롤리팝이 클래스에 연결되도록 표시되고 인터페이스 이름을 가진 레이블은 상속 관계를 식별합니다. Visual Studio는 모든 인터페이스 멤버에 대한 스텁을 생성합니다. 이 시점에서 인터페이스를 구현합니다.

## <a name="see-also"></a>관련 항목
 [방법: 클래스 디자이너를 사용 하 여 형식 만들기](../ide/how-to-create-types-by-using-class-designer.md) [방법: 기존 형식 보기 (클래스 디자이너)](../ide/how-to-view-existing-types-class-designer.md) [방법: 형식 간의 상속 만들기 (클래스 디자이너)](../ide/how-to-create-inheritance-between-types-class-designer.md) [클래스 및 형식 리팩터링 (클래스 디자이너)](../ide/refactoring-classes-and-types-class-designer.md)
