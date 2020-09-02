---
title: 경고 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558491"
---
# <a name="warning-task"></a>경고 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

평가된 조건부 문에 따라 빌드 중에 경고를 로깅합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Warning` 작업의 매개 변수를 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Code`|선택적 `String` 매개 변수입니다.<br /><br /> 경고와 연결할 경고 코드입니다.|  
|`File`|선택적 `String` 매개 변수입니다.<br /><br /> 있는 경우 관련 파일을 지정합니다. 파일을 제공하지 않으면 경고 작업이 포함된 파일이 사용됩니다.|  
|`HelpKeyword`|선택적 `String` 매개 변수입니다.<br /><br /> 경고와 연결할 도움말 키워드입니다.|  
|`Text`|선택적 `String` 매개 변수입니다.<br /><br /> `Condition` 매개 변수가 `true`로 평가될 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]가 기록하는 경고 텍스트입니다.|  
  
## <a name="remarks"></a>설명  
 `Warning` 작업을 통해 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트는 다음 빌드 단계를 계속하기 전에 필수 구성 또는 속성의 존재를 확인할 수 있습니다.  
  
 `Warning` 작업의 `Condition` 매개 변수가 `true`로 평가되는 경우 `Text` 매개 변수 값은 로깅되고 빌드가 계속 실행됩니다. `Condition` 매개 변수가 없으면 경고 텍스트가 로깅됩니다. 로깅에 대 한 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조 하세요.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 명령줄에서 설정된 속성을 확인합니다. 설정된 속성이 없는 경우 프로젝트에서는 경고 이벤트를 발생시키고 `Warning` 작업의 `Text` 매개 변수 값을 기록합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
