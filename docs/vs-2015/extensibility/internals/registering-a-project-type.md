---
title: 프로젝트 형식 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e0140b752adda02aba6126580ec08ee1f7536a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843360"
---
# <a name="registering-a-project-type"></a>프로젝트 형식 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

새 프로젝트 형식을 만들 때에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 형식을 인식 하 고 사용할 수 있도록 하는 레지스트리 항목을 만들어야 합니다. 일반적으로 레지스트리 스크립트 (.rgs) 파일을 사용 하 여 이러한 레지스트리 항목을 만듭니다.  
  
 아래 예제에서 레지스트리의 문은 기본 경로와 데이터를 제공 하 고, 각 문에 대 한 레지스트리 스크립트의 항목이 포함 된 테이블을 제공 합니다. 테이블은 스크립트 항목 및 문에 대 한 추가 정보를 제공 합니다.  
  
> [!NOTE]
> 다음 레지스트리 정보는 프로젝트 형식을 등록 하기 위해 작성 하는 레지스트리 스크립트 항목의 유형 및 용도에 대 한 예입니다. 실제 항목과 해당 사용의 용도는 프로젝트 형식에 대 한 특정 요구 사항에 따라 달라질 수 있습니다. 사용 가능한 샘플을 검토 하 여 개발 중인 프로젝트의 형식과 유사한 항목을 찾은 다음 해당 샘플에 대 한 레지스트리 스크립트를 검토 해야 합니다.  
  
 다음은 HKEY_CLASSES_ROOT의 예입니다.  
  
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
  
|이름|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|확장명이. p p 인 프로젝트 형식 파일의 이름 및 설명입니다.|  
|`Content Type`|REG_SZ|`Text/plain`|프로젝트 파일에 대 한 콘텐츠 형식입니다.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|이 형식의 프로젝트에 사용 되는 기본 아이콘입니다. % MODULE% 문이 레지스트리에서 프로젝트 형식 DLL의 기본 위치로 완료 되었습니다.|  
|`@`|REG_SZ|`&Open in Visual Studio`|이 프로젝트 형식이 열리는 기본 응용 프로그램입니다.|  
|`@`|REG_SZ|`devenv.exe "%1"`|이 형식의 프로젝트를 열 때 실행 되는 기본 명령입니다.|  
  
 다음 예는 HKEY_LOCAL_MACHINE에서 가져온 것 이며 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages] 키 아래에 있습니다.  
  
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
  
