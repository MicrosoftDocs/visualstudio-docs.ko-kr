---
title: Configuring Warnings in Visual Basic
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33302a4a686d80621cc64ee018371a2d03ea30ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114721"
---
# <a name="configuring-warnings-in-visual-basic"></a>Visual Basic에서 경고 구성

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 컴파일러에는 런타임 오류를 일으킬 수 있는 코드에 대한 일련의 경고가 포함됩니다. 이 정보를 사용하여 버그가 더 적으면서 더 깔끔하고 더 빠르고 더 나은 코드를 작성할 수 있습니다. 예를 들어 컴파일러에서는 사용자가 할당되지 않은 개체 변수의 멤버를 호출하거나, 반환 값을 설정하지 않고 함수에서 반환되거나, 예외를 catch하기 위한 논리에서 오류가 있는 `Try` 블록을 실행하려고 시도할 경우 경고를 생성합니다.

경우에 따라 컴파일러에서는 사용자가 오류 발생이 예상되는 작업이 아닌 긴급한 작업에 집중할 수 있도록 사용자 대신 추가 논리를 제공합니다. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]의 이전 버전에서 **Option Strict**는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 컴파일러가 제공하는 추가 논리를 제한하는 데 사용되었습니다. 경고를 구성하면 이 논리를 개별 경고 수준에서 더 세밀하게 제한할 수 있습니다.

프로젝트를 사용자 지정하고 애플리케이션에 관련되지 않은 일부 경고를 끄면서 다른 경고를 오류로 전환하고자 할 수 있습니다. 이 페이지에서는 개별 경고를 켜고 끄는 방법을 설명합니다.

## <a name="turning-warnings-off-and-on"></a>경고 끄기 및 켜기
경고를 구성하는 방법은 두 가지입니다. **프로젝트 디자이너**를 사용하여 구성하거나 **/warnaserror** 및 **/nowarn** 컴파일러 옵션을 사용할 수 있습니다.

**프로젝트 디자이너** 페이지의 **컴파일** 탭에서 경고를 켜고 끌 수 있습니다. 모든 경고를 사용하지 않으려면 **모든 경고 사용 안 함** 확인란을 선택하고, 모든 경고를 오류로 처리하려면 **모든 경고를 오류로 처리**를 선택합니다. 표시된 표에서 원하는 대로 일부 개별 경고를 오류 또는 경고로 토글할 수 있습니다.

**Option Strict**가 **끄기**로 설정되면 **Option Strict** 관련 경고를 서로 개별적으로 처리할 수 없습니다. **Option Strict**가 **켜기**로 설정되면 상태에 관계없이 관련 경고가 오류로 처리됩니다. 명령줄 컴파일러에서 **을 지정하여** Option Strict**가** 사용자 지정`/optionstrict:custom`으로 설정되면 **Option Strict** 경고를 개별적으로 켜고 끌 수 있습니다.

컴파일러의 **/warnaserror** 명령줄 옵션을 사용하여 경고를 오류로 처리할지 여부를 지정할 수도 있습니다. \+ 또는 -를 사용하여 이 목록에 쉼표로 구분된 목록을 추가하면 어떤 경고를 오류 또는 경고로 처리할지 지정할 수 있습니다. 다음 표에서는 가능한 옵션을 자세히 설명합니다.

|명령줄 옵션|지정 내용|
| - |---------------|
|`/warnaserror+`|모든 경고를 오류로 처리합니다.|
|`/warnsaserror`-|경고를 오류로 처리하지 않습니다. 이것이 기본값입니다.|
|`/warnaserror+:<warning list` `>`|해당 오류 ID 번호가 쉼표로 구분된 목록으로 나열된 특정 경고를 오류로 처리합니다.|
|`/warnaserror-:<warning list>`|해당 오류 ID 번호가 쉼표로 구분된 목록으로 나열된 특정 경고를 오류로 처리하지 않습니다.|
|`/nowarn`|경고를 보고하지 않습니다.|
|`/nowarn:<warning list>`|해당 오류 ID 번호가 쉼표로 구분된 목록으로 나열된 지정된 경고를 보고하지 않습니다.|

