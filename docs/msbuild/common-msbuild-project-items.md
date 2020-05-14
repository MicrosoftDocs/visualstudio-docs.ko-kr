---
title: 일반적인 MSBuild 프로젝트 항목 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7725108fd71f4292a8d3fa4dfe68ca29d3dcd90
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634450"
---
# <a name="common-msbuild-project-items"></a>일반적인 MSBuild 프로젝트 항목

MSBuild에서 항목은 하나 이상의 파일에 대한 명명된 참조입니다. 항목에는 파일 이름, 경로 및 버전 번호와 같은 메타데이터가 포함됩니다. Visual Studio의 모든 프로젝트 형식에는 공통된 여러 항목이 있습니다. 이러한 항목은 *Microsoft.Build.CommonTypes.xsd* 파일에 정의되어 있습니다.
## <a name="common-items"></a>공통 항목

 다음은 모든 공통 프로젝트 항목의 목록입니다.
다음은 모든 공통 프로젝트 항목의 목록입니다.

### <a name="reference"></a>참고

 프로젝트의 어셈블리(관리) 참조를 나타냅니다.

|항목 메타데이터 이름|설명|
|---------------|-----------------|
|HintPath|선택적 문자열입니다. 어셈블리의 상대 또는 절대 경로입니다.|
|이름|선택적 문자열입니다. 어셈블리의 표시 이름(예: "System.Windows.Forms")입니다.|
|FusionName|선택적 문자열입니다. 항목에 단순 또는 강력한 Fusion 이름을 지정합니다.<br /><br /> 이 특성이 있는 경우 Fusion 이름을 알기 위해 어셈블리 파일을 열 필요가 없으므로 시간을 절약할 수 있습니다.|
|SpecificVersion|선택적 부울입니다. Fusion 이름의 버전만 참조할지 여부를 지정합니다.|
|별칭|선택적 문자열입니다. 참조에 대한 별칭입니다.|
|Private|선택적 부울입니다. 참조를 출력 폴더에 복사할지 여부를 지정합니다. 이 특성은 Visual Studio IDE에 있는 참조의 **로컬 복사** 속성과 일치합니다.|

### <a name="comreference"></a>COMReference

 프로젝트의 COM(비관리) 구성 요소 참조를 나타냅니다. 이 항목은 .NET 프로젝트에만 적용됩니다.

|항목 메타데이터 이름|설명|
|---------------|-----------------|
|이름|선택적 문자열입니다. 구성 요소의 표시 이름입니다.|
|GUID|필수 문자열입니다. 구성 요소의 GUID로, {12345678-1234-1234-1234-1234567891234} 형식을 갖습니다.|
|VersionMajor|필수 문자열입니다. 구성 요소 버전 번호의 주 버전 부분입니다. 예를들어 전체 버전 번호가 "5.46"이면 "5"입니다.|
|VersionMinor|필수 문자열입니다. 구성 요소 버전 번호의 부 버전 부분입니다. 예를들어 전체 버전 번호가 "5.46"이면 "46"입니다.|
|LCID|선택적 문자열입니다. 구성 요소의 LocaleID입니다.|
|WrapperTool|선택적 문자열입니다. 구성 요소에 사용되는 래퍼 도구의 이름(예: "tlbimp")입니다.|
|Isolated|선택적 부울입니다. 등록이 필요 없는 구성 요소인지 여부를 지정합니다.|

### <a name="comfilereference"></a>COMFileReference

 [ResolveComReference](resolvecomreference-task.md) 대상의 `TypeLibFiles` 매개 변수에 전달되는 형식 라이브러리 목록을 나타냅니다. 이 항목은 .NET 프로젝트에만 적용됩니다.

|항목 메타데이터 이름|설명|
|---------------|-----------------|
|WrapperTool|선택적 문자열입니다. 구성 요소에 사용되는 래퍼 도구의 이름(예: "tlbimp")입니다.|

