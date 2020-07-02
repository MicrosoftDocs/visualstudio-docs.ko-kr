---
title: ProjectItem 요소 (Visual Studio 프로젝트 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 943f50823892e3cd942709bdcd4556b65c006b58
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770303"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 요소 (Visual Studio 프로젝트 템플릿)
프로젝트 템플릿에 포함 되는 파일을 지정 합니다.

> [!NOTE]
> `ProjectItem`요소는 템플릿이 프로젝트 또는 항목에 대 한 것인지에 따라 서로 다른 특성을 허용 합니다. 이 항목에서는 프로젝트 템플릿의 요소에 대해 설명 합니다 `ProjectItem` . `ProjectItem`항목 템플릿에 대 한 요소에 대 한 설명은 [ProjectItem 요소 (Visual Studio 항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)를 참조 하세요.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<ProjectItem>

## <a name="syntax"></a>구문

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| 특성 | 설명 |
|---------------------| - |
| `TargetFileName` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 프로젝트 항목의 이름과 경로를 지정 합니다. 이 특성은 템플릿 *.zip* 파일의 디렉터리 구조와 다른 디렉터리 구조를 만들거나 매개 변수 대체를 사용 하 여 항목 이름을 만드는 데 유용 합니다. |
| `ReplaceParameters` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때이 항목에 대체 해야 하는 매개 변수 값이 있는지 여부를 지정 하는 부울 값입니다. 기본값은 `false`입니다. |
| `OpenInEditor` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 해당 편집기에서 항목을 열어야 하는지 여부를 지정 하는 부울 값입니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .<br /><br /> `OpenInWebBrowser`및 `OpenInHelpBrowser` 특성은 값이 인 항목에서 무시 됩니다 `OpenInEditor` `true` .<br /><br /> 기본값은 `false`입니다. |
| `OpenInWebBrowser` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 해당 항목을 웹 브라우저에서 열지 여부를 지정 하는 부울 값입니다.<br /><br /> 프로젝트에 로컬인 HTML 파일 및 텍스트 파일만 웹 브라우저에서 열 수 있습니다. 이 특성을 사용 하 여 외부 Url을 열 수 없습니다.<br /><br /> 기본값은 `false`입니다. |
| `OpenInHelpBrowser` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 도움말 뷰어에서 항목을 열어야 하는지 여부를 지정 하는 부울 값입니다.<br /><br /> 프로젝트에 로컬인 HTML 파일 및 텍스트 파일만 도움말 브라우저에서 열 수 있습니다. 이 특성을 사용 하 여 외부 Url을 열 수 없습니다.<br /><br /> 기본값은 `false`입니다. |
| `OpenOrder` | 선택적 특성입니다.<br /><br /> 각 편집기에서 항목을 열 순서를 나타내는 숫자 값을 지정 합니다. 모든 값은 10의 배수 여야 합니다. 값이 더 높은 항목이 `OpenOrder` 먼저 열립니다. |

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|프로젝트에 추가할 파일 또는 디렉터리를 지정 합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 `string`템플릿 *.zip* 파일에 있는 파일의 이름 또는 경로를 나타내는입니다.

## <a name="remarks"></a>설명
 `ProjectItem`은의 선택적 자식 요소입니다 `Project` .

 `TargetFileName`특성을 사용 하 여 template *.zip* 파일의 디렉터리 구조와 다른 디렉터리 구조를 만들 수 있습니다. 예를 *들어 파일을* 파일의 루트에 있는 경우에는 파일을 템플릿에서 *만든* 모든 프로젝트에서 *customfiles* 라는 디렉터리에 배치 하려는 경우에는 다음 XML을 사용 합니다.

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 `TargetFileName`특성을 사용 하 여 파일 이름에 국제 문자를 포함 하는 파일의 이름을 바꿀 수도 있습니다. 예를 들어 *, .zip 파일* 에는 유니코드 문자를 포함 하는 파일 이름이 포함 될 수 없으므로 *.zip* 파일로 압축 하려면 먼저 파일의 이름을 바꿔야 합니다. `TargetFileName`특성은 파일 이름을 원래 유니코드 파일 이름으로 다시 설정 하는 데 사용할 수 있습니다.

 특성을 사용 하 여 매개 변수를 사용 하 여 `TargetFileName` 파일 이름을 바꿀 수도 있습니다. 다음 절차에서는 프로젝트 이름에 따라 파일 이름에 *.zip* 파일의 루트 디렉터리에 있는 *MyFile*파일의 이름을 바꾸는 방법을 설명 합니다.

### <a name="to-rename-files-with-parameters"></a>매개 변수를 사용 하 여 파일 이름을 바꾸려면

1. *.Vstemplate* 파일에서 다음 XML을 사용 합니다.

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. 텍스트 편집기 또는에서 프로젝트 파일 (*.vbproj* )을 엽니다 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

3. 프로젝트 파일에서 다음 XML과 비슷한 줄을 찾습니다.

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. 코드 줄을 다음 XML로 바꿉니다.

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    이 템플릿에서 프로젝트가 생성 되 면 파일 이름은 사용자가 **새 프로젝트** 대화 상자에서 입력 한 이름에 따라 모든 안전 하지 않은 문자 및 공백이 제거 됩니다. 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조 하세요.

## <a name="example"></a>예제
 다음 예제에서는 응용 프로그램에 대 한 프로젝트 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
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
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [ProjectItem 요소 (Visual Studio 항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)
