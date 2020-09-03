---
title: '방법: 다중 파일 항목 템플릿 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e70039f361ac3410a8ddcccb0f139d8bdcb32ed9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668085"
---
# <a name="how-to-create-multi-file-item-templates"></a>방법: 다중 파일 항목 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목 템플릿은 하나의 항목만 지정할 수 있지만 항목이 여러 파일로 구성되는 경우가 있습니다. 예를 들어 Visual Basic용 Windows Forms 항목 템플릿에는 다음 3개 파일이 필요합니다.

- 양식에 대한 코드가 들어 있는 .vb 파일

- 양식에 대한 디자이너 정보가 들어 있는 .designer.vb 파일

- 양식에 대한 포함 리소스가 들어 있는 .resx 파일

  다중 파일 항목 템플릿에는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 항목을 만들 때 올바른 파일 이름 확장명을 사용하도록 매개 변수가 필요합니다. **템플릿 내보내기** 마법사를 사용하여 항목 템플릿을 만드는 경우 이러한 매개 변수가 자동으로 생성되므로 더 이상 편집할 필요가 없습니다. 다음 단계에서는 매개 변수를 사용하여 올바른 파일 이름 확장명을 만드는 방법을 설명합니다.

### <a name="to-manually-create-a-multi-file-item-template"></a>다중 파일 항목 템플릿을 수동으로 만들려면

1. 단일 파일 항목 템플릿을 만드는 것처럼 항목 템플릿을 만듭니다. 자세한 내용은 [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)를 참조하세요.

2. `TargetFileName` 특성을 모든 `ProjectItem` 요소에 추가합니다. `TargetFileName` 특성 값을 $fileinputname$.*FileExtension*으로 설정합니다. 여기서 *FileExtension*은 템플릿에 포함될 파일의 파일 이름 확장명입니다. 예를 들면 다음과 같습니다.

    ```
    <ProjectItem TargetFileName="$fileinputname$.vb">
        Form1.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
        Form1.Designer.vb
    </ProjectItem>
    <ProjectItem TargetFileName="$fileinputname$.resx">
        Form1.resx
    </ProjectItem>
    ```

     이 템플릿에서 파생된 항목이 프로젝트에 추가되면 파일 이름은 사용자가 **새 항목 추가** 대화 상자에 입력한 이름을 기반으로 합니다.

3. 템플릿에 포함할 파일을 선택하고 선택 영역을 마우스 오른쪽 단추로 클릭한 다음 **보내기**를 클릭하고 **압축(ZIP) 폴더**를 클릭합니다. 선택한 파일이 .zip 파일로 압축됩니다.

4. .zip 파일을 사용자 항목 템플릿 위치에 배치합니다. 기본적으로 이 디렉터리는 \My Documents\Visual Studio *Version*\Templates\ItemTemplates\\입니다. 자세한 내용은 [방법: 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조 하세요.

## <a name="example"></a>예
 다음 예제에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Windows Forms 템플릿을 보여 줍니다. 이 템플릿을 기반으로 항목이 생성되면 생성된 3개 파일의 이름은 **새 항목 추가** 대화 상자에 입력된 이름과 일치합니다.

```
<VSTemplate Version="2.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-file Item Template</Name>
        <Icon>Icon.ico</Icon>
        <Description>An example of a multi-file item template</Description>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">
            Form1.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">
            Form1.Designer.vb
        </ProjectItem>
        <ProjectItem TargetFileName="$fileinputname$.resx">
            Form1.resx
        </ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [방법: 항목 템플릿](../ide/how-to-create-item-templates.md) [템플릿 매개 변수](../ide/template-parameters.md) 만들기 [방법: 템플릿에서 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)
