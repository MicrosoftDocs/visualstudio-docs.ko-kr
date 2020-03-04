---
title: 탐색 경계 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2a57d79fb64675f90edf50e6a0d7d50b8a3c6fd7
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169419"
---
# <a name="exploration-bounds"></a>탐색 경계

**PexSettingsAttributeBase**는 특성으로서 설정 경계에 대한 추상 기본 클래스입니다. IntelliTest의 설정 개요는 [폭포수형 설정](settings-waterfall.md)을 참조하세요.

이와 관련된 명명된 속성 및 파생 특성을 사용하여 설정을 수정할 수 있습니다.

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **제약 조건 해결 경계**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - [제약 조건 해결기](input-generation.md#constraint-solver)가 새롭거나 다른 실행 경로를 따르게 만드는 입력을 검색해야 하는 시간(초)입니다.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) - [제약 조건 해결기](input-generation.md#constraint-solver)가 입력을 검색하는 데 사용할 수 있는 크기(MB)입니다.
* **탐색 경로 경계**
  * [MaxBranches](#maxbranches) - 단일 실행 경로를 따라 사용할 수 있는 최대 분기 수입니다.
  * [MaxCalls](#maxcalls) - 단일 실행 경로 중에 생성될 수 있는 최대 호출 수입니다.
  * [MaxStack](#maxstack) - 단일 실행 경로 중 임의 시점에 활성 호출 프레임 수로 측정된 최대 스택 크기입니다.
  * [MaxConditions](#maxconditions) - 단일 실행 경로 중에 확인될 수 있는 입력에 대한 최대 조건 수입니다.
* **탐색 경계**
  * [MaxRuns](#maxruns) - 탐색 중에 시도될 최대 실행 수입니다.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) - 새 테스트를 내보내지 않는 최대 연속 실행 수입니다.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) - 탐색 중에 시도될 고유한 실행 경로를 사용한 최대 실행 수입니다.
  * [MaxExceptions](#maxexceptions) - 모든 검색된 실행 경로 조합에 대해 검색될 수 있는 최대 예외 수입니다.
* **테스트 도구 모음 코드 생성 설정**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) - True인 경우 경로 경계([MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions))를 초과하는 실행 경로는 무시됩니다.
  * [TestEmissionFilter](#testemissionfilter) - IntelliTest가 테스트를 내보내는 환경을 나타냅니다.
  * [TestEmissionBranchHits](#testemissionbranchhits) - IntelliTest가 내보내는 테스트 수를 제어합니다.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

[제약 조건 해결기](input-generation.md#constraint-solver)가 새롭거나 다른 실행 경로를 사용하게 만드는 입력을 계산해야 하는 시간(초)입니다. **PexSettingsAttributeBase** 및 해당 파생 형식의 옵션입니다.

IntelliTest가 프로그램 실행 경로를 더 깊게 탐색할수록 IntelliTest가 프로그램의 제어 흐름 및 데이터 흐름을 기반으로 제약 조건 시스템이 더 복잡해집니다. 시간 제한에 따라 이 값을 설정하여 IntelliTest가 새 실행 경로를 검색하는 데 다소 시간을 소요하도록 허용할 수 있습니다.

일반적으로 시간 제한의 이유는 IntelliTest가 솔루션이 없는 제약 조건 시스템에 대한 솔루션을 찾으려고 하지만 이 사실을 인식하지 못하기 때문입니다. 이 경우가 시간 제한의 가장 일반적인 사례이므로 경계를 늘리는 것은 좋은 방법이 아닙니다.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

[제약 조건 해결기](input-generation.md#constraint-solver)가 새롭거나 다른 실행 경로를 사용하게 만드는 입력을 계산해야 하는 크기(MB)입니다. *PexSettingsAttributeBase** 및 해당 파생 형식의 옵션입니다.

IntelliTest가 프로그램 실행 경로를 더 깊게 탐색할수록 IntelliTest가 프로그램의 제어 흐름 및 데이터 흐름을 기반으로 제약 조건 시스템이 더 복잡해집니다. 컴퓨터의 사용 가능한 메모리에 따라 이 값을 설정하여 IntelliTest가 더 복잡한 제약 조건 시스템을 처리하도록 허용할 수 있습니다.

일반적으로 시간 제한의 이유는 IntelliTest가 솔루션이 없는 제약 조건 시스템에 대한 솔루션을 찾으려고 하지만 이 사실을 인식하지 못하기 때문입니다. 이 경우가 메모리 부족 상황의 가장 일반적인 사례이므로 경계를 늘리는 것은 좋은 방법이 아닙니다.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

단일 실행 경로를 따라 사용할 수 있는 최대 분기 수입니다.

이 탐색 경계의 목적은 IntelliTest가 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 길이를 제한하는 것입니다. 특히, 이를 통해 프로그램이 무한 루프로 들어가는 경우 IntelliTest가 응답하지 않는 문제를 방지합니다.

매개 변수가 있는 테스트 입력을 사용하지 않는 분기를 포함하여 실행 및 모니터링된 코드의 각 조건부 및 무조건부 분기는 이 제한 계산에 포함됩니다.

예를 들어 다음 코드는 대략 100개의 분기를 사용합니다.

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

단일 실행 경로 중에 생성될 수 있는 최대 호출 수입니다.

이 탐색 경계의 목적은 IntelliTest가 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 길이를 제한하는 것입니다. 특히, 이를 통해 프로그램이 수없이 반복적으로 메서드를 호출하여 IntelliTest가 복구될 수 없는 스택 오버플로를 유발하는 경우 IntelliTest가 응답하지 않는 문제를 방지합니다.

실행 및 모니터링된 코드의 각 호출(직접, 간접, 가상, 이동)은 이 제한 계산에 포함됩니다.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

단일 실행 경로 중 임의 시점에 활성 호출 프레임 수로 측정된 최대 스택 크기입니다.

이 탐색 경계의 목적은 IntelliTest가 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 스택 크기를 제한하는 것입니다. 특히, 이를 통해 IntelliTest가 모든 사용 가능한 스택 공간을 사용하여 IntelliTest가 복구될 수 없는 스택 오버플로를 유발하는 문제를 방지합니다.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

단일 실행 경로 중에 확인될 수 있는 입력에 대한 최대 조건 수입니다.

이 탐색 경계의 목적은 IntelliTest가 [입력 생성](input-generation.md) 중에 탐색하는 실행 경로의 복잡성을 제한하는 것입니다. 매개 변수가 있는 테스트의 입력을 사용하는 각 조건부 분기는 이 제한 계산에 포함됩니다.

예를 들어 다음 코드의 각 경로는 n+1개 조건을 사용합니다.

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

IntelliTest가 테스트 탐색 중에 시도할 최대 실행 수입니다.

이 탐색 경계의 목적은 루프 또는 반복이 포함된 코드에 무한 수의 실행 경로가 있으므로 [입력 생성](input-generation.md) 중에 IntelliTest를 제한하는 것입니다.

두 가지 설정 **MaxRuns** 및 **MaxRunsWithUniquePaths**는 다음과 같이 관련됩니다.

* IntelliTest는 다른 테스트 입력을 통해 매개 변수가 있는 테스트 메서드를 **MaxRuns**번까지 호출합니다.
* 실행된 코드가 결정적이면 IntelliTest는 매번 다른 경로를 사용합니다. 그러나 조건에 따라 실행된 코드가 다른 입력을 통해 이전에 이미 사용된 실행 경로를 따를 수 있습니다.
* IntelliTest는 발견한 고유한 실행 경로 수를 계산합니다. 이 개수는 **MaxRunsWithUniquePaths** 옵션으로 제한됩니다.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

새 테스트를 내보내지 않는 최대 연속 실행 수입니다.

IntelliTest가 짧은 시간 내에 많은 흥미로운 테스트 입력을 찾을 수 있지만, 잠시 후에는 더 많은 새로운 테스트 입력을 찾지 못하고 추가적인 단위 테스트를 내보내지 못합니다. 이 구성 옵션은 IntelliTest가 새로운 테스트를 내보내지 않고 수행할 수 있는 연속 시도 수에 대한 경계를 적용합니다. 경계에 도달하면 탐색이 중단됩니다.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

IntelliTest가 탐색 중에 고려할 최대 고유 경로 수입니다.

이 탐색 경계의 목적은 루프 또는 반복이 포함된 코드에 무한 수의 실행 경로가 있으므로 [입력 생성](input-generation.md) 중에 IntelliTest를 제한하는 것입니다.

두 가지 설정 **MaxRuns** 및 **MaxRunsWithUniquePaths**는 다음과 같이 관련됩니다.

* IntelliTest는 다른 테스트 입력을 통해 매개 변수가 있는 테스트 메서드를 **MaxRuns**번까지 호출합니다.
* 실행된 코드가 결정적이면 IntelliTest는 매번 다른 경로를 사용합니다. 그러나 조건에 따라 실행된 코드가 다른 입력을 통해 이전에 이미 사용된 실행 경로를 따를 수 있습니다.
* IntelliTest는 발견한 고유한 실행 경로 수를 계산합니다. 이 개수는 **MaxRunsWithUniquePaths** 옵션으로 제한됩니다.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

탐색이 중단되기 전에 발생할 수 있는 최대 예외 수입니다.

이 탐색 경계의 목적은 많은 버그가 포함된 코드의 탐색을 중지하는 것입니다. IntelliTest가 코드에서 너무 많은 오류를 발견하면 탐색이 중지됩니다.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

구성된 경로 경계 [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) 및 [MaxConditions](#maxconditions)를 초과하는 실행 경로는 무시됩니다.

이 탐색 경계의 목적은 종료되지 않을 수 있는 테스트를 처리하는 것입니다. IntelliTest는 [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack) 또는 [MaxConditions](#maxconditions)와 같은 탐색 경계에 도달하면 해당 테스트가 종료되지 않는 프로세스가 아니고 나중에 스택 오버플로를 유발하지 않을 것으로 가정합니다. 해당 테스트로 인해 다른 테스트 프레임워크에 문제가 발생할 수 있는데, 이 특성을 사용하면 IntelliTest가 종료되지 않을 수 있는 프로세스에 대한 테스트 사례 또는 스택 오버플로를 유발하는 테스트 사례를 내보내지 않도록 할 수 있습니다.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

IntelliTest가 내보내야 하는 테스트 형식을 나타냅니다. 가능한 값은 다음과 같습니다.

* **모두** - 가정 위반을 포함하여 모든 것에 대한 테스트를 내보냅니다.
* **FailuresAndIncreasedBranchHits**(기본값) - 모든 실패에 대한 테스트를 내보내고 테스트 사례에서 [TestEmissionBranchHits](#testemissionbranchhits)에 의해 제어되는 검사가 증가할 때마다 테스트를 내보냅니다.
* **FailuresAndUniquePaths** - IntelliTest가 발견한 모든 실패에 대한 테스트를 내보내고 고유 실행 경로를 생성하는 각 테스트 입력에 대한 테스트를 내보냅니다.
* **Failures** - 실패에 대한 테스트만 내보냅니다.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

현재 [TestEmissionFilter](#testemissionfilter) 설정에 따라 IntelliTest가 이전에 검사하지 않은 프로그램의 분기를 검사할 때 새 테스트 사례를 내보냅니다.

**TestEmissionBranchHits** 설정은 IntelliTest에서 분기 검사 여부만 고려해야 하는지(**TestEmissionBranchHits=1**), 테스트에서 분기가 한 번 또는 두 번 검사되는지(**TestEmissionBranchHits=2**) 등을 결정합니다.

**TestEmissionBranchHits=1**은 IntelliTest가 도달할 수 있는 모든 분기를 검사할 매우 작은 테스트 도구 모음을 생성합니다. 특히, 이 테스트 도구 모음은 도달한 모든 기본 블록 및 문도 검사합니다.

이 옵션의 기본값은 **TestEmissionBranchHits=2**로서, 미래 재발 오류를 검색하는 데 더 적합한 더 표현적인 테스트 도구 모음을 생성합니다.

## <a name="got-feedback"></a>피드백이 있으신가요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
