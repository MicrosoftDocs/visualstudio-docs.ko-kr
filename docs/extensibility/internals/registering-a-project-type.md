---
title: 프로젝트 유형 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05ac1f393632934f193f5f4efaaf9e5459ffbb14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705879"
---
# <a name="registering-a-project-type"></a>프로젝트 형식 등록
새 프로젝트 유형을 만들 때 프로젝트 유형을 인식하고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 작업할 수 있는 레지스트리 항목을 만들어야 합니다. 일반적으로 레지스트리 스크립트(.rgs) 파일을 사용하여 이러한 레지스트리 항목을 만듭니다.

 아래 예제에서 레지스트리의 문은 해당하는 경우 기본 경로 및 데이터를 제공하고 각 문에 대한 레지스트리 스크립트의 항목을 포함하는 테이블을 제공합니다. 표는 스크립트 항목과 명령문에 대한 추가 정보를 제공합니다.

> [!NOTE]
> 다음 레지스트리 정보는 프로젝트 유형을 등록하기 위해 작성할 레지스트리 스크립트의 항목 유형 및 목적의 예가 될 것입니다. 실제 항목및 용도는 프로젝트 유형의 특정 요구 사항에 따라 다를 수 있습니다. 사용 가능한 샘플을 검토하여 개발 중인 프로젝트 유형과 매우 유사한 샘플을 찾은 다음 해당 샘플의 레지스트리 스크립트를 검토해야 합니다.

 다음 예제는 HKEY_CLASSES_ROOT.

## <a name="example"></a>예제

```
\.figp
   @="FigPrjFile"
   "Content Type"="text/plain"
\.figp\ShellNew
   "NullFile"=""
\FigPrjFile
   @="Figure Project File"
\DefaultIcon
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"
\shell\open
   @="&Open in Visual Studio"
\shell\open\command
   @="devenv.exe \"%1\""
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrjFile`|.figp라는 확장명이 있는 프로젝트 유형 파일의 이름 및 설명입니다.|
|`Content Type`|REG_SZ|`Text/plain`|프로젝트 파일의 콘텐츠 유형입니다.|
|`NullFile`|REG_SZ|`Null`||
|`@`|REG_SZ|`%MODULE%,-206`|이 유형의 프로젝트에 사용되는 기본 아이콘입니다. %MODULE% 문은 프로젝트 유형 DLL의 기본 위치로 레지스트리에서 완료됩니다.|
|`@`|REG_SZ|`&Open in Visual Studio`|이 프로젝트 유형이 열리는 기본 응용 프로그램입니다.|
|`@`|REG_SZ|`devenv.exe "%1"`|이 유형의 프로젝트가 열릴 때 실행되는 기본 명령입니다.|

 다음 예제는 HKEY_LOCAL_MACHINE 키 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\패키지]의 레지스트리에 있습니다.

## <a name="example"></a>예제

```
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)
   @="FigPrj Project Package"
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"
   "CompanyName"="Microsoft"
   "ProductName"="Figure Project Sample"
   "ProductVersion"="9.0"
   "MinEdition"="professional"
   "ID"=dword:00000001
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL
   "DllName"="FigPrjUI.dll"
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation
   "FigProjects"=""
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`(기본값)|REG_SZ|`FigPrj Project VSPackage`|이 등록된 VSPackage(프로젝트 유형)의 지역화 가능한 이름입니다.|
|`InprocServer32`|REG_SZ|`%MODULE%`|프로젝트 유형 DLL의 경로입니다. IDE는 이 DLL을 로드하고 VSPackage `DllGetClassObject` CLSID를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 전달하여 <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 개체를 생성합니다.|
|`CompanyName`|REG_SZ|`Microsoft`|프로젝트 유형을 개발한 회사의 이름입니다.|
|`ProductName`|REG_SZ|`Figure Project Sample`|프로젝트 유형의 이름입니다.|
|`ProductVersion`|REG_SZ|`9.0`|프로젝트 유형 릴리스의 버전 번호입니다.|
|`MinEdition`|REG_SZ|`professional`|등록 중인 VS패키지 에디션입니다.|
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|프로젝트 VSPackage의 패키지 로드 키입니다. 환경이 시작된 후 프로젝트가 로드될 때 키의 유효성이 검사됩니다.|
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|프로젝트 유형에 대한 지역화된 리소스가 포함된 위성 DLL의 파일 이름입니다.|
|`Path`|REG_SZ|`%RESOURCE_PATH%`|위성 DLL의 경로입니다.|
|`FigProjectsEvents`|REG_SZ|값에 대한 문을 참조하십시오.|이 자동화 이벤트에 대해 반환된 텍스트 문자열을 확인합니다.|
|`FigProjectItemsEvents`|REG_SZ|값에 대한 문을 참조하십시오.|이 자동화 이벤트에 대해 반환된 텍스트 문자열을 확인합니다.|

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\프로젝트]의 레지스트리에 있습니다.

