---
title: RegisterAssembly 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ef27b61e162fedbf0b8fcaac38d93bedbc77c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682397"
---
# <a name="registerassembly-task"></a>RegisterAssembly 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정된 어셈블리 내의 메타데이터를 읽고 필요한 엔트리를 레지스트리에 추가할 수 있습니다. 이렇게 하면 COM 클라이언트에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스를 투명하게 만들 수 있습니다. 이 작업의 동작은 [Regasm.exe (어셈블리 등록 도구)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)와 유사 하지만 동일 하지는 않습니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `RegisterAssembly` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`Assemblies`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> COM에 등록할 어셈블리를 지정합니다.|  
|`AssemblyListFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> `RegisterAssembly` 작업과 [UnregisterAssembly](../msbuild/unregisterassembly-task.md) 작업 사이의 상태에 대한 정보를 포함합니다. 이를 통해 `UnregisterAssembly` 작업이 `RegisterAssembly` 작업에서 등록하지 못한 어셈블리의 등록을 취소하려고 하는 시도를 방지합니다.|  
|`CreateCodeBase`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 전역 어셈블리 캐시에 설치되지 않은 어셈블리에 대한 파일 경로를 지정하는 코드베이스 항목을 레지스트리에 만듭니다. 전역 어셈블리 캐시에 등록 중인 어셈블리를 다음에 설치하려면 이 옵션을 지정해야 합니다.|  
|`TypeLibFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 지정된 어셈블리에서 생성할 형식 라이브러리를 지정합니다. 생성된 형식 라이브러리에는 어셈블리 내에 정의된 액세스 가능 형식에 대한 정의가 들어 있습니다. 형식 라이브러리는 다음 조건 중 하나가 충족되는 경우에만 생성됩니다.<br /><br /> - 해당 이름의 형식 라이브러리가 해당 위치에 존재하지 않습니다.<br />- 형식 라이브러리는 존재하지만 전달되는 어셈블리보다 오래된 것입니다.<br /><br /> 형식 라이브러리가 전달되는 어셈블리보다 최신인 경우 새 형식 라이브러리가 만들어지지 않으며 어셈블리는 계속 등록됩니다.<br /><br /> 이 매개 변수를 지정하는 경우 `Assemblies` 매개 변수와 동일한 수의 항목이 포함되어야 하며, 그러지 않으면 작업이 실패합니다. 입력을 지정하지 않으면 작업은 기본적으로 어셈블리의 이름이 되며 항목의 확장명을 .tlb로 변경합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `RegisterAssembly` 작업을 사용하여 `MyAssemblies` 항목 컬렉션으로 지정된 어셈블리를 등록합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
