---
title: ResolveNonMSBuildProjectOutput 작업 | Microsoft Docs
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
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aaf99affe9c29762aa8b47ea76419da429089b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156151"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

비 MSBuild 프로젝트 참조의 출력 파일을 확인합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `ResolveNonMSBuildProjectOutput` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|선택적 `String` 매개 변수입니다.<br /><br /> 확인된 프로젝트 출력을 포함하는 XML 문자열을 지정합니다.|  
|`ProjectReferences`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 프로젝트 참조를 지정합니다.|  
|`ResolvedOutputPaths`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 확인된 참조 경로 목록을 포함하고 원래 프로젝트 참조 특성을 유지합니다.|  
|`UnresolvedProjectReferences`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 사전 확인된 출력 목록을 사용하여 확인할 수 없는 프로젝트 참조 항목 목록을 포함합니다.<br /><br /> Visual Studio가 비 MSBuild 프로젝트만을 미리 확인하기 때문에 이 목록의 프로젝트 참조는 MSBuild 형식입니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
