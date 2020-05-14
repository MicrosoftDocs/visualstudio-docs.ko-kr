---
title: '새로운 프로젝트 생성: 후드 아래, 2부 | 마이크로 소프트 문서'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707016"
---
# <a name="new-project-generation-under-the-hood-part-two"></a>새 프로젝트 생성: 내부 살펴보기, 2부

[새 프로젝트 생성: 1부에서는](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) **새 프로젝트** 대화 상자가 어떻게 채워지는지 확인했습니다. **Visual C# Windows 응용 프로그램을**선택하고 **이름** 및 **위치** 텍스트 상자를 작성하고 확인을 클릭했다고 가정해 보겠습니다.

## <a name="generating-the-solution-files"></a>솔루션 파일 생성
 응용 프로그램 템플릿을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 선택하면 해당 .vstemplate 파일의 압축을 풀고 열고 이 파일의 XML 명령을 해석하는 템플릿을 시작합니다. 이러한 명령은 새 솔루션 또는 기존 솔루션에서 프로젝트 및 프로젝트 항목을 만듭니다.

 템플릿은 .vstemplate 파일을 포함하는 동일한 .zip 폴더에서 항목 템플릿이라고 하는 소스 파일을 압축 해제합니다. 템플릿은 이러한 파일을 새 프로젝트에 복사하여 그에 따라 사용자 지정합니다.

### <a name="template-parameter-replacement"></a>템플릿 매개 변수 교체
 템플릿이 항목 템플릿을 새 프로젝트에 복사하면 모든 템플릿 매개 변수를 문자열로 대체하여 파일을 사용자 지정합니다. 템플릿 매개 변수는 $date$와 같은 달러 기호 앞에 오는 특수 토큰입니다.

 일반적인 프로젝트 항목 템플릿을 살펴보겠습니다. 프로그램 파일\마이크로소프트 비주얼 스튜디오 8\Common7\IDE\프로젝트 템플릿\CSharp\윈도우\1033\WindowsApplication.zip 폴더에서 Program.cs 추출 하 고 검사 합니다.

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

단순이라는 새 Windows 응용 프로그램 프로젝트를 만드는 경우 `$safeprojectname$` 템플릿은 매개 변수를 프로젝트 이름으로 바꿉니다.

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

## <a name="a-look-inside-a-vstemplate-file"></a>내부를 살펴보십시오. VS템플릿 파일
 기본 .vstemplate 파일에는 이 형식이 있습니다.

```xml
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">
    <TemplateData>
    </TemplateData>
    <TemplateContent>
    </TemplateContent>
</VSTemplate>
```

 새 프로젝트 \<생성에서 TemplateData> [섹션: Under the Hood, Part 1.](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 이 섹션의 태그는 **새 프로젝트** 대화 상자의 모양을 제어하는 데 사용됩니다.

 \<TemplateContent> 섹션의 태그는 새 프로젝트 및 프로젝트 항목의 생성을 제어합니다. 다음은 cswindowsapplication.vs template 파일에서 \<템플릿 콘텐츠> 섹션 \프로그램 파일\마이크로소프트 비주얼 스튜디오 8\Common7\IDE\프로젝트 템플릿\CSharp\윈도우\1033\WindowsApplication.zip 폴더.

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

 프로젝트 \<> 태그는 프로젝트의 생성을 제어하고 \<ProjectItem> 태그는 프로젝트 항목의 생성을 제어합니다. 매개 변수 ReplaceParameters true이 면 템플릿 프로젝트 파일 또는 항목의 모든 템플릿 매개 변수를 사용자 지정 합니다. 이 경우 Settings.settings을 제외한 모든 프로젝트 항목이 사용자 지정됩니다.

 TargetFileName 매개 변수는 결과 프로젝트 파일 또는 항목의 이름과 상대 경로를 지정합니다. 이렇게 하면 프로젝트에 대한 폴더 구조를 만들 수 있습니다. 이 인수를 지정하지 않으면 프로젝트 항목의 이름이 프로젝트 항목 템플릿과 동일합니다.

 결과 Windows 응용 프로그램 폴더 구조는 다음과 같습니다.

 ![SimpleSolution](../../extensibility/internals/media/simplesolution.png "SimpleSolution")

 템플릿의 첫 \<번째이자 유일한 프로젝트> 태그는 다음과 같습니다.

```xml
<Project File="WindowsApplication.csproj" ReplaceParameters="true">
```

 이렇게 하면 새 프로젝트 템플릿을 복사하여 템플릿 항목 windowsapplication.csproj를 복사하고 사용자 지정하여 Simple.csproj 프로젝트 파일을 만들도록 지시합니다.

### <a name="designers-and-references"></a>디자이너 및 참조
 솔루션 탐색기에서 속성 폴더가 있고 예상된 파일이 포함되어 있음을 확인할 수 있습니다. 그러나 Resources.resx에 Resources.Designer.cs Form1.cs Form1.Designer.cs 같은 프로젝트 참조 및 디자이너 파일 종속성은 어떻습니까?  이러한 파일은 생성될 때 Simple.csproj 파일에 설정됩니다.

 다음은 프로젝트 \<참조를 만드는 Simple.csproj의 항목 그룹>.

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

 솔루션 탐색기에서 나타나는 6개의 프로젝트 참조임을 확인할 수 있습니다. 다음은 다른 \<항목 그룹> 섹션입니다. 명확성을 위해 많은 코드 줄이 삭제되었습니다. 이 섹션에서는 Settings.Designer.cs 설정설정에 따라 달라집니다.

```xml
<ItemGroup>
    <Compile Include="Properties\Settings.Designer.cs">
        <DependentUpon>Settings.settings</DependentUpon>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>참조

- [새 프로젝트 생성: 내부 살펴보기, 1부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)
- [MSBuild](../../msbuild/msbuild.md)
