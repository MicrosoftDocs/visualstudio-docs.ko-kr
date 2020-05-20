---
title: AssignProjectConfiguration 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5159b73058c73c925cae644c2e3ddd2bc84ac41
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634554"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration 작업

이 작업은 목록 구성 문자열을 허용하고 여기에 지정된 프로젝트를 할당합니다.

## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 `AssignProjectConfiguration` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`SolutionConfigurationContents`|선택적 `string` 출력 매개 변수입니다.<br /><br /> 각 프로젝트에 대한 프로젝트 구성을 포함하는 XML 문자열을 포함합니다. 구성은 명명된 프로젝트에 할당됩니다.|
|`DefaultToVcxPlatformMapping`|선택적 `string` 출력 매개 변수입니다.<br /><br /> 대부분의 형식에 사용되는 플랫폼 이름과 *.vcxproj* 파일에 사용되는 플랫폼 이름 간의 매핑을 세미콜론으로 구분한 목록을 포함합니다.<br /><br /> 다음은 그 예입니다.<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|옵션<br /><br /> `string` 출력 매개 변수입니다.<br /><br /> *.vcxproj* 플랫폼 이름에서 대부분의 형식에 사용되는 플랫폼 이름으로의 매핑 목록을 세미콜론으로 구분하여 포함합니다.<br /><br /> 다음은 그 예입니다.<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|선택적 `string` 출력 매개 변수입니다.<br /><br /> 현재 프로젝트에 대한 구성을 포함합니다.|
|`CurrentProjectPlatform`|선택적 `string` 출력 매개 변수입니다.<br /><br /> 현재 프로젝트에 대한 플랫폼을 포함합니다.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|선택적 `bool` 출력 매개 변수입니다.<br /><br /> 프로젝트 구성에서 사용되지 않은 경우에도 참조를 빌드해야 함을 나타내는 플래그를 포함합니다.|
|`ShouldUnsetParentConfigurationAndPlatform`|선택적 `bool` 출력 매개 변수입니다.<br /><br /> 부모 구성 및 플랫폼을 설정 해제해야 함을 나타나는 플래그를 포함합니다.|
|`OutputType`|선택적 `string` 출력 매개 변수입니다.<br /><br /> 프로젝트에 대한 출력 형식을 포함합니다.|
|`ResolveConfigurationPlatformUsingMappings`|선택적 `bool` 출력 매개 변수입니다.<br /><br /> 전달된 프로젝트 참조의 구성 및 플랫폼을 확인하기 위해 빌드가 기본 매핑을 사용해야 하는지를 나타내는 플래그를 포함합니다.|
|`AssignedProjects`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 확인된 참조 경로의 목록을 포함합니다.|
|`UnassignedProjects`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 사전 확인된 출력 목록을 사용하여 확인할 수 없는 프로젝트 참조 항목의 목록을 포함합니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
