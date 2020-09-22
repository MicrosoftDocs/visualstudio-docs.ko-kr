---
title: '방법: 프로젝트 파일의 이름 또는 위치 참조 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae8a32d4587b71f238c023d08a1328ce83ba37d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842002"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>방법: 프로젝트 파일의 이름 또는 위치 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

자체 속성을 만들 필요 없이 프로젝트 파일 자체에 있는 프로젝트의 이름 또는 위치를 사용할 수 있습니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 프로젝트 파일 이름 및 프로젝트와 관련된 기타 속성을 참조하는 예약된 속성을 제공합니다. 예약 된 속성에 대 한 자세한 내용은 [MSBuild 예약 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)을 참조 하세요.  
  
## <a name="using-the-msbuildprojectname-property"></a>MSBuildProjectName 속성 사용  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 매번 정의하지 않고 프로젝트 파일에서 사용할 수 있는 몇몇 예약된 속성을 제공합니다. 예를 들어 예약된 속성 `MSBuildProjectName`은 프로젝트 파일 이름에 대한 참조를 제공합니다.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>MSBuildProjectName 속성을 사용하려면  
  
- 속성을 사용하는 것처럼 $() 표시를 사용하여 프로젝트 파일에서 속성을 참조합니다. 예를 들면 다음과 같습니다.  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  예약된 속성 사용의 장점은 프로젝트 파일 이름에 대한 모든 변경 내용이 자동으로 통합된다는 점입니다. 다음에 프로젝트를 빌드할 때 출력 파일에 새 이름이 포함되고 직접 추가 작업을 할 필요가 없습니다.  
  
> [!NOTE]
> 프로젝트 파일에서 예약된 속성을 다시 정의할 수 없습니다.  
  
## <a name="example"></a>예제  
 다음 예제 프로젝트 파일은 출력의 이름을 지정하기 위해 프로젝트 이름을 예약된 속성으로 참조합니다.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
[MSBuild](msbuild.md)  
 [MSBuild의 예약 된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)
