---
title: 빌드 시스템 사용자 지정
description: 이 아티클에서는 Mac용 Visual Studio에서 사용하는 MSBuild 빌드 시스템을 간략히 소개합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128385"
---
# <a name="customizing-the-build-system"></a>빌드 시스템 사용자 지정

Microsoft Build Engine은 애플리케이션을 빌드하기 위한 플랫폼입니다. MSBuild라고도 하는 이 엔진은 Microsoft에서 개발되었으며 .NET 애플리케이션의 빌드에 사용됩니다. Mono 프레임워크에는 **xbuild**라는 Microsoft 빌드 엔진의 자체 구현도 있습니다. 그러나 현재 xbuild는 단계적으로 사용이 중단되었으며, 모든 운영 체제에서 MSBuild가 사용됩니다.

**MSBuild**는 Mac용 Visual Studio에서 프로젝트의 빌드 시스템으로 사용되며 소스 파일 등의 입력 집합을 가져와 작업하고 실행 파일 등의 출력으로 변환합니다. 컴파일러 등의 도구를 호출하면 이 출력을 얻을 수 있습니다.

## <a name="msbuild-file"></a>MSBuild 파일

MSBuild는 프로젝트 파일이라는 XML 파일을 사용합니다. 이 파일은 프로젝트의 일부인 *항목*(예: 이미지 리소스)과 프로젝트를 빌드하는 데 필요한 *속성*을 정의합니다. 이 프로젝트 파일의 파일 확장명은 C# 프로젝트의 `.csproj`와 같이 항상 `proj`로 끝납니다.

### <a name="viewing-the-msbuild-file"></a>MSBuild 파일 보기

프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **찾기에 표시**를 선택하여 MSBuild 파일을 찾습니다. 찾기 창에는 다음 이미지와 같이 `.csproj` 파일을 비롯하여 프로젝트와 관련된 모든 파일과 폴더가 표시됩니다.

![Finder에서 csproj 위치](media/customizing-build-system-image1.png)

Mac용 Visual Studio의 새 탭에서 `.csproj`를 표시하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **도구 > 파일 편집**으로 이동합니다.

![원본 편집기에서 csproj 열기](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>MSBuild 파일의 컴퍼지션

모든 MSBuild 파일에는 다음과 같이 필수 루트 `Project` 요소가 포함되어 있습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

일반적으로 프로젝트는 `.targets` 파일도 가져옵니다. 이 파일에는 다양한 파일을 처리하고 빌드하는 방법을 설명하는 많은 규칙이 포함되어 있습니다. 가져오기는 일반적으로 `proj` 파일의 아래쪽에 표시되며, C# 프로젝트의 경우 다음과 같이 표시됩니다.

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

대상 파일은 다른 MSBuild 파일입니다. 이 파일에는 여러 프로젝트에서 다시 사용할 수 있는 MSBuild 코드가 들어 있습니다. 예를 들어 `MSBuildBinPath` 속성(또는 변수)이 나타내는 디렉터리의 `Microsoft.CSharp.targets` 파일에는 C# 소스 파일에서 C# 어셈블리를 빌드하기 위한 논리가 포함되어 있습니다.

### <a name="items-and-properties"></a>항목 및 속성

MSBuild에는 두 가지 기본적인 데이터 형식인 ‘항목’ 및 ‘속성’이 있습니다. 두 데이터 형식은 다음 섹션에서 자세히 설명합니다.  

#### <a name="properties"></a>속성

속성은 키/값 쌍으로, 컴파일러 옵션 등 컴파일에 영향을 주는 설정을 저장하는 데 사용됩니다.

PropertyGroup을 사용하여 설정되며, 임의 개수의 속성을 포함하는 임의 개수의 PropertiesGroup을 포함할 수 있습니다.

예를 들어, 간단한 콘솔 애플리케이션의 PropertyGroup은 다음 XML과 같이 표시될 수 있습니다.

```xml
<PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
    <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <RootNamespace>refactoring</RootNamespace>
    <AssemblyName>refactoring</AssemblyName>
    <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
</PropertyGroup>
```

`$()` 구문을 사용하여 식에서 속성을 참조할 수 있습니다. 예를 들어 `$(Foo)`는 `Foo` 속성의 값으로 평가됩니다. 속성을 설정하지 않은 경우 오류 없이 빈 문자열로 평가됩니다.

#### <a name="items"></a>Items

항목은 빌드 시스템에 대한 입력을 목록 또는 집합으로 처리하는 방법을 제공하며, 일반적으로 파일을 나타냅니다. 각 항목에는 항목 *종류*, 항목 *사양*, 선택적 임의 *메타데이터*가 있습니다. MSBuild는 개별 항목에서 작동하지 않고, 항목 *집합*이라는 지정된 형식의 모든 항목을 사용합니다.

`ItemGroup`을 선언하여 항목을 만듭니다. 임의 개수의 항목을 포함하는 임의 개수의 ItemGroup이 있을 수 있습니다.

예를 들어, 다음 코드 조각은 iOS 시작 화면을 만듭니다. 시작 화면에는 사양이 이미지 경로로 지정된 빌드 형식 `BundleResource`가 있습니다.

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 `@()` 구문을 사용하여 식에서 항목 집합을 참조할 수 있습니다. 예를 들어 `@(BundleResource)`는 모든 BundleResource 항목을 의미하는 BundleResource 항목 집합으로 평가됩니다. 이 형식의 항목이 없는 경우 오류 없이 비어 있습니다.

## <a name="resources-for-learning-msbuild"></a>MSBuild 학습용 리소스

다음 리소스를 사용하여 MSBuild에 대해 자세히 알아볼 수 있습니다.

* [MSBuild 개요](/visualstudio/msbuild/msbuild)
* [MSBuild 개념](/visualstudio/msbuild/msbuild-concepts)
