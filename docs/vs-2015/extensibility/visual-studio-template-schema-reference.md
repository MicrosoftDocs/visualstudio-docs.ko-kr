---
title: Visual Studio 템플릿 스키마 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a15a08dc674940897bf465946efd2ec350cc7c42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422125"
---
# <a name="visual-studio-template-schema-reference"></a>Visual Studio 템플릿 스키마 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에는 프로젝트 템플릿, 항목 템플릿 및 시작 키트에 대한 메타데이터를 저장하는 파일인 .vstemplate 파일의 XML 요소에 대한 정보가 포함되어 있습니다.  
  
 vstemplate.xsd를 사용하여 사용자 지정 .vstemplate 파일의 유효성을 검사할 수 있습니다. 이 파일은에서 \\ 사용할 수 있습니다. *Visual Studio 설치 폴더*\Xml\Schemas\1033\vstemplate.xsd.  
  
|요소|자식 요소|특성|  
|-------------|--------------------|----------------|  
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|없음|없음|  
|[Assembly(템플릿)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|  
|[Assembly(마법사 확장명)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|Name<br /><br /> 값|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|  
|[설명](../extensibility/description-element-visual-studio-templates.md)|--|패키지<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|  
|[폴더](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> 폴더|Name|  
||[사용되지 않음]|--|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|  
|[숨김](../extensibility/hidden-element-visual-studio-templates.md)|--|--|  
|[아이콘과](../extensibility/icon-element-visual-studio-templates.md)|--|패키지<br /><br /> ID|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|  
|[이름](../extensibility/name-element-visual-studio-templates.md)|--|패키지<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|  
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|폴더<br /><br /> ProjectItem|파일<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|  
|[ProjectItem(항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|하위 유형<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem(프로젝트 템플릿)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|  
|[참조](../extensibility/reference-element-visual-studio-templates.md)|어셈블리|--|  
|[참조](../extensibility/references-element-visual-studio-templates.md)|참고|--|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|버전|  
|[SDKReference](../extensibility/sdkreference-element-visual-studio-templates.md)|--|패키지|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Name|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Project<br /><br /> 참조<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Name<br /><br /> 설명<br /><br /> 아이콘<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> 숨김<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|형식<br /><br /> 버전|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|Name|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|어셈블리<br /><br /> FullClassName|--|  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)   
 [방법: 시작 키트 만들기](../ide/how-to-create-starter-kits.md)