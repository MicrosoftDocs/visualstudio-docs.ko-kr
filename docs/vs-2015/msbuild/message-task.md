---
title: Message 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190901"
---
# <a name="message-task"></a>메시지 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

빌드하는 동안 메시지를 로깅합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Message` 작업의 매개 변수를 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Importance`|선택적 `String` 매개 변수입니다.<br /><br /> 메시지의 중요도를 지정합니다. 이 매개 변수는 `high`, `normal` 또는 `low` 값을 가질 수 있습니다. 기본값은 `normal`입니다.|  
|`Text`|선택적 `String` 매개 변수입니다.<br /><br /> 기록할 오류 텍스트입니다.|  
  
## <a name="remarks"></a>설명  
 `Message` 작업을 통해 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트는 빌드 프로세스의 여러 다른 단계에서 로거로 메시지를 발생할 수 있습니다.  
  
 `Condition` 매개 변수가 `true`이면 `Text` 매개 변수 값은 로깅되고 빌드가 계속 실행됩니다. `Condition` 매개 변수가 없으면 메시지 텍스트가 로깅됩니다. 로깅에 대 한 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조 하세요.  
  
 기본적으로 메시지는 MSBuild 콘솔 로거로 전송됩니다. <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> 매개 변수를 설정하여 이를 변경할 수 있습니다. 로거는 `Importance` 매개 변수를 해석합니다.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 등록된 모든 로거에 메시지를 로깅합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)
