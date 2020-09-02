---
title: WriteLinesToFile 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f530648c7dd772fb60148f4d755d4a4ffb420cbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419961"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정된 항목의 경로를 지정된 텍스트 파일에 씁니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `WriteLinestoFile` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`File`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 항목을 쓸 파일을 지정합니다.|  
|`Lines`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 파일에 쓸 항목을 지정합니다.|  
|`Overwrite`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업에서 파일의 모든 기존 내용을 덮어씁니다.|  
|`Encoding`|선택적 `String` 매개 변수입니다.<br /><br /> 문자 인코딩을 선택합니다(예: "Unicode").  <xref:System.Text.Encoding>을 참조하세요.|  
  
## <a name="remarks"></a>설명  
 `Overwrite`가 `true`인 경우 새 파일을 만들고 파일에 내용을 쓴 다음 파일을 닫습니다. 대상 파일이 이미 있으면 덮어씁니다. `Overwrite`가 `false`인 경우 콘텐츠를 파일에 추가합니다. 대상 파일이 아직 없으면 만듭니다.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `WriteLinesToFile` 작업을 사용하여 `MyItems` 항목 컬렉션의 항목 경로를 `MyTextFile` 항목 컬렉션에서 지정한 파일에 씁니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
