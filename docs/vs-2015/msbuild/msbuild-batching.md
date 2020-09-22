---
title: MSBuild 일괄 처리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841651"
---
# <a name="msbuild-batching"></a>MSBuild 일괄 처리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에는 항목 목록을 항목 메타데이터에 따라 여러 다른 범주 또는 일괄 처리로 나누고 각 일괄 처리를 사용하여 한 번에 하나의 대상 또는 작업을 실행하는 기능이 있습니다.  
  
## <a name="task-batching"></a>작업 일괄 처리  
 작업 일괄 처리를 사용하면 항목 목록을 다른 일괄 처리로 나누고 해당 일괄 처리 각각을 별도로 작업에 전달하는 방법을 제공하여 프로젝트 파일을 간소화할 수 있습니다. 즉, 프로젝트 파일은 여러 번 실행될 수 있지만 작업 및 해당 특성을 한 번만 선언해야 합니다.  
  
 작업 특성 중 하나에서 %(*ItemMetaDataName*) 표기법을 사용하여 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]가 작업에서 일괄 처리를 수행하도록 지정합니다. 다음 예제에서는 `Example` 항목 목록을 `Color` 항목 메타데이터 값에 기반한 일괄 처리로 분할하고 일괄 처리 각각을 `MyTask` 작업에 개별적으로 전달합니다.  
  
> [!NOTE]
> 작업 특성의 다른 위치에서 항목 목록을 참조하지 않거나 메타데이터 이름이 모호할 수 있는 경우 %(*ItemCollection.ItemMetaDataName*) 표기법을 사용하여 일괄 처리에 사용할 항목 메타데이터 값을 정규화할 수 있습니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 보다 구체적인 일괄 처리 예제는 [작업 일괄 처리의 항목 메타 데이터](../msbuild/item-metadata-in-task-batching.md)를 참조 하세요.  
  
## <a name="target-batching"></a>대상 일괄 처리  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 대상이 실행되기 전에 대상의 입력 및 출력이 최신 상태인지를 확인합니다. 입력 및 출력이 모두 최신 상태인 경우 대상을 건너뜁니다. 대상 내의 작업이 일괄 처리를 사용하는 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 항목의 각 일괄 처리에 대한 입력 및 출력이 최신 상태인지를 확인해야 합니다. 그렇지 않으면 대상이 적중될 때마다 실행됩니다.  
  
 다음 예제에서는 %(*ItemMetaDataName*) 표기법을 사용하는 `Outputs` 특성이 포함된 `Target` 요소를 보여줍니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 `Example` 항목 목록을 `Color` 항목 메타데이터를 기반으로 하는 일괄 처리로 나누고, 각 일괄 처리에 대한 출력 파일의 타임스탬프를 분석합니다. 일괄 처리의 출력이 최신 상태인 경우 대상이 실행됩니다. 그렇지 않으면 대상을 건너뜁니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 대상 일괄 처리의 또 다른 예는 [대상 일괄 처리의 항목 메타 데이터](../msbuild/item-metadata-in-target-batching.md)를 참조 하세요.  
  
## <a name="property-functions-using-metadata"></a>메타데이터를 사용하는 속성 함수  
 메타데이터를 포함하는 속성 함수에서 일괄 처리를 제어할 수 있습니다. 예를 들면 다음과 같습니다.  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 <xref:System.IO.Path.Combine%2A>를 사용하여 컴파일 항목 경로와 루트 폴더 경로를 결합합니다.  
  
 속성 함수는 메타데이터 값 내에 나타나지 않을 수 있습니다.  예를 들면 다음과 같습니다.  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 사용할 수 없습니다.  
  
 속성 함수에 대 한 자세한 내용은 [속성 함수](../msbuild/property-functions.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [ItemMetadata 요소 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [고급 개념](../msbuild/msbuild-advanced-concepts.md)