|이름|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`(기본값)|REG_SZ|`FigPrj Project VSPackage`|이 등록 된 VSPackage의 지역화할 수 있는 이름 (프로젝트 형식)입니다.|  
|`InprocServer32`|REG_SZ|`%MODULE%`|프로젝트 형식 DLL의 경로입니다. IDE는이 DLL을 로드 하 고 VSPackage CLSID를로 전달 하 여 `DllGetClassObject` <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> 개체를 생성 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 합니다.|  
|`CompanyName`|REG_SZ|`Microsoft`|프로젝트 형식을 개발한 회사의 이름입니다.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|프로젝트 형식에 대 한 이름입니다.|  
|`ProductVersion`|REG_SZ|`9.0`|프로젝트 형식 릴리스의 버전 번호입니다.|  
|`MinEdition`|REG_SZ|`professional`|등록 중인 VSPackage의 버전입니다.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|VSPackage 프로젝트에 대 한 패키지 로드 키입니다. 환경이 시작 된 후 프로젝트가 로드 되 면 키의 유효성이 검사 됩니다.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|프로젝트 형식에 대 한 지역화 된 리소스를 포함 하는 위성 DLL의 파일 이름입니다.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|위성 DLL의 경로입니다.|  
|`FigProjectsEvents`|REG_SZ|Value에 대 한 문을 참조 하세요.|이 자동화 이벤트에 대해 반환 되는 텍스트 문자열을 결정 합니다.|  
|`FigProjectItemsEvents`|REG_SZ|Value에 대 한 문을 참조 하세요.|이 자동화 이벤트에 대해 반환 되는 텍스트 문자열을 결정 합니다.|  
  
 다음 모든 예제는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 키 아래에 있습니다.  
  
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
  
|이름|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|이 형식의 기본 프로젝트 이름입니다.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|패키지에 등록 된 위성 DLL에서 검색할 이름의 리소스 ID입니다.|  
|`Package`|REG_SZ|`%CLSID_Package%`|패키지에 등록 된 VSPackage의 클래스 ID입니다.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|프로젝트 템플릿 파일의 기본 경로입니다. 새 프로젝트 템플릿에 표시 되는 파일입니다.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|프로젝트 항목 템플릿 파일의 기본 경로입니다. 새 항목 추가 템플릿에 표시 되는 파일입니다.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|IDE에서 **열기** 대화 상자를 구현할 수 있도록 합니다.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|IDE에서 열려는 프로젝트가이 프로젝트 형식 (프로젝트 팩터리)에서 처리 되는지 여부를 확인 하는 데 사용 됩니다. 둘 이상의 항목에 대 한 형식은 세미콜론으로 구분 된 목록입니다. 예: ".vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|IDE에서 다른 이름으로 저장 작업의 기본 파일 이름 확장명으로 사용 됩니다.|  
|`Filter Settings`|REG_DWORD|다양 한 정보는 다음 표를 참조 하세요.|이러한 설정은 UI 대화 상자에 파일을 표시 하는 다양 한 필터를 설정 하는 데 사용 됩니다.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|항목 템플릿 추가의 리소스 ID입니다.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**새 항목 추가** 템플릿에 대 한 대화 상자에 표시 되는 프로젝트 항목의 경로입니다.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**새 항목 추가** 대화 상자에 표시 되는 파일의 트리 노드에서 정렬 순서를 결정 합니다.|  
  
 다음 표에서는 이전 코드 세그먼트에서 사용할 수 있는 필터 옵션을 보여 줍니다.  
  
|필터 옵션|Description|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|필터가 **파일에서 찾기** 대화 상자에 있는 일반 필터 중 하나 임을 나타냅니다. 공통 필터는 필터 목록에 나열 된 필터 보다 먼저 표시 됩니다.|  
|`CommonOpenFilesFilter`|필터가 **파일 열기** 대화 상자의 일반 필터 중 하나 임을 나타냅니다. 공통 필터는 필터 목록에 나열 된 필터 보다 먼저 표시 됩니다.|  
|`FindInFilesFilter`|필터가 **파일에서 찾기** 대화 상자에 있는 필터 중 하나 이며 일반 필터 뒤에 표시 되는 것을 나타냅니다.|  
|`NotOpenFileFilter`|는 **파일 열기** 대화 상자에서 필터를 사용 하지 않음을 나타냅니다.|  
|`NotAddExistingItemFilter`|**기존 항목** 추가 대화 상자에서 필터를 사용 하지 않음을 나타냅니다.|  
  
 기본적으로 필터에 이러한 플래그를 하나 이상 설정 하지 않으면 **기존 항목 추가** 대화 상자와 공통 필터가 나열 된 후 **파일 열기** 대화 상자에서 필터가 사용 됩니다. 이 필터는 **파일에서 찾기** 대화 상자에서 사용 되지 않습니다.  
  
 다음 모든 예제는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 키 아래에 있습니다.  
  
## <a name="example"></a>예제  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|이름|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|새 프로젝트 템플릿에 대 한 리소스 ID입니다.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|등록 된 프로젝트 형식의 프로젝트에 대 한 기본 경로입니다.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|새 프로젝트 마법사 대화 상자에 표시 되는 프로젝트의 정렬 순서를 설정 합니다.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0은이 형식의 프로젝트가 새 프로젝트 대화 상자에만 표시 됨을 나타냅니다.|  
  
 다음 모든 예제는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects] 키 아래에 있습니다.  
  
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
  
|이름|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|없음|다음 항목이 기타 파일 프로젝트 항목에 대 한 것임을 나타내는 기본값입니다.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|새 항목 추가 템플릿 파일에 대 한 리소스 ID 값입니다.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|**새 항목 추가** 대화 상자에 표시 되는 항목의 기본 경로입니다.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|**새 항목 추가** 대화 상자의 트리 노드에 표시 하기 위한 정렬 순서를 설정 합니다.|  
  
 다음 예는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus] 키 아래에 있습니다.  
  
## <a name="example"></a>예제  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 메뉴 항목은 메뉴 정보를 검색 하는 데 사용 되는 리소스에 대 한 IDE를 가리킵니다. 이 데이터가 메뉴 데이터베이스에 병합 되 면 레지스트리의 MenusMerged 섹션에 동일한 키가 추가 됩니다. VSPackage는 MenusMerged 섹션 아래의 항목을 직접 수정 하면 안 됩니다. 다음 표의 데이터 필드에는 세 개의 쉼표로 구분 된 필드가 있습니다. 첫 번째 필드는 메뉴 리소스 파일의 전체 경로를 식별 합니다.  
  
- 첫 번째 필드를 생략 하면 VSPackage GUID로 식별 되는 위성 DLL에서 메뉴 리소스가 로드 됩니다.  
  
  두 번째 필드는 CTMENU 형식의 메뉴 리소스 ID를 식별 합니다.  
  
- 리소스 ID를 지정 하 고 첫 번째 매개 변수에서 파일 경로를 제공 하면 메뉴 리소스가 전체 파일 경로에서 로드 됩니다.  
  
- 리소스 ID를 제공 하지만 파일 경로가이 아닌 경우 위성 DLL에서 메뉴 리소스가 로드 됩니다.  
  
- 전체 파일 경로를 제공 하 고 리소스 ID를 생략 하면 로드할 파일은 CTO 파일 이어야 합니다.  
  
  마지막 필드는 CTMENU 리소스의 버전 번호를 식별 합니다. 버전 번호를 변경 하 여 메뉴를 다시 병합할 수 있습니다.  
  
|Name|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|% CLSID_Package%|REG_SZ|`,1000,1`|메뉴 정보를 검색할 리소스입니다.|  
  
 다음 모든 예제는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates] 키 아래에 있습니다.  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Name|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|그림 프로젝트의 새 프로젝트 템플릿에 대 한 리소스 ID 값입니다.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|새 프로젝트 디렉터리의 기본 경로입니다. 이 디렉터리의 항목은 **새 프로젝트 마법사** 대화 상자에 표시 됩니다.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|**새 프로젝트** 대화 상자의 트리 노드에 프로젝트가 표시 되는 순서를 설정 합니다.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0은이 형식의 프로젝트가 **새 프로젝트** 대화 상자에만 표시 됨을 나타냅니다.|  
  
 다음 예는 레지스트리의 [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts] 키 아래에 있습니다.  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Name|유형|데이터|Description|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|등록 된 VSPackage의 클래스 ID입니다.|  
|`UseInterface`|REG_DWORD|`1`|1은 UI가이 프로젝트와 상호 작용 하는 데 사용 됨을 나타냅니다. 0은 UI 인터페이스가 없음을 나타냅니다.|  
  
 새 프로젝트 형식을 제어 하는 .vsz 파일에는 RELATIVE_PATH 항목이 포함 되는 경우가 많습니다. 이 경로는 다음 설정 키에 있는 프로젝트 형식의 \ProductDir 항목에 지정 된 경로를 기준으로 합니다.  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 예를 들어, 엔터프라이즈 프레임 워크 프로젝트 템플릿은 다음 레지스트리 항목을 추가 합니다.  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 즉, .vsz 파일에 PROJECT_TYPE = EF 항목을 포함 하는 경우 환경은 이전에 지정한 제품 디렉터리 디렉터리에서 .vsz 파일을 찾습니다.  
  
## <a name="see-also"></a>참고 항목  
 [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)   
 [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
