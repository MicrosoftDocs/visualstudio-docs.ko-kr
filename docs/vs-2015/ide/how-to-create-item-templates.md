---
title: '방법: 항목 템플릿 만들기 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9edc79002a4a2d7c2fe135d7eb4669f5f010599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668070"
---
# <a name="how-to-create-item-templates"></a>방법: 항목 템플릿 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목 [첫 번째 절차](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box)의 단계에서는 **템플릿 내보내기** 마법사를 사용하여 항목 템플릿을 만드는 방법을 보여 줍니다. 템플릿이 여러 파일로 구성 되는 경우 [방법: 다중 파일 항목 템플릿 만들기](../ide/how-to-create-multi-file-item-templates.md)를 참조 하세요.

 마법사에서 기본 템플릿 만들기에 대한 많은 작업을 수행하지만 대부분의 경우 템플릿을 내보낸 후 .vstemplate 파일을 수동으로 수정해야 합니다. 예를 들어 항목을 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 프로젝트의 **새 항목 추가** 대화 상자에 표시하려면 몇 가지 추가 단계를 수행해야 합니다. 이 항목의 [두 번째 절차](#to-enable-the-item-template-to-be-used-in-a-store-project)에 따라 해당 작업을 수행할 수 있습니다.

 경우에 따라 항목 템플릿을 처음부터 수동으로 만들어야 하거나 만들 수 있습니다. [세 번째 절차](#to-enable-templates-for-specific-project-sub-types)에서는 이 작업 방법을 보여 줍니다.

 .vstemplate 파일에 사용할 수 있는 요소에 대한 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조하세요.

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>사용자 지정 프로젝트 항목 템플릿을 새 항목 추가 대화 상자에 추가하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 프로젝트를 만들거나 엽니다.

2. 항목을 프로젝트에 추가한 후 원하는 경우 수정합니다.

3. 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 수정합니다. 자세한 내용은 [방법: 템플릿에서 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)를 참조 하세요.

4. **파일** 메뉴에서 **템플릿 내보내기**를 클릭합니다.

5. **항목 템플릿**을 클릭하고 항목을 포함하는 프로젝트를 선택한 후 **다음**을 클릭합니다.

6. 템플릿을 만들 항목을 선택하고 **다음**을 클릭합니다.

7. 템플릿에 포함할 어셈블리 참조를 선택한 후 **다음**을 클릭합니다.

8. 아이콘 파일 이름, 미리 보기 이미지, 템플릿 이름 및 템플릿 설명을 입력한 다음 **마침**을 클릭합니다.

     템플릿 파일은 .zip 파일에 추가되고 대화 상자에서 지정한 디렉터리에 복사됩니다. 기본 위치는 **.입니다. \Users \\<username \> \Documents\visual Studio \<Version> \My에서 내보낸 \\ 템플릿** 폴더입니다.

    > [!WARNING]
    > 이전 버전의 Visual Studio에서 기본 위치는 **.입니다. \Users \\<username \> \Documents\visual Studio \<Version> \Templates\ItemTemplates**를 입력 합니다.

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>항목 템플릿을 저장소 프로젝트에서 사용할 수 있도록 하려면

1. 위 절차의 단계에 따라 항목 템플릿을 내보냅니다.

2. ..\Users\\*username*\Documents\Visual Studio *Version*\Templates\ItemTemplates\(또는 **My Exported Templates**) 폴더에 복사된 .zip 파일에서 .vstemplate 파일을 추출합니다.

3. Visual Studio에서 .vstemplate 파일을 엽니다.

4. Windows 8.1 저장소 C# 프로젝트의 경우 .vstemplate 파일에 다음 XML을 열고 닫는 `<TemplateData>` 태그(`<TemplateGroupID>WinRT-Managed</TemplateGroupID>`)로 묶어 추가합니다.

    C++ Windows 8.1 스토어 프로젝트에서는 `WinRT-Native-6.3` 값을 사용합니다. Windows 10 및 기타 프로젝트 유형의 경우 [TemplateGroupID 요소(Visual Studio 템플릿)](../extensibility/templategroupid-element-visual-studio-templates.md)를 참조하세요.

    다음 예제에서는 XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` 행이 추가된 이후 .vstemplate 파일의 전체 내용을 보여 줍니다. 이 예제는 C# 프로젝트에만 적용됩니다. 및 요소를 수정 \<ProjectType> \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> 하 여 다른 언어 및 프로젝트 형식을 지정할 수 있습니다.

   ```xml
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
     <TemplateData>
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>
       <Name>MyItemStoreTemplate</Name>
       <Description>This is an example itemtemplate</Description>
       <ProjectType>CSharp</ProjectType>
       <SortOrder>10</SortOrder>
       <Icon>__TemplateIcon.ico</Icon>
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>
     </TemplateData>
     <TemplateContent>
       <References />
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>
     </TemplateContent>
   </VSTemplate>
   ```

    가능한 다른 TemplateGroupID 값은 [TemplateGroupID 요소(Visual Studio 템플릿)](../extensibility/templategroupid-element-visual-studio-templates.md)를 참조하세요. 전체 .vstemplate 참조는 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조하세요.

5. Visual Studio에서 .vstemplate 파일을 저장한 다음 닫습니다.

6. .vstemplate 파일을 복사하여 ..\Users\\*username*\Documents\Visual Studio *Version*\Templates\ItemTemplates\ 폴더에 있는 .zip 파일에 다시 붙여넣습니다.

    **파일 복사** 대화 상자가 나타나면 **복사하는 파일로 대상 파일 덮어쓰기** 옵션을 선택합니다.

   이제 **새 항목 추가** 대화 상자에서 이 템플릿을 기반으로 한 항목을 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 프로젝트에 추가할 수 있습니다.

   매개 변수 이름에 대한 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조하세요.

### <a name="to-enable-templates-for-specific-project-sub-types"></a>특정 프로젝트 하위 유형에 템플릿을 사용하도록 설정하려면

1. 개발 환경에서는 특정 프로젝트에 대해 프로젝트 항목을 항목 추가 대화 상자에서 사용할 수 있도록 할 수 있습니다. 이 절차를 사용하여 Windows, 웹, Office 또는 데이터베이스 프로젝트에 대해 사용할 수 있는 사용자 지정 항목을 만들 수 있습니다.

    .vstemplate 파일에서 항목 템플릿에 대한 ProjectType 요소를 찾습니다.

    ProjectType 요소 바로 뒤에 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 요소를 추가합니다.

2. 요소의 텍스트 값을 다음 값 중 하나로 설정합니다.

   1. Windows

   2. Office

   3. 데이터베이스

   4. 웹

      예를 들어 `<ProjectSubType>Database</ProjectSubType>`을 참조하십시오.

      다음 예제에서는 Office 프로젝트에 사용할 수 있는 항목 템플릿을 보여 줍니다.

   ```
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

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>템플릿 내보내기 마법사를 사용하지 않고 항목 템플릿을 수동으로 만들려면

1. 프로젝트 및 프로젝트 항목을 만듭니다.

2. 템플릿으로 저장할 준비가 될 때까지 프로젝트 항목을 수정합니다.

3. 해당되는 경우 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 수정합니다. 매개 변수 대체에 대한 자세한 내용은 방법: 템플릿 매개 변수 대체를 참조하세요.

4. XML 파일을 만들고 .vstemplate 파일 확장명을 사용하여 새 항목 템플릿과 같은 디렉터리에 저장합니다.

5. 항목 템플릿 메타데이터를 제공하도록 .vstemplate XML 파일을 작성합니다. 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md) 및 이전 섹션의 예제를 참조하세요.

6. .vstemplate 파일을 저장한 다음 닫습니다.

7. Windows 탐색기에서 템플릿에 포함할 파일을 선택하고 선택 항목을 마우스 오른쪽 단추로 클릭한 다음 보내기를 클릭하고 압축(ZIP) 폴더를 클릭합니다. 선택한 파일이 .zip 파일로 압축됩니다.

8. .zip 파일을 복사하여 사용자 항목 템플릿 위치에 붙여넣습니다. Visual Studio 2015에서 기본 디렉터리는 ..\Users\\<username\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\입니다. 자세한 내용은 방법: 프로젝트 템플릿과 항목 템플릿 찾기 및 구성을 참조하세요.

## <a name="see-also"></a>관련 항목
 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md) [방법: 다중 파일 항목 템플릿 만들기](../ide/how-to-create-multi-file-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
