---
title: 기본 프로젝트 시스템 만들기, 2부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739717"
---
# <a name="create-a-basic-project-system-part-2"></a>기본 프로젝트 시스템 만들기, 2부
이 시리즈의 첫 번째 연습인 [기본 프로젝트 시스템 만들기 1부는](../extensibility/creating-a-basic-project-system-part-1.md)기본 프로젝트 시스템을 만드는 방법을 보여 주며, 이를 통해 기본 프로젝트 시스템을 만드는 방법을 보여 주며, 기본 프로젝트 시스템을 만드는 방법을 보여 주며, 기본 프로젝트 시스템 만들기를 보여 주시면 됩니다. 이 연습에서는 Visual Studio 템플릿, 속성 페이지 및 기타 기능을 추가하여 기본 프로젝트 시스템을 기반으로 합니다. 이 연습은 시작하기 전에 첫 번째 연습을 완료해야 합니다.

이 연습에서는 프로젝트 파일 이름 확장자 *.myproj가*있는 프로젝트 형식을 만드는 방법을 설명합니다. 연습을 완료하려면 연습이 기존 Visual C# 프로젝트 시스템에서 차용되므로 고유한 언어를 만들 필요가 없습니다.

이 연습에서는 이러한 작업을 수행하는 방법을 설명합니다.

- Visual Studio 템플릿을 만듭니다.

- Visual Studio 템플릿을 배포합니다.

- **새** 프로젝트 대화 상자에서 프로젝트 유형 자식 노드를 만듭니다.

- Visual Studio 템플릿에서 매개 변수 대체를 활성화합니다.

- 프로젝트 속성 페이지를 만듭니다.

> [!NOTE]
> 이 연습의 단계는 C# 프로젝트를 기반으로 합니다. 그러나 파일 이름 확장자 및 코드와 같은 세부 사항을 제외하고 Visual Basic 프로젝트에 동일한 단계를 사용할 수 있습니다.

## <a name="create-a-visual-studio-template"></a>비주얼 스튜디오 템플릿 만들기
- [기본 프로젝트 시스템을 만들고 1부에서는](../extensibility/creating-a-basic-project-system-part-1.md) 기본 프로젝트 템플릿을 만들고 프로젝트 시스템에 추가하는 방법을 보여 주며, 1부에서는 이를 추가합니다. 또한 시스템 레지스트리에 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> * \\Templates\Project\SimpleProject\\ * 폴더의 전체 경로를 기록하는 특성을 사용하여 Visual Studio에 이 템플릿을 등록하는 방법도 보여 주었습니다.

기본 프로젝트 템플릿 대신 Visual Studio*템플릿(.vstemplate* 파일)을 사용하여 **새 프로젝트** 대화 상자에 템플릿이 표시되는 방식과 템플릿 매개 변수를 대체하는 방법을 제어할 수 있습니다. *.vstemplate* 파일은 프로젝트 시스템 템플릿을 사용하여 프로젝트를 만들 때 소스 파일을 포함하는 방법을 설명하는 XML 파일입니다. 프로젝트 시스템 자체는 *.zip* 파일에서 *.vstemplate* 파일 및 소스 파일을 수집하 여 빌드되며 *.zip* 파일을 Visual Studio에 알려진 위치에 복사하여 배포됩니다. 이 프로세스는 이 연습의 후반부에서 자세히 설명합니다.

1. 에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]기본 프로젝트 시스템 만들기 1 [부](../extensibility/creating-a-basic-project-system-part-1.md)다음을 따라 만든 SimpleProject 솔루션을 엽니다.

2. *SimpleProjectPackage.cs* 파일에서 ProvideProjectFactory 특성을 찾습니다. 두 번째 매개 변수(프로젝트 이름)를 null로 바꾸고 네 번째 매개 변수(프로젝트 템플릿 폴더에 대한 경로)를 "로 바꿉니다. \\\NullPath", 다음과 같습니다.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. *템플릿\프로젝트\SimpleProject 폴더에 SimpleProject.vstemplate라는 XML 파일을 추가합니다.\\ \\* *SimpleProject.vstemplate*

