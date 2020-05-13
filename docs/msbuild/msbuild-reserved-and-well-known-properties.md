---
title: MSBuild의 예약된 속성 및 잘 알려진 속성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633254"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild의 예약된 속성 및 잘 알려진 속성

MSBuild는 프로젝트 파일과 MSBuild 이진 파일에 대한 정보를 저장하는 미리 정의된 속성 집합을 제공합니다. 이러한 속성은 다른 MSBuild 속성과 동일한 방식으로 평가됩니다. 예를 들어, `MSBuildProjectFile` 속성을 사용하려면 `$(MSBuildProjectFile)`을 입력합니다.

 MSBuild에서는 다음 표에 있는 값을 사용하여 예약된 속성 및 잘 알려진 속성을 미리 정의할 수 있습니다. 예약된 속성은 재정의할 수 없지만 잘 알려진 속성은 동일하게 이름이 지정된 환경 속성, 전역 속성 또는 프로젝트 파일에 선언된 속성을 사용하여 재정의할 수 있습니다.

## <a name="reserved-and-well-known-properties"></a>예약된 속성 및 잘 알려진 속성

 다음 표에서는 MSBuild의 미리 정의된 속성에 대해 설명합니다.

| 속성 | 예약됨 또는 잘 알려짐 | 설명 |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | 예약됨 | 현재 사용 중인 MSBuild 이진 파일이 있는 폴더의 절대 경로(예: *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>* )입니다. 이 속성은 MSBuild 디렉터리에 있는 파일을 참조해야 할 경우에 유용합니다.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildExtensionsPath` | 잘 알려짐 | .NET Framework 4에서는 `MSBuildExtensionsPath`와 `MSBuildExtensionsPath32`의 기본값 사이에 차이가 없음을 정의했습니다. 이전 버전에서 `MSBUILDLEGACYEXTENSIONSPATH`의 기본값 동작을 사용으로 설정하려면 환경 변수 `MSBuildExtensionsPath`를 null이 아닌 값으로 설정하면 됩니다.<br /><br /> .NET Framework 3.5 이전에서는 `MSBuildExtensionsPath`의 기본값이 현재 프로세스의 비트에 따라 *\Program Files\\* 또는 *\Program Files (x86)* 폴더 아래 MSBuild 하위 폴더의 경로를 가리킵니다. 예를 들어, 64비트 컴퓨터에 32비트 프로세스인 경우 이 속성은 *\Program Files (x86)* 폴더를 가리킵니다. 64비트 컴퓨터에 64비트 프로세스인 경우 이 속성은 *\Program Files* 폴더를 가리킵니다.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요.<br /><br /> 이 위치는 사용자 지정 대상 파일을 넣는 데 유용합니다. 예를 들어, 대상 파일을 *\Program Files\MSBuild\MyFiles\Northwind.targets*에 설치한 다음, 이 XML 코드를 사용하여 프로젝트 파일로 가져옵니다.<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | 잘 알려짐 | *\Program Files* 또는 *\Program Files (x86)* 폴더 아래에 있는 MSBuild 하위 폴더의 경로입니다. 이 경로는 항상 32비트 머신의 32비트 *\Program Files(x86)* 폴더와 64비트 머신의 *\Program Files*를 가리킵니다. `MSBuildExtensionsPath` 및 `MSBuildExtensionsPath64`도 참조하세요.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildExtensionsPath64` | 잘 알려짐 | *\Program Files* 폴더 아래에 있는 MSBuild 하위 폴더의 경로입니다. 64비트 컴퓨터의 경우 이 경로는 항상 *\Program Files* 폴더를 가리킵니다. 32비트 컴퓨터에서는 이 경로가 비어 있습니다. `MSBuildExtensionsPath` 및 `MSBuildExtensionsPath32`도 참조하세요.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildInteractive` | 예약됨 | MSBuild가 대화형으로 실행되어 사용자 입력을 허용하는 경우 `true`입니다. 이 설정은 `-interactive` 명령줄 옵션에 의해 제어됩니다. |
| `MSBuildLastTaskResult` | 예약됨 | 이전 작업이 오류 없이(경고가 있어도) 완료되면 `true`이고, 이전 작업에 오류가 있으면 `false`입니다. 일반적으로 작업에서 오류가 발생하면 오류는 해당 프로젝트에서 마지막으로 발생하는 항목입니다. 따라서 이 속성의 값은 `false`를 사용하지 않습니다. 단, 다음 시나리오에서는 제외됩니다.<br /><br /> - [Task 요소(MSBuild)](../msbuild/task-element-msbuild.md)의 `ContinueOnError` 특성이 `WarnAndContinue`(또는 `true`)나 `ErrorAndContinue`로 설정된 경우<br /><br /> - `Target`에 [OnError 요소(MSBuild)](../msbuild/onerror-element-msbuild.md)가 자식 요소로 포함되어 있는 경우 |
| `MSBuildNodeCount` | 예약됨 | 작성 시 사용되는 동시 프로세스의 최대 수입니다. 이 값은 명령줄에서 **-maxcpucount**에 대해 지정한 값입니다. 값을 지정하지 않고 **/maxcpucount**를 지정한 경우 `MSBuildNodeCount`는 컴퓨터의 프로세서 수를 지정합니다. 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md) 및 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)를 참조하세요. |
| `MSBuildProgramFiles32` | 예약됨 | 32비트 프로그램 폴더의 위치(예: *C:\Program Files (x86)* )입니다.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildProjectDefaultTargets` | 예약됨 | `DefaultTargets` 요소의 `Project` 특성에 지정된 대상의 전체 목록입니다. 예를 들어, 다음 `Project` 요소의 `MSBuildDefaultTargets` 속성 값이 `A;B;C`입니다.<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | 예약됨 | 프로젝트 파일이 있는 디렉터리의 절대 경로(예: *C:\MyCompany\MyProduct*)입니다.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildProjectDirectoryNoRoot` | 예약됨 | `MSBuildProjectDirectory` 속성 값입니다. 단, 루트 드라이브를 제외합니다.<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildProjectExtension` | 예약됨 | 마침표가 포함된 프로젝트 파일의 파일 확장명(예: *.proj*)입니다. |
| `MSBuildProjectFile` | 예약됨 | 파일 확장명이 포함된 프로젝트 파일의 전체 파일 이름(예: *MyApp.proj*)입니다. |
| `MSBuildProjectFullPath` | 예약됨 | 파일 확장명이 포함된 프로젝트 파일의 절대 경로와 전체 파일 이름(예: *C:\MyCompany\MyProduct\MyApp.proj*)입니다. |
| `MSBuildProjectName` | 예약됨 | 파일 확장명이 없는 프로젝트 파일의 파일 이름(예: *MyApp*)입니다. |
| `MSBuildRuntimeType` | 예약됨 | 현재 실행 중인 런타임의 형식입니다. MSBuild 15에서 도입되었습니다. MSBuild가 데스크톱 .NET Framework에서 실행 중임을 나타내는 `Full`, MSBuild가 .NET Core에서 실행 중임을 나타내는 `Core`(예를 들어 `dotnet build`에서) 또는 MSBuild가 Mono에서 실행 중임을 나타내는 `Mono` 값이 정의되어 있지 않을 수 있습니다(MSBuild 15 이전). |
| `MSBuildStartupDirectory` | 예약됨 | MSBuild가 호출되는 폴더의 절대 경로입니다. 이 속성을 사용하면 모든 디렉터리에서 *\<dirs>.proj* 파일을 만들지 않고 프로젝트 트리에서 특정 지점 아래에 모든 것을 빌드할 수 있습니다. 대신 다음과 같이 프로젝트(예: *c:\traversal.proj*)를 하나만 포함합니다.<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> 임의의 트리 위치에 빌드하려면 다음을 입력합니다.<br /><br /> `msbuild c:\traversal.proj`<br /><br /> 이 속성에는 마지막 백슬래시를 포함하지 마세요. |
| `MSBuildThisFile` | 예약됨 | `MSBuildThisFileFullPath`의 파일 이름 및 파일 확장명 부분입니다. |
| `MSBuildThisFileDirectory` | 예약됨 | `MSBuildThisFileFullPath`의 디렉터리 부분입니다.<br /><br /> 경로에 마지막 백슬래시를 포함하세요. |
| `MSBuildThisFileDirectoryNoRoot` | 예약됨 | 루트 드라이브를 제외한 `MSBuildThisFileFullPath`의 디렉터리 부분입니다.<br /><br /> 경로에 마지막 백슬래시를 포함하세요. |
| `MSBuildThisFileExtension` | 예약됨 | `MSBuildThisFileFullPath`의 파일 확장명 부분입니다. |
| `MSBuildThisFileFullPath` | 예약됨 | 실행하는 대상을 포함하는 프로젝트 또는 대상 파일의 절대 경로입니다.<br /><br /> 팁: 대상 파일에 관련되고 원본 프로젝트 파일에는 관련되지 않은 대상 파일의 상대 경로를 지정할 수 있습니다. |
| `MSBuildThisFileName` | 예약됨 | 파일 확장명을 제외한 `MSBuildThisFileFullPath`의 파일 이름 부분입니다. |
| `MSBuildToolsPath` | 예약됨 | `MSBuildToolsVersion` 값과 연결된 MSBuild 버전의 설치 경로입니다.<br /><br /> 경로에 마지막 백슬래시를 포함하지 마세요.<br /><br /> 이 속성은 재정의할 수 없습니다. |
| `MSBuildToolsVersion` | 예약됨 | 프로젝트 빌드에 사용된 MSBuild 도구 집합의 버전입니다.<br /><br /> 참고: MSBuild 도구 집합은 애플리케이션 빌드에 사용되는 작업, 대상 및 도구로 구성됩니다. 도구에는 *csc.exe* 및 *vbc.exe*와 같은 컴파일러가 포함됩니다. 자세한 내용은 [도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 및 [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)을 참조하세요. |
| `MSBuildVersion` | 예약됨 | 프로젝트 빌드에 사용된 MSBuild의 버전입니다. <br /><br/> 이 속성은 대체할 수 없습니다. 대체하면 `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` 오류 메시지가 반환됩니다. |

## <a name="names-that-conflict-with-msbuild-elements"></a>MSBuild 요소와 충돌하는 이름

위의 내용 외에 MSBuild 언어 요소에 해당하는 이름은 사용자 정의 속성, 항목 또는 항목 메타 데이터에 대해 사용할 수 없습니다.

* VisualStudioProject
* Target
* PropertyGroup
* Output
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* When
* Otherwise

## <a name="see-also"></a>참조

- [MSBuild 참조](../msbuild/msbuild-reference.md)

- [MSBuild 속성](../msbuild/msbuild-properties.md)
