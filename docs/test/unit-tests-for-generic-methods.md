---
title: 제네릭 메서드의 단위 테스트
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2158c889aefc85c908aa9ee42d45858fd11d557e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590815"
---
# <a name="unit-tests-for-generic-methods"></a>제네릭 메서드의 단위 테스트

다른 메서드와 동일한 방식으로 제네릭 메서드의 단위 테스트를 생성할 수 있습니다. 다음 섹션에서는 제네릭 메서드의 단위 테스트를 만드는 방법에 대한 정보와 예제를 제공합니다.

## <a name="type-arguments-and-type-constraints"></a>형식 인수 및 형식 제약 조건

Visual Studio는 `MyList<T>`와 같은 제네릭 클래스의 단위 테스트를 생성하는 경우 제네릭 도우미와 테스트 메서드의 두 메서드를 생성합니다. `MyList<T>`에 하나 이상의 형식 제약 조건이 있는 경우 형식 인수가 형식 제약 조건을 모두 충족해야 합니다. 테스트 대상 제네릭 코드가 허용되는 모든 입력에 대해 예상대로 작동하는지 확인하기 위해 테스트 메서드는 테스트하려는 모든 제약 조건을 사용하여 제네릭 도우미 메서드를 호출합니다.

## <a name="examples"></a>예
다음 예제에서는 제네릭의 단위 테스트를 보여 줍니다.

- [생성된 테스트 코드 편집](#EditingGeneratedTestCode) 이 예제에는 생성된 테스트 코드와 편집된 테스트 코드의 두 섹션이 있습니다. 제네릭 메서드에서 생성된 원시 테스트 코드를 유용한 테스트 메서드로 편집하는 방법을 보여 줍니다.

- [형식 제약 조건 사용](#TypeConstraintNotSatisfied) 이 예제에서는 형식 제약 조건을 사용하는 제네릭 메서드의 단위 테스트를 보여 줍니다. 이 예제에서는 형식 제약 조건이 충족되지 않습니다.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> 예제 1: 생성된 테스트 코드 편집
이 섹션의 테스트 코드는 `SizeOfLinkedList()`라는 테스트 대상 코드 메서드를 테스트합니다. 이 메서드는 연결된 목록의 노드 수를 지정하는 정수를 반환합니다.

생성된 테스트 코드 섹션의 첫 번째 코드 샘플은 Visual Studio Enterprise에서 생성된 편집하지 않은 테스트 코드를 보여 줍니다. 편집된 테스트 코드 섹션의 두 번째 샘플은 두 가지 데이터 형식 `int` 및 `char`에 대해 SizeOfLinkedList 메서드의 기능을 테스트하도록 만드는 방법을 보여 줍니다.

이 코드는 다음 두 개의 메서드를 보여 줍니다.

- 테스트 도우미 메서드, `SizeOfLinkedListTestHelper<T>()`. 기본적으로 테스트 도우미 메서드의 이름은 "TestHelper"입니다.

- 테스트 메서드, `SizeOfLinkedListTest()`. 모든 테스트 메서드는 TestMethod 특성으로 표시됩니다.

#### <a name="generated-test-code"></a>생성된 테스트 코드
다음 테스트 코드는 `SizeOfLinkedList()` 메서드에서 생성된 것입니다. 편집하지 않은 생성된 테스트이기 때문에 SizeOfLinkedList 메서드를 올바르게 테스트하도록 수정해야 합니다.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T); // TODO: Initialize to an appropriate value
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value
    int expected = 0; // TODO: Initialize to an appropriate value
    int actual;
    actual = target.SizeOfLinkedList();
    Assert.AreEqual(expected, actual);
    Assert.Inconclusive("Verify the correctness of this test method.");
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
   SizeOfLinkedListTestHelper<GenericParameterHelper>();
}
```

앞의 코드에서 제네릭 형식 매개 변수는 `GenericParameterHelper`입니다. 다음 예제와 같이 특정 데이터 형식을 제공하도록 편집할 수도 있지만, 이 문을 편집하지 않고 테스트를 실행할 수 있습니다.

#### <a name="edited-test-code"></a>편집된 테스트 코드
다음 코드에서는 테스트 메서드 및 테스트 도우미 메서드가 테스트 대상 코드 메서드 `SizeOfLinkedList()`를 성공적으로 테스트하도록 편집되었습니다.

##### <a name="test-helper-method"></a>테스트 도우미 메서드
테스트 도우미 메서드는 1단계부터 5단계까지의 레이블이 지정된 코드 줄에 해당하는 다음 단계를 수행합니다.

1. 연결된 제네릭 목록을 만듭니다.

2. 연결된 목록에 4개의 노드를 추가합니다. 이러한 노드 내용의 데이터 형식은 알 수 없습니다.

3. 연결된 목록의 예상 크기를 `expected` 변수에 할당합니다.

4. 연결된 목록의 실제 크기를 계산하고 `actual` 변수에 할당합니다.

5. Assert 문에서 `actual`과 `expected`를 비교합니다. actual이 expected와 같지 않으면 테스트가 실패합니다.

##### <a name="test-method"></a>테스트 메서드
테스트 메서드는 SizeOfLinkedListTest라는 테스트를 실행할 때 호출되는 코드로 컴파일됩니다. 6단계와 7단계로 레이블이 지정된 코드 줄에 해당하는 다음 단계를 수행합니다.

1. 테스트 도우미 메서드를 호출할 때 `<int>`를 지정하여 `integer` 변수에 대해 테스트가 작동하는지 확인합니다.

2. 테스트 도우미 메서드를 호출할 때 `<char>`를 지정하여 `char` 변수에 대해 테스트가 작동하는지 확인합니다.

```csharp
public void SizeOfLinkedListTestHelper<T>()
{
    T val = default(T);
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1
    for (int i = 0; i < 4; i++) // step 2
    {
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);
        target.Append(newNode);
    }
    int expected = 5; // step 3
    int actual;
    actual = target.SizeOfLinkedList(); // step 4
    Assert.AreEqual(expected, actual); // step 5
}