경고 목록에는 오류로 처리되어야 하는 경고의 오류 ID 번호가 포함되고 이 오류 ID 번호는 명령줄 옵션과 함께 특정 경고를 켜거나 끄는 데 사용될 수 있습니다. 경고 목록에 잘못된 번호가 있으면 오류가 보고됩니다.

## <a name="examples"></a>예
이 명령줄 인수 예제에 대한 표에서는 각 인수가 수행하는 작업을 설명합니다.

|인수|Description|
|--------------|-----------------|
|`vbc /warnaserror`|모든 경고를 오류로 처리하도록 지정합니다.|
|`vbc /warnaserror:42024`|경고 42024가 오류로 처리되도록 지정합니다.|
|`vbc /warnaserror:42024,42025`|경고 42024 및 42025가 오류로 처리되도록 지정합니다.|
|`vbc /nowarn`|경고가 보고되지 않도록 지정합니다.|
|`vbc /nowarn:42024`|경고 42024가 보고되지 않도록 지정합니다.|
|`vbc /nowarn:42024,42025`|경고 42024 및 42025가 보고되지 않도록 지정합니다.|

## <a name="types-of-warnings"></a>경고 형식
오류로 처리할 수 있는 경고 목록은 다음과 같습니다.

### <a name="implicit-conversion-warning"></a>암시적 변환 경고
암시적 변환 인스턴스에 대해 생성됩니다. `&` 연산자를 사용할 때 내부 숫자 형식을 문자열로 암시적으로 변환하는 경우는 포함되지 않습니다. 새 프로젝트의 기본값은 끄기입니다.

ID: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>런타임에 바인딩 메서드 호출 및 오버로드 확인 경고
런타임에 바인딩 인스턴스에 대해 생성됩니다. 새 프로젝트의 기본값은 끄기입니다.

ID: 42017

### <a name="operands-of-type-object-warnings"></a>'Object' 형식 경고의 피연산자
`Object`Option Strict On**관련 오류를 생성하는** 형식의 피연산자가 발생할 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42018 및 42019

### <a name="declarations-require-as-clause-warnings"></a>선언에 'As' 절 필요 경고
`As` 절이 없는 변수, 함수 또는 속성 선언에서 **Option Strict On** 관련 오류가 발생할 경우 생성됩니다. 형식이 할당되지 않은 변수는 `Object` 형식으로 간주합니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42020(변수 선언), 42021(함수 선언) 및 42022(속성 선언).

### <a name="possible-null-reference-exception-warnings"></a>가능한 Null 참조 예외 경고
값이 할당되기 전에 변수가 사용된 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>사용되지 않는 로컬 변수 경고
로컬 변수가 선언되었지만 참조된 적이 없는 경우 생성됩니다. 이 옵션은 기본적으로 사용됩니다.

ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>인스턴스 변수를 통한 공유 멤버 액세스 경고
인스턴스를 통한 공유 멤버 액세스에 부작용이 있을 수 있는 경우나 인스턴스 변수를 통한 공유 멤버 액세스가 식의 오른쪽에서 이루어지지 않거나 매개 변수로 전달되고 있는 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>재귀 연산자 또는 속성 액세스 경고
루틴의 본문에서 루틴이 정의된 같은 연산자 또는 속성을 사용하는 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42004(연산자), 42026(속성)

### <a name="function-or-operator-without-return-value-warning"></a>반환 값이 없는 함수/연산자 경고
함수 또는 연산자에 반환 값이 지정되지 않은 경우 생성됩니다. 이 경고에는 함수와 이름이 같은 암시적 로컬 변수에 대한 `Set`이 생략된 경우가 포함됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42105(함수), 42016(연산자)

### <a name="overloads-modifier-used-in-a-module-warning"></a>모듈에 사용되는 오버로드 한정자 경고
`Overloads`가 `Module`에 사용될 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>중복되거나 겹치는 catch 블록 경고
정의되지 않은 다른 `Catch` 블록에 대한 관계로 인해 `Catch` 블록에 도달하지 못한 경우 생성됩니다. 새 프로젝트의 기본값은 켜기입니다.

ID: 42029, 42031

## <a name="see-also"></a>참고 항목

- [오류 형식](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Try...Catch...Finally 명령문](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/warnaserror(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [컴파일 페이지, 프로젝트 디자이너(Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [기본적으로 해제되어 있는 컴파일러 경고](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)
