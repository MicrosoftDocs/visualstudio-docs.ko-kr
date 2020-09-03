---
title: '방법: 클래스 디자이너를 사용하여 형식 만들기'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98e489a37e5d75cbc17d17c32a1fa3b53f9993f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770223"
---
# <a name="how-to-create-types-by-using-class-designer"></a>방법: 클래스 디자이너를 사용하여 형식 만들기

새로운 형식의 C# 및 Visual Basic 프로젝트를 디자인하려면 클래스 다이어그램에서 해당 형식을 만듭니다. 기존 형식을 보려면 [방법: 기존 형식 보기](how-to-view-existing-types.md)를 참조하세요.

## <a name="create-a-new-type"></a><a name="CreateType"></a> 새 형식 만들기

1. **도구 상자**의 **클래스 디자이너**에서 이 중 하나를 클래스 다이어그램으로 끌어 옵니다.

    - **클래스** 또는 **추상 클래스**

    - **Enum**

    - **인터페이스**

    - **구조체**(VB) 또는 **구조체**(C#)

    - **대리자**

    - **모듈**(VB에만 해당)

2. 형식 이름을 지정합니다. 그 다음 액세스 수준을 선택합니다.

3. 형식에 대해 초기 코드를 추가할 파일을 선택합니다.

    - 새 파일을 만들어 현재 프로젝트에 추가하려면 **새 파일 만들기**를 선택하고 파일 이름을 지정합니다.

    - 기존 파일에 코드를 추가하려면 **기존 파일에 추가**를 선택합니다.

         여러 앱 간에 코드를 공유하는 프로젝트가 솔루션에 포함되어 있는 경우 앱 프로젝트의 클래스 다이어그램에 새 형식을 추가할 수 있지만 해당 클래스 파일이 같은 앱 프로젝트 또는 공유 프로젝트에 있어야 합니다.

4. 이제 형식을 정의할 다른 항목을 추가합니다.

    |**형식**|**추가**|
    |-|-|
    |클래스, 추상 클래스, 구조체 또는 구조체|형식을 정의하는 메서드, 속성, 필드, 이벤트, 생성자(메서드), 소멸자(메서드) 및 상수|
    |열거형|열거형을 구성하고 있는 필드 값|
    |인터페이스|인터페이스를 구성하는 메서드, 속성 및 이벤트|
    |대리자|대리자를 정의하는 매개 변수|
    |모듈|모듈을 정의하는 메서드, 속성, 필드, 이벤트, 생성자(메서드) 및 상수|

     [멤버 만들기](creating-and-configuring-type-members.md#create-members)를 참조하세요.

## <a name="apply-a-custom-attribute-to-a-type"></a><a name="CustAttributeType"></a> 형식에 사용자 지정 특성 적용

1. 클래스 다이어그램에서 형식의 모양을 클릭합니다.

2. **속성**에서 해당 형식의 **사용자 지정 특성** 속성 옆에 있는 줄임표(...) 단추를 클릭합니다.

3. 하나 이상의 사용자 지정 특성을 한 줄에 하나씩 추가합니다. 중괄호로 묶지 마십시오.

   사용자 지정 특성이 해당 형식에 적용됩니다.

## <a name="apply-a-custom-attribute-to-a-type-member"></a><a name="CustAttributeMember"></a> 형식 멤버에 사용자 지정 특성 적용

1. 클래스 다이어그램에서 형식 모양에 있는 멤버의 이름을 클릭하거나 클래스 세부 내용 창에서 해당 행을 클릭합니다.

2. **속성**에서 해당 멤버의 **사용자 지정 특성** 속성을 찾습니다.

3. 하나 이상의 사용자 지정 특성을 한 줄에 하나씩 추가합니다. 중괄호로 묶지 마십시오.

   사용자 지정 특성이 해당 형식에 적용됩니다.

## <a name="see-also"></a>참고 항목

- [방법: 형식 간에 상속 만들기](how-to-create-inheritance-between-types.md)
- [방법: 형식 간에 연결 만들기](how-to-create-associations-between-types.md)
- [형식 멤버 만들기 및 구성](creating-and-configuring-type-members.md)
- [클래스 및 형식 디자인](designing-and-viewing-classes-and-types.md)
