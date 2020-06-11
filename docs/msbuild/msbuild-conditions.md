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
ms.openlocfilehash: 926c54be9d31a6d0708b33248b6887c0ac7e324e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184070"
---
# <a name="msbuild-conditions"></a>MSBuild 조건

MSBuild는 `Condition` 특성이 허용될 때마다 적용할 수 있는 특정 조건 집합을 지원합니다. 다음 표에서는 이러한 조건에 대해 설명합니다.

|조건|설명|
|---------------|-----------------|
|'`stringA`' == '`stringB`'|`stringA`가 `stringB`와 같으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다. 이 검사는 대/소문자를 구분하지 않습니다.|
|'`stringA`' != '`stringB`'|`stringA`가 `stringB`와 같지 않으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다. 이 검사는 대/소문자를 구분하지 않습니다.|
|\<, >, \<=, >=|피연산자의 숫자 값을 평가합니다. 관계형 평가가 true이면 `true`를 반환합니다. 피연산자는 10진수 또는 16진수 숫자로 평가되어야 합니다. 16진수는 "0x"로 시작해야 합니다. **참고:**  XML에서는 `<` 및 `>` 문자를 이스케이프해야 합니다. `<` 기호는 `&lt;`로 표시됩니다. `>` 기호는 `&gt;`로 표시됩니다.|
|Exists('`stringA`')|이름이 `stringA`인 파일이나 폴더가 있으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|
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

    <PropertyGroup Condition="'$(TargetFramework.TrimEnd(`0123456789.`))' == 'net'">
        <!-- Properties for .NET Framework -->
    </PropertyGroup>

</Project>
```

## <a name="see-also"></a>참조

- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [조건부 구문](../msbuild/msbuild-conditional-constructs.md)
- [연습: 처음부터 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
