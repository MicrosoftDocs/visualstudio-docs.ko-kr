---
title: T4 Include 지시문
description: 'Visual Studio 텍스트 템플릿에서 <# #> 지시문을 사용하여 다른 파일의 텍스트를 포함할 수 있음을 @include 알아봅니다.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7361d92b05fd6838d20b32ea9f0b3b14530266fa
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386308"
---
# <a name="t4-include-directive"></a>T4 Include 지시문

Visual Studio 텍스트 템플릿에서 지시문을 사용하여 다른 파일의 텍스트를 포함할 수 `<#@include#>` 있습니다. 텍스트 템플릿에서 첫 번째 클래스 기능 블록 `include` 앞의 어느 곳에나`<#+ ... #>` 지시문을 둘 수 있습니다. 포함된 파일에는 `include` 지시문 및 다른 지시문도 포함할 수 있습니다. 따라서 템플릿 간에 템플릿 코드와 상용구 텍스트를 공유할 수 있습니다.

## <a name="using-include-directives"></a>include 지시문 사용

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` 절대이거나 현재 템플릿 파일을 기준으로 할 수 있습니다.

   또한 특정 Visual Studio 확장은 포함 파일을 검색할 자체 디렉터리를 지정할 수 있습니다. 예를 들어 시각화 및 모델링 SDK(DSL 도구)를 설치한 경우 다음 폴더가 포함 목록에 `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` 추가됩니다.

   이러한 추가적인 포함 폴더는 포함 파일의 파일 확장명에 따라 달라질 수 있습니다. 예를 들어 DSL 도구의 포함 폴더에서는 파일 확장명이 `.tt`인 파일이 있는 포함 파일에만 액세스할 수 있습니다.

- `filePath`는 "%"로 구분되는 환경 변수를 포함할 수 있습니다. 예를 들면 다음과 같습니다.

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- 포함 파일의 이름에 `".tt"` 확장명을 사용할 필요가 없습니다.

   포함 파일에 `".t4"`와 같은 다른 확장명을 사용할 수 있습니다. 이는 프로젝트에 파일을 추가할 때 Visual Studio 자동으로 사용자 지정 도구 속성을 로 `.tt` 설정하기  `TextTemplatingFileGenerator` 때문입니다. 일반적으로 포함된 파일을 개별적으로 변형하지 않을 수 있습니다.

   반면에 파일 확장명에 따라 포함 파일을 검색할 추가 폴더가 영향을 받는 경우가 있다는 사실에 유의해야 합니다. 이는 다른 파일이 들어 있는 포함된 파일이 있는 경우 중요할 수 있습니다.

- 포함된 내용은 포함하는 텍스트 템플릿의 일부인 것처럼 처리됩니다. 그러나 `<#+...#>` 지시문 뒤에 일반 텍스트와 표준 제어 블록이 있는 경우에도 클래스 기능 블록 `include`이 포함된 파일을 포함할 수 있습니다.

- 템플릿이 `once="true"` 두 개 이상의 다른 포함 파일에서 호출되는 경우에도 템플릿이 한 번만 포함되도록 하려면 를 사용합니다.

   이 기능을 사용하면 다른 일부 조각에 이미 포함되어 있다는 걱정 없이 원하는 시간에 포함할 수 있는 재사용 가능한 T4 조각 라이브러리를 쉽게 빌드할 수 있습니다.  예를 들어 템플릿 처리 및 C# 생성을 처리하는 매우 세분화된 조각 라이브러리가 있다고 가정합니다.  또한 예외 생성과 같은 몇 가지 추가 작업 관련 유틸리티에서 이러한 유틸리티를 사용한 다음, 더 많은 애플리케이션별 템플릿에서 사용할 수 있습니다. 종속성 그래프를 그리는 경우 일부 코드 조각이 여러 번 포함될 수 있습니다. 그러나 `once` 매개 변수가 이후에 포함되지 않도록 방지합니다.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **결과적으로 생성된 파일, MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> MSBuild 및 Visual Studio 프로젝트 속성 사용
 include 지시문에서 $(SolutionDir)와 같은 Visual Studio 매크로를 사용할 수 있지만 MSBuild에서는 작동하지 않습니다. 빌드 컴퓨터에서 템플릿을 변형하려는 경우 대신 프로젝트 속성을 사용해야 합니다.

 프로젝트 속성을 정의하기 위해 .csproj 또는 .vbproj 파일을 편집합니다. 이 예제에서는 `myIncludeFolder`라는 속성을 정의합니다.

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 이제 Visual Studio 및 MSBuild에서 모두 올바르게 변환된 텍스트 템플릿의 프로젝트 속성을 사용할 수 있습니다.

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
