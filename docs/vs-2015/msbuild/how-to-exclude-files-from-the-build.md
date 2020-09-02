---
title: '방법: 빌드에서 파일 제외 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7aac21e1ee4d77453808090fc37a3fccaf77e1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821610"
---
# <a name="how-to-exclude-files-from-the-build"></a>방법: 빌드에서 파일 제외
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 파일에서 와일드카드를 사용하여 모든 파일을 하나의 디렉터리 또는 중첩된 디렉터리 집합에 빌드의 입력으로 포함할 수 있습니다. 그러나 해당 디렉터리 또는 중첩된 디렉터리 집합 중 하나의 디렉터리에 빌드의 입력으로 포함하지 않으려는 하나의 파일이 있을 수 있습니다. 입력 목록에서 해당 파일 또는 디렉터리를 명시적으로 제외할 수 있습니다. 특정 조건에서만 포함하려는 파일이 프로젝트에 있을 수도 있습니다. 파일을 빌드에 포함할 조건을 명시적으로 선언할 수 있습니다.  
  
## <a name="excluding-a-file-or-directory-from-the-inputs-for-a-build"></a>빌드의 입력에서 파일 또는 디렉터리 제외  
 항목 목록은 빌드에 사용할 입력 파일입니다. 포함할 항목은 `Include` 특성을 사용하여 그룹으로 또는 개별적으로 선언됩니다. 다음은 그 예입니다.  
  
```  
<CSFile Include="Form1.cs"/>  
<CSFile Include ="File1.cs;File2.cs"/>  
<CSFile Include="*.cs"/>  
<JPGFile Include="Images\**\*.jpg"/>  
```  
  
 와일드카드를 사용하여 모든 파일을 하나의 디렉터리 또는 중첩된 디렉터리 집합에 빌드의 입력으로 포함한 경우, 해당 디렉터리 또는 중첩된 디렉터리 집합 중 하나의 디렉터리에 포함하지 않으려면 하나 이상의 파일이 있을 수 있습니다. 항목 목록에서 항목을 제외하려면 `Exclude` 특성을 사용합니다.  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>Form2를 제외한 모든 .cs 또는 .vb 파일을 포함하려면  
  
- 다음 `Include` 및 `Exclude` 특성 중 하나를 사용합니다.  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs"/>  
    ```  
  
     \- 또는 -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb"/>  
    ```  
  
#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>Form2 및 Form3을 제외한 모든 .cs 또는 .vb 파일을 포함하려면  
  
- 다음 `Include` 및 `Exclude` 특성 중 하나를 사용합니다.  
  
    ```  
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>  
    ```  
  
     \- 또는 -  
  
    ```  
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>  
    ```  
  
#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Version2 디렉터리에서 해당 항목을 제외한 모든 .jpg 파일을 이미지 디렉터리의 하위 디렉터리에 포함하려면  
  
- 다음 `Include` 및 `Exclude` 특성을 사용합니다.  
  
    ```  
    <JPGFile  
        Include="Images\**\*.jpg"  
        Exclude = "Images\**\Version2\*.jpg"/>  
    ```  
  
    > [!NOTE]
    > 두 특성의 경로를 모두 지정해야 합니다. `Include` 특성에서 파일 위치를 지정할 때 절대 경로를 사용하는 경우 `Exclude` 특성에서도 절대 경로를 사용해야 하고, `Include` 특성에서 상대 경로를 사용하는 경우 `Exclude` 특성에서도 상대 경로를 사용해야 합니다.  
  
## <a name="using-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>조건을 사용하여 빌드의 입력에서 파일 또는 디렉터리 제외  
 예를 들어 디버그 빌드에 포함하지만 릴리스 빌드에는 포함하지 않으려는 항목이 있는 경우 `Condition` 특성을 사용하여 항목을 포함할 조건을 지정할 수 있습니다.  
  
#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Formula.vb 파일을 릴리스 빌드에만 포함하려면  
  
- 다음과 같이 `Condition` 특성을 사용합니다.  
  
    ```  
    <Compile  
        Include="Formula.vb"  
        Condition=" '$(Configuration)' == 'Release' " />  
    ```  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 Form2.cs를 제외한 모든 .cs 파일이 디렉터리에 포함된 프로젝트를 빌드합니다.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs Exclude="Form2.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [품목이](../msbuild/msbuild-items.md)   
 [MSBuild](msbuild.md) [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)
