---
title: 개요 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5eb619269dfd8922919999249b4ced0b9b98ebb7
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256207"
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft IntelliTest 개요

IntelliTest를 사용하면 초기에 버그를 찾을 수 있으므로 테스트 유지 관리 비용이 감소합니다. 자동화 및 투명 테스트 방법을 사용하는 IntelliTest는 .NET 코드에 대한 후보 테스트 도구 모음을 생성할 수 있습니다. 테스트 도구 모음 생성은 지정하는 *정확성 속성*에 따라 추가로 안내될 수 있습니다. IntelliTest는 테스트 중인 코드가 발전함에 따라 자동으로 테스트 도구 모음을 발전시키기도 합니다.

**특성 테스트** IntelliTest를 사용하여 기존 단위 테스트의 도구 모음을 기준으로 코드 동작을 결정할 수 있습니다.
이런 테스트 도구 모음은 리팩터링 레거시 또는 익숙하지 않은 코드와 연결된 복잡성을 처리하기 위한 기반을 형성하는 재발 도구 모음으로 사용될 수 있습니다.

**단계별 테스트 입력 생성** IntelliTest는 공개 코드 분석 및 제약 조건 해결 방법을 사용하여 정확한 테스트 입력 값을 자동으로 생성합니다. 대개 사용자가 개입할 필요가 없습니다. 복합 개체 형식의 경우 자동으로 팩터리를 생성합니다. 요구 사항에 맞게 팩터리를 확장하고 구성하여 테스트 입력 생성을 제어할 수 있습니다. 코드의 어설션으로 지정된 정확성 속성도 테스트 입력 생성을 추가로 제어하는 데 자동으로 사용됩니다.

**IDE 통합** IntelliTest는 Visual Studio IDE에 완벽하게 통합됩니다. 테스트 도구 모음 생성 중에 수집된 모든 정보(예: 자동 생성된 입력, 코드의 출력, 생성된 테스트 사례 및 통과 또는 실패 상태)가 Visual Studio IDE 내에 표시됩니다. Visual Studio IDE를 떠나지 않고 코드 수정과 IntelliTest 재실행 간에 쉽게 반복할 수 있습니다.
테스트는 솔루션에 단위 테스트 프로젝트로 저장되고 나중에 Visual Studio 테스트 탐색기를 통해 자동으로 검색됩니다.

**기존 테스트 사례 보완** IntelliTest를 사용하여 이미 따르고 있는 기존 테스트 사례를 보완합니다.

테스트 대상:

* 기본 형식 데이터에 대한 알고리즘 또는 기본 형식 데이터 배열:
  * [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)를 작성합니다.
