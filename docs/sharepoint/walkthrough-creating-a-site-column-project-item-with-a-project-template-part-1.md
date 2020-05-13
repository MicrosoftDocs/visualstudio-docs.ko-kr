---
title: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 843d56482a82c2a8210de50455753c9703698503
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557848"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부
  SharePoint 프로젝트는 하나 이상의 SharePoint 프로젝트 항목에 대 한 컨테이너입니다. 사용자 고유의 SharePoint 프로젝트 항목 형식을 만든 다음 프로젝트 템플릿에 연결 하 여 Visual Studio에서 SharePoint 프로젝트 시스템을 확장할 수 있습니다. 이 연습에서는 사이트 열을 만들기 위한 프로젝트 항목 형식을 정의 하 고, 사이트 열 프로젝트 항목을 포함 하는 새 프로젝트를 만드는 데 사용할 수 있는 프로젝트 템플릿을 만듭니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사이트 열에 대 한 새 SharePoint 프로젝트 항목 형식을 정의 하는 Visual Studio 확장을 만듭니다. 프로젝트 항목 형식에는 **속성** 창에 표시 되는 간단한 사용자 지정 속성이 포함 됩니다.

- 프로젝트 항목에 대 한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트 템플릿 만들기

- VSIX ([!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension) 패키지를 빌드하여 프로젝트 템플릿과 확장 어셈블리를 배포 합니다.

- 프로젝트 항목 디버깅 및 테스트

  이는 독립 실행형 연습입니다. 이 연습을 완료 한 후 프로젝트 템플릿에 마법사를 추가 하 여 프로젝트 항목을 향상 시킬 수 있습니다. 자세한 내용은 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)를 참조 하세요.

> [!NOTE]
> 일련의 샘플 워크플로는 [SharePoint workflow samples](/sharepoint/dev/general-development/sharepoint-workflow-samples)를 참조 하십시오.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Microsoft Windows, SharePoint 및 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- SharePoint의 사이트 열입니다. 자세한 내용은 [열](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))을 참조 하세요.

- Visual Studio의 프로젝트 템플릿 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음 세 개의 프로젝트를 만들어야 합니다.

- VSIX 프로젝트입니다. 이 프로젝트는 VSIX 패키지를 만들어 사이트 열 프로젝트 항목 및 프로젝트 템플릿을 배포 합니다.

- 프로젝트 템플릿 프로젝트입니다. 이 프로젝트는 사이트 열 프로젝트 항목을 포함 하는 새 SharePoint 프로젝트를 만드는 데 사용할 수 있는 프로젝트 템플릿을 만듭니다.

- 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 사이트 열 프로젝트 항목의 동작을 정의 하는 Visual Studio 확장을 구현 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 4.5** 이 선택 되어 있는지 확인 합니다.

4. **Visual Basic** 또는 **시각적 C#**  노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

5. 프로젝트 템플릿 목록에서 **VSIX 프로젝트**를 선택 합니다.

6. **이름** 상자에 **SiteColumnProjectItem**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **SiteColumnProjectItem** 프로젝트를 **솔루션 탐색기**에 추가 합니다.

#### <a name="to-create-the-project-template-project"></a>프로젝트 템플릿 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 4.5** 이 선택 되어 있는지 확인 합니다.

3. **시각적 개체 C#**  또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

4. 프로젝트 템플릿 목록  **C# 에서 프로젝트 템플릿 또는** **Visual Basic 프로젝트 템플릿** 템플릿을 선택 합니다.

5. **이름** 상자에 **SiteColumnProjectTemplate**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **SiteColumnProjectTemplate** 프로젝트를 솔루션에 추가 합니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

7. Visual Basic 프로젝트를 만든 경우 프로젝트에서 다음 파일도 삭제 합니다.

    - *MyApplication. .vb*

    - MyApplication.myapp

    - *리소스. 디자이너 .vb*

    - *리소스 .resx*

    - *설정. 디자이너 .vb*

    - 설정. 설정

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 4.5** 이 선택 되어 있는지 확인 합니다.

3. **시각적 C# 개체** 또는 **Visual Basic** 노드를 확장 하 고 **Windows** 노드를 선택한 다음 **클래스 라이브러리** 템플릿을 선택 합니다.

4. **이름** 상자에 **ProjectItemTypeDefinition** 를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **ProjectItemTypeDefinition** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트 구성
 코드 파일 및 어셈블리 참조를 추가 하 여 확장 프로젝트를 구성 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. ProjectItemTypeDefinition 프로젝트에서 이름이 **SiteColumnProjectItemTypeProvider**인 코드 파일을 추가 합니다.

