---
title: MSBuild 대상 | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b3fcea8d073b4c40685d41b7432f1e24662a7ad
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633189"
---
# <a name="msbuild-targets"></a>MSBuild 대상

대상은 특정 순서로 작업을 그룹화하며 빌드 프로세스를 더 작은 단위로 팩터링될 수 있도록 합니다. 예를 들어 하나의 대상이 빌드에 대한 준비를 위해 출력 디렉터리에서 모든 파일을 삭제할 수 있는 반면 다른 대상은 프로젝트에 대한 입력을 컴파일하고 빈 디렉터리에 배치합니다. 작업에 대한 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

## <a name="declare-targets-in-the-project-file"></a>프로젝트 파일에서 대상 선언

 [Target](../msbuild/target-element-msbuild.md) 요소로 프로젝트 파일에 대상을 선언합니다. 예를 들어 다음 XML은 Construct라는 대상을 만든 다음 컴파일 항목 형식으로 Csc 작업을 호출합니다.

```xml
<Target Name="Construct">
    <Csc Sources="@(Compile)" />
</Target>
```

 MSBuild 속성처럼 대상은 다시 정의될 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<Target Name="AfterBuild" >
    <Message Text="First occurrence" />
</Target>
<Target Name="AfterBuild" >
    <Message Text="Second occurrence" />
</Target>
```

 AfterBuild가 실행되는 경우 "두 번째 발생"만 표시됩니다.

 MSBuild는 가져오기 순서에 종속되며, 대상의 마지막 정의가 사용됩니다.

## <a name="target-build-order"></a>대상 빌드 순서

 단일 대상에 대한 입력이 다른 대상의 출력을 사용하는 경우에는 대상의 순서를 지정해야 합니다.
 
 대상 실행의 순서를 지정하는 방법은 여러 가지가 있습니다.

- 초기 대상

- 기본 대상

- 첫 번째 대상

- 대상 종속성

- `BeforeTargets` 및 `AfterTargets`(MSBuild 4.0)

대상은 빌드의 후속 대상이 종속되더라도 단일 빌드 중에 두 번 실행되지 않습니다. 대상이 실행되면 빌드 내에서 해당 대상의 역할은 완료됩니다.

대상 빌드 순서에 대한 세부 내용 및 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md)를 참조하세요.

## <a name="target-batching"></a>대상 일괄 처리

대상 요소에는 %(\<Metadata>) 형식에서 메타데이터를 지정하는 `Outputs` 특성이 있을 수 있습니다. 이 경우 MSBuild는 해당 메타데이터 값을 가진 항목을 그룹화 또는 "일괄 처리"하여 각 고유 메타데이터 값에 대해 한 번씩 대상을 실행합니다. 예를 들면 다음과 같습니다.

```xml
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

## <a name="default-build-targets"></a>기본 빌드 대상

다음은 Microsoft.Common.CurrentVersion.Targets의 공용 대상입니다.