* 복잡한 데이터에 대한 알고리즘(예: 컴파일러):
  * IntelliTest가 먼저 데이터의 추상 표현을 생성하고 나서 알고리즘에 공급하도록 합니다.
  * IntelliTest가 [사용자 지정 개체 만들기](input-generation.md#objects)와 데이터 고정을 사용하여 인스턴스를 빌드하고 나서 알고리즘을 호출하도록 합니다.
* 데이터 컨테이너:
  * [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)를 작성합니다.
  * IntelliTest가 [사용자 지정 개체 만들기](input-generation.md#objects)와 데이터 고정을 사용하여 인스턴스를 빌드하고 나서 컨테이너의 메서드를 호출하고 나중에 고정을 다시 확인하도록 함
  * 매개 변수 값에 따라 다양한 구현 메서드를 호출하는 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)를 작성합니다.
* 기존 코드베이스:
  * Visual Studio의 IntelliTest 마법사를 사용하여 먼저 [PUT(매개 변수가 있는 단위 테스트)](test-generation.md#parameterized-unit-testing) 집합을 생성합니다.

## <a name="the-hello-world-of-intellitest"></a>IntelliTest의 Hello World

IntelliTest는 테스트된 프로그램과 관련된 입력을 찾습니다. 즉, IntelliTest를 사용하여 유명한 **Hello World!** 문자열을 생성할 수 있습니다. 이 경우 C# MSTest 기반 테스트 프로젝트를 만들고 **Microsoft.Pex.Framework**에 대한 참조를 추가했다고 가정합니다. 다른 테스트 프레임워크를 사용할 경우에는 C# 클래스 라이브러리를 만들고 프로젝트 설정 방법에 대한 테스트 프레임워크 설명서를 참조하세요.

다음 예제에서는 IntelliTest가 필요한 문자열을 생성하도록 **값** 매개 변수에 대한 두 가지 제약 조건을 만듭니다.

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

컴파일 및 실행이 완료되면 IntelliTest는 다음과 같은 테스트 집합을 생성합니다.

1. ""
2. "\0\0\0\0\0"
3. "Hello"
4. "\0\0\0\0\0\0"
5. "Hello\0"
6. "Hello\0\0"
7. "Hello\0World!"
8. "Hello World!"

> [!NOTE]
> 빌드 문제가 발생할 경우 Microsoft.VisualStudio.TestPlatform.TestFramework 및 Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions 참조를 Microsoft.VisualStudio.QualityTools.UnitTestFramework 참조로 바꿔보세요.

[IntelliTest를 사용하여 단위 테스트 생성](../../test/generate-unit-tests-for-your-code-with-intellitest.md)을 읽고 생성된 테스트가 어디에 저장되는지 이해합니다. 생성된 테스트 코드에는 다음 코드와 같은 테스트가 포함되어야 합니다.

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

너무나 쉽습니다!

추가 리소스:
  * [Channel 9 동영상](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest) 보기
  * 이 [MSDN Magazine 개요](https://msdn.microsoft.com/magazine/dn904672.aspx) 읽기

## <a name="important-attributes"></a>중요한 특성

* [PexClass](attribute-glossary.md#pexclass)는 **PUT**가 포함된 형식을 표시합니다.
* [PexMethod](attribute-glossary.md#pexmethod)는 **PUT**를 표시합니다.
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)은 null이 아닌 매개 변수를 표시합니다.

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)는 테스트 프로젝트를 프로젝트에 바인딩합니다.
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute)는 계측할 어셈블리를 지정합니다.

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> 중요한 정적 도우미 클래스

* [PexAssume](static-helper-classes.md#pexassume)은 가정을 평가합니다(입력 필터링).
* [PexAssert](static-helper-classes.md#pexassert)는 어설션을 평가합니다.
* [PexChoose](static-helper-classes.md#pexchoose)는 새 선택 항목을 생성합니다(추가 입력).
* [PexObserve](static-helper-classes.md#pexobserve)는 생성된 테스트에 대한 라이브 값을 기록합니다.

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>제한 사항

이 섹션에서는 IntelliTest의 제한 사항을 설명합니다.

* [비결정성](#nondeterminism)
* [동시성](#concurrency)
* [네이티브 .NET 코드](#native-code)
* [플랫폼](#platform)
* [언어](#language)
* [상징적 지각](#symbolic-reasoning)
* [스택 추적](#incorrect-stack-traces)

### <a name="nondeterminism"></a>비결정성

IntelliTest는 분석된 프로그램이 결정적이라고 가정합니다. 결정적이 아닌 경우 IntelliTest는 탐색 경계에 도달할 때까지 순환합니다.

IntelliTest는 프로그램이 IntelliTest에서 제어할 수 없는 입력에 의존할 경우 비결정적이라고 간주합니다.

IntelliTest는 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)에 제공되고 [PexChoose](static-helper-classes.md#pexchoose)에서 가져오는 입력을 제어합니다.
그런 면에서 관리되지 않거나 계측되지 않는 코드에 대한 호출의 결과도 계측된 프로그램에 대한 “입력”으로 간주하지만 IntelliTest가 해당 입력을 제어할 수 없습니다. 프로그램의 제어 흐름이 이러한 외부 소스에서 생성되는 특정 값에 의존할 경우 IntelliTest는 프로그램을 이전에 검사된 영역으로 “이동”할 수 없습니다.

또한 프로그램을 다시 실행할 때 외부 소스의 값이 변경될 경우 프로그램을 비결정적으로 간주합니다. 이 경우 IntelliTest가 프로그램 실행을 제어할 수 없어서 해당 검색은 비효율적인 것이 됩니다.

때때로 언제 이 문제가 발생하는지가 분명하지 않습니다. 다음 예제를 살펴보세요.

* **GetHashCode()** 메서드의 결과가 비관리 코드에 의해 제공되고 예측할 수 없습니다.
* **System.Random** 클래스가 현재 시스템 시간을 사용하여 실제로 무작위 값을 제공합니다.
* **System.DateTime** 클래스가 IntelliTest가 제어하지 않는 현재 시간을 제공합니다.

### <a name="concurrency"></a>동시성

IntelliTest는 다중 스레드 프로그램을 처리하지 않습니다.

### <a name="native-code"></a>네이티브 코드

IntelliTest는 **P/Invoke**를 통해 호출된 x86 명령 등의 네이티브 코드를 인식하지 못합니다. IntelliTest에는 해당 호출을 [제약 조건 해결기](input-generation.md#constraint-solver)에 전달될 수 있는 제약 조건으로 변환하는 방법이 없습니다.
.NET 코드의 경우에도 직접 계측하는 코드를 분석만할 수 있습니다. IntelliTest는 리플렉션 라이브러리를 비롯하여 **mscorlib**의 특정 부분을 계측할 수 없습니다. **DynamicMethod**를 계측할 수 없습니다.

제안된 해결 방법은 해당 메서드가 동적 어셈블리의 형식으로 배치되는 테스트 모드를 포함하는 것입니다. 그러나 일부 메서드가 계측되지 않더라도 IntelliTest는 가능한 한 많은 계측된 코드를 검사하려고 시도합니다.

### <a name="platform"></a>플랫폼

IntelliTest는 X86, 32비트 .NETframework에서만 지원됩니다.

### <a name="language"></a>언어

원칙적으로 IntelliTest는 모든 .NET 언어로 작성된 임의 .NET 프로그램을 분석할 수 있습니다. 그러나 Visual Studio에서는 C#만 지원합니다.

### <a name="symbolic-reasoning"></a>상징적 지각

IntelliTest는 자동 [제약 조건 해결기](input-generation.md#constraint-solver)를 사용하여 테스트 및 테스트 중인 프로그램에 대한 관련 값을 결정합니다. 그러나 제약 조건 해결기의 기능은 제한됩니다.

### <a name="incorrect-stack-traces"></a>잘못된 스택 추적

IntelliTest는 각 계측된 메서드에서 예외를 catch하고 “rethrow”(다시 throw)하므로 스택 추적의 줄 번호가 정확하지 않습니다. 이것은 “rethrow” 명령의 의도적인 제한 사항입니다.

## <a name="further-reading"></a>추가 정보

* [소개 블로그 게시물](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [IntelliTest를 사용하여 코드에 대한 단위 테스트 생성](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
