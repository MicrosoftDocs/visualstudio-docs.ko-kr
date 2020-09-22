---
title: ProjectType 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b01dd370fe5e3d7a5207363c5ab7ec4f2a0254c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841411"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**새 프로젝트** 또는 **새 항목 추가** 대화 상자의 지정 된 그룹 아래에 나타나도록 프로젝트 템플릿을 분류 합니다.  
  
> [!WARNING]
> 프로젝트 템플릿은 Visual Studio 2012에서 시작 하는 c + +에 대해 지원 됩니다. Visual Studio 2010 이전 버전에서 c + +에 대해 지원 되지 않습니다.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>구문  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 이 값은 템플릿이 만들 프로젝트의 형식을 지정 하 고 다음 값 중 하나를 포함 해야 합니다.  
  
- `CSharp`: 템플릿이 프로젝트 또는 항목을 생성 하도록 지정 합니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
- `VisualBasic`: 템플릿이 프로젝트 또는 항목을 생성 하도록 지정 합니다 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .  
  
- `Web`: 템플릿에서 웹 프로젝트 또는 항목을 생성 하도록 지정 합니다. 요소에 `ProjectType` 이 값이 포함 된 경우 프로젝트 또는 항목의 언어가 [Projectsubtype 형식 요소 (Visual Studio 템플릿)](../extensibility/projectsubtype-element-visual-studio-templates.md)에 정의 됩니다.  
  
## <a name="remarks"></a>설명  
 `ProjectType`은 `TemplateData`의 필수 자식 요소입니다.  
  
 요소의 값은 `ProjectType` **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 있는 위치를 지정 합니다. 예를 들어 값이 인 템플릿이 `ProjectType` `CSharp` **새 프로젝트** 대화 상자의 **Visual c #** 노드 아래에 나타납니다.  
  
 템플릿 하위 유형은 [Projectsubtype 형식](../extensibility/projectsubtype-element-visual-studio-templates.md) 요소를 사용 하 여 지정할 수 있습니다.  
  
## <a name="example"></a>예제  
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
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType 요소(Visual Studio 템플릿)](../extensibility/projectsubtype-element-visual-studio-templates.md)
