---
title: GetReferenceAssemblyPaths 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2ca532e37fa2f70800416539a7de2ff5e9978e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633982"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths 작업

다양한 프레임워크의 참조 어셈블리 경로를 반환합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `GetReferenceAssemblyPaths` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|선택적 `String[]` 출력 매개 변수입니다.<br /><br /> `TargetFrameworkMoniker` 매개 변수를 기반으로 경로를 반환합니다. `TargetFrameworkMoniker`가 null이거나 비어 있으면 이 경로는 `String.Empty`가 됩니다.|
|`FullFrameworkReferenceAssemblyPaths`|선택적 `String[]` 출력 매개 변수입니다.<br /><br /> 모니커의 프로필 부분을 고려하지 않고 `TargetFrameworkMoniker` 매개 변수를 기반으로 경로를 반환합니다. `TargetFrameworkMoniker`가 null이거나 비어 있으면 이 경로는 `String.Empty`가 됩니다.|
|`TargetFrameworkMoniker`|선택적 `String` 매개 변수입니다.<br /><br /> 참조 어셈블리 경로와 연결된 대상 프레임워크 모니커를 지정합니다.|
|`RootPath`|선택적 `String` 매개 변수입니다.<br /><br /> 참조 어셈블리 경로를 생성하는 데 사용할 루트 경로를 지정합니다.|
|`BypassFrameworkInstallChecks`|선택적 <xref:System.Boolean> 매개 변수입니다.<br /><br /> `true`인 경우 대상 프레임워크에 따라 특정 런타임 프레임워크가 설치되었는지 확인하기 위해 기본적으로 `GetReferenceAssemblyPaths`가 수행하는 기본 검사를 무시합니다.|
|`TargetFrameworkMonikerDisplayName`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 대상 프레임워크 모니커의 표시 이름을 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)