---
title: MSBuild 조건 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
- Exists, MSBuild condition function
- HasTrailingSlash, MSBuild condition function
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5994e3f5b17f50d707c4c5a00666d60c2efd3184
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711705"
---
# <a name="msbuild-conditions"></a>MSBuild 조건

MSBuild는 `Condition` 특성이 허용될 때마다 적용할 수 있는 특정 조건 집합을 지원합니다. 다음 표에서는 이러한 조건에 대해 설명합니다.

|조건|설명|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|`stringA`가 `stringB`와 같으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(Configuration)'=='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다. 이 검사는 대/소문자를 구분하지 않습니다.|
|'`stringA`' != '`stringB`'|`stringA`가 `stringB`와 같지 않으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(Configuration)'!='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다. 이 검사는 대/소문자를 구분하지 않습니다.|
|\<, >, \<=, >=|피연산자의 숫자 값을 평가합니다. 관계형 평가가 true이면 `true`를 반환합니다. 피연산자는 10진수 또는 16진수 숫자로 평가되어야 합니다. 16진수는 "0x"로 시작해야 합니다. **참고:**  XML에서는 `<` 및 `>` 문자를 이스케이프해야 합니다. `<` 기호는 `&lt;`로 표시됩니다. `>` 기호는 `&gt;`로 표시됩니다.|
|Exists('`stringA`')|이름이 `stringA`인 파일이나 폴더가 있으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="!Exists('$(Folder)')"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|
|HasTrailingSlash('`stringA`')|지정한 문자열에 후행 백슬래시(\\) 또는 슬래시(/) 문자가 있는 경우 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|
|!|피연산자가 `false`로 평가되면 `true`로 평가됩니다.|
|`And`|피연산자가 `true`로 평가되면 `true`로 평가됩니다.|
|`Or`|피연산자 중 하나 이상이 `true`로 평가되면 `true`로 평가됩니다.|
|()|내부에 포함된 식이 `true`로 평가되면 `true`로 평가되는 그룹화 메커니즘입니다.|
|$if$ ( %expression% ), $else$, $endif$|지정한 `%expression%`이 전달된 사용자 지정 템플릿 매개 변수의 문자열 값과 일치하는지를 확인합니다. `$if$` 조건이 `true`로 평가되면 해당 문이 실행되고 그렇지 않으면 `$else$` 조건이 확인됩니다. `$else$` 조건이 `true`이면 해당 문이 실행되고 그렇지 않으면 `$endif$` 조건이 식 평가를 종료합니다.<br /><br /> 사용법의 예제는 [Visual Studio 프로젝트/항목 템플릿 매개 변수 논리](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)를 참조하세요.|

[TrimEnd()](/dotnet/api/system.string.trimend) 함수가 문자열의 관련 있는 파트만 비교하는 데 사용되고 있는 다음 예제에서처럼 조건에서 문자열 메서드를 사용하여 .NET Framework와 .NET Core 대상 프레임워크를 구분할 수 있습니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">

    <PropertyGroup>
        <TargetFrameworks>net45;net48;netstandard2.1;netcoreapp2.1;netcoreapp3.1</TargetFrameworks>
    </PropertyGroup>

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

MSBuild 프로젝트 파일에는 true 부울 형식이 없습니다. 부울 데이터는 비어 있거나 임의의 값으로 설정할 수 있는 속성으로 표시됩니다. 따라서 `'$(Prop)' == 'true'`는 "Prop이 `true`인 경우"를 의미하지만 `'$(Prop)' != 'false'`는 "Prop이 `true` 또는 설정되지 않았거나 다른 항목으로 설정된 경우"를 의미합니다.

부울 논리는 조건 컨텍스트에서만 평가되므로 `<Prop2>'$(Prop1)' == 'true'</Prop>`와 같은 속성 설정은 부울 값으로 평가되지 않고 변수 확장 후 문자열로 표시됩니다.  

MSBuild는 부울 값으로 사용되는 문자열 속성을 보다 쉽게 사용할 수 있도록 몇 가지 특수 처리 규칙을 구현합니다. 부울 리터럴은 허용되므로 `Condition="true"` 및 `Condition="false"`는 예상대로 작동합니다. MSBuild에는 부울 부정 연산자를 지원하는 특수 규칙도 포함됩니다. 따라서 `$(Prop)`이 'true'인 경우 `!$(Prop)`이 `!true`로 확장되고,이는 사용자가 예상한 대로 `false`와 동일하게 비교됩니다.

## <a name="see-also"></a>참고 항목

- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [조건부 구문](../msbuild/msbuild-conditional-constructs.md)
- [연습: 처음부터 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