2. 메뉴 모음에서 **프로젝트** > **참조 추가**를 선택합니다.

3. **참조 관리자-ProjectItemTypeDefinition** 대화 상자에서 **어셈블리** 노드를 확장 하 고 **프레임 워크** 노드를 선택한 다음 system.componentmodel 확인란을 선택 합니다.

4. **확장** 노드를 선택 하 고 VisualStudio 어셈블리 옆의 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

## <a name="define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의
 새 프로젝트 항목 형식의 동작을 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 인터페이스를 구현 하는 클래스를 만듭니다. 새 형식의 프로젝트 항목을 정의 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식을 정의 하려면

1. **SiteColumnProjectItemTypeProvider** 코드 파일에서 기본 코드를 다음 코드로 바꾼 다음 파일을 저장 합니다.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Visual Studio 프로젝트 템플릿 만들기
 프로젝트 템플릿을 만들면 다른 개발자가 사이트 열 프로젝트 항목을 포함 하는 SharePoint 프로젝트를 만들 수 있습니다. SharePoint 프로젝트 템플릿에는 *.csproj* 또는 *.vbproj* 및 *.vstemplate* 파일, sharepoint 프로젝트와 관련 된 파일 등 Visual Studio의 모든 프로젝트에 필요한 파일이 포함 되어 있습니다. 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

 이 절차에서는 빈 SharePoint 프로젝트를 만들어 SharePoint 프로젝트와 관련 된 파일을 생성 합니다. 그런 다음 이러한 파일을 SiteColumnProjectTemplate 프로젝트에 추가 하 여이 프로젝트에서 생성 된 템플릿에 포함 되도록 합니다. 또한 SiteColumnProjectTemplate 프로젝트 파일을 구성 하 여 **새 프로젝트** 대화 상자에 프로젝트 템플릿이 표시 되는 위치를 지정 합니다.

#### <a name="to-create-the-files-for-the-project-template"></a>프로젝트 템플릿에 대 한 파일을 만들려면

1. 관리자 자격 증명을 사용 하 여 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 두 번째 인스턴스를 시작 합니다.

2. **BaseSharePointProject**라는 SharePoint 2010 프로젝트를 만듭니다.

   > [!IMPORTANT]
   > **SharePoint 사용자 지정 마법사**에서 **팜 솔루션으로 배포** 옵션 단추를 선택 하지 않습니다.

3. 프로젝트에 빈 요소 항목을 추가 하 고 항목 이름을 **Field1**으로 지정한 다음

4. 프로젝트를 저장 한 다음 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 두 번째 인스턴스를 닫습니다.

5. SiteColumnProjectItem 솔루션이 **솔루션 탐색기**열려 있는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 인스턴스에서 **SiteColumnProjectTemplate** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **기존 항목**을 선택 합니다.

6. **기존 항목 추가** 대화 상자에서 파일 확장명 목록을 열고 **모든 파일 (\*\*)** 을 선택 합니다.

7. BaseSharePointProject 프로젝트를 포함 하는 디렉터리에서 key.snk 파일을 선택한 다음 **추가** 단추를 선택 합니다.

   > [!NOTE]
   > 이 연습에서 만든 프로젝트 템플릿은 동일한 key.snk 파일을 사용 하 여 템플릿을 사용 하 여 만든 각 프로젝트에 서명 합니다. 이 샘플을 확장 하 여 각 프로젝트 인스턴스에 대해 다른 key.snk 파일을 만드는 방법을 알아보려면 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)참조 하세요.

8. 5-8 단계를 반복 하 여 BaseSharePointProject 디렉터리의 지정 된 하위 폴더에서 다음 파일을 추가 합니다.

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\packaget\package\packagepackage*

   - *\Package\Package.Template.xml*

     이러한 파일을 SiteColumnProjectTemplate 프로젝트에 직접 추가 합니다. 프로젝트에서 Field1, Features 또는 Package 하위 폴더를 다시 만들지 마세요. 이러한 파일에 대 한 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>개발자가 새 프로젝트 대화 상자에서 프로젝트 템플릿을 검색 하는 방법을 구성 하려면

1. **솔루션 탐색기**에서 **SiteColumnProjectTemplate** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **프로젝트 언로드**를 선택 합니다. 파일의 변경 내용을 저장 하 라는 메시지가 표시 되 면 **예** 단추를 선택 합니다.

