---
title: T4 Assembly 지시문
description: Visual Studio 디자인 타임 텍스트 템플릿에서 어셈블리 지시문은 템플릿 코드에서 해당 형식을 사용할 수 있도록 어셈블리를 로드 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38b5a7fe2308884d4837a068770af67435ada70e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386360"
---
# <a name="t4-assembly-directive"></a>T4 Assembly 지시문

Visual Studio 디자인 타임 텍스트 템플릿에서 `assembly` 지시문은 템플릿 코드에서 해당 형식을 사용할 수 있도록 어셈블리를 로드 합니다. 결과는 Visual Studio 프로젝트에 어셈블리 참조를 추가 하는 것과 비슷합니다.

 텍스트 템플릿 작성에 대 한 일반적인 개요는 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

> [!NOTE]
> 전처리된 런타임 텍스트 템플릿에는 `assembly` 지시문이 필요하지 않습니다. 대신 Visual Studio 프로젝트의 **참조** 에 필요한 어셈블리를 추가 합니다.

## <a name="using-the-assembly-directive"></a>assembly 지시문 사용
 지시문의 구문은 다음과 같습니다.

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 어셈블리 이름은 다음 중 하나여야 합니다.

- GAC 어셈블리의 강력한 이름(예: `System.Xml.dll`). `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`와 같은 긴 형식도 사용할 수 있습니다. 자세한 내용은 <xref:System.Reflection.AssemblyName>를 참조하세요.

- 어셈블리의 절대 경로

  구문을 사용 하 여와 `$(variableName)` 같은 Visual Studio 변수를 참조 하 `$(SolutionDir)` 고 `%VariableName%` 환경 변수를 참조할 수 있습니다. 예를 들면 다음과 같습니다.

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 assembly 지시문은 전처리된 텍스트 템플릿에서 아무런 효과가 없습니다. 대신 Visual Studio 프로젝트의 **참조** 섹션에 필요한 참조를 포함 합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조하세요.

## <a name="standard-assemblies"></a>표준 어셈블리
 다음 어셈블리가 자동으로 로드되므로 해당 어셈블리에 대한 assembly 지시문을 작성할 필요가 없습니다.

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  사용자 지정 지시문을 사용하는 경우 지시문 프로세서에서 추가 어셈블리를 로드할 수 있습니다. 예를 들어 DSL(Domain-Specific Language)을 위한 템플릿을 작성하는 경우 다음 어셈블리에 대한 assembly 지시문을 작성할 필요가 없습니다.

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- DSL이 들어 있는 어셈블리

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> MSBuild 및 Visual Studio에서 프로젝트 속성 사용
 $ (솔루션 디렉터리)와 같은 Visual Studio 매크로는 MSBuild에서 작동 하지 않습니다. 빌드 컴퓨터에서 템플릿을 변형하려는 경우 대신 프로젝트 속성을 사용해야 합니다.

 프로젝트 속성을 정의하기 위해 .csproj 또는 .vbproj 파일을 편집합니다. 이 예제에서는 `myLibFolder`라는 속성을 정의합니다.

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 이제 Visual Studio 및 MSBuild에서 모두 올바르게 변환된 텍스트 템플릿의 프로젝트 속성을 사용할 수 있습니다.

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>참조

- [T4 Include 지시문](../modeling/t4-include-directive.md)
