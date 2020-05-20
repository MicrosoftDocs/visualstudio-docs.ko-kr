---
title: Visual C++ 코드 조각
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: db6ea1e233d32872322926a4d75b847ee6a49ba3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77277832"
---
# <a name="visual-c-code-snippets"></a>Visual C++ 코드 조각

Visual Studio에서 코드 조각을 사용하여 일반적으로 사용되는 코드를 C++ 코드 파일에 추가할 수 있습니다. 일반적으로 C#에서와 거의 같은 방법으로 코드 조각을 사용하지만 기본 코드 조각 집합은 서로 다릅니다.

코드의 특정 위치에 코드 조각을 추가하거나(삽입) 몇몇 선택된 코드를 코드 조각으로 감쌀 수 있습니다.

## <a name="insert-a-code-snippet"></a>코드 조각 삽입

코드 조각을 삽입하려면 C++ 코드 파일( *.cpp* 또는 *.h*)을 열고, 파일 내에서 아무 곳이나 클릭하고, 다음의 하나를 수행합니다.

- 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 표시하고 **코드 조각 삽입**을 선택합니다.

- **편집/IntelliSense** 메뉴에서 **코드 조각 삽입**을 선택합니다.

- 바로 가기 키 사용: **Ctrl**+**K**+**X**

**#if**로 시작하는 선택 항목 목록이 표시되어야 합니다. **#if**를 선택하면 다음 코드가 파일에 추가됩니다.

```cpp
#if 0

#endif // 0
```

**0**을 올바른 조건으로 바꿀 수 있습니다.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>코드 조각을 사용하여 선택한 코드 감싸기

코드 조각을 사용하여 선택한 코드를 감싸려면 한 줄이나 여러 줄을 선택하고 다음의 하나를 수행합니다.

- 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 표시하고 **코드 감싸기**를 선택

- **편집** > **IntelliSense** 메뉴에서 **코드 감싸기**를 선택

- 키보드를 사용하여 누름: **Ctrl**+**K**+**S**

**#if**를 선택합니다. 다음과 유사한 결과가 표시됩니다.

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

0을 올바른 조건으로 바꿀 수 있습니다.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>C++ 코드 조각의 전체 목록이 있는 위치

C++ 코드 조각의 전체 목록을 찾으려면 **도구** 메뉴에서 **코드 조각 관리자**로 이동하고 **언어**를 **Visual C++** 로 설정합니다. 아래 창에서 **Visual C++** 를 확장합니다. 모든 C++ 코드 조각의 이름이 사전순으로 표시되어야 합니다.

대부분 코드 조각의 이름은 이름 자체로 설명되지만 일부 이름은 혼동될 수 있습니다.

## <a name="class-vs-classi"></a>class 및 classi

**class** 코드 조각은 `MyClass` 클래스의 정의를 해당하는 기본 생성자 및 소멸자와 함께 제공합니다. 여기서 생성자와 소멸자는 클래스 외부에 있습니다.

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

**classi** 코드 조각도 `MyClass` 클래스의 정의를 제공하지만 기본 생성자 및 소멸자는 클래스 정의 내부에 정의됩니다.

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>for, forr 및 rfor

다양한 `for` 루프를 제공하는 세 가지 **for** 코드 조각이 있습니다.

**rfor** 코드 조각은 [범위 기반](/cpp/cpp/range-based-for-statement-cpp) for 루프(링크)를 제공합니다. 이 구문은 인덱스 기반 `for` 루프보다 선호됩니다.

```cpp
for (auto& i : v)
{

}
```

**for** 코드 조각은 조건이 개체의 길이(`size_t`)에 기반을 둔 `for` 루프를 제공합니다.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**forr** 코드 조각은 조건이 개체의 길이(정수)에 기반을 둔 역방향 `for` 루프를 제공합니다.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>소멸자 조각(~)

소멸자 코드 조각( **~** )은 다양한 컨텍스트에서 다양한 동작을 보여 줍니다. 이 조각을 클래스 내부에 삽입하면 이 조각이 해당 클래스에 대한 소멸자를 제공합니다. 예를 들어, 다음과 같이 코드를 가정합니다.

```cpp
class SomeClass {

};
```

소멸자 조각을 삽입하면 이 조각이 `SomeClass`에 대한 소멸자를 제공합니다.

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

클래스 외부에서 소멸자 조각을 삽입하려고 하면 이 조각이 자리 표시자 이름으로 소멸자를 제공합니다.

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>참고 항목

- [코드 조각](../ide/code-snippets.md)