---
title: 기본 프로젝트 시스템 만들기, 1부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739729"
---
# <a name="create-a-basic-project-system-part-1"></a>기본 프로젝트 시스템 만들기, 1부
Visual Studio에서 프로젝트는 개발자가 소스 코드 파일 및 기타 자산을 구성하는 데 사용하는 컨테이너입니다. 프로젝트는 **솔루션 탐색기에서**솔루션의 자식으로 나타납니다. 프로젝트를 통해 소스 코드를 구성, 빌드, 디버깅 및 배포하고 웹 서비스, 데이터베이스 및 기타 리소스에 대한 참조를 만들 수 있습니다.

 프로젝트는 프로젝트 파일(예: Visual C# 프로젝트에 대한 *.csproj* 파일)에 정의됩니다. 고유한 프로젝트 파일 이름 확장명을 포함하는 고유한 프로젝트 유형을 만들 수 있습니다. 프로젝트 유형에 대한 자세한 내용은 [프로젝트 유형을](../extensibility/internals/project-types.md)참조하십시오.

> [!NOTE]
> 사용자 지정 프로젝트 유형으로 Visual Studio를 확장해야 하는 경우 프로젝트 시스템을 처음부터 빌드하는 데 여러 가지 장점이 있는 [VSPS(Visual Studio](https://github.com/Microsoft/VSProjectSystem) 프로젝트 시스템)를 활용하는 것이 좋습니다.
>
> - 더 쉬운 온보딩.  기본 프로젝트 시스템에도 수만 줄의 코드가 필요합니다.  VSPS를 활용하면 필요에 맞게 사용자 지정할 준비가 되기 전에 몇 번의 클릭만으로 온보딩 비용을 절감할 수 있습니다.
> - 유지 보수가 용이합니다.  VSPS를 활용하면 자체 시나리오만 유지관리하면 됩니다.  모든 프로젝트 시스템 인프라의 유지 를 처리합니다.
>
>   Visual Studio 2013보다 오래된 Visual Studio 버전을 대상으로 해야 하는 경우 Visual Studio 확장에서 VSPS를 활용할 수 없습니다.  이 경우 이 연습은 시작하기에 좋은 장소입니다.

 이 연습에서는 프로젝트 파일 이름 확장자 *.myproj가*있는 프로젝트 형식을 만드는 방법을 보여 주며 이 연습은 기존 Visual C# 프로젝트 시스템에서 차용합니다.

> [!NOTE]
> 확장 프로젝트의 자세한 예는 [VSSDK 샘플을](https://github.com/Microsoft/VSSDK-Extensibility-Samples)참조하십시오.

 이 연습에서는 이러한 작업을 수행하는 방법을 설명합니다.

- 기본 프로젝트 유형을 만듭니다.

- 기본 프로젝트 템플릿을 만듭니다.

- Visual Studio를 통해 프로젝트 템플릿을 등록합니다.

- 새 프로젝트 대화 상자를 연 다음 템플릿을 사용하여 **프로젝트** 인스턴스를 만듭니다.

- 프로젝트 시스템에 대한 프로젝트 팩터리를 만듭니다.

- 프로젝트 시스템에 대한 프로젝트 노드를 만듭니다.

- 프로젝트 시스템에 대한 사용자 지정 아이콘을 추가합니다.

- 기본 템플릿 매개 변수 대체를 구현합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

 또한 프로젝트에 대한 [관리되는 패키지 프레임워크의](https://github.com/tunnelvisionlabs/MPFProj10)소스 코드를 다운로드해야 합니다. 만들려는 솔루션에 액세스할 수 있는 위치로 파일을 추출합니다.

## <a name="create-a-basic-project-type"></a>기본 프로젝트 유형 만들기
 **SimpleProject라는**C# VSIX 프로젝트를 만듭니다. (파일**File** > **새** > **프로젝트** 다음 시각적 **C #** > **확장성** > **VSIX 프로젝트).** Visual Studio 패키지 프로젝트 항목 템플릿을 추가합니다(솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택한 다음 **확장성** > **Visual Studio 패키지로**이동). 파일 의 이름을 *단순 프로젝트 패키지*.

## <a name="creating-a-basic-project-template"></a>기본 프로젝트 템플릿 만들기
 이제 이 기본 VSPackage를 수정하여 새로운 *.myproj* 프로젝트 유형을 구현할 수 있습니다. *.myproj* 프로젝트 유형을 기반으로 하는 프로젝트를 만들려면 Visual Studio에서 새 프로젝트에 추가할 파일, 리소스 및 참조를 알아야 합니다. 이 정보를 제공하려면 프로젝트 파일을 프로젝트 템플릿 폴더에 넣습니다. 사용자가 *.myproj* 프로젝트를 사용하여 프로젝트를 만들면 파일이 새 프로젝트에 복사됩니다.

### <a name="to-create-a-basic-project-template"></a>기본 프로젝트 템플릿을 만들려면

1. 프로젝트에 세 개의 폴더를 추가하고 다른 폴더 아래에 하나씩 *추가합니다.* (솔루션 **탐색기에서** **SimpleProject** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가를**가리키고 **새 폴더**를 클릭합니다. 폴더 의 이름을 *템플릿으로 지정합니다.* 템플릿 폴더에 *프로젝트*라는 폴더를 추가 *합니다.* *프로젝트* 폴더에 SimpleProject라는 폴더를 *추가합니다.*

2. *템플릿\프로젝트\SimpleProject* 폴더에서 *SimpleProject.ico라는*아이콘으로 사용할 비트맵 이미지 파일을 추가합니다. **추가를**클릭하면 아이콘 편집기가 열립니다.

3. 아이콘을 돋보이게 합니다. 이 아이콘은 연습의 후반부새 **프로젝트** 대화 상자에 나타납니다.

    ![간단한 프로젝트 아이콘](../extensibility/media/simpleprojicon.png "심플프로지아이콘")

4. 아이콘을 저장하고 아이콘 편집기 닫습니다.

5. *템플릿\프로젝트\SimpleProject* 폴더에 *Program.cs*라는 **클래스** 항목을 추가 합니다.

6. 기존 코드를 다음 줄로 바꿉니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   > 이것은 *Program.cs* 코드의 최종 형식이 아닙니다. 대체 매개 변수는 이후 단계에서 처리됩니다. 컴파일 오류가 표시될 수 있지만 파일의 **BuildAction이** **콘텐츠인**한 평소와 같이 프로젝트를 빌드하고 실행할 수 있어야 합니다.

7. 파일을 저장합니다.

8. *속성* 폴더에서 *AssemblyInfo.cs* 파일을 *Project\SimpleProject* 폴더로 복사합니다.

9. *프로젝트\SimpleProject* 폴더에서 *SimpleProject.myproj*라는 XML 파일을 추가합니다.

   > [!NOTE]
   > 이 유형의 모든 프로젝트에 대한 파일 이름 확장명은 *.myproj입니다.* 변경하려면 연습에서 언급된 모든 곳에서 변경해야 합니다.

10. 기존 콘텐츠를 다음 줄로 바꿉습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. 파일을 저장합니다.

12. **속성** 창에서 *AssemblyInfo.cs*, *Program.cs,* *SimpleProject.ico*및 *SimpleProject.myproj의* **빌드 작업을** **콘텐츠로**설정하고 **VSIX 속성에 포함을** **True로**설정합니다.

    이 프로젝트 템플릿은 디버그 구성과 릴리스 구성이 모두 있는 기본 Visual C# 프로젝트에 대해 설명합니다. 이 프로젝트에는 *AssemblyInfo.cs* 및 *Program.cs*두 개의 소스 파일과 여러 어셈블리 참조가 포함됩니다. 템플릿에서 프로젝트를 만들면 ProjectGuid 값이 자동으로 새 GUID로 바뀝뀝습니다.

    **솔루션 탐색기에서** **확장된 템플릿 폴더는** 다음과 같이 표시되어야 합니다.

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>기본 프로젝트 팩터리 만들기
 Visual Studio에 프로젝트 템플릿 폴더의 위치를 알려야 합니다. 이렇게 하려면 VSPackage를 빌드할 때 템플릿 위치가 시스템 레지스트리에 기록되도록 프로젝트 팩터리를 구현하는 VSPackage 클래스에 특성을 추가합니다. 먼저 프로젝트 팩터리 GUID로 식별되는 기본 프로젝트 팩터리를 만듭니다. 특성을 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 사용하여 프로젝트 팩터리를 `SimpleProjectPackage` 클래스에 연결합니다.

### <a name="to-create-a-basic-project-factory"></a>기본 프로젝트 팩터리작성

1. 프로젝트 팩터리용 GUID를 **만듭니다(도구** 메뉴에서 **GUID 만들기를**클릭) 다음 예제에서 GUID를 사용합니다. 이미 정의된 `PackageGuidString`섹션이 `SimpleProjectPackage` 있는 섹션 근처의 클래스에 GUID를 추가합니다. GUID는 GUID 형식과 문자열 형식모두여야 합니다. 결과 코드는 다음 예제와 유사해야 합니다.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. *SimpleProjectFactory.cs*라는 맨 위 *SimpleProject* 폴더에 클래스를 추가 합니다.

3. 다음 using 지시문을 추가합니다.

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. 클래스에 GUID 특성을 추가합니다. `SimpleProjectFactory` 특성의 값은 새 프로젝트 팩터리 GUID입니다.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   이제 프로젝트 템플릿을 등록할 수 있습니다.

### <a name="to-register-the-project-template"></a>프로젝트 템플릿을 등록하려면

1. *SimpleProjectPackage.cs*다음과 같이 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 클래스에 `SimpleProjectPackage` 특성을 추가합니다.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인합니다.

    다시 빌드는 프로젝트 템플릿을 등록합니다.

   매개 `defaultProjectExtension` `possibleProjectExtensions` 변수와 프로젝트 파일 이름 확장명 *(.myproj)로*설정됩니다. `projectTemplatesDirectory` 매개 변수는 템플릿 폴더의 상대 경로로 *설정됩니다.* 빌드 하는 동안이 경로 전체 빌드로 변환 되 고 프로젝트 시스템을 등록 하는 레지스트리에 추가 됩니다.

## <a name="test-the-template-registration"></a>템플릿 등록 테스트
 템플릿 등록은 Visual Studio에서 새 프로젝트 대화 상자에 템플릿 이름과 아이콘을 표시할 수 있도록 프로젝트 템플릿 폴더의 위치를 시각적 **스튜디오에** 알려줍니다.

### <a name="to-test-the-template-registration"></a>템플릿 등록을 테스트하려면

1. **F5를** 눌러 Visual Studio의 실험인스턴스디버깅을 시작합니다.

2. 실험 인스턴스에서 새로 만든 프로젝트 유형의 새 프로젝트를 만듭니다. 새 **프로젝트** 대화 **상자에는 설치 된 템플릿**아래에 **SimpleProject가** 표시됩니다.

   이제 등록된 프로젝트 팩터리가 있습니다. 그러나 아직 프로젝트를 만들 수 없습니다. 프로젝트 패키지와 프로젝트 팩터리는 함께 작동하여 프로젝트를 만들고 초기화합니다.

## <a name="add-the-managed-package-framework-code"></a>관리되는 패키지 프레임워크 코드 추가
 프로젝트 패키지와 프로젝트 팩터리 간의 연결을 구현합니다.

- 관리되는 패키지 프레임워크의 소스 코드 파일을 가져옵니다.

    1. SimpleProject 프로젝트를 언로드(솔루션 **탐색기에서**프로젝트 노드를 선택하고 상황에 맞는 메뉴에서 **프로젝트 언로드를**클릭합니다.) XML 편집기에서 프로젝트 파일을 엽니다.

    2. 프로젝트 파일에 다음 블록을 \<추가합니다(가져오기 블록 바로 위)>. 방금 `ProjectBasePath` 다운로드한 관리되는 패키지 프레임워크 코드에서 *ProjectBase.files* 파일의 위치로 설정합니다. 경로 이름에 백슬래시를 추가해야 할 수 있습니다. 그렇지 않으면 프로젝트가 관리되는 패키지 프레임워크 소스 코드를 찾지 못할 수 있습니다.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > 경로 끝에 있는 백슬래시를 잊지 마십시오.

    3. 프로젝트를 다시 로드합니다.

    4. 다음 어셈블리에 대한 참조를 추가합니다.

        - `Microsoft.VisualStudio.Designer.Interfaces`* \<(VSSDK 설치>\VisualStudioIntegration\일반 어셈블리\v2.0)*

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>프로젝트 팩터리 초기화

1. *SimpleProjectPackage.cs* 파일에 다음 `using` 지시문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. 에서 `Microsoft.VisualStudio.Package.ProjectPackage` `SimpleProjectPackage` 클래스를 파생합니다.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. 프로젝트 팩터리를 등록합니다. 바로 그 직후의 `SimpleProjectPackage.Initialize` `base.Initialize`메서드에 다음 줄을 추가합니다.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. 추상 속성 `ProductUserContext`구현 :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. *SimpleProjectFactory.cs*기존 `using` 지시문 `using` 다음에 다음 지시문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. 에서 `ProjectFactory` `SimpleProjectFactory` 클래스를 파생합니다.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. 클래스에 다음 더미 메서드를 추가합니다. `SimpleProjectFactory` 이 메서드는 이후 섹션에서 구현합니다.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. 클래스에 다음 필드와 생성기를 추가합니다. `SimpleProjectFactory` 이 `SimpleProjectPackage` 참조는 서비스 공급자 사이트를 설정하는 데 사용할 수 있도록 개인 필드에 캐시됩니다.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인합니다.

## <a name="test-the-project-factory-implementation"></a>프로젝트 공장 구현 테스트
 프로젝트 팩터리 구현에 대한 생성자가 호출되는지 여부를 테스트합니다.

### <a name="to-test-the-project-factory-implementation"></a>프로젝트 팩터리 구현을 테스트하려면

1. *SimpleProjectFactory.cs* 파일에서 `SimpleProjectFactory` 생성자의 다음 줄에 중단점을 설정합니다.

    ```csharp
    this.package = package;
    ```

2. **F5를** 눌러 Visual Studio의 실험 인스턴스를 시작합니다.

3. 실험 인스턴스에서 새 프로젝트를 만들기 시작합니다. 새 **프로젝트** 대화 상자에서 **SimpleProject** 프로젝트 유형을 선택한 다음 **확인을**클릭합니다. 중단점에서 실행이 중지됩니다.

4. 중단점을 지우고 디버깅을 중지합니다. 아직 프로젝트 노드를 만들지 않았기 때문에 프로젝트 만들기 코드는 여전히 예외를 throw합니다.

## <a name="extend-the-projectnode-class"></a>ProjectNode 클래스 확장
 이제 `SimpleProjectNode` 클래스에서 파생되는 클래스를 구현할 `ProjectNode` 수 있습니다. 기본 `ProjectNode` 클래스는 프로젝트 생성의 다음 작업을 처리합니다.

- 프로젝트 템플릿 파일인 *SimpleProject.myproj를*새 프로젝트 폴더에 복사합니다. 새 **프로젝트** 대화 상자에 입력된 이름에 따라 복사본이름이 바뀝니다. `ProjectGuid` 속성 값이 새 GUID로 대체됩니다.

- 프로젝트 템플릿 파일인 *SimpleProject.myproj의*MSBuild 요소를 트래버스하고 요소를 찾습니다. `Compile` 각 `Compile` 대상 파일에 대해 파일을 새 프로젝트 폴더에 복사합니다.

  파생 클래스는 `SimpleProjectNode` 다음 작업을 처리합니다.

- **솔루션 탐색기에서** 프로젝트 및 파일 노드에 대한 아이콘을 만들거나 선택할 수 있습니다.

- 추가 프로젝트 템플릿 매개 변수 대체를 지정할 수 있습니다.

### <a name="to-extend-the-projectnode-class"></a>ProjectNode 클래스를 확장하려면

1. `SimpleProjectNode.cs`(이)라는 클래스를 추가합니다.

2. 기존 코드를 다음 코드로 바꿉니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   이 `SimpleProjectNode` 클래스 구현에는 다음과 같은 재정의된 메서드가 있습니다.

- `ProjectGuid`을 통해 프로젝트 팩터리 GUID를 반환합니다.

- `ProjectType`프로젝트 유형의 지역화된 이름을 반환합니다.

- `AddFileFromTemplate`을 사용하여 선택한 파일을 템플릿 폴더에서 대상 프로젝트로 복사합니다. 이 메서드는 이후 섹션에서 추가로 구현됩니다.

  `SimpleProjectNode` 생성자와 마찬가지로 `SimpleProjectFactory` 생성자는 나중에 사용할 수 위해 개인 필드에 `SimpleProjectPackage` 참조를 캐시합니다.

  클래스를 `SimpleProjectFactory` 클래스에 `SimpleProjectNode` 연결하려면 메서드에서 새 `SimpleProjectNode` 메서드를 `SimpleProjectFactory.CreateProject` 인스턴스화하고 나중에 사용할 수 있도록 개인 필드에 캐시해야 합니다.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>프로젝트 팩터리 클래스와 노드 클래스를 연결하려면

1. *SimpleProjectFactory.cs* 파일에서 다음 `using` 지시문을 추가합니다.

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. 다음 `SimpleProjectFactory.CreateProject` 코드를 사용하여 메서드를 바꿉니다.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인합니다.

## <a name="test-the-projectnode-class"></a>ProjectNode 클래스 테스트
 프로젝트 팩터리에서 프로젝트 계층 구조를 만드는지 여부를 확인합니다.

### <a name="to-test-the-projectnode-class"></a>ProjectNode 클래스를 테스트하려면

1. **F5** 키를 눌러 디버깅을 시작합니다. 실험 인스턴스에서 새 SimpleProject를 만듭니다.

2. Visual Studio는 프로젝트를 만들려면 프로젝트 팩터리로 호출해야 합니다.

3. Visual Studio의 실험적 인스턴스를 닫습니다.

## <a name="add-a-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘 추가
 이전 섹션의 프로젝트 노드 아이콘은 기본 아이콘입니다. 사용자 지정 아이콘으로 변경할 수 있습니다.

### <a name="to-add-a-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 추가하려면

1. **리소스** 폴더에 *SimpleProjectNode.bmp*라는 비트맵 파일을 추가합니다.

2. **속성** 창에서 비트맵을 16x 16픽셀로 줄입니다. 비트맵을 차별화합니다.

    ![간단한 프로젝트 명령](../extensibility/media/simpleprojprojectcomm.png "심플프로즈프로젝트콤")

3. **속성** 창에서 비트맵의 **빌드 작업을** **포함된 리소스로**변경합니다.

4. *SimpleProjectNode.cs*다음 `using` 지시문을 추가합니다.

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. 클래스에 다음 정적 필드 및 `SimpleProjectNode` 생성기를 추가합니다.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. 클래스의 시작 부분에 다음 `SimpleProjectNode` 속성을 추가합니다.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. 인스턴스 생성자 다음 코드로 바꿉니다.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   정적 생성 `SimpleProjectNode` 중에 어셈블리 매니페스트 리소스에서 프로젝트 노드 비트맵을 검색하고 나중에 사용할 수 위해 개인 필드에 캐시합니다. 이미지 경로의 구문을 확인합니다. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 어셈블리에 포함된 매니페스트 리소스의 이름을 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 보려면 메서드를 사용합니다. 이 메서드가 어셈블리에 `SimpleProject` 적용되면 결과는 다음과 같이 되어야 합니다.

- *SimpleProject.리소스*

- *비주얼 스튜디오.프로젝트.리소스*

- *심플 프로젝트.VS패키지.리소스*

- *리소스.이미지리스.bmp*

- *마이크로소프트.비주얼스튜디오.프로젝트.돈트쇼다시디아로그.리소스*

- *마이크로소프트.비주얼스튜디오.프로젝트.보안경고디아로그.리소스*

- *심플 프로젝트.리소스.심플 프로젝트노드.bmp*

  인스턴스 생성 중에 `ProjectNode` 기본 클래스는 *Resources\imagelis.bmp에서*일반적으로 사용되는 16 x 16 비트맵이 포함된 *Resources.imagelis.bmp를*로드합니다. 이 비트맵 목록은 에서 `SimpleProjectNode` `ImageHandler.ImageList`사용할 수 있습니다. `SimpleProjectNode`프로젝트 노드 비트맵을 목록에 추가합니다. 이미지 목록에서 프로젝트 노드 비트맵의 오프셋은 나중에 public `ImageIndex` 속성값으로 사용하기 위해 캐시됩니다. Visual Studio는 이 속성을 사용하여 프로젝트 노드 아이콘으로 표시할 비트맵을 결정합니다.

## <a name="test-the-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘 테스트
 프로젝트 팩터리에서 사용자 지정 프로젝트 노드 아이콘이 있는 프로젝트 계층 구조를 만드는지 여부를 확인합니다.

### <a name="to-test-the-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 테스트하려면

1. 디버깅을 시작하고 실험 인스턴스에서 새 SimpleProject를 만듭니다.

2. 새로 만든 프로젝트에서 *SimpleProjectNode.bmp가* 프로젝트 노드 아이콘으로 사용된다는 것을 알 수 있습니다.

     ![간단한 프로젝트 새 프로젝트 노드](../extensibility/media/simpleprojnewprojectnode.png "심플프로뉴프로젝트노드")

3. 코드 편집기에서 *Program.cs*를 엽니다. 다음 코드와 유사한 소스 코드가 표시됩니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     템플릿 매개 변수$nameSpace$와 $className$에는 새 값이 없습니다. 다음 섹션에서 템플릿 매개 변수 대체를 구현하는 방법을 배웁니다.

## <a name="substitute-template-parameters"></a>템플릿 매개 변수 대체
 이전 섹션에서는 특성을 사용하여 프로젝트 템플릿을 Visual `ProvideProjectFactory` Studio에 등록했습니다. 이러한 방식으로 템플릿 폴더의 경로를 등록하면 클래스를 재정의하고 확장하여 기본 템플릿 `ProjectNode.AddFileFromTemplate` 매개 변수 대체를 활성화할 수 있습니다. 자세한 내용은 [새 프로젝트 생성: 두 번째 부](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)에서 를 참조하십시오.

 이제 클래스에 대체 `AddFileFromTemplate` 코드를 추가합니다.

### <a name="to-substitute-template-parameters"></a>템플릿 매개 변수를 대체하려면

1. *SimpleProjectNode.cs* 파일에 다음 `using` 지시문을 추가합니다.

   ```csharp
   using System.IO;
   ```

2. 다음 `AddFileFromTemplate` 코드를 사용하여 메서드를 바꿉니다.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. 할당 문 바로 직후에 메서드에서 `className` 중단점을 설정합니다.

   할당 문은 네임스페이스와 새 클래스 이름에 대한 적절한 값을 결정합니다. 두 `ProjectNode.FileTemplateProcessor.AddReplace` 메서드 호출은 이러한 새 값을 사용하여 해당 템플릿 매개 변수 값을 대체합니다.

## <a name="test-the-template-parameter-substitution"></a>템플릿 매개 변수 대체 테스트
 이제 템플릿 매개 변수 대체를 테스트할 수 있습니다.

### <a name="to-test-the-template-parameter-substitution"></a>템플릿 매개 변수 대체를 테스트하려면

1. 디버깅을 시작하고 실험 인스턴스에서 새 SimpleProject를 만듭니다.

2. 메서드의 중단점에서 실행이 `AddFileFromTemplate` 중지됩니다.

3. `nameSpace` 및 `className` 매개 변수에 대한 값을 검사합니다.

   - `nameSpace`\< *\템플릿\프로젝트\SimpleProject\SimpleProject.myproj* 프로젝트 템플릿 파일에서 루트네임스페이스> 요소의 값이 부여됩니다. 이 경우 값은 `MyRootNamespace`입니다.

   - `className`은 파일 이름 확장명없이 클래스 소스 파일 이름의 값이 부여됩니다. 이 경우 대상 폴더에 복사할 첫 번째 파일이 *AssemblyInfo.cs.* 따라서 className의 값은 `AssemblyInfo`.

4. 중단점을 제거하고 **F5를** 눌러 실행을 계속합니다.

    비주얼 스튜디오는 프로젝트 만들기를 완료해야 합니다.

5. 코드 편집기에서 *Program.cs*를 엽니다. 다음 코드와 유사한 소스 코드가 표시됩니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    네임스페이스는 이제 `MyRootNamespace` 이며 클래스 이름은 `Program`지금 .

6. 프로젝트 디버그를 시작합니다. 새 프로젝트는 "Hello VSX!!!"를 컴파일, 실행 및 표시해야 합니다. 콘솔 창에 표시합니다.

    ![간단한 프로젝트 명령](../extensibility/media/simpleprojcommand.png "심플프로즈커맨드")

   축하합니다! 기본 관리 되는 프로젝트 시스템을 구현 했습니다.
