---
title: FormatVersion 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149621"
---
# <a name="formatversion-task"></a>FormatVersion 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

버전 번호에 수정 버전 번호를 추가합니다.  
  
- Case #1: Input: Version = \<undefined> ;  수정 버전 = \<don't care> ;   Output: OutputVersion = "1.0.0.0"  
  
- 사례 #2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"  
  
- Case #3: Input: Version = "1.0.0.0" Revision = \<don't care> ;  Output: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `FormatVersion` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`FormatType`|선택적 `String` 매개 변수입니다.<br /><br /> 서식 유형을 지정합니다.<br /><br /> -   "Version" = 버전입니다.<br />-   "Path" = "."을 "_";로 바꿉니다.|  
|`OutputVersion`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 수정 번호를 포함하는 출력 버전을 지정합니다.|  
|`Revision`|선택적 `Int32` 매개 변수입니다.<br /><br /> 버전에 추가할 수정을 지정합니다.|  
|`Version`|선택적 `String` 매개 변수입니다.<br /><br /> 서식을 지정할 버전 번호 문자열을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
