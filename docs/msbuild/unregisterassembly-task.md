---
title: UnregisterAssembly 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8cddcf9bf0632914d1a6de1cc904dbf0f173e6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631499"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly 작업

COM interop 용도로 지정된 어셈블리의 등록을 취소합니다. [RegisterAssembly 작업](../msbuild/registerassembly-task.md)의 역작업을 수행합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `UnregisterAssembly` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Assemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 등록을 취소할 어셈블리를 지정합니다.|
|`AssemblyListFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> `RegisterAssembly` 작업 및 `UnregisterAssembly` 작업 간의 상태 정보를 포함합니다. 이를 통해 작업이 `RegisterAssembly` 작업에서 등록되지 못한 어셈블리의 등록을 취소하려고 하는 시도를 방지합니다.<br /><br /> 이 매개 변수를 지정하는 경우 `Assemblies` 및 `TypeLibFiles` 매개 변수는 무시됩니다.|
|`TypeLibFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 지정된 어셈블리에서 지정된 형식 라이브러리의 등록을 취소합니다. **참고:** 이 매개 변수는 형식 라이브러리 파일 이름이 어셈블리 이름과 다른 경우에 필요합니다.|

## <a name="remarks"></a>설명

 이 작업이 성공하기 위해 이 어셈블리가 있어야 할 필요는 없습니다. 존재하지 않는 어셈블리의 등록을 취소하려고 하면 작업은 성공하지만 경고가 발생합니다. 이 작업의 해당 작업이 레지스트리에서 어셈블리 등록을 제거하는 것이기 때문입니다. 어셈블리가 없으면 레지스트리에 없으므로 작업은 성공합니다.

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension> 클래스에서 직접 상속하는 <xref:System.MarshalByRefObject> 클래스의 매개 변수도 상속합니다. `MarshalByRefObject` 클래스는 <xref:Microsoft.Build.Utilities.Task> 클래스와 동일한 기능을 제공하지만 해당 애플리케이션 도메인에서 인스턴스화될 수 있습니다.

## <a name="example"></a>예제

 다음 예제에서는 `UnregisterAssembly` 작업을 사용하여 `OutputPath` 및 `FileName` 속성으로 지정된 경로에서 어셈블리(있는 경우)의 등록을 취소합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [RegisterAssembly 작업](../msbuild/registerassembly-task.md)
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)