---
title: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eccb9038b9fd929c713422aa79082c94ade512fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015933"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부
  사용자 고유의 프로젝트 항목 형식을 만들어 Visual Studio에서 SharePoint 프로젝트 시스템을 확장할 수 있습니다. 이 연습에서는 sharepoint 사이트에 대 한 사용자 지정 작업을 만들기 위해 SharePoint 프로젝트에 추가할 수 있는 프로젝트 항목을 만듭니다. 사용자 지정 작업은 SharePoint 사이트의 **사이트 작업** 메뉴에 메뉴 항목을 추가 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 동작에 대 한 새 형식의 SharePoint 프로젝트 항목을 정의 하는 Visual Studio 확장을 만듭니다. 새 프로젝트 항목 형식은 여러 사용자 지정 기능을 구현 합니다.

  - Visual Studio에서 사용자 지정 작업을 위한 디자이너 표시와 같이 프로젝트 항목과 관련 된 추가 작업의 시작 지점으로 사용 되는 바로 가기 메뉴입니다.

  - 개발자가 프로젝트 항목의 특정 속성 및 프로젝트 항목을 포함 하는 프로젝트를 변경할 때 실행 되는 코드입니다.

  - **솔루션 탐색기**의 프로젝트 항목 옆에 표시 되는 사용자 지정 아이콘입니다.

- 프로젝트 항목에 대 한 Visual Studio 항목 템플릿을 만듭니다.

- VSIX (Visual Studio Extension) 패키지를 빌드하여 프로젝트 항목 템플릿과 확장 어셈블리를 배포 합니다.

- 프로젝트 항목 디버깅 및 테스트

  이는 독립 실행형 연습입니다. 이 연습을 완료 한 후에는 항목 템플릿에 마법사를 추가 하 여 프로젝트 항목을 향상 시킬 수 있습니다. 자세한 내용은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)를 참조 하세요.

> [!NOTE]
> 워크플로에 대 한 사용자 지정 활동을 만드는 방법을 보여 주는 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 에서 샘플을 다운로드할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터에서 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Microsoft Windows, SharePoint 및 Visual Studio

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- SharePoint의 사용자 지정 작업. 자세한 내용은 [사용자 지정 작업](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14))을 참조 하세요.

- Visual Studio의 항목 템플릿 자세한 내용은 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조하세요.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 다음 세 개의 프로젝트를 만들어야 합니다.

- VSIX 프로젝트입니다. 이 프로젝트는 SharePoint 프로젝트 항목을 배포 하는 VSIX 패키지를 만듭니다.

- 항목 템플릿 프로젝트입니다. 이 프로젝트는 sharepoint 프로젝트에 SharePoint 프로젝트 항목을 추가 하는 데 사용할 수 있는 항목 템플릿을 만듭니다.

- 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 SharePoint 프로젝트 항목의 동작을 정의 하는 Visual Studio 확장을 구현 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자의 맨 위에 있는 목록에서 **.NET Framework 4.5** 가 선택 되어 있는지 확인 합니다.

4. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

    > [!NOTE]
    > **확장성** 노드는 VISUAL Studio SDK를 설치 하는 경우에만 사용할 수 있습니다. 자세한 내용은이 항목의 앞부분에 있는 전제 조건 섹션을 참조 하세요.

5. **VSIX 프로젝트** 템플릿을 선택 합니다.

6. **이름** 상자에 **CustomActionProjectItem**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**솔루션 탐색기**에 **CustomActionProjectItem** 프로젝트를 추가 합니다.

#### <a name="to-create-the-item-template-project"></a>항목 템플릿 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자의 맨 위에 있는 목록에서 **.NET Framework 4.5** 가 선택 되어 있는지 확인 합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **확장성** 노드를 선택 합니다.

4. 프로젝트 템플릿 목록에서 **c # 항목 템플릿** 또는 **Visual Basic 항목 템플릿** 템플릿을 선택 합니다.

