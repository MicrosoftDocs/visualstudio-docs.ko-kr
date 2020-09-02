---
title: CallTarget 작업 | Microsoft Docs
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
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9093b35cc444fc0b346f81a91d20afe73bd476cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160416"
---
# <a name="calltarget-task"></a>CallTarget 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 파일 내의 지정된 대상을 호출합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `CallTarget` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|선택적 `Boolean` 출력 매개 변수입니다.<br /><br /> `true`인 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 엔진이 대상마다 한 번씩 호출됩니다. `false`인 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 엔진이 한 번씩 호출되어 모든 대상을 빌드합니다. 기본값은 `false`입니다.|  
|`TargetOutputs`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 빌드된 모든 대상의 출력을 포함합니다.|  
|`Targets`|선택적 `String[]` 매개 변수입니다.<br /><br /> 빌드할 대상을 지정합니다.|  
|`UseResultsCache`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 캐시된 결과(있는 경우)가 반환됩니다.<br /><br /> **참고** MSBuild 작업이 실행되면 해당 출력은 (ProjectFileName, GlobalProperties)[TargetNames] 범위에 빌드 항목의 목록으로 캐시됩니다.|  
  
## <a name="remarks"></a>설명  
 `Targets`에 지정된 대상이 실패하고 `RunEachTargetSeparately`가 `true`인 경우 작업이 나머지 대상을 계속 빌드합니다.  
  
 기본 대상을 빌드하려는 경우 [MSBuild 작업](../msbuild/msbuild-task.md)을 사용하고 `$(MSBuildProjectFile)`와 동일한 `Projects` 매개 변수를 설정합니다.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예  
 다음 예제에서는 `CallOtherTargets` 내에서 `TargetA`를 호출합니다.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [대상](../msbuild/msbuild-targets.md)