## <a name="example"></a>예제

```
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)
   @="FigPrj Project"
   "DisplayName"="#2"
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"
   "DisplayProjectFileExtensions"="#3"
   "PossibleProjectExtensions"="figp"
   "DefaultProjectExtension"=".figp"
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)
   @="#4"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000000
   "FindInFilesFilter"=dword:00000000
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2
      (Folder 2 contains settings for Find in Files filters.)
   @="#5"
   "CommonOpenFilesFilter"=dword:00000000
   "CommonFindFilesFilter"=dword:00000000
   "NotAddExistingItemFilter"=dword:00000001
   "FindInFilesFilter"=dword:00000001
   "NotOpenFileFilter"=dword:00000000
   "SortPriority"=dword:000003e8
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`FigPrj Project`|이 유형의 프로젝트의 기본 이름입니다.|
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|패키지에 등록된 위성 DLL에서 검색할 이름의 리소스 ID입니다.|
|`Package`|REG_SZ|`%CLSID_Package%`|패키지에 등록된 VSPackage의 클래스 ID입니다.|
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|프로젝트 템플릿 파일의 기본 경로입니다. 새 프로젝트 템플릿에 표시되는 파일입니다.|
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|프로젝트 항목 템플릿 파일의 기본 경로입니다. 새 항목 추가 템플릿에 표시되는 파일입니다.|
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE가 **열기** 대화 상자를 구현할 수 있도록 합니다.|
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE에서 열리는 프로젝트가 이 프로젝트 유형(프로젝트 팩터리)에서 처리되는지 여부를 결정하는 데 사용됩니다. 두 개 이상의 항목에 대한 형식은 세미콜론 으로 구분된 목록입니다. 예를 들어 "vdproj;vdp".|
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE에서 Save As 작업의 기본 파일 이름 확장명으로 사용합니다.|
|`Filter Settings`|REG_DWORD|다양한, 다음 표문과 코멘트를 참조하십시오.|이러한 설정은 UI 대화 상자에 파일을 표시하기 위한 다양한 필터를 설정하는 데 사용됩니다.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|항목 템플릿 추가를 위한 리소스 ID입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|새 항목 **추가** 템플릿의 대화 상자에 표시되는 프로젝트 항목의 경로입니다.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**새 항목 추가** 대화 상자에 표시되는 파일의 트리 노드에서 정렬 순서를 결정합니다.|

 다음 표에서는 이전 코드 세그먼트에서 사용할 수 있는 필터 옵션을 보여 주실 수 있습니다.

|필터 옵션|설명|
|-------------------|-----------------|
|`CommonFindFilesFilter`|필터가 **파일에서 찾기** 대화 상자의 일반적인 필터 중 하나임을 나타냅니다. 공통 필터는 필터가 공통으로 표시되지 않기 전에 필터 목록에 나열됩니다.|
|`CommonOpenFilesFilter`|필터가 **파일 열기** 대화 상자의 일반적인 필터 중 하나임을 나타냅니다. 공통 필터는 필터가 공통으로 표시되지 않기 전에 필터 목록에 나열됩니다.|
|`FindInFilesFilter`|필터가 **파일에서 찾기** 대화 상자의 필터 중 하나가 되고 공통 필터 아래에 나열됨을 나타냅니다.|
|`NotOpenFileFilter`|파일 **열기** 대화 상자에서 필터가 사용되지 않음을 나타냅니다.|
|`NotAddExistingItemFilter`|**기존 항목** 추가 대화 상자에서 필터를 사용하지 않음을 나타냅니다.|

 기본적으로 필터에 이러한 플래그가 하나 이상 설정되어 있지 않으면 **기존 항목 추가** 대화 상자와 공통 필터가 나열된 후 파일 **열기** 대화 상자에 필터가 사용됩니다. 필터는 **파일에서 찾기** 대화 상자에서 사용되지 않습니다.

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\프로젝트]의 레지스트리에 있습니다.

## <a name="example"></a>예제

```
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|새 프로젝트 템플릿에 대한 리소스 ID입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|등록된 프로젝트 유형의 프로젝트에 대한 기본 경로입니다.|
|`SortPriority`|REG_DWORD|`41 (x29)`|새 프로젝트 마법사 대화 상자에 표시되는 프로젝트의 정렬 순서를 설정합니다.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0은 이 유형의 프로젝트가 새 프로젝트 대화 상자에만 표시된다는 것을 나타냅니다.|

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\프로젝트]의 레지스트리에 있습니다.

## <a name="example"></a>예제

