---
title: Choose 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4f699b4ffc9372af0c803d094390544932d652b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634476"
---
# <a name="choose-element-msbuild"></a>Choose 요소(MSBuild)

자식 요소를 평가하여 평가할 `ItemGroup` 요소 및/또는 `PropertyGroup` 요소의 집합 하나를 선택합니다.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>구문

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|선택적 요소입니다.<br /><br /> 모든 `When` 요소의 조건이 `false`로 평가될 경우 평가할 코드 `PropertyGroup` 및 `ItemGroup` 요소의 블록을 지정합니다. `Choose` 요소에 0개 이상의 `Otherwise` 요소가 있을 수 있으며 마지막 요소여야 합니다.|
|[When](../msbuild/when-element-msbuild.md)|필수적 요소입니다.<br /><br /> `Choose` 요소에서 선택할 수 있는 가능한 코드 블록을 지정합니다. `Choose` 요소에는 `When` 요소가 하나 이상 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [Otherwise](../msbuild/otherwise-element-msbuild.md) | 모든 `When` 요소가 `false`로 평가될 경우 실행할 코드 블록을 지정합니다. |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |
| [When](../msbuild/when-element-msbuild.md) | `Choose` 요소에서 선택할 수 있는 가능한 코드 블록을 지정합니다. |

## <a name="remarks"></a>설명

 `Choose`, `When` 및 `Otherwise` 요소는 몇 가지 가능한 대안 중에서 실행할 코드의 한 섹션을 선택하는 방법을 제공하기 위해 함께 사용됩니다. 자세한 내용은 [조건부 구문](../msbuild/msbuild-conditional-constructs.md)을 참조하세요.

## <a name="example"></a>예

 다음 프로젝트에서는 `Choose` 요소를 사용하여 설정할 `When` 요소의 속성 값 집합을 선택합니다. 두 `When` 요소의 `Condition` 특성이 모두 `false`로 평가되면 `Otherwise` 요소의 속성 값이 설정됩니다.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
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
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>추가 정보

- [조건부 구문](../msbuild/msbuild-conditional-constructs.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
