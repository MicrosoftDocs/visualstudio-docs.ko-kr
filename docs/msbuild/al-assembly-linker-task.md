---
title: AL(어셈블리 링커) 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6861fee8691c32415111347ab673f9e48bfb9e11
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634593"
---
# <a name="al-assembly-linker-task"></a>AL(어셈블리 링커) 작업

AL 작업은 Windows SDK(소프트웨어 개발 키트)와 함께 배포되는 도구인 *AL.exe*를 래핑합니다. 이 어셈블리 링커 도구는 모듈 또는 리소스 파일에 해당하는 하나 이상의 파일에 있는 매니페스트로 어셈블리를 생성하는 데 사용됩니다. 컴파일러 및 개발 환경에서 이러한 기능을 이미 제공할 수 있으므로 이 작업을 직접 사용할 필요가 없는 경우가 많습니다. 어셈블리 링커는 혼합 언어 개발에서 생성될 수 있는 것과 같은 여러 구성 요소 파일에서 단일 어셈블리를 만들어야 하는 개발자에게 가장 유용합니다. 이 작업은 모듈을 단일 어셈블리 파일로 결합하지 않습니다. 결과 어셈블리가 올바르게 로드되려면 여전히 개별 모듈이 분산되어야 하고 사용 가능해야 하기 때문입니다. *AL.exe*에 대한 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `AL` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|---------------------| - |
| `AlgorithmID` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리 매니페스트가 포함된 파일을 제외하고 다중 파일 어셈블리에 있는 모든 파일을 해시하는 알고리즘을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/algid` 옵션에 대한 설명서를 참조하세요. |
| `BaseAddress` | 선택적 `String` 매개 변수입니다.<br /><br /> 런타임에 DLL이 사용자의 컴퓨터에 로드되는 주소를 지정합니다. 운영 체제가 프로세스 공간에서 DLL을 재배치하게 하지 않고 DLL의 기본 주소를 직접 지정하면 애플리케이션의 로드 속도가 빨라집니다. 이 매개 변수는 /base[address](/dotnet/framework/tools/al-exe-assembly-linker)에 해당합니다. |
| `CompanyName` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Company` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/comp[any]` 옵션에 대한 설명서를 참조하세요. |
| `Configuration` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Configuration` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/config[uration]` 옵션에 대한 설명서를 참조하세요. |
| `Copyright` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Copyright` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/copy[right]` 옵션에 대한 설명서를 참조하세요. |
| `Culture` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리에 연결할 문화권 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/c[ulture]` 옵션에 대한 설명서를 참조하세요. |
| `DelaySign` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 어셈블리에 공개 키만 배치하려면 `true`이고, 어셈블리에 완전하게 서명하려면 `false`입니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/delay[sign]` 옵션에 대한 설명서를 참조하세요. |
| `Description` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Description` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/descr[iption]` 옵션에 대한 설명서를 참조하세요. |
| `EmbedResources` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 어셈블리 매니페스트가 포함된 이미지에 지정된 리소스를 포함합니다. 이 작업은 이미지에 리소스 파일의 내용을 복사합니다. 이 매개 변수에 전달된 항목에는 `LogicalName` 및 `Access`라는 선택적 메타데이터가 연결될 수 있습니다. `LogicalName` 메타데이터는 리소스에 대한 내부 식별자를 지정하는 데 사용됩니다.  해당 리소스가 다른 어셈블리에 표시되지 않게 하려면 `Access` 메타데이터를 `private`로 설정할 수 있습니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/embed[resource]` 옵션에 대한 설명서를 참조하세요. |
| `EvidenceFile` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리에 지정된 파일을 `Security.Evidence`라는 리소스 이름으로 포함합니다.<br /><br /> 기본 리소스에는 `Security.Evidence`를 사용할 수 없습니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/e[vidence]` 옵션에 해당합니다. |
| `ExitCode` | 선택적 `Int32` 읽기 전용 출력 매개 변수입니다.<br /><br /> 실행한 명령에서 제공하는 종료 코드를 지정합니다. |
| `FileVersion` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `File Version` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/fileversion` 옵션에 대한 설명서를 참조하세요. |
| `Flags` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Flags` 필드에 대한 값을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/flags` 옵션에 대한 설명서를 참조하세요. |
| `GenerateFullPaths` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 오류 메시지에 보고되는 파일에 대해 이 작업은 절대 경로를 사용합니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/fullpaths` 옵션에 해당합니다. |
| `KeyContainer` | 선택적 `String` 매개 변수입니다.<br /><br /> 키 쌍을 보관하는 컨테이너를 지정합니다. 어셈블리 매니페스트에 공개 키를 삽입하여 어셈블리에 서명(강력한 이름을 부여)합니다. 그런 다음 이 작업은 프라이빗 키를 사용하여 최종 어셈블리에 서명합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/keyn[ame]` 옵션에 대한 설명서를 참조하세요. |
| `KeyFile` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리에 서명하기 위한 키 쌍 또는 공개 키를 포함하는 파일을 지정합니다. 컴파일러는 퍼블릭 키를 어셈블리 매니페스트에 삽입한 다음 프라이빗 키를 사용하여 최종 어셈블리에 서명합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/keyf[ile]` 옵션에 대한 설명서를 참조하세요. |
| `LinkResources` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 지정한 리소스 파일을 어셈블리에 연결합니다. 리소스가 어셈블리의 일부가 되지만 파일은 복사되지 않습니다. 이 매개 변수에 전달된 항목에는 `LogicalName`, `Target` 및 `Access`라는 선택적 메타데이터가 연결될 수 있습니다. `LogicalName` 메타데이터는 리소스에 대한 내부 식별자를 지정하는 데 사용됩니다. `Target` 메타데이터는 작업이 파일을 복사하는 경로 및 파일 이름을 지정할 수 있습니다. 그런 후에 이 새 파일을 어셈블리로 컴파일합니다. 해당 리소스가 다른 어셈블리에 표시되지 않게 하려면 `Access` 메타데이터를 `private`로 설정할 수 있습니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/link[resource]` 옵션에 대한 설명서를 참조하세요. |
| `MainEntryPoint` | 선택적 `String` 매개 변수입니다.<br /><br /> 모듈을 실행 파일로 변환할 때 진입점으로 사용할 메서드의 정규화된 이름(*class.method*)을 지정합니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/main` 옵션에 해당합니다. |
| `OutputAssembly` | 필수 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 이 작업에서 생성한 파일의 이름을 지정합니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/out` 옵션에 해당합니다. |
| `Platform` | 선택적 `String` 매개 변수입니다.<br /><br /> 이 코드를 실행할 수 있는 플랫폼을 제한하며, `x86`, `Itanium`, `x64` 또는 `anycpu` 중 하나여야 합니다. 기본값은 `anycpu`입니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/platform` 옵션에 해당합니다. |
| `ProductName` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Product` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/prod[uct]` 옵션에 대한 설명서를 참조하세요. |
| `ProductVersion` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `ProductVersion` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/productv[ersion]` 옵션에 대한 설명서를 참조하세요. |
| `ResponseFiles` | 선택적 `String[]` 매개 변수입니다.<br /><br /> 어셈블리 링커를 통과하기 위한 추가 옵션을 포함하는 응답 파일을 지정합니다. |
| `SdkToolsPath` | 선택적 `String` 매개 변수입니다.<br /><br /> resgen.exe와 같은 SDK 도구에 대한 경로를 지정합니다. |
| `SourceModules` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 어셈블리로 컴파일할 하나 이상의 모듈입니다. 모듈은 결과 어셈블리의 매니페스트에 나열되며 어셈블리가 로드되기 위해 여전히 분산되고 사용 가능해야 합니다. 이 매개 변수로 전달된 항목은 작업이 파일을 복사하는 경로 및 파일 이름을 지정하는 `Target`이라는 추가 메타데이터를 포함할 수 있습니다. 작업은 파일을 복사한 후에 이 새 파일을 어셈블리로 컴파일합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)에 대한 설명서를 참조하세요. 이 매개 변수는 특정 스위치 없이 *Al.exe*로 전달되는 모듈 목록에 해당합니다. |
| `TargetType` | 선택적 `String` 매개 변수입니다.<br /><br /> 출력 파일의 파일 형식 즉, `library`(코드 라이브러리), `exe`(콘솔 애플리케이션) 또는 `win`(Windows 기반 애플리케이션)을 지정합니다. 기본값은 `library`입니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/t[arget]` 옵션에 해당합니다. |
| `TemplateFile` | 선택적 `String` 매개 변수입니다.<br /><br /> culture 필드를 제외한 모든 어셈블리 메타데이터를 상속받을 상위 어셈블리를 지정합니다. 지정된 어셈블리에는 강력한 이름이 있어야 합니다.<br /><br /> `TemplateFile` 매개 변수를 사용하여 만든 어셈블리는 위성 어셈블리가 됩니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/template` 옵션에 해당합니다. |
| `Timeout` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 작업 실행 파일이 얼마 후에 종료될 지를 밀리초 단위로 지정합니다. 기본값은 시간 제한이 없음을 나타내는 `Int.MaxValue`입니다. |
| `Title` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Title` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/title` 옵션에 대한 설명서를 참조하세요. |
| `ToolPath` | 선택적 `String` 매개 변수입니다.<br /><br /> 작업에서 내부 실행 파일(Al.exe)을 로드할 위치를 지정합니다. 이 매개 변수를 지정하지 않으면 작업에서는 MSBuild를 실행하고 있는 프레임워크 버전에 해당하는 SDK 설치 경로가 사용됩니다. |
| `Trademark` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리의 `Trademark` 필드에 대한 문자열을 지정합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/trade[mark]` 옵션에 대한 설명서를 참조하세요. |
| `Version` | 선택적 `String` 매개 변수입니다.<br /><br /> 이 어셈블리의 버전 정보를 지정합니다. 문자열의 형식은 *major.minor.build.revision*입니다. 기본값은 0입니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/v[ersion]` 옵션에 대한 설명서를 참조하세요. |
| `Win32Icon` | 선택적 `String` 매개 변수입니다.<br /><br /> *.ico* 파일을 어셈블리에 삽입합니다. *.ico* 파일을 사용하면 파일 탐색기에서 출력 파일을 원하는 모양으로 나타납니다. 이 매개 변수는 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/win32icon` 옵션에 해당합니다. |
| `Win32Resource` | 선택적 `String` 매개 변수입니다.<br /><br /> Win32 리소스( *.res* 파일)를 출력 파일에 삽입합니다. 자세한 내용은 [Al.exe(어셈블리 링커)](/dotnet/framework/tools/al-exe-assembly-linker)의 `/win32res` 옵션에 대한 설명서를 참조하세요. |

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [ToolTaskExtension 기본 클래스](../msbuild/tooltaskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 지정된 옵션을 사용하여 어셈블리를 만듭니다.

```xml
<AL
    EmbedResources="@(EmbeddedResource)"
    Culture="%(EmbeddedResource.Culture)"
    TemplateFile="@(IntermediateAssembly)"
    KeyContainer="$(KeyContainerName)"
    KeyFile="$(KeyOriginatorFile)"
    DelaySign="$(DelaySign)"

    OutputAssembly=
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">

    <Output TaskParameter="OutputAssembly"
        ItemName="SatelliteAssemblies"/>
</AL>
```

## <a name="see-also"></a>참조

* [작업 참조](../msbuild/msbuild-task-reference.md)
* [작업](../msbuild/msbuild-tasks.md)