```
===================================================
Build
The main build entry point.
===================================================
<Target Name="Build"
    Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
    DependsOnTargets="$(BuildDependsOn)"
    Returns="$(TargetPath)" />


===================================================
BeforeBuild
Redefine this target in your project in order to run tasks just before Build
===================================================
<Target Name="BeforeBuild"/>


===================================================
AfterBuild
Redefine this target in your project in order to run tasks just after Build
===================================================
<Target Name="AfterBuild"/>


===================================================
CoreBuild
The core build step calls each of the build targets.
===================================================
<Target Name="CoreBuild"
    DependsOnTargets="$(CoreBuildDependsOn)">


===================================================
Rebuild
Delete all intermediate and final build outputs, and then build the project from scratch.
===================================================
<Target Name="Rebuild"
    Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
    DependsOnTargets="$(RebuildDependsOn)"
    Returns="$(TargetPath)"/>


===================================================
BeforeRebuild
Redefine this target in your project in order to run tasks just before Rebuild
===================================================
<Target Name="BeforeRebuild"/>


===================================================
AfterRebuild
Redefine this target in your project in order to run tasks just after Rebuild
===================================================
<Target Name="AfterRebuild"/>


===================================================
BuildGenerateSources
Redefine this target in your project in order to run tasks for BuildGenerateSources
Set BuildPassReferences to enable P2P builds
===================================================
<Target Name="BuildGenerateSources"
    DependsOnTargets="BuildGenerateSourcesTraverse;$(BuildGenerateSourcesAction)" />


===================================================
BuildCompile
Redefine this target in your project in order to run tasks for BuildCompile
===================================================
<Target Name="BuildCompile"
    DependsOnTargets="BuildCompileTraverse;$(BuildCompileAction)" />


===================================================
BuildLink
Redefine this target in your project in order to run tasks for BuildLink
===================================================
<Target Name="BuildLink"
    DependsOnTargets="BuildLinkTraverse;$(BuildLinkAction)" />


===================================================
CopyRunEnvironmentFiles
Copy environment files necessary to run the user's app to the final directory.
This is a public target that can be invoked by an IDE.
This may be used by an IDE to make the app.config file available for running
the target app.
===================================================
<Target
    Name="CopyRunEnvironmentFiles"
    DependsOnTargets="PrepareForBuild;SetWin32ManifestProperties;_CopyAppConfigFile;_CleanRecordFileWrites"/>


===================================================
Run
Run the final build output if it is a .EXE
===================================================
<Target
    Name="Run"
    DependsOnTargets="$(RunDependsOn)">


===================================================
BuildOnlySettings
This target is called only when doing a real build.  It is specifically not called during project load.
===================================================
<Target Name="BuildOnlySettings">


===================================================
PrepareForBuild
Prepare the prerequisites for building.
===================================================
<Target Name="PrepareForBuild"
    DependsOnTargets="$(PrepareForBuildDependsOn)">


===================================================
GetFrameworkPaths
Get the paths for the .NET Framework installation directory

These paths are not used directly by this .targets file but are available for pre and
post build steps.

This is a generally overriden target, for example it is overriden in the Microsoft.NETFramework.targets file
===================================================
<Target Name="GetFrameworkPaths"/>


===================================================
GetReferenceAssemblyPaths
Get the paths for the Reference Assemblies for the known versions of the
.NET Framework.

These paths are used by the build process in order to resolve the correct
assemblies from the various directories, and to support multi-targeting
===================================================
<Target Name="GetReferenceAssemblyPaths"
    DependsOnTargets="$(GetReferenceAssemblyPathsDependsOn)">


===================================================
AssignLinkMetadata
For items of a certain set of whitelisted types, make sure that
if they are defined in a file other than the project file, that 
they have "Link" metadata set to an appropriate default. 
===================================================
<Target Name="AssignLinkMetadata"
    Condition=" '$(SynthesizeLinkMetadata)' == 'true' ">


===================================================
PreBuildEvent
Run the pre-build event if there is one.
===================================================
<Target Name="PreBuildEvent"
    Condition="'$(PreBuildEvent)'!=''"
    DependsOnTargets="$(PreBuildEventDependsOn)">


===================================================
UnmanagedUnregistration
If the main assembly had previously been registered for COM interop, unregister it now.
We will re-register the new version after it has been built.
===================================================
<Target Name="UnmanagedUnregistration"
    Condition="(('$(_AssemblyTimestampBeforeCompile)' != '$(_AssemblyTimestampAfterCompile)' or '$(RegisterForComInterop)' != 'true' or '$(OutputType)' != 'library') or
                ('$(_AssemblyTimestampBeforeCompile)' == '')) and
               Exists('@(_UnmanagedRegistrationCache)')"
    DependsOnTargets="$(UnmanagedUnregistrationDependsOn)">


===================================================
GetTargetFrameworkVersion
This stand-alone target returns the target framework version (i.e. v3.5, v4.0, etc.)
that would be used if we built this project.
===================================================
<Target
    Name="GetTargetFrameworkVersion"
    Returns="$(TargetFrameworkVersion)" />


===================================================
ResolveReferences
===================================================
<Target Name="ResolveReferences"
    DependsOnTargets="$(ResolveReferencesDependsOn)"/>


===================================================
BeforeResolveReferences
Redefine this target in your project in order to run tasks just before ResolveReferences
===================================================
<Target Name="BeforeResolveReferences"/>


===================================================
AfterResolveReferences
Redefine this target in your project in order to run tasks just after ResolveReferences
===================================================
<Target Name="AfterResolveReferences"/>


===================================================
AssignProjectConfiguration
Assigns the appropriate configuration to each project in the list of project references passed in.
Adds to the project references passed in any project references implied by dependencies expressed in the solution file, if any.
===================================================
<Target Name="AssignProjectConfiguration"
    Condition="'$(CurrentSolutionConfigurationContents)' != '' or '@(ProjectReference)'!=''">


===================================================
ResolveProjectReferences
Build referenced projects
===================================================
<Target Name="ResolveProjectReferences"
    DependsOnTargets="AssignProjectConfiguration;_SplitProjectReferencesByFileExistence"
    Returns="@(_ResolvedNativeProjectReferencePaths);@(_ResolvedProjectReferencePaths)">


===================================================
GetTargetPath
This stand-alone target returns the name of the build product (i.e. EXE, DLL)
that would be produced if we built this project.
===================================================
<Target Name="GetTargetPath"
    DependsOnTargets="$(GetTargetPathDependsOn)"
    Returns="$(TargetPath)"/>


===================================================
GetTargetPathWithTargetPlatformMoniker
This stand-alone target returns the name and version of the target platform for this project.
===================================================
<Target Name="GetTargetPathWithTargetPlatformMoniker"
    DependsOnTargets="$(GetTargetPathWithTargetPlatformMonikerDependsOn)"
    Returns="@(TargetPathWithTargetPlatformMoniker)">


===================================================
GetNativeManifest
Compute the manifest item for this project.
===================================================
<Target
    Name="GetNativeManifest"
    Returns="@(ComputedApplicationManifest)">


===================================================
ResolveNativeReferences
Resolve native references
===================================================
<Target Name="ResolveNativeReferences"
    Condition="'@(NativeReference)'!=''"
    DependsOnTargets="ResolveProjectReferences">


===================================================
ResolveAssemblyReferences
Given the list of assemblies, find the closure of all assemblies that they depend on. These are
what we need to copy to the output directory.

[IN]
@(Reference) - List of assembly references as fusion names.
@(_ResolvedProjectReferencePaths) - List of project references produced by projects that this project depends on.

    The 'Private' attribute on the reference corresponds to the Copy Local flag in IDE.
    The 'Private' flag can have three possible values:
        - 'True' means the reference should be Copied Local
        - 'False' means the reference should not be Copied Local
        - [Missing] means this task will decide whether to treat this reference as CopyLocal or not.

[OUT]
@(ReferencePath) - Paths to resolved primary files.
@(ReferenceDependencyPaths) - Paths to resolved dependency files.
@(_ReferenceRelatedPaths) - Paths to .xmls and .pdbs.
@(ReferenceSatellitePaths) - Paths to satellites.
@(_ReferenceSerializationAssemblyPaths) - Paths to XML serialization assemblies created by sgen.
@(_ReferenceScatterPaths) - Paths to scatter files.
@(ReferenceCopyLocalPaths) - Paths to files that should be copied to the local directory.
===================================================
<Target Name="ResolveAssemblyReferences"
    Returns="@(ReferencePath)"
    DependsOnTargets="$(ResolveAssemblyReferencesDependsOn)">


===================================================
GenerateBindingRedirects
Inject the binding redirects into the app config file based on suggested redirects as output from ResolveAssemblyReferences.

[IN]
@(AppConfigWithTargetPath) - Path to the source app config file. This can be null if the project 
                             doesn't contain an app config file.
$(TargetFileName) -          The file name of the build target.

[OUT]
@(OutputAppConfigFile) -     Path to the output app config file in the intermediate directory.
===================================================
<Target Name="GenerateBindingRedirects"
    Inputs="$(MSBuildAllProjects);@(AppConfigFile);$(ResolveAssemblyReferencesStateFile);$(IntermediateOutputPath);@(SuggestedBindingRedirects)"
    Outputs="$(_GenerateBindingRedirectsIntermediateAppConfig)"
    Condition="'$(AutoGenerateBindingRedirects)' == 'true' and '$(GenerateBindingRedirectsOutputType)' == 'true'">


===================================================
GenerateBindingRedirectsUpdateAppConfig
Updates the project to use the generated app.config content.  This needs to run regardless of 
inputs/outputs so it is seperate from GenerateBindingRedirects.
===================================================
<Target Name="GenerateBindingRedirectsUpdateAppConfig"
    AfterTargets="GenerateBindingRedirects"
    Condition="'$(AutoGenerateBindingRedirects)' == 'true' and '$(GenerateBindingRedirectsOutputType)' == 'true' and Exists('$(_GenerateBindingRedirectsIntermediateAppConfig)')">


===================================================
GetInstalledSDKs
Gets the list of SDKs installed in the SDKDirectoryRoot and SDKRegistryRoot locations
These paths are used by the ResolveSDKReference task and the ResolveAssemblyReference task.
===================================================
<Target Name="GetInstalledSDKLocations"
      DependsOnTargets="$(GetInstalledSDKLocationsDependsOn)"
      Returns="@(InstalledSDKLocations)" />


===================================================
ResolveSDKReferences
Given a list of SDKReference items and a list of resolved winmd files which may contain metadata as to which sdk they came from
we need to find the sdk root folders on disk and populate a ResolvedSDKReference item which has the full path to the SDK ROOT 
and the sdk identity as a piece of metadata.
===================================================
<Target Name="ResolveSDKReferences"
    Returns="@(ResolvedSDKReference)"
    DependsOnTargets="$(ResolveSDKReferencesDependsOn)">


===================================================
FindInvalidProjectReferences
Find project to project references with target platform version higher than the one used by the current project and 
creates a list of invalid references to be unresolved. It issues a warning for each invalid reference.
===================================================
<Target Name="FindInvalidProjectReferences"
    Condition ="'$(FindInvalidProjectReferences)' == 'true'"
    DependsOnTargets="$(FindInvalidProjectReferencesDependsOn)">


===================================================
ExpandSDKReferences
After we have resolved the sdk refrence we need to make sure that we automatically include the references which are part of the SDK (both winmd and dll)
as part of the assemblies passed to the compiler.

Project systems or project which do not want to reference all dlls or winmd files should override this target to do nothing.
===================================================
<Target Name="ExpandSDKReferences"
    Returns="@(ReferencesFromSDK)"
    DependsOnTargets="$(ExpandSDKReferencesDependsOn)" />


===================================================
ExportWindowsMDFile
When a project is generating a a winmd file through c# or vb, ect the compiler will create a WinMDModule file. This file needs to be run
through the winmdexp tool in order to generate the resulting WinMD file.
===================================================
<Target Name="ExportWindowsMDFile"
    DependsOnTargets="Compile"
    Condition="'$(ExportWinMDFile)' == 'true'"
    Inputs="@(IntermediateAssembly);@(DocFileItem);@(_DebugSymbolsIntermediatePath);@(ReferencePath);$(MSBuildAllProjects)"
    Outputs="$(_IntermediateWindowsMetadataPath);$(WinMDExpOutputPdb);$(WinMDOutputDocumentationFile)" />


===================================================
DesignTimeResolveAssemblyReferences
Given the list of assemblies, resolve their reference paths.
This target is called by Visual Studio at run time in order to filter references
according to the targeted framework.
===================================================
<Target Name="DesignTimeResolveAssemblyReferences"
    Condition="'$(DesignTimeReference)'!=''"
    DependsOnTargets="$(DesignTimeResolveAssemblyReferencesDependsOn)">


===================================================
ResolveComReferences
Resolve COM references
===================================================
<Target Name="ResolveComReferences"
    Condition="'@(COMReference)'!='' or '@(COMFileReference)'!=''"
    Returns="@(ReferencePath)"
    DependsOnTargets="PrepareForBuild;ResolveKeySource;ResolveAssemblyReferences" />


===================================================
PrepareResources
Prepare resources for the Compile step.
===================================================
<Target Name="PrepareResources"
    DependsOnTargets="$(PrepareResourcesDependsOn)"/>


===================================================
PrepareResourceNames
Prepare the names of resource files.
===================================================
<Target Name="PrepareResourceNames"
    DependsOnTargets="$(PrepareResourceNamesDependsOn)"/>


===================================================
AssignTargetPaths
This target creates <TargetPath> tags for items. <TargetPath> is a relative folder plus filename
for the destination of this item.
===================================================
<Target Name="AssignTargetPaths"
    DependsOnTargets="$(AssignTargetPathsDependsOn)">


===================================================
GetItemTargetPaths
This target returns all items that have TargetPath metadata assigned by the AssignTargetPaths target.
===================================================
<Target Name="GetItemTargetPaths"
    DependsOnTargets="AssignTargetPaths"
    Returns="
    @(EmbeddedResource);
    @(ContentWithTargetPath);
    @(_NoneWithTargetPath);
    @(_DeploymentBaseManifestWithTargetPath);
    " />


===================================================
SplitResourcesByCulture
Split EmbeddedResource items into five lists based on whether
they are resx files, licx files or other resources and whether they should be localized. Also adds Type and Culture
metadata. Type indicates whether the resource is "Resx" or "Non-Resx".
===================================================
<Target Name="SplitResourcesByCulture"
    DependsOnTargets="AssignTargetPaths">


===================================================
CreateCustomManifestResourceNames
Allows custom manifest resource name generation tasks to plug
into the build process
===================================================
<Target Name="CreateCustomManifestResourceNames"
    DependsOnTargets="$(CreateCustomManifestResourceNamesDependsOn)"/>


===================================================
ResGen
Run GenerateResource on the given resx files.
===================================================
<Target Name="ResGen"
    DependsOnTargets="$(ResGenDependsOn)"/>


===================================================
BeforeResGen
Redefine this target in your project in order to run tasks just before Resgen.
===================================================
<Target Name="BeforeResGen"/>


===================================================
AfterResGen
Redefine this target in your project in order to run tasks just after Resgen.
===================================================
<Target Name="AfterResGen"/>


===================================================
ResolveKeySource
Resolve the strong name key used to sign the assembly as well as the certificate used to
sign the ClickOnce manifests.
===================================================
<Target Name="ResolveKeySource"
    Condition="$(SignManifests) == 'true' or $(SignAssembly) == 'true'">


===================================================
Compile
===================================================
<Target Name="Compile"
    DependsOnTargets="$(CompileDependsOn)"/>


===================================================
GenerateTargetFrameworkMonikerAttribute
Emit the target framework moniker attribute as  a code fragment into a temporary source file for the compiler.
===================================================
<Target Name="GenerateTargetFrameworkMonikerAttribute"
    BeforeTargets="BeforeCompile"
    DependsOnTargets="PrepareForBuild;GetReferenceAssemblyPaths"
    Inputs="$(MSBuildToolsPath)\Microsoft.Common.targets"
    Outputs="$(TargetFrameworkMonikerAssemblyAttributesPath)"
    Condition="'$(GenerateTargetFrameworkAttribute)' == 'true'">


===================================================
GenerateAdditionalSources
Emit any specified code fragments into a temporary source file for the compiler.
===================================================
<Target Name="GenerateAdditionalSources"
    BeforeTargets="BeforeCompile"
    DependsOnTargets="PrepareForBuild;GetReferenceAssemblyPaths"
    Inputs="$(MSBuildAllProjects)"
    Outputs="$(AssemblyAttributesPath)"
    Condition="'@(AssemblyAttributes)' != '' and '$(GenerateAdditionalSources)' == 'true'">


===================================================
BeforeCompile
Redefine this target in your project in order to run tasks just before Compile.
===================================================
<Target Name="BeforeCompile"/>


===================================================
AfterCompile
Redefine this target in your project in order to run tasks just after Compile.
===================================================
<Target Name="AfterCompile"/>


===================================================
GenerateSerializationAssemblies
Run GenerateSerializationAssemblies on the assembly produced by this build.
===================================================
<Target Name="GenerateSerializationAssemblies"
    Condition="'$(_SGenGenerateSerializationAssembliesConfig)' == 'On' or ('@(WebReferenceUrl)'!='' and '$(_SGenGenerateSerializationAssembliesConfig)' == 'Auto')"
    DependsOnTargets="AssignTargetPaths;Compile;ResolveKeySource"
    Inputs="$(MSBuildAllProjects);@(IntermediateAssembly)"
    Outputs="$(IntermediateOutputPath)$(_SGenDllName)">


===================================================
CreateSatelliteAssemblies
Create one satellite assembly for every unique culture in the resources.
===================================================
<Target Name="CreateSatelliteAssemblies"
    DependsOnTargets="$(CreateSatelliteAssembliesDependsOn)" />


===================================================
GenerateSatelliteAssemblies
Actually run al.exe to create the satellite assemblies.
===================================================
<Target Name="GenerateSatelliteAssemblies"
    Inputs="$(MSBuildAllProjects);@(_SatelliteAssemblyResourceInputs);$(IntermediateOutputPath)$(TargetName)$(TargetExt)"
    Outputs="$(IntermediateOutputPath)%(Culture)\$(TargetName).resources.dll"
    Condition="'@(_SatelliteAssemblyResourceInputs)' != ''">


===================================================
ComputeIntermediateSatelliteAssemblies
Compute the paths to the intermediate satellite assemblies,
with culture attributes so we can copy them to the right place.
===================================================
<Target Name="ComputeIntermediateSatelliteAssemblies"
    Condition="@(EmbeddedResource->'%(WithCulture)') != ''"
    DependsOnTargets="$(ComputeIntermediateSatelliteAssembliesDependsOn)">


===================================================
SetWin32ManifestProperties
Set Win32Manifest and EmbeddedManifest properties to be used later in the build.
===================================================
<Target Name="SetWin32ManifestProperties"
    Condition="'$(Win32Manifest)'==''"
    DependsOnTargets="ResolveComReferences;ResolveNativeReferences;_SetExternalWin32ManifestProperties;_SetEmbeddedWin32ManifestProperties" />


===================================================
GenerateManifests
Generates ClickOnce application and deployment manifests or a native manifest.
===================================================
<Target Name="GenerateManifests"
    Condition="'$(GenerateClickOnceManifests)'=='true' or '@(NativeReference)'!='' or '@(ResolvedIsolatedComModules)'!='' or '$(GenerateAppxManifest)' == 'true'"
    DependsOnTargets="$(GenerateManifestsDependsOn)"/>


===================================================
GenerateApplicationManifest
Generates a ClickOnce or native application manifest.
An application manifest specifies declarative application identity, dependency and security information.
===================================================
<Target Name="GenerateApplicationManifest"
    DependsOnTargets="
        _DeploymentComputeNativeManifestInfo;
        _DeploymentComputeClickOnceManifestInfo;
        ResolveComReferences;
        ResolveNativeReferences;
        _GenerateResolvedDeploymentManifestEntryPoint"
    Inputs="
        $(MSBuildAllProjects);
        @(AppConfigWithTargetPath);
        $(_DeploymentBaseManifest);
        @(ResolvedIsolatedComModules);
        @(_DeploymentManifestDependencies);
        @(_DeploymentResolvedManifestEntryPoint);
        @(_DeploymentManifestFiles)"
    Outputs="@(ApplicationManifest)">


===================================================
GenerateDeploymentManifest
Generates a ClickOnce deployment manifest.
An deployment manifest specifies declarative application identity and application update information.
===================================================
<Target Name="GenerateDeploymentManifest"
    DependsOnTargets="GenerateApplicationManifest"
    Inputs="
        $(MSBuildAllProjects);
        @(ApplicationManifest)
        "
    Outputs="@(DeployManifest)">


===================================================
PrepareForRun
Copy the build outputs to the final directory if they have changed.
===================================================
<Target Name="PrepareForRun"
    DependsOnTargets="$(PrepareForRunDependsOn)"/>


===================================================
CopyFilesToOutputDirectory
Copy all build outputs, satellites and other necessary files to the final directory.
===================================================
<Target Name="CopyFilesToOutputDirectory"
    DependsOnTargets="
        ComputeIntermediateSatelliteAssemblies;
        _CopyFilesMarkedCopyLocal;
        _CopySourceItemsToOutputDirectory;
        _CopyAppConfigFile;
        _CopyManifestFiles;
        _CheckForCompileOutputs;
        _SGenCheckForOutputs">


===================================================
GetCopyToOutputDirectoryItems
Get all project items that may need to be transferred to the output directory.
This includes baggage items from transitively referenced projects. It would appear
that this target computes full transitive closure of content items for all referenced
projects; however that is not the case. It only collects the content items from its
immediate children and not children of children. The reason this happens is that
the ProjectReferenceWithConfiguration list that is consumed by _SplitProjectReferencesByFileExistence
is only populated in the current project and is empty in the children. The empty list
causes _MSBuildProjectReferenceExistent to be empty and terminates the recursion.
===================================================
<Target Name="GetCopyToOutputDirectoryItems"
    Returns="@(AllItemsFullPathWithTargetPath)"
    KeepDuplicateOutputs=" '$(MSBuildDisableGetCopyToOutputDirectoryItemsOptimization)' == '' "
    DependsOnTargets="$(GetCopyToOutputDirectoryItemsDependsOn)">


===================================================
UnmanagedRegistration
Registers the main assembly for COM interop.
===================================================
<Target Name="UnmanagedRegistration"
    Condition="'$(RegisterForComInterop)'=='true' and '$(OutputType)'=='library'"
    DependsOnTargets="$(UnmanagedRegistrationDependsOn)" />>


===================================================
IncrementalClean
Remove files that were produced in a prior build but weren't produced in the current build.
The reason is that if, for example, the name of the .exe has changed we want to delete the
old copy.

Leave the Clean cache file containing only the files produced in the current build.
===================================================
<Target Name="IncrementalClean"
    DependsOnTargets="_CleanGetCurrentAndPriorFileWrites">


===================================================
Clean
Delete all intermediate and final build outputs.
===================================================
<Target Name="Clean"
    Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
    DependsOnTargets="$(CleanDependsOn)" />


===================================================
BeforeClean
Redefine this target in your project in order to run tasks just before Clean.
===================================================
<Target Name="BeforeClean"/>


===================================================
AfterClean
Redefine this target in your project in order to run tasks just after Clean.
===================================================
<Target Name="AfterClean"/>


===================================================
CleanReferencedProjects
Call Clean target on all Referenced Projects.
===================================================
<Target Name="CleanReferencedProjects"
    DependsOnTargets="AssignProjectConfiguration; _SplitProjectReferencesByFileExistence">


===================================================
CleanPublishFolder
===================================================
<Target Name="CleanPublishFolder"/>


===================================================
PostBuildEvent
Run the post-build event. This step is driven by two parameters:

(1) The $(RunPostBuildEvent) property is set by the user through the IDE and can be one of four values.

    - OnBuildSuccess: In this case, every step of the build must succeed for the post-build step to run.
    - <Blank>: This is the same as OnBuildSuccess.
    - OnOutputUpdated: In this case, the post-build step will run only if the main output assembly was
    actually updated.
    - Always: The post-build step is always run.

(2) The $(_AssemblyTimestampBeforeCompile) and $(_AssemblyTimestampAfterCompile) values are
    set by the _TimeStampBeforeCompile and _TimeStampAfterCompile targets.  If the assembly was actually
    rebuilt during this build, then the two values will be different.
===================================================
<Target Name="PostBuildEvent"
    Condition="'$(PostBuildEvent)' != '' and ('$(RunPostBuildEvent)' != 'OnOutputUpdated' or '$(_AssemblyTimestampBeforeCompile)' != '$(_AssemblyTimestampAfterCompile)')"
    DependsOnTargets="$(PostBuildEventDependsOn)">


===================================================
Publish
This target is only called when doing ClickOnce publishing outside the IDE, which implicitly builds before publishing.
===================================================
<Target Name="Publish"
    DependsOnTargets="$(PublishDependsOn)"/>


===================================================
SetGenerateManifests
This target simply assures the GenerateClickOnceManifests property is set whenever the publish target is invoked.
===================================================
<Target Name="SetGenerateManifests"/>


===================================================
PublishOnly
The "PublishOnly" target is intended for ClickOnce publishing inside the IDE, where the build has already been done
by the BuildManager.
===================================================
<Target Name="PublishOnly"
    DependsOnTargets="$(PublishOnlyDependsOn)"/>


===================================================
BeforePublish
Redefine this target in your project in order to run tasks just before Publish.
===================================================
<Target Name="BeforePublish"/>


===================================================
AfterPublish
Redefine this target in your project in order to run tasks just after Publish.
===================================================
<Target Name="AfterPublish"/>


===================================================
PublishBuild
Defines the set of targets that publishing is directly dependent on.
===================================================
<Target Name="PublishBuild"
    DependsOnTargets="$(PublishBuildDependsOn)"/>


===================================================
AllProjectOutputGroups
The targets below drive output groups, which provide generic information about a
project's inputs (e.g., content files, compilation sources, etc.) and built outputs
(e.g., built EXE/DLL, PDB, XML documentation files, etc.)

Each target may produce two kinds of items:  outputs and dependencies.  Outputs are
items from the current project; dependencies are items that are brought into the
current project as a result of referencing other projects or components.

For both outputs and dependencies, the Include attribute
specifies the location of the output/dependency; it must be a full path.  Any number
of additional attributes may be placed on an output/dependency item.
===================================================
<Target Name="AllProjectOutputGroups"
    DependsOnTargets="
        BuiltProjectOutputGroup;
        DebugSymbolsProjectOutputGroup;
        DocumentationProjectOutputGroup;
        SatelliteDllsProjectOutputGroup;
        SourceFilesProjectOutputGroup;
        ContentFilesProjectOutputGroup;
        SGenFilesOutputGroup"/>


===================================================
BuiltProjectOutputGroup
This target performs population of the Build project output group.
===================================================
<Target Name="BuiltProjectOutputGroup"
    Returns="@(BuiltProjectOutputGroupOutput)"
    DependsOnTargets="$(BuiltProjectOutputGroupDependsOn)">


===================================================
DebugSymbolsProjectOutputGroup
This target performs population of the Debug Symbols project output group.
===================================================
<Target Name="DebugSymbolsProjectOutputGroup"
    Returns="@(DebugSymbolsProjectOutputGroupOutput)"
    DependsOnTargets="$(DebugSymbolsProjectOutputGroupDependsOn)"/>


===================================================
DocumentationProjectOutputGroup
This target performs population of the Documentation project output group.
===================================================
<Target Name="DocumentationProjectOutputGroup"
    Returns="@(DocumentationProjectOutputGroupOutput)"
    DependsOnTargets="$(DocumentationProjectOutputGroupDependsOn)"/>


===================================================
SatelliteDllsProjectOutputGroup
This target performs population of the Satellite Files project output group.
===================================================
<Target Name="SatelliteDllsProjectOutputGroup"
    Returns="@(SatelliteDllsProjectOutputGroupOutput)"
    DependsOnTargets="$(SatelliteDllsProjectOutputGroupDependsOn)">


===================================================
SourceFilesProjectOutputGroup
This target performs population of the Source Files project output group.
Source files are items in the project whose type is "Compile" and "EmbeddedResource".
===================================================
<Target Name="SourceFilesProjectOutputGroup"
    Returns="@(SourceFilesProjectOutputGroupOutput)"
    DependsOnTargets="$(SourceFilesProjectOutputGroupDependsOn)">


===================================================
ContentFilesProjectOutputGroup
This target performs population of the Content Files project output group.
Content files are items in the project whose type is "Content".
===================================================
<Target Name="ContentFilesProjectOutputGroup"
    Returns="@(ContentFilesProjectOutputGroupOutput)"
    DependsOnTargets="$(ContentFilesProjectOutputGroupDependsOn)">


===================================================
SGenFilesOutputGroup
This target performs population of the GenerateSerializationAssemblies Files project output group.
GenerateSerializationAssemblies files are those generated by the GenerateSerializationAssemblies target and task.
===================================================
<Target Name="SGenFilesOutputGroup"
    Returns="@(SGenFilesOutputGroupOutput)"
    DependsOnTargets="$(SGenFilesOutputGroupDependsOn)"/>


===================================================
GetResolvedSDKReferences
These targets are to gather information from the SDKs.
===================================================
<Target Name="GetResolvedSDKReferences"
    DependsOnTargets="ResolveSDKReferences"
    Returns="@(ResolvedSDKReference)"/>


===================================================
PriFilesOutputGroup
This target performs population of the pri files output group
===================================================
<Target Name="PriFilesOutputGroup"
    Condition="'@(_ReferenceRelatedPaths)' != ''"
    DependsOnTargets="BuildOnlySettings;PrepareForBuild;AssignTargetPaths;ResolveReferences"
    Returns="@(PriFilesOutputGroupOutput)">


===================================================
SDKRedistOutputGroup
This target gathers the Redist folders from the SDKs which have been resolved.
===================================================
<Target Name="SDKRedistOutputGroup"
    Returns="@(SDKRedistOutputGroupOutput)"
    DependsOnTargets="$(SDKRedistOutputGroupDependsOn)"/>
```

## <a name="see-also"></a>참조

- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [방법: 여러 프로젝트 파일에서 동일한 대상 사용](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