5. **이름** 상자에 **ItemTemplate**을 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ItemTemplate** 프로젝트를 솔루션에 추가 합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트** 대화 상자의 맨 위에 있는 목록에서 **.NET Framework 4.5** 가 선택 되어 있는지 확인 합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 하 고 **Windows** 노드를 선택한 다음 **클래스 라이브러리** 프로젝트 템플릿을 선택 합니다.

4. **이름** 상자에 **ProjectItemDefinition**를 입력 하 고 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**ProjectItemDefinition** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트 구성
 SharePoint 프로젝트 항목 형식을 정의 하는 코드를 작성 하기 전에 확장 프로젝트에 코드 파일 및 어셈블리 참조를 추가 해야 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. **솔루션 탐색기**에서 **ProjectItemDefinition** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

2. 프로젝트 항목 목록에서 **코드 파일**을 선택 합니다.

3. **이름** 상자에 적절 한 파일 이름 확장명을 가진 **CustomAction** 이름을 입력 한 다음 **추가** 단추를 선택 합니다.

4. **솔루션 탐색기**에서 **ProjectItemDefinition** 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

5. **참조 관리자-ProjectItemDefinition** 대화 상자에서 **어셈블리** 노드를 선택 하 고 **프레임 워크** 노드를 선택 합니다.

6. 다음 각 어셈블리 옆의 확인란을 선택 합니다.

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. **확장** 노드를 선택 하 고 VisualStudio 어셈블리 옆의 확인란을 선택한 다음 **확인** 단추를 선택 합니다.

## <a name="define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식 정의
 인터페이스를 구현 하는 클래스를 만들어 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 새 프로젝트 항목 형식의 동작을 정의 합니다. 새 형식의 프로젝트 항목을 정의 하려는 경우 언제 든 지이 인터페이스를 구현 합니다.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>새 SharePoint 프로젝트 항목 형식을 정의 하려면

1. ProjectItemDefinition 프로젝트에서 CustomAction 코드 파일을 엽니다.

2. 이 파일의 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>에서 프로젝트 항목의 아이콘을 만듭니다 솔루션 탐색기
 사용자 지정 SharePoint 프로젝트 항목을 만들 때 이미지 (아이콘 또는 비트맵)를 프로젝트 항목과 연결할 수 있습니다. 이 이미지는 **솔루션 탐색기**의 프로젝트 항목 옆에 표시 됩니다.

 다음 절차에서는 프로젝트 항목에 대 한 아이콘을 만들고 확장 어셈블리에 아이콘을 포함 합니다. 이 아이콘은 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> 앞에서 만든 클래스의에서 참조 합니다 `CustomActionProjectItemTypeProvider` .

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>프로젝트 항목의 사용자 지정 아이콘을 만들려면

1. **솔루션 탐색기**에서 **ProjectItemDefinition** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**...을 선택 합니다.

2. 프로젝트 항목 목록에서 **아이콘 파일** 항목을 선택 합니다.

    > [!NOTE]
    > Visual Basic 프로젝트에서 **일반** 노드를 선택 하 여 **아이콘 파일** 항목을 표시 해야 합니다.

3. **이름** 상자에 **CustomAction_SolutionExplorer .ico**를 입력 한 다음 **추가** 단추를 선택 합니다.

     새 아이콘이 **이미지 편집기**에 열립니다.

4. 인식할 수 있는 디자인을 포함 하도록 아이콘 파일의 16x16 버전을 편집 하 고 아이콘 파일을 저장 합니다.

5. **솔루션 탐색기**에서 **CustomAction_SolutionExplorer**를 선택 합니다.

6. **속성** 창에서 **빌드 작업** 속성 옆의 화살표를 선택 합니다.

7. 표시 되는 목록에서 **포함 리소스**를 선택 합니다.

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 프로젝트 항목의 모든 코드는 이제 프로젝트에 있습니다. 프로젝트를 빌드하여 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-your-project"></a>프로젝트를 빌드하려면

1. **ProjectItemDefinition** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

