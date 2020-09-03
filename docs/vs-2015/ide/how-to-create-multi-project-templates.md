---
title: '방법: 다중 프로젝트 템플릿 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1de155b71e82bb7561030cae2e1d0d4d777c9586
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668068"
---
# <a name="how-to-create-multi-project-templates"></a>방법: 다중 프로젝트 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다중 프로젝트 템플릿은 두 개 이상의 프로젝트에 대한 컨테이너로 사용됩니다. **새 프로젝트** 대화 상자에서 다중 프로젝트 템플릿에 기반하는 프로젝트를 만든 경우 템플릿의 모든 프로젝트를 솔루션에 추가합니다.

 다중 프로젝트 템플릿에는 .zip 파일로 압축된 다음 항목이 포함되어야 합니다.

- 전체 다중 프로젝트 템플릿에 대한 루트 .vstemplate 파일입니다. 이 루트 .vstemplate 파일은 **새 프로젝트** 대화 상자에서 표시하는 메타데이터를 포함하고, 이 템플릿에서 프로젝트의 .vstemplate 파일을 찾을 위치를 지정합니다. 이 파일은 .zip 파일의 루트에 있어야 합니다.

- 전체 프로젝트 템플릿에 필요한 파일이 포함된 하나 이상의 폴더입니다. 여기에는 프로젝트의 모든 코드 파일 및 프로젝트의 .vstemplate 파일이 포함됩니다.

  예를 들어 두 개의 프로젝트가 포함된 다중 프로젝트 템플릿 .zip 파일에는 다음 파일 및 디렉터리가 있을 수 있습니다.

  MultiProjectTemplate.vstemplate

  \Project1\Project1.vstemplate

  \Project1\Project1.vbproj

  \Project1\Class.vb

  \Project2\Project2.vstemplate

  \Project2\Project2.vbproj

  \Project2\Class.vb

  다중 프로젝트 템플릿의 루트 .vstemplate 파일은 다음과 같은 점에서 단일 프로젝트 템플릿과 다릅니다.

- `VSTemplate` 요소의 `Type` 특성에는 `ProjectGroup` 값이 포함됩니다. 예를 들면 다음과 같습니다.

  ```
  <VSTemplate Version="2.0.0" Type="ProjectGroup"
      xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
  ```

- `TemplateContent` 요소에는 포함된 프로젝트의 .vstemplate 파일에 대한 경로를 정의하는 하나 이상의 `ProjectTemplateLink` 요소를 가진 `ProjectCollection` 요소가 포함됩니다. 예를 들면 다음과 같습니다.

  ```
  <TemplateContent>
      <ProjectCollection>
          <ProjectTemplateLink>
              Project1\Project1.vstemplate
          </ProjectTemplateLink>
          <ProjectTemplateLink>
              Project2\Project2.vstemplate
          </ProjectTemplateLink>
      </ProjectCollection>
  </TemplateContent>
  ```

  또한 다중 프로젝트 템플릿은 일반 템플릿 다르게 작동합니다. 다중 프로젝트 템플릿에는 다음과 같은 고유한 특징이 있습니다.

- 다중 프로젝트 템플릿에 있는 개별 프로젝트는 **새 프로젝트** 대화 상자에서 이름을 할당할 수 없습니다. 대신`ProjectTemplateLink` 요소의 `ProjectName` 특성을 사용하여 각 프로젝트의 이름을 지정합니다. 자세한 내용은 다음 섹션의 첫 번째 예제를 참조하세요.

- 다중 프로젝트 템플릿에는 다른 언어로 작성된 프로젝트가 포함될 수 있지만 전체 템플릿 자체는 `ProjectType` 요소를 사용하여 하나의 범주에만 배치될 수 있습니다.

### <a name="to-create-a-multi-project-template"></a>다중 프로젝트 템플릿을 만들려면

1. 다중 프로젝트 템플릿에 포함할 프로젝트를 만듭니다.

2. 모든 프로젝트에 .vstemplate 파일을 만듭니다. 자세한 내용은 [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md)를 참조 하세요.

3. 다중 프로젝트 템플릿의 메타데이터를 포함하는 루트 .vstemplate 파일을 만듭니다. 자세한 내용은 다음 섹션의 첫 번째 예제를 참조하세요.

4. 템플릿에 포함할 파일 및 폴더를 선택하고 선택 영역을 마우스 오른쪽 단추로 클릭한 다음 **보내기**를 클릭하고 **압축(ZIP) 폴더**를 클릭합니다. 파일 및 폴더가 .zip 파일로 압축됩니다.

5. .Zip 템플릿 파일을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 템플릿 디렉터리에 배치합니다. 기본적으로 이 디렉터리는 \My Documents\Visual Studio *Version*\Templates\ProjectTemplates\\입니다.

## <a name="example"></a>예
 이 예제에서는 기본 다중 프로젝트 루트 .vstemplate 파일을 보여줍니다. 이 예제에서 템플릿에는 `My Windows Application` 프로젝트와 `My Class Library` 프로젝트가 들어 있습니다. `ProjectName` 요소의 `ProjectTemplateLink` 특성은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 이 프로젝트에 할당할 이름을 설정합니다. `ProjectName` 특성이 없으면 .vstemplate 파일의 이름이 프로젝트 이름으로 사용됩니다.

```
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example"></a>예
 이 예제에서는 `SolutionFolder` 요소를 사용하여 프로젝트를 `Math Classes` 및 `Graphics Classes`의 두 그룹으로 나눕니다. 이 템플릿에는 각 솔루션 폴더에 2개가 포함되는 4개의 프로젝트가 포함되어 있습니다.

```
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md) [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md) [Visual studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md) [솔루션 폴더 요소 (Visual Studio 템플릿)](../extensibility/solutionfolder-element-visual-studio-templates.md) [projecttemplatelink 요소 (visual studio 템플릿)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
