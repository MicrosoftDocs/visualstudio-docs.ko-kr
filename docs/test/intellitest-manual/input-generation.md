---
title: 동적 기호 실행 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Dynamic symbolic execution
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e5a3248d3f081bcab08c08110d305f0aa6235817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79306994"
---
# <a name="input-generation-using-dynamic-symbolic-execution"></a>동적 기호 실행을 사용하여 입력 생성

IntelliTest는 프로그램에서 분기 조건을 분석하여 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)에 대한 입력을 생성합니다. 테스트 입력은 입력이 프로그램의 새 분기 동작을 트리거할 수 있는지에 따라 선택됩니다. 분석은 증분 프로세스입니다. 정식 테스트 입력 매개 변수 `q: I -> {true, false}`에 대한 조건자 `I`를 구체화합니다. `q`는 IntelliTest가 이미 관찰한 동작의 집합을 나타냅니다. 처음에는 아무것도 관찰되지 않았으므로 `q := false`입니다.

루프 단계는 다음과 같습니다.

1. IntelliTest는 `i`제약 조건 해결기`q(i)=false`를 사용하여 [가 되도록 입력 ](#constraint-solver)를 결정합니다. 생성 시 입력 `i`는 이전에 표시되지 않은 실행 경로를 사용합니다. 처음에는 실행 경로가 검색되지 않았으므로 이것은 `i`가 입력일 수 있음을 의미합니다.

1. IntelliTest는 선택된 입력 `i`를 사용하여 테스트를 실행하고 테스트 및 테스트 중인 프로그램의 실행을 모니터링합니다.

1. 실행하는 동안 프로그램은 프로그램의 모든 조건부 분기에 의해 결정된 특정 경로를 사용합니다. 실행을 결정하는 모든 조건 집합을 *경로 조건*이라고 하며, 정식 입력 매개 변수에 대한 조건자 `p: I -> {true, false}`로 기록됩니다. IntelliTest는 이 조건자의 표현을 계산합니다.

1. IntelliTest는 `q := (q or p)`를 설정합니다. 즉, `p`에 의해 표현된 경로를 확인했다는 사실을 기록합니다.

1. 1단계로 이동합니다.

IntelliTest의 [제약 조건 해결기](#constraint-solver)는 .NET 프로그램에 나타날 수 있는 모든 형식의 값을 처리할 수 있습니다.

* [정수](#integers-and-floats) 및 [부동](#integers-and-floats)
* [개체](#objects)
* [구조체](#structs)
* [배열](#arrays-and-strings) 및 [문자열](#arrays-and-strings)

IntelliTest는 명시된 가정을 위반하는 입력을 필터링합니다.

즉시 입력([매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)에 대한 인수) 외에 테스트는 [PexChoose](static-helper-classes.md#pexchoose) 정적 클래스에서 추가적인 입력 값을 가져올 수 있습니다. 선택 항목에 따라 [매개 변수가 있는 모의 개체](#parameterized-mocks)의 동작이 결정됩니다.

## <a name="constraint-solver"></a>제약 조건 해결기

IntelliTest는 제약 조건 해결기를 사용하여 테스트 및 테스트 중인 프로그램의 관련 입력 값을 결정합니다.

IntelliTest는 [Z3](https://github.com/Z3Prover/z3/wiki) 제약 조건 해결기를 사용합니다.

## <a name="dynamic-code-coverage"></a>동적 코드 검사

런타임 모니터링의 파생 작업으로 IntelliTest는 동적 코드 검사 데이터를 수집합니다.
IntelliTest는 실행된 코드만 인식하므로 이를 *동적*이라고 합니다. 따라서 IntelliTest는 다른 검사 도구가 일반적으로 제공하는 것과 같은 방식으로 검사의 절대 값을 제공할 수 없습니다.

예를 들어 IntelliTest가 동적 검사를 5/10 기본 블록으로 보고할 경우 이것은 10개 중 5개 블록이 검사되었음을 의미합니다. 여기서 지금까지 분석을 통해 도달한 모든 메서드의 총 블록 수는 테스트 중인 어셈블리에 있는 모든 메서드와는 달리 10개입니다.
분석이 진행되면서 도달 가능한 메서드가 더 많이 검색되면 분자(이 예제에서는 5) 및 분모(10)가 증가할 수 있습니다.

## <a name="integers-and-floats"></a>정수 및 부동

IntelliTest의 [제약 조건 해결기](#constraint-solver)는 테스트 및 테스트 중인 프로그램에 대한 서로 다른 실행 경로를 트리거하기 위해 **byte**, **int**, **float** 등과 같은 기본 형식의 테스트 입력 값을 결정합니다.

## <a name="objects"></a>개체

IntelliTest에서 [기존 .NET 클래스의 인스턴스를 만들](#existing-classes)거나 IntelliTest를 사용하여 특정 인터페이스를 구현하고 사용법에 따라 다양한 방식으로 동작하는 [모의 개체를 자동으로 만들](#parameterized-mocks) 수 있습니다.

<a name="existing-classes"></a>
## <a name="instantiate-existing-classes"></a>기존 클래스 인스턴스화

**무엇이 문제일까요?**

IntelliTest는 테스트 및 테스트 중인 프로그램 실행 시 실행된 명령을 모니터링합니다. 특히 필드에 대한 모든 액세스를 모니터링합니다. 그런 다음 테스트 및 테스트 중인 프로그램이 다른 흥미로운 방식으로 동작하도록 [제약 조건 해결기](#constraint-solver)를 사용하여 개체 및 해당 필드 값을 비롯한 새 테스트 입력을 결정합니다.

이것은 IntelliTest가 특정 형식의 개체를 만들고 해당 필드 값을 설정해야 함을 의미합니다. 클래스가 [표시 가능](#visibility)하고 [visible](#visibility) 기본 생성자를 포함하는 경우 IntelliTest는 클래스의 인스턴스를 만들 수 있습니다.
클래스의 모든 필드가 [표시 가능](#visibility)하면 IntelliTest는 이 필드를 자동으로 설정할 수 있습니다.

형식이 표시 가능하지 않거나 필드가 [표시 가능](#visibility)하지 않으면 IntelliTest는 최대 코드 검사를 수행하기 위해 개체를 만들고 흥미로운 상태로 전환하기 위한 지원이 필요합니다. IntelliTest는 리플렉션을 사용하여 자의적인 방식으로 인스턴스를 만들고 초기화할 수 있지만 정상적인 프로그램 실행 중에는 절대 가능하지 않은 상태로 개체가 전환될 수 있으므로 일반적으로 바람직하지 않은 방법입니다. 대신에 IntelliTest는 사용자의 힌트에 의존합니다.

## <a name="visibility"></a>표시 유형

.NET에는 정교한 표시 유형 모델이 있습니다. 형식, 메서드, 필드 및 기타 멤버는 **private**, **public**, **internal** 등이 될 수 있습니다.

IntelliTest는 테스트를 생성할 때 생성된 테스트의 컨텍스트 내에서 .NET 표시 유형 규칙을 준수하는 작업(예: 생성자, 메서드 호출 및 필드 설정)만 수행하려고 합니다.

규칙은 다음과 같습니다.

* **internal 멤버 표시 유형**
  * IntelliTest는 생성된 테스트가 바깥쪽 [PexClass](attribute-glossary.md#pexclass)에 표시 가능한 internal 멤버에 액세스할 수 있다고 가정합니다.
  .NET에는 internal 멤버의 표시 유형을 다른 어셈블리로 확장하는 **InternalsVisibleToAttribute**가 있습니다.

* **[PexClass](attribute-glossary.md#pexclass)의 private 및 family(C#의 protected) 멤버 표시 유형**
  * IntelliTest는 항상 생성된 테스트를 [PexClass](attribute-glossary.md#pexclass)에 직접 배치하거나 서브클래스에 배치합니다. 따라서 IntelliTest는 모든 표시 가능한 family 멤버(C#의 **protected**)를 사용할 수 있다고 가정합니다.
  * 생성된 테스트가 [PexClass](attribute-glossary.md#pexclass)에 직접 배치되면(대기 partial 클래스 사용) IntelliTest는 [PexClass](attribute-glossary.md#pexclass)의 모든 private 멤버를 사용할 수 있다고 가정합니다.

* **public 멤버 표시 유형**
  * IntelliTest는 [PexClass](attribute-glossary.md#pexclass)의 컨텍스트에서 표시 가능한 모든 내보낸 멤버를 사용할 수 있다고 가정합니다.

## <a name="parameterized-mocks"></a>매개 변수가 있는 모의 개체

인터페이스 형식의 매개 변수가 있는 메서드는 어떻게 테스트하나요? 또는 봉인되지 않은 클래스의 경우는 어떤가요? IntelliTest는 이 메서드가 호출될 때 나중에 사용되는 구현을 인식하지 못합니다. 또한 테스트 시간에 사용할 수 있는 실제 구현이 없을 수도 있습니다.

일반적인 답변은 *모의 개체*를 명시적 동작과 함께 사용하는 것입니다.

모의 개체는 인터페이스를 구현하거나 봉인되지 않은 클래스를 확장합니다. 실제 구현이 아니라 모의 개체를 사용하여 테스트를 실행할 수 있는 바로 가기를 나타냅니다. 모의 개체의 동작은 동작이 사용되는 각 테스트 사례의 일부로 수동으로 정의됩니다. 모의 개체와 해당 동작을 쉽게 정의할 수 있는 많은 도구가 있지만, 이 동작은 여전히 수동으로 정의해야 합니다.

모의 개체의 하드 코드된 값 대신 IntelliTest는 값을 생성할 수 있습니다. [매개 변수가 있는 유닛 테스트](test-generation.md#parameterized-unit-testing)를 구현하는 것처럼 IntelliTest는 매개 변수가 있는 모의 개체를 구현합니다.

매개 변수가 있는 모의 개체에는 두 가지 실행 모드가 있습니다.

* **선택**: 코드를 탐색할 때 매개 변수가 있는 모의 개체는 추가 테스트 입력의 소스이고 IntelliTest는 흥미로운 값을 선택하려고 합니다.
* **재생**: 이전에 생성된 테스트를 실행할 경우 매개 변수가 있는 모의 개체는 동작(미리 정의된 동작)이 있는 스텁처럼 동작합니다.

[PexChoose](static-helper-classes.md#pexchoose)를 사용하여 매개 변수가 있는 모의 개체의 값을 얻습니다.

## <a name="structs"></a>구조체

IntelliTest의 **struct** 값 지각 기능은 [개체](#objects)를 처리하는 방법과 비슷합니다.

## <a name="arrays-and-strings"></a>배열 및 문자열

IntelliTest는 테스트 및 테스트 중인 프로그램 실행 시 실행된 명령을 모니터링합니다. 특히 프로그램이 문자열 또는 배열의 길이와 다차원 배열의 하한 및 최소 길이를 사용하는 경우를 관찰합니다.
또한 프로그램이 문자열 또는 배열의 다양한 요소를 사용하는 방식을 관찰합니다. 그런 다음 [제약 조건 해결기](#constraint-solver)를 사용하여 테스트 및 테스트 중인 프로그램이 흥미로운 방식으로 동작하게 만드는 길이 및 요소 값을 확인합니다.

IntelliTest는 흥미로운 프로그램 동작을 트리거하는 데 필요한 배열 및 문자열의 크기를 최소화하려고 합니다.

<a name="additional-inputs"></a>
## <a name="obtain-additional-inputs"></a>추가 입력 가져오기

[PexChoose](static-helper-classes.md#pexchoose) 정적 클래스는 테스트에 대한 추가 입력을 가져오고 [매개 변수가 있는 모의 개체](#parameterized-mocks)를 구현하는 데 사용될 수 있습니다.

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.

## <a name="further-reading"></a>추가 정보

* [작동 원리](https://devblogs.microsoft.com/devops/smart-unit-tests-a-mental-model/)
