---
title: 정적 도우미 클래스 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Static helper classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5010761213cf79756cf8da3d2fffe60dd0b61efd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79306988"
---
# <a name="static-helper-classes"></a>정적 도우미 클래스

IntelliTest는 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)를 작성할 때 사용할 수 있는 정적 도우미 클래스 집합을 제공합니다.

* [PexAssume](#pexassume): 입력에 대한 가정을 정의하는 데 사용되고 원치 않는 입력을 필터링할 때 유용합니다.
* [PexAssert](#pexassert): 테스트 프레임워크가 클래스를 제공하지 않을 경우 사용할 간단한 어설션 클래스입니다.
* [PexChoose](#pexchoose): IntelliTest가 관리하는 추가적인 테스트 입력 스트림입니다.
* [PexObserve](#pexobserve): 구체적인 값을 기록하고 필요한 경우 생성된 코드에서 유효성을 검사합니다.

일부 클래스를 통해 낮은 수준에서 IntelliTest 지각 엔진을 조작할 수 있습니다.

* [PexSymbolicValue](#pexsymbolicvalue): 변수에 대한 기호 제약 조건을 검사하거나 수정하는 유틸리티입니다.

<a name="pexassume"></a>
## <a name="pexassume"></a>PexAssume

가정(예: [매개 변수가 있는 단위 테스트](test-generation.md#precondition)의 [사전 조건](test-generation.md#parameterized-unit-testing))을 표현하는 데 사용되는 정적 클래스입니다. 이 클래스의 메서드는 부적절한 테스트 입력을 필터링하는 데 사용할 수 있습니다.

가정된 조건이 일부 테스트 입력에 적용되지 않으면 **PexAssumeFailedException**이 throw됩니다. 이로 인해 테스트가 자동으로 무시됩니다.

**예제**

다음 매개 변수가 있는 테스트에서는 **j=0**을 간주하지 않습니다.

```csharp
public void TestSomething(int i, int j) {
     PexAssume.AreNotEqual(j, 0);
     int k = i/j;
     ...
}
```

**주의**

위의 코드는 거의 다음과 같습니다.

```csharp
     if (j==0)
          return;
```

단, 실패한 **PexAssume**으로 인해 테스트 사례가 생성되지 않는 경우는 제외합니다. **if** 문의 경우 IntelliTest는 개별 테스트 사례를 생성하여 **if** 문의 **then** 분기를 검사합니다.

**PexAssume**에는 문자열, 배열 및 컬렉션에 대한 가정에 맞게 특수화된 중첩 클래스도 포함됩니다.

<a name="pexassert"></a>
## <a name="pexassert"></a>PexAssert

어설션(예: [매개 변수가 있는 단위 테스트](test-generation.md#postcondition)의 [사후 조건](test-generation.md#parameterized-unit-testing))을 표현하는 데 사용되는 정적 클래스입니다.

어설션된 조건이 일부 테스트 입력에 적용되지 않으면 **PexAssertFailedException**이 throw되어 테스트가 실패합니다.

**예제**

다음은 정수의 절대 값이 양수가 되도록 어설션합니다.

```csharp
public void TestSomething(int i) {
     int j = Maths.Abs(i);
     PexAssert.IsTrue(j >= 0);
     ...
}
```

<a name="pexchoose"></a>
## <a name="pexchoose"></a>PexChoose

테스트에 보조 입력 값을 제공하며 [매개 변수가 있는 모의 개체](input-generation.md#parameterized-mocks)를 구현하는 데 사용할 수 있는 정적 클래스입니다.

**PexChoose** 클래스는 특정 입력 값에 대해 테스트가 통과하는지 아니면 실패하는지를 확인하는 데 사용할 수 없습니다. **PexChoose**는 *선택 항목*이라고도 하는 입력 값만을 제공합니다. 사용자는 입력 값을 제한해야 하며 테스트 통과 또는 실패를 정의하는 어설션을 작성해야 합니다.

**작동 모드**

**PexChoose** 클래스는 두 가지 모드에서 작동할 수 있습니다.

* IntelliTest가 [입력 생성](input-generation.md) 중에 테스트 및 테스트된 코드의 기호 분석을 수행하는 동안 선택기는 임의 값을 반환하고 IntelliTest는 각 값이 테스트 및 테스트된 코드에서 어떻게 사용되는지 추적합니다. IntelliTest는 관련 값을 생성하여 테스트 및 테스트된 코드에서 여러 가지 실행 경로를 트리거합니다.

* 특정 테스트 사례에 대해 생성된 코드에서는 특정 방법으로 선택 항목 공급자를 설정하므로, 해당 테스트 사례를 다시 실행하면 특정 선택 항목이 특정 실행 경로를 트리거합니다.

**사용 현황**

* **PexChoose.Value**를 호출해서 새 값을 생성하면 됩니다.

```csharp
public int Foo() {
    return PexChoose.Value<int>("foo");
}
```

<a name="pexobserve"></a>
## <a name="pexobserve"></a>PexObserve

명명된 값을 기록하기 위한 정적 클래스입니다.

IntelliTest가 코드를 탐색할 때 **PexObserve**는 형식 문자열 표현으로 계산된 값을 기록하는 데 사용됩니다. 이 값은 고유한 이름과 연결됩니다.

```csharp
PexObserve.Value<string>("result", result);
```

**예제**

```csharp
// product code
public static class MathEx {
     public static int Square(int value) { return value * value; }
}

// fixture
[TestClass]
public partial class MathExTests {
     [PexMethod]
     public int SquareTest(int a) {
        int result = MathEx.Square(a);
        // storing result
        return result;
     }
}
```

<a name="pexsymbolicvalue"></a>
## <a name="pexsymbolicvalue"></a>PexSymbolicValue

매개 변수에 대한 제약 조건을 무시하고 값과 연결된 기호 정보를 인쇄하는 데 사용되는 정적 클래스입니다.

**사용 현황**

일반적으로 IntelliTest는 실행 중에 코드의 모든 실행 경로를 검사하려고 시도합니다. 그러나 특히 가정 및 어설션 조건을 계산할 경우에는 일부 가능한 사례를 탐색하면 안 됩니다.

**예제**

이 예제에서는 **PexAssume.Arrays.ElementsAreNotNull** 메서드의 구현을 보여 줍니다.
이 메서드에서는 배열 값 길이에 대한 제약 조건을 무시하여 IntelliTest가 다양한 크기의 배열을 생성하지 않도록 합니다. 제약 조건은 여기에서만 무시됩니다. 테스트된 코드가 배열 길이에 따라 다르게 동작할 경우 IntelliTest는 테스트된 코드의 제약 조건에서 다양한 크기의 배열을 생성할 수 없습니다.

```csharp
public static void AreElementsNotNull<T>(T[] value)
    where T : class
{
    PexAssume.NotNull(value);
    // the followings prevents the exploration of all array lengths
    int len = PexSymbolicValue.Ignore<int>(value.Length);

    // building up a boolean value as follows prevents exploration
    // of all combinations of non-null (instead, there are just two cases)
    bool anyNull = false;
    for (int i = 0; i < len; ++i)
        anyNull |= value[i] == null;

    // was any element null?
    if (anyNull)
        PexAssume.Fail("some element of array is a null reference");
}
```

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
