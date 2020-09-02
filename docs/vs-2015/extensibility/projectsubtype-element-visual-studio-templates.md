---
title: ProjectSubType 형식 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d07a62027b494242d3c25aba00fbd5f4d75df78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193916"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿을 요소에 지정 된 값의 하위 범주로 분류 합니다 `ProjectType` .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectSubType>  
  
## <a name="syntax"></a>구문  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 이 값은 템플릿의 하위 범주를 지정 합니다.  
  
## <a name="remarks"></a>설명  
 `ProjectSubType`은 `TemplateData`의 선택적 자식 요소입니다.  
  
 `ProjectSubType`요소는 [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) 요소에 하위 범주를 제공 합니다. 이 값은 다음을 포함할 수 있습니다.  
  
- `SmartDevice-NETCFv1`: 템플릿이 버전 1.0을 대상으로 하도록 지정 합니다 [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
- `SmartDevice-NETCFv2`: Tempalate 버전 2.0를 대상으로 지정 합니다 [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
  템플릿에 `ProjectType` 값이 인 요소가 포함 된 경우 `Web` `ProjectSubType` 요소는 템플릿의 프로그래밍 언어를 지정 합니다. 이 요소에는 다음 값을 사용할 수 있습니다.  
  
- `CSharp`: 템플릿에서 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 웹 프로젝트 또는 항목을 생성 하도록 지정 합니다.  
  
- `VisualBasic`: 템플릿에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 웹 프로젝트 또는 항목을 생성 하도록 지정 합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 버전 2.0을 대상으로 하는 장치 응용 프로그램의 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[Compact](../includes/compact-md.md)] .  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [ProjectType 요소(Visual Studio 템플릿)](../extensibility/projecttype-element-visual-studio-templates.md)