## <a name="create-a-visual-studio-item-template"></a>Visual Studio 항목 템플릿 만들기
 다른 개발자가 프로젝트 항목을 사용할 수 있도록 하려면 프로젝트 템플릿 또는 항목 템플릿을 만들어야 합니다. 개발자는 Visual Studio에서 이러한 템플릿을 사용 하 여 새 프로젝트를 만들거나 기존 프로젝트에 항목을 추가 하 여 프로젝트 항목의 인스턴스를 만듭니다. 이 연습에서는 ItemTemplate 프로젝트를 사용 하 여 프로젝트 항목을 구성 합니다.

#### <a name="to-create-the-item-template"></a>항목 템플릿을 만들려면

1. ItemTemplate 프로젝트에서 Class1 코드 파일을 삭제 합니다.

2. ItemTemplate 프로젝트에서 *itemtemplate .vstemplate* 파일을 엽니다.

3. 파일의 내용을 다음 XML로 바꾼 다음 파일을 저장 하 고 닫습니다.

    > [!NOTE]
    > 다음 XML은 Visual c # 항목 템플릿에 대 한 것입니다. Visual Basic 항목 템플릿을 만드는 경우 요소의 값을 `ProjectType` 로 바꿉니다 `VisualBasic` .

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     이 파일은 항목 템플릿의 내용 및 동작을 정의 합니다. 이 파일의 내용에 대 한 자세한 내용은 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조 하세요.

4. **솔루션 탐색기**에서 **ItemTemplate** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

5. **새 항목 추가** 대화 상자에서 **텍스트 파일** 템플릿을 선택 합니다.

6. **이름** 상자에 **CustomAction**를 입력 한 다음 **추가** 단추를 선택 합니다.

7. *CustomAction* 파일에 다음 XML을 추가 하 고 파일을 저장 한 후 닫습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     이 파일에는 프로젝트 항목에 포함 된 파일에 대 한 정보가 포함 되어 있습니다. `Type`요소의 특성은 `ProjectItem` 프로젝트 항목 정의의로 전달 되는 동일한 문자열로 설정 해야 합니다 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> ( `CustomActionProjectItemTypeProvider` 이 연습의 앞부분에서 만든 클래스). *.Spdata* 파일의 내용에 대 한 자세한 내용은 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)를 참조 하세요.

8. **솔루션 탐색기**에서 **ItemTemplate** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

9. **새 항목 추가** 대화 상자에서 **XML 파일** 템플릿을 선택 합니다.

10. **이름** 상자에 **Elements.xml**를 입력 한 다음 **추가** 단추를 선택 합니다.

11. *Elements.xml* 파일의 내용을 다음 XML로 바꾼 다음 파일을 저장 하 고 닫습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     이 파일은 SharePoint 사이트의 **사이트 작업** 메뉴에서 메뉴 항목을 만드는 기본 사용자 지정 작업을 정의 합니다. 사용자가 메뉴 항목을 선택 하면 요소에 지정 된 URL이 `UrlAction` 웹 브라우저에서 열립니다. 사용자 지정 작업을 정의 하는 데 사용할 수 있는 XML 요소에 대 한 자세한 내용은 [사용자 지정 작업 정의](/sharepoint/dev/schema/custom-action-definition-schema)를 참조 하세요.

12. 필요에 따라 *ItemTemplate* 파일을 열고 인식할 수 있는 디자인을 포함 하도록 수정 합니다. 이 아이콘은 **새 항목 추가** 대화 상자의 프로젝트 항목 옆에 표시 됩니다.

13. **솔루션 탐색기**에서 **ItemTemplate** 프로젝트에 대 한 바로 가기 메뉴를 열고 **프로젝트 언로드**를 선택 합니다.

14. **Itemtemplate** 프로젝트에 대 한 바로 가기 메뉴를 다시 열고 **ItemTemplate 편집** 또는 **itemtemplate 편집**을 선택 합니다.

