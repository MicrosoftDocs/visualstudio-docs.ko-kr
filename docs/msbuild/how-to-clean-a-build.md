---
title: '방법: 빌드 정리 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b7848189c866481e6e97d05d95b5fb97a3d4893
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633917"
---
# <a name="how-to-clean-a-build"></a>방법: 빌드 정리

빌드를 정리할 때 프로젝트 및 구성 요소 파일을 그대로 두고 모든 중간 파일과 출력 파일이 삭제됩니다. 그런 다음 프로젝트 및 구성 요소 파일에서 중간 파일과 출력 파일의 새 인스턴스를 빌드할 수 있습니다. 

## <a name="create-a-directory-for-output-items"></a>출력 항목에 대한 디렉터리 만들기

 기본적으로 프로젝트를 컴파일할 때 만들어진 *.exe* 파일은 프로젝트 및 원본 파일과 동일한 디렉터리에 배치됩니다. 그러나 일반적으로 출력 항목은 별도 디렉터리에 생성됩니다.

### <a name="to-create-a-directory-for-output-items"></a>출력 항목에 대한 디렉터리를 만들려면

1. `Property` 요소를 사용하여 디렉터리의 위치 및 이름을 정의합니다. 예를 들어 프로젝트 및 원본 파일이 포함된 디렉터리에 *BuiltApp*이라는 디렉터리를 만듭니다.

     `<builtdir>BuiltApp</builtdir>`

2. 디렉터리가 없는 경우 [MakeDir](../msbuild/makedir-task.md) 작업을 사용하여 디렉터리를 만듭니다. 예를 들어:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>출력 항목 제거

 중간 파일 및 출력 파일의 새 인스턴스를 만들기 전에 중간 파일 및 출력 파일의 모든 이전 인스턴스를 취소할 수 있습니다. [RemoveDir](../msbuild/removedir-task.md) 작업을 사용하여 디렉터리 및 모든 파일과 디스크에서 포함하는 디렉터리를 삭제합니다.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>디렉터리에 포함된 디렉터리 및 모든 파일을 제거하려면

- `RemoveDir` 작업을 사용하여 디렉터리를 제거합니다. 예를 들어:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>예제

 다음 코드 예제 프로젝트는 `RemoveDir` 작업을 사용하여 디렉터리 및 모든 파일과 포함하는 디렉터리를 삭제하는 새 대상 `Clean`을 포함합니다. 또한 이 예제에서 `Compile` 대상은 빌드가 정리될 때 삭제된 출력 항목에 대한 별도 디렉터리를 만듭니다.

 `Compile`은 기본 대상으로 정의되므로 다른 대상 또는 대상을 지정하지 않으면 자동으로 사용됩니다. 명령줄 스위치 **-target**을 사용하여 다른 대상을 지정합니다. 예를 들어:

 `msbuild <file name>.proj -target:Clean`

 **-target** 스위치는 **-t**로 단축할 수 있으며 둘 이상의 대상을 지정할 수 있습니다. 예를 들어 대상 `Compile` 대신 `Clean` 대상을 사용하려면 다음을 입력합니다.

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <!-- Set the application name as a property -->
        <name>HelloWorldCS</name>

        <!-- Set the output folder as a property -->
        <builtdir>BuiltApp</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <!-- Specify the inputs by type and file name -->
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Check whether an output folder exists and create
        one if necessary -->
        <MakeDir Directories = "$(builtdir)"
            Condition = "!Exists('$(builtdir)')" />

        <!-- Run the Visual C# compiler -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(BuiltDir)\$(appname).exe">
            <Output TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>

        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>

    <Target Name = "Clean">
        <RemoveDir Directories="$(builtdir)" />
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [MakeDir 작업](../msbuild/makedir-task.md)
- [RemoveDir 작업](../msbuild/removedir-task.md)
- [Csc 작업](../msbuild/csc-task.md)
- [대상](../msbuild/msbuild-targets.md)
