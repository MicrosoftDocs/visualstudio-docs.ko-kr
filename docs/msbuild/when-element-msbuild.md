---
title: When 요소(MSBuild) | Microsoft Docs
description: 선택할 Choose 요소에 가능한 코드 블록을 지정하는 MSBuild When 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36d96eacc0fbc88a3fcf082493e064a77c5c403a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933819"
---
# <a name="when-element-msbuild"></a>When 요소(MSBuild)

`Choose` 요소에서 선택할 수 있는 가능한 코드 블록을 지정합니다.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>구문

```xml
<When Condition="'StringA'=='StringB'">
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</When>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|조건|필수 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Choose](../msbuild/choose-element-msbuild.md)|선택적 요소입니다.<br /><br /> 자식 요소를 평가하여 실행할 코드의 한 섹션을 선택합니다. `Choose` 요소에는 `When` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 사용자 정의 [Item](../msbuild/item-element-msbuild.md) 요소 집합을 포함합니다. `ItemGroup` 요소에는 `When` 요소가 0개 또는 그 이상 있을 수 있습니다.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 사용자 정의 [Property](../msbuild/property-element-msbuild.md) 요소 집합을 포함합니다. `PropertyGroup` 요소에는 `When` 요소가 0개 또는 그 이상 있을 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Choose 요소(MSBuild)](../msbuild/choose-element-msbuild.md)|자식 요소를 평가하여 실행할 코드의 한 섹션을 선택합니다.|

## <a name="remarks"></a>설명

 `Condition` 특성이 true로 평가되면 `When` 요소의 자식 `ItemGroup` 및 `PropertyGroup` 요소가 실행되고 모든 후속 `When` 요소가 생략됩니다.

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
