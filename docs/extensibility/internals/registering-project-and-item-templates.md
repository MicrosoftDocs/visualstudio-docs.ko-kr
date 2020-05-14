---
title: 프로젝트 및 항목 템플릿 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705819"
---
# <a name="registering-project-and-item-templates"></a>프로젝트 템플릿 및 항목 템플릿 등록
프로젝트 유형은 프로젝트 및 프로젝트 항목 템플릿이 있는 디렉터리를 등록해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]프로젝트 유형과 연결된 등록 정보를 사용하여 **새 프로젝트 추가** 및 새 항목 **추가** 대화 상자에 표시할 항목을 결정합니다.

 템플릿에 대한 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가를](../../extensibility/internals/adding-project-and-project-item-templates.md)참조하십시오.

## <a name="registry-entries-for-projects"></a>프로젝트에 대한 레지스트리 항목
 다음 예제에서는 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*버전*> 아래의 레지스트리 항목을 보여 준다. 함께 제공되는 표에서는 예제에 사용된 요소를 설명합니다.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|이름|Type|Description|
|----------|----------|-----------------|
|@|REG_SZ|이러한 종류의 프로젝트의 기본 이름입니다.|
|DisplayName|REG_SZ|패키지에 등록된 위성 DLL에서 검색할 이름의 리소스 ID입니다.|
|패키지|REG_SZ|패키지에 등록된 패키지의 클래스 ID입니다.|
|프로젝트템플릿디더|REG_SZ|프로젝트 템플릿 파일의 기본 경로입니다. 프로젝트 템플릿 파일은 **새 프로젝트** 템플릿에 의해 표시됩니다.|

### <a name="registering-item-templates"></a>항목 템플릿 등록
 항목 템플릿을 저장하는 디렉터리를 등록해야 합니다.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| 이름 | Type | Description |
|--------------------------|-----------| - |
| @ | REG_SZ | 항목 템플릿 추가를 위한 리소스 ID입니다. |
| 템플릿디더 | REG_SZ | 새 항목 **추가** 마법사에 대한 대화 상자에 표시되는 프로젝트 항목의 경로입니다. |
| 템플릿로컬화서브디르 | REG_SZ | 지역화된 템플릿을 포함하는 TemplatesDir의 하위 디렉터리 이름을 지정하는 문자열의 리소스 ID입니다. 위성 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL이 있는 경우 위성 DLL에서 문자열 리소스를 로드하기 때문에 각 위성 DLL에는 다른 지역화된 하위 디렉터리 이름이 포함될 수 있습니다. |
| 정렬 우선 순위 | REG_DWORD | 정렬우선 순위를 설정하여 새 **항목 추가** 대화 상자에 템플릿이 표시되는 순서를 제어합니다. 더 큰 정렬우선 순위 값은 템플릿 목록의 앞에 나타납니다. |

### <a name="registering-file-filters"></a>파일 필터 등록
 선택적으로 파일 이름을 묻는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 메시지가 표시될 때 사용하는 필터를 등록할 수 있습니다. 예를 들어 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] **파일 열기** 대화 상자의 필터는 다음과 같은 것입니다.

 **비주얼 C #\*파일\*(.cs,\*.resx, .settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 여러 필터의 등록을 지원하기 위해 각 필터는 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*버전*>\Project\<*ProjectGUID* \\<\\{ProjectGUID>}\\필터 하위*키*> 따라 자체 하위 키에 등록됩니다. 하위 키 이름은 임의입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서는 하위 키의 이름을 무시하고 해당 값만 사용합니다.

 다음 표에 표시된 플래그를 설정하여 필터가 사용되는 컨텍스트를 제어할 수 있습니다. 필터에 플래그가 설정되어 있지 않으면 **기존 항목 추가** 대화 상자및 파일 **열기** 대화 상자의 공통 필터 아래에 나열되지만 **파일에서 찾기** 대화 상자에는 사용되지 않습니다.

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

|이름|Type|Description|
|----------|----------|-----------------|
|공통 찾기 파일 필터|REG_DWORD|필터를 **파일에서 찾기** 대화 상자의 일반적인 필터 중 하나로 만듭니다. 일반적인 필터는 필터가 공통으로 표시되지 않기 전에 필터 목록에 나열됩니다.|
|공통 오픈 파일필터|REG_DWORD|필터를 **파일 열기** 대화 상자의 일반적인 필터 중 하나로 만듭니다. 일반적인 필터는 필터가 공통으로 표시되지 않기 전에 필터 목록에 나열됩니다.|
|찾기인파일필터|REG_DWORD|**파일에서 찾기** 대화 상자의 공통 필터 다음의 필터를 나열합니다.|
|열지 않음파일 필터|REG_DWORD|파일 **열기** 대화 상자에서 필터가 사용되지 않음을 나타냅니다.|
|NotAdd기존항목필터|REG_DWORD|**기존 항목 추가** 대화 상자에서 필터가 사용되지 않음을 나타냅니다.|
|정렬 우선 순위|REG_DWORD|정렬우선순위를 설정하여 필터가 표시되는 순서를 제어합니다. 더 큰 정렬우선 순위 값은 필터 목록의 앞에 나타납니다.|

## <a name="directory-structure"></a>디렉터리 구조
 VSPackage는 위치가 IDE(통합 개발 환경)를 통해 등록된 한 로컬 또는 원격 디스크의 아무 곳에나 템플릿 파일 및 폴더를 배치할 수 있습니다. 그러나 조직의 용이성을 위해 제품의 설치 경로 아래에 다음 디렉터리 구조를 권장합니다.

 \ 템플릿

 \프로젝트(프로젝트 템플릿 포함)

 \ 응용 프로그램

 \구성 요소

 \ ...

 \프로젝트항목(프로젝트 항목 포함)

 \클래스

 \양식

 \웹 페이지

 \HelperFiles (다중 파일 프로젝트 항목에 사용되는 파일 포함)

 \마법사파일

## <a name="see-also"></a>참조

- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [마법사](../../extensibility/internals/wizards.md)
- [응용 프로그램 지역화](../../ide/globalizing-and-localizing-applications.md)
- [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