4. *SimpleProject.vs 템플릿의* 내용을 다음 코드로 바꿉니다.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. **속성** 창에서 * \\\\ 템플릿\프로젝트\SimpleProject* 폴더에서 5개의 파일을 모두 선택하고 **빌드 작업을** **ZipProject로**설정합니다.

    ![간단한 프로젝트 폴더](../extensibility/media/simpproj2.png "심프로즈2")

    TemplateData> 섹션에서는 \<다음과 같이 새 **프로젝트** 대화 상자에서 SimpleProject 프로젝트 유형의 위치와 모양을 결정합니다.

- \<이름> 요소는 프로젝트 템플릿의 이름을 SimpleProject 응용 프로그램으로 지정합니다.

- 설명 \<> 요소에는 프로젝트 템플릿을 선택할 때 **새 프로젝트** 대화 상자에 나타나는 설명이 포함되어 있습니다.

- \<아이콘> 요소는 SimpleProject 프로젝트 유형과 함께 나타나는 아이콘을 지정합니다.

- \<ProjectType> 요소는 새 프로젝트 대화 상자에서 프로젝트 유형의 이름을 **지정합니다.** 이 이름은 ProvideProjectFactory 특성의 프로젝트 이름 매개 변수를 대체합니다.

  > [!NOTE]
  > \<ProjectType> 요소는 SimpleProjectPackage.cs `LanguageVsTemplate` 파일의 `ProvideProjectFactory` 특성 인수와 일치해야 합니다.

  TemplateContent> 섹션에서는 \<새 프로젝트를 만들 때 생성되는 이러한 파일에 대해 설명합니다.

- *심플프로젝트.마이프로즈*

- *Program.cs*

- *AssemblyInfo.cs*

  세 파일 `ReplaceParameters` 모두 true로 설정되어 매개 변수 대체를 가능하게 합니다. *Program.cs* 파일이 `OpenInEditor` true로 설정되어 프로젝트를 만들 때 코드 편집기에서 파일을 열수 있습니다.

  Visual Studio 템플릿 스키마의 요소에 대한 자세한 내용은 [Visual Studio 템플릿 스키마 참조를](../extensibility/visual-studio-template-schema-reference.md)참조하십시오.

> [!NOTE]
> 프로젝트에 두 개 이상의 Visual Studio 템플릿이 있는 경우 모든 템플릿은 별도의 폴더에 있습니다. 해당 폴더의 모든 파일에는 **빌드 작업이** **ZipProject로**설정되어 있어야 합니다.

## <a name="adding-a-minimal-vsct-file"></a>최소 .vsct 파일 추가
 새 Visual Studio 템플릿을 인식하려면 설치 모드에서 Visual Studio를 실행해야 합니다. 설치 모드에는 *.vsct* 파일이 있어야 합니다. 따라서 프로젝트에 최소 *.vsct* 파일을 추가 해야 합니다.

1. *SimpleProject.vsct라는* XML 파일을 SimpleProject 프로젝트에 추가합니다.

2. *SimpleProject.vsct* 파일의 내용을 다음 코드로 바꿉니다.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. 이 파일의 **빌드 작업을** **VSCT컴파일로**설정합니다. **속성** 창이 아닌 *.csproj* 파일에서만 이 작업을 수행할 수 있습니다. 이 파일의 **빌드 작업이** 이 시점에서 **없음으로** 설정되어 있는지 확인합니다.

    1. SimpleProject 노드를 마우스 오른쪽 단추로 클릭한 다음 **SimpleProject.csproj 편집을**클릭합니다.

    2. *.csproj* 파일에서 *SimpleProject.vsct* 항목을 찾습니다.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. 빌드 작업을 **VSCT컴파일로**변경합니다.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. 프로젝트 파일을 닫고 편집기닫습니다.

    5. SimpleProject 노드를 저장한 다음 **솔루션 탐색기에서** **프로젝트 다시로드를**클릭합니다.

## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio 템플릿 빌드 단계 검토
 VSPackage 프로젝트 빌드 시스템은 일반적으로 *.vstemplate 파일이* 변경되거나 *.vstemplate* 파일이 포함된 프로젝트가 다시 빌드될 때 설치 모드에서 Visual Studio를 실행합니다. MSBuild의 자세한 수준을 일반 또는 그 이상으로 설정하여 따를 수 있습니다.

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. 프로젝트 **및 솔루션** 노드를 확장한 다음 **빌드 및 실행을**선택합니다.

