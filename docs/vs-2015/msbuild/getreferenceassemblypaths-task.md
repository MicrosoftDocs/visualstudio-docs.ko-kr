---
title: GetReferenceAssemblyPaths 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f771f3c769ea41979210058a58dc1d0d125a4ffe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149483"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다양한 프레임워크의 참조 어셈블리 경로를 반환합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `GetReferenceAssemblyPaths` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|선택적 `String[]` 출력 매개 변수입니다.<br /><br /> `TargetFrameworkMoniker` 매개 변수를 기반으로 경로를 반환합니다. `TargetFrameworkMoniker`가 null이거나 비어 있으면 이 경로는 `String.Empty`가 됩니다.|  
|`FullFrameworkReferenceAssemblyPaths`|선택적 `String[]` 출력 매개 변수입니다.<br /><br /> 모니커의 프로필 부분을 고려하지 않고 `TargetFrameworkMoniker` 매개 변수를 기반으로 경로를 반환합니다. `TargetFrameworkMoniker`가 null이거나 비어 있으면 이 경로는 `String.Empty`가 됩니다.|  
|`TargetFrameworkMoniker`|선택적 `String` 매개 변수입니다.<br /><br /> 참조 어셈블리 경로와 연결된 대상 프레임워크 모니커를 지정합니다.|  
|`RootPath`|선택적 `String` 매개 변수입니다.<br /><br /> 참조 어셈블리 경로를 생성하는 데 사용할 루트 경로를 지정합니다.|  
|`BypassFrameworkInstallChecks`|선택적 [부울](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> `true`인 경우 대상 프레임워크에 따라 특정 런타임 프레임워크가 설치되었는지 확인하기 위해 기본적으로 `GetReferenceAssemblyPaths`가 수행하는 기본 검사를 무시합니다.|  
|`TargetFrameworkMonikerDisplayName`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 대상 프레임워크 모니커의 표시 이름을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
