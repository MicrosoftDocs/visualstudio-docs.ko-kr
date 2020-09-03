---
title: ParameterGroup 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f4faa9038a5931dec376903f166301f27f00b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154792"
---
# <a name="parametergroup-element"></a>ParameterGroup 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`UsingTask``TaskFactory`에 의해 생성된 작업에 존재할 매개 변수의 선택적 목록을 포함합니다. 자세한 내용은 [UsingTask 요소 (MSBuild)](../msbuild/usingtask-element-msbuild.md)를 참조 하세요.  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
  
## <a name="syntax"></a>구문  
  
```  
<ParameterGroup />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[매개 변수](../msbuild/parameter-element.md)|`UsingTask``TaskFactory`에 의해 생성되는 작업에 대한 특정 매개 변수에 대한 정보를 포함합니다. 요소의 이름은 매개 변수의 이름입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 작업을 등록하는 방법을 제공합니다. 프로젝트에는 `UsingTask` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다.|  
  
## <a name="example"></a>예  
 다음 예제에서는 `ParameterGroup` 요소를 사용하는 방법을 보여 줍니다.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
