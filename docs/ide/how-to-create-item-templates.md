---
title: 항목 템플릿 만들기
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 0a0d4122d36c0946b6c1c98ef0f1523ce35751a6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284479"
---
# <a name="how-to-create-item-templates"></a>방법: 항목 템플릿 만들기

이 문서에서는 **템플릿 내보내기 마법사**를 사용하여 항목 템플릿을 만드는 방법을 보여줍니다. 템플릿이 여러 파일로 구성되는 경우 [방법: 다중 파일 항목 템플릿 만들기](../ide/how-to-create-multi-file-item-templates.md)를 참조하세요.

## <a name="add-an-item-template-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 항목 템플릿 추가

1. Visual Studio에서 프로젝트를 만들거나 엽니다.

1. 프로젝트에 항목을 추가한 후 원하는 경우 수정합니다.

1. 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 수정합니다. 자세한 내용은 [방법: 템플릿 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)를 참조하세요.

1. **프로젝트** 메뉴에서 **템플릿 내보내기**를 선택합니다.

1. **템플릿 형식 선택** 페이지에서 선택 **항목 템플릿**을 선택하고 해당 항목을 포함하는 프로젝트를 선택하고 **다음**을 선택합니다.

1. **내보낼 항목 선택** 페이지에서 템플릿을 만들 항목을 선택한 후 **다음**을 선택합니다.

1. **항목 참조 선택** 페이지에서 템플릿에 포함할 어셈블리 참조를 선택한 후 **다음**을 선택합니다.

1. **템플릿 옵션 선택** 페이지에서, 템플릿 이름 및 설명(옵션), 아이콘 이미지 및 미리 보기 이미지를 입력한 다음 **마침**을 선택합니다.

    템플릿 파일은 *.zip* 파일에 추가되고 마법사에서 지정한 디렉터리에 복사됩니다. 기본 위치는 *%USERPROFILE%\Documents\Visual Studio \<version\>\My Exported Templates*입니다.

1. **템플릿 내보내기 마법사**에서 **템플릿을 자동으로 Visual Studio로 가져오기** 옵션을 선택하지 않은 경우 내보낸 템플릿을 찾습니다. 그런 다음, 사용자 항목 템플릿 디렉터리에 복사합니다. 기본 위치는 *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ItemTemplates*입니다.

1. Visual Studio를 종료한 다음 다시 엽니다.

1. 새 프로젝트를 만들거나 기존 프로젝트를 연 다음, **프로젝트** > **새 항목 추가**를 선택하거나 **Ctrl**+**Shift**+**A**를 누릅니다.

   **새 항목 추가** 대화 상자에 항목 템플릿이 나타납니다. **템플릿 내보내기 마법사**에서 설명을 추가한 경우 대화 상자의 오른쪽에 설명이 나타납니다.

## <a name="enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>유니버설 Windows 앱 프로젝트에서 사용할 항목 템플릿 활성화

마법사에서 기본 템플릿 만들기에 대한 많은 작업을 수행하지만 대부분의 경우 템플릿을 내보낸 후 *.vstemplate* 파일을 수동으로 수정해야 합니다. 예를 들어 항목을 유니버설 Windows 앱 프로젝트의 **새 항목 추가** 대화 상자에 표시하려면 몇 가지 추가 단계를 수행해야 합니다.

1. 이전 섹션의 단계에 따라 항목 템플릿을 내보냅니다.

1. 생성된 *.zip* 파일을 추출하고, Visual Studio에서 *.vstemplate* 파일을 엽니다.

1. C# 유니버설 Windows 프로젝트의 경우 `<TemplateData>` 요소 내에 다음과 같은 XML을 추가합니다.

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. Visual Studio에서 *.vstemplate* 파일을 저장한 다음, 닫습니다.

1. *.zip* 파일에 *.vstemplate* 파일을 다시 복사하여 붙여넣습니다.

     **파일 복사** 대화 상자가 나타나면 **복사하는 파일로 대상 파일 덮어쓰기** 옵션을 선택합니다.

이제 **새 항목 추가** 대화 상자에서 이 템플릿을 기반으로 한 항목을 유니버설 Windows 프로젝트에 추가할 수 있습니다.

## <a name="enable-templates-for-specific-project-subtypes"></a>특정 프로젝트 하위 형식에 템플릿 사용

Windows, Office, 대시보드 또는 웹과 같은 특정 프로젝트 하위 유형에만 템플릿이 표시되도록 지정할 수 있습니다.

1. *.vstemplate* 파일에서 항목 템플릿에 대한 `ProjectType` 요소를 찾습니다.

1. [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 요소 바로 뒤에 `ProjectType` 요소를 추가합니다.

1. 요소의 텍스트 값을 다음 값 중 하나로 설정합니다.

    - Windows
    - Office
    - 데이터베이스
    - 웹

예를 들어 `<ProjectSubType>Database</ProjectSubType>`을 참조하십시오.

다음 예제에서는 **Office** 프로젝트용 항목 템플릿을 보여 줍니다.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="manually-create-an-item-template"></a>수동으로 항목 템플릿 만들기

경우에 따라 항목 템플릿을 처음부터 수동으로 만들 수 있습니다.

1. 프로젝트 및 프로젝트 항목을 만듭니다.

2. 템플릿으로 저장할 준비가 될 때까지 프로젝트 항목을 수정합니다.

3. 해당되는 경우 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 수정합니다. 매개 변수 대체에 대한 자세한 내용은 [방법: 템플릿 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)를 참조하세요.

4. XML 파일을 만들고 *.vstemplate* 파일 확장명을 사용하여 프로젝트 항목 파일과 같은 디렉터리에 저장합니다.

5. 항목 템플릿 메타데이터를 제공하도록 *.vstemplate* XML 파일을 편집합니다. 자세한 내용은 [템플릿 스키마 참조(확장성)](../extensibility/visual-studio-template-schema-reference.md) 및 이전 섹션의 예제를 참조하세요.

6. *.vstemplate* 파일을 저장한 다음, 닫습니다.

7. **Windows 탐색기**에서 템플릿에 포함하려는 파일을 선택합니다. 마우스 오른쪽 단추를 클릭한 다음, **보내기** > **압축(ZIP) 폴더**를 선택합니다. 선택한 파일이 *.zip* 파일로 압축됩니다.

::: moniker range="vs-2017"

8. *.zip* 파일을 복사하여 사용자 항목 템플릿 위치에 붙여넣습니다. 기본 디렉터리는 *%USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates*입니다. 자세한 내용은 [방법: 프로젝트 템플릿과 항목 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조하세요.

::: moniker-end

::: moniker range=">=vs-2019"

8. *.zip* 파일을 복사하여 사용자 항목 템플릿 위치에 붙여넣습니다. 기본 디렉터리는 *%USERPROFILE%\Documents\Visual Studio 2019\Templates\ItemTemplates*입니다. 자세한 내용은 [방법: 프로젝트 템플릿과 항목 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조하세요.

::: moniker-end

## <a name="see-also"></a>참조

- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 다중 파일 항목 템플릿 만들기](../ide/how-to-create-multi-file-item-templates.md)
- [Visual Studio 템플릿 스키마 참조(확장성)](../extensibility/visual-studio-template-schema-reference.md)