[TestMethod()]
public void SizeOfLinkedListTest()
{
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> SizeOfLinkedListTest 테스트를 실행할 때마다 해당 TestHelper 메서드가 두 번 호출됩니다. 테스트에 성공하려면 assert 문이 항상 true로 평가되어야 합니다. 테스트에 실패할 경우 실패 원인이 `<int>`를 지정한 호출 때문인지 또는 `<char>`를 지정한 호출 때문인지 명확하지 않을 수 있습니다. 대답을 찾기 위해 호출 스택을 검사하거나, 테스트 메서드에 중단점을 설정한 후 테스트를 실행하는 동안 디버그할 수 있습니다. 자세한 내용은 [방법: ASP.NET 솔루션에서 테스트를 실행하는 동안 디버그](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b)를 참조하세요.

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> 예제 2: 형식 제약 조건 사용
이 예제에서는 충족되지 않은 형식 제약 조건을 사용하는 제네릭 메서드의 단위 테스트를 보여 줍니다. 첫 번째 섹션에서는 테스트 대상 코드 프로젝트의 코드를 보여 줍니다. 형식 제약 조건이 강조 표시됩니다.

두 번째 섹션에서는 테스트 프로젝트의 코드를 보여 줍니다.

#### <a name="code-under-test-project"></a>테스트 프로젝트 대상 코드

```csharp
using System;
using System.Linq;
using System.Collections.Generic;
using System.Text;

namespace ClassLibrary2
{
    public class Employee
    {
        public Employee(string s, int i)
        {
        }
    }

    public class GenericList<T> where T : Employee
    {
        private class Node
        {
            private T data;
            public T Data
            {
                get { return data; }
                set { data = value; }
            }
        }
    }
}
```

#### <a name="test-project"></a>테스트 프로젝트

새로 생성된 모든 단위 테스트와 마찬가지로, 이 단위 테스트에 결과 불충분이 아닌 Assert 문을 추가하여 유용한 결과를 반환하도록 해야 합니다. TestMethod 특성으로 표시된 메서드가 아니라 "TestHelper" 메서드에 추가합니다. 이 테스트의 경우 `DataTestHelper<T>()`로 이름이 지정되었습니다.

이 예제에서는 제네릭 형식 매개 변수 `T`에 `where T : Employee` 제약 조건이 있습니다. 이 제약 조건은 테스트 메서드에서 충족되지 않습니다. 따라서 `DataTest()` 메서드에는 `T`에 배치된 형식 제약 조건을 요구 사항에 제공하도록 경고하는 Assert 문이 포함되어 있습니다. 이 Assert 문의 메시지는 다음과 같습니다. `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

즉, 테스트 메서드 `DataTest()`에서 `DataTestHelper<T>()` 메서드를 호출하는 경우 `Employee` 형식의 매개 변수 또는 `Employee`에서 파생 클래스를 전달해야 합니다.

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
{
    [TestClass()]
    public class GenericList_NodeTest
    {

        public void DataTestHelper<T>()
            where T : Employee
        {
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value
            T expected = default(T); // TODO: Initialize to an appropriate value
            T actual;
            target.Data = expected;
            actual = target.Data;
            Assert.AreEqual(expected, actual);
            Assert.Inconclusive("Verify the correctness of this test method.");
        }

        [TestMethod()]
        public void DataTest()
        {
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +
            "Please call DataTestHelper<T>() with appropriate type parameters.");
        }
    }
}
```

## <a name="see-also"></a>참고 항목

- [코드 단위 테스트](../test/unit-test-your-code.md)
