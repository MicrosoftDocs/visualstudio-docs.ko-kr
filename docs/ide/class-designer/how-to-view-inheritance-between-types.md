---
title: '방법: 형식 간의 상속 보기(클래스 디자이너)'
description: 클래스 디자이너의 클래스 다이어그램에서 기본 형식과 파생 형식 간의 상속 관계를 찾는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82785f1a5cac2185925c63c4d6d224ffd5fd67de
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901195"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>방법: 클래스 디자이너에서 형식 간의 상속 보기

**클래스 디자이너** 의 클래스 다이어그램에서 기본 형식과 파생 형식 간에 상속 관계(있는 경우)를 찾을 수 있습니다. 두 형식 간에 상속 관계가 없는 경우 새로 만들려면 [방법: 형식 간에 상속 만들기](how-to-create-inheritance-between-types.md)를 참조하세요.

## <a name="to-find-the-base-type"></a>기본 형식을 찾으려면

1. 클래스 다이어그램에서 기본 클래스 또는 인터페이스를 확인할 형식을 클릭합니다.

2. **클래스 다이어그램** 메뉴에서 **기본 클래스 표시** 또는 **기본 인터페이스 표시** 를 선택합니다.

     형식의 기본 클래스 또는 인터페이스가 다이어그램에서 선택된 상태로 표시됩니다. 이제 숨겨진 상속 선이 두 모양 간에 표시됩니다.

기본 형식을 표시할 형식을 마우스 오른쪽 단추로 클릭하고 **기본 클래스 표시** 또는 **기본 인터페이스 표시** 를 선택해도 됩니다.

## <a name="to-find-the-derived-types"></a>파생 형식을 찾으려면

1. 클래스 다이어그램에서 파생 클래스 또는 인터페이스를 확인할 형식을 클릭합니다.

2. **클래스 다이어그램** 메뉴에서 **파생 클래스 표시** 또는 **파생 인터페이스 표시** 를 선택합니다.

     형식의 파생 클래스 또는 인터페이스가 다이어그램에 표시됩니다. 이제 숨겨진 상속 선이 모양 간에 표시됩니다.

파생 형식을 확인할 형식을 마우스 오른쪽 단추로 클릭하고 **파생 클래스 표시** 또는 **파생 인터페이스 표시** 를 선택해도 됩니다.

## <a name="see-also"></a>추가 정보

- [방법: 형식 간에 연결 만들기](how-to-create-associations-between-types.md)
- [형식 및 관계 보기](designing-and-viewing-classes-and-types.md)