2. **SiteColumnProjectTemplate** 노드에 대 한 바로 가기 메뉴를 다시 열고 **SiteColumnProjectTemplate 편집** 또는 **SiteColumnProjectTemplate 편집**을 선택 합니다.

3. 프로젝트 파일에서 다음 `VSTemplate` 요소를 찾습니다.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. 이 요소를 다음 XML로 바꿉니다.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` 요소는 프로젝트를 빌드할 때 프로젝트 템플릿이 만들어지는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객이 **새 프로젝트** 대화 상자를 열고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 하는 경우에만 프로젝트 템플릿을 사용할 수 있도록 합니다.

5. 파일을 저장하고 닫습니다.

6. **솔루션 탐색기**에서 **SiteColumnProjectTemplate** 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **프로젝트 다시 로드**를 선택 합니다.

## <a name="edit-the-project-template-files"></a>프로젝트 템플릿 파일 편집
 SiteColumnProjectTemplate 프로젝트에서 다음 파일을 편집 하 여 프로젝트 템플릿의 동작을 정의 합니다.

- *AssemblyInfo.cs* 또는 *AssemblyInfo*

- *Elements .xml*

- *SharePointProjectItem*

- *Feature1*

- *Package. 패키지*

- *SiteColumnProjectTemplate*

- *Projecttemplate .csproj* 또는 *projecttemplate .vbproj*

  다음 절차에서는 이러한 파일 중 일부에 대체 가능한 매개 변수를 추가 합니다. 대체 가능 매개 변수는 달러 기호 ($) 문자로 시작 하 고 끝나는 토큰입니다. 사용자가이 프로젝트 템플릿을 사용 하 여 프로젝트를 만들면 Visual Studio에서 새 프로젝트의 이러한 매개 변수를 특정 값으로 자동으로 바꿉니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조 하세요.

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>AssemblyInfo.cs 또는 AssemblyInfo 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *AssemblyInfo.cs* 또는 *AssemblyInfo* 파일을 열고 맨 위에 다음 문을 추가 합니다.

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     SharePoint 프로젝트의 **샌드박스가 적용 된 솔루션** 속성이 **True**로 설정 된 경우 Visual Studio는 AssemblyInfo 코드 파일에 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>를 추가 합니다. 그러나 프로젝트 템플릿의 AssemblyInfo 코드 파일은 기본적으로 <xref:System.Security> 네임 스페이스를 가져오지 않습니다. 컴파일 오류를 방지 하려면이 **using** 또는 **Imports** 문을 추가 해야 합니다.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-elementsxml-file"></a>Elements .xml 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *Elements xml* 파일의 내용을 다음 xml로 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     새 XML은 사이트 열의 이름, 해당 기본 형식 및 갤러리의 사이트 열을 나열할 그룹을 정의 하는 `Field` 요소를 추가 합니다. 이 파일의 내용에 대 한 자세한 내용은 [필드 정의 스키마](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14))를 참조 하세요.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>SharePointProjectItem 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *SharePointProjectItem* 파일의 내용을 다음 XML로 바꿉니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    새 XML은 파일을 다음과 같이 변경 합니다.

   - `ProjectItem` 요소의 `Type` 특성을 프로젝트 항목 정의의 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>에 전달 되는 동일한 문자열로 변경 합니다 (이 연습의 앞부분에서 만든 `SiteColumnProjectItemTypeProvider` 클래스).

   - `ProjectItem` 요소에서 `SupportedTrustLevels` 및 `SupportedDeploymentScopes` 특성을 제거 합니다. ProjectItemTypeDefinition 프로젝트의 `SiteColumnProjectItemTypeProvider` 클래스에 신뢰 수준 및 배포 범위가 지정 되어 있으므로 이러한 특성 값은 필요 하지 않습니다.

     *.Spdata* 파일의 내용에 대 한 자세한 내용은 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)를 참조 하세요.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-feature1feature-file"></a>Feature1 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *Feature1* 파일의 내용을 다음 XML로 바꿉니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    새 XML은 파일을 다음과 같이 변경 합니다.

   - `feature` 요소의 `Id` 및 `featureId` 특성 값을 `$guid4$`로 변경 합니다.

   - `projectItemReference` 요소의 `itemId` 특성 값을 `$guid2$`로 변경 합니다.

     *기능* 파일에 대 한 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-packagepackage-file"></a>패키지를 편집 하려면 패키지 파일

1. SiteColumnProjectTemplate 프로젝트에서 *패키지* 파일의 내용을 다음 XML로 바꿉니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    새 XML은 파일을 다음과 같이 변경 합니다.

   - `package` 요소의 `Id` 및 `solutionId` 특성 값을 `$guid3$`로 변경 합니다.

   - `featureReference` 요소의 `itemId` 특성 값을 `$guid4$`로 변경 합니다.

     *패키지* 파일에 대 한 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Sitecolumnprojecttemplate 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 SiteColumnProjectTemplate 파일의 내용을 XML의 다음 섹션 중 하나로 바꿉니다.

   - Visual C# 프로젝트 템플릿을 만드는 경우 다음 XML을 사용 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Visual Basic 프로젝트 템플릿을 만드는 경우 다음 XML을 사용 합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    새 XML은 파일을 다음과 같이 변경 합니다.

   - `Name` 요소를 값 **사이트 열**로 설정 합니다. 이 이름은 **새 프로젝트** 대화 상자에 나타납니다.

   - 각 프로젝트 인스턴스에 포함 된 각 filethat 요소를 추가 합니다.`ProjectItem`

   - `http://schemas.microsoft.com/developer/vstemplate/2005`네임 스페이스를 사용 합니다. 이 솔루션의 다른 프로젝트 파일은 `http://schemas.microsoft.com/developer/msbuild/2003` 네임 스페이스를 사용 합니다. 따라서 XML 스키마 경고 메시지가 생성 되지만이 연습에서는 무시 해도 됩니다.

     *.Vstemplate* 파일의 내용에 대 한 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조 하세요.

