---
title: 웹 템플릿 만들기
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 6870143be825469fde2be4b3448da24d54034fc1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284180"
---
# <a name="how-to-manually-create-web-templates"></a>방법: 수동으로 웹 템플릿 만들기

웹 템플릿을 만드는 것은 다른 종류의 템플릿을 만드는 것과 다릅니다. 웹 프로젝트 템플릿은 **새 웹 사이트 추가** 대화 상자에 나타나고 웹 프로젝트 항목은 프로그래밍 언어에 따라 분류되므로 *vstemplate* 파일은 템플릿을 웹 템플릿으로 지정하고 프로그래밍 언어를 식별해야 합니다.

> [!NOTE]
> 웹 템플릿에는 빈 *.webproj* 파일이 포함되어 있어야 하고, 이 파일은 *vstemplate* 파일에서 `Project` 요소의 `File` 특성에 참조되어야 합니다. 웹 프로젝트에는 *.proj* 프로젝트 파일이 필요하지 않지만 이 스텁 파일을 만들어야 웹 템플릿이 올바르게 작동합니다.

## <a name="to-manually-create-a-web-template"></a>웹 템플릿을 수동으로 만들려면

1. 웹 프로젝트를 만듭니다.

2. 프로젝트에서 파일을 수정 또는 삭제하거나 프로젝트에 새 파일을 추가합니다.

3. XML 파일을 만들고 *vstemplate* 파일 이름 확장명을 사용하여 프로젝트와 같은 디렉터리에 저장합니다. Visual Studio에서 프로젝트에 추가하지 마세요.

4. 프로젝트 템플릿 메타데이터를 제공하도록 *vstemplate* XML 파일을 편집합니다. 자세한 내용은 [다음에 나오는 예제](#example)를 참조하세요.

5. *vstemplate* 파일에서 `ProjectType` 요소를 찾고 텍스트 값을 `Web`으로 설정합니다.

6. `ProjectType` 요소 다음에 `ProjectSubType` 요소를 추가하고 텍스트 값을 템플릿의 프로그래밍 언어로 설정합니다. 프로그래밍 언어는 다음 값 중 하나일 수 있습니다.

   - CSharp
   - VisualBasic

     예를 들어:

     ```xml
     <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
     </TemplateData>
     ```

7. 템플릿(*vstemplate* 파일 포함)에 있는 파일을 선택하고 마우스 오른쪽 단추를 클릭한 다음, **보내기** > **압축(ZIP) 폴더**를 선택합니다. 파일이 *.zip* 파일로 압축됩니다.

8. *.zip* 템플릿 파일을 Visual Studio 프로젝트 템플릿 디렉터리에 배치합니다. 기본적으로 이 디렉터리는 *%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates*입니다.

## <a name="example"></a>예제

다음 예제에서는 웹 프로젝트 템플릿에 대한 기본 *vstemplate* 파일을 보여줍니다.

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참조

- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿 스키마 참조(확장성)](../extensibility/visual-studio-template-schema-reference.md)
