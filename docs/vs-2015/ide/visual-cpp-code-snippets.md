---
title: Visual C++ 코드 조각 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 213f4299ac71c08118563a008abe065f2c02423e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655399"
---
# <a name="visual-c-code-snippets"></a>Visual C# 코드 조각
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 코드 조각을 사용하여 일반적으로 사용되는 코드를 C++ 코드 파일에 추가할 수 있습니다. 일반적으로 C#에서와 거의 같은 방법으로 코드 조각을 사용하지만 기본 코드 조각 집합은 서로 다릅니다.

 코드의 특정 위치에 코드 조각을 추가하거나(삽입) 몇몇 선택된 코드를 코드 조각으로 감쌀 수 있습니다.

## <a name="inserting-a-code-snippet"></a>코드 조각 삽입
 코드 조각을 삽입하려면 C++ 코드 파일(.cpp or .h)을 열고, 파일 내에서 아무 곳이나 클릭하고, 다음의 하나를 수행합니다.

- 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 표시하고 **코드 조각 삽입**을 선택합니다.

- **편집/IntelliSense** 메뉴에서 **코드 조각 삽입**을 선택합니다.

- 바로 가기 키 **Ctrl+K+X**를 사용합니다.

  **#if**로 시작하는 선택 항목 목록이 표시되어야 합니다. **#if**를 선택하면 다음 코드가 파일에 추가됩니다.

```cpp
#if 0

#endif // 0
```

 0을 올바른 조건으로 바꿀 수 있습니다.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>코드 조각을 사용하여 선택한 코드 감싸기
 코드 조각을 사용하여 선택한 코드를 감싸려면 한 줄이나 여러 줄을 선택하고 다음의 하나를 수행합니다.

1. 마우스 오른쪽 단추를 클릭 하 여 상황에 맞는 메뉴를 가져오고 **코드 감싸기** 를 선택 합니다.

2. **편집/IntelliSense** 메뉴에서 **코드 감싸기**를 선택합니다.

3. 바로 가기 키 **Ctrl+K+S**를 사용합니다.

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
 **class** 코드 조각은 MyClass 클래스의 정의를 해당하는 기본 생성자 및 소멸자와 함께 제공합니다. 여기서 생성자와 소멸자는 클래스 외부에 있습니다.

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

 classi 코드 조각도 MyClass 클래스의 정의를 제공하지만 기본 생성자 및 소멸자는 클래스 정의 내부에 정의됩니다.

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

## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>for, foreach, forr 및 rfor
 다양한 for 루프를 제공하는 네 가지 조각이 있습니다.

 **For** 코드 조각은 `for` 조건이 개체의 길이 (의)를 기반으로 하는 루프를 제공 합니다 `size_t` .

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

 **foreach** 코드 조각은 컬렉션의 멤버를 반복하는 `for each` 루프를 제공합니다.

```cpp
for each (object var in collection_to_loop)
{

}
```

 **Forr** 코드 조각은 `for` 조건이 개체의 길이 (정수)를 기반으로 하는 역방향 루프를 제공 합니다.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

 **Rfor** 코드 조각은 [범위 기반](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) for 루프 (링크)를 제공 합니다.

```cpp
for (auto& i : v)
{

}
```

## <a name="the-destructor-snippet-"></a>소멸자 조각(~)
 소멸자 코드 조각( **~** )은 다양한 컨텍스트에서 다양한 동작을 보여 줍니다. 이 조각을 클래스 내부에 삽입하면 이 조각이 해당 클래스에 대한 소멸자를 제공합니다. 예를 들어, 다음과 같이 코드를 가정합니다.

```cpp
class SomeClass {

};
```

 소멸자 조각을 삽입하면 이 조각이 SomeClass에 대한 소멸자를 제공합니다.

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