### <a name="nativereference"></a>NativeReference

 네이티브 매니페스트 파일 또는 이러한 파일에 대한 참조를 나타냅니다.

|항목 메타데이터 이름|설명|
|---------------|-----------------|
|이름|필수 문자열입니다. 매니페스트 파일의 기본 이름입니다.|
|HintPath|필수 문자열입니다. 매니페스트 파일의 상대 경로입니다.|

### <a name="projectreference"></a>ProjectReference

 다른 프로젝트에 대한 참조를 나타냅니다.

|항목 메타데이터 이름|설명|
|---------------|-----------------|
|이름|선택적 문자열입니다. 참조의 표시 이름입니다.|
|프로젝트|선택적 문자열입니다. 참조의 GUID로, {12345678-1234-1234-1234-1234567891234} 형식을 갖습니다.|
|패키지|선택적 문자열입니다. 참조되는 프로젝트 파일의 경로입니다.|
|ReferenceOutputAssembly|선택적 부울입니다. `false`로 설정하면 참조된 프로젝트의 출력이 이 프로젝트의 [참조](#reference)로 포함되지 않지만, 이 프로젝트 앞에 다른 프로젝트가 빌드되도록 합니다. 기본값은 `true`입니다.|

### <a name="compile"></a>Compile

 컴파일러에 대한 소스 파일을 나타냅니다.

| 항목 메타데이터 이름 | 설명 |
|-----------------------| - |
| DependentUpon | 선택적 문자열입니다. 올바르게 컴파일하기 위해 이 파일이 의존하는 파일을 지정합니다. |
| AutoGen | 선택적 부울입니다. Visual Studio IDE(통합 개발 환경)에서 프로젝트를 위해 해당 파일이 생성되었는지 여부를 나타냅니다. |
| 링크 | 선택적 문자열입니다. 파일이 물리적으로 프로젝트 파일의 영향 범위 밖에 있을 때 표시할 표기 경로입니다. |
| 표시 | 선택적 부울입니다. Visual Studio의 **솔루션 탐색기**에 파일을 표시할지 여부를 나타냅니다. |
| CopyToOutputDirectory | 선택적 문자열입니다. 출력 디렉터리에 파일을 복사할지 여부를 결정합니다. 값:<br /><br /> 1.  Never<br />2.  항상<br />3.  PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

 생성된 어셈블리에 포함될 리소스를 나타냅니다.

| 항목 메타데이터 이름 | 설명 |
|-----------------------| - |
| DependentUpon | 선택적 문자열입니다. 올바르게 컴파일하기 위해 이 파일이 종속되는 파일을 지정합니다. |
| 생성기 | 필수 문자열입니다. 이 항목에서 실행되는 파일 생성기의 이름입니다. |
| LastGenOutput | 필수 문자열입니다. 이 항목에서 실행된 모든 파일 생성기가 만든 파일의 이름입니다. |
| CustomToolNamespace | 필수 문자열입니다. 이 항목에서 실행되는 모든 파일 생성기가 코드를 만들어야 하는 네임스페이스입니다. |
| 링크 | 선택적 문자열입니다. 파일이 물리적으로 프로젝트의 영향 범위 밖에 있을 때 이 표기 경로가 표시됩니다. |
| 표시 | 선택적 부울입니다. Visual Studio의 **솔루션 탐색기**에 파일을 표시할지 여부를 나타냅니다. |
| CopyToOutputDirectory | 선택적 문자열입니다. 출력 디렉터리에 파일을 복사할지 여부를 결정합니다. 값:<br /><br /> 1.  Never<br />2.  항상<br />3.  PreserveNewest |
| LogicalName | 필수 문자열입니다. 포함된 리소스의 논리적 이름입니다. |

### <a name="content"></a>콘텐츠

 프로젝트로 컴파일되지 않지만 프로젝트에 포함되거나 함께 게시될 수 있는 파일을 나타냅니다.

| 항목 메타데이터 이름 | 설명 |
|-----------------------| - |
| DependentUpon | 선택적 문자열입니다. 올바르게 컴파일하기 위해 이 파일이 의존하는 파일을 지정합니다. |
| 생성기 | 필수 문자열입니다. 이 항목에서 실행되는 파일 생성기의 이름입니다. |
| LastGenOutput | 필수 문자열입니다. 이 항목에서 실행된 모든 파일 생성기가 만든 파일의 이름입니다. |
| CustomToolNamespace | 필수 문자열입니다. 이 항목에서 실행되는 모든 파일 생성기가 코드를 만들어야 하는 네임스페이스입니다. |
| 링크 | 선택적 문자열입니다. 파일이 물리적으로 프로젝트의 영향 범위 밖에 있을 때 표시될 표기 경로입니다. |
| PublishState | 필수 문자열입니다. 콘텐츠의 게시 상태로 다음 중 하나입니다.<br /><br /> -   기본값<br />-   포함됨<br />-   제외됨<br />-   DataFile<br />-   필수 조건 |
| IsAssembly | 선택적 부울입니다. 파일이 어셈블리인지 여부를 지정합니다. |
| 표시 | 선택적 부울입니다. Visual Studio의 **솔루션 탐색기**에 파일을 표시할지 여부를 나타냅니다. |
| CopyToOutputDirectory | 선택적 문자열입니다. 출력 디렉터리에 파일을 복사할지 여부를 결정합니다. 값:<br /><br /> 1.  Never<br />2.  항상<br />3.  PreserveNewest |

### <a name="none"></a>없음

 빌드 프로세스에서 역할이 없는 파일을 나타냅니다.

| 항목 메타데이터 이름 | 설명 |
|-----------------------| - |
| DependentUpon | 선택적 문자열입니다. 올바르게 컴파일하기 위해 이 파일이 의존하는 파일을 지정합니다. |
| 생성기 | 필수 문자열입니다. 이 항목에서 실행되는 파일 생성기의 이름입니다. |
| LastGenOutput | 필수 문자열입니다. 이 항목에서 실행된 모든 파일 생성기가 만든 파일의 이름입니다. |
| CustomToolNamespace | 필수 문자열입니다. 이 항목에서 실행되는 모든 파일 생성기가 코드를 만들어야 하는 네임스페이스입니다. |
| 링크 | 선택적 문자열입니다. 파일이 물리적으로 프로젝트의 영향 범위 밖에 있을 때 표시될 표기 경로입니다. |
| 표시 | 선택적 부울입니다. Visual Studio의 **솔루션 탐색기**에 파일을 표시할지 여부를 나타냅니다. |
| CopyToOutputDirectory | 선택적 문자열입니다. 출력 디렉터리에 파일을 복사할지 여부를 결정합니다. 값:<br /><br /> 1.  Never<br />2.  항상<br />3.  PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

 `[AssemblyMetadata(key, value)]`로 생성될 어셈블리 특성을 나타냅니다.

| 항목 메타데이터 이름 | 설명 |
|-----------------------| - |
| 포함 | `AssemblyMetadataAttribute` 특성 생성자의 첫 번째 매개 변수(키)가 됩니다. |
| 값 | 필수 문자열입니다. `AssemblyMetadataAttribute` 특성 생성자의 두 번째 매개 변수(값)가 됩니다. |

> [!NOTE]
> .NET Core SDK를 사용하는 프로젝트에만 적용됩니다.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

 빌드에 대한 기본 애플리케이션 매니페스트를 나타내며 ClickOnce 배포 보안 정보를 포함합니다.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

 가져올 FxCop 프로젝트를 나타냅니다.

### <a name="import"></a>가져오기

 Visual Basic 컴파일러가 네임스페이스를 가져올 어셈블리를 나타냅니다.

## <a name="see-also"></a>참조

- [일반적인 MSBuild 프로젝트 속성](../msbuild/common-msbuild-project-properties.md)
