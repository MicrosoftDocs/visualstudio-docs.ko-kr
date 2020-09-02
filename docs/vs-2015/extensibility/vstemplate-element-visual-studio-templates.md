---
title: .Vstemplate 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8219f12eed091858a43c2bd5092b8b06f8320bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422902"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대 한 모든 메타 데이터를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Type`|템플릿을 프로젝트 템플릿 또는 항목 템플릿으로 식별 합니다. 이 특성의 값은 또는가 될 수 있습니다 `Project` `Item` .|  
|`Version`|템플릿에 대 한 버전 번호를 지정 합니다. 및의 템플릿에는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] `Version` 특성 값이 `3.0.0` 있습니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류 하 고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 방법을 정의 하는 데이터를 지정 합니다.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿의 내용을 지정 합니다.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|선택적 요소입니다.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|선택적 요소입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
 없음  
  
## <a name="remarks"></a>설명  
 `VSTemplate`요소는 .vstemplate 파일의 루트 요소입니다.  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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
