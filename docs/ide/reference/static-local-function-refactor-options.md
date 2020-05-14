---
title: 정적 로컬 함수 리팩터링 옵션
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144832"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>정적 로컬 함수 리팩터링 및 빠른 작업

이 문서에서는 정적 로컬 함수와 관련된 두 가지 생산성 기능을 간략하게 설명합니다. 하나는 로컬 함수를 정적으로 지정하는 리팩터링이고, 다른 하나는 정적 로컬 함수에 변수를 전달하는 코드를 생성하는 빠른 작업입니다.

## <a name="make-local-function-static"></a>로컬 함수를 정적으로 지정

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 로컬 함수를 정적으로 만들어서 함수 밖에서 정의된 변수를 함수 선언과 호출로 전달합니다.

**시기:** 로컬 함수를 정적으로 지정하고 모든 변수를 함수 범위에서 정의하려고 합니다.

**이유:** 정적 로컬 함수는 가독성을 개선합니다. 특정 코드가 격리되었다는 것을 알고 있으면 보다 쉽게 이해하고, 다시 읽고, 다시 사용할 수 있습니다. 또한 정적 로컬 함수는 단일 메서드에서만 호출되는 정적 함수로 클래스가 무효화되지 않도록 범위를 제공합니다.

### <a name="how-to"></a>방법

1. 로컬 함수 이름 위에 캐럿을 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![로컬 함수를 정적으로 지정](media/make-local-function-static.png)

3. **로컬 함수를 '정적'으로 지정**을 선택합니다.

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>정적 로컬 함수에서 변수를 명시적으로 전달

이 빠른 작업은 다음에 적용됩니다.

- C#

**내용:** 로컬 정적 함수에 변수를 명시적으로 전달합니다.

**시기:** 로컬 함수를 정적으로 지정하지만 외부에서 초기화된 변수를 계속 사용하려고 합니다.

**이유:** 정적 로컬 함수를 사용하면 판독기는 프로그램의 특정 컨텍스트에서만 함수를 선언 및 호출할 수 있다는 것을 알고 있으므로 판독기에 설명이 제공됩니다. 이 컨텍스트 외부에서 변수를 정의할 수 있는 유연성을 제공하지만 변수를 정적 로컬 함수에 인수로 전달할 수 있습니다.

### <a name="how-to"></a>방법

1. 정적 로컬 함수에서 사용되는 변수에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![정적 로컬 함수에서 변수를 명시적으로 전달](media/pass-variable-explicitly-static-local-function.png)

3. **Pass variable explicitly in local static function**(변수를 로컬 static 함수로 명시적으로 전달)을 선택합니다.

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)