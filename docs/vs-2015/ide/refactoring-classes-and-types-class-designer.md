---
title: 클래스 및 형식 리팩터링(클래스 디자이너) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5803b720ae1271d8319310820d1f0dc159db8bf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670264"
---
# <a name="refactoring-classes-and-types-class-designer"></a>클래스 및 형식 리팩터링(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드를 리팩터링할 때 외부 동작이 아닌 내부 구조와 개체 설계 방식을 변경하면 코드를 보다 효율적이며 쉽게 이해하고 유지 관리할 수 있습니다. 클래스 디자이너 및 클래스 세부 내용 창을 사용하면 Visual Studio 프로젝트에서 Visual C# .NET, Visual Basic .NET 또는 C++ 코드를 리팩터링할 때 수행해야 하는 작업과 버그 발생 가능성을 줄일 수 있습니다.

> [!NOTE]
> 프로젝트가 소스 코드로 제어되며 체크 아웃되지 않은 경우, 참조되는 프로젝트인 경우 또는 해당 파일이 디스크에서 읽기 전용으로 표시된 경우 프로젝트의 파일은 읽기 전용일 수 있습니다. 이러한 상태 중 하나인 프로젝트에서 작업할 때는 프로젝트 상태에 따라 다양한 방식으로 작업을 저장할 수 있습니다. 이 방식은 리팩터링 코드와 직접 편집 등의 다른 방법으로 변경하는 코드에도 적용됩니다. 자세한 내용은 [읽기 전용 정보 표시(클래스 디자이너)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a)를 참조하세요.

## <a name="common-tasks"></a>일반 태스크

|Task|지원 콘텐츠|
|----------|------------------------|
|**클래스 리팩터링:** 리팩터링 작업을 통해 클래스를 부분 클래스로 분할하거나 추상 기본 클래스를 구현할 수 있습니다.|-   [방법: 클래스를 부분 클래스로 분할 (클래스 디자이너)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|
|**인터페이스 사용:** 클래스 디자이너에서는 인터페이스 메서드의 코드를 제공하는 클래스에 인터페이스를 연결하여 클래스 다이어그램에서 인터페이스를 구현할 수 있습니다.|-   [방법: 인터페이스 구현 (클래스 디자이너)](../ide/how-to-implement-an-interface-class-designer.md)|
|**형식, 형식 구성원 및 매개 변수 리팩터링:** 클래스 디자이너를 사용하여 형식 이름을 바꾸거나, 형식 구성원을 재정의하거나, 한 형식에서 다른 형식으로 이동할 수 있습니다. nullable 형식을 만들 수도 있습니다.|-   [형식 및 형식 멤버 이름 바꾸기](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [형식 간에 형식 멤버 이동](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [방법: Nullable 형식 만들기 (클래스 디자이너)](../ide/how-to-create-a-nullable-type-class-designer.md)|

### <a name="renaming-types-and-type-members"></a><a name="RenamingTypesAndMembers"></a> 형식 및 형식 멤버 이름 바꾸기
 클래스 디자이너에서는 클래스 다이어그램이나 속성 창에서 형식 또는 형식의 멤버 이름을 바꿀 수 있습니다. 클래스 세부 내용 창에서는 형식이 아닌 멤버의 이름을 변경할 수 있습니다. 형식 또는 형식 멤버의 이름을 바꾸면 이전 이름이 표시되었던 모든 창과 코드 위치로 변경 내용이 전파됩니다.

##### <a name="to-rename-a-name-in-the-class-designer"></a>클래스 디자이너에서 이름을 바꾸려면

1. 클래스 다이어그램에서 형식 또는 멤버를 선택하고 이름을 클릭합니다.

     멤버의 이름이 편집 가능한 상태가 됩니다.

2. 형식 또는 형식 멤버의 새 이름을 입력합니다.

##### <a name="to-rename-a-name-in-the-class-details-window"></a>클래스 세부 내용 창에서 이름을 바꾸려면

1. 클래스 세부 내용 창을 표시하려면 형식 또는 형식 멤버를 마우스 오른쪽 단추로 클릭하고 **클래스 세부 내용**을 클릭합니다.

     클래스 세부 내용 창이 나타납니다.

2. **이름** 열에서 형식 멤버의 이름을 변경합니다.

3. 셀에서 포커스를 이동하려면 **Enter** 키를 누르거나 셀 바깥쪽을 클릭합니다.

    > [!NOTE]
    > 클래스 세부 내용 창에서는 형식이 아닌 멤버의 이름을 변경할 수 있습니다.

##### <a name="to-rename-a-name-in-the-properties-window"></a>속성 창에서 이름을 바꾸려면

1. 클래스 다이어그램 또는 클래스 세부 내용 창에서 형식이나 멤버를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

     속성 창이 나타나고 형식 또는 형식 멤버의 속성이 표시됩니다.

2. **이름** 속성에서 형식 또는 형식 멤버의 이름을 변경합니다.

     새 이름은 현재 프로젝트에서 이전 이름이 표시되었던 모든 창 및 코드 위치로 전파됩니다.

### <a name="moving-type-members-from-one-type-to-another"></a><a name="MovingTypeMembers"></a> 형식 간에 형식 멤버 이동
 **클래스 디자이너**를 사용하면 형식 멤버를 현재 클래스 다이어그램에 표시되어 있는 형식 간에 이동할 수 있습니다.

##### <a name="to-move-a-type-member-from-one-type-to-another"></a>형식 멤버를 형식 간에 이동하려면

1. 디자인 화면에 표시된 형식에서 다른 형식으로 이동할 멤버를 마우스 오른쪽 단추로 클릭하고 **잘라내기**를 클릭합니다.

2. 대상 형식을 마우스 오른쪽 단추로 클릭한 다음 **붙여넣기**를 클릭합니다.

     속성이 소스 형식에서 제거되고 대상 형식에 나타납니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[형식 및 관계 보기(클래스 디자이너)](../ide/viewing-types-and-relationships-class-designer.md)||
|[클래스 및 형식 디자인(클래스 디자이너)](../ide/designing-classes-and-types-class-designer.md)||
