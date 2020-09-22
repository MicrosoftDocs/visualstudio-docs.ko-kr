---
title: 작업 일괄 처리의 항목 메타데이터 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 15a6eeea6ebf75513419cc763b2e29a6b6264391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842131"
---
# <a name="item-metadata-in-task-batching"></a>작업 일괄 처리의 항목 메타데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에는 항목 목록을 항목 메타데이터에 따라 여러 다른 범주 또는 일괄 처리로 나누고 각 일괄 처리를 사용하여 한 번에 하나의 작업을 실행하는 기능이 있습니다. 어떤 항목이 어떤 일괄 처리를 통해 전달될지 정확히 이해하는 것은 어려울 수 있습니다. 이 항목에서는 일괄 처리와 관련된 다음과 같은 일반적인 시나리오를 다룹니다.  
  
- 하나의 항목 목록을 일괄 처리로 나누기  
  
- 여러 항목 목록을 일괄 처리로 나누기  
  
- 한 번에 하나씩 일괄 처리  
  
- 항목 목록 필터링  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 사용한 일괄 처리에 대한 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.  
  
## <a name="dividing-an-item-list-into-batches"></a>하나의 항목 목록을 일괄 처리로 나누기  
 일괄 처리를 사용하면 항목 목록이 항목 메타데이터에 따라 여러 다른 일괄 처리로 나뉜 후 각 일괄 처리가 따로 작업으로 전달될 수 있습니다. 이 방식은 위성 어셈블리를 빌드하는 데 유용합니다.  
  
 다음 예제에서는 항목 목록을 항목 메타데이터에 따라 일괄 처리로 나누는 방법을 보여 줍니다. `ExampColl` 항목 목록은 `Number` 항목 메타데이터에 따라 세 개의 일괄 처리로 나뉩니다. `Text` 특성에 `%(ExampColl.Number)`가 있으면 일괄 처리가 수행되어야 한다는 알림이 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 제공됩니다. `ExampColl` 항목 목록은 `Number` 메타데이터에 따라 세 개의 일괄 처리로 나뉘고 각 일괄 처리가 작업에 따로 전달됩니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [메시지 작업](../msbuild/message-task.md) 작업은 다음 정보를 표시합니다.  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>여러 항목 목록을 일괄 처리로 나누기  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 여러 항목 목록을 동일한 메타데이터에 따라 일괄 처리로 나눌 수 있습니다. 이렇게 하면 쉽게 여러 다른 항목 목록을 일괄 처리로 나누어 여러 어셈블리를 빌드할 수 있습니다. 예를 들어 .cs 파일의 항목 목록을 애플리케이션 일괄 처리 및 어셈블리 일괄 처리로 나누고, 리소스 파일의 항목 목록을 애플리케이션 일괄 처리 및 어셈블리 일괄 처리로 나눌 수 있습니다. 그런 후 일괄 처리를 사용하여 이러한 항목 목록을 하나의 작업에 전달하고 애플리케이션 및 어셈블리를 둘 다 빌드할 수 있습니다.  
  
> [!NOTE]
> 작업에 전달되는 항목 목록에 참조된 메타데이터가 있는 항목이 없으면 해당 항목 목록의 모든 항목이 모든 일괄 처리로 전달됩니다.  
  
 다음 예제에서는 여러 항목 목록을 항목 메타데이터에 따라 일괄 처리로 나누는 방법을 보여 줍니다. `ExampColl` 및 `ExampColl2` 항목 목록은 `Number` 항목 메타데이터에 따라 세 개의 일괄 처리로 나뉩니다. `Text` 특성에 `%(Number)`가 있으면 일괄 처리가 수행되어야 한다는 알림이 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 제공됩니다. `ExampColl` 및 `ExampColl2` 항목 목록은 `Number` 메타데이터에 따라 세 개의 일괄 처리로 나뉘고 각 일괄 처리가 작업에 따로 전달됩니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [메시지 작업](../msbuild/message-task.md) 작업은 다음 정보를 표시합니다.  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>한 번에 하나씩 일괄 처리  
 항목이 만들어질 때 모든 항목에 할당된 잘 알려진 항목 메타데이터에 대해서도 일괄 처리를 수행할 수 있습니다. 이를 통해 컬렉션에 있는 모든 항목이 일괄 처리에 사용할 메타데이터를 갖게 됩니다. `Identity` 메타데이터 값은 모든 항목에 대해 고유하므로 항목 목록에 있는 모든 항목을 별도 일괄 처리로 나누는 데 유용합니다. 잘 알려진 항목 메타 데이터의 전체 목록은 [잘 알려진 항목 메타 데이터](../msbuild/msbuild-well-known-item-metadata.md)를 참조 하세요.  
  
 다음 예제에서는 항목 목록의 각 항목을 한 번에 하나씩 일괄 처리로 지정하는 방법을 보여 줍니다. 모든 항목의 `Identity` 메타데이터 값은 고유하므로 `ExampColl` 항목 목록은 각각이 항목 목록의 항목 1개를 포함하는 6개의 일괄 처리로 나뉩니다. `Text` 특성에 `%(Identity)`가 있으면 일괄 처리가 수행되어야 한다는 알림이 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 제공됩니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [메시지 작업](../msbuild/message-task.md) 작업은 다음 정보를 표시합니다.  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>항목 목록 필터링  
 일괄 처리를 사용하면 항목 목록이 작업에 전달되기 전에 특정 항목 목록을 필터링할 수 있습니다. 예를 들어 `Extension`의 잘 알려진 항목 메타데이터 값에 따라 필터링을 수행하면 특정 확장명을 갖는 파일에만 작업을 실행할 수 있습니다.  
  
 다음 예제에서는 항목 목록을 항목 메타데이터에 따라 일괄 처리로 나눈 다음 해당 일괄 처리가 작업에 전달될 때 필터링하는 방법을 보여 줍니다. `ExampColl` 항목 목록은 `Number` 항목 메타데이터에 따라 세 개의 일괄 처리로 나뉩니다. 작업의 `Condition` 특성은 `Number` 항목 메타데이터 값이 `2`인 일괄 처리만 작업으로 전달되도록 지정합니다.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [메시지 작업](../msbuild/message-task.md) 작업은 다음 정보를 표시합니다.  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>참고 항목  
 [잘 알려진 항목 메타 데이터](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item 요소 (MSBuild)](../msbuild/item-element-msbuild.md)   
 [ItemMetadata 요소 (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [일괄](../msbuild/msbuild-batching.md)   
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)