2. 파일을 저장하고 닫습니다.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Projecttemplate .csproj 또는 projecttemplate .vbproj 파일을 편집 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *projecttemplate .csproj* 파일 또는 *projecttemplate .vbproj* 파일의 콘텐츠를 다음 XML 섹션 중 하나로 바꿉니다.

    - Visual C# 프로젝트 템플릿을 만드는 경우 다음 XML을 사용 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Visual Basic 프로젝트 템플릿을 만드는 경우 다음 XML을 사용 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     새 XML은 파일을 다음과 같이 변경 합니다.

    - `TargetFrameworkVersion` 요소를 사용 하 여 4.5이 아닌 .NET Framework 3.5를 지정 합니다.

    - `SignAssembly` 및 `AssemblyOriginatorKeyFile` 요소를 추가 하 여 프로젝트 출력에 서명 합니다.

    - SharePoint 프로젝트에서 사용 하는 어셈블리 참조에 대 한 `Reference` 요소를 추가 합니다.

    - *.Xml* 및 *SharePointProjectItem*와 같은 프로젝트의 각 기본 파일에 대 한 요소를 추가 합니다.

2. 파일을 저장하고 닫습니다.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>VSIX 패키지를 만들어 프로젝트 템플릿 배포
 확장을 배포 하려면 **SiteColumnProjectItem** 솔루션의 vsix 프로젝트를 사용 하 여 vsix 패키지를 만듭니다. 먼저 VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 구성 하 고 만들려면

1. **솔루션 탐색기**의 **SiteColumnProjectItem** 프로젝트에서 매니페스트 편집기의 source.extension.vsixmanifest 파일을 엽니다.

     Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)를 참조 하세요.

2. **제품 이름** 상자에 **사이트 열**을 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에 **사이트 열을 만드는 데 사용할 SharePoint 프로젝트**를 입력 합니다.

