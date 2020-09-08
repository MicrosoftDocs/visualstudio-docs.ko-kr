---
title: MSBuild 변환 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34394ba35a349a1564f6c3fdd43052be3e1fdf03
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633111"
---
# <a name="msbuild-transforms"></a>MSBuild 변환

변환은 항목 목록 간의 일대일 변환입니다. 변환을 수행하면 프로젝트가 항목 목록을 변환할 수 있을 뿐만 아니라, 대상이 입력과 출력 간의 직접 매핑을 식별할 수 있습니다. 이 항목에서는 변환 및 MSBuild에서 변환을 사용하여 보다 효율적으로 프로젝트를 빌드하는 방법을 설명합니다.

## <a name="transform-modifiers"></a>변환 한정자

변환은 임의적이지만 모든 변환 한정자가%(\<ItemMetaDataName>) 형식인 특별한 구문으로 제한됩니다. 모든 항목 메타데이터를 변환 한정자로 사용할 수 있습니다. 모든 항목이 생성될 때 할당되는 잘 알려진 항목 메타데이터가 포함됩니다. 잘 알려진 항목 메타데이터의 목록은 [잘 알려진 항목 메타데이터](../msbuild/msbuild-well-known-item-metadata.md)를 참조하세요.

다음 예제에서는 *.resx* 파일 목록이 *.resources* 파일의 목록으로 변환됩니다. %(Filename) 변환 한정자는 각 *.resources* 파일이 해당하는 *.resx* 파일과 동일한 파일 이름을 갖도록 지정합니다.

```xml
@(RESXFile->'%(filename).resources')
```

예를 들어 @(RESXFile) 항목 목록의 항목이 *Form1.resx*, *Form2.resx* 및 *Form3.resx*인 경우 변환 목록의 출력은  *Form1.resources*, *Form2.resources* 및 *Form3.resources*가 됩니다.

> [!NOTE]
> 표준 항목 목록에 구분 기호를 지정한 것과 동일한 방식으로 변환된 항목 목록에 사용자 지정 구분 기호를 지정할 수 있습니다. 예를 들어 기본 세미콜론(;) 대신 쉼표(,)를 사용하여 변환된 항목 목록을 구분하려면 `@(RESXFile->'Toolset\%(filename)%(extension)', ',')` XML을 사용합니다.

## <a name="use-multiple-modifiers"></a>여러 한정자 사용

 변환 식은 순서에 관계 없이 결합되고 반복될 수 있는 여러 개의 한정자를 포함할 수 있습니다. 다음 예제에서는 파일을 포함하는 디렉터리의 이름을 변경하지만 파일의 원래 이름 및 파일 이름 확장명을 유지합니다.

```xml
@(RESXFile->'Toolset\%(filename)%(extension)')
```

 예를 들어 `RESXFile` 항목 목록에 포함된 항목이 *Project1\Form1.resx*, *Project1\Form2.resx* 및 *Project1\Form3.text*인 경우 변환 목록의 출력은 *Toolset\Form1.resx*, *Toolset\Form2.resx* 및 *Toolset\Form3.text*가 됩니다.

## <a name="dependency-analysis"></a>종속성 분석

 변환은 변환 항목 목록과 원래 항목 목록 간에 일대일 매핑을 보장합니다. 따라서 대상이 입력의 변환인 출력을 만드는 경우 MSBuild는 입력 및 출력의 타임 스탬프를 분석하고, 대상을 건너뛰거나, 빌드하거나, 부분적으로 다시 빌드할지를 결정할 수 있습니다.

 다음 예제의 [복사 작업](../msbuild/copy-task.md)에서 `BuiltAssemblies` 항목 목록의 모든 파일은 `Outputs` 특성에서 변환을 사용하여 지정된 작업의 대상 폴더에 있는 파일에 매핑됩니다. `BuiltAssemblies` 항목 목록의 파일이 변경되면 `Copy` 작업은 변경된 파일에 대해서만 실행되고 다른 모든 파일은 건너뜁니다. 종속성 분석 및 변환을 사용하는 방법에 대한 자세한 내용은 [방법: 증분 방식으로 빌드](../msbuild/how-to-build-incrementally.md)를 참조하세요.

```xml
<Target Name="CopyOutputs"
    Inputs="@(BuiltAssemblies)"
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">

    <Copy
        SourceFiles="@(BuiltAssemblies)"
        DestinationFolder="$(OutputPath)"/>

</Target>
```

## <a name="example"></a>예제

### <a name="description"></a>설명

 다음 예제에서는 변환을 사용하는 MSBuild 프로젝트 파일을 보여 줍니다. 이 예제에서는 *c:\sub0\sub1\sub2\sub3* 디렉터리에 *.xsd* 파일 하나만 있고 작업 디렉터리가 *c:\sub0*이라고 가정합니다.

### <a name="code"></a>코드

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Schema Include="sub1\**\*.xsd"/>
    </ItemGroup>

    <Target Name="Messages">
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>
        <Message Text="identity: @(Schema->'%(identity)')"/>
        <Message Text="filename: @(Schema->'%(filename)')"/>
        <Message Text="directory: @(Schema->'%(directory)')"/>
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>
        <Message Text="extension: @(Schema->'%(extension)')"/>
    </Target>
</Project>
```

### <a name="comments"></a>주석

 이 예제는 다음과 같은 출력을 생성합니다.

```
rootdir: C:\
fullpath: C:\sub0\sub1\sub2\sub3\myfile.xsd
rootdir + directory + filename + extension: C:\sub0\sub1\sub2\sub3\myfile.xsd
identity: sub1\sub2\sub3\myfile.xsd
filename: myfile
directory: sub0\sub1\sub2\sub3\
relativedir: sub1\sub2\sub3\
extension: .xsd
```

## <a name="see-also"></a>참조

- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [방법: 증분 방식으로 빌드](../msbuild/how-to-build-incrementally.md)
