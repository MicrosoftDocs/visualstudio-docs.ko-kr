---
title: 프로젝트항목 요소(비주얼 스튜디오 프로젝트 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701849"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem 요소(비주얼 스튜디오 프로젝트 템플릿)
프로젝트 템플릿에 포함된 파일을 지정합니다.

> [!NOTE]
> 이 `ProjectItem` 요소는 템플릿이 프로젝트 또는 항목에 대한 것인지 여부에 따라 다른 특성을 허용합니다. 이 항목에서는 `ProjectItem` 프로젝트 템플릿의 요소를 설명합니다. 항목 템플릿의 `ProjectItem` 요소에 대한 설명은 [ProjectItem 요소(Visual Studio 항목 템플릿)를](../extensibility/projectitem-element-visual-studio-item-templates.md)참조하십시오.

 \<VS템플릿 \<> 프로젝트항목 \<>>> \<프로젝트 콘텐츠

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

| attribute | 설명 |
|---------------------| - |
| `TargetFileName` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 프로젝트 항목의 이름과 경로를 지정합니다. 이 특성은 템플릿 *.zip* 파일의 디렉터리 구조와 다른 디렉터리 구조를 만들거나 매개 변수 대체를 사용하여 항목 이름을 만드는 데 유용합니다. |
| `ReplaceParameters` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 교체해야 하는 매개 변수 값이 항목에 있는지 여부를 지정하는 부울 값입니다. 기본값은 `false`입니다. |
| `OpenInEditor` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 해당 편집기에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 항목을 열지 여부를 지정하는 부울 값입니다.<br /><br /> `OpenInWebBrowser` 및 `OpenInHelpBrowser` 특성은 값이 있는 항목에서 `OpenInEditor` `true`무시됩니다.<br /><br /> 기본값은 `false`입니다. |
| `OpenInWebBrowser` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 항목을 웹 브라우저에서 열어야 하는지 여부를 지정하는 부울 값입니다.<br /><br /> 프로젝트에 로컬인 HTML 파일및 텍스트 파일만 웹 브라우저에서 열 수 있습니다. 이 속성으로 외부 URL을 열 수 없습니다.<br /><br /> 기본값은 `false`입니다. |
| `OpenInHelpBrowser` | 선택적 특성입니다.<br /><br /> 템플릿에서 프로젝트를 만들 때 도움말 뷰어에서 항목을 열지 여부를 지정하는 부울 값입니다.<br /><br /> 도움말 브라우저에서 프로젝트에 로컬인 HTML 파일 및 텍스트 파일만 열 수 있습니다. 이 속성으로 외부 URL을 열 수 없습니다.<br /><br /> 기본값은 `false`입니다. |
| `OpenOrder` | 선택적 특성입니다.<br /><br /> 해당 편집기에서 항목이 열릴 순서를 나타내는 숫자 값을 지정합니다. 모든 값은 10의 배수여야 합니다. 값이 더 `OpenOrder` 높은 항목이 먼저 열립니다. |

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[프로젝트](../extensibility/project-element-visual-studio-templates.md)|프로젝트에 추가할 파일 또는 디렉터리를 지정합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 템플릿 `string` *.zip* 파일의 파일에 대한 이름 또는 경로를 나타내는 A입니다.

## <a name="remarks"></a>설명
 `ProjectItem`은 의 선택적 `Project`자식입니다.

 이 `TargetFileName` 특성을 사용하여 템플릿 *.zip* 파일의 디렉터리 구조와 다른 디렉터리 구조를 만들 수 있습니다. 예를 들어 *MyFile.vb* 파일이 *템플릿 .zip* 파일의 루트에 있지만 템플릿에서 만든 모든 프로젝트에서 *CustomFiles라는* 디렉토리에 파일을 배치하려는 경우 다음 XML을 사용합니다.

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 이 `TargetFileName` 특성은 파일 이름에 국제 문자가 포함된 파일의 이름을 바꿀 수도 있습니다. 예를 들어 템플릿 *.zip* 파일에는 유니코드 문자가 있는 파일 이름이 포함될 수 없으므로 *.zip* 파일로 압축하려면 먼저 파일의 이름을 바여야 합니다. 이 `TargetFileName` 특성을 사용하여 파일 이름을 원래 유니코드 파일 이름으로 다시 설정할 수 있습니다.

 이 `TargetFileName` 특성을 사용하여 매개 변수가 있는 파일의 이름을 바꿀 수도 있습니다. 다음 절차에서는 템플릿 *.zip* 파일의 루트 디렉토리에 있는 *파일 MyFile.vb의*이름을 프로젝트 이름을 기반으로 하는 파일 이름으로 이름을 변경하는 방법을 설명합니다.

### <a name="to-rename-files-with-parameters"></a>매개 변수가 있는 파일의 이름을 바꾸려면

1. *.vstemplate* 파일에서 다음 XML을 사용합니다.

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. 텍스트 편집기 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 프로젝트 파일(프로젝트에 대한 *.vbproj)을* 엽니다.

3. 다음 XML과 유사한 프로젝트 파일에서 줄을 찾습니다.

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. 코드 줄을 다음 XML로 바꿉니다.

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    이 템플릿에서 프로젝트를 만들면 파일 이름은 사용자가 **새 프로젝트** 대화 상자에 입력한 이름을 기반으로 하며 안전하지 않은 모든 문자와 공백이 제거됩니다. 자세한 내용은 [템플릿 매개 변수 를](../ide/template-parameters.md)참조하십시오.

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
- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [ProjectItem 요소(비주얼 스튜디오 항목 템플릿)](../extensibility/projectitem-element-visual-studio-item-templates.md)
