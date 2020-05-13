---
title: 클래스 디자이너의 C++ 형식 정의
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590698"
---
# <a name="c-typedefs-in-class-designer"></a>클래스 디자이너의 C++ 형식 정의

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) 문은 이름과 기본 형식 간에 하나 이상의 간접 참조 레이어를 만듭니다. **클래스 디자이너**는 `typedef` 키워드로 선언된 C++ typedef 형식을 지원합니다. 예:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

그런 다음 이 형식을 사용하여 인스턴스를 선언할 수 있습니다.

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>클래스 및 구조체 도형

**클래스 디자이너**에서 C++ typedef는 typedef에서 지정된 형식의 도형입니다. 소스에서 `typedef class`를 선언하는 경우 도형에 둥근 모서리와 **클래스** 레이블이 있습니다. `typedef struct`의 경우 도형에 사각형 모서리와 **구조체** 레이블이 있습니다.

클래스와 구조체에는 그 안에 선언된 typedef가 중첩되어 있을 수 있습니다. **클래스 디자이너**에서 클래스 및 구조체 모양은 중첩된 typedef 선언을 중첩된 도형으로 표시할 수 있습니다.

Typedef 도형은 오른쪽 클릭 메뉴(상황에 맞는 메뉴)에서 **형식 연결로 표시** 및 **컬렉션 형식 연결로 표시** 명령을 지원합니다.

### <a name="class-typedef-example"></a>Typedef 클래스 예제

```cpp
class B {};
typedef B MyB;
```

![클래스 디자이너의 C++ 클래스 typedef](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>구조체 typedef 예제

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![클래스 디자이너의 C++ 구조체 typedef](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>명명되지 않은 typedef

**클래스 디자이너**는 이름 없이 typedef를 선언할 수 있지만 지정한 태그 이름을 사용하지 않습니다. **클래스 디자이너**는 **클래스 뷰**가 생성하는 이름을 사용합니다. 예를 들어 다음 선언은 유효하지만 **클래스 뷰** 및 **클래스 디자이너**에 **__unnamed**라는 개체로 나타납니다.

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **클래스 디자이너**는 소스 형식이 함수 포인터인 typedef를 표시하지 않습니다.

## <a name="see-also"></a>참고 항목

- [C++ 코드 사용](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