5. **자산** 탭을 선택한 다음 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값은 source.extension.vsixmanifest 파일의 `ProjectTemplate` 요소에 해당 합니다. 이 요소는 프로젝트 템플릿이 포함 된 VSIX 패키지의 하위 폴더를 식별 합니다. 자세한 내용은 [Projecttemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **SiteColumnProjectTemplate**를 선택한 다음 **확인** 단추를 선택 합니다.

9. **새로 만들기** 단추를 다시 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

10. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값은 source.extension.vsixmanifest 파일의 `MefComponent` 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

11. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

12. **프로젝트** 목록에서 **ProjectItemTypeDefinition**를 선택한 다음 **확인** 단추를 선택 합니다.

13. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택한 후 프로젝트가 오류 없이 컴파일되는지 확인 합니다.

## <a name="test-the-project-template"></a>프로젝트 템플릿 테스트
 이제 프로젝트 템플릿을 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 SiteColumnProjectItem 솔루션의 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 **사이트 열** 프로젝트를 테스트 합니다. 마지막으로 SharePoint 프로젝트를 빌드하고 실행 하 여 사이트 열이 예상 대로 작동 하는지 확인 합니다.

#### <a name="to-start-debugging-the-solution"></a>솔루션 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 SiteColumnProjectItem 솔루션을 엽니다.

2. SiteColumnProjectItemTypeProvider 코드 파일에서 `InitializeType` 메서드의 첫 번째 코드 줄에 중단점을 추가한 다음 **F5** 키를 선택 하 여 디버깅을 시작 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-project-in-visual-studio"></a>Visual Studio에서 프로젝트를 테스트 하려면

1. Visual Studio의 실험적 인스턴스의 메뉴 모음에서 **파일** > **새** > **프로젝트**를 선택 합니다.

2. 프로젝트 템플릿에서 지 원하는 언어에 따라  **C# 시각적 개체** 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **사이트 열** 템플릿을 선택 합니다.

4. **이름** 상자에 **SiteColumnTest** 를 입력 하 고 **확인** 단추를 선택 합니다.

     **솔루션 탐색기**에서 **Field1**이라는 프로젝트 항목을 포함 하는 새 프로젝트가 표시 됩니다.

5. Visual Studio의 다른 인스턴스에 있는 코드가 `InitializeType` 메서드에서 이전에 설정한 중단점에서 중지 되는지 확인 한 다음 **F5** 키를 선택 하 여 계속 해 서 프로젝트를 디버깅 합니다.

6. **솔루션 탐색기**에서 **Field1** 노드를 선택 하 고 **F4** 키를 선택 합니다.

     **속성** 창이 열립니다.

7. 속성 목록에서 속성 **예제 속성이** 나타나는지 확인 합니다.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint에서 사이트 열을 테스트 하려면

1. **솔루션 탐색기**에서 **SiteColumnTest** 노드를 선택 합니다.

2. **속성** 창의 **사이트 URL** 속성 옆에 있는 입력란에 **http://localhost** 을 입력 합니다.

     이 단계에서는 디버깅에 사용할 개발 컴퓨터의 로컬 SharePoint 사이트를 지정 합니다.

    > [!NOTE]
    > 사이트 열 프로젝트 템플릿은 프로젝트가 만들어질 때이 값을 수집 하기 위한 마법사를 제공 하지 않으므로 기본적으로 **사이트 URL** 속성은 비어 있습니다. 개발자에 게이 값을 요청 하 고 새 프로젝트에서이 속성을 구성 하는 마법사를 추가 하는 방법을 알아보려면 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)참조 하세요.

3. **F5** 키를 선택합니다.

     사이트 열이 패키지 되 고 프로젝트의 **사이트 URL** 속성에 지정 된 SharePoint 사이트에 배포 됩니다. 웹 브라우저가이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > **스크립트 디버깅 사용 안 함** 대화 상자가 나타나면 **예** 단추를 선택 하 여 프로젝트를 계속 디버깅 합니다.

4. **사이트 작업** 메뉴에서 **사이트 설정**을 선택 합니다.

5. **사이트 설정** 페이지의 **갤러리** 목록에서 **사이트 열** 링크를 선택 합니다.

6. 사이트 열 목록에서 **사용자 지정 열** 그룹에 **SiteColumnTest**라는 열이 포함 되어 있는지 확인 합니다.

7. 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 테스트를 마친 후 Visual Studio의 실험적 인스턴스에서 프로젝트 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구** > **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **사이트 열** 확장을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것임을 확인 합니다.

4. **닫기** 단추를 선택 하 여 제거를 완료 합니다.

5. Visual Studio의 두 인스턴스 (SiteColumnProjectItem 솔루션이 열리는 실험적 인스턴스 및 Visual Studio의 인스턴스)를 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료 한 후에 마법사를 프로젝트 템플릿에 추가할 수 있습니다. 사용자가 사이트 열 프로젝트를 만들면 마법사에서 디버깅에 사용할 사이트 URL과 새 솔루션이 샌드 박싱 되었는지 여부를 사용자에 게 묻는 메시지를 표시 하 고 마법사는이 정보를 사용 하 여 새 프로젝트를 구성 합니다. 또한이 마법사는 열에 대 한 정보 (예: 사이트 열 갤러리의 열을 나열 하는 기본 유형 및 그룹)를 수집 하 고이 정보를 새 프로젝트의 *Elements* 파일에 추가 합니다. 자세한 내용은 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)