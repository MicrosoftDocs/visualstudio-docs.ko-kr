---
title: Otherwise 요소(MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acf285c895e5160e850b6bc8f20f920279a5e26c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154786"
---
# <a name="otherwise-element-msbuild"></a>Otherwise 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 `When` 요소가 `false`로 평가될 경우에만 실행할 코드 블록을 지정합니다.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>구문  
  
```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[선택](../msbuild/choose-element-msbuild.md)|선택적 요소입니다.<br /><br /> 자식 요소를 평가하여 실행할 코드의 한 섹션을 선택합니다. `Choose` 요소에는 `Otherwise` 요소가 0개 또는 그 이상 있을 수 있습니다.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 사용자 정의 [Item](../msbuild/item-element-msbuild.md) 요소 집합을 포함합니다. `ItemGroup` 요소에는 `Otherwise` 요소가 0개 또는 그 이상 있을 수 있습니다.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|선택적 요소입니다.<br /><br /> 사용자 정의 [Property](../msbuild/property-element-msbuild.md) 요소 집합을 포함합니다. `PropertyGroup` 요소에는 `Otherwise` 요소가 0개 또는 그 이상 있을 수 있습니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[선택](../msbuild/choose-element-msbuild.md)|자식 요소를 평가하여 실행할 코드의 한 섹션을 선택합니다.|  
  
## <a name="remarks"></a>설명  
 `Choose` 요소에 `Otherwise` 요소가 1개만 있을 수 있으며 마지막 요소여야 합니다.  
  
 `Choose`, `When` 및 `Otherwise` 요소는 몇 가지 가능한 대안 중에서 실행할 코드의 한 섹션을 선택하는 방법을 제공하기 위해 함께 사용됩니다. 자세한 내용은 [조건부 구문](../msbuild/msbuild-conditional-constructs.md)을 참조하세요.  
  
## <a name="example"></a>예  
 다음 프로젝트에서는 `Choose` 요소를 사용하여 설정할 `When` 요소의 속성 값 집합을 선택합니다. 두 `When` 요소의 `Condition` 특성이 모두 `false`로 평가되면 `Otherwise` 요소의 속성 값이 설정됩니다.  
  
```  
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
  
## <a name="see-also"></a>관련 항목  
 [조건부 구문](../msbuild/msbuild-conditional-constructs.md)   
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
