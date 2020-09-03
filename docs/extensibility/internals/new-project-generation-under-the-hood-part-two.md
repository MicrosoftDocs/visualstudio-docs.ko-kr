---
title: '새 프로젝트 생성: 내부에서 2 부 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8692f2012e5f2733982f04e35a7fed415e49c636
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707016"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>새 프로젝트 생성: 내부 살펴보기, 2부

[새 프로젝트 생성 시:](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) **새 프로젝트** 대화 상자를 채우는 방법에 대해 설명 합니다. **Visual c # Windows 응용 프로그램**을 선택 하 고 **이름** 및 **위치** 텍스트 상자를 채운 다음 확인을 클릭 했다고 가정해 보겠습니다.

## <a name="generating-the-solution-files"></a>솔루션 파일 생성
 응용 프로그램 템플릿을 선택 하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 해당 .vstemplate 파일의 압축을 풀고 해당 .vstemplate 파일을 열고이 파일의 XML 명령을 해석 하는 템플릿을 시작 합니다. 이러한 명령은 새 솔루션이 나 기존 솔루션에서 프로젝트 및 프로젝트 항목을 만듭니다.

 템플릿은 .vstemplate 파일을 보관 하는 동일한 .zip 폴더에서 항목 템플릿 이라는 소스 파일의 압축을 풉니다. 템플릿은 이러한 파일을 새 프로젝트에 복사 하 여 적절 하 게 사용자 지정 합니다.

### <a name="template-parameter-replacement"></a>템플릿 매개 변수 바꾸기
 템플릿이 새 프로젝트에 항목 템플릿을 복사 하면 템플릿 매개 변수를 문자열로 바꿔서 파일을 사용자 지정 합니다. 템플릿 매개 변수는 $와 같이 달러 $date 기호가 앞에 오고 그 뒤에 오는 특수 토큰입니다.

 일반적인 프로젝트 항목 템플릿을 살펴보겠습니다. Program Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 폴더에서 Program.cs를 추출 하 고 검사 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace $safeprojectname$
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

Simple 이라는 새 Windows 응용 프로그램 프로젝트를 만드는 경우 템플릿이 `$safeprojectname$` 매개 변수를 프로젝트의 이름으로 바꿉니다.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Simple
{
    static class Program
    {
        // source code deleted here for brevity
    }
}
```

 템플릿 매개 변수의 전체 목록은 [템플릿 매개 변수](../../ide/template-parameters.md)를 참조하세요.

## <a name="a-look-inside-a-vstemplate-file"></a>내에서 찾습니다. .Vstemplate 파일
 기본 .vstemplate 파일의 형식은 다음과 같습니다.

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 \<TemplateData> [새 프로젝트 생성](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)의 섹션에서 설명 하 고 있습니다. 이 단원의 태그는 **새 프로젝트** 대화 상자의 모양을 제어 하는 데 사용 됩니다.

 섹션의 태그는 \<TemplateContent> 새 프로젝트 및 프로젝트 항목의 생성을 제어 합니다. \<TemplateContent>Files\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip 폴더의 cswindowsapplication .vstemplate 파일에 있는 섹션은 다음과 같습니다.

```xml
<TemplateContent>
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">
    <ProjectItem ReplaceParameters="true"
      TargetFileName="Properties\AssemblyInfo.cs">
      AssemblyInfo.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Resources.resx">
      Resources.resx
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">
      Resources.Designer.cs
    </ProjectItem>
    <ProjectItem TargetFileName="Properties\Settings.settings">
      Settings.settings
    </ProjectItem>
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">
      Settings.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">
      Form1.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Form1.Designer.cs
    </ProjectItem>
    <ProjectItem ReplaceParameters="true">
      Program.cs
    </ProjectItem>
  </Project>
</TemplateContent>
```

 \<Project>태그는 프로젝트의 생성을 제어 하 고 태그는 \<ProjectItem> 프로젝트 항목의 생성을 제어 합니다. ReplaceParameters 매개 변수가 true 이면 템플릿에서 프로젝트 파일이 나 항목의 모든 템플릿 매개 변수를 사용자 지정 합니다. 이 경우 설정의 경우를 제외 하 고 모든 프로젝트 항목이 사용자 지정 됩니다.

 TargetFileName 매개 변수는 결과 프로젝트 파일 또는 항목의 이름 및 상대 경로를 지정 합니다. 그러면 프로젝트에 대 한 폴더 구조를 만들 수 있습니다. 이 인수를 지정 하지 않으면 프로젝트 항목은 프로젝트 항목 템플릿과 동일한 이름을 갖게 됩니다.

 결과 Windows 응용 프로그램 폴더 구조는 다음과 같습니다.

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 템플릿의 첫 번째 및 유일한 \<Project> 태그는 다음과 같습니다.

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 이렇게 하면 템플릿 항목 windowsapplication 프로그램 .csproj를 복사 하 고 사용자 지정 하 여 간단한 .csproj 프로젝트 파일을 만들도록 새 프로젝트 템플릿에 지시 합니다.

### <a name="designers-and-references"></a>디자이너 및 참조
 솔루션 탐색기에서 속성 폴더가 있고 필요한 파일을 포함 하 고 있음을 볼 수 있습니다. 하지만 프로젝트 참조 및 디자이너 파일 종속성 (예: Resources.Designer.cs에 대 한 Form1.Designer.cs 및 Form1.cs에 대 한)은 무엇 인가요?  이러한 파일은 생성 될 때 간단한 .csproj 파일에 설정 됩니다.

 \<ItemGroup>프로젝트 참조를 만드는 간단한 .csproj의는 다음과 같습니다.

```xml
<ItemGroup>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Drawing" />
    <Reference Include="System.Windows.Forms" />
    <Reference Include="System.Xml" />
</ItemGroup>
```

 이러한 참조가 솔루션 탐색기에 표시 되는 여섯 개의 프로젝트 참조 임을 확인할 수 있습니다. 다른 섹션은 다음과 같습니다 \<ItemGroup> . 명확성을 위해 많은 코드 줄이 삭제 되었습니다. 이 섹션에서는 Settings.Designer.cs를 설정에 따라 결정 합니다. 설정:

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>추가 정보

- [새 프로젝트 생성: 내부 살펴보기, 1부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
