---
title: MSBuild 조건부 구문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7b22f63d5d3d6e0b1f7789561029bbfbfb4cdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143752"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild 조건부 구문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) 및 [Otherwise](../msbuild/otherwise-element-msbuild.md) 요소를 포함하는 / 또는 처리에 메커니즘을 제공합니다.  
  
## <a name="using-the-choose-element"></a>Choose 요소 사용  
 `Choose` 요소에는 `true`로 계산될 때까지 위쪽에서 아래쪽 순서로 테스트되는 `Condition` 특성을 포함한 일련의 `When` 요소가 포함됩니다. 하나 이상의 `When` 요소가 `true`로 계산되면 첫 번째 요소만 사용합니다. `Otherwise` 요소가 있는 경우 `When` 요소에 대한 조건이 `true`로 계산되는지를 평가합니다.  
  
 `Choose` 요소를 `Project`, `When` 및 `Otherwise` 요소의 자식 요소로 사용할 수 있습니다. `When` 및 `Otherwise` 요소에는 `ItemGroup`, `PropertyGroup` 또는 `Choose` 자식 요소가 포함됩니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 / 또는 처리 중 하나에 `Choose` 및 `When` 요소를 사용합니다. 프로젝트의 속성 및 항목은 `Configuration` 속성의 값에 따라 설정됩니다.  
  
```  
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
  
## <a name="see-also"></a>관련 항목  
 [Choose 요소 (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When 요소 (MSBuild)](../msbuild/when-element-msbuild.md)   
 [그렇지 않으면 요소 (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)
