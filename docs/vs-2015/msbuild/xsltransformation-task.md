---
title: XslTransformation 작업 | Microsoft Docs
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1705fd2b79f8b5044aa4ffa0b65801d6db6c7f33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198952"
---
# <a name="xsltransformation-task"></a>XslTransformation 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT 또는 컴파일된 XSLT 및 출력을 사용하여 XML 입력을 출력 디바이스 또는 파일로 변환합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `XslTransformation` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`OutputPaths`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> XML 변환에 대한 출력 파일을 지정합니다.|  
|`Parameters`|선택적 `String` 매개 변수입니다.<br /><br /> 매개 변수를 XSLT 입력 문서로 지정합니다.|  
|`XmlContent`|선택적 `String` 매개 변수입니다.<br /><br /> XML 입력을 문자열로 지정합니다.|  
|`XmlInputPaths`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> XML 입력 파일을 지정합니다.|  
|`XslCompiledDllPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 컴파일된 XSLT를 지정합니다.|  
|`XslContent`|선택적 `String` 매개 변수입니다.<br /><br /> XSLT 입력을 문자열로 지정합니다.|  
|`XslInputPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> XSLT 입력 파일을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