3. **MSBuild 프로젝트 빌드 출력 세부 정보** 로 설정 **합니다.** **확인**을 클릭합니다.

4. SimpleProject 프로젝트를 다시 빌드합니다.

    *.zip* 프로젝트 파일을 만드는 빌드 단계는 다음 예제와 유사해야 합니다.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>비주얼 스튜디오 템플릿 배포
Visual Studio 템플릿에는 경로 정보가 포함되어 있지 않습니다. 따라서 템플릿 *.zip* 파일은 Visual Studio에 알려진 위치에 배포되어야 합니다. 프로젝트 템플릿 폴더의 위치는 일반적으로 *<% LOCALAPPDATA% >\Microsoft\VisualStudio\14.0Exp\프로젝트 템플릿입니다.*

프로젝트 팩터리를 배포하려면 설치 프로그램에 관리자 권한이 있어야 합니다. 그것은 비주얼 스튜디오 설치 노드에서 템플릿을 배포: *...\마이크로소프트 비주얼 스튜디오 14.0\Common7\IDE\프로젝트 템플릿*.

## <a name="test-a-visual-studio-template"></a>비주얼 스튜디오 템플릿 테스트
프로젝트 팩터리에서 Visual Studio 템플릿을 사용하여 프로젝트 계층 구조를 만드는지 여부를 확인합니다.

1. Visual Studio SDK 실험 인스턴스를 재설정합니다.

    On [!INCLUDE[win7](../debugger/includes/win7_md.md)]: **시작** 메뉴에서 **Microsoft 비주얼 스튜디오/Microsoft 비주얼 스튜디오 SDK/도구** 폴더를 찾은 다음 **Microsoft Visual Studio 실험 인스턴스 재설정을**선택합니다.

    이후 버전의 Windows: **시작** 화면에서 **Microsoft Visual Studio \<버전을 실험 인스턴스> 재설정합니다.**

2. 명령 프롬프트 창이 나타납니다. 단어를 볼 때 **계속하려면 키를**누릅니다, **ENTER를**클릭합니다. 창이 닫히면 Visual Studio를 엽니다.

3. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

4. 실험적 인스턴스에서 SimpleProject 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **SimpleProject**를 선택합니다.

