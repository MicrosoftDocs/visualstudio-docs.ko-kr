---
title: MT 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- vc.task.mt
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBUILD (C++), MT task
- MT task (MSBuild (C++))
ms.assetid: bb94913c-1042-4968-9f08-b394518e899f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe0ce106fc471431d3aac088eb3f45cfb28c564
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633059"
---
# <a name="mt-task"></a>MT 작업

Microsoft 매니페스트 도구, *mt.exe*를 래핑합니다. 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 **MT** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수 및 몇 가지 매개 변수 집합은 명령줄 옵션에 해당합니다.

> [!NOTE]
> *mt.exe* 설명서는 명령줄 옵션에 대한 접두사로 하이픈( **-** )을 사용하지만 이 항목에서는 슬래시( **/** )를 사용합니다. 두 접두사 중 하나를 사용할 수 있습니다.

|매개 변수|Description|
|---------------|-----------------|
|**AdditionalManifestFiles**|선택적 **String[]** 매개 변수입니다.<br /><br /> 하나 이상의 매니페스트 파일의 이름을 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/manifest** 옵션을 참조하세요.|
|**AdditionalOptions**|선택적 **String** 매개 변수입니다.<br /><br /> 명령줄 옵션의 목록입니다. 예를 들어 /\<option1> /\<option2> /\<option#>을 참조하십시오. 이 매개 변수를 사용하여 다른 **MT** 작업 매개 변수로 표현되지 않는 명령줄 옵션을 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)를 참조하세요.|
|**AssemblyIdentity**|선택적 **String** 매개 변수입니다.<br /><br /> 매니페스트의 **assemblyIdentity** 요소의 특성 값을 지정합니다. 쉼표로 구분된 목록을 지정합니다. 여기서 첫 번째 구성 요소는 뒤에 *\<attribute name>=<attribute_value>* 형식을 가진 하나 이상의 이름/값 쌍이 오는 `name` 특성의 값입니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/identity** 옵션을 참조하세요.|
|**ComponentFileName**|선택적 **String** 매개 변수입니다.<br /><br /> *.rgs* 또는 *.tlb* 파일에서 빌드하려는 동적 연결 라이브러리의 이름을 지정합니다. **RegistrarScriptFile** 또는 **TypeLibraryFile** MT 작업 매개 변수를 지정하는 경우 이 매개 변수는 필수입니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/dll** 옵션을 참조하세요.|
|**DependencyInformationFile**|선택적 **String** 매개 변수입니다.<br /><br /> 매니페스트 도구에 대한 빌드 종속성 정보를 추적하기 위해 Visual Studio에서 사용하는 종속성 정보 파일을 지정합니다.|
|**EmbedManifest**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 어셈블리에 매니페스트 파일을 포함합니다. `false`인 경우 독립 실행형 매니페스트 파일로 만듭니다.|
|**EnableDPIAwareness**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 애플리케이션을 DPI 인식으로 표시하는 매니페스트 정보에 추가합니다. DPI 인식 애플리케이션을 작성하면 사용자 인터페이스는 높은 DPI 디스플레이 설정의 광범위한 부분에서 일관성 있게 보입니다.<br /><br /> 자세한 내용은 [높은 DPI](/windows/desktop/win7devguide/high-dpi)를 참조하세요.|
|**GenerateCatalogFiles**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 카탈로그 정의( *.cdf*) 파일을 생성합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/makecdfs** 옵션을 참조하세요.|
|**GenerateCategoryTags**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 범주 태그가 생성됩니다. 이 매개 변수가 `true`인 경우 **ManifestFromManagedAssemblyMT** 작업 매개 변수도 지정되어야 합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/category** 옵션을 참조하세요.|
|**InputResourceManifests**|선택적 **String** 매개 변수입니다.<br /><br /> 지정한 식별자를 가진 RT_MANIFEST 형식의 리소스에서 매니페스트를 입력합니다. \<file>[;[#]\<resource_id>] 형식의 리소스를 지정합니다. 여기서 선택적 \<resource_id> 매개 변수는 음수가 아닌 16비트 숫자입니다.<br /><br /> `resource_id`가 지정되지 않은 경우 CREATEPROCESS_MANIFEST_RESOURCE 기본값(1)이 사용됩니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/inputresource** 옵션을 참조하세요.|
|**ManifestFromManagedAssembly**|선택적 **String** 매개 변수입니다.<br /><br /> 지정된 관리되는 어셈블리에서 매니페스트를 생성합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/managedassemblyname** 옵션을 참조하세요.|
|**ManifestToIgnore**|선택적 **String** 매개 변수입니다.<br /><br /> (사용되지 않습니다.)|
|**OutputManifestFile**|선택적 **String** 매개 변수입니다.<br /><br /> 출력 매니페스트의 이름을 지정합니다. 이 매개 변수가 생략되고 하나의 매니페스트만 작업 중인 경우 해당 매니페스트는 위치에서 수정됩니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/out** 옵션을 참조하세요.|
|**OutputResourceManifests**|선택적 **String** 매개 변수입니다.<br /><br /> 지정한 식별자를 가진 RT_MANIFEST 형식의 리소스에 매니페스트를 출력합니다. 리소스는 \<file>[;[#]\<resource_id>] 형식이며 여기서 선택적 \<resource_id> 매개 변수는 음수가 아닌 16비트 숫자입니다.<br /><br /> `resource_id`가 지정되지 않은 경우 CREATEPROCESS_MANIFEST_RESOURCE 기본값(1)이 사용됩니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/outputresource** 옵션을 참조하세요.|
|**RegistrarScriptFile**|선택적 **String** 매개 변수입니다.<br /><br /> 등록이 필요 없는 COM 매니페스트를 지원하기 위해 사용할 등록자 스크립트( *.rgs*) 파일의 이름을 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/rgs** 옵션을 참조하세요.|
|**ReplacementsFile**|선택적 **String** 매개 변수입니다.<br /><br /> 등록자 스크립트( *.rgs*) 파일에서 대체 가능한 문자열 값이 들어 있는 파일을 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/replacements** 옵션을 참조하세요.|
|**ResourceOutputFileName**|선택적 **String** 매개 변수입니다.<br /><br /> 매니페스트를 프로젝트 출력에 포함시키는 데 사용하는 출력 리소스 파일을 지정합니다.|
|**Sources**|선택적 `ITaskItem[]` 매개 변수입니다.<br /><br /> 공백으로 구분된 매니페스트 소스 파일 목록을 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/manifest** 옵션을 참조하세요.|
|**SuppressDependencyElement**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 종속성 요소 없이 매니페스트를 생성합니다. 이 매개 변수가 `true`인 경우 **ManifestFromManagedAssemblyMT** 작업 매개 변수도 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/nodependency** 옵션을 참조하세요.|
|**SuppressStartupBanner**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/nologo** 옵션을 참조하세요.|
|**TrackerLogDirectory**|선택적 `String` 매개 변수입니다.<br /><br /> 이 작업에 대한 추적 로그를 저장할 중간 디렉터리를 지정합니다.|
|**TypeLibraryFile**|선택적 **String** 매개 변수입니다.<br /><br /> 형식 라이브러리( *.tlb*) 파일의 이름을 지정합니다. 이 매개 변수를 지정하는 경우 **ComponentFileNameMT** 작업 매개 변수도 지정합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/tlb** 옵션을 참조하세요.|
|**UpdateFileHashes**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 **UpdateFileHashesSearchPathMT** 작업 매개 변수로 지정된 경로에서 파일의 해시 값을 계산한 다음 계산된 값을 사용하여 매니페스트의 **file** 요소의 **hash** 특성의 값을 업데이트합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/hashupdate** 옵션을 참조하세요. 또한 이 표에서 **UpdateFileHashesSearchPath** 매개 변수도 참조하세요.|
|**UpdateFileHashesSearchPath**|선택적 `String` 매개 변수입니다.<br /><br /> 파일 해시가 업데이트될 때 사용할 검색 경로를 지정합니다. **UpdateFileHashesMT** 작업 매개 변수와 함께 이 매개 변수를 사용합니다.<br /><br /> 자세한 내용은 이 표의 **UpdateFileHashes** 매개 변수를 참조하세요.|
|**VerboseOutput**|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 자세한 디버깅 정보를 표시합니다.<br /><br /> 자세한 내용은 [Mt.exe](/windows/desktop/SbsCs/mt-exe)의 **/verbose** 옵션을 참조하세요.|

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
