---
title: 클래스 디자이너의 C++ 클래스
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: d68391bbd4c6c873940bbc2714ee41db8309b629
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590737"
---
# <a name="c-classes-in-class-designer"></a>클래스 디자이너의 C++ 클래스

**클래스 디자이너**는 C++ 클래스를 지원하며, C++ 클래스가 여러 상속 관계를 포함한다는 점을 제외하고 Visual Basic 및 C# 클래스 모양과 동일한 방식으로 네이티브 C++ 클래스를 시각화합니다. 클래스 모양을 확장하여 추가 필드와 메서드를 클래스에 표시하거나 축소하여 공간을 절약할 수 있습니다.

> [!NOTE]
> **클래스 디자이너**는 공용 구조체(해당 데이터 멤버 중 가장 큰 데이터 멤버에 필요한 만큼만 메모리가 할당되는 특수한 클래스 형식)를 지원하지 않습니다.

## <a name="simple-inheritance"></a>단순 상속

둘 이상의 클래스를 클래스 다이어그램으로 끌면 클래스에는 클래스 상속 관계가 설정되고 화살표가 클래스를 연결합니다. 화살표는 기본 클래스의 방향을 가리킵니다. 예를 들어 다음 클래스가 클래스 다이어그램에 표시되면 화살표는 B에서 A를 가리키도록 클래스를 연결합니다.

```cpp
class A {};
class B : A {};
```

클래스 B만 클래스 다이어그램으로 끌어 B에 대한 클래스 모양을 마우스 오른쪽 단추로 클릭한 다음 **기본 클래스 표시**를 클릭할 수도 있습니다. 그러면 기본 클래스가 A로 표시됩니다.

## <a name="multiple-inheritance"></a>다중 상속

**클래스 디자이너**는 다중 클래스 상속 관계의 시각화를 지원합니다. *다중 상속*은 파생 클래스에 둘 이상의 기본 클래스의 특성이 있을 때 사용됩니다. 다음은 다중 상속의 예입니다.

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

둘 이상의 클래스를 클래스 다이어그램으로 끌면 클래스에는 다중 클래스 상속 관계가 설정되고 화살표가 클래스를 연결합니다. 화살표는 기본 클래스의 방향을 가리킵니다.

클래스 모양을 마우스 오른쪽 단추로 클릭한 다음 **기본 클래스 표시**를 클릭하면 선택한 클래스에 대한 기본 클래스가 표시됩니다.

> [!NOTE]
> C++ 코드에는 **파생 클래스 표시** 명령이 지원되지 않습니다. **클래스 뷰**로 이동하여 형식 노드를 확장하고 **파생 형식** 하위 폴더를 확장한 후 해당 형식을 클래스 다이어그램으로 끌어 파생 클래스를 표시할 수 있습니다.

