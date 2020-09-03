---
title: 오류 작업 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b220d12b872a81cba5f46bd14fdebafaa58cf4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201806"
---
# <a name="error-task"></a>오류 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

빌드를 중지하고 평가된 조건부 문에 따라 오류를 기록합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Error` 작업의 매개 변수를 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Code`|선택적 `String` 매개 변수입니다.<br /><br /> 오류와 연결할 오류 코드입니다.|  
|`File`|선택적 `String` 매개 변수입니다.<br /><br /> 오류가 포함된 파일의 이름입니다. 파일 이름을 제공하지 않으면 오류 작업이 포함된 파일이 사용됩니다.|  
|`HelpKeyword`|선택적 `String` 매개 변수입니다.<br /><br /> 오류와 연결할 도움말 키워드입니다.|  
|`Text`|선택적 `String` 매개 변수입니다.<br /><br /> `Condition` 매개 변수가 `true`로 평가될 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]가 기록하는 오류 텍스트입니다.|  
  
## <a name="remarks"></a>설명  
 `Error` 작업을 수행하면 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트에서 로거에 대해 오류 텍스트를 실행하고 빌드 실행을 중지할 수 있습니다.  
  
 `Condition` 매개 변수가 `true`로 평가될 경우 빌드가 중지되고 오류가 기록됩니다. `Condition` 매개 변수가 없으면 오류가 기록되고 빌드 실행이 중지됩니다. 로깅에 대 한 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조 하세요.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 코드 예제는 모든 필수 속성이 설정되었는지 확인합니다. 설정되지 않은 경우 프로젝트에서는 오류 이벤트를 발생시키고 `Error` 작업의 `Text` 매개 변수 값을 기록합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)
