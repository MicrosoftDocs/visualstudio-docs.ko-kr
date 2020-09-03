---
title: ResolveManifestFiles 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6ba088b91496c633afe34c20e40c12ded7d2279b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161360"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

빌드 프로세스에서 빌드된 항목, 종속성, 위성, 콘텐츠, 디버그 기호 및 설명서 등의 항목을 확인합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `ResolveManifestFiles` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 배포 매니페스트의 이름을 지정합니다.|  
|`EntryPoint`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 매니페스트에 대한 진입점인 ClickOnce 매니페스트 참조 또는 관리되는 어셈블리를 지정합니다.|  
|`ExtraFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 추가 파일을 지정합니다.|  
|`ManagedAssemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 관리되는 어셈블리를 지정합니다.|  
|`NativeAssemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 네이티브 어셈블리를 지정합니다.|  
|`OutputAssemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 생성된 어셈블리를 지정합니다.|  
|`OutputDeploymentManifestEntryPoint`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 출력 배포 매니페스트 진입점을 지정합니다.|  
|`OutputEntryPoint`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 출력 진입점을 지정합니다.|  
|`OutputFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 출력 파일을 지정합니다.|  
|`PublishFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 게시 파일을 지정합니다.|  
|`SatelliteAssemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 위성 어셈블리를 지정합니다.|  
|`SigningManifests`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 매니페스트에 서명됩니다.|  
|`TargetCulture`|선택적 `String` 매개 변수입니다.<br /><br /> 위성 어셈블리의 대상 문화권을 지정합니다.|  
|`TargetFrameworkVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 대상 .NET Framework 버전을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
