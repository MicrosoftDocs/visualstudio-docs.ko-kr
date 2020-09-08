---
title: ResolveAssemblyReference 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveAssemblyReference
- MSBuild.ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects
- MSBuild.ResolveAssemblyReference.FoundConflict
- MSBuild.ResolveAssemblyRedirects.SuggestedRedirects
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveAssemblyReference task [MSBuild]
- MSBuild, ResolveAssemblyReference task
ms.assetid: 4d56d848-b29b-4dff-86a2-0a96c9e4a170
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b79bd8eb3f7d813e3acd091ce5f2ffbc7b3eeb49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632760"
---
# <a name="resolveassemblyreference-task"></a>ResolveAssemblyReference 작업

두 번째 및 `n`번째 순서 종속성을 비롯하여 지정한 어셈블리에 종속되는 모든 어셈블리를 확인합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `ResolveAssemblyReference` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`AllowedAssemblyExtensions`|선택적 `String[]` 매개 변수입니다.<br /><br /> 참조를 확인할 때 사용할 어셈블리 파일 확장명입니다. 기본 파일 이름 확장명은 *.exe* 및 *.dll*입니다.|
|`AllowedRelatedFileExtensions`|선택적 `String[]` 매개 변수입니다.<br /><br /> 서로 관련된 파일을 검색하는 데 사용할 파일 확장명입니다. 기본 확장명은 *.pdb* 및 *.xml*입니다.|
|`AppConfigFile`|선택적 `String` 매개 변수입니다.<br /><br /> 구문 분석하고 bindingRedirect 매핑을 추출할 *app.config* 파일을 지정합니다. 이 매개 변수가 지정되어 있으면 `AutoUnify` 매개 변수가 `false`여야 합니다.|
|`Assemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 식별해야 하는 전체 경로 및 종속성에 대한 항목을 지정합니다. 이러한 항목은 “System”과 같은 단순한 이름이나 “System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089”와 같은 강력한 이름을 포함할 수 있습니다.<br /><br /> 이 매개 변수에 전달된 항목에는 원할 경우 다음의 항목 메타데이터를 포함할 수 있습니다.<br /><br /> -   `Private`: `Boolean` 값입니다. `true`면, 항목이 로컬로 복사됩니다. 기본값은 `true`입니다.<br />-   `HintPath`: `String` 값입니다. 참조로 사용할 경로 및 파일 이름을 지정합니다. {HintPathFromItem}이 `SearchPaths` 매개 변수에 지정되면 이 메타데이터가 사용됩니다. 기본값은 빈 문자열입니다.<br />-   `SpecificVersion`: `Boolean` 값입니다. `true`일 경우, `Include` 특성에 지정된 정확한 이름이 일치해야 합니다. `false`일 경우, 동일한 단순 이름의 모든 어셈블리가 작동합니다. `SpecificVersion` 을 지정하지 않으면 작업에서 해당 항목의 `Include` 특성에 있는 값이 검사됩니다. 특성은 단순 이름일 경우 `SpecificVersion` 는 `false`여야 합니다. 강력한 이름일 경우에는 `SpecificVersion` 는 `true`여야 합니다.<br />     참조 항목 유형과 함께 사용하는 경우는 `Include` 특성이 확인할 어셈블리의 전체 Fusion 이름이어야 합니다. 어셈블리는 Fusion이 `Include` 특성과 정확하게 일치하는 경우에만 확인됩니다.<br />     프로젝트가 .NET Framework 버전을 대상으로 하고 더 높은 .NET Framework 버전에 대해 컴파일된 어셈블리를 참조하는 경우에는, 참조에 `SpecificVersion` 이 `true`여야 합니다.<br />     프로젝트가 프로필을 대상으로 하고 프로필에 없는 어셈블리를 참조하는 경우에는, 참조에 `SpecificVersion` 이 `true`여야 합니다.<br />-   `ExecutableExtension`: `String` 값입니다. 이 메타데이터가 있으면 확인된 어셈블리에 이 확장이 있어야 합니다. 없으면 검사된 각 디렉터리에 대해 *.dll*이 첫 번째로 고려되고 *.exe*가 그다음으로 고려됩니다.<br />-   `SubType`: `String` 값입니다. 빈 SubType 메타데이터가 있는 항목만 전체 어셈블리 경로로 확인됩니다. 비어 있지 않은 SubType 메타데이터를 사용하는 항목은 무시됩니다.<br />-   `AssemblyFolderKey`: `String` 값입니다. 이 메타데이터는 레거시용으로 지원됩니다. **hklm\\\<VendorFolder>** 와 같이, `Assemblies`에서 어셈블리 참조를 확인하는 데 사용해야 하는 사용자 정의 레지스트리 키를 지정합니다.|
|`AssemblyFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 종속성을 찾을 정규화된 어셈블리의 목록을 지정합니다.<br /><br /> 이 매개 변수에 전달된 항목에는 원할 경우 다음의 항목 메타데이터를 포함할 수 있습니다.<br /><br /> -   `Private`: 선택적 `Boolean` 값입니다. true면, 항목이 로컬로 복사됩니다.<br />-   `FusionName`: 선택적 `String` 메타데이터입니다. 이 항목에 대한 단순 또는 강력한 이름을 지정합니다. 이 특성이 있는 경우 이름을 알기 위해 어셈블리 파일을 열 필요가 없으므로 시간을 절약할 수 있습니다.|
|`AutoUnify`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수는 일반 *App.Config* 파일을 가질 수 없는 DLL과 같은 어셈블리 빌드에 사용됩니다.<br /><br /> `true`이면 자동으로 결과 종속성 그래프가 AppConfigFile 매개 변수에 전달된 *App.Config* 파일이 있었던 것처럼 처리됩니다. 이 가상 *App.Config* 파일에는 가장 높은 버전 어셈블리가 선택되도록 충돌하는 각 어셈블리 집합에 대한 bindingRedirect 항목이 있습니다. 모든 충돌은 해결될 것이므로 이에 대한 결과는 충돌하는 어셈블리에 대한 경고가 없으리라는 것입니다.<br /><br /> `true`면, 각각의 고유한 재매핑에 대해 이전 버전과 새 버전을 보여 주는 높은 우선 순위 주석이 표시되며, 해당 `AutoUnify` 는 `true`입니다.<br /><br /> `true`이면, AppConfigFile 매개 변수는 비어 있어야 합니다.<br /><br /> `false`이면, 어셈블리 버전 재매핑은 자동으로 발생하지 않습니다. 두 버전의 어셈블리가 있는 경우에는 경고가 발생합니다.<br /><br /> `false`이면, 동일한 어셈블리의 서로 다른 버전 간 충돌 시 각각의 고유한 충돌에 대해 높은 우선 순위 주석이 표시됩니다. 이 주석 다음에 단일 경고가 표시됩니다. 이 경고에는 고유한 오류 코드와 "참조와 종속 어셈블리의 서로 다른 버전 사이에 충돌이 발생했습니다"라는 텍스트가 포함되어 있습니다.<br /><br /> 기본값은 `false`입니다.|
|`CandidateAssemblyFiles`|선택적 `String[]` 매개 변수입니다.<br /><br /> 검색 및 확인 프로세스에 사용할 어셈블리 목록을 지정합니다. 이 매개 변수에 전달된 값은 절대 파일 이름이나 프로젝트에 상대적인 파일 이름이어야 합니다.<br /><br /> 이 목록에 있는 어셈블리는 `SearchPaths` 매개 변수에 고려해야 할 경로 중 하나로서 {CandidateAssemblyFiles}가 포함되어 있는 것으로 간주됩니다.|
|`CopyLocalDependenciesWhenParentReferenceInGac`|선택적 <xref:System.Boolean> 매개 변수입니다.<br /><br /> true일 경우 종속성을 로컬로 복사해야 할지 결정하기 위해 확인해야 할 사항 중 하나는 프로젝트 파일에 있는 부모 참조에 개인 메타데이터가 설정되어 있는지 확인하는 것입니다. 설정되어 있다면 개인 값이 종속성으로 사용됩니다.<br /><br /> 메타데이터를 설정되어 있지 않으면 종속성은 부모 참조와 동일한 검사를 통과합니다. 이러한 검사 중 하나는 참조가 GAC에 있는지 확인하는 것입니다. 참조가 GAC에 있으면 참조가 대상 컴퓨터의 GAC에 있는 것으로 간주되므로 로컬로 복사되지 않습니다. 이것은 특정 참조에만 적용되고 해당 종속성에는 적용되지 않습니다.<br /><br /> 예를 들어 GAC에 있는 프로젝트 파일에 있는 참조는 로컬로 복사되지 않지만, 해당 종속성은 GAC에 없으므로 로컬로 복사됩니다.<br /><br /> false일 경우, 프로젝트 파일 참조는 이 참조가 GAC에 있는지 알기 위해 확인되며 적절하게 로컬로 복사됩니다.<br /><br /> 종속성은 GAC에 있는지 알기 위해 확인되고, 프로젝트 파일의 부모 참조가 GAC에 있는지 알기 위해서도 확인됩니다.<br /><br /> 프로젝트 파일의 부모 참조가 GAC에 있으면 종속성은 로컬로 복사되지 않습니다.<br /><br /> 이 매개 변수가 true든 false든 상관없이, 여러 부모 참조가 있고 이 중 어느 것도 GAC에 없다면, 이것들은 모두 로컬로 복사됩니다.|
|`CopyLocalFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 값이 `ResolvedFiles`인 `ResolvedDependencyFiles`인 `RelatedFiles`인 `SatelliteFiles`, `ScatterFiles` , `CopyLocal` , `true`여야 합니다.|
|`FilesWritten`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 디스크에 기록된 항목을 포함합니다.|
|`FindDependencies`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`일 경우, 종속성이 검색됩니다. 그렇지 않은 경우에는 기본 참조만 검색됩니다. 기본값은 `true`입니다.|
|`FindRelatedFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`일 경우 *.pdb* 파일 및 *.xml* 파일과 같은 관련 파일이 검색됩니다. 기본값은 `true`입니다.|
|`FindSatellites`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`일 경우 위성 어셈블리가 검색됩니다. 기본값은 `true.`|
|`FindSerializationAssemblies`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`일 경우, 작업에서 serialization 어셈블리를 검색합니다. 기본값은 `true`입니다.|
|`FullFrameworkAssemblyTables`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 재배포 목록을 특정 프레임워크 디렉터리와 연결하기 위해 "FrameworkDirectory" 메타데이터가 있는 항목을 지정합니다. 연결하지 못하면 오류가 기록됩니다. FrameworkDirectory가 설정되지 않은 경우 RAR(Resolve Assembly Reference) 논리에서는 대상 프레임워크 디렉터리를 사용합니다.|
|`FullFrameworkFolders`|선택적 <xref:System.String?displayProperty=fullName>`[]` 매개 변수입니다.<br /><br /> RedistList 디렉터리를 포함하는 폴더를 지정합니다. 이 디렉터리는 *%programfiles%\reference assemblies\microsoft\framework\v4.0*과 같이, 지정된 클라이언트 프로필에 대한 전체 프레임워크를 나타냅니다.|
|`FullTargetFrameworkSubsetNames`|선택적 `String[]` 매개 변수입니다.<br /><br /> 대상 프레임워크 하위 집합 이름 목록을 포함합니다. 목록에 있는 하위 집합 이름이 `TargetFrameworkSubset` Name 속성에 있는 것과 일치하는 경우, 시스템에서는 빌드 시 해당 특정 대상 프레임워크 하위 집합을 제외합니다.|
|`IgnoreDefaultInstalledAssemblyTables`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업에서는 `TargetFrameworkDirectories` 아래의 *\RedistList* 디렉터리에 있는 설치된 추가 어셈블리 표(또는 “재배포 목록”)를 검색하여 사용합니다. 기본값은 `false.`|
|`IgnoreDefaultInstalledAssemblySubsetTables`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`라면, 작업에서는 `TargetFrameworkDirectories` 아래의 *\SubsetList* 디렉터리에 있는 설치된 추가 어셈블리 하위 집합 표(또는 “하위 집합 목록”)를 검색하여 사용합니다. 기본값은 `false.`|
|`InstalledAssemblySubsetTables`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 대상 하위 집합에 있는 것으로 예상되는 어셈블리를 지정하는 XML 파일의 목록을 포함합니다.<br /><br /> 옵션으로서, 이 목록의 항목이 `InstalledAssemblySubsetTable`을 특정 프레임워크 디렉터리와 연결할 "FrameworkDirectory" 메타데이터를 지정할 수<br /><br /> 있습니다.<br /><br /> `TargetFrameworkDirectories` 요소가 하나만 있다면, 이 목록에 있는 항목 중 "FrameworkDirectory" 메타데이터가 없는 모든 항목은 `TargetFrameworkDirectories`에 전달되는 고유한 값으로 설정된 것처럼 처리됩니다.|
|`InstalledAssemblyTables`|선택적 `String` 매개 변수입니다.<br /><br /> 대상 컴퓨터에 설치되어 있는 것으로 예상되는 어셈블리를 지정하는 XML 파일의 목록을 포함합니다.<br /><br /> `InstalledAssemblyTables` 가 설정되어 있으면, 목록에 있는 어셈블리 중 이전 버전은 XML에 나열된 최신 버전에 병합됩니다. 또한 InGAC='true'라는 설정이 있는 어셈블리는 필수 조건으로 간주되며, 명시적으로 재정의하지 않으면 CopyLocal='false'로 설정됩니다.<br /><br /> 옵션으로서, 이 목록의 항목이 `InstalledAssemblyTable` 을 특정 프레임워크 디렉터리와 연결할 "FrameworkDirectory" 메타데이터를 지정할 수 있습니다.  그러나, 재배포 이름이 다음과 같이 시작하지 않으면 이 설정은 무시됩니다.<br /><br /> "Microsoft-Windows-CLRCoreComp"<br /><br /> `TargetFrameworkDirectories` 요소가 하나만 있다면, 이 목록에 있는 항목 중 "FrameworkDirectory" 메타데이터가 없는 모든 항목은<br /><br /> `TargetFrameworkDirectories`에 전달되는 고유한 값으로 설정된 것처럼 처리됩니다.|
|`LatestTargetFrameworkDirectories`|선택적 `String[]` 매개 변수입니다.<br /><br /> 컴퓨터에서 대상으로 지정할 수 있는 최신 프레임워크에 대한 재배포 목록이 들어 있는 디렉터리의 목록을 지정합니다. 설정하지 않는 경우, 지정된 대상 프레임워크 식별자에 대한 컴퓨터에 설치된 최상위 프레임워크가 사용됩니다.|
|`ProfileName`|선택적 `String` 매개 변수입니다.<br /><br /> - 대상으로 지정할 프레임워크 프로필의 이름을 지정합니다. 예를 들어, Client, Web 또는 Network가 있습니다.|
|`RelatedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> .XML 및 *.pdb* 파일과 같이 참조와 동일한 기본 이름을 가진 관련된 파일을 포함합니다.<br /><br /> 이 매개 변수에 나열된 파일에는 원할 경우 다음의 항목 메타데이터를 포함할 수 있습니다.<br /><br /> -   `Primary`: `Boolean` 값입니다. `true`일 경우, 파일 항목이 `Assemblies` 매개 변수입니다. 기본값은 `false`여야 합니다.<br />-   `CopyLocal`: `Boolean` 값입니다. 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다.|
|`ResolvedDependencyFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 종속성에 대한 *n*번째 순서 경로를 포함합니다. 이 매개 변수는 `ResolvedFiles` 매개 변수에 들어 있는 첫 번째 순서 기본 참조를 포함하지 않습니다.<br /><br /> 이 매개 변수에 있는 항목에는 원할 경우 다음의 항목 메타데이터를 포함합니다.<br /><br /> -   `CopyLocal`: `Boolean` 값입니다. 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다.<br />-   `FusionName`: `String` 값입니다. 이 종속성의 이름을 지정합니다.<br />-   `ResolvedFrom`: `String` 값입니다. 이 파일을 확인한 리터럴 검색 경로를 지정합니다.|
|`ResolvedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 전체 경로로 확인된 모든 기본 참조의 목록을 포함합니다.<br /><br /> 이 매개 변수에 있는 항목에는 원할 경우 다음의 항목 메타데이터를 포함합니다.<br /><br /> -   `CopyLocal`: `Boolean` 값입니다. 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다.<br />-   `FusionName`: `String` 값입니다. 이 종속성의 이름을 지정합니다.<br />-   `ResolvedFrom`: `String` 값입니다. 이 파일을 확인한 리터럴 검색 경로를 지정합니다.|
|`SatelliteFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 찾은 위성 파일을 지정합니다. 이 항목을 존재하도록 한 참조 또는 종속성이 CopyLocal=true일 경우 이것은 CopyLocal=true입니다.<br /><br /> 이 매개 변수에 있는 항목에는 원할 경우 다음의 항목 메타데이터를 포함합니다.<br /><br /> -   `CopyLocal`: `Boolean` 값입니다. 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다. 이 값은 이 항목을 존재하도록 한 참조 또는 종속성에 `true` 라는 `CopyLocal` 값이 있을 경우 `true`여야 합니다.<br />-   `DestinationSubDirectory`: `String` 값입니다. 이 항목을 복사할 상대적인 대상 디렉터리를 지정합니다.|
|`ScatterFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 지정된 어셈블리 중 하나와 연결된 분산 파일을 포함합니다.<br /><br /> 이 매개 변수에 있는 항목에는 원할 경우 다음의 항목 메타데이터를 포함합니다.<br /><br /> -   `CopyLocal`: `Boolean` 값입니다. 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다.|
|`SearchPaths`|필수 `String[]` 매개 변수입니다.<br /><br /> 디스크에서 어셈블리를 나타내는 파일을 찾기 위해 검색할 디렉터리 또는 특별한 위치를 지정합니다. 검색 경로가 나열된 순서가 중요합니다. 각 어셈블리에 대한 경로 목록은 왼쪽에서 오른쪽으로 검색됩니다. 어셈블리를 나타내는 파일을 찾으면 검색이 중지되고 다음 어셈블리에 대한 검색이 시작됩니다.<br /><br /> 이 매개 변수는 아래 목록의 디렉터리 경로 또는 특수 리터럴 값이 포함될 수 있는 세미콜론으로 구분된 값 목록을 사용합니다.<br /><br /> -   `{HintPathFromItem}`: 작업에서 기본 항목의 `HintPath` 메타데이터를 검사하도록 지정합니다.<br />-   `{CandidateAssemblyFiles}`: 작업에서 `CandidateAssemblyFiles` 매개 변수를 통해 전달된 파일을 검사하도록 지정합니다.<br />-   `{Registry:` \<AssemblyFoldersBase>, \<RuntimeVersion>, \<AssemblyFoldersSuffix>`}`: 작업이 레지스트리에 지정된 추가 폴더에서 검색하도록 지정합니다. \<AssemblyFoldersBase>, \<RuntimeVersion> 및 \<AssemblyFoldersSuffix>은 검색할 레지스트리 위치의 특정 값으로 대체되어야 합니다. 공통 대상의 기본 사양은 {Registry:$(FrameworkRegistryBase), $(TargetFrameworkVersion), $(AssemblyFoldersSuffix), $(AssemblyFoldersExConditions)}입니다.<br />-   `{AssemblyFolders}`: 작업에서 Visual Studio.NET 2003 레지스트리의 어셈블리 찾기 체계를 사용하도록 지정합니다.<br />-   `{GAC}`: 작업이 GAC(전역 어셈블리 캐시)에서 검색하도록 지정합니다.<br />-   `{RawFileName}`: 작업에서 항목의 `Include` 값을 정확한 경로 및 파일 이름으로 간주하도록 지정합니다.|
|`SerializationAssemblyFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 찾은 모든 XML Serialization 어셈블리를 포함합니다. 이 항목을 존재하도록 한 참조 또는 종속성이 CopyLocal=true일 경우에만 이 항목이 CopyLocal=true로 표시됩니다.<br /><br /> `Boolean` 메타데이터 CopyLocal은 지정된 참조를 출력 디렉터리로 복사해야 하는지 여부를 나타냅니다.|
|`Silent`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`일 경우 메시지가 기록되지 않습니다. 기본값은 `false`입니다.|
|`StateFile`|선택적 `String` 매개 변수입니다.<br /><br /> 이 작업에 대한 중간 빌드 상태를 저장할 위치를 나타내는 파일 이름을 지정합니다.|
|`SuggestedRedirects`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> `AutoUnify` 매개 변수의 값과 관계없이 충돌하는 모든 고유 어셈블리 ID에 대해 하나의 항목을 포함합니다. 여기에는 애플리케이션 구성 파일에 적합한 bindingRedirect 항목이 없는 것으로 나타난 모든 culture 및 PKT가 포함됩니다.<br /><br /> 각 항목에는 다음 정보가 들어 있습니다.<br /><br /> -   `Include` 특성: 버전 필드 값이 0.0.0.0인 어셈블리 제품군의 전체 이름을 포함합니다.<br />-   `MaxVersion` 항목 메타데이터: 최대 버전 번호가 포함됩니다.|
|`TargetedRuntimeVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 2\.0.57027 또는 v2.0.57027과 같이 런타임 버전을 대상으로 지정합니다.|
|`TargetFrameworkDirectories`|선택적 `String[]` 매개 변수입니다.<br /><br /> 대상 프레임워크 디렉터리의 경로를 지정합니다. 이 매개 변수는 결과 항목에 대한 CopyLocal 상태를 결정하는 데 필요합니다.<br /><br /> 이 매개 변수를 지정하지 않는 경우, 결과 항목의 소스 항목에 `true`라는 `Private` 메타데이터 값이 명시적으로 포함되지 않는 한 `true`라는 CopyLocal 값이 있는 결과 항목은 존재하지 않게 됩니다.|
|`TargetFrameworkMoniker`|선택적 `String` 매개 변수입니다.<br /><br /> 있을 경우 TargetFrameworkMoniker가 모니터링합니다. 로깅에 사용됩니다.|
|`TargetFrameworkMonikerDisplayName`|선택적 `String` 매개 변수입니다.<br /><br /> 있을 경우 모니터링하는 TargetFrameworkMoniker의 표시 이름입니다. 로깅에 사용됩니다.|
|`TargetFrameworkSubsets`|선택적 `String[]` 매개 변수입니다.<br /><br /> 대상 프레임워크 디렉터리에서 검색할 대상 프레임워크 하위 집합 이름의 목록을 포함합니다.|
|`TargetFrameworkVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 프로젝트 대상 프레임워크 버전입니다. 기본값은 비어 있으며 이것은 대상 프레임워크를 기반으로 하는 참조에 대한 필터링이 없음을 의미합니다.|
|`TargetProcessorArchitecture`|선택적 `String` 매개 변수입니다.<br /><br /> 기본 대상 프로세서 아키텍처입니다. GAC(전역 어셈블리 캐시) 참조를 확인하는 데 사용됩니다.<br /><br /> 이 매개 변수는 `x86`, `IA64` 또는 `AMD64` 값을 가질 수 있습니다.<br /><br /> 이 매개 변수가 없는 경우, 작업에서는 현재 실행 중인 프로세스의 아키텍처와 일치하는 어셈블리를 먼저 고려합니다. 어셈블리가 없는 경우 작업에서는 `ProcessorArchitecture` 의 `MSIL` 값이 있거나 `ProcessorArchitecture` 값이 없는 GAC에 있는 어셈블리를 고려합니다.|

## <a name="warnings"></a>경고

 다음 경고가 기록됩니다.

- `ResolveAssemblyReference.TurnOnAutoGenerateBindingRedirects`

- `ResolveAssemblyReference.SuggestedRedirects`

- `ResolveAssemblyReference.FoundConflicts`

- `ResolveAssemblyReference.AssemblyFoldersExSearchLocations`

- `ResolveAssemblyReference.UnifiedPrimaryReference`

- `ResolveAssemblyReference.PrimaryReference`

- `ResolveAssemblyReference.UnifiedDependency`

- `ResolveAssemblyReference.UnificationByAutoUnify`

- `ResolveAssemblyReference.UnificationByAppConfig`

- `ResolveAssemblyReference.UnificationByFrameworkRetarget`

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
