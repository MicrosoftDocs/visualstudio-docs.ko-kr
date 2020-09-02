---
title: WriteCodeFragment 작업 | Microsoft Docs
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
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa9882d30a8483937f77da21bb4700d4899a68a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555480"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

생성된 특정 코드 조각에서 임시 코드 파일을 생성합니다. 파일을 삭제하지는 않습니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `WriteCodeFragment` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`AssemblyAttributes`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 작성할 특성의 설명입니다. 항목 `Include` 값은 특성의 전체 유형 이름입니다(예: "System.AssemblyVersionAttribute").<br /><br /> 각 메타데이터는 매개 변수의 이름 값 쌍이며 `String` 형식이어야 합니다. 일부 특성만 위치 생성자 인수를 허용합니다. 그러나 모든 특성에 이러한 인수를 사용할 수 있습니다. 위치 생성자 특성을 설정하려면 "_Parameter1", "_Parameter2" 등과 유사한 메타데이터 이름을 사용합니다.<br /><br /> 매개 변수 인덱스는 생략할 수 없습니다.|  
|`Language`|필수 `String` 매개 변수입니다.<br /><br /> 생성할 코드의 언어를 지정합니다.<br /><br /> `Language`는 CodeDom 공급자를 사용할 수 있는 언어일 수 있습니다(예: "C#" 또는 "VisualBasic"). 내보낸 파일은 해당 언어에 대한 기본 파일 이름 확장명을 갖습니다.|  
|`OutputDirectory`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 생성된 코드에 대한 대상 폴더를 지정합니다. 일반적으로 중간 폴더입니다.|  
|`OutputFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 생성된 파일의 경로를 지정합니다. 이 매개 변수가 파일 이름을 사용하여 설정된 경우 대상 폴더는 파일 이름에 추가됩니다. 루트를 사용하여 설정된 경우 대상 폴더는 무시됩니다.<br /><br /> 이 매개 변수가 설정되지 않은 경우 출력 파일 이름은 지정된 언어에 대한 대상 폴더, 임의의 파일 이름 및 기본 파일 이름 확장명입니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
