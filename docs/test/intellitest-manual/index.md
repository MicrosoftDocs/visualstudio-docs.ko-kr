---
title: IntelliTest 참조 설명서 | Microsoft 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b1c40412da096db63da87e04711cdc1a95b5cc84
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "75591621"
---
# <a name="intellitest-reference-manual"></a>IntelliTest 참조 설명서

## <a name="contents"></a>콘텐츠

* **[IntelliTest 개요](introduction.md)**
  - [IntelliTest의 Hello World](introduction.md#the-hello-world-of-intellitest)
  - [제한 사항](introduction.md#limitations)
    * [비결정성](introduction.md#nondeterminism)
    * [동시성](introduction.md#concurrency)
    * [네이티브 코드](introduction.md#native-code)
    * [플랫폼](introduction.md#platform)
    * [언어](introduction.md#language)
    * [상징적 지각](introduction.md#symbolic-reasoning)
    * [잘못된 스택 추적](introduction.md#incorrect-stack-traces)
  - [추가 정보](introduction.md#further-reading)

* **[IntelliTest 시작](getting-started.md)**
  - [중요한 특성](getting-started.md#important-attributes)
  - [중요한 정적 도우미 클래스](getting-started.md#helper-classes)

* **[테스트 생성](test-generation.md)**
  - [테스트 생성기](test-generation.md#test-generators)
  - [매개 변수가 있는 유닛 테스트](test-generation.md#parameterized-unit-testing)
  - [제네릭 매개 변수가 있는 유닛 테스트](test-generation.md#generic-parameterized)
  - [예외 허용](test-generation.md#allowing-exceptions)
  - [내부 형식 테스트](test-generation.md#internal-types)
  - [가정 및 어설션](test-generation.md#assumptions-and-assertions)
  - [사전 조건](test-generation.md#precondition)
  - [사후 조건](test-generation.md#postcondition)
  - [테스트 실패](test-generation.md#test-failures)
  - [설치 및 해체](test-generation.md#setup-teardown)
  - [추가 정보](test-generation.md#further-reading)

* **[입력 생성](input-generation.md)**
  - [제약 조건 해결기](input-generation.md#constraint-solver)
  - [동적 코드 검사](input-generation.md#dynamic-code-coverage)
  - [정수 및 부동](input-generation.md#integers-and-floats)
  - [개체](input-generation.md#objects)
  - [기존 클래스 인스턴스화](input-generation.md#existing-classes)
  - [표시 유형](input-generation.md#visibility)
  - [매개 변수가 있는 모의 개체](input-generation.md#parameterized-mocks)
  - [구조체](input-generation.md#structs)
  - [배열 및 문자열](input-generation.md#arrays-and-strings)
  - [추가 입력 가져오기](input-generation.md#additional-inputs)
  - [추가 정보](input-generation.md#further-reading)

* **[탐색 경계](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[특성 용어집](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[폭포수형 설정](settings-waterfall.md)**

* **[정적 도우미 클래스](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[경고 및 오류](warnings-and-errors.md)**
  - [MaxBranches 초과](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime 초과](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions 초과](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls 초과](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack 초과](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns 초과](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests 초과](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [솔루션을 구체화할 수 없음](warnings-and-errors.md#cannot-concretize-solution)
  - [개체를 생성하는 데 도움이 필요](warnings-and-errors.md#help-construct)
  - [형식을 찾는 데 도움이 필요](warnings-and-errors.md#help-types)
  - [사용 가능한 형식 추측](warnings-and-errors.md#usable-type-guessed)
  - [탐색 중 발생한 예기치 않은 오류](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [계측하지 않은 메서드 호출](warnings-and-errors.md#uninstrumented-method-called)
  - [외부 메서드 호출](warnings-and-errors.md#external-method-called)
  - [계측할 수 없는 메서드 호출](warnings-and-errors.md#uninstrumentable-method-called)
  - [테스트 가능성 문제](warnings-and-errors.md#testability-issue)
  - [제한 사항](warnings-and-errors.md#limitation)
  - [관촬된 호출 불일치](warnings-and-errors.md#observed-call-mismatch)
  - [정적 필드에 저장된 값](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
