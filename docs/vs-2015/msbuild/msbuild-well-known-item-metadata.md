---
title: MSBuild 잘 알려진 항목 메타데이터 | Microsoft Docs
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
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154077"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild 잘 알려인 항목 메타데이터
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 표에서는 만들어질 때 모든 항목에 할당된 메타데이터에 대해 설명합니다. 각 예제에서 프로젝트에 파일 `C:\MyProject\Source\Program.cs`를 포함하는 데 다음과 같은 항목 선언이 사용되었습니다.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|항목 메타데이터|설명|  
|-------------------|-----------------|  
|%(FullPath)|항목의 전체 경로를 포함합니다. 다음은 그 예입니다.<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|항목의 루트 디렉터리를 포함합니다. 다음은 그 예입니다.<br /><br /> `C:\`|  
|%(Filename)|확장명 없이 항목의 파일 이름을 포함합니다. 다음은 그 예입니다.<br /><br /> `Program`|  
|%(Extension)|항목의 파일 이름 확장명을 포함합니다. 다음은 그 예입니다.<br /><br /> `.cs`|  
|%(RelativeDir)|마지막 백슬래시(\\)까지 `Include` 특성에 지정된 경로를 포함합니다. 다음은 그 예입니다.<br /><br /> `Source\`|  
|%(Directory)|루트 디렉터리를 제외한 항목의 디렉터리를 포함합니다. 예를 들어:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|`Include` 특성에 와일드카드 \*\*가 포함되는 경우 메타데이터는 와일드카드를 대신하는 경로 부분을 지정합니다. 와일드 카드에 대 한 자세한 내용은 [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)을 참조 하세요.<br /><br /> *C:\MySolution\MyProject\Source \\ * 폴더에 Program.cs 파일이 포함 되어 있으면이 고, 프로젝트 파일에 다음 항목이 포함 되어 있으면입니다.<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> `%(MyItem.RecursiveDir)` 값은 *MySolution\MyProject\Source\\* 가 됩니다.|  
|%(Identity)|`Include` 특성에 지정된 항목입니다. 다음은 그 예입니다.<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|항목을 마지막으로 수정한 시간의 타임스탬프를 포함합니다. 예를 들어:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|항목을 만든 시간의 타임스탬프를 포함합니다. 예를 들어:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|항목을 마지막으로 액세스한 시간의 타임스탬프를 포함합니다.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>관련 항목  
 [품목이](../msbuild/msbuild-items.md)   
 [일괄](../msbuild/msbuild-batching.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)
