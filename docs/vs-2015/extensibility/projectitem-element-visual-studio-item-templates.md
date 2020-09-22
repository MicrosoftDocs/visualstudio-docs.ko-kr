---
title: ProjectItem 요소 (Visual Studio 항목 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4778603278bf07dc7b0a45544b4835d2ed2cbf8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841374"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem 요소(Visual Studio 항목 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목 템플릿에 포함 되는 파일을 지정 합니다.  
  
> [!NOTE]
> `ProjectItem`요소는 템플릿이 프로젝트 또는 항목에 대 한 것인지에 따라 서로 다른 특성을 허용 합니다. 이 항목에서는 `ProjectItem` 항목에 대 한 요소에 대해 설명 합니다. `ProjectItem`프로젝트 템플릿에 대 한 요소에 대 한 설명은 [ProjectItem 요소 (Visual Studio 프로젝트 템플릿)](../extensibility/projectitem-element-visual-studio-project-templates.md)를 참조 하세요.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectItem>  
  
## <a name="syntax"></a>구문  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|`SubType`|선택적 특성입니다.<br /><br /> 다중 파일 항목 템플릿에서 항목의 하위 유형을 지정 합니다. 이 값은 항목을 여는 데 사용할 편집기를 결정 하는 데 사용 됩니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`CustomTool`|선택적 특성입니다.<br /><br /> 프로젝트 파일의 항목에 대 한 사용자 지정 도구를 설정 합니다.|  
|`ItemType`|선택적 특성입니다.<br /><br /> 프로젝트 파일의 항목에 대 한 ItemType을 설정 합니다.|  
|`ReplaceParameters`|선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때이 항목에 대체 해야 하는 매개 변수 값이 있는지 여부를 지정 하는 부울 값입니다. 기본값은 `false`입니다.|  
|`TargetFileName`|선택적 특성입니다.<br /><br /> 템플릿에서 만든 항목의 이름을 지정 합니다. 이 특성은 매개 변수 대체를 사용 하 여 항목 이름을 만드는 데 유용 합니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|템플릿의 내용을 지정 합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 `string`템플릿 .zip 파일의 파일 이름을 나타내는입니다.  
  
## <a name="remarks"></a>설명  
 `ProjectItem` 은의 선택적 자식 요소입니다 `TemplateContent` .  
  
 `TargetFileName`특성을 사용 하 여 매개 변수를 사용 하 여 파일 이름을 바꿀 수 있습니다. 예를 들어 파일이 `MyFile.vb` template .zip 파일의 루트 디렉터리에 있지만 **새 항목 추가** 대화 상자에서 사용자가 제공한 파일 이름에 따라 파일 이름을 지정 하려는 경우 다음 XML을 사용 합니다.  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 이 템플릿에서 항목이 생성 되 면 파일 이름은 사용자가 **새 항목 추가** 대화 상자에 입력 한 이름을 기반으로 합니다. 다중 파일 항목 템플릿을 만들 때 유용 합니다. 자세한 내용은 [방법: 다중 파일 항목 템플릿](../ide/how-to-create-multi-file-item-templates.md) 및 [템플릿 매개 변수](../ide/template-parameters.md)만들기를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 클래스의 표준 항목 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)   
 [방법: 다중 파일 항목 템플릿 만들기](../ide/how-to-create-multi-file-item-templates.md)   
 [템플릿 매개 변수](../ide/template-parameters.md)
