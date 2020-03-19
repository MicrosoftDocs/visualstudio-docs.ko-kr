---
title: GetAssemblyIdentity 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a09bd4955cee6e50368f7155fb2e03c2c1758bf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634021"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity 작업

지정된 파일에서 어셈블리 ID를 검색하고 ID 정보를 출력합니다.

## <a name="task-parameters"></a>작업 매개 변수

다음 표에서는 `GetAssemblyIdentity` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Assemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 검색된 어셈블리 ID를 포함합니다.|
|`AssemblyFiles`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> ID를 검색할 파일을 지정합니다.|

## <a name="remarks"></a>설명

`Assemblies` 매개 변수에 의한 항목 출력에는 `Version`, `PublicKeyToken` 및 `Culture`라는 항목 메타데이터 항목이 포함됩니다.

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `MyAssemblies` 항목을 지정한 파일의 ID를 검색하고 `MyAssemblyIdentities` 항목에 출력합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
