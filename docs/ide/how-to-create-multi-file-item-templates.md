---
title: 다중 파일 항목 템플릿 만들기
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 4a4f0c50fc0a3fe21da560356d3551ca85ef9d66
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284427"
---
# <a name="how-to-create-multi-file-item-templates"></a>방법: 다중 파일 항목 템플릿 만들기

항목 템플릿은 하나의 항목만 지정할 수 있지만 항목이 여러 파일로 구성되는 경우가 있습니다. 예를 들어 Windows Forms 항목 템플릿에는 다음 3개 파일이 필요합니다.

- 양식에 대한 코드가 들어 있는 파일

- 양식에 대한 디자이너 정보가 들어 있는 파일

- 양식에 대한 포함 리소스가 들어 있는 파일

다중 파일 항목 템플릿에는 항목을 만들 때 올바른 파일 확장명을 사용하도록 매개 변수가 필요합니다. **템플릿 내보내기 마법사**를 사용하여 다중 파일 항목 템플릿을 만드는 경우 이러한 매개 변수가 자동으로 생성되므로 더 이상 편집할 필요가 없습니다.

## <a name="use-the-export-template-wizard"></a>템플릿 내보내기 마법사 사용

단일 파일 항목 템플릿과 동일한 방식으로 다중 파일 항목 템플릿을 만들 수 있습니다. [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)를 참조하세요. 마법사의 **내보낼 항목 선택** 페이지에서 종속 파일(예: Windows Forms 양식 파일)을 가진 파일을 선택합니다. 마법사에서 디자이너 및 리소스 파일과 같은 종속 파일을 템플릿에 자동으로 포함합니다.

## <a name="manually-create-a-multi-file-item-template"></a>수동으로 다중 파일 항목 템플릿 만들기

1. 단일 파일 항목 템플릿을 수동으로 만들 때처럼 항목 템플릿을 만들되, 다중 파일 항목을 구성 하는 각 파일을 포함합니다.

1. *.vstemplate* XML 파일에서 각 개별 파일에 대한 `ProjectItem` 요소를 추가하고 이 요소에 `TargetFileName` 특성을 추가합니다. `TargetFileName` 특성 값을 *$fileinputname$.FileExtension*으로 설정합니다. 여기서 *FileExtension*은 템플릿에 포함될 파일의 파일 확장명입니다. 예를 들어:

    ```xml
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

     > [!NOTE]
     > 이 템플릿에서 파생된 항목이 프로젝트에 추가되면 파일 이름은 사용자가 **새 항목 추가** 대화 상자에 입력한 이름에서 파생됩니다.

1. 템플릿에 포함할 파일을 선택하고 마우스 오른쪽 단추를 클릭한 다음 **보내기** > **압축(ZIP) 폴더**를 선택합니다.

   선택한 파일이 *.zip* 파일로 압축됩니다.

1. *.zip* 파일을 사용자 항목 템플릿 위치에 복사합니다. 기본적으로 이 디렉터리는 *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*입니다. 자세한 내용은 [방법: 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조하세요.

1. Visual Studio를 종료한 다음 다시 엽니다.

1. 새 프로젝트를 만들거나 기존 프로젝트를 연 다음, **프로젝트** > **새 항목 추가**를 선택하거나 **Ctrl**+**Shift**+**A**를 누릅니다.

   **새 항목 추가** 대화 상자에 다중 파일 항목 템플릿이 나타납니다.

## <a name="example"></a>예제

다음 예제에서는 Windows Forms 템플릿을 보여 줍니다. 이 템플릿을 기반으로 항목이 생성되면 생성된 3개 파일의 이름은 **새 항목 추가** 대화 상자에 입력된 이름과 일치합니다.

```xml
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

## <a name="see-also"></a>참조

- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [방법: 템플릿의 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)