다중 클래스 상속에 대한 자세한 내용은 [다중 상속](https://msdn.microsoft.com/library/6td5yws2.aspx) 및 [다중 기본 클래스](/cpp/cpp/multiple-base-classes)를 참조하세요.

## <a name="abstract-classes"></a>추상 클래스

**클래스 디자이너**는 추상 클래스(“추상 기본 클래스” 라고도 함)를 지원합니다. 추상 클래스는 인스턴스화하지는 않고 여기에서 다른 클래스를 파생할 수는 있는 클래스입니다. 이 문서 앞부분에 있는 “다중 상속”의 예제를 사용하여 `Bird` 클래스를 개별 개체로 인스턴스화할 수 있습니다.

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

그러나 `Swimmer` 클래스를 개별 개체로 인스턴스화하지 않을 수도 있습니다. 예를 들어 `Penguin`, `Whale`, `Fish`와 같은 동물 클래스 형식만 파생할 수 있습니다. 이 경우에는 `Swimmer` 클래스를 추상 기본 클래스로 선언할 것입니다.

클래스를 추상으로 선언하려면 `abstract` 키워드를 사용할 수 있습니다. abstract로 표시되거나 추상 클래스에 포함된 멤버는 가상의 멤버이며, 추상 클래스에서 파생된 클래스에 의해 구현되어야 합니다.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

순수 가상 함수를 하나 이상 포함하여 클래스를 abstract로 선언할 수도 있습니다.

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

이러한 선언을 클래스 다이어그램에 표시하면 클래스 이름 `Swimmer` 및 그 순수 가상 함수 `swim`은 **추상 클래스**라는 표기와 함께 가상 클래스 모양에 기울임꼴로 표시됩니다. 추상 클래스 형식 모양은 테두리가 점선인 점을 제외하고 일반 클래스와 동일합니다.

추상 기본 클래스에서 파생 클래스는 기본 클래스의 각 순수 가상 함수를 재정의해야 합니다. 그렇지 않으면 파생 클래스를 인스턴스화할 수 없습니다. 따라서 예를 들어 `Swimmer` 클래스에서 `Fish` 클래스를 파생하면 `Fish`가 `swim` 메서드를 재정의해야 합니다.

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

이 코드를 클래스 다이어그램에 표시하면 **클래스 디자이너**는 `Fish`에서 `Swimmer`까지 상속 선을 그립니다.

## <a name="anonymous-classes"></a>익명 클래스

**클래스 디자이너**는 익명 클래스를 지원합니다. *익명 클래스 형식*은 식별자 없이 선언된 클래스입니다. 익명 클래스는 생성자나 소멸자를 가질 수 없고, 인수로서 함수에 전달될 수 없으며, 함수에서 반환 값으로서 반환될 수 없습니다. 다음 예제와 같이 익명 클래스를 사용하여 클래스 이름을 Typedef 이름으로 바꿀 수 있습니다.

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

구조체는 익명일 수도 있습니다. **클래스 디자이너**는 익명 클래스와 구조체를 해당 형식을 표시할 때와 같이 표시합니다. 익명 클래스와 구조체를 선언하고 표시할 수 있지만 **클래스 디자이너**는 사용자가 지정한 태그 이름을 사용하지 않습니다. 클래스 뷰가 생성하는 이름을 사용합니다. 클래스 또는 구조체는 클래스 뷰 및 **클래스 디자이너**에서 **__unnamed**라는 요소로 나타납니다.

익명 클래스에 대한 자세한 내용은 [익명 클래스 형식](/cpp/cpp/anonymous-class-types)을 참조하세요.

## <a name="template-classes"></a>템플릿 클래스

**클래스 디자이너**는 템플릿 클래스의 시각화를 지원합니다. 중첩된 선언도 지원합니다. 다음 표는 몇 가지 일반적인 선언을 보여 줍니다.

| Code 요소 | 클래스 디자이너 보기 |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> 템플릿 클래스 |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> 템플릿 클래스 |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> 템플릿 클래스 |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> 템플릿 클래스 |

다음 표는 부분 특수화의 몇 가지 예를 보여 줍니다.

|Code 요소|클래스 디자이너 보기|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> 템플릿 클래스|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> 템플릿 클래스|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> 템플릿 클래스|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> 템플릿 클래스|

다음 표는 부분 특수화에서 상속의 몇 가지 예를 보여 줍니다.

|Code 요소|클래스 디자이너 보기|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> 템플릿 클래스<br /><br /> `B`<br /><br /> 클래스<br /><br /> (클래스 A를 가리킴)<br /><br /> `C`<br /><br /> 클래스<br /><br /> (클래스 A를 가리킴)|

다음 표는 부분 특수화 템플릿 함수의 몇 가지 예를 보여 줍니다.

|Code 요소|클래스 디자이너 보기|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U>(+1개 오버로드)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> 템플릿 클래스<br /><br /> `B<T2>`<br /><br /> 템플릿 클래스<br /><br /> (B는 클래스 A의 **중첩 형식**에 포함됨)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> 클래스<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> 템플릿 클래스|

다음 표는 템플릿 상속의 몇 가지 예를 보여 줍니다.

|Code 요소|클래스 디자이너 보기|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> 클래스<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> 클래스<br /><br /> (B는 클래스 C의 **중첩 형식**에 포함됨)<br /><br /> `C<T>`<br /><br /> 템플릿 클래스|

다음 표는 정식 특수 클래스 연결의 몇 가지 예를 보여 줍니다.

|Code 요소|클래스 디자이너 보기|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> 클래스<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> 클래스<br /><br /> `C<T>`<br /><br /> 템플릿 클래스<br /><br /> `D`<br /><br /> 클래스<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>참고 항목

- [C++ 코드 사용](working-with-visual-cpp-code.md)
- [클래스 및 구조체](/cpp/cpp/classes-and-structs-cpp)
- [익명 클래스 형식](/cpp/cpp/anonymous-class-types)
- [다중 상속](https://msdn.microsoft.com/library/6td5yws2.aspx)
- [다중 기본 클래스](/cpp/cpp/multiple-base-classes)
- [템플릿](/cpp/cpp/templates-cpp)