15. `VSTemplate`프로젝트 파일에서 다음 요소를 찾습니다.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. 이 `VSTemplate` 요소를 다음 XML로 바꾼 다음 파일을 저장 하 고 닫습니다.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`요소는 프로젝트를 빌드할 때 항목 템플릿이 만들어지는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객이 **새 항목 추가** 대화 상자를 열고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 하는 경우에만 항목 템플릿을 사용할 수 있도록 합니다.

17. **솔루션 탐색기**에서 **ItemTemplate** 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **프로젝트 다시 로드**를 선택 합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>VSIX 패키지를 만들어 프로젝트 항목을 배포 합니다.
 확장을 배포 하려면 솔루션의 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 빌드하여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 구성 하 고 만들려면

1. **솔루션 탐색기**에서 CustomActionProjectItem 프로젝트의 **source.extension.vsixmanifest** 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     Visual Studio가 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일은 모든 VSIX 패키지에 필요한 source.extension.vsixmanifest 파일의 기반이 됩니다. 이 파일에 대 한 자세한 내용은 [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)를 참조 하세요.

2. **제품 이름** 상자에 **사용자 지정 작업 프로젝트 항목**을 입력 합니다.

3. **작성자** 상자에 **Contoso**를 입력 합니다.

4. **설명** 상자에 **사용자 지정 작업을 나타내는 SharePoint 프로젝트 항목**을 입력 합니다.

5. **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

6. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `ItemTemplate` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에서 프로젝트 항목 템플릿을 포함 하는 하위 폴더를 식별 합니다. 자세한 내용은 [ItemTemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))를 참조 하세요.

7. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

8. **프로젝트** 목록에서 **ItemTemplate**을 선택 하 고 **확인** 단추를 선택 합니다.

9. **자산** 탭에서 **새로 만들기** 단추를 다시 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

10. **유형** 목록에서 **VisualStudio**을 선택 합니다.

    > [!NOTE]
    > 이 값 `MefComponent` 은 source.extension.vsixmanifest 파일의 요소에 해당 합니다. 이 요소는 VSIX 패키지에 있는 확장 어셈블리의 이름을 지정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

11. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

12. **프로젝트** 목록에서 **ProjectItemDefinition**를 선택 합니다.

13. **확인** 단추를 선택합니다.

14. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 후 프로젝트가 오류 없이 컴파일되는지 확인 합니다.

15. CustomActionProjectItem 프로젝트에 대 한 빌드 출력 폴더에 CustomActionProjectItem 파일이 포함 되어 있는지 확인 합니다.

     기본적으로 빌드 출력 폴더는 .입니다. CustomActionProjectItem 프로젝트를 포함 하는 폴더 아래의 \bin\Debug 폴더

## <a name="test-the-project-item"></a>프로젝트 항목 테스트
 이제 프로젝트 항목을 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 CustomActionProjectItem 솔루션의 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 SharePoint 프로젝트의 **사용자 지정 작업** 프로젝트 항목을 테스트 합니다. 마지막으로 SharePoint 프로젝트를 빌드하고 실행 하 여 사용자 지정 작업이 예상 대로 작동 하는지 확인 합니다.

#### <a name="to-start-debugging-the-solution"></a>솔루션 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 CustomActionProjectItem 솔루션을 엽니다.

2. CustomAction 코드 파일을 연 다음 메서드의 첫 번째 코드 줄에 중단점을 추가 합니다 `InitializeType` .

3. **F5** 키를 선택 하 여 디버깅을 시작 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action 프로젝트 Item\1.0에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Visual Studio에서 프로젝트 항목을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서, 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. **Visual c #** 또는 **Visual Basic** (항목 템플릿에서 지 원하는 언어에 따라)를 확장 하 고 **SharePoint**를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **SharePoint 2010 프로젝트**를 선택 합니다.

4. **이름** 상자에 **CustomActionTest**를 입력 하 고 **확인** 단추를 선택 합니다.

5. **SharePoint 사용자 지정 마법사**에서 디버깅에 사용할 사이트의 URL을 입력 한 후 **마침** 단추를 선택 합니다.

6. **솔루션 탐색기**에서 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

7. **새 항목 추가** 대화 상자에서 **SharePoint** 노드 아래의 **2010** 노드를 선택 합니다.

     프로젝트 항목 목록에 **사용자 지정 작업** 항목이 표시 되는지 확인 합니다.

8. **사용자 지정 작업** 항목을 선택한 다음 **추가** 단추를 선택 합니다.

     Visual Studio에서 **CustomAction1** 라는 항목이 프로젝트에 추가 되 고 편집기에서 *Elements.xml* 파일이 열립니다.

9. 메서드의 이전에 설정한 중단점에서 Visual Studio의 다른 인스턴스의 코드가 중지 되는지 확인 `InitializeType` 합니다.

10. **F5** 키를 선택 하 여 프로젝트를 계속 디버깅 합니다.

11. Visual Studio의 실험적 인스턴스에서 **솔루션 탐색기**의 **CustomAction1** 노드에 대 한 바로 가기 메뉴를 열고 **사용자 지정 작업 디자이너 보기**를 선택 합니다.

12. 메시지 상자가 표시 되는지 확인 하 고 **확인** 단추를 선택 합니다.

     이 바로 가기 메뉴를 사용 하 여 개발자에 게 사용자 지정 작업을 위한 디자이너 표시와 같은 추가 옵션이 나 명령을 제공할 수 있습니다.

13. 메뉴 모음에서 출력 **보기**를 선택  >  **Output**합니다.

     **출력** 창이 열립니다.

14. **솔루션 탐색기**에서 **CustomAction1** 항목에 대 한 바로 가기 메뉴를 열고 이름을 **MyCustomAction**로 변경 합니다.

     **출력** 창에 확인 메시지가 표시 됩니다. 이 메시지는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> 클래스에서 정의한 이벤트 처리기에 의해 작성 됩니다 `CustomActionProjectItemTypeProvider` . 이 이벤트 및 기타 프로젝트 항목 이벤트를 처리 하 여 개발자가 프로젝트 항목을 수정할 때 사용자 지정 동작을 구현할 수 있습니다.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint에서 사용자 지정 작업을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 **MyCustomAction** 프로젝트 항목의 자식인 *Elements.xml* 파일을 엽니다.

2. *Elements.xml* 파일에서 다음과 같이 변경한 후 파일을 저장 합니다.

    - 요소에서 `CustomAction` `Id` 특성을 다음 예제와 같이 GUID 또는 다른 고유한 문자열로 설정 합니다.

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - 요소에서 `CustomAction` `Title` 다음 예제와 같이 특성을 설정 합니다.

        ```xml
        Title="SharePoint Developer Center"
        ```

    - 요소에서 `CustomAction` `Description` 다음 예제와 같이 특성을 설정 합니다.

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - 요소에서 `UrlAction` `Url` 다음 예제와 같이 특성을 설정 합니다.

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. **F5** 키를 선택합니다.

     사용자 지정 작업은 패키지 되 고 프로젝트의 **사이트 URL** 속성에 지정 된 SharePoint 사이트에 배포 됩니다. 웹 브라우저가이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > **스크립트 디버깅 사용 안 함** 대화 상자가 나타나면 **예** 단추를 선택 하 여 프로젝트를 계속 디버깅 합니다.

4. **사이트 작업** 메뉴에서 **SharePoint 개발자 센터**를 선택 하 고 브라우저에서 웹 사이트가 열리는지 확인 한 https://docs.microsoft.com/sharepoint/dev/ 다음 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목 테스트를 마친 후 Visual Studio의 실험적 인스턴스에서 프로젝트 항목 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **사용자 지정 작업 프로젝트 항목**을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것임을 확인 합니다.

4. **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

5. Visual Studio의 실험적 인스턴스와 CustomActionProjectItem 솔루션이 열려 있는 인스턴스를 모두 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료 한 후에는 항목 템플릿에 마법사를 추가할 수 있습니다. 사용자가 SharePoint 프로젝트에 사용자 지정 작업 프로젝트 항목을 추가 하면 마법사에서 작업에 대 한 정보 (예: 작업을 선택할 때 이동할 URL)를 수집 하 고 새 프로젝트 항목의 *Elements.xml* 파일에이 정보를 추가 합니다. 자세한 내용은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [아이콘에 대 한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 아이콘에 대 한 이미지 편집기 &#40;&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)