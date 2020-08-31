---
title: MSBuild 15의 새로운 기능 | Microsoft Docs
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 733c3253245e293a6e52953bc93fc35a1281a616
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711679"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15의 새로운 기능

MSBuild는 현재 [.NET Core SDK](https://www.microsoft.com/net/download/core)의 일부로 제공되며 Windows, macOS 및 Linux에서 .NET Core 프로젝트를 빌드할 수 있습니다.

## <a name="changed-path"></a>변경된 경로

 MSBuild는 이제 각 Visual Studio 버전 아래의 폴더에 설치됩니다. 예: *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. 또한 다음 PowerShell 모듈을 사용하여 MSBuild를 찾을 수도 있습니다. [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild는 전역 어셈블리 캐시에 더 이상 설치되지 않습니다. MSBuild를 프로그래밍 방식으로 참조하려면 NuGet 패키지를 사용하세요. 자세한 내용은 [MSBuild 15.0에 대한 기존 애플리케이션 업데이트](../msbuild/updating-an-existing-application.md)를 참조하세요.

## <a name="changed-properties"></a>변경된 속성

 다음 MSBuild 속성은 새 버전 번호의 결과로 업데이트되었습니다.

- 이 도구 버전의 `MSBuildToolsVersion`은 15.0입니다. 어셈블리 버전은 15.1.0.0입니다.

- `MSBuildToolsPath`는 더 이상 고정된 위치를 포함하지 않습니다. 기본적으로 Visual Studio 설치 위치를 기준으로 *MSBuild\15.0\Bin* 폴더에 있지만 Visual Studio 설치 위치는 설치 시 변경할 수 있습니다.

- `ToolsVersion` 값은 더 이상 레지스트리에 설정되지 않습니다.

- `SDK35ToolsPath` 및 `SDK40ToolsPath` 속성은 이 버전의 Visual Studio(예: 4.X 도구의 10.0A)를 사용하여 패키지된 .NET Framework SDK를 가리킵니다.

## <a name="updates"></a>업데이트

- [Project 요소](../msbuild/project-element-msbuild.md)는 새 `SDK` 특성을 포함합니다. 이제 `Xmlns` 특성도 선택 사항입니다. `SDK` 특성에 대한 자세한 내용은 [방법: MSBuild 프로젝트 SDK 사용](../msbuild/how-to-use-project-sdk.md), [패키지, 메타패키지, 프레임워크](/dotnet/core/packages) 및 [.NET Core용 csproj 형식에 대한 추가 사항](/dotnet/core/tools/csproj)을 참조하세요.
- 대상 외부의 [Item 요소](../msbuild/item-element-msbuild.md)는 새 `Update` 특성을 포함합니다. 또한 `Remove` 특성 대한 제한 사항도 제거되었습니다.
- *Directory.Build.props*는 디렉터리에 있는 프로젝트에 대한 사용자 지정을 제공하는 사용자 지정 파일입니다. `ImportDirectoryBuildTargets` 속성을 **false**로 설정한 경우가 아니면 *Microsoft.Common.props*에서 이 파일을 자동으로 가져옵니다. *Directory.Build.targets*는 *Microsoft.Common.targets*를 통해 가져옵니다.
- 현재 특성 목록과 충돌하지 않는 이름을 가진 메타데이터를 특성으로 선택적으로 표시할 수 있습니다. 자세한 내용은 [Item 요소](../msbuild/item-element-msbuild.md)를 참조하세요.

## <a name="new-property-functions"></a>새 속성 함수

- `EnsureTrailingSlash`는 경로에 후행 슬래시(없는 경우)를 추가합니다.
- `NormalizePath`는 path 요소를 결합하고 출력 문자열에 현재 운영 체제에 대한 정확한 디렉터리 구분 문자가 있는지 확인합니다.
- `NormalizeDirectory`는 path 요소를 결합하고 후행 슬래시를 확인하며 출력 문자열에 현재 운영 체제에 대한 정확한 디렉터리 구분 문자가 있는지 확인합니다.
- `GetPathOfFileAbove`는 바로 앞에 오는 파일의 경로를 반환합니다. `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`를 호출하는 것과 기능적으로 동일합니다.

## <a name="see-also"></a>참고 항목

- [MSBuild](../msbuild/msbuild.md)
