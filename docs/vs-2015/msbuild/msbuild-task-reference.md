---
title: MSBuild 작업 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fe581985ec173099790311517c0442a9c29c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154115"
---
# <a name="msbuild-task-reference"></a>MSBuild 작업 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

작업은 빌드 프로세스 동안 실행되는 코드를 제공합니다. 다음 목록의 작업이 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에 포함되어 있습니다. [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]가 설치되면 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 프로젝트를 빌드하는 데 사용되는 추가 작업을 사용할 수 있습니다. 자세한 내용은 [Visual C++ 작업](../msbuild/msbuild-tasks-specific-to-visual-cpp.md)을 참조 하세요.  
  
 이 섹션의 항목에 나열된 매개 변수 외에도 각 작업에는 다음과 같은 매개 변수가 있습니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Condition`|선택적 `String` 매개 변수입니다.<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 엔진이 이 작업이 실행될지 여부를 결정하는 데 사용하는 `Boolean` 식입니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 지원되는 조건에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
|`ContinueOnError`|선택적 매개 변수입니다. 다음 값 중 하나를 포함할 수 있습니다.<br /><br /> -   **WarnAndContinue** 또는 **true**. 작업이 실패할 경우 [Target](../msbuild/target-element-msbuild.md) 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 경고로 처리됩니다.<br />-   **ErrorAndContinue**. 작업이 실패할 경우 `Target` 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 오류로 처리됩니다.<br />-   **ErrorAndStop** 또는 **false**(기본값). 작업이 실패할 경우 `Target` 요소의 나머지 작업이 실행되지 않고 전체 `Target` 요소와 빌드가 실패한 것으로 간주됩니다.<br /><br /> .NET Framework 4.5 이전 버전은 `true` 및 `false` 값만 지원합니다.<br /><br /> 자세한 내용은 [방법: 작업의 오류 무시를](../msbuild/how-to-ignore-errors-in-tasks.md)참조 하세요.|  
  
## <a name="in-this-section"></a>섹션 내용  
 [작업 기본 클래스](../msbuild/task-base-class.md)  
 <xref:Microsoft.Build.Utilities.Task> 클래스에서 파생되는 작업에 해당 매개 변수 몇 개를 추가합니다.  
  
 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)  
 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 파생되는 작업에 해당 매개 변수 몇 개를 추가합니다.  
  
 [ToolTaskExtension 기본 클래스](../msbuild/tooltaskextension-base-class.md)  
 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스에서 파생되는 작업에 해당 매개 변수 몇 개를 추가합니다.  
  
 [AL (어셈블리 링커) 작업](../msbuild/al-assembly-linker-task.md)  
 모듈 또는 리소스 파일에 해당하는 하나 이상의 파일에 있는 매니페스트로 어셈블리를 만듭니다.  
  
 [AspNetCompiler 작업](../msbuild/aspnetcompiler-task.md)  
 ASP.NET 애플리케이션을 미리 컴파일하는 유틸리티인 aspnet_compiler.exe를 래핑합니다.  
  
 [문화권 할당 작업](../msbuild/assignculture-task.md)  
 항목에 문화권 식별자를 할당합니다.  
  
 [할당 Projectconfiguration 작업](../msbuild/assignprojectconfiguration-task.md)  
 구성 문자열의 목록을 수락하고 지정된 프로젝트에 할당합니다.  
  
 [AssignTargetPath 작업](../msbuild/assigntargetpath-task.md)  
 파일 목록을 수락하고 `<TargetPath>` 특성을 아직 지정하지 않은 경우 추가합니다.  
  
 [CallTarget 작업](../msbuild/calltarget-task.md)  
 프로젝트 파일에서 대상을 호출합니다.  
  
 [CombinePath 작업](../msbuild/combinepath-task.md)  
 지정된 경로를 단일 경로로 결합합니다.  
  
 [ConvertToAbsolutePath 작업](../msbuild/converttoabsolutepath-task.md)  
 절대 경로 또는 참조를 상대 경로로 변환합니다.  
  
 [작업 복사](../msbuild/copy-task.md)  
 새 위치에 파일을 복사합니다.  
  
 [CreateCSharpManifestResourceName 작업](../msbuild/createcsharpmanifestresourcename-task.md)  
 지정된 .resx 파일 이름 또는 기타 리소스에서 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 스타일 매니페스트 이름을 만듭니다.  
  
 [CreateItem 작업](../msbuild/createitem-task.md)  
 입력 항목에서 항목 컬렉션을 채워 항목을 한 목록에서 다른 목록으로 복사할 수 있도록 합니다.  
  
 [CreateProperty 작업](../msbuild/createproperty-task.md)  
 입력 값에서 속성을 채워 값을 한 속성 또는 문자열에서 다른 속성 또는 문자열로 복사할 수 있도록 합니다.  
  
 [CreateVisualBasicManifestResourceName 작업](../msbuild/createvisualbasicmanifestresourcename-task.md)  
 지정된 .resx 파일 이름 또는 기타 리소스에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 스타일 매니페스트 이름을 만듭니다.  
  
 [Csc 작업](../msbuild/csc-task.md)  
 Visual C# 컴파일러를 호출하여 실행 파일, 동적 연결 라이브러리 또는 코드 모듈을 생성합니다.  
  
 [작업 삭제](../msbuild/delete-task.md)  
 지정한 파일을 삭제합니다.  
  
 [오류 작업](../msbuild/error-task.md)  
 빌드를 중지하고 평가된 조건부 문에 따라 오류를 기록합니다.  
  
 [Exec 작업](../msbuild/exec-task.md)  
 지정된 인수를 사용하여 지정된 프로그램 또는 명령을 실행합니다.  
  
 [FindAppConfigFile 작업](../msbuild/findappconfigfile-task.md)  
 제공된 목록에서 app.config 파일(있는 경우)을 찾습니다.  
  
 [FindInList 작업](../msbuild/findinlist-task.md)  
 일치하는 항목 사양을 갖는 항목을 지정된 목록에서 찾습니다.  
  
 [Find미달 경로 작업](../msbuild/findunderpath-task.md)  
 지정된 폴더 및 모든 하위 폴더에 있는 지정된 항목 컬렉션의 항목을 확인합니다.  
  
 [FormatUrl 작업](../msbuild/formaturl-task.md)  
 URL을 올바른 URL 형식으로 변환합니다.  
  
 [FormatVersion 작업](../msbuild/formatversion-task.md)  
 버전 번호에 수정 버전 번호를 추가합니다.  
  
 [GenerateApplicationManifest 작업](../msbuild/generateapplicationmanifest-task.md)  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 매니페스트 또는 네이티브 매니페스트를 생성합니다.  
  
 [GenerateBootstrapper 작업](../msbuild/generatebootstrapper-task.md)  
 애플리케이션과 해당 필수 조건을 검색, 다운로드, 설치할 수 있는 자동화된 방법을 제공합니다.  
  
 [GenerateDeploymentManifest 작업](../msbuild/generatedeploymentmanifest-task.md)  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 매니페스트를 생성합니다.  
  
 [GenerateResource 작업](../msbuild/generateresource-task.md)  
 .txt 및 .resx 파일을 공용 언어 런타임 이진 .resources 파일로 변환합니다.  
  
 [GenerateTrustInfo 작업](../msbuild/generatetrustinfo-task.md)  
 기본 매니페스트, `TargetZone` 및 `ExcludedPermissions` 매개 변수에서 애플리케이션 신뢰를 생성합니다.  
  
 [GetAssemblyIdentity 작업](../msbuild/getassemblyidentity-task.md)  
 지정된 파일에서 어셈블리 ID를 검색하고 ID 정보를 출력합니다.  
  
 [GetFrameworkPath 작업](../msbuild/getframeworkpath-task.md)  
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 어셈블리에 대한 경로를 검색합니다.  
  
 [GetFrameworkSdkPath 작업](../msbuild/getframeworksdkpath-task.md)  
 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]에 대한 경로를 검색합니다.  
  
 [GetReferenceAssemblyPaths 작업](../msbuild/getreferenceassemblypaths-task.md)  
 다양한 프레임워크의 참조 어셈블리 경로를 반환합니다.  
  
 [LC 작업](../msbuild/lc-task.md)  
 .licx 파일에서 .license 파일을 생성합니다.  
  
 [MakeDir 작업](../msbuild/makedir-task.md)  
 디렉터리 및 부모 디렉터리(필요한 경우)를 만듭니다.  
  
 [메시지 작업](../msbuild/message-task.md)  
 빌드하는 동안 메시지를 로깅합니다.  
  
 [작업 이동](../msbuild/move-task.md)  
 새 위치로 파일을 이동합니다.  
  
 [MSBuild 작업](../msbuild/msbuild-task.md)  
 다른 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트에서 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트를 빌드합니다.  
  
 [ReadLinesFromFile 작업](../msbuild/readlinesfromfile-task.md)  
 텍스트 파일에서 항목 목록을 읽습니다.  
  
 [RegisterAssembly 작업](../msbuild/registerassembly-task.md)  
 지정된 어셈블리 내의 메타데이터를 읽고 레지스트리에 필요한 항목을 추가합니다.  
  
 [RemoveDir 작업](../msbuild/removedir-task.md)  
 지정한 디렉터리와 모든 파일 및 하위 디렉터리를 제거합니다.  
  
 [RemoveDuplicates 작업](../msbuild/removeduplicates-task.md)  
 지정된 항목 컬렉션에서 중복된 항목을 제거합니다.  
  
 [RequiresFramework35SP1Assembly 작업](../msbuild/requiresframework35sp1assembly-task.md)  
 애플리케이션에 .NET Framework 3.5 SP1이 필요한지 여부를 확인합니다.  
  
 ResGen 작업  
 사용되지 않습니다. [GenerateResource 작업](../msbuild/generateresource-task.md)을 사용하여 .txt 및 .resx 파일을 공용 언어 런타임 이진 .resources 파일로 변환하거나 그 반대로 변환합니다.  
  
 [ResolveAssemblyReference 작업](../msbuild/resolveassemblyreference-task.md)  
 지정된 어셈블리에 종속된 모든 어셈블리를 결정합니다.  
  
 [ResolveComReference 작업](../msbuild/resolvecomreference-task.md)  
 하나 이상의 형식 라이브러리 이름 또는 .tlb 파일 목록을 가져온 후 해당 형식 라이브러리를 디스크의 위치로 확인합니다.  
  
 [ResolveKeySource 작업](../msbuild/resolvekeysource-task.md)  
 강력한 이름 키 소스를 확인합니다.  
  
 [ResolveManifestFiles 작업](../msbuild/resolvemanifestfiles-task.md)  
 빌드 프로세스에서 빌드된 항목, 종속성, 위성, 콘텐츠, 디버그 기호 및 설명서 등의 항목을 확인합니다.  
  
 [ResolveNativeReference 작업](../msbuild/resolvenativereference-task.md)  
 네이티브 참조를 확인합니다.  
  
 [ResolveNonMSBuildProjectOutput 작업](../msbuild/resolvenonmsbuildprojectoutput-task.md)  
 비 MSBuild 프로젝트 참조의 출력 파일을 확인합니다.  
  
 [SGen 작업](../msbuild/sgen-task.md)  
 지정된 어셈블리의 형식에 대한 XML serialization 어셈블리를 만듭니다.  
  
 [SignFile 작업](../msbuild/signfile-task.md)  
 지정된 인증서를 사용하여 지정한 파일에 서명을 합니다.  
  
 [Touch 작업](../msbuild/touch-task.md)  
 파일의 액세스 및 수정 시간을 설정합니다.  
  
 [UnregisterAssembly 작업](../msbuild/unregisterassembly-task.md)  
 COM interop 용도로 지정된 어셈블리의 등록을 취소합니다.  
  
 [UpdateManifest 작업](../msbuild/updatemanifest-task.md)  
 매니페스트에서 선택한 속성을 업데이트하고 다시 서명합니다.  
  
 [Vbc 작업](../msbuild/vbc-task.md)  
 Visual Basic 컴파일러를 호출하여 실행 파일, 동적 연결 라이브러리 또는 코드 모듈을 생성합니다.  
  
 [경고 작업](../msbuild/warning-task.md)  
 평가된 조건부 문에 따라 빌드 중에 경고를 로깅합니다.  
  
 [WriteCodeFragment 작업](../msbuild/writecodefragment-task.md)  
 생성된 특정 코드 조각을 사용하여 임시 코드 파일을 생성합니다. 파일을 삭제하지는 않습니다.  
  
 [WriteLinesToFile 작업](../msbuild/writelinestofile-task.md)  
 지정된 항목을 지정된 텍스트 파일에 씁니다.  
  
 [XmlPeek 작업](../msbuild/xmlpeek-task.md)  
 XML 파일에서의 XPath 쿼리에 의해 지정된 대로 값을 반환합니다.  
  
 [XmlPoke 작업](../msbuild/xmlpoke-task.md)  
 XML 파일로의 XPath 쿼리에 의해 지정된 대로 값을 반환합니다.  
  
 [XslTransformation 작업](../msbuild/xsltransformation-task.md)  
 XSLT(*Extensible Stylesheet Language Transformation*) 또는 컴파일된 XSLT 및 출력을 사용하여 XML 입력을 출력 디바이스 또는 파일로 변환합니다.  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [작업 작성](../msbuild/task-writing.md)   
 [작업](../msbuild/msbuild-tasks.md)
