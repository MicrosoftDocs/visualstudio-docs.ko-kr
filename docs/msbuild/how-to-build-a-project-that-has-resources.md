---
title: '방법: 리소스를 사용하는 프로젝트 빌드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a76246096eec8779ce331e93f01be5ab791d1cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633956"
---
# <a name="how-to-build-a-project-that-has-resources"></a>방법: 리소스를 사용하는 프로젝트 빌드

프로젝트의 현지화된 버전을 빌드할 경우 모든 사용자 인터페이스 요소를 언어에 따라 다른 리소스 파일로 분리해야 합니다. 프로젝트에서 문자열만 사용할 경우 리소스 파일에는 텍스트 파일이 사용됩니다. 또는 *.resx* 파일을 리소스 파일로 사용할 수 있습니다.

## <a name="compile-resources-with-msbuild"></a>MSBuild를 사용하여 리소스 컴파일

MSBuild와 함께 제공되는 일반 작업 라이브러리에는 *.resx* 또는 text 파일에서 리소스를 컴파일하는 데 사용할 수 있는 `GenerateResource` 작업이 포함됩니다. 이 작업에는 컴파일할 리소스 파일을 지정하는 `Sources` 매개 변수와 출력 리소스 파일의 이름을 지정하는 `OutputResources` 매개 변수가 포함됩니다. `GenerateResource` 작업에 대한 자세한 내용은 [GenerateResource 작업](../msbuild/generateresource-task.md)을 참조하세요.

#### <a name="to-compile-resources-with-msbuild"></a>MSBuild를 사용하여 리소스를 컴파일하려면

1. 프로젝트의 리소스 파일을 확인하고 `GenerateResource` 작업에 항목 목록 또는 파일 이름으로 전달합니다.

2. 출력 리소스 파일의 이름을 설정할 수 있는 `GenerateResource` 작업의 `OutputResources` 매개 변수를 지정합니다.

3. 작업의 `Output` 요소를 사용하여 `OutputResources` 매개 변수 값을 항목에 저장합니다.

4. `Output` 요소에서 생성된 항목을 다른 작업에 대한 입력으로 사용합니다.

## <a name="example"></a>예제

다음 코드 예제에서는 `Output` 요소를 사용하여 `GenerateResource` 작업의 `OutputResources` 특성에 컴파일된 리소스 파일 *alpha.resources* 및 *beta.resources*가 포함되고 이러한 두 파일이 `Resources` 항목 목록 내에 배치되도록 지정하는 방법을 보여 줍니다. 이러한 *.resources* 파일을 같은 이름의 항목 모음으로 식별하면 해당 파일을 [Csc](../msbuild/csc-task.md) 작업 등의 다른 작업에 대한 입력으로 쉽게 사용할 수 있습니다.

이 작업은 [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)에 **/compile** 스위치를 사용하는 것과 같습니다.

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example"></a>예제

다음 예제 프로젝트에는 리소스를 컴파일하는 `GenerateResource` 작업 및 소스 코드 파일과 컴파일된 리소스 파일을 둘 다 컴파일하는 `Csc` 작업이 포함됩니다. `GenerateResource` 작업으로 컴파일된 리소스 파일은 `Resources` 항목에 저장되고 `Csc` 작업에 전달됩니다.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource 작업](../msbuild/generateresource-task.md)
- [Csc 작업](../msbuild/csc-task.md)
- [Resgen.exe(리소스 파일 생성기)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
