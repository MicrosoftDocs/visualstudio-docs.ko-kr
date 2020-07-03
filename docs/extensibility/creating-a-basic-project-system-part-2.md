---
title: 기본 프로젝트 시스템 만들기, 2 부 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 2b9d5ce673e0ee44e888905239c12251241015ab
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903829"
---
# <a name="create-a-basic-project-system-part-2"></a>기본 프로젝트 시스템 만들기, 2 부
[기본 프로젝트 시스템을 만드는](../extensibility/creating-a-basic-project-system-part-1.md)이 시리즈의 첫 번째 연습은 기본 프로젝트 시스템을 만드는 방법을 보여 줍니다. 이 연습은 Visual Studio 템플릿, 속성 페이지 및 기타 기능을 추가 하 여 기본 프로젝트 시스템을 기반으로 합니다. 이 연습을 시작 하기 전에 첫 번째 연습을 완료 해야 합니다.

이 연습에서는 프로젝트 파일 이름 확장명이 *. myproj*인 프로젝트 형식을 만드는 방법을 배웁니다. 연습을 완료 하기 위해 활용는 기존 Visual c # 프로젝트 시스템에서 연습을 수행 하기 때문에 사용자 고유의 언어를 만들 필요가 없습니다.

이 연습에서는 다음 작업을 수행 하는 방법을 배웁니다.

- Visual Studio 템플릿 만들기

- Visual Studio 템플릿을 배포 합니다.

- **새 프로젝트** 대화 상자에서 프로젝트 형식 자식 노드를 만듭니다.

- Visual Studio 템플릿에서 매개 변수 대체를 사용 하도록 설정 합니다.

- 프로젝트 속성 페이지를 만듭니다.

> [!NOTE]
> 이 연습의 단계는 c # 프로젝트를 기반으로 합니다. 그러나 파일 이름 확장명, 코드 등의 세부 사항을 제외 하 고 Visual Basic 프로젝트에 대해 동일한 단계를 사용할 수 있습니다.

## <a name="create-a-visual-studio-template"></a>Visual Studio 템플릿 만들기
- [기본 프로젝트 시스템을 만들고 1 부에서는](../extensibility/creating-a-basic-project-system-part-1.md) 기본 프로젝트 템플릿을 만들고 프로젝트 시스템에 추가 하는 방법을 보여 줍니다. 또한 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 시스템 레지스트리에서 * \\ \\ Templates\Projects\SimpleProject* 폴더의 전체 경로를 기록 하는 특성을 사용 하 여이 템플릿을 Visual Studio에 등록 하는 방법을 보여 줍니다.

기본 프로젝트 템플릿 대신 Visual Studio 템플릿 (*.vstemplate* 파일)을 사용 하 여 **새 프로젝트** 대화 상자에 템플릿을 표시 하는 방법과 템플릿 매개 변수를 대체 하는 방법을 제어할 수 있습니다. *.Vstemplate* 파일은 프로젝트 시스템 템플릿을 사용 하 여 프로젝트를 만들 때 소스 파일이 포함 되는 방법을 설명 하는 XML 파일입니다. 프로젝트 시스템 자체는 *.vstemplate* 파일 및 소스 파일을 *.zip* 파일에 수집 하 고 *.zip* 파일을 Visual Studio에 알려진 위치에 복사 하 여 배포 됩니다. 이 프로세스에 대해서는이 연습의 뒷부분에서 자세히 설명 합니다.

1. 에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [기본 프로젝트 시스템 만들기 (1 부)](../extensibility/creating-a-basic-project-system-part-1.md)에 따라 만든 SimpleProject 솔루션을 엽니다.

2. *SimpleProjectPackage.cs* 파일에서 ProvideProjectFactory 특성을 찾습니다. 두 번째 매개 변수 (프로젝트 이름)를 null로 바꾸고 네 번째 매개 변수 (프로젝트 템플릿 폴더의 경로)를 "로 바꿉니다. \\ 다음과 같이 \NullPath "를 수행 합니다.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. *SimpleProject* 라는 XML 파일을 * \\ Templates\Projects\SimpleProject \\ * 폴더에 추가 합니다.

4. *SimpleProject* 의 내용을 다음 코드로 바꿉니다.

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

