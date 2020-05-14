---
title: GenerateDeploymentManifest 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca55f3eeb9b3119b27e67dcb0255f8386c521af6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634073"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest 작업

ClickOnce 배포 매니페스트를 생성합니다. ClickOnce 배포 매니페스트는 배포의 고유한 ID를 정의하고, 설치 또는 온라인 모드와 같은 배포 특성을 식별하고, 애플리케이션 업데이트 설정 및 업데이트 위치를 지정하고, 해당 ClickOnce 애플리케이션 매니페스트를 지정하여 애플리케이션의 배포를 설명합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `GenerateDeploymentManifest` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|--------------------------| - |
| `AssemblyName` | 선택적 `String` 매개 변수입니다.<br /><br /> 생성된 매니페스트에 대한 어셈블리 ID의 `Name` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 이름은 `EntryPoint` 또는 `InputManifest` 매개 변수에서 유추됩니다. 이름을 유추할 수 없으면 작업에서 오류가 throw됩니다. |
| `AssemblyVersion` | 선택적 `String` 매개 변수입니다.<br /><br /> 생성된 매니페스트에 대한 어셈블리 ID의 `Version` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 작업은 "1.0.0.0" 값을 사용합니다. |
| `CreateDesktopShortcut` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> true이면 ClickOnce 애플리케이션 설치 동안 아이콘이 바탕 화면에 만들어집니다. |
| `DeploymentUrl` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션에 대한 업데이트 위치를 지정합니다. 이 매개 변수를 지정하지 않으면 애플리케이션에 대한 업데이트 위치가 정의되지 않습니다. 그러나 `UpdateEnabled` 매개 변수가 `true`이면 업데이트 위치를 지정해야 합니다. 지정된 값은 정규화된 URL 또는 UNC 경로여야 합니다. |
| `Description` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션에 대한 선택적 설명을 지정합니다. |
| `DisallowUrlActivation` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 애플리케이션이 URL을 통해 열릴 때 자동으로 실행되어야 하는지 여부를 지정합니다. 이 매개 변수가 `true`이면 애플리케이션을 **시작** 메뉴에서만 시작할 수 있습니다. 이 매개 변수의 기본값은 `false`입니다. 이 입력은 `Install` 매개 변수 값이 `true`일 때만 적용됩니다. |
| `EntryPoint` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 생성된 매니페스트 어셈블리에 대한 진입점을 나타냅니다. ClickOnce 배포 매니페스트의 경우 이 입력은 ClickOnce 애플리케이션 매니페스트를 지정합니다.<br /><br />`EntryPoint` 작업 매개 변수를 지정하지 않으면 `<customHostSpecified>` 태그는 `<entryPoint>` 태그의 자식으로 삽입됩니다. 예:<br /><br /> `<entryPoint xmlns="urn:schemas-microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> 다음 단계를 사용하여 애플리케이션 매니페스트에 DLL 종속성을 추가할 수 있습니다.<br /><br /> 1.  <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>를 호출하여 어셈블리 참조를 확인합니다.<br />2.  이전 작업의 출력 및 어셈블리 자체를 <xref:Microsoft.Build.Tasks.ResolveManifestFiles>에 전달합니다.<br />3.  `Dependencies` 매개 변수를 사용하여 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>에 종속성을 전달합니다. |
| `ErrorReportUrl` | 선택적 <xref:System.String?displayProperty=fullName> 매개 변수입니다.<br /><br /> ClickOnce 설치 중에 대화 상자에 표시되는 웹 페이지의 URL을 지정합니다. |
| `InputManifest` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 매니페스트 생성기에 대한 기본으로 사용되는 입력 XML 문서를 나타냅니다. 이를 통해 사용자 지정 매니페스트 정의와 같은 구조화된 데이터가 출력 매니페스트에 반영될 수 있습니다. XML 문서의 루트 요소는 asmv1 네임스페이스의 어셈블리 노드여야 합니다. |
| `Install` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 애플리케이션이 설치된 애플리케이션인지 아니면 온라인 전용 애플리케이션인지 여부를 지정합니다. 이 매개 변수가 `true`이면 애플리케이션은 사용자의 **시작** 메뉴에 설치되며 **프로그램 추가/제거** 대화 상자를 사용하여 제거할 수 있습니다. 이 매개 변수가 `false`이면 애플리케이션을 웹 페이지에서 온라인으로 사용해야 합니다. 이 매개 변수의 기본값은 `true`입니다. |
| `MapFileExtensions` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> *.deploy* 파일 이름 확장명 매핑이 사용되는지 여부를 지정합니다. 이 매개 변수가 `true`이면 모든 프로그램 파일이 *.deploy* 파일 이름 확장명을 사용하여 게시됩니다. 이 옵션은 웹 서버 보안에서 ClickOnce 애플리케이션 배포를 사용하도록 설정하기 위해 차단을 해제해야 하는 파일 이름 확장명의 수를 제한하는 데 유용합니다. 이 매개 변수의 기본값은 `false`입니다. |
| `MaxTargetPath` | 선택적 `String` 매개 변수입니다.<br /><br /> ClickOnce 애플리케이션 배포에서 파일 경로의 최대 허용 길이를 지정합니다. 이 매개 변수를 지정하는 경우 애플리케이션에서 각 파일 경로의 길이가 이 제한에 대해 확인됩니다. 한도를 초과하는 항목에서는 빌드 경고가 발생합니다. 이 입력이 지정되지 않거나 0으로 지정된 경우 검사가 수행되지 않습니다. |
| `MinimumRequiredVersion` | 선택적 `String` 매개 변수입니다.<br /><br /> 사용자가 업데이트를 건너뛸 수 있는지 여부를 지정합니다. 사용자가 필요한 최소 버전보다 낮은 버전을 보유하고 있으면 업데이트를 건너뛸 수 있는 옵션이 제공되지 않습니다. 이 입력은 `Install` 매개 변수의 값이 `true`일 때만 적용됩니다. |
| `OutputManifest` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 생성된 출력 매니페스트 파일의 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 출력 파일의 이름이 생성된 매니페스트의 ID에서 유추됩니다. |
| `Platform` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 대상 플랫폼을 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> 기본값은 `AnyCPU`입니다. |
| `Product` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 이름이 생성된 매니페스트의 ID에서 유추됩니다. 이 이름은 **시작** 메뉴의 바로 가기 이름에 사용되고 **프로그램 추가/제거** 대화 상자에 표시되는 이름의 일부입니다. |
| `Publisher` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 게시자를 지정합니다. 이 매개 변수를 지정하지 않으면 이름이 등록된 사용자 또는 생성된 매니페스트의 ID에서 유추됩니다. 이 이름은 **시작** 메뉴의 폴더 이름에 사용되고 **프로그램 추가/제거** 대화 상자에 표시되는 이름의 일부입니다. |
| `SuiteNamel` | 선택적 `String` 매개 변수입니다.<br /><br /> ClickOnce 배포 후에 애플리케이션이 위치할 **시작** 메뉴의 폴더 이름을 지정합니다. |
| `SupportUrl` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션에 대한 **프로그램 추가/제거** 대화 상자에 표시되는 링크를 지정합니다. 지정된 값은 정규화된 URL 또는 UNC 경로여야 합니다. |
| `TargetCulture` | 선택적 `String` 매개 변수입니다.<br /><br /> 애플리케이션의 문화권을 식별하고 생성된 매니페스트에 대한 어셈블리 ID의 `Language` 필드를 지정합니다. 이 매개 변수를 지정하지 않으면 애플리케이션은 문화권이 고정되어 있다고 가정합니다. |
| `TrustUrlParameters` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> URL 쿼리 문자열 매개 변수를 애플리케이션에 사용할 수 있게 해야 할지 여부를 지정합니다. 이 매개 변수의 기본값은 해당 매개 변수를 애플리케이션에 사용할 수 없음을 나타내는 `false`입니다. |
| `UpdateEnabled` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 애플리케이션을 업데이트할 수 있는지 여부를 나타냅니다. 이 매개 변수의 기본값은 `false`입니다. 이 매개 변수는 `Install` 매개 변수의 값이 `true`일 때만 적용됩니다. |
| `UpdateInterval` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 애플리케이션에 대한 업데이트 간격을 지정합니다. 이 매개 변수의 기본값은 0입니다. 이 매개 변수는 `Install` 및 `UpdateEnabled` 매개 변수의 값이 모두 `true`일 때만 적용됩니다. |
| `UpdateMode` | 선택적 `String` 매개 변수입니다.<br /><br /> 업데이트를 애플리케이션이 시작되기 전에 포그라운드에서 확인해야 하는지 아니면 애플리케이션이 실행되는 동안 백그라운드에서 확인해야 하는지 여부를 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> 이 매개 변수의 기본값은 `Background`입니다. 이 매개 변수는 `Install` 및 `UpdateEnabled` 매개 변수의 값이 모두 `true`일 때만 적용됩니다. |
| `UpdateUnit` | 선택적 `String` 매개 변수입니다.<br /><br /> `UpdateInterval` 매개 변수의 단위를 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> 이 매개 변수는 `Install` 및 `UpdateEnabled` 매개 변수의 값이 모두 `true`일 때만 적용됩니다. |

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.GenerateManifestBase> 클래스의 매개 변수도 상속합니다. Task 클래스의 매개 변수 목록에 대해서는 [Task 기본 클래스](../msbuild/task-base-class.md)를 참조하세요.

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [GenerateApplicationManifest 작업](../msbuild/generateapplicationmanifest-task.md)
- [SignFile 작업](../msbuild/signfile-task.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
