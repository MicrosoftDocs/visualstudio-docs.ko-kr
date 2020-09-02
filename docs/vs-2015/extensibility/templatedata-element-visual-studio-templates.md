---
title: Templates Data 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 209d8066d232c63364a045aee6b8dd2153033666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186448"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.  
  
 \<VSTemplate>  
 \<TemplateData>  
  
## <a name="syntax"></a>구문  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[이름](../extensibility/name-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 템플릿의 이름을 지정 합니다.|  
|[설명](../extensibility/description-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 템플릿에 대 한 설명을 지정 합니다.|  
|[아이콘과](../extensibility/icon-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿에 대 한 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 아이콘 역할을 하는 이미지 파일의 경로와 파일 이름을 지정 합니다.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자의 지정 된 그룹 아래에 표시 되도록 프로젝트 템플릿을 분류 합니다.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자의 지정 된 하위 범주 아래에 표시 되도록 프로젝트 템플릿을 분류 합니다.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿 ID를 지정 합니다.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿 그룹 ID를 지정 합니다.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 된 것 처럼 동일한 범주의 다른 템플릿 간에 템플릿을 정렬 하는 데 사용 되는 값을 지정 합니다.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트를 인스턴스화할 때 포함 하는 폴더를 만들지 여부를 지정 합니다.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트 또는 항목을 만들 때 Visual Studio 프로젝트 시스템에서 생성 하는 이름을 지정 합니다.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> Visual Studio 프로젝트 시스템에서 프로젝트 또는 항목을 만들 때 기본 이름을 생성할지 여부를 지정 합니다.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트를 임시 프로젝트로 만들 수 있는지 여부를 지정 합니다.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 사용자가 새 프로젝트가 저장 되는 기본 디렉터리를 쉽게 수정할 수 있도록 **새 프로젝트** 대화 상자에서 **찾아보기** 단추를 사용할 수 있는지 여부를 지정 합니다.|  
|[숨김](../extensibility/hidden-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 템플릿이 나타나는지 여부를 지정 합니다.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자에 템플릿이 표시 되는 부모 범주 수를 지정 합니다.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|선택적 요소입니다.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자의 **위치** 텍스트 상자를 프로젝트 템플릿에 대해 사용, 사용 안 함 또는 숨길지 여부를 지정 합니다.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿이 .NET Framework의 특정 최소 버전 및 이후 버전 (있는 경우)만 지 원하는 경우이 요소를 사용 합니다.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿에서 웹 프로젝트에 대 한 마스터 페이지를 지원할지 여부를 지정 합니다.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 웹 프로젝트에 대해 템플릿에서 코드 분리를 지원할지, 아니면 코드에서 페이지 모델을 지원할지를 지정 합니다.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 템플릿이 여러 언어에 대해 동일한 지 여부 및 **새 프로젝트** 대화 상자에서 **언어** 옵션을 사용할 수 있는지 여부를 지정 합니다.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|선택적 요소입니다.<br /><br /> 프로젝트 템플릿의 대상 플랫폼을 지정합니다. 이 요소는 프로젝트 템플릿을 사용 하 여 앱을 만들도록 지정 합니다 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] .|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대 한 모든 메타 데이터를 포함 합니다.|  
  
## <a name="remarks"></a>설명  
 `TemplateData` 는 필수 요소입니다.  
  
 선택적 요소를 포함 하지 않는 경우 해당 요소에 대 한 기본값이 사용 됩니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