5. **속성** 창의 * \\ Templates\Projects\SimpleProject \\ * 폴더에서 5 개 파일을 모두 선택 하 고 **빌드 작업** 을 **ZipProject**로 설정 합니다.

    ![간단한 프로젝트 폴더](../extensibility/media/simpproj2.png "SimpProj2")

    섹션은 다음과 \<TemplateData> 같이 **새 프로젝트** 대화 상자에서 SimpleProject 프로젝트 형식의 위치와 모양을 결정 합니다.

- \<Name>요소는 프로젝트 템플릿의 이름을 SimpleProject 응용 프로그램으로 지정할 수 있습니다.

- 요소에는 \<Description> 프로젝트 템플릿을 선택할 때 **새 프로젝트** 대화 상자에 표시 되는 설명이 포함 되어 있습니다.

- \<Icon>요소는 SimpleProject 프로젝트 형식과 함께 표시 되는 아이콘을 지정 합니다.

- \<ProjectType>요소는 **새 프로젝트** 대화 상자에서 프로젝트 형식의 이름을로 합니다. 이 이름은 ProvideProjectFactory 특성의 프로젝트 이름 매개 변수를 대체 합니다.

  > [!NOTE]
  > \<ProjectType>요소는 `LanguageVsTemplate` `ProvideProjectFactory` SimpleProjectPackage.cs 파일에 있는 특성의 인수와 일치 해야 합니다.

  \<TemplateContent>이 섹션에서는 새 프로젝트를 만들 때 생성 되는 다음 파일에 대해 설명 합니다.

- *SimpleProject*

- *Program.cs*

