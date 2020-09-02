---
title: Output 요소(MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 52b8ef11e295d60e71a59820a48bca5e477c639d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163598"
---
# <a name="output-element-msbuild"></a>Output 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목 및 속성에서 태스크 출력 값을 저장합니다.  
  
 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  
  
## <a name="syntax"></a>구문  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`TaskParameter`|필수 특성입니다.<br /><br /> 태스크 출력 매개 변수의 이름입니다.|  
|`PropertyName`|`PropertyName` 또는 `ItemName` 특성이 필요합니다.<br /><br /> 태스크의 출력 매개 변수 값을 수신하는 속성입니다. 그런 다음 프로젝트는 PropertyName 구문을 사용 하 여 속성을 참조할 수 있습니다 `$(` *PropertyName* `)` . 이 속성 이름은 새 속성 이름 또는 프로젝트에 이미 정의된 이름일 수 있습니다.<br /><br /> `ItemName`을 이미 사용한 경우 이 특성을 사용할 수 없습니다.|  
|`ItemName`|`PropertyName` 또는 `ItemName` 특성이 필요합니다.<br /><br /> 태스크의 출력 매개 변수 값을 수신하는 항목입니다. 그러면 프로젝트에서 ItemName 구문을 사용 하 여 항목을 참조할 수 있습니다 `@(` *ItemName* `)` . 항목 이름은 새 항목 이름 또는 프로젝트에 이미 정의되어 있는 다른 이름일 수 있습니다.<br /><br /> `PropertyName`을 이미 사용한 경우 이 특성을 사용할 수 없습니다.|  
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업의 인스턴스를 만들고 실행합니다.|  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 `Target` 요소 내에서 실행되는 `Csc` 태스크를 보여 줍니다. 태스크 매개 변수에 전달된 항목 및 속성은 이 예제의 범위 밖에서 선언됩니다. 출력 매개 변수 `OutputAssembly`의 값은 `FinalAssemblyName` 항목에 저장되고 출력 매개 변수 `BuildSucceeded`의 값은 `BuildWorked` 속성에 저장됩니다. 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)   
 [작업](../msbuild/msbuild-tasks.md)