```
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)
   @="Miscellaneous Files Project"
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1
                                 (CLSID for Figures Project projects)
   @="#6"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"
   "SortPriority"=dword:00000064
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|None|다음 항목이 기타 파일 프로젝트 항목에 대한 기본값입니다.|
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|새 항목 추가 템플릿 파일에 대한 리소스 ID 값입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|새 항목 **추가** 대화 상자에 표시될 항목의 기본 경로입니다.|
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**새 항목 추가** 대화 상자의 트리 노드에 표시할 정렬 순서를 설정합니다.|

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\메뉴]의 레지스트리에 있습니다.

## <a name="example"></a>예제

```
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"
```

 메뉴 항목은 IDE를 메뉴 정보를 검색하는 데 사용되는 리소스로 가리킵니다. 이 데이터가 메뉴 데이터베이스에 병합되면 레지스트리의 MenusMerged 섹션에 동일한 키가 추가됩니다. VSPackage는 MenusMerged 섹션 아래의 아무 것도 직접 수정해서는 안 됩니다. 다음 표의 데이터 필드에는 세 개의 쉼표로 구분된 필드가 있습니다. 첫 번째 필드는 메뉴 리소스 파일의 전체 경로를 식별합니다.

- 첫 번째 필드를 생략하면 VSPackage GUID로 식별된 위성 DLL에서 메뉴 리소스가 로드됩니다.

  두 번째 필드는 CTMENU 형식의 메뉴 리소스 ID를 식별합니다.

- 리소스 ID가 지정되고 파일 경로가 첫 번째 매개 변수에 의해 제공되면 전체 파일 경로에서 메뉴 리소스가 로드됩니다.

- 리소스 ID가 제공되지만 파일 경로가 없는 경우 메뉴 리소스는 위성 DLL에서 로드됩니다.

- 전체 파일 경로가 제공되고 리소스 ID가 생략된 경우 로드할 파일은 CTO 파일이 될 것으로 예상됩니다.

  마지막 필드는 CTMENU 리소스의 버전 번호를 식별합니다. 버전 번호를 변경하여 메뉴를 다시 병합할 수 있습니다.

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|%CLSID_Package%|REG_SZ|`,1000,1`|메뉴 정보를 검색할 리소스입니다.|

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplate]라는 키 아래의 레지스트리에 있습니다.

```
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)
   @="#7"
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"
   "SortPriority"=dword:00000029
   "NewProjectDialogOnly"=dword:00000000
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|그림 프로젝트 새 프로젝트 템플릿의 리소스 ID 값입니다.|
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|새 프로젝트 디렉터리기본 경로입니다. 이 디렉터리에 있는 항목은 **새 프로젝트 마법사** 대화 상자에 표시됩니다.|
|`SortPriority`|REG_DWORD|`41 (x29)`|**새** 프로젝트 대화 상자의 트리 노드에 프로젝트가 표시될 순서를 설정합니다.|
|`NewProjectDialogOnly`|REG_DWORD|`0`|0은 이 유형의 프로젝트가 새 **프로젝트** 대화 상자에만 표시된다는 것을 나타냅니다.|

 다음 예제는 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts]라는 키 아래의 레지스트리에 있습니다.

```
\FiguresProductSample
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"
   "UseInterface"=dword:00000001
```

|이름|형식|데이터|설명|
|----------|----------|----------|-----------------|
|`Package`|REG_SZ|`%CLSID_Package%`|등록된 VSPackage의 클래스 ID입니다.|
|`UseInterface`|REG_DWORD|`1`|1은 UI가 이 프로젝트와 상호 작용하는 데 사용된다는 것을 나타냅니다. 0은 UI 인터페이스가 없음을 나타냅니다.|

 새 프로젝트 형식을 제어하는 the.vsz 파일에는 RELATIVE_PATH 항목이 포함되어 있는 경우가 많습니다. 이 경로는 다음 설치 키에서 프로젝트 유형의 \ProductDir 항목 아래에 지정된 경로를 기준으로 합니다.

 HKEY_LOCAL_MACHINE\소프트웨어\마이크로소프트\비주얼 스튜디오\7.0Exp\설치

 예를 들어 엔터프라이즈 프레임워크 프로젝트 템플릿은 다음 레지스트리 항목을 추가합니다.

 HKEY_LOCAL_MACHINE\SOFTWARE\마이크로소프트\비주얼 스튜디오\7.0Exp\설치\EF\ProductDir = C:\프로그램 파일\마이크로소프트 비주얼 스튜디오\엔터프라이즈프레임 프레임 워크\

 즉, .vsz 파일에 PROJECT_TYPE=EF 항목을 포함하는 경우 환경은 이전에 지정한 ProductDir 디렉터리에서 .vsz 파일을 찾습니다.

## <a name="see-also"></a>참조
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
