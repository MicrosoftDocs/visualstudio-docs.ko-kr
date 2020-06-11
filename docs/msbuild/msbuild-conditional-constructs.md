---
title: MSBuild 조건부 구문 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7d6693a24d208cab6bd3b58ce16dcba8a32b190
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184291"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 조건부 구문

MSBuild는 [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) 및 [Otherwise](../msbuild/otherwise-element-msbuild.md) 요소를 포함하는 / 또는 처리 중 하나에 메커니즘을 제공합니다.

## <a name="use-the-choose-element"></a>Choose 요소 사용

 `Choose` 요소에는 `true`로 계산될 때까지 위쪽에서 아래쪽 순서로 테스트되는 `Condition` 특성을 포함한 일련의 `When` 요소가 포함됩니다. 하나 이상의 `When` 요소가 `true`로 계산되면 첫 번째 요소만 사용합니다. `Otherwise` 요소가 있는 경우 `When` 요소에 대한 조건이 `true`로 계산되는지를 평가합니다.

 `Choose` 요소를 `Project`, `When` 및 `Otherwise` 요소의 자식 요소로 사용할 수 있습니다. `When` 및 `Otherwise` 요소에는 `ItemGroup`, `PropertyGroup` 또는 `Choose` 자식 요소가 포함됩니다.

## <a name="example"></a>예제

 다음 예제에서는 / 또는 처리 중 하나에 `Choose` 및 `When` 요소를 사용합니다. 프로젝트의 속성 및 항목은 `Configuration` 속성의 값에 따라 설정됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
    </Choose>
    <!-- Rest of Project -->
</Project>
```

이 예제에서는 컴파일러 상수 `DEFINED_CONSTANT`의 조건이 사용됩니다. 이러한 요소는 `DefinedConstants` 속성에 포함되어 있습니다. 정규식은 세미콜론으로 구분된 목록의 정확한 상수를 찾는 데 사용됩니다.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>참조

- [Choose 요소(MSBuild)](../msbuild/choose-element-msbuild.md)
- [When 요소(MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise 요소(MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
