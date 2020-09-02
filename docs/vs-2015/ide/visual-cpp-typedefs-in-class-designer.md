---
title: 클래스 디자이너의 Visual C++ 형식 정의 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646745"
---
# <a name="visual-c-typedefs-in-class-designer"></a>클래스 디자이너의 Visual C++ 형식 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Typedef 문은 이름과 기본 형식 간에 하나 이상의 간접 참조 레이어를 만듭니다. 클래스 디자이너는 `typedef` 키워드로 선언된 C++ typedef 형식을 지원합니다. 예:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 그런 다음 이 형식을 사용하여 인스턴스를 선언할 수 있습니다.

 `COORD OriginPoint;`

 이름 없이 typedef를 선언할 수 있지만, 클래스 디자이너에서 지정한 태그 이름이 사용되지 않습니다. 클래스 뷰에서 생성하는 이름이 사용됩니다. 예를 들어 다음 선언은 유효하지만 클래스 뷰 및 클래스 디자이너에 **__unnamed**라는 개체로 나타납니다.

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 `typedef` 형식을 사용하는 방법에 대한 자세한 내용은 [(NOTINBUILD)typedef 지정자](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1)를 참조하세요.

 C++ typedef 도형은 typedef에 지정된 형식의 도형입니다. 예를 들어 소스에서 `typedef class`를 선언하는 경우 도형에 둥근 모서리와 **클래스** 레이블이 있습니다. `typedef struct`의 경우 도형에 사각형 모서리와 **구조체** 레이블이 있습니다.

 클래스와 구조체 내부에서 중첩된 typedef가 선언될 수 있으므로 클래스 및 구조체 도형에 중첩된 typedef 선언이 중첩된 도형으로 표시될 수 있습니다.

 Typedef 도형은 상황에 맞는 메뉴에서 **형식 연결로 표시** 및 **컬렉션 형식 연결로 표시** 명령을 지원합니다.

 다음은 클래스 디자이너에서 지원하는 typedef 형식의 몇 가지 예입니다.

 `typedef type name`

 *이름* : *형식*

 형식 정의

 가능한 경우 *name* 형식에 연결하는 형식 연결 선을 그립니다.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

 형식 정의

 함수 포인터에 대한 Typedef입니다. 형식 연결 선이 그려지지 않습니다.

 소스 형식이 함수 포인터인 경우 클래스 디자이너에 typedef가 표시되지 않습니다.

```
typedef int MyInt;
class A {
   MyInt I;
};
```

 `MyInt: int`

 형식 정의

 `A`

 클래스

 소스 형식 도형에서 대상 형식 도형을 가리키는 형식 연결 선을 그립니다.

 `Class B {};`

 `typedef B MyB;`

 `B`

 클래스

 `MyB : B`

 형식 정의

 typedef 도형을 마우스 오른쪽 단추로 클릭하고 **도형 연결로 표시**를 클릭하면 typedef 또는 클래스와 두 도형을 연결하는 선(형식 연결 선과 유사)의 **별칭**이 표시됩니다.

 `typedef B MyB;`

 `typedef MyB A;`

 `MyBar : Bar`

 형식 정의

 위와 동일합니다.

```
Class B {};
typedef B MyB;

class A {
   MyB B;
};
```

 `B`

 클래스

 `MyB : B`

 형식 정의

 `A`

 클래스

 `MyB`는 중첩된 typedef 도형입니다.

 `#include <vector>`

 `...`

 `using namespace std;`

 `...`

 `typedef vector<int> MyIntVect;`

 `vector<T>`Class

 `MyIntVect : vector<int>`

 형식 정의

 `class B {};`

 `typedef B MyB;`

 `class A : MyB {};`

 `MyB : B`

 형식 정의

 -> B

 `B`

 `A`

 클래스

 -> MyB

 클래스 디자이너에서 상황에 맞는 메뉴 명령을 사용하여 이러한 종류의 관계를 표시하는 기능을 지원하지 않습니다.

 `#include <vector>`

 `Typedef MyIntVect std::vector<int>;`

 `Class MyVect : MyIntVect {};`

 `std::vector<T>`

 클래스

 `MyIntVect : std::vector<int>`

 형식 정의

 `MyVect`

 클래스

 -> MyIntVect

## <a name="see-also"></a>관련 항목
 [Visual C++ 코드 (클래스 디자이너)](../ide/working-with-visual-cpp-code-class-designer.md) [(notinbuild) typedef 지정자](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1) 사용
