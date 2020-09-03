---
title: ResolveKeySource 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5cbe2f4998ab78ce39cde4b26a38b13c70b2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193714"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

강력한 이름 키 원본을 확인합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `ResolveKeySource` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|선택적 `Int32` 매개 변수입니다.<br /><br /> 카운트다운 메시지를 표시할 시간(초)을 설정하거나 가져옵니다.|  
|`AutoClosePasswordPromptTimeout`|선택적 `Int32` 매개 변수입니다.<br /><br /> 암호 프롬프트 대화 상자를 닫기 전에 대기하는 시간(초)을 가져오거나 설정합니다.|  
|`CertificateFile`|선택적 `String` 매개 변수입니다.<br /><br /> 인증서 파일의 경로를 가져오거나 설정합니다.|  
|`CertificateThumbprint`|선택적 `String` 매개 변수입니다.<br /><br /> 인증서 지문을 가져오거나 설정합니다.|  
|`KeyFile`|선택적 `String` 매개 변수입니다.<br /><br /> 키 파일의 경로를 가져오거나 설정합니다.|  
|`ResolvedKeyContainer`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 확인된 키 컨테이너를 가져오거나 설정합니다.|  
|`ResolvedKeyFile`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 확인된 키 파일을 가져오거나 설정합니다.|  
|`ResolvedThumbprint`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 확인된 인증서 지문을 가져오거나 설정합니다.|  
|`ShowImportDialogDespitePreviousFailures`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 이전에 실패했어도 가져오기 대화 상자를 표시합니다.|  
|`SuppressAutoClosePasswordPrompt`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 암호 프롬프트 대화 상자를 자동으로 닫을지 여부를 지정하는 부울 값을 가져오거나 설정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