5. SimpleProject의 새 인스턴스가 표시됩니다.

    ![간단한 프로젝트 새 인스턴스](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![내 프로젝트 새 인스턴스](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>프로젝트 유형 자식 노드 만들기
**새 프로젝트** 대화 상자에서 자식 노드를 프로젝트 유형 노드에 추가할 수 있습니다. 예를 들어 SimpleProject 프로젝트 유형의 경우 콘솔 응용 프로그램, 창 응용 프로그램, 웹 응용 프로그램 등을 위한 자식 노드가 있을 수 있습니다.

자식 노드는 프로젝트 파일을 변경하고 \< \<ZipProject> 요소에> 자식을 추가하여 생성됩니다. 빌드 또는 배포 중에 템플릿을 복사하면 모든 하위 노드가 프로젝트 템플릿 폴더의 하위 폴더가 됩니다.

이 섹션에서는 SimpleProject 프로젝트 유형에 대한 콘솔 자식 노드를 만드는 방법을 보여 주며 있습니다.

1. * \\템플릿\프로젝트\SimpleProject\\ * 폴더의 이름을 * \\템플릿\프로젝트\콘솔앱으로\\바꿉니다.*

2. **속성** 창에서 * \\Templates\Project\ConsoleApp\\ * 폴더에서 5개의 파일을 모두 선택하고 **빌드 작업이** **ZipProject**로 설정되어 있는지 확인합니다.

3. SimpleProject.vs 템플릿 파일에서 닫는 태그 바로 앞의 \<TemplateData> 섹션 끝에 다음 줄을 추가합니다.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    이렇게 하면 콘솔 응용 프로그램 템플릿이 콘솔 자식 노드와 하위 노드 위의 한 수준인 SimpleProject 상위 노드에 모두 표시됩니다.

4. *SimpleProject.vs 템플릿 파일을 저장합니다.*

5. *.csproj* 파일에서 각 \<ZipProject 요소에 OutputSubPath> 추가합니다. 이전과 같이 프로젝트를 언로드하고 프로젝트 파일을 편집합니다.

6. \<ZipProject> 요소를 찾습니다. 각 \<ZipProject> 요소에 \<OutputSubPath> 요소를 추가하고 콘솔 값을 지정합니다. 지퍼 프로젝트

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. 이 \<속성 그룹> 프로젝트 파일에 추가합니다.

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. 프로젝트 파일을 저장하고 프로젝트를 다시 로드합니다.

## <a name="test-the-project-type-child-node"></a>프로젝트 유형 자식 노드 테스트
수정된 프로젝트 파일을 테스트하여 **Console** 자식 노드가 **새 프로젝트** 대화 상자에 나타나는지 확인합니다.

1. Microsoft **비주얼 스튜디오 실험 인스턴스 재설정** 도구를 실행합니다.

2. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

3. 새 **프로젝트** 대화 상자에서 **SimpleProject** 노드를 클릭합니다. **콘솔 응용 프로그램** 템플릿이 템플릿 창에 나타나야 **합니다.**

4. 단순 프로젝트 노드를 **확장합니다.** **콘솔** 자식 노드가 나타납니다. **SimpleProject 응용 프로그램** 템플릿이 **템플릿** 창에 계속 나타납니다.

5. **디버깅 취소를** 클릭하고 중지합니다.

    ![간단한 프로젝트 롤업](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![간단한 프로젝트 콘솔 노드](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>프로젝트 템플릿 매개 변수 대체
- [기본 프로젝트 시스템을 만드는 1부에서는](../extensibility/creating-a-basic-project-system-part-1.md) 기본 `ProjectNode.AddFileFromTemplate` 종류의 템플릿 매개 변수 대체를 수행하는 방법을 덮어쓰는 방법을 보여 주어 야했습니다. 이 섹션에서는 보다 정교한 Visual Studio 템플릿 매개 변수를 사용하는 방법을 설명합니다.

**새 프로젝트** 대화 상자에서 Visual Studio 템플릿을 사용하여 프로젝트를 만들 때 템플릿 매개 변수가 문자열로 대체되어 프로젝트를 사용자 지정합니다. 템플릿 매개 변수는 달러 기호(예: $time$)로 시작하고 끝나는 특수 토큰입니다. 다음 두 매개 변수는 템플릿을 기반으로 하는 프로젝트에서 사용자 지정을 사용하도록 설정하는 데 특히 유용합니다.

- $GUID[1-10]$가 새 Guid로 대체됩니다. 최대 10개의 고유 GUID(예: $guid1$)를 지정할 수 있습니다.

- $safeprojectname$는 **새 프로젝트** 대화 상자에서 사용자가 제공한 이름으로, 모든 안전하지 않은 문자와 공백을 제거하도록 수정되었습니다.

  템플릿 매개 변수의 전체 목록은 [템플릿 매개 변수 를](../ide/template-parameters.md)참조하십시오.

### <a name="to-substitute-project-template-parameters"></a>프로젝트 템플릿 매개 변수를 대체하려면

1. *SimpleProjectNode.cs* 파일에서 메서드를 `AddFileFromTemplate` 제거합니다.

2. \< * \\템플릿\프로젝트\콘솔앱\SimpleProject.myproj* 파일에서 루트네임스페이스> 속성을 찾아 해당 값을 $safeprojectname$로 변경합니다.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. * \\템플릿\프로젝트\SimpleProject\Program.cs* 파일에서 파일의 내용을 다음 코드로 바꿉니다.

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

5. 새로운 SimpleProject 콘솔 응용 프로그램을 만듭니다. (프로젝트 **유형** 창에서 **SimpleProject**를 선택합니다. **Visual Studio 설치 템플릿에서**콘솔 응용 **프로그램을**선택합니다.)

6. 새로 만든 프로젝트에서 *Program.cs.* 다음과 같이 보일 것입니다 (파일의 GUID 값은 다릅니다.)

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>프로젝트 속성 페이지 만들기
사용자가 템플릿을 기반으로 하는 프로젝트에서 속성을 보고 변경할 수 있도록 프로젝트 유형에 대한 속성 페이지를 만들 수 있습니다. 이 섹션에서는 구성 독립적인 속성 페이지를 만드는 방법을 보여 주며, 이 섹션에서는 이 기본 속성 페이지는 속성 표표를 사용하여 속성 페이지 클래스에 노출되는 공용 속성을 표시합니다.

기본 클래스에서 속성 `SettingsPage` 페이지 클래스를 파생합니다. `SettingsPage` 클래스에서 제공하는 속성 그리드는 대부분의 기본 데이터 형식을 인식하고 이를 표시하는 방법을 알고 있습니다. 또한 클래스는 `SettingsPage` 프로젝트 파일에 속성 값을 유지하는 방법을 알고 있습니다.

이 섹션에서 만든 속성 페이지를 사용하면 다음 프로젝트 속성을 변경하고 저장할 수 있습니다.

- AssemblyName

- OutputType

- 루트 네임 스페이스.

1. *SimpleProjectPackage.cs* 파일에서 이 `ProvideObject` 특성을 `SimpleProjectPackage` 클래스에 추가합니다.

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    그러면 속성 페이지 `GeneralPropertyPage` 클래스가 COM에 등록됩니다.

2. *SimpleProjectNode.cs* 파일에서 다음 두 개의 재정의된 `SimpleProjectNode` 메서드를 클래스에 추가합니다.

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    이 두 메서드 모두 속성 페이지 GUID의 배열을 반환합니다. 일반속성 페이지 GUID는 배열의 유일한 요소이므로 **속성 페이지** 대화 상자에는 한 페이지만 표시됩니다.

3. SimpleProject 프로젝트에 *GeneralPropertyPage.cs라는* 클래스 파일을 추가합니다.

4. 다음 코드를 사용하여 이 파일의 내용을 바꿉니다.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    클래스는 `GeneralPropertyPage` 세 개의 공용 속성 AssemblyName, OutputType 및 루트네임스페이스를 노출합니다. AssemblyName에는 설정된 메서드가 없으므로 읽기 전용 속성으로 표시됩니다. OutputType은 나열된 상수이므로 드롭다운 목록으로 나타납니다.

    기본 `SettingsPage` 클래스는 `ProjectMgr` 속성을 유지하도록 제공합니다. 메서드는 `BindProperties` `ProjectMgr` 지속된 속성 값을 검색 하 고 해당 속성을 설정 하는 데 사용 합니다. 메서드는 `ApplyChanges` `ProjectMgr` 속성의 값을 가져옵니다 하 고 프로젝트 파일에 유지 하는 데 사용 합니다. 속성 집합 메서드는 속성을 유지해야 함을 나타내기 위해 true로 설정합니다. `IsDirty` 지속성은 프로젝트 또는 솔루션을 저장할 때 발생합니다.

5. SimpleProject 솔루션을 다시 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타나야 합니다.

6. 실험적인 인스턴스에서 새 SimpleProject 응용 프로그램을 만듭니다.

7. Visual Studio는 Visual Studio 템플릿을 사용하여 프로젝트를 만들기 위해 프로젝트 팩터리를 호출합니다. 새 *Program.cs* 파일이 코드 편집기에서 열립니다.

8. **솔루션 탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. **속성 페이지** 대화 상자가 표시됩니다.

    ![단순 프로젝트 속성 페이지](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>프로젝트 속성 페이지 테스트
이제 속성 값을 수정하고 변경할 수 있는지 여부를 테스트할 수 있습니다.

1. **MyConsoleApplication 속성 페이지** 대화 상자에서 **기본 Namespace를** **My Application**으로 변경합니다.

2. **OutputType** 속성을 선택한 다음 **클래스 라이브러리를**선택합니다.

3. **적용**, **확인**을 차례로 클릭합니다.

4. **속성 페이지** 대화 상자를 다시 열고 변경 내용이 유지되었는지 확인합니다.

5. Visual Studio의 실험적 인스턴스를 닫습니다.

6. 실험 인스턴스를 다시 엽니다.

7. **속성 페이지** 대화 상자를 다시 열고 변경 내용이 유지되었는지 확인합니다.

8. Visual Studio의 실험적 인스턴스를 닫습니다.
    ![실험 인스턴스 닫기](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
