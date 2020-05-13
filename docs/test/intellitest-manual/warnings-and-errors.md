---
title: 경고 및 오류 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c3f5fe55a4e1afb1a9551d43d0d61ae9f76b81e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275442"
---
# <a name="warnings-and-errors"></a>경고 및 오류

## <a name="warnings-and-errors-by-category"></a>범주별 경고 및 오류

* **경계**
  * [MaxBranches 초과](#maxbranches-exceeded)
  * [MaxConstraintSolverTime 초과](#maxconstraintsolvertime-exceeded)
  * [MaxConditions 초과](#maxconditions-exceeded)
  * [MaxCalls 초과](#maxcalls-exceeded)
  * [MaxStack 초과](#maxstack-exceeded)
  * [MaxRuns 초과](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests 초과](#maxrunswithoutnewtests-exceeded)

* **제약 조건 해결**
  * [솔루션을 구체화할 수 없음](#cannot-concretize-solution)

* **도메인 또는 런타임**
  * [개체를 생성하는 데 도움이 필요](#help-construct)
  * [형식을 찾는 데 도움이 필요](#help-types)
  * [사용 가능한 형식 추측](#usable-type-guessed)

* **실행**
  * [탐색 중 발생한 예기치 않은 오류](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **계측**
  * [계측되지 않은 메서드 호출](#uninstrumented-method-called)
  * [외부 메서드 호출](#external-method-called)
  * [계측할 수 없는 메서드 호출](#uninstrumentable-method-called)
  * [테스트 가능성 문제](#testability-issue)
  * [제한 사항](#limitation)

* **인터프리터**
  * [관찰된 호출 불일치](#observed-call-mismatch)
  * [정적 필드에 저장된 값](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 길이를 제한합니다. 이 기능은 프로그램이 무한 루프로 들어가는 경우 IntelliTest가 응답하지 않는 문제를 방지합니다.

[매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing) 입력을 사용하지 않는 분기를 포함하여 실행 및 모니터링된 코드의 모든 조건부 및 무조건부 분기는 이 제한 계산에 포함됩니다.

예를 들어 다음 코드는 대략 100개의 분기를 사용합니다.

```csharp
for (int i=0; i<100; i++) { }
```

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxBranches](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음 예제에서는 이 경계를 효과적으로 제거합니다.

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

**TestExcludePathBoundsExceeded** 옵션을 설정하여 일반적으로 이러한 문제를 처리하는 방법을 IntelliTest에 알릴 수도 있습니다.

테스트 코드에서 [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)를 사용하여 루프 조건에서 생성된 제약 조건을 무시할 수 있습니다.

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime 초과

IntelliTest는 [제약 조건 해결기](input-generation.md#constraint-solver)를 사용하여 새 테스트 입력을 컴퓨팅합니다. 제약 조건 해결은 시간이 오래 걸리는 프로세스일 수 있으므로 IntelliTest를 사용하여 경계를 구성할 수 있습니다(특히 **MaxConstraintSolverTime**).

대부분의 애플리케이션에서는 시간 제한을 크게 늘려도 검사 성능은 향상되지 않습니다. 그 이유는 대부분의 시간 제한은 솔루션이 없는 제약 조건 시스템에서 발생하기 때문입니다. 그러나 IntelliTest는 시간 제한을 초래하는 모든 가능한 솔루션을 시도해야 일관성이 없는지 확인할 수 있습니다.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 길이를 제한합니다. 이 기능은 프로그램이 무한 루프로 들어가는 경우 IntelliTest가 응답하지 않는 문제를 방지합니다.

[매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)의 입력을 사용하는 각 조건부 분기는 이 제한 계산에 포함됩니다.

예를 들어 다음 코드의 각 경로는 **n+1**개 조건을 사용합니다.

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxConditions](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음은 그 예입니다.

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

**TestExcludePathBoundsExceeded** 옵션을 설정하여 일반적으로 이러한 문제를 처리하는 방법을 IntelliTest에 알릴 수도 있습니다.

[PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)를 사용하여 루프 조건에서 생성된 제약 조건을 무시할 수 있습니다.

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 길이를 제한합니다. 이 기능은 프로그램이 무한 루프로 들어가는 경우 IntelliTest가 응답하지 않는 문제를 방지합니다.

실행 및 모니터링된 코드의 각 호출(직접, 간접, 가상 또는 이동)은 이 제한 계산에 포함됩니다.

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxCalls](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음 예제에서는 이 경계를 효과적으로 제거합니다.

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

**TestExcludePathBoundsExceeded** 옵션을 설정하여 일반적으로 이러한 문제를 처리하는 방법을 IntelliTest에 알릴 수도 있습니다.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 호출 스택 크기를 제한합니다. 이 기능은 스택 오버플로가 발생하는 경우 IntelliTest가 종료되는 문제를 방지합니다.

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxStack](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음 예제에서는 이 경계를 효과적으로 제거합니다(권장되지 않음).

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

**TestExcludePathBoundsExceeded** 옵션을 설정하여 일반적으로 이러한 문제를 처리하는 방법을 IntelliTest에 알릴 수도 있습니다.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로 개수를 제한합니다. 이 기능을 사용하면 프로그램에 루프 또는 반복이 있는 경우 IntelliTest가 종료되지 않습니다.

IntelliTest가 특정 입력을 사용하여 매개 변수가 있는 테스트를 실행할 때마다 새 테스트 사례를 내보내는 경우는 여기에 해당하지 않을 수 있습니다. 자세한 내용은 [TestEmissionFilter](exploration-bounds.md#testemissionfilter)를 참조하세요.

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxRuns](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음 예제에서는 이 경계를 효과적으로 제거합니다(권장되지 않음).

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests 초과

IntelliTest는 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로 개수를 제한합니다. 이 기능을 사용하면 프로그램에 루프 또는 반복이 있는 경우 IntelliTest가 종료되지 않습니다.

IntelliTest가 특정 입력을 사용하여 매개 변수가 있는 테스트를 실행할 때마다 새 테스트 사례를 내보내는 경우는 여기에 해당하지 않을 수 있습니다. 자세한 내용은 [TestEmissionFilter](exploration-bounds.md#testemissionfilter)를 참조하세요.

IntelliTest는 처음에 많은 흥미로운 테스트 입력을 찾지만, 잠시 후에는 추가적인 테스트를 내보내지 않습니다. 이 옵션은 IntelliTest가 또 다른 관련 테스트 입력을 계속 찾을 수 있는 기간을 제어합니다.

**PexClass** 또는 **PexMethod** 같이 [PexSettingsAttributeBase](attribute-glossary.md#pexclass)에서 파생된 특성의 [MaxRunsWithoutNewTests](attribute-glossary.md#pexmethod) 옵션을 편집할 수 있습니다. 다음 예제에서는 이 경계를 효과적으로 제거합니다(권장되지 않음).

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>솔루션을 구체화할 수 없음

이 오류는 종종 이전 오류의 결과로 발생합니다. IntelliTest는 [제약 조건 해결기](input-generation.md#constraint-solver)를 사용하여 새 테스트 입력을 확인합니다. 때때로 [제약 조건 해결기](input-generation.md#constraint-solver)에서 제안된 테스트 입력이 유효하지 않습니다. 이 문제는 다음과 같은 경우 발생할 수 있습니다.

* 특정 제약 조건을 알 수 없는 경우
* 사용자 코드에서 오류를 발생시키는 사용자 정의 방법으로 값을 만든 경우
* 일부 관련 형식에 IntelliTest에서 제어되지 않는 초기화 논리가 포함된 경우(예: COM 클래스)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>개체를 생성하는 데 도움이 필요

IntelliTest는 [테스트 입력을 생성](input-generation.md)하고 일부 입력은 필드가 포함된 개체일 수 있습니다.
여기서 IntelliTest는 private 필드가 포함된 클래스의 인스턴스를 생성하려고 하고 이 private 필드에 특정 값이 포함될 경우 흥미로운 프로그램 동작이 발생할 것이라고 가정합니다.

그러나 리플렉션을 사용할 수 있지만 IntelliTest는 임의 필드 값을 사용하여 개체를 생성하지 않습니다.
대신에 이러한 경우 IntelliTest는 사용자가 클래스의 public 메서드를 사용하여 개체를 만들고 개체를 private 필드에 원하는 값이 포함된 상태로 전환하는 방법에 대한 힌트를 제공하도록 합니다.

IntelliTest에서 흥미로운 개체를 생성하는 데 도움이 되는 방법을 알아보려면 [기존 클래스 인스턴스화](input-generation.md#existing-classes)를 참조하세요.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>형식을 찾는 데 도움이 필요

IntelliTest는 모든 .NET 형식에 대한 [테스트 입력을 생성](input-generation.md)합니다. 여기서 IntelliTest는 추상 클래스에서 파생되거나 추상 인터페이스를 구현하는 인스턴스를 만들려고 하지만 제약 조건을 충족하는 형식을 인식하지 못합니다.

제약 조건과 일치하는 하나 이상의 형식을 가리키면 IntelliTest에 도움이 될 수 있습니다. 일반적으로 다음 특성 중 하나가 도움이 됩니다.

* **PexUseTypeAttribute** - 특정 형식을 가리킵니다.

  예를 들어 IntelliTest가 “**System.Collections.IDictionary**에 할당할 수 있는 형식을 알 수 없다”고 보고할 경우 다음 **PexUseTypeAttribute**를 테스트 또는 설비 클래스에 연결하면 도움이 될 수 있습니다.

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **어셈블리 수준 특성**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>사용 가능한 형식 추측

IntelliTest는 모든 .NET 형식에 대한 [테스트 입력을 생성](input-generation.md)합니다. 형식이 추상 또는 인터페이스인 경우 IntelliTest는 해당 형식의 특정 구현을 선택해야 합니다. 해당 항목을 선택하려면 어떤 형식이 있는지 알아야 합니다.

이 경고가 표시되면 IntelliTest가 일부 참조된 어셈블리를 확인하고 구현 형식을 찾았지만 해당 형식을 사용해야 하는지 또는 다른 곳에 사용 가능한 더 적절한 형식이 있는지 확신할 수 없음을 나타냅니다. IntelliTest는 단순히 적절해 보이는 형식을 선택했습니다.

이 경고를 피하려면 IntelliTest의 형식 선택을 허용하거나 해당 [PexUseType](attribute-glossary.md#pexusetype)을 추가하여 IntelliTest가 다른 형식을 사용하도록 지원할 수 있습니다.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>탐색 중 발생한 예기치 않은 오류

테스트를 탐색하는 동안 예기치 않은 예외가 catch되었습니다.

[이 예외를 버그로 보고](#report-bug)하세요.

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

사용자 코드에서 예외가 발생했습니다. 스택 추적을 검사하고 코드에서 버그를 제거합니다.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>계측되지 않은 메서드 호출

IntelliTest는 프로그램 실행을 모니터링하여 [테스트 입력을 생성](input-generation.md)합니다. IntelliTest가 동작을 모니터링할 수 있도록 관련 코드를 제대로 계측해야 합니다.

이 경고는 계측된 코드가 다른 계측되지 않은 어셈블리에서 메서드를 호출할 경우 나타납니다.
IntelliTest가 두 항목의 상호 작용을 탐색하도록 하려면 다른 어셈블리(또는 어셈블리의 일부)도 계측해야 합니다.

<a name="external-method-called"></a>
## <a name="external-method-called"></a>외부 메서드 호출

IntelliTest는 .NET 애플리케이션의 실행을 모니터링하여 [테스트 입력을 생성](input-generation.md)합니다.
IntelliTest는 .NET 언어로 작성되지 않은 코드에 대한 의미 있는 테스트 입력을 생성할 수 없습니다.

이 경고는 계측된 코드가 IntelliTest에서 분석할 수 없는 비관리 네이티브 메서드를 호출할 경우 표시됩니다. IntelliTest가 두 항목의 상호 작용을 탐색하도록 하려면 관리되지 않는 메서드를 모방해야 합니다.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>계측할 수 없는 메서드 호출

IntelliTest는 .NET 애플리케이션의 실행을 모니터링하여 [테스트 입력을 생성](input-generation.md)합니다. 그러나 기술적인 이유로 IntelliTest가 모니터링할 수 없는 몇 가지 메서드가 있습니다. 예를 들어 IntelliTest는 정적 생성자를 모니터링할 수 없습니다.

이 경고는 계측된 코드가 IntelliTest에서 모니터링할 수 없는 메서드를 호출할 경우 표시됩니다.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>테스트 가능성 문제

IntelliTest는 프로그램 실행을 모니터링하여 [테스트 입력을 생성](input-generation.md)합니다. 프로그램이 결정적이고 관련 동작이 테스트 입력을 통해 제어될 경우에만 관련 테스트 입력을 생성할 수 있습니다.

이 경고는 테스트 사례를 실행하는 동안 비결정적으로 동작하거나 환경과 상호 작용하는 메서드가 호출되었기 때문에 표시됩니다. 이러한 메서드의 예로는 **System.Random** 및 **System.IO.File**이 있습니다. IntelliTest가 의미 있는 테스트 입력을 만들도록 하려면 IntelliTest에서 추적 가능성 문제로 플래그를 지정하는 메서드를 모방해야 합니다.

<a name="limitation"></a>
## <a name="limitation"></a>제한 사항

IntelliTest는 [제약 조건 해결기](input-generation.md)를 사용하여 [테스트 입력을 생성](input-generation.md#constraint-solver)합니다.
그러나 [제약 조건 해결기](input-generation.md#constraint-solver)의 범위를 벗어나는 몇 가지 작업이 있습니다.
현재 여기에는 다음과 같은 작업이 포함됩니다.

* 대부분의 부동 소수점 작업(부동 소수점 숫자의 경우 일부 선형 산술만 지원됨)
* 부동 소수점 숫자와 정수 간 변환
* **System.Decimal** 형식에 대한 모든 작업

이 경고는 실행된 코드가 작업을 수행하거나 IntelliTest에서 해석할 수 없는 메서드를 호출할 경우 표시됩니다.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>관찰된 호출 불일치

IntelliTest는 프로그램 실행을 모니터링하여 [테스트 입력을 생성](input-generation.md)합니다. 그러나 IntelliTest는 일부 명령을 모니터링할 수 없습니다. 예를 들어 네이티브 코드를 모니터링할 수 없고 계측되지 않은 코드를 모니터링할 수 없습니다.

IntelliTest는 코드를 모니터링할 때 해당 코드에 관련된 테스트 입력을 생성할 수 없습니다.
종종 IntelliTest는 메서드에 대한 호출이 반환될 때까지 해당 메서드를 모니터링할 수 없다는 사실을 인식하지 못합니다. 그러나 이 경고의 원인은 다음과 같습니다.

* IntelliTest가 계측되지 않은 메서드 호출을 시작한 일부 코드를 모니터링한 경우
* 계측되지 않은 메서드가 계측된 메서드를 호출한 경우
* IntelliTest가 호출된 계측된 메서드를 모니터링할 경우

IntelliTest는 계측되지 않은 중간 메서드가 수행한 작업을 알 수 없으므로 중첩된 계측된 호출에 관련된 테스트 입력을 생성할 수 없습니다.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>정적 필드에 저장된 값

IntelliTest는 단위 테스트가 결정적일 경우에만 [관련 테스트 입력](input-generation.md)을 체계적으로 결정할 수 있습니다. 즉, 동일한 테스트 입력에 대해 항상 동일한 방식으로 동작합니다. 특히, 이는 테스트를 다시 실행할 수 있는 상태에서 해당 테스트가 시스템을 벗어나야 함을 의미합니다.
이상적으로는 단위 테스트가 전역 상태를 변경하면 안 되지만 전역 변수와의 모든 상호 작용이 모방되어야 합니다.

이 경고는 정적 필드가 변경되었음을 나타냅니다. 이로 인해 테스트가 비결정적으로 동작할 수 있습니다.

다음과 같은 경우 정적 필드 변경이 허용됩니다.

* 테스트 입력으로 인해 설치 또는 정리 코드가 변경을 실행 취소하는 경우
* 필드가 한 번만 시작되고 이후에 값이 변경되지 않는 경우

<a name="report-bug"></a>

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
