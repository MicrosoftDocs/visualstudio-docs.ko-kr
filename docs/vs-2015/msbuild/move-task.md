---
title: Move 작업 | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191579"
---
# <a name="move-task"></a>Move 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

새 위치로 파일을 이동합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Move` 작업의 매개 변수를 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`DestinationFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 소스 파일을 이동할 파일의 목록을 지정합니다. 이 목록은 `SourceFiles` 매개 변수에 지정된 목록에 대한 일대일 매핑이어야 합니다. 즉, `SourceFiles`에 지정된 첫 번째 파일이 `DestinationFiles` 등에 지정된 첫 번째 위치에 이동됩니다.|  
|`DestinationFolder`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 파일을 이동하려는 디렉터리를 지정합니다.|  
|`MovedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 성공적으로 이동된 항목을 계산합니다.|  
|`OverwriteReadOnlyFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 파일이 읽기 전용으로 표시되더라도 파일을 덮어씁니다.|  
|`SourceFiles`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 이동할 파일을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 `DestinationFolder` 매개 변수 또는 `DestinationFiles` 매개 변수 중 하나(둘 다가 아닌)를 지정해야 합니다. 둘 다를 지정하는 경우 작업이 실패하고 오류가 기록됩니다.  
  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
