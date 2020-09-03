---
title: 기본 프로젝트 시스템 만들기, 1 부 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20637fb47d85b7cb8341df22d056ffe44534835f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295484"
---
# <a name="creating-a-basic-project-system-part-1"></a>기본 프로젝트 시스템 만들기, 1부
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 프로젝트는 개발자가 소스 코드 파일 및 기타 자산을 구성 하는 데 사용 하는 컨테이너입니다. 프로젝트는 **솔루션 탐색기**에서 솔루션의 자식으로 표시 됩니다. 프로젝트를 사용 하 여 소스 코드를 구성, 빌드, 디버그 및 배포 하 고 웹 서비스, 데이터베이스 및 기타 리소스에 대 한 참조를 만들 수 있습니다.  
  
 프로젝트는 프로젝트 파일 (예: Visual c # 프로젝트의 .csproj 파일)에서 정의 됩니다. 고유한 프로젝트 파일 이름 확장명을 가진 고유한 프로젝트 형식을 만들 수 있습니다. 프로젝트 형식에 대 한 자세한 내용은 [프로젝트 형식](../extensibility/internals/project-types.md)을 참조 하세요.  
  
> [!NOTE]
> 사용자 지정 프로젝트 형식을 사용 하 여 Visual Studio를 확장 해야 하는 경우 프로젝트 시스템을 처음부터 빌드할 때 많은 이점을 제공 하는 [Visual Studio 프로젝트 시스템](https://github.com/Microsoft/VSProjectSystem) 을 활용 하는 것이 좋습니다.  
> 
> - 등록을 용이 하 게 합니다.  기본 프로젝트 시스템 에서도 수십 개의 코드 줄이 필요 합니다.  CPS를 활용 하면 요구에 맞게 사용자 지정할 준비가 되기 전에 몇 번의 클릭으로 등록 비용이 줄어듭니다.  
>   - 간편한 유지 관리.  CPS를 활용 하 여 자신만의 시나리오를 유지 관리 해야 합니다.  모든 프로젝트 시스템 인프라의 보존 처리 합니다.  
> 
>   Visual Studio 2013 보다 오래 된 Visual Studio 버전을 대상으로 해야 하는 경우 Visual Studio 확장에서 CPS를 활용할 수 없습니다.  이 경우에는이 연습을 시작할 수 있는 좋은 장소입니다.  
  
 이 연습에서는 프로젝트 파일 이름 확장명이. myproj 인 프로젝트 형식을 만드는 방법을 보여 줍니다. 이 연습은 기존 Visual c # 프로젝트 시스템에서 활용.  
  
> [!NOTE]
> 전체 언어 프로젝트 [시스템에 대](../misc/vssdk-samples.md)한 종단 간 샘플을 보려면 대상 시스템에서 IronPython 샘플 심층 이해를 참조 하세요.  
  
 이 연습에서는 다음 작업을 수행 하는 방법을 배웁니다.  
  
- 기본 프로젝트 형식을 만듭니다.  
  
- 기본 프로젝트 템플릿을 만듭니다.  
  
- Visual Studio에 프로젝트 템플릿을 등록 합니다.  
  
- **새 프로젝트** 대화 상자를 연 다음 템플릿을 사용 하 여 프로젝트 인스턴스를 만듭니다.  
  
- 프로젝트 시스템에 대 한 프로젝트 팩터리를 만듭니다.  
  
- 프로젝트 시스템에 대 한 프로젝트 노드를 만듭니다.  
  
- 프로젝트 시스템에 대 한 사용자 지정 아이콘을 추가 합니다.  
  
- 기본 템플릿 매개 변수 대체를 구현 합니다.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
 또한 [프로젝트에 대 한 관리 되는 패키지 프레임 워크](https://archive.codeplex.com/?p=mpfproj12)의 소스 코드도 다운로드 해야 합니다. 만들려는 솔루션에서 액세스할 수 있는 위치에 파일을 추출 합니다.  
  
## <a name="creating-a-basic-project-type"></a>기본 프로젝트 형식 만들기  
 **SimpleProject**라는 c # VSIX 프로젝트를 만듭니다. (**파일, 새로 만들기, 프로젝트** , **c #, 확장성, Visual Studio 패키지**). Visual Studio 패키지 프로젝트 항목 템플릿을 추가 합니다 (솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가/새 항목**을 선택한 다음 **확장성/Visual Studio 패키지**로 이동). 파일 이름을 **SimpleProjectPackage**로 합니다.  
  
## <a name="creating-a-basic-project-template"></a>기본 프로젝트 템플릿 만들기  
 이제이 기본 VSPackage을 수정 하 여 새. n e t 프로젝트 형식을 구현할 수 있습니다. . Myproj 프로젝트 형식을 기반으로 하는 프로젝트를 만들려면 Visual Studio에서 새 프로젝트에 추가할 파일, 리소스 및 참조를 알고 있어야 합니다. 이 정보를 제공 하려면 프로젝트 파일 폴더에 프로젝트 파일을 배치 합니다. 사용자가. myproj 프로젝트를 사용 하 여 프로젝트를 만들 때 파일이 새 프로젝트에 복사 됩니다.  
  
#### <a name="to-create-a-basic-project-template"></a>기본 프로젝트 템플릿을 만들려면  
  
1. 프로젝트에 세 개의 폴더 ( **Templates\Projects\SimpleProject**)를 추가 합니다. **솔루션 탐색기**에서 **SimpleProject** 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 폴더**를 클릭 합니다. 폴더 이름을 `Templates`서 무료 평가판 계정을 등록할 수 있습니다. **Templates** 폴더에 라는 폴더를 추가 `Projects` 합니다. **프로젝트** 폴더에서 라는 폴더를 추가 `SimpleProject` 합니다.  
  
2. **Projects\SimpleProject** 폴더에 라는 아이콘 파일을 추가 `SimpleProject.ico` 합니다. **추가**를 클릭 하면 아이콘 편집기가 열립니다.  
  
3. 아이콘을 고유한 것으로 만듭니다. 이 아이콘은 연습의 뒷부분에 있는 **새 프로젝트** 대화 상자에 나타납니다.  
  
    ![간단한 프로젝트 아이콘](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. 아이콘을 저장 하 고 아이콘 편집기를 닫습니다.  
  
5. **Projects\SimpleProject** 폴더에서 라는 **클래스** 항목을 추가 합니다 `Program.cs` .  
  
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
   > 이는 Program.cs 코드의 최종 형식이 아닙니다. 대체 매개 변수는 이후 단계에서 처리 됩니다. 컴파일 오류가 표시 될 수 있지만 **파일의 빌드** **내용이 콘텐츠**이면 평소와 같이 프로젝트를 빌드하고 실행할 수 있어야 합니다.  
  
7. 파일을 저장합니다.  
  
8. **Properties** 폴더에서 AssemblyInfo.cs 파일을 **Projects\SimpleProject** 폴더로 복사 합니다.  
  
9. **Projects\SimpleProject** 폴더에 이라는 XML 파일을 추가 `SimpleProject.myproj` 합니다.  
  
   > [!NOTE]
   > 이 형식의 모든 프로젝트에 대 한 파일 이름 확장명은. myproj입니다. 변경 하려는 경우 연습에서 언급 한 모든 위치에서 변경 해야 합니다.  
  
10. 기존 내용을 다음 줄로 바꿉니다.  
  
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
  
12. **속성** 창에서 AssemblyInfo.cs, Program.cs, SimpleProject 및 SimpleProject의 **빌드 작업** 을 **콘텐츠**로 설정 하 고 **VSIX 속성에 포함** 을 **True**로 설정 합니다.  
  
    이 프로젝트 템플릿은 디버그 구성과 릴리스 구성이 모두 포함 된 기본 Visual c # 프로젝트를 설명 합니다. 프로젝트에는 두 개의 소스 파일, AssemblyInfo.cs 및 Program.cs와 여러 개의 어셈블리 참조가 포함 됩니다. 템플릿에서 프로젝트를 만들면 ProjectGuid 값이 자동으로 새 GUID로 바뀝니다.  
  
    **솔루션 탐색기**확장 된 **템플릿** 폴더는 다음과 같이 표시 됩니다.  
  
    템플릿  
  
    프로젝트  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject  
  
    SimpleProject  
  
## <a name="creating-a-basic-project-factory"></a>기본 프로젝트 팩터리 만들기  
 Visual Studio에서 프로젝트 템플릿 폴더의 위치를 알려 주어 야 합니다. 이렇게 하려면 VSPackage를 빌드할 때 템플릿 위치가 시스템 레지스트리에 기록 되도록 프로젝트 팩터리를 구현 하는 VSPackage 클래스에 특성을 추가 합니다. 먼저 프로젝트 팩터리 GUID로 식별 되는 기본 프로젝트 팩터리를 만듭니다. 특성을 사용 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 하 여 프로젝트 팩터리를 SimpleProjectPackage 클래스에 연결 합니다.  
  
#### <a name="to-create-a-basic-project-factory"></a>기본 프로젝트 팩터리를 만들려면  
  
1. 코드 편집기에서 SimpleProjectPackageGuids.cs를 엽니다.  
  
2. 프로젝트 팩터리의 Guid를 만들거나 ( **도구** 메뉴에서 **guid 만들기**를 클릭 하 여) 다음 예제에서 사용 합니다. Guid를 SimpleProjectPackageGuids 클래스에 추가 합니다. Guid는 GUID 형식 및 문자열 형식 이어야 합니다. 결과 코드는 다음 예제와 유사 합니다.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. 라는 top **SimpleProject** 폴더에 클래스를 추가 `SimpleProjectFactory.cs` 합니다.  
  
4. 다음 using 명령문을 추가합니다.  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Guid 특성을 SimpleProjectFactory 클래스에 추가 합니다. 특성의 값은 새 프로젝트 팩터리 GUID입니다.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   이제 프로젝트 템플릿을 등록할 수 있습니다.  
  
#### <a name="to-register-the-project-template"></a>프로젝트 템플릿을 등록 하려면  
  
1. SimpleProjectPackage.cs에서 <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> 다음과 같이 SimpleProjectPackage 클래스에 특성을 추가 합니다.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인 합니다.  
  
    다시 작성 하면 프로젝트 템플릿이 등록 됩니다.  
  
   및 매개 변수는 `defaultProjectExtension` `possibleProjectExtensions` 프로젝트 파일 이름 확장명 (. myproj)으로 설정 됩니다. `projectTemplatesDirectory`매개 변수는 템플릿 폴더의 상대 경로로 설정 됩니다. 빌드 중에이 경로는 전체 빌드로 변환 되어 레지스트리에 추가 되어 프로젝트 시스템을 등록 합니다.  
  
## <a name="testing-the-template-registration"></a>템플릿 등록 테스트  
 템플릿 등록을 통해 visual studio가 **새 프로젝트** 대화 상자에 템플릿 이름 및 아이콘을 표시할 수 있도록 visual studio에서 프로젝트 템플릿 폴더의 위치를 알 수 있습니다.  
  
#### <a name="to-test-the-template-registration"></a>템플릿 등록을 테스트 하려면  
  
1. F5 키를 눌러 Visual Studio의 실험적 인스턴스 디버깅을 시작 합니다.  
  
2. 실험적 인스턴스에서 새로 만든 프로젝트 형식에 대 한 새 프로젝트를 만듭니다. **새 프로젝트** 대화 상자의 **설치 된 템플릿**아래에 **SimpleProject** 이 표시 됩니다.  
  
   이제 등록 된 프로젝트 팩터리가 있습니다. 그러나 아직 프로젝트를 만들 수는 없습니다. 프로젝트 패키지와 프로젝트 팩터리는 함께 작동 하 여 프로젝트를 만들고 초기화 합니다.  
  
## <a name="add-the-managed-package-framework-code"></a>관리 되는 패키지 프레임 워크 코드 추가  
 프로젝트 패키지와 프로젝트 팩터리 간의 연결을 구현 합니다.  
  
- 관리 되는 패키지 프레임 워크에 대 한 소스 코드 파일을 가져옵니다.  
  
    1. SimpleProject 프로젝트를 언로드합니다 ( **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 상황에 맞는 메뉴에서 **프로젝트 언로드**를 클릭 한 다음 XML 편집기에서 프로젝트 파일을 엽니다.  
  
    2. 프로젝트 파일에 다음 블록을 추가 합니다 (블록 바로 위 \<Import> ). ProjectBasePath를 방금 다운로드 한 관리 되는 패키지 프레임 워크 코드에서 ProjectBase. files 파일의 위치로 설정 합니다. 경로 이름에 백슬래시를 추가 해야 할 수도 있습니다. 그렇지 않은 경우 프로젝트에서 관리 되는 패키지 프레임 워크 코드를 찾지 못할 수 있습니다.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > 경로 끝에 백슬래시를 잊지 마십시오.  
  
    3. 프로젝트를 다시 로드 합니다.  
  
    4. 다음 어셈블리에 대한 참조를 추가합니다.  
  
        - VisualStudio ( \<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0) (영문)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>프로젝트 팩터리를 초기화 하려면  
  
1. SimpleProjectPackage.cs 파일에서 다음 문을 추가 합니다 `using` .  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. 에서 클래스를 파생 시킵니다 `SimpleProjectPackage` `Microsoft.VisualStudio.Package.ProjectPackage` .  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. 프로젝트 팩터리를 등록 합니다. 다음 줄을 `SimpleProjectPackage.Initialize` 메서드에 추가 `base.Initialize` 합니다.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. 추상 속성을 구현 합니다 `ProductUserContext` .  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. SimpleProjectFactory.cs에서 `using` 기존 문 뒤에 다음 문을 추가 합니다 `using` .  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. 에서 클래스를 파생 시킵니다 `SimpleProjectFactory` `ProjectFactory` .  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. 다음 더미 메서드를 클래스에 추가 합니다 `SimpleProjectFactory` . 이후 섹션에서이 메서드를 구현 합니다.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. 클래스에 다음 필드 및 생성자를 추가 `SimpleProjectFactory` 합니다. 이 `SimpleProjectPackage` 참조는 서비스 공급자 사이트를 설정 하는 데 사용할 수 있도록 전용 필드에 캐시 됩니다.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인 합니다.  
  
## <a name="testing-the-project-factory-implementation"></a>프로젝트 팩터리 구현 테스트  
 프로젝트 팩터리 구현에 대 한 생성자가 호출 되는지 여부를 테스트 합니다.  
  
#### <a name="to-test-the-project-factory-implementation"></a>프로젝트 팩터리 구현을 테스트 하려면  
  
1. SimpleProjectFactory.cs 파일에서 생성자의 다음 줄에 중단점을 설정 `SimpleProjectFactory` 합니다.  
  
    ```  
    this.package = package;  
    ```  
  
2. F5 키를 눌러 Visual Studio의 실험적 인스턴스를 시작 합니다.  
  
3. 실험적 인스턴스에서 새 프로젝트 만들기를 시작 합니다. **새 프로젝트** 대화 상자에서 SimpleProject 프로젝트 형식을 선택 하 고 **확인**을 클릭 합니다. 중단점에서 실행이 중지됩니다.  
  
4. 중단점을 지우고 디버깅을 중지 합니다. 프로젝트 노드를 아직 만들지 않았기 때문에 프로젝트 만들기 코드에서 여전히 예외를 throw 합니다.  
  
## <a name="extending-the-project-node-class"></a>프로젝트 노드 클래스 확장  
 이제 클래스 `SimpleProjectNode` 에서 파생 되는 클래스를 구현할 수 있습니다 `ProjectNode` . `ProjectNode`기본 클래스는 다음과 같은 프로젝트 생성 작업을 처리 합니다.  
  
- 프로젝트 템플릿 파일 (SimpleProject)을 새 프로젝트 폴더에 복사 합니다. **새 프로젝트** 대화 상자에 입력 한 이름에 따라 복사본의 이름이 바뀝니다. `ProjectGuid`속성 값은 새 GUID로 대체 됩니다.  
  
- 프로젝트 템플릿 파일 (SimpleProject)의 MSBuild 요소를 트래버스 하 고 요소를 찾습니다 `Compile` . 각 `Compile` 대상 파일에 대해 파일을 새 프로젝트 폴더에 복사 합니다.  
  
  파생 된 `SimpleProjectNode` 클래스는 다음과 같은 작업을 처리 합니다.  
  
- **솔루션 탐색기** 의 프로젝트 및 파일 노드에 대 한 아이콘을 만들거나 선택할 수 있습니다.  
  
- 추가 프로젝트 템플릿 매개 변수 대체가 지정 되도록 설정 합니다.  
  
#### <a name="to-extend-the-project-node-class"></a>프로젝트 노드 클래스를 확장 하려면  
  
1. 
  
2. `SimpleProjectNode.cs`(이)라는 클래스를 추가합니다.  
  
3. 기존 코드를 다음 코드로 바꿉니다.  
  
   ```  
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
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
   이 `SimpleProjectNode` 클래스 구현에는 다음과 같은 재정의 된 메서드가 있습니다.  
  
- `ProjectGuid`-프로젝트 팩터리 GUID를 반환 합니다.  
  
- `ProjectType`-프로젝트 형식의 지역화 된 이름을 반환 합니다.  
  
- `AddFileFromTemplate`-선택한 파일을 템플릿 폴더에서 대상 프로젝트로 복사 합니다. 이 메서드는 이후 섹션에서 추가로 구현 됩니다.  
  
  생성자 `SimpleProjectNode` 와 마찬가지로 생성자는 `SimpleProjectFactory` `SimpleProjectPackage` 나중에 사용 하기 위해 전용 필드에 참조를 캐시 합니다.  
  
  클래스를 `SimpleProjectFactory` 클래스에 연결 하려면 `SimpleProjectNode` 메서드에 새를 인스턴스화하고 `SimpleProjectNode` `SimpleProjectFactory.CreateProject` 나중에 사용할 수 있도록 전용 필드에 캐시 해야 합니다.  
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>프로젝트 팩터리 클래스와 node 클래스를 연결 하려면  
  
1. SimpleProjectFactory.cs 파일에서 다음 문을 추가 합니다 `using` .  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. `SimpleProjectFactory.CreateProject`다음 코드를 사용 하 여 메서드를 바꿉니다.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. 솔루션을 다시 빌드하고 오류 없이 빌드되는지 확인 합니다.  
  
## <a name="testing-the-project-node-class"></a>프로젝트 노드 클래스 테스트  
 프로젝트 팩터리를 테스트 하 여 프로젝트 계층 구조가 생성 되는지 확인 합니다.  
  
#### <a name="to-test-the-project-node-class"></a>프로젝트 노드 클래스를 테스트 하려면  
  
1. F5 키를 눌러 디버깅을 시작합니다. 실험적 인스턴스에서 새 SimpleProject을 만듭니다.  
  
2. Visual Studio는 프로젝트 팩터리를 호출 하 여 프로젝트를 만들어야 합니다.  
  
3. Visual Studio의 실험적 인스턴스를 닫습니다.  
  
## <a name="adding-a-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 추가 아이콘  
 이전 섹션의 프로젝트 노드 아이콘은 기본 아이콘입니다. 사용자 지정 아이콘으로 변경할 수 있습니다.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 추가 하려면  
  
1. **Resources** 폴더에 SimpleProjectNode.bmp 라는 비트맵 파일을 추가 합니다.  
  
2. **속성** 창에서 비트맵을 16 x 16 픽셀로 줄입니다. 비트맵을 고유한 것으로 만듭니다.  
  
    ![간단한 프로젝트 명령](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. **속성** 창에서 비트맵의 **빌드 작업** 을 **포함 리소스**로 변경 합니다.  
  
4. SimpleProjectNode.cs에서 다음 문을 추가 합니다 `using` .  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. 클래스에 다음 정적 필드 및 생성자를 추가 합니다 `SimpleProjectNode` .  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. 클래스의 시작 부분에 다음 속성을 추가 `SimpleProjectNode` 합니다.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. 인스턴스 생성자를 다음 코드로 바꿉니다.  
  
   ```  
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
  
   정적 생성 중에는 `SimpleProjectNode` 어셈블리 매니페스트 리소스에서 프로젝트 노드 비트맵을 검색 하 고 나중에 사용할 수 있도록 전용 필드에 캐시 합니다. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>이미지 경로의 구문을 확인 합니다. 어셈블리에 포함 된 매니페스트 리소스의 이름을 확인 하려면 메서드를 사용 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 합니다. 이 메서드가 어셈블리에 적용 되는 경우 결과는 다음과 같아야 합니다 `SimpleProject` .  
  
- SimpleProject  
  
- VisualStudio  
  
- SimpleProject. VSPackage  
  
- Resources.imagelis.bmp  
  
- VisualStudio. DontShowAgainDialog  
  
- VisualStudio. SecurityWarningDialog  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  인스턴스를 생성 하는 동안 `ProjectNode` 기본 클래스는 Resources\imagelis.bmp에서 일반적으로 사용 되는 16 x 16 비트맵을 포함 하는 Resources.imagelis.bmp를 로드 합니다. 이 비트맵 목록은를 `SimpleProjectNode` ImageHandler. ImageList로 사용할 수 있습니다. `SimpleProjectNode` 프로젝트 노드 비트맵을 목록에 추가 합니다. 이미지 목록에서 프로젝트 노드 비트맵의 오프셋은 나중에 공용 속성의 값으로 사용 하기 위해 캐시 됩니다 `ImageIndex` . Visual Studio는이 속성을 사용 하 여 프로젝트 노드 아이콘으로 표시할 비트맵을 결정 합니다.  
  
## <a name="testing-the-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘 테스트  
 프로젝트 팩터리를 테스트 하 여 사용자 지정 프로젝트 노드 아이콘이 있는 프로젝트 계층 구조를 만드는 지 여부를 확인 합니다.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>사용자 지정 프로젝트 노드 아이콘을 테스트 하려면  
  
1. 디버깅을 시작 하 고 실험적 인스턴스에서 새 SimpleProject을 만듭니다.  
  
2. 새로 만든 프로젝트에서 SimpleProjectNode.bmp가 프로젝트 노드 아이콘으로 사용 되는지 확인 합니다.  
  
     ![간단한 프로젝트 새 프로젝트 노드](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. 코드 편집기에서 Program.cs를 엽니다. 소스 코드는 다음 코드와 유사 하 게 표시 됩니다.  
  
    ```  
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
  
     템플릿 매개 변수 $nameSpace $ 및 $className $는 새 값을 포함 하지 않습니다. 다음 섹션에서 템플릿 매개 변수 대체를 구현 하는 방법에 대해 알아봅니다.  
  
## <a name="substituting-template-parameters"></a>템플릿 매개 변수 대체  
 이전 섹션에서는 특성을 사용 하 여 Visual Studio에 프로젝트 템플릿을 등록 `ProvideProjectFactory` 했습니다. 이러한 방식으로 템플릿 폴더의 경로를 등록 하면 클래스를 재정의 하 고 확장 하 여 기본 템플릿 매개 변수 대체를 사용 하도록 설정할 수 있습니다 `ProjectNode.AddFileFromTemplate` . 자세한 내용은 [새 프로젝트 생성: 내부에서 2 부를](../extensibility/internals/new-project-generation-under-the-hood-part-two.md)참조 하세요.  
  
 이제 클래스에 대체 코드를 추가 `AddFileFromTemplate` 합니다.  
  
#### <a name="to-substitute-template-parameters"></a>템플릿 매개 변수를 대체 하려면  
  
1. SimpleProjectNode.cs 파일에서 다음 문을 추가 합니다 `using` .  
  
   ```  
   using System.IO;  
   ```  
  
2. `AddFileFromTemplate`다음 코드를 사용 하 여 메서드를 바꿉니다.  
  
   ```  
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
  
3. 메서드에 대입문을 설정 `className` 합니다.  
  
   대입문은 네임 스페이스 및 새 클래스 이름에 대 한 적절 한 값을 결정 합니다. 두 `ProjectNode.FileTemplateProcessor.AddReplace` 메서드 호출에서는 이러한 새 값을 사용 하 여 해당 템플릿 매개 변수 값을 바꿉니다.  
  
## <a name="testing-the-template-parameter-substitution"></a>템플릿 매개 변수 대체 테스트  
 이제 템플릿 매개 변수 대체를 테스트할 수 있습니다.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>템플릿 매개 변수 대체를 테스트 하려면  
  
1. 디버깅을 시작 하 고 실험적 인스턴스에서 새 SimpleProject을 만듭니다.  
  
2. 메서드의 중단점에서 실행이 중지 `AddFileFromTemplate` 됩니다.  
  
3. `nameSpace`및 매개 변수의 값을 검사 `className` 합니다.  
  
   - `nameSpace` 에는 \<RootNamespace> \Templates\Projects\SimpleProject\SimpleProject.myproj 프로젝트 템플릿 파일의 요소 값이 지정 됩니다. 이 경우 값은 "MyRootNamespace"입니다.  
  
   - `className` 에는 파일 이름 확장명이 없는 클래스 소스 파일 이름의 값이 지정 됩니다. 이 경우 대상 폴더에 복사 되는 첫 번째 파일은 AssemblyInfo.cs입니다. 따라서 className의 값은 "AssemblyInfo"입니다.  
  
4. 중단점을 제거 하 고 F5 키를 눌러 실행을 계속 합니다.  
  
    Visual Studio에서 프로젝트 만들기를 완료 해야 합니다.  
  
5. 코드 편집기에서 Program.cs를 엽니다. 소스 코드는 다음 코드와 유사 하 게 표시 됩니다.  
  
   ```  
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
  
    네임 스페이스는 이제 "MyRootNamespace"이 고 클래스 이름은 "Program"입니다.  
  
6. 프로젝트 디버그를 시작합니다. 새 프로젝트를 컴파일하고 실행 하 고 "Hello VSX!!!"를 표시 해야 합니다. 콘솔 창에 표시합니다.  
  
    ![간단한 프로젝트 명령](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   축하합니다! 기본 관리 되는 프로젝트 시스템을 구현 했습니다.
