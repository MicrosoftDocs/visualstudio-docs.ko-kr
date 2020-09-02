---
title: 증분 빌드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb11467d8d59e7af11741d7719da2858ac1a784c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192885"
---
# <a name="incremental-builds"></a>증분 빌드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

증분 빌드는 해당 입력 파일과 관련하여 최신 상태인 출력 파일이 있는 대상이 실행되지 않도록 최적화된 빌드입니다. 대상 요소는 대상이 입력으로 예상하는 항목을 나타내는 `Inputs` 특성 및 출력으로 생성하는 항목을 나타내는 `Outputs` 특성을 모두 가질 수 있습니다. MSBuild는 이러한 특성의 값 사이에서 1-1 매핑을 찾으려고 시도합니다. 1-1 매핑이 존재하는 경우 MSBuild는 해당 출력 항목의 타임스탬프와 모든 입력 항목의 타임스탬프를 비교합니다. 1-1 매핑이 없는 출력 파일은 모든 입력 파일과 비교됩니다. 출력 파일이 해당 입력 파일보다 최신이거나 두 파일의 타임스탬프가 같은 경우 항목이 최신 상태인 것으로 간주됩니다.  
  
 모든 출력 항목이 최신 상태인 경우 MSBuild는 대상을 건너뜁니다. 이 대상의 *증분 빌드*는 빌드 속도를 크게 향상 시킬 수 있습니다. 일부 파일만 최신 상태인 경우 MSBuild는 대상을 실행하지만 최신 항목을 건너뛰므로 모든 항목을 최신 상태로 합니다. 이는 *부분 증분 빌드*로 알려져 있습니다.  
  
 1-1 매핑은 일반적으로 항목 변환에서 생성됩니다. 자세한 내용은 [변환](../msbuild/msbuild-transforms.md)을 참조하세요.  
  
 다음 대상을 살펴보세요.  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 `Compile` 항목 형식으로 표시되는 파일 집합은 백업 디렉터리에 복사됩니다. 백업 파일에는 .bak 파일 이름 확장명이 있습니다. `Compile` 항목 형식으로 표시되는 파일 또는 해당 백업 파일은 백업 대상이 실행된 후 삭제 또는 수정되지 않으며 후속 빌드에서 백업 대상을 건너뜁니다.  
  
## <a name="output-inference"></a>출력 유추  
 MSBuild는 대상의 `Inputs` 및 `Outputs` 특성을 비교하여 대상을 실행해야 하는지 여부를 결정합니다. 이상적으로 증분 빌드가 완료된 후 존재하는 파일 집합은 연결된 대상의 실행 여부와 관계 없이 동일하게 유지되어야 합니다. 작업에 의해 만들어지거나 변경되는 속성 및 항목은 빌드에 영향을 줄 수 있기 때문에 MSBuild는 영향을 주는 대상을 건너뛰더라도 해당 값을 유추해야 합니다. 이는 *출력 유추*로 알려져 있습니다.  
  
 여기에는 세 가지 경우가 있습니다.  
  
- 대상에 `false`로 평가되는 `Condition` 특성이 있습니다. 이 경우 대상이 실행되지 않으며 빌드에는 아무 영향이 없습니다.  
  
- 대상에 오래된 출력이 있으며 최신 상태가 되도록 실행됩니다.  
  
- 대상에 오래된 출력이 없으며 건너뜁니다. MSBuild는 대상을 평가하고 대상이 실행된 것처럼 항목 및 속성에 변경 내용을 만듭니다.  
  
  증분 컴파일을 지원하기 위해 작업은 모든 `Output` 요소의 `TaskParameter` 특성 값이 작업 입력 매개 변수와 동일한지 확인해야 합니다. 다음은 몇 가지 예입니다.  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 대상이 실행되거나 건너뛰어지는지 여부에 관계 없이 값 "123"을 갖는 속성 Easy를 만듭니다.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 대상이 실행되거나 건너뛰어지는지 여부에 관계 없이 두 개의 항목 "a.cs" 및 "b.cs"를 갖는 항목 종류 Simple을 만듭니다.  
  
 MSBuild 3.5부터 출력 유추는 대상의 항목 및 속성 그룹에 대해 자동으로 수행됩니다. `CreateItem` 작업은 대상에 필요하지 않으며 피해야 합니다. 또한 `CreateProperty` 작업은 대상이 실행되었는지 여부를 결정하도록 대상에만 사용되어야 합니다.  
  
## <a name="determining-whether-a-target-has-been-run"></a>대상이 실행되었는지 여부 결정  
 출력 유추로 인해 대상에 `CreateProperty` 작업을 추가하여 대상이 실행되었는지 여부를 결정할 수 있도록 속성 및 항목을 검사해야 합니다. 대상에 `CreateProperty` 작업을 추가하고 `TaskParameter`가 "ValueSetByTask"인 `Output` 요소를 제공합니다.  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 대상이 실행되는 경우에만 속성 CompileRan을 만들고 `true` 값을 제공합니다. 대상을 건너뛰는 경우 CompileRan은 생성되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [대상](../msbuild/msbuild-targets.md)
