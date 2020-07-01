---
title: 클래스 디자이너에서 클래스 및 형식 이름 바꾸기 및 이동
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baf0e9d9d0f4bb45ef965f64c256bd9360af112b
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768603"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>클래스 디자이너에서 클래스 및 형식 리팩터링

코드를 리팩터링할 때 외부 동작이 아닌 내부 구조와 개체 설계 방식을 변경하면 코드를 보다 효율적이며 쉽게 이해하고 유지 관리할 수 있습니다. 클래스 디자이너 및 클래스 세부 내용 창을 사용하면 Visual Studio 프로젝트에서 C#, Visual Basic 또는 C++ 코드를 리팩터링할 때 수행해야 하는 작업과 버그 발생 가능성을 줄일 수 있습니다.

> [!NOTE]
> 프로젝트가 소스 코드로 제어되며 체크 아웃되지 않은 경우, 참조되는 프로젝트인 경우 또는 해당 파일이 디스크에서 읽기 전용으로 표시된 경우 프로젝트의 파일은 읽기 전용일 수 있습니다. 이러한 상태 중 하나인 프로젝트에서 작업할 때는 프로젝트 상태에 따라 다양한 방식으로 작업을 저장할 수 있습니다. 이 방식은 리팩터링 코드와 직접 편집 등의 다른 방법으로 변경하는 코드에도 적용됩니다.

## <a name="common-tasks"></a>일반 작업

|Task|지원 콘텐츠|
|----------| - |
|**클래스 리팩터링:** 리팩터링 작업을 통해 클래스를 부분 클래스로 분할하거나 추상 기본 클래스를 구현할 수 있습니다.|-   [방법: 클래스를 부분 클래스로 분할](how-to-split-a-class-into-partial-classes.md)|
|**인터페이스 사용:** 클래스 디자이너에서는 인터페이스 메서드의 코드를 제공하는 클래스에 인터페이스를 연결하여 클래스 다이어그램에서 인터페이스를 구현할 수 있습니다.|-   [방법: 인터페이스 구현](how-to-implement-an-interface.md)|
|**형식, 형식 구성원 및 매개 변수 리팩터링:** 클래스 디자이너를 사용하여 형식 이름을 바꾸거나, 형식 구성원을 재정의하거나, 한 형식에서 다른 형식으로 이동할 수 있습니다. nullable 형식을 만들 수도 있습니다.|-   [형식 및 형식 멤버 이름 바꾸기](#rename-types-and-type-members)<br />-   [형식 간에 형식 멤버 이동](#move-type-members-from-one-type-to-another)<br />-   [방법: Nullable 형식 만들기](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>형식 및 형식 멤버 이름 바꾸기

클래스 디자이너에서는 클래스 다이어그램이나 **속성** 창에서 형식 또는 형식의 멤버 이름을 바꿀 수 있습니다. **클래스 세부 내용** 창에서는 형식이 아닌 멤버의 이름을 변경할 수 있습니다. 형식 또는 형식 멤버의 이름을 바꾸면 이전 이름이 표시되었던 모든 창과 코드 위치로 변경 내용이 전파됩니다.

### <a name="rename-in-the-class-designer"></a>클래스 디자이너에서 이름 바꾸기

1. 클래스 다이어그램에서 형식 또는 멤버를 선택하고 이름을 선택합니다.

     멤버의 이름이 편집 가능한 상태가 됩니다.

2. 형식 또는 형식 멤버의 새 이름을 입력합니다.

### <a name="rename-in-the-class-details-window"></a>클래스 세부 내용 창에서 이름 바꾸기

1. **클래스 세부 내용** 창을 표시하려면 형식 또는 형식 멤버를 마우스 오른쪽 단추로 클릭하고 **클래스 세부 내용**을 선택합니다.

     **클래스 세부 내용** 창이 나타납니다.

2. **이름** 열에서 형식 멤버의 이름을 변경합니다.

3. 셀에서 포커스를 이동하려면 **Enter** 키를 누르거나 셀 바깥쪽을 클릭합니다.

    > [!NOTE]
    > **클래스 세부 내용** 창에서는 형식이 아닌 멤버의 이름을 변경할 수 있습니다.

### <a name="rename-in-the-properties-window"></a>속성 창에서 이름 바꾸기

1. 클래스 다이어그램 또는 **클래스 세부 내용** 창에서 형식이나 멤버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

     **속성** 창이 나타나고 형식 또는 형식 멤버의 속성이 표시됩니다.

2. **이름** 속성에서 형식 또는 형식 멤버의 이름을 변경합니다.

     새 이름은 현재 프로젝트에서 이전 이름이 표시되었던 모든 창 및 코드 위치로 전파됩니다.

## <a name="move-type-members-from-one-type-to-another"></a>형식 간에 형식 멤버 이동

**클래스 디자이너**를 사용하면 형식 멤버를 다른 형식으로 이동할 수 있습니다. 두 형식이 모두 현재 클래스 다이어그램에 표시되어야 합니다.

1. 디자인 화면에 표시된 형식에서 다른 형식으로 이동할 멤버를 마우스 오른쪽 단추로 클릭하고 **잘라내기**를 선택합니다.

2. 대상 형식을 마우스 오른쪽 단추로 클릭하고 **붙여넣기**를 선택합니다.

     속성이 소스 형식에서 제거되고 대상 형식에 나타납니다.

## <a name="see-also"></a>참고 항목

- [클래스 및 형식 디자인](designing-and-viewing-classes-and-types.md)
