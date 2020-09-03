---
title: '방법: 다른 옵션을 사용하여 동일한 원본 파일 빌드 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bf76967363f4c0d97d93c895fbeb6209c8503f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821676"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>방법: 동일한 소스 파일을 다른 옵션을 사용하여 빌드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트를 빌드할 때 같은 구성 요소를 서로 다른 빌드 옵션으로 자주 컴파일하게 됩니다. 예를 들어 기호 정보가 포함된 디버그 빌드를 만들거나 기호 정보가 없지만 최적화가 사용하도록 설정된 릴리스 빌드를 만들 수 있습니다. x86 또는 [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] 등의 특정 플랫폼에서 실행되는 프로젝트를 빌드할 수도 있습니다. 이러한 모든 경우에 대부분의 빌드 옵션은 동일하게 유지되고, 빌드 구성을 제어하기 위해 몇 가지 옵션만 변경됩니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]를 통해 속성과 조건을 사용하여 다양한 빌드 구성을 만듭니다.  
  
## <a name="using-properties-to-modify-projects"></a>속성을 사용하여 프로젝트 수정  
 `Property` 요소는 임시 디렉터리의 위치와 같이 프로젝트 파일에서 여러 번 참조되는 변수를 정의하고 디버그 빌드 및 릴리스 빌드 등의 여러 구성에서 사용되는 속성 값을 설정합니다. 속성에 대 한 자세한 내용은 [MSBuild 속성](msbuild-properties1.md)을 참조 하세요.  
  
 속성을 사용하면 프로젝트 파일을 변경할 필요 없이 빌드의 구성을 변경할 수 있습니다. `Property` 요소 및 `PropertyGroup` 요소의 `Condition` 특성을 사용하여 속성 값을 변경할 수 있습니다. 조건에 대 한 자세한 내용은 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] [조건](../msbuild/msbuild-conditions.md)을 참조 하세요.  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>또 다른 속성을 기반으로 속성 그룹을 설정하려면  
  
- 다음과 같은 `PropertyGroup` 요소의 `Condition` 특성을 사용합니다.  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>또 다른 속성을 기반으로 속성을 정의하려면  
  
- 다음과 같은 `Property` 요소의 `Condition` 특성을 사용합니다.  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>명령줄에서 속성 지정  
 프로젝트 파일이 여러 구성을 허용하도록 작성되면 프로젝트를 빌드할 때마다 해당 구성을 변경하는 기능을 포함해야 합니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 는 **/property** 또는 **/p** 스위치를 사용 하 여 명령줄에서 속성을 지정할 수 있도록 하 여이 기능을 제공 합니다.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>명령줄에서 프로젝트 속성을 설정하려면  
  
- 속성 및 속성 값과 함께 **/property** 스위치를 사용 합니다. 예를 들어:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     \- 또는 -  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>명령줄에서 둘 이상의 프로젝트 속성을 지정하려면  
  
- 속성 및 속성 값에 **/property** 또는 **/p** 스위치를 여러 번 사용 하거나 하나의 **/property** 또는 **/p** 스위치를 사용 하 고 여러 속성을 세미콜론 (;)으로 구분 합니다. 예를 들어:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   \- 또는-  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  환경 변수는 속성으로 처리되고 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 의해 자동으로 통합되기도 합니다. 환경 변수 사용에 대한 자세한 내용은 [방법: 빌드 시 환경 변수 사용](../msbuild/how-to-use-environment-variables-in-a-build.md)을 참조하세요.  
  
  명령 줄에서 지정된 속성 값이 프로젝트 파일에서 같은 속성에 설정된 모든 값보다 우선 적용되고 프로젝트 파일의 값이 환경 변수의 값보다 우선 적용됩니다.  
  
  프로젝트 태그에서 `TreatAsLocalProperty` 특성을 사용하여 이 동작을 변경할 수 있습니다. 해당 특성을 통해 나열된 속성 이름의 경우 명령줄에서 지정된 속성 값이 프로젝트 파일의 값보다 우선 적용되지 않습니다. 이 항목의 뒷부분에 있는 예제를 참조하세요.  
  
## <a name="example"></a>예제  
 다음 코드 예제 "Hello World" 프로젝트에는 디버그 빌드 및 릴리스 빌드를 만드는 데 사용할 수 있는 새로운 두 가지 속성 그룹이 포함됩니다.  
  
 이 프로젝트의 디버그 버전을 빌드하려면 다음을 입력합니다.  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 이 프로젝트의 일반 정품 버전을 빌드하려면 다음을 입력합니다.  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>예제  
 다음 예제에서는 `TreatAsLocalProperty` 특성을 사용하는 방법을 보여 줍니다. `Color` 속성에는 프로젝트 파일의 `Blue` 값 및 명령줄의 `Green` 값이 포함됩니다. 프로젝트 태그의 `TreatAsLocalProperty="Color"`를 사용하면 명령줄 속성(`Green`)이 프로젝트 파일에 정의된 속성(`Blue`)을 재정의하지 않습니다.  
  
 프로젝트를 빌드하려면 다음 명령을 입력합니다.  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>관련 항목  
[MSBuild](msbuild.md)  
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [Project 요소 (MSBuild)](../msbuild/project-element-msbuild.md)
