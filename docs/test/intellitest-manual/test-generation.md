---
title: 테스트 생성 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c251a1539b42da2b4e92c2996457075f3c3be135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315176"
---
# <a name="test-generation"></a>테스트 생성

기존 유닛 테스트에서 테스트는 몇 가지 항목으로 구성됩니다.

* [메서드 호출의 시퀀스](test-generation.md#test-generators)
* 메서드와 함께 호출된 인수, 인수는 [테스트 입력](input-generation.md)입니다.
* [어설션](#assumptions-and-assertions) 집합을 명시하여 테스트된 애플리케이션의 의도한 동작에 대한 유효성 검사

다음은 예제 테스트 구조입니다.

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest는 메서드 호출 및 어설션의 시퀀스를 제공하는 더욱 일반적인 [매개 변수가 있는 단위 테스트](#parameterized-unit-testing)에 대한 관련 인수 값을 자동으로 결정할 수 있습니다.

<a name="test-generators"></a>
## <a name="test-generators"></a>테스트 생성기

IntelliTest는 실행할 테스트에서 구현의 메서드 시퀀스를 선택하고 파생 데이터에 대한 어설션을 확인하는 동안 메서드에 대한 입력을 생성하는 방식으로 테스트 사례를 생성합니다.

[매개 변수가 있는 단위 테스트](#parameterized-unit-testing)는 본문에 메서드 호출의 시퀀스를 직접 명시합니다.

IntelliTest에서 개체를 생성해야 할 경우 필요에 따라 생성자 및 팩터리 메서드 호출이 자동으로 시퀀스에 추가됩니다.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>매개 변수가 있는 유닛 테스트

PUT(*매개 변수가 있는 단위 테스트*)는 매개 변수를 사용하는 테스트입니다. 일반적으로 폐쇄형 메서드인 기존 단위 테스트와 달리 PUT는 모든 매개 변수 집합을 사용합니다. 그렇게 간단한가요? 예 - 기존 테스트에서는 IntelliTest가 테스트에서 도달할 수 있는 코드를 [완전히 검사](input-generation.md#dynamic-code-coverage)하는 [(최소) 입력 집합을 생성](input-generation.md)하려고 합니다.

PUT는 MSTest(또는 NUnit, xUnit)와 비슷한 방식으로 [PexMethod](attribute-glossary.md#pexmethod) 사용자 지정 특성을 사용하여 정의됩니다. PUT는 [PexClass](attribute-glossary.md#pexclass) 태그가 지정된 클래스에서 논리적으로 그룹화되는 인스턴스 메서드입니다. 다음 예제에서는 **MyPexTest** 클래스에 저장된 간단한 PUT를 보여 줍니다.

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

여기서 **ReplaceFirstChar**은 문자열의 첫 번째 문제를 바꾸는 메서드입니다.

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

이 테스트에서 IntelliTest는 테스트된 코드의 많은 실행 경로를 검사하는 PUT에 대한 [입력을 자동으로 생성](input-generation.md)할 수 있습니다. 다른 실행 경로를 검사하는 각 입력은 단위 테스트로 “직렬화”됩니다.

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>제네릭 매개 변수가 있는 유닛 테스트

매개 변수가 있는 단위 테스트는 제네릭 메서드일 수 있습니다. 이 경우 사용자는 [PexGenericArguments](attribute-glossary.md#pexgenericarguments)를 사용하여 메서드를 인스턴스화하는 데 사용되는 형식을 지정해야 합니다.

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>예외 허용

IntelliTest는 예외를 예상된 예외 및 예기치 않은 예외로 심사하는 데 유용한 다양한 유효성 검사 특성을 제공합니다.

예상된 예외는 ***ExpectedException(typeof(* xxx**))와 같은 적절한 주석과 함께 부정적인 테스트 사례를 생성하지만, 예기치 않은 예외는 실패한 테스트 사례를 생성합니다.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

유효성 검사기는 다음과 같습니다.

* [PexAllowedException](attribute-glossary.md#pexallowedexception): 모든 위치의 특정 예외 형식을 허용합니다.
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): 지정된 어셈블리의 특정 예외 형식을 허용합니다.
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): 지정된 형식의 특정 예외 형식을 허용합니다.
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): 테스트 중인 형식의 특정 예외 형식을 허용합니다.

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>internal 형식 테스트

IntelliTest는 볼 수 있는 internal 형식을 “테스트”할 수 있습니다. IntelliTest가 형식을 볼 수 있도록 Visual Studio IntelliTest 마법사를 통해 다음 특성이 제품 또는 테스트 프로젝트에 추가됩니다.

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>가정 및 어설션

사용자는 가정 및 어설션을 사용하여 테스트에 대한 [사전 조건](#precondition)(가정) 및 [사후 조건](#postcondition)(어설션)을 표현할 수 있습니다. IntelliTest가 매개 변수 값 집합을 생성하고 코드를 “탐색”하면 테스트의 가정을 위반할 수 있습니다. 이 문제가 발생하면 IntelliTest는 해당 경로에 대한 테스트를 생성하지 않고 해당 경로를 자동으로 무시합니다.

어설션은 일반 단위 테스트 프레임워크에서 잘 알려진 개념이므로 IntelliTest는 각 지원되는 프레임워크에서 제공된 기본 제공 **Assert** 클래스를 이미 “이해”합니다. 그러나 대부분의 프레임워크는 **Assume** 클래스를 제공하지 않습니다. 이 경우 IntelliTest는 [PexAssume](static-helper-classes.md#pexassume) 클래스를 제공합니다. 기존 테스트 프레임워크를 사용하지 않을 경우에도 IntelliTest에는 [PexAssert](static-helper-classes.md#pexassert) 클래스가 있습니다.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

특히 null이 아닌 가정은 사용자 지정 특성으로 인코드할 수 있습니다.

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Precondition

메서드의 사전 조건은 메서드가 성공하는 조건을 표현합니다.

일반적으로 사전 조건을 적용하려면 매개 변수 및 개체 상태를 확인하고 위반될 경우 **ArgumentException** 또는 **InvalidOperationException**을 throw합니다.

IntelliTest에서 [매개 변수가 있는 단위 테스트](#parameterized-unit-testing)의 사전 조건은 [PexAssume](static-helper-classes.md#pexassume)을 사용하여 표현됩니다.

<a name="postcondition"></a>
## <a name="postcondition"></a>사후 조건

메서드의 사후 조건은 사전 조건이 처음에 유효했다는 가정 아래 메서드를 실행하는 동안과 그 후에 유지되어야 하는 조건을 표현합니다.

일반적으로 사후 조건은 **Assert** 메서드 호출을 통해 적용됩니다.

IntelliTest에서 [매개 변수가 있는 단위 테스트](#parameterized-unit-testing)의 사후 조건은 [PexAssert](static-helper-classes.md#pexassert)를 사용하여 표현됩니다.

<a name="test-failures"></a>
## <a name="test-failures"></a>테스트 실패
생성된 테스트 사례가 실패하는 경우는 언제인가요?

1. [구성된 경로 경계](exploration-bounds.md) 내에서 종료되지 않을 경우 [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) 옵션이 설정되지 않는 한 실패로 간주합니다.

1. 테스트에서 **PexAssumeFailedException**을 throw할 경우 테스트가 성공합니다. 그러나 일반적으로 [TestEmissionFilter](exploration-bounds.md#testemissionfilter)가 **All**로 설정된 경우가 아니면 테스트가 필터링됩니다.

1. 테스트가 [어설션](#assumptions-and-assertions)을 위반하면(예: 유닛 테스트 프레임워크의 어설션 위반 예외 throw) 테스트가 실패합니다.

위의 아무것도 의사 결정을 생성하지 않으면 예외를 throw하지 않는 경우에만 테스트가 성공합니다. 어설션 위반은 예외와 같은 방식으로 처리됩니다.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>설치 및 해체

테스트 프레임워크와 통합하는 과정의 일부로 IntelliTest는 설치 및 해제 메서드를 검색 및 실행하는 기능을 지원합니다.

**예제**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>추가 정보

* [Test to code binding](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)(테스트-코드 바인딩)
* [One test to rule them all](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)(한 번 테스트로 모두 제어)

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
