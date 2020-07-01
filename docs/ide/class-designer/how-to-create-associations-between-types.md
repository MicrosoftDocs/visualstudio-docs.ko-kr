---
title: '방법: 형식 간의 연결 만들기(클래스 디자이너)'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cce893efaad5f2317b175391a2685cae7053e3c
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770954"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>방법: 클래스 디자이너에서 형식 간의 연결 만들기

**클래스 디자이너**의 연결 선은 다이어그램에서 클래스가 어떻게 연결되어 있는지 보여 줍니다. 연결 선은 해당 프로젝트에서 다른 클래스의 필드 또는 속성의 형식인 클래스를 나타냅니다. 일반적으로 연결 선은 프로젝트에서 클래스 간에 가장 중요한 관계를 보여 주는 데 사용됩니다.

모든 필드와 속성을 연결로 표시할 수 있지만 다이어그램에서 강조할 내용에 따라 중요한 멤버만 연결로 표시하는 것이 좋습니다. 그 밖의 멤버는 일반 멤버로 표시하거나 완전히 숨길 수도 있습니다.

> [!NOTE]
> **클래스 디자이너**에서는 단방향 연결만 지원됩니다.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>클래스 다이어그램에서 연결 선을 정의하려면

1. 도구 상자의 **클래스 디자이너**에서 **연결**을 선택합니다.

2. 서로 연결할 두 모양 간에 연결 선을 그립니다.

     첫 번째 클래스에 새 속성이 만들어집니다. 이 속성은 모양 구획 내에 만들어지지 않고 기본 이름으로 된 연결 선으로 표시됩니다. 해당 형식은 연결 선이 가리키는 모양입니다.

## <a name="to-change-the-name-of-an-association"></a>연결의 이름을 변경하려면

다이어그램 화면에서 연결 선의 레이블을 클릭한 후에 편집합니다.

또는 다음 단계를 수행합니다.

1. 연결로 표시된 속성이 포함된 도형을 선택합니다.

   도형은 포커스를 얻고 멤버는 **클래스 세부 내용** 및 **속성** 창에 표시됩니다.

2. **클래스 세부 내용**이나 **속성** 창에서 해당 속성의 이름 필드를 편집하고 **Enter** 키를 누릅니다.

   **클래스 세부 내용** 창, 형식 연결 선, **속성** 창 및 코드에서 이름이 업데이트됩니다.

## <a name="see-also"></a>참고 항목

- [방법: 멤버 표시와 연결 표시 간 변경](how-to-change-between-member-notation-and-association-notation.md)
