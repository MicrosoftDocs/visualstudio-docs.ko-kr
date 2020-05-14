---
title: 템플릿데이터 요소(비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699186"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 요소(Visual Studio 템플릿)
템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.

 \<VS템플릿 \<> 템플릿데이터>

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
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

| 요소 | Description |
| - | - |
| [이름](../extensibility/name-element-visual-studio-templates.md) | 필수 요소입니다.<br /><br /> **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 나타나는 템플릿의 이름을 지정합니다. |
| [설명](../extensibility/description-element-visual-studio-templates.md) | 필수 요소입니다.<br /><br /> **새 프로젝트** 또는 새 **항목 추가** 대화 상자에 나타나는 템플릿에 대한 설명을 지정합니다. |
| [아이콘](../extensibility/icon-element-visual-studio-templates.md) | 필수 요소입니다.<br /><br /> 템플릿에 대한 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 나타나는 아이콘 역할을 하는 이미지 파일의 경로 및 파일 이름을 지정합니다. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | 필수 요소입니다.<br /><br /> 새 프로젝트 대화 상자에서 지정된 그룹 아래에 표시되도록 프로젝트 템플릿을 **분류합니다.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 새 프로젝트 대화 상자에서 지정된 하위 범주 아래에 표시되도록 프로젝트 템플릿을 **분류합니다.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿 ID를 지정합니다. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿 그룹 ID를 지정합니다. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 나타나는 것과 같이 동일한 범주의 다른 템플릿 중에서 템플릿을 정렬하는 데 사용되는 값을 지정합니다. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 포함 폴더가 프로젝트 인스턴스화시 생성되는지 여부를 지정합니다. |
| [기본 이름](../extensibility/defaultname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> Visual Studio 프로젝트 시스템이 프로젝트 또는 항목을 만들 때 생성할 이름을 지정합니다. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> Visual Studio 프로젝트 시스템이 프로젝트 또는 항목이 생성될 때 프로젝트 또는 항목에 대한 기본 이름을 생성할지 여부를 지정합니다. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 프로젝트를 임시 프로젝트로 만들 수 있는지 여부를 지정합니다(Visual Studio 2017에만). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자에서 **찾아보기** 단추를 사용할 수 있는지 여부를 지정하여 사용자가 새 프로젝트가 저장된 기본 디렉터리를 쉽게 수정할 수 있도록 합니다. |
| [숨겨진](../extensibility/hidden-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 **새 프로젝트** 또는 새 항목 **추가** 대화 상자에 표시되는지 여부를 지정합니다. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자에 템플릿을 표시할 상위 범주 수를 지정합니다. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | 선택적 요소입니다. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | 선택적 요소입니다.<br /><br /> **새 프로젝트** 대화 상자의 **위치** 텍스트 상자가 프로젝트 템플릿에 대해 사용 설정, 사용 안 함 또는 숨겨져 있는지 여부를 지정합니다. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 .NET Framework의 특정 최소 버전만 지원하는 경우 이 요소를 사용하고 이후 버전(있는 경우)을 사용합니다. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 웹 프로젝트의 마스터 페이지를 지원하는지 여부를 지정합니다. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 웹 프로젝트에 대한 코드 분리또는 코드 뒤 페이지 모델을 지원하는지 여부를 지정합니다. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 템플릿이 여러 언어에 대해 동일한지 여부와 **새 프로젝트** 대화 상자에서 **언어** 옵션을 사용할 수 있는지 여부를 지정합니다. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | 선택적 요소입니다.<br /><br /> 프로젝트 템플릿의 대상 플랫폼을 지정합니다. 이 요소는 프로젝트 템플릿이 앱을 만드는 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 데 사용되도록 지정합니다. |

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|필수 요소입니다.<br /><br /> 프로젝트 템플릿, 항목 템플릿 또는 시작 키트에 대한 모든 메타데이터가 들어 있습니다.|

## <a name="remarks"></a>설명
 `TemplateData`는 필수 요소입니다.

 선택적 요소를 포함하지 않으면 해당 요소에 대한 기본값이 사용됩니다.

## <a name="example"></a>예제
 다음 예제에서는 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 합니다.

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

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
