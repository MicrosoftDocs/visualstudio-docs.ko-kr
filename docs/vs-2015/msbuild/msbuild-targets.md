---
title: MSBuild 대상 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4cc8d9654fc2d277f0b7c69483ab46aa3209983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157608"
---
# <a name="msbuild-targets"></a>MSBuild 대상
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대상은 특정 순서로 작업을 그룹화하며 빌드 프로세스를 더 작은 단위로 팩터링될 수 있도록 합니다. 예를 들어 하나의 대상이 빌드에 대한 준비를 위해 출력 디렉터리에서 모든 파일을 삭제할 수 있는 반면 다른 대상은 프로젝트에 대한 입력을 컴파일하고 빈 디렉터리에 배치합니다. 작업에 대한 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.  
  
## <a name="declaring-targets-in-the-project-file"></a>프로젝트 파일에서 대상 선언  
 [Target](../msbuild/target-element-msbuild.md) 요소로 프로젝트 파일에 대상을 선언합니다. 예를 들어 다음 XML은 Construct라는 대상을 만든 다음 컴파일 항목 형식으로 Csc 작업을 호출합니다.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 MSBuild 속성처럼 대상은 다시 정의될 수 있습니다. 예를 들면 다음과 같습니다.  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 AfterBuild가 실행되는 경우 "두 번째 발생"만 표시됩니다.  
  
## <a name="target-build-order"></a>대상 빌드 순서  
 단일 대상에 대한 입력이 다른 대상의 출력을 사용하는 경우에는 대상의 순서를 지정해야 합니다. 대상 실행의 순서를 지정하는 방법은 여러 가지가 있습니다.  
  
- 초기 대상  
  
- 기본 대상  
  
- 첫 번째 대상  
  
- 대상 종속성  
  
- `BeforeTargets` 및 `AfterTargets`(MSBuild 4.0)  
  
  대상은 빌드의 후속 대상이 종속되더라도 단일 빌드 중에 두 번 실행되지 않습니다. 대상이 실행되면 빌드 내에서 해당 대상의 역할은 완료됩니다.  
  
  대상 빌드 순서에 대 한 자세한 내용 및 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md)를 참조 하세요.  
  
## <a name="target-batching"></a>대상 일괄 처리  
 대상 요소에는 %(메타데이터) 형식에서 메타데이터를 지정하는 `Outputs` 특성이 있을 수 있습니다. 이 경우 MSBuild는 해당 메타데이터 값을 가진 항목을 그룹화 또는 "일괄 처리"하여 각 고유 메타데이터 값에 대해 한 번씩 대상을 실행합니다. 예를 들면 다음과 같습니다.  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 RequiredTargetFramework 메타데이터로 참조 항목을 일괄 처리합니다. 대상의 출력은 다음과 같습니다.  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 대상 일괄 처리는 실제 빌드에 거의 사용되지 않습니다. 작업 일괄 처리가 더 일반적입니다. 자세한 내용은 [일괄 처리](../msbuild/msbuild-batching.md)를 참조하세요.  
  
## <a name="incremental-builds"></a>증분 빌드  
 증분 빌드는 해당 입력 파일과 관련하여 최신 상태인 출력 파일이 있는 대상이 실행되지 않도록 최적화된 빌드입니다. 대상 요소는 대상이 입력으로 예상하는 항목 및 출력으로 생성하는 항목을 나타내는 `Inputs` 및 `Outputs` 특성을 모두 가질 수 있습니다.  
  
 모든 출력 항목이 최신 상태인 경우 MSBuild는 대상을 건너뜁니다. 이로 인해 빌드 속도가 크게 향상됩니다. 이를 대상의 증분 빌드라고 합니다. 일부 파일만 최신 상태인 경우 MSBuild는 최신 항목 없이 대상을 실행합니다. 이를 대상의 부분 증분 빌드라고 합니다. 자세한 내용은 [증분 빌드](../msbuild/incremental-builds.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [방법: 여러 프로젝트 파일에서 동일한 대상 사용](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
