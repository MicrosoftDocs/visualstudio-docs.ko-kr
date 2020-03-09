---
title: '방법: 빌드할 파일 선택 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0566078c7f90faf204c35024e2c308b5ef881c01
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633813"
---
# <a name="how-to-select-the-files-to-build"></a>방법: 빌드할 파일 선택

여러 파일이 포함된 프로젝트를 빌드할 경우 각 파일을 프로젝트 파일에 개별적으로 나열하거나, 와일드카드를 사용하여 모든 파일을 하나의 디렉터리 또는 중첩된 디렉터리 집합에 포함할 수 있습니다.

## <a name="specify-inputs"></a>입력 지정

항목은 빌드의 입력을 나타냅니다. 항목에 대한 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

빌드용 파일을 포함하려면 파일이 MSBuild 프로젝트 파일의 항목 목록에 포함되어야 합니다. 파일을 개별적으로 포함하거나 와일드카드를 사용하여 많은 파일을 한 번에 포함하는 방식으로 여러 파일을 항목 목록에 추가할 수 있습니다.

#### <a name="to-declare-items-individually"></a>항목을 개별적으로 선언하려면

- 다음과 비슷한 `Include` 특성을 사용합니다.

    `<CSFile Include="form1.cs"/>`

    또는

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > 항목 컬렉션의 항목이 프로젝트 파일과 같은 디렉터리에 있지 않으면 항목의 전체 또는 상대 경로를 지정해야 합니다. 예를 들어 `Include="..\..\form2.cs"`을 참조하십시오.

#### <a name="to-declare-multiple-items"></a>여러 항목을 선언하려면

- 다음과 비슷한 `Include` 특성을 사용합니다.

    `<CSFile Include="form1.cs;form2.cs"/>`

    또는

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>와일드카드를 사용하여 입력 지정

와일드카드를 사용하여 하위 디렉터리의 모든 파일 또는 특정 파일만 빌드의 입력으로 재귀적으로 포함할 수도 있습니다. 와일드카드에 대한 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

다음 예제는 프로젝트 파일이 *Project* 디렉터리에 있는, 다음 디렉터리와 하위 디렉터리에 그래픽 파일이 포함된 프로젝트를 기반으로 합니다.

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>*Images* 디렉터리 및 하위 디렉터리의 모든 *.jpg* 파일을 포함하려면

- 다음 `Include` 특성을 사용합니다.

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>*img*로 시작하는 모든 *.jpg* 파일을 포함하려면

- 다음 `Include` 특성을 사용합니다.

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>디렉터리에서 이름이 *jpgs*로 끝나는 모든 파일을 포함하려면

- 다음 `Include` 특성 중 하나를 사용합니다.

    `Include="Images\**\*jpgs\*.*"`

    또는

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>작업에 항목 전달

프로젝트 파일에서 @() 표기법을 사용하여 전체 항목 목록을 빌드의 입력으로 지정할 수 있습니다. 모든 파일을 개별적으로 나열하든지, 와일드카드를 사용하든지 관계없이 이 표기법을 사용할 수 있습니다.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>모든 Visual C# 또는 Visual Basic 파일을 입력으로 사용하려면

- 다음과 비슷한 `Include` 특성을 사용합니다.

    `<CSC Sources="@(CSFile)">...</CSC>`

    또는

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> 항목과 함께 와일드카드를 사용하여 빌드의 입력을 지정해야 합니다. 입력을 지정하는 데 [Csc](../msbuild/csc-task.md) 또는 [Vbc](../msbuild/vbc-task.md)와 같은 MSBuild 작업의 `Sources` 특성을 사용할 수는 없습니다. 다음 예제는 프로젝트 파일에서 유효하지 않습니다.
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example"></a>예제

다음 코드 예제에서는 모든 입력 파일을 개별적으로 포함하는 프로젝트를 보여 줍니다.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example"></a>예제

다음 코드 예제에서는 와일드카드를 사용하여 모든 *.cs* 파일을 포함합니다.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [방법: 빌드에서 파일 제외](../msbuild/how-to-exclude-files-from-the-build.md)
- [항목](../msbuild/msbuild-items.md)