- *AssemblyInfo.cs*

  세 파일을 모두 `ReplaceParameters` true로 설정 하면 매개 변수 대체가 가능 합니다. *Program.cs* 파일을 `OpenInEditor` true로 설정 하면 프로젝트가 만들어질 때 코드 편집기에서 파일이 열립니다.

  Visual Studio 템플릿 스키마의 요소에 대 한 자세한 내용은 [Visual studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조 하세요.

> [!NOTE]
> 프로젝트에 Visual Studio 템플릿이 둘 이상 있는 경우 모든 템플릿은 별도의 폴더에 있습니다. 해당 폴더의 모든 파일에는 **빌드 작업** 을 **ZipProject**로 설정 해야 합니다.

## <a name="adding-a-minimal-vsct-file"></a>최소 vsct 파일 추가
 새 또는 수정 된 Visual Studio 템플릿을 인식 하려면 visual Studio를 설치 모드에서 실행 해야 합니다. 설치 모드에는 *. vsct* 파일이 있어야 합니다. 따라서 프로젝트에 최소 *vsct* 파일을 추가 해야 합니다.

1. *SimpleProject* 라는 XML 파일을 SimpleProject 프로젝트에 추가 합니다.

2. *SimpleProject* 파일의 내용을 다음 코드로 바꿉니다.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. 이 파일의 **빌드 작업** 을 **VSCTCompile**로 설정 합니다. **속성** 창이 아닌 *.csproj* 파일 에서만이 작업을 수행할 수 있습니다. 이 시점에서이 파일의 **빌드 작업이** **없음** 으로 설정 되어 있는지 확인 합니다.

    1. SimpleProject 노드를 마우스 오른쪽 단추로 클릭 한 다음 **SimpleProject 편집**을 클릭 합니다.

    2. *.Csproj* 파일에서 *SimpleProject* 항목을 찾습니다.

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. 빌드 작업을 **VSCTCompile**로 변경 합니다.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. 프로젝트 파일을 열고 편집기를 닫습니다.

    5. SimpleProject 노드를 저장 한 다음 **솔루션 탐색기** **프로젝트 다시 로드**를 클릭 합니다.

## <a name="examine-the-visual-studio-template-build-steps"></a>Visual Studio 템플릿 빌드 단계를 검토 합니다.
 VSPackage 프로젝트 빌드 시스템은 일반적으로 *.vstemplate* 파일을 변경 하거나 *.vstemplate* 파일을 포함 하는 프로젝트를 다시 작성할 때 설치 모드에서 Visual Studio를 실행 합니다. MSBuild의 자세한 정도를 보통 이상으로 설정 하 여 수행할 수 있습니다.

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **프로젝트 및 솔루션** 노드를 확장 하 고 **빌드 및 실행**을 선택 합니다.

3. **MSBuild 프로젝트 빌드 출력의 자세한 정도** 를 **보통**으로 설정 합니다. **확인**을 클릭합니다.

4. SimpleProject 프로젝트를 다시 빌드합니다.

    *.Zip* 프로젝트 파일을 만드는 빌드 단계는 다음 예제와 유사 합니다.

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

## <a name="deploy-a-visual-studio-template"></a>Visual Studio 템플릿 배포
Visual Studio 템플릿에 경로 정보가 없습니다. 따라서 템플릿 *.zip* 파일은 Visual Studio에 알려진 위치에 배포 되어야 합니다. ProjectTemplates 폴더의 위치는 일반적으로 *<% LOCALAPPDATA% > \microsoft\visualstudio\14.0exp\projecttemplates*입니다.

프로젝트 팩터리를 배포 하려면 설치 프로그램에 관리자 권한이 있어야 합니다. Visual Studio 설치 노드: *. ..\Microsoft Visual studio 14.0 \ Common7\IDE\ProjectTemplates*에 템플릿을 배포 합니다.

## <a name="test-a-visual-studio-template"></a>Visual Studio 템플릿 테스트
프로젝트 팩터리를 테스트 하 여 Visual Studio 템플릿을 사용 하 여 프로젝트 계층 구조를 만드는 지 여부를 확인 합니다.

1. Visual Studio SDK 실험적 인스턴스를 다시 설정 합니다.

    설정 [!INCLUDE[win7](../debugger/includes/win7_md.md)] : **시작** 메뉴에서 **Microsoft Visual Studio/Microsoft Visual Studio SDK/도구** 폴더를 찾은 다음 **Microsoft Visual Studio 실험적 인스턴스 다시 설정**을 선택 합니다.

    이후 버전의 Windows에서는 **시작** 화면에서 **Microsoft Visual Studio \<version> 실험적 인스턴스 다시 설정**을 입력 합니다.

2. 명령 프롬프트 창이 나타납니다. **아무 키나 눌러 계속 하려면** **enter**키를 누릅니다. 창을 닫은 후 Visual Studio를 엽니다.

3. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 나타납니다.

4. 실험적 인스턴스에서 SimpleProject 프로젝트를 만듭니다. **새 프로젝트** 대화 상자에서 **SimpleProject**를 선택 합니다.

5. SimpleProject의 새 인스턴스가 표시 되어야 합니다.

    ![단순 프로젝트 새 인스턴스](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![내 프로젝트 새 인스턴스](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>프로젝트 형식 자식 노드 만들기
**새 프로젝트** 대화 상자의 프로젝트 형식 노드에 자식 노드를 추가할 수 있습니다. 예를 들어 SimpleProject 프로젝트 형식의 경우 콘솔 응용 프로그램, 창 응용 프로그램, 웹 응용 프로그램 등에 대 한 자식 노드가 있을 수 있습니다.

자식 노드는 프로젝트 파일을 변경 하 고 자식 노드 \<OutputSubPath> 를 요소에 추가 하 여 만듭니다 \<ZipProject> . 빌드 또는 배포 중에 템플릿을 복사 하면 모든 자식 노드가 프로젝트 템플릿 폴더의 하위 폴더가 됩니다.

이 섹션에서는 SimpleProject 프로젝트 형식에 대 한 콘솔 자식 노드를 만드는 방법을 보여 줍니다.

1. * \\ Templates\Projects\SimpleProject \\ * 폴더의 이름을 * \\ Templates\Projects\ConsoleApp \\ *로 바꿉니다.

2. **속성** 창의 * \\ Templates\Projects\ConsoleApp \\ * 폴더에서 5 개 파일을 모두 선택 하 고 **빌드 작업이** **ZipProject**로 설정 되었는지 확인 합니다.

3. SimpleProject 파일에서 \<TemplateData> 닫는 태그 바로 앞에 있는 섹션의 끝에 다음 줄을 추가 합니다.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    이렇게 하면 콘솔 응용 프로그램 템플릿이 콘솔 자식 노드와 SimpleProject 부모 노드 (자식 노드 위의 한 수준)에 모두 표시 됩니다.

4. *SimpleProject* 파일을 저장 합니다.

5. *.Csproj* 파일에서 \<OutputSubPath> 각 ZipProject 요소에를 추가 합니다. 이전 처럼 프로젝트를 언로드하고 프로젝트 파일을 편집 합니다.

6. 요소를 찾습니다 \<ZipProject> . 각 \<ZipProject> 요소에 요소를 추가 하 \<OutputSubPath> 고 값 콘솔에 지정 합니다. ZipProject

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

7. \<PropertyGroup>프로젝트 파일에 다음을 추가 합니다.

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. 프로젝트 파일을 저장 하 고 프로젝트를 다시 로드 합니다.

## <a name="test-the-project-type-child-node"></a>프로젝트 형식 자식 노드 테스트
수정 된 프로젝트 파일을 테스트 하 여 **콘솔** 자식 노드가 **새 프로젝트** 대화 상자에 표시 되는지 여부를 확인 합니다.

1. **Microsoft Visual Studio 실험적 인스턴스 다시 설정** 도구를 실행 합니다.

2. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 표시 되어야 합니다.

3. **새 프로젝트** 대화 상자에서 **SimpleProject** 노드를 클릭 합니다. **콘솔 응용 프로그램** 템플릿이 **템플릿** 창에 표시 됩니다.

4. **SimpleProject** 노드를 확장 합니다. **콘솔** 자식 노드가 표시 됩니다. **SimpleProject 응용 프로그램** 템플릿이 **템플릿** 창에 계속 표시 됩니다.

5. **취소** 및 디버깅 중지를 클릭 합니다.

    ![간단한 프로젝트 롤업](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Simple Project Console 노드](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>프로젝트 템플릿 매개 변수 대체
- [기본 프로젝트 시스템 만들기, 1 부에서는](../extensibility/creating-a-basic-project-system-part-1.md) 메서드를 덮어써서 `ProjectNode.AddFileFromTemplate` 기본 종류의 템플릿 매개 변수 대체를 수행 하는 방법을 살펴보았습니다. 이 섹션에서는 보다 정교한 Visual Studio 템플릿 매개 변수를 사용 하는 방법을 설명 합니다.

**새 프로젝트** 대화 상자에서 Visual Studio 템플릿을 사용 하 여 프로젝트를 만드는 경우 프로젝트를 사용자 지정 하기 위해 템플릿 매개 변수가 문자열로 바뀝니다. 템플릿 매개 변수는 달러 기호 (예: $time $)로 시작 하 고 끝나는 특수 토큰입니다. 다음 두 매개 변수는 특히 템플릿을 기반으로 하는 프로젝트에서 사용자 지정을 사용 하도록 설정 하는 데 유용 합니다.

- $GUID [1-10] $은 새 Guid로 대체 됩니다. 최대 10 개의 고유 Guid를 지정할 수 있습니다 (예: $guid $1).

- $safeprojectname $은 **새 프로젝트** 대화 상자에서 사용자가 제공한 이름으로, 안전 하지 않은 문자 및 공백을 모두 제거 하도록 수정 되었습니다.

  템플릿 매개 변수의 전체 목록은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조 하세요.

### <a name="to-substitute-project-template-parameters"></a>프로젝트 템플릿 매개 변수를 대체 하려면

1. *SimpleProjectNode.cs* 파일에서 메서드를 제거 `AddFileFromTemplate` 합니다.

2. * \\ Templates\Projects\ConsoleApp\SimpleProject.myproj* 파일에서 속성을 찾아 \<RootNamespace> 값을 $safeprojectname $로 변경 합니다.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. * \\ Templates\Projects\SimpleProject\Program.cs* 파일에서 파일의 내용을 다음 코드로 바꿉니다.

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

4. SimpleProject 프로젝트를 다시 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 표시 되어야 합니다.

5. 새 SimpleProject 콘솔 응용 프로그램을 만듭니다. **프로젝트 형식** 창에서 **SimpleProject**를 선택 합니다. **Visual Studio에 설치 된 템플릿**에서 **콘솔 응용 프로그램**을 선택 합니다.

6. 새로 만든 프로젝트에서 *Program.cs*를 엽니다. 다음과 유사 하 게 표시 됩니다 (파일의 GUID 값이 서로 다름).

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
사용자가 템플릿을 기반으로 하는 프로젝트의 속성을 보고 변경할 수 있도록 프로젝트 형식에 대 한 속성 페이지를 만들 수 있습니다. 이 섹션에서는 구성 독립적 속성 페이지를 만드는 방법을 보여 줍니다. 이 기본 속성 페이지는 속성 표를 사용 하 여 속성 페이지 클래스에 노출 하는 공용 속성을 표시 합니다.

기본 클래스에서 속성 페이지 클래스를 파생 시킵니다 `SettingsPage` . 클래스에서 제공 하는 속성 표에서는 `SettingsPage` 대부분의 기본 데이터 형식을 인식 하 고이를 표시 하는 방법을 알고 있습니다. 또한 `SettingsPage` 클래스는 프로젝트 파일에 속성 값을 유지 하는 방법을 알고 있습니다.

이 섹션에서 만든 속성 페이지를 사용 하 여 다음 프로젝트 속성을 변경 하 고 저장할 수 있습니다.

- AssemblyName

- OutputType

- RootNamespace.

1. *SimpleProjectPackage.cs* 파일에서 `ProvideObject` 다음 특성을 클래스에 추가 합니다 `SimpleProjectPackage` .

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    그러면 속성 페이지 클래스가 `GeneralPropertyPage` COM에 등록 됩니다.

2. *SimpleProjectNode.cs* 파일에서 다음과 같은 두 개의 재정의 된 메서드를 클래스에 추가 합니다 `SimpleProjectNode` .

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

    이러한 메서드는 모두 속성 페이지 Guid의 배열을 반환 합니다. GeneralPropertyPage GUID는 배열의 유일한 요소 이므로 **속성 페이지** 대화 상자에는 하나의 페이지만 표시 됩니다.

3. *GeneralPropertyPage.cs* 라는 클래스 파일을 SimpleProject 프로젝트에 추가 합니다.

4. 다음 코드를 사용 하 여이 파일의 내용을 바꿉니다.

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

    `GeneralPropertyPage`클래스는 세 가지 public 속성인 AssemblyName, OutputType 및 RootNamespace을 노출 합니다. AssemblyName에는 set 메서드가 없기 때문에 읽기 전용 속성으로 표시 됩니다. OutputType은 열거 된 상수 이므로 드롭다운 목록으로 표시 됩니다.

    `SettingsPage`기본 클래스는 `ProjectMgr` 속성을 유지 하기 위해를 제공 합니다. `BindProperties`메서드는 `ProjectMgr` 를 사용 하 여 지속형 속성 값을 검색 하 고 해당 속성을 설정 합니다. `ApplyChanges`메서드는 `ProjectMgr` 를 사용 하 여 속성 값을 가져오고이를 프로젝트 파일에 유지 합니다. 속성 집합 메서드는 `IsDirty` 속성을 유지 해야 함을 나타내려면 true로 설정 합니다. 지 속성은 프로젝트나 솔루션을 저장할 때 발생 합니다.

5. SimpleProject 솔루션을 다시 빌드하고 디버깅을 시작 합니다. 실험적 인스턴스가 표시 되어야 합니다.

6. 실험적 인스턴스에서 새 SimpleProject 응용 프로그램을 만듭니다.

7. Visual Studio는 프로젝트 팩터리를 호출 하 여 Visual Studio 템플릿을 사용 하 여 프로젝트를 만듭니다. 새 *Program.cs* 파일이 코드 편집기에서 열립니다.

8. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. **속성 페이지** 대화 상자가 표시됩니다.

    ![간단한 프로젝트 속성 페이지](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>프로젝트 속성 페이지 테스트
이제 속성 값을 수정 하 고 변경할 수 있는지 여부를 테스트할 수 있습니다.

1. **MyConsoleApplication 속성 페이지** 대화 상자에서 **Defaultnamespace** 를 **MyApplication**로 변경 합니다.

2. **OutputType** 속성을 선택한 다음 **클래스 라이브러리**를 선택 합니다.

3. **적용**, **확인**을 차례로 클릭합니다.

4. **속성 페이지** 대화 상자를 다시 열고 변경 내용이 유지 되었는지 확인 합니다.

5. Visual Studio의 실험적 인스턴스를 닫습니다.

6. 실험적 인스턴스를 다시 엽니다.

7. **속성 페이지** 대화 상자를 다시 열고 변경 내용이 유지 되었는지 확인 합니다.

8. Visual Studio의 실험적 인스턴스를 닫습니다.
    ![실험적 인스턴스를 닫습니다.](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
