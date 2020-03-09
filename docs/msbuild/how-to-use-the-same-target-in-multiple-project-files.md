---
title: '방법: 여러 프로젝트 파일에서 동일한 대상 사용 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633761"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>방법: 여러 프로젝트 파일에서 동일한 대상 사용

여러 MSBuild 프로젝트 파일을 만들었다면 여러 프로젝트 파일에서 동일한 작업 및 대상을 사용해야 한다는 사실을 알게 되었을 것입니다. 모든 프로젝트 파일에 이러한 작업이나 대상에 대한 완전한 설명을 포함하는 대신, 대상을 별도 프로젝트 파일에 저장한 다음, 해당 대상을 사용해야 하나ㅡㄴ 다른 프로젝트로 해당 프로젝트를 가져올 수 있습니다.
## <a name="use-the-import-element"></a>Import 요소 사용

 `Import` 요소는 한 프로젝트 파일을 다른 프로젝트 파일에 삽입하는 데 사용됩니다. 가져올 프로젝트 파일은 유효한 MSBuild 프로젝트 파일이어야 하며 올바른 형식의 XML을 포함해야 합니다. `Project` 특성은 가져온 프로젝트 파일의 경로를 지정합니다. `Import` 요소에 대한 자세한 내용은 [Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)를 참조하세요.
`Import` 요소는 한 프로젝트 파일을 다른 프로젝트 파일에 삽입하는 데 사용됩니다. 가져올 프로젝트 파일은 유효한 MSBuild 프로젝트 파일이어야 하며 올바른 형식의 XML을 포함해야 합니다. `Project` 특성은 가져온 프로젝트 파일의 경로를 지정합니다. `Import` 요소에 대한 자세한 내용은 [Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)를 참조하세요.

#### <a name="to-import-a-project"></a>프로젝트를 가져오려면

1. 가져온 프로젝트의 속성 및 항목에 대한 매개 변수로 사용되는 모든 속성 및 항목을 가져오기 프로젝트 파일에 정의합니다.

2. `Import` 요소를 사용하여 프로젝트를 가져옵니다. 예를 들어:

     `<Import Project="MyCommon.targets"/>`

3. `Import` 요소 다음에, 가져온 프로젝트의 속성 및 항목의 기본 정의를 재정의해야 하는 모든 속성 및 항목을 프로젝트 파일에 정의합니다.

## <a name="order-of-evaluation"></a>계산 순서

 MSBuild가 `Import` 요소에 도달하면 가져온 프로젝트는 `Import` 요소의 해당 위치에 있는 가져오기 프로젝트에 효과적으로 삽입됩니다. 따라서 `Import` 요소의 위치는 속성 및 항목의 값에 영향을 줄 수 있습니다. 가져온 프로젝트에 의해 설정된 속성 및 항목과 가져온 프로젝트가 사용하는 속성 및 항목을 이해하는 것이 중요합니다.

 프로젝트가 빌드될 때 모든 속성이 먼저 평가된 후 항목이 평가됩니다. 예를 들어, 다음 XML은 가져온 프로젝트 파일 *MyCommon.targets*를 정의합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 다음 XML은 *MyCommon.targets*를 가져오는 *MyApp.proj*를 정의합니다.

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 프로젝트가 빌드될 때 다음과 같은 메시지가 표시됩니다.

 `Name="MyCommon"`

 속성 `Name`이 *MyApp.proj*에 정의된 이후에 프로젝트를 가져오므로 *MyCommon.targets*의 `Name` 정의가 *MyApp.proj*가 정의를 재정의합니다. 속성 Name이 정의되기 전에 프로젝트를 가져오면 빌드는 다음 메시지를 표시합니다.

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>프로젝트를 가져올 때 다음 방법 사용

1. 가져온 프로젝트의 속성 및 항목에 대한 매개 변수로 사용되는 모든 속성 및 항목을 프로젝트 파일에 정의합니다.

2. 프로젝트를 가져옵니다.

3. 가져온 프로젝트의 속성 및 항목의 기본 정의를 재정의해야 하는 모든 속성 및 항목을 프로젝트 파일에 정의합니다.

## <a name="example"></a>예제

 다음 코드 예제에서는 두 번째 코드 예제에서 가져오는 *MyCommon.targets* 파일을 보여 줍니다. *.targets* 파일은 가져오기 프로젝트의 속성을 평가하여 빌드를 구성합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>예제

 다음 코드 예제에서는 *MyCommon.targets* 파일을 가져옵니다.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>참조

- [Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)
- [대상](../msbuild/msbuild-targets.md)
