---
title: GenerateApplicationManifest 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3493c487c446bb66e99bf98a7c3f5599599801fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841958"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 매니페스트 또는 네이티브 매니페스트를 생성합니다. 네이티브 매니페스트는 구성 요소의 고유 ID를 정의하고 구성 요소를 구성하는 모든 어셈블리와 파일을 식별하는 방식으로 구성 요소를 설명합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 매니페스트는 애플리케이션의 진입점을 지정하고 애플리케이션 보안 수준을 지정하여 네이티브 매니페스트를 확장합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `GenerateApplicationManifest` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`AssemblyName`|선택적 `String` 매개 변수입니다.<br /><br /> 생성된 매니페스트에 대한 어셈블리 ID의 `Name` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 이름은 `EntryPoint` 또는 `InputManifest` 매개 변수에서 유추됩니다. 이름을 만들 수 없으면 작업에서 오류가 throw됩니다.|  
|`AssemblyVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 생성된 매니페스트에 대한 어셈블리 ID의 `Version` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 기본값 “1.0.0.0”이 사용됩니다.|  
|`ClrVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션에 필요한 CLR(공용 언어 런타임 지원)의 최소 버전을 지정합니다. 기본값은 빌드 시스템에서 사용 중인 CLR 버전입니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 매개 변수가 무시됩니다.|  
|`ConfigFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 애플리케이션 구성 파일이 포함된 항목을 지정합니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 매개 변수가 무시됩니다.|  
|`Dependencies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 생성된 매니페스트에 대한 종속 어셈블리 집합을 정의하는 항목 목록을 지정합니다. 각 항목은 배포 상태 및 종속성 형식을 나타내는 항목 메타데이터를 통해 추가로 설명될 수 있습니다. 자세한 내용은 아래 “항목 메타데이터” 섹션을 참조하세요.|  
|`Description`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션 및 구성 요소에 대한 설명을 지정합니다.|  
|`EntryPoint`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 생성된 매니페스트 어셈블리에 대한 진입점을 나타내는 단일 항목을 지정합니다.<br /><br /> [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 매니페스트의 경우 이 매개 변수는 애플리케이션 실행 시 시작되는 어셈블리를 지정합니다.|  
|`ErrorReportUrl`|선택적 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> ClickOnce 설치의 오류 보고 중에 대화 상자에 표시되는 웹 페이지의 URL을 지정합니다.|  
|`FileAssociations`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> ClickOnce 배포 매니페스트와 연결된 하나 이상의 파일 형식 목록을 지정합니다.<br /><br /> .NET Framework 3.5 이상을 대상으로 할 경우에만 유효한 파일 연결입니다.|  
|`Files`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 매니페스트에 포함할 파일입니다. 각 파일의 전체 경로를 지정합니다.|  
|`HostInBrowser`|선택적 [부울](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> `true`의 경우 애플리케이션이 브라우저에서 호스트됩니다(예: WPF 웹 브라우저 애플리케이션).|  
|`IconFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 애플리케이션 아이콘 파일을 나타냅니다. 애플리케이션 아이콘은 생성된 애플리케이션 매니페스트에 표시되고 [시작] 메뉴 및 [프로그램 추가/제거] 대화 상자에 사용됩니다. 이 입력을 지정하지 않으면 기본 아이콘이 사용됩니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 매개 변수가 무시됩니다.|  
|`InputManifest`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 매니페스트 생성기에 대한 기본으로 사용되는 입력 XML 문서를 나타냅니다. 이를 통해 애플리케이션 보안 또는 사용자 지정 매니페스트 정의와 같은 구조화된 데이터가 출력 매니페스트에 반영될 수 있습니다. XML 문서의 루트 요소는 asmv1 네임스페이스의 어셈블리 노드여야 합니다.|  
|`IsolatedComReferences`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 생성된 매니페스트에서 격리할 COM 구성 요소를 지정합니다. 이 매개 변수는 “등록이 필요 없는 COM” 배포를 위해 COM 구성 요소를 격리하는 기능을 지원합니다. 이 기능은 표준 COM 등록 정의를 사용하여 매니페스트를 자동 생성하는 방식으로 작동합니다. 그러나 이 기능이 제대로 작동하려면 COM 구성 요소가 빌드 컴퓨터에 등록되어야 합니다.|  
|`ManifestType`|선택적 `String` 매개 변수입니다.<br /><br /> 생성할 매니페스트의 형식을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> 이 매개 변수를 지정하지 않으면 작업에서 기본적으로 `ClickOnce`가 사용됩니다.|  
|`MaxTargetPath`|선택적 `String` 매개 변수입니다.<br /><br /> [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 배포에서 사용할 파일 경로의 최대 허용 가능한 길이를 지정합니다. 이 값을 지정하는 경우 애플리케이션에서 각 파일 경로의 길이가 이 제한에 대해 확인됩니다. 제한을 초과하는 항목은 빌드 경고에서 발생합니다. 이 입력이 지정되지 않거나 0으로 지정된 경우 검사가 수행되지 않습니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 매개 변수가 무시됩니다.|  
|`OSVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션에 필요한 최소 OS(운영 체제) 버전을 지정합니다. 예를 들어 값 “5.1.2600.0”은 운영 체제가 Windows XP임을 나타냅니다. 이 매개 변수를 지정하지 않으면 값 .NET Framework의 최소 지원 OS인 Windows 98 Second Edition을 나타내는 “4.10.0.0”이 사용됩니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 입력이 무시됩니다.|  
|`OutputManifest`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 생성된 출력 매니페스트 파일의 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 출력 파일의 이름이 생성된 매니페스트의 ID에서 유추됩니다.|  
|`Platform`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 대상 플랫폼을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 이 매개 변수를 지정하지 않으면 작업에서 기본적으로 `AnyCPU`가 사용됩니다.|  
|`Product`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 이름이 생성된 매니페스트의 ID에서 유추됩니다. 이 이름은 시작 메뉴의 바로 가기 이름에 사용되고 프로그램 추가/제거 대화 상자에 표시되는 이름의 일부입니다.|  
|`Publisher`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 게시자를 지정합니다. 이 매개 변수를 지정하지 않으면 이름이 등록된 사용자 또는 생성된 매니페스트의 ID에서 유추됩니다. 이 이름은 시작 메뉴의 폴더 이름에 사용되고 프로그램 추가/제거 대화 상자에 표시되는 이름의 일부입니다.|  
|`RequiresMinimumFramework35SP1`|선택적 `Boolean` 매개 변수입니다.<br /><br /> True인 경우 애플리케이션에는 .NET Framework 3.5 SP1 이상의 최신 버전이 필요합니다.|  
|`TargetCulture`|선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 문화권을 식별하고 생성된 매니페스트에 대한 어셈블리 ID의 `Language` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 애플리케이션은 문화권이 고정되어 있다고 가정합니다.|  
|`TargetFrameworkMoniker`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> 대상 프레임워크 모니커를 지정합니다.|  
|`TargetFrameworkProfile`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> 대상 프레임워크 프로필을 지정합니다.|  
|`TargetFrameworkSubset`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> 대상으로 지정할 .NET Framework 하위 집합의 이름을 지정합니다.|  
|`TargetFrameworkVersion`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> 프로젝트의 대상 .NET Framework를 지정합니다.|  
|`TrustInfoFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 애플리케이션 보안을 지정하는 XML 문서를 나타냅니다. XML 문서의 루트 요소는 asmv2 네임스페이스의 trustInfo 노드여야 합니다. 작업에서 네이티브 매니페스트를 생성할 경우 이 매개 변수가 무시됩니다.|  
|`UseApplicationTrust`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> True인 경우 `Product`, `Publisher` 및 `SupportUrl` 속성은 애플리케이션 매니페스트에 기록됩니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 클래스의 매개 변수도 상속합니다. 작업 클래스의 매개 변수 목록은 [작업 기본 클래스](../msbuild/task-base-class.md)를 참조 하세요.  
  
 작업을 사용 하는 방법에 대 한 자세한 내용은 `GenerateDeploymentManifest` [Generateapplicationmanifest 작업](../msbuild/generateapplicationmanifest-task.md)을 참조 하세요.  
  
 종속성 및 파일에 대한 입력을 항목 메타데이터로 추가로 데코레이팅하면 각 항목의 추가 배포 상태를 지정할 수 있습니다.  
  
## <a name="item-metadata"></a>항목 메타데이터  
  
|메타데이터 이름|Description|  
|-------------------|-----------------|  
|`DependencyType`|종속성이 애플리케이션 또는 필수 구성 요소와 함께 게시 및 설치되는지 여부를 나타냅니다. 이 메타데이터는 모든 종속성에 유효하지만 파일에 사용되지 않습니다. 이 메타데이터의 사용 가능한 값은 다음과 같습니다.<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install이 기본값입니다.|  
|`AssemblyType`|종속성이 관리되는 어셈블리 또는 네이티브 어셈블리인지 나타냅니다. 이 메타데이터는 모든 종속성에 유효하지만 파일에 사용되지 않습니다. 이 메타데이터의 사용 가능한 값은 다음과 같습니다.<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified`가 기본값으로, 매니페스트 생성기가 자동으로 어셈블리 형식을 결정할 것임을 나타냅니다.|  
|`Group`|요청 시 추가 파일을 다운로드하기 위한 그룹을 나타냅니다. 그룹 이름은 애플리케이션에서 정의되고 문자열을 사용할 수 있습니다. 빈 문자열은 파일이 다운로드 그룹에 포함되지 않음을 나타내는 기본값입니다. 그룹에 포함되지 않은 파일은 초기 애플리케이션 다운로드에 포함되지 않습니다. 그룹에 포함된 파일은 <xref:System.Deployment.Application>을 애플리케이션에서 명시적으로 요청한 경우에만 다운로드됩니다.<br /><br /> 이 메타데이터는 `IsDataFile`이 `false`인 모든 파일 및 `DependencyType`이 `Install`인 모든 종속성에 유효합니다.|  
|`TargetPath`|생성된 매니페스트에서 경로를 정의하는 방법을 지정합니다. 이 특성은 모든 파일에 유효합니다. 이 특성을 지정하지 않으면 항목 사양이 사용됩니다. 이 특성은 `DependencyType` 값이 `Install`인 모든 파일 및 종속성에 유효합니다.|  
|`IsDataFile`|파일이 데이터 파일인지 여부를 나타내는 `Boolean` 메타데이터 값입니다. 데이터 파일은 애플리케이션 업데이트 간에 마이그레이션된다는 점에서 특별합니다. 이 메타데이터는 파일에만 유효합니다. 기본값은 `False`입니다.|  
  
## <a name="example"></a>예제  
 이 예제에서는 `GenerateApplicationManifest` 작업을 사용하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 매니페스트를 생성하고 `GenerateDeploymentManifest` 작업을 사용하여 단일 어셈블리가 포함된 애플리케이션의 배포 매니페스트를 생성합니다. 그런 다음 `SignFile` 작업을 사용하여 매니페스트에 서명합니다.  
  
 다음은 단일 프로그램에 대한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 매니페스트가 생성되는 가장 간단할 수 있는 매니페스트 생성 시나리오를 보여 줍니다. 기본 이름 및 ID는 매니페스트에 대한 어셈블리에서 유추됩니다.  
  
> [!NOTE]
> 아래 예제에서는 매니페스트 생성 측면에 집합하도록 모든 애플리케이션 이진 파일이 미리 빌드되어 있습니다. 이 예제에서는 완벽하게 작동하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 생성합니다.  
  
> [!NOTE]
> `Thumbprint`이 예제에서 작업에 사용 되는 속성에 대 한 자세한 내용은 `SignFile` [signfile 작업](../msbuild/signfile-task.md)을 참조 하세요.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>예제  
 이 예제에서는 `GenerateApplicationManifest` 및 `GenerateDeploymentManifest` 작업을 통해 단일 어셈블리가 포함된 애플리케이션에 대한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 및 배포 매니페스트를 생성하여 매니페스트의 이름과 ID를 지정합니다.  
  
 이 예제는 매니페스트의 이름 및 ID가 명시적으로 지정된다는 점을 제외하고 이전 예제와 비슷합니다. 또한 이 예제는 설치된 애플리케이션이 아닌 온라인 애플리케이션으로 구성됩니다.  
  
> [!NOTE]
> 아래 예제에서는 매니페스트 생성 측면에 집합하도록 모든 애플리케이션 이진 파일이 미리 빌드되어 있습니다. 이 예제에서는 완벽하게 작동하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 생성합니다.  
  
> [!NOTE]
> `Thumbprint`이 예제에서 작업에 사용 되는 속성에 대 한 자세한 내용은 `SignFile` [signfile 작업](../msbuild/signfile-task.md)을 참조 하세요.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>예제  
 이 예제에서는 `GenerateApplicationManifest` 및 `GenerateDeploymentManifest` 작업을 통해 여러 파일 및 어셈블리가 포함된 애플리케이션에 대한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 및 배포 매니페스트를 생성합니다.  
  
> [!NOTE]
> 아래 예제에서는 매니페스트 생성 측면에 집합하도록 모든 애플리케이션 이진 파일이 미리 빌드되어 있습니다. 이 예제에서는 완벽하게 작동하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 생성합니다.  
  
> [!NOTE]
> `Thumbprint`이 예제에서 작업에 사용 되는 속성에 대 한 자세한 내용은 `SignFile` [signfile 작업](../msbuild/signfile-task.md)을 참조 하세요.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>예제  
 이 예제에서는 `GenerateApplicationManifest` 작업을 통해 애플리케이션 Test.exe에 대한 네이티브 매니페스트를 생성하여 네이티브 구성 요소 Alpha.dll 및 격리된 COM 구성 요소 Bravo.dll을 참조합니다.  
  
 이 예제에서는 Test.exe.manifest를 생성하여 등록이 필요 없는 COM을 활용하는 애플리케이션 XCOPY를 배포 가능하도록 만듭니다.  
  
> [!NOTE]
> 아래 예제에서는 매니페스트 생성 측면에 집합하도록 모든 애플리케이션 이진 파일이 미리 빌드되어 있습니다. 이 예제에서는 완벽하게 작동하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 생성합니다.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest 작업](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile 작업](../msbuild/signfile-task.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
