---
title: '방법: 수동으로 웹 템플릿 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4bf604e747158c651f284c6463c2c2f65ae3c47a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651809"
---
# <a name="how-to-manually-create-web-templates"></a>방법: 수동으로 웹 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

웹 템플릿을 만드는 것은 다른 종류의 템플릿을 만드는 것과 다릅니다. 웹 프로젝트 템플릿은 **새 웹 사이트 추가** 대화 상자에 나타나고 웹 프로젝트 항목은 프로그래밍 언어에 따라 분류 되므로 .vstemplate 파일은 템플릿을 웹 템플릿으로 지정 하 고 프로그래밍 언어를 식별 해야 합니다.

> [!NOTE]
> 웹 템플릿은 `Project` 요소의 `File` 특성을 사용하여 지정된 빈 .webproj 파일을 포함해야 합니다. 웹 프로젝트에는 프로젝트 파일이 필요하지 않지만 웹 템플릿이 제대로 작동하기 위해서는 이 파일이 필요합니다.

### <a name="to-manually-create-a-web-template"></a>웹 템플릿을 수동으로 만들려면

1. 웹 프로젝트를 만듭니다.

2. 프로젝트에서 파일을 수정 또는 삭제하거나 프로젝트에 새 파일을 추가합니다.

3. XML 파일을 만들고 .vstemplate 파일 확장명을 사용하여 프로젝트와 같은 디렉터리에 저장합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 프로젝트에 추가하지 마세요.

4. 프로젝트 템플릿 메타데이터를 제공하도록 .vstemplate XML 파일을 작성합니다. 자세한 내용은 다음 섹션의 예제를 참조하세요.

5. .vstemplate 파일에서 `ProjectType` 요소를 찾고 텍스트 값을 `Web`으로 설정합니다.

6. `ProjectType` 요소 다음에 `ProjectSubType` 요소를 추가하고 텍스트 값을 템플릿의 프로그래밍 언어로 설정합니다. 프로그래밍 언어는 다음 값 중 하나일 수 있습니다.

   - CSharp

   - VisualBasic

     예를 들어:

   ```
   <TemplateData>
       ...
       <ProjectType>Web</ProjectType>
       <ProjectSubType>CSharp</ProjectSubType>
       ...
   </TemplateData>
   ```

7. 템플릿(.vstemplate 파일 포함)에 있는 파일을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 **보내기**를 클릭하고 **압축(ZIP) 폴더**를 클릭합니다. 파일이 .zip 파일로 압축됩니다.

8. .Zip 템플릿 파일을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 템플릿 디렉터리에 배치합니다. 기본적으로 이 디렉터리는 \My Documents\Visual Studio *Version*\My Exported Templates\\에 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 웹 프로젝트 템플릿에 대한 기본 .vstemplate 파일을 보여 줍니다.

```
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
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

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
