---
title: GetFrameworkPath 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149489"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 어셈블리에 대한 경로를 검색합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `GetFrameworkPath` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 프레임워크 버전 1.1 어셈블리에 대한 경로가 있는 경우 포함됩니다. 그렇지 않으면 `null`를 반환합니다.|  
|`FrameworkVersion20Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 프레임워크 버전 2.0 어셈블리에 대한 경로가 있는 경우 포함됩니다. 그렇지 않으면 `null`를 반환합니다.|  
|`FrameworkVersion30Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 프레임워크 버전 3.0 어셈블리에 대한 경로가 있는 경우 포함됩니다. 그렇지 않으면 `null`를 반환합니다.|  
|`FrameworkVersion35Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 프레임워크 버전 3.5 어셈블리에 대한 경로가 있는 경우 포함됩니다. 그렇지 않으면 `null`를 반환합니다.|  
|`FrameworkVersion40Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 프레임워크 버전 4.0 어셈블리에 대한 경로가 있는 경우 포함됩니다. 그렇지 않으면 `null`를 반환합니다.|  
|`Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 사용 가능한 경우 최신 프레임워크 어셈블리에 대한 경로를 포함합니다. 그렇지 않으면 `null`를 반환합니다.|  
  
## <a name="remarks"></a>설명  
 여러 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 설치한 경우 이 작업은 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 실행하도록 설계한 버전을 반환합니다.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예  
 다음 예제에서는 `GetFrameworkPath` 작업을 사용하여 `FrameworkPath` 속성에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]에 대한 경로를 저장합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
