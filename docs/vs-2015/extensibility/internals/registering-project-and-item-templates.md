---
title: 프로젝트 템플릿 및 항목 템플릿 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a06e7a292d960e675ad4b0de97499557542fef1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185832"
---
# <a name="registering-project-and-item-templates"></a>프로젝트 템플릿 및 항목 템플릿 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 형식은 프로젝트 및 프로젝트 항목 템플릿이 있는 디렉터리를 등록 해야 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 형식과 연결 된 등록 정보를 사용 하 여 **새 프로젝트 추가** 및 **새 항목 추가** 대화 상자에 표시할 항목을 결정 합니다.  
  
 템플릿에 대 한 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)를 참조 하세요.  
  
## <a name="registry-entries-for-projects"></a>프로젝트에 대 한 레지스트리 항목  
 다음 예에서는 HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *Version*>에 있는 레지스트리 항목을 보여 줍니다. 해당 표에서는 예제에 사용 된 요소에 대해 설명 합니다.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Name|유형|설명|  
|----------|----------|-----------------|  
|@|REG_SZ|이 종류의 프로젝트 기본 이름입니다.|  
|DisplayName|REG_SZ|패키지에 등록 된 위성 DLL에서 검색할 이름의 리소스 ID입니다.|  
|패키지|REG_SZ|패키지에 등록 된 패키지의 클래스 ID입니다.|  
|Project템플릿 디렉터리|REG_SZ|프로젝트 템플릿 파일의 기본 경로입니다. 프로젝트 템플릿 파일은 **새 프로젝트** 템플릿에 의해 표시 됩니다.|  
  
### <a name="registering-item-templates"></a>항목 템플릿 등록  
 항목 템플릿을 저장할 디렉터리를 등록 해야 합니다.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Name|유형|설명|  
|----------|----------|-----------------|  
|@|REG_SZ|항목 템플릿 추가의 리소스 ID입니다.|  
|템플릿 디렉터리|REG_SZ|**새 항목 추가** 마법사의 대화 상자에 표시 되는 프로젝트 항목의 경로입니다.|  
|TemplatesLocalizedSubDir|REG_SZ|지역화 된 템플릿을 포함 하는 템플릿 디렉터리의 하위 디렉터리 이름을 나타내는 문자열의 리소스 ID입니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]는 위성 dll (있는 경우)에서 문자열 리소스를 로드 하므로 각 위성 dll은 다른 지역화 된 하위 디렉터리 이름을 포함할 수 있습니다.|  
|SortPriority|REG_DWORD|**새 항목 추가** 대화 상자에서 템플릿이 표시 되는 순서를 제어 하려면 sortpriority를 설정 합니다. SortPriority 값이 크면 템플릿 목록에 앞에 표시 됩니다.|  
  
### <a name="registering-file-filters"></a>파일 필터 등록  
 필요에 따라 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 파일 이름을 묻는 메시지가 표시 될 때에서 사용 하는 필터를 등록할 수 있습니다. 예를 들어 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] **파일 열기** 대화 상자에 대 한 필터는 다음과 같습니다.  
  
 **Visual c # 파일 ( \* .cs, \* .resx, \* settings, \* .xsd, \* .wsdl); \* . cs, \* .resx, \* settings, \* .xsd, \* .wsdl)**  
  
 여러 필터의 등록을 지원 하기 위해 각 필터는 HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < *Version*> \projects \\ { \<*ProjectGUID*> } \projects \\ < *하위 키*>의 고유한 하위 키에 등록 됩니다. 하위 키 이름은 임의로입니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하위 키의 이름을 무시 하 고 해당 값만 사용 합니다.  
  
 다음 표와 같이 플래그를 설정 하 여 필터를 사용 하는 컨텍스트를 제어할 수 있습니다. 필터에 설정 된 플래그가 없으면 **기존 항목 추가** 대화 상자 및 **파일 열기** 대화 상자에서 일반 필터 뒤에 나열 되며 파일 **에서 찾기** 대화 상자에서 사용 되지 않습니다.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Name|유형|설명|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG_DWORD|**파일에서 찾기** 대화 상자에서 필터를 일반 필터 중 하나로 만듭니다. 공통 필터는 필터 목록에 나열 된 필터 보다 먼저 표시 됩니다.|  
|CommonOpenFilesFilter|REG_DWORD|**파일 열기** 대화 상자에서 필터를 일반 필터 중 하나로 만듭니다. 공통 필터는 필터 목록에 나열 된 필터 보다 먼저 표시 됩니다.|  
|FindInFilesFilter|REG_DWORD|**파일에서 찾기** 대화 상자에서 일반 필터 뒤에 오는 필터를 나열 합니다.|  
|NotOpenFileFilter|REG_DWORD|는 **파일 열기** 대화 상자에서 필터를 사용 하지 않음을 나타냅니다.|  
|NotAddExistingItemFilter|REG_DWORD|필터가 **기존 항목 추가** 대화 상자에서 사용 되지 않음을 나타냅니다.|  
|SortPriority|REG_DWORD|필터가 표시 되는 순서를 제어 하는 SortPriority를 설정 합니다. 더 큰 SortPriority 값이 필터 목록에서 앞에 표시 됩니다.|  
  
## <a name="directory-structure"></a>디렉터리 구조  
 Vspackage는 IDE (통합 개발 환경)를 통해 위치를 등록 하기만 하면 로컬 또는 원격 디스크의 어디에 나 템플릿 파일 및 폴더를 넣을 수 있습니다. 그러나 조직의 편의를 위해 제품의 설치 경로에서 다음과 같은 디렉터리 구조를 권장 합니다.  
  
 \Templates  
  
 \Projects (프로젝트 템플릿 포함)  
  
 \Applications  
  
 \Components  
  
 \ ...  
  
 \ProjectItems (프로젝트 항목 포함)  
  
 \Class  
  
 \Form  
  
 \Web 페이지  
  
 \HelperFiles (다중 파일 프로젝트 항목에서 사용 되는 파일 포함)  
  
 \WizardFiles  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [마법사로](../../extensibility/internals/wizards.md)   
 [응용 프로그램 지역화](../../ide/localizing-applications.md)   
 [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
