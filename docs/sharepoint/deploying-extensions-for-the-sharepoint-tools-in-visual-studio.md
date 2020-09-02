---
title: Visual Studio에서 SharePoint 도구에 대 한 확장 배포 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580646"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio에서 SharePoint 도구에 대 한 확장 배포

SharePoint 도구 확장을 배포 하려면 확장 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일을 포함 하는 확장 (VSIX) 패키지를 만듭니다. VSIX 패키지는 OPC (Open 패키징 규칙) 표준을 따르는 압축 파일입니다. VSIX 패키지에는 *.vsix* 확장명이 있습니다.

VSIX 패키지를 만든 후에는 다른 사용자가 .vsix 파일을 실행 하 여 확장을 설치할 수 있습니다. 사용자가 확장을 설치 하면 모든 파일이%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions 폴더에 설치 됩니다. 확장을 배포 하려면 VSIX 패키지를 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트에 업로드 하거나 네트워크 공유 또는 다른 웹 사이트에서 패키지를 호스트 하는 등의 다른 방법으로 고객에 게 패키지를 배포할 수 있습니다.

VSIX 패키지를 만들고 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)에 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio 확장](../extensibility/shipping-visual-studio-extensions.md)제공을 참조 하세요.

 Visual Studio에서 vsix **프로젝트** 템플릿을 사용 하 여 vsix 패키지를 만들거나 vsix 패키지를 수동으로 만들 수 있습니다.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>VSIX 프로젝트를 사용 하 여 VSIX 패키지 만들기

Visual Studio SDK에서 제공 하는 **Vsix 프로젝트** 템플릿을 사용 하 여 SharePoint 도구 확장에 대 한 vsix 패키지를 만들 수 있습니다. Vsix 프로젝트를 사용 하면 VSIX 패키지를 수동으로 만드는 방법에 비해 몇 가지 이점이 있습니다.

- Visual Studio는 프로젝트를 빌드할 때 VSIX 패키지를 자동으로 생성 합니다. 패키지에 배포 파일을 추가 하 고 패키지에 대 한 [Content_Types] .xml 파일을 만드는 등의 작업이 수행 됩니다.

- Vsix 패키지에 확장 프로젝트의 빌드 출력과 프로젝트 템플릿 및 항목 템플릿과 같은 기타 파일을 포함 하도록 VSIX 프로젝트를 구성할 수 있습니다.

VSIX 프로젝트를 사용 하는 방법에 대 한 자세한 내용은 [Vsix 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조 하세요.

### <a name="organize-your-projects"></a>프로젝트 구성

기본적으로 VSIX 프로젝트는 어셈블리가 아닌 VSIX 패키지만 생성 합니다. 따라서 일반적으로 VSIX 프로젝트에서 SharePoint 도구 확장을 구현 하지 않습니다. 일반적으로 두 개 이상의 프로젝트를 사용 하 여 작업 합니다.

- VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트입니다.

특정 확장 형식에 대 한 추가 프로젝트를 사용할 수도 있습니다.

- 확장 프로그램에서 사용 하는 SharePoint 명령을 구현 하는 클래스 라이브러리 프로젝트입니다. 이 시나리오를 보여 주는 연습은 [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)를 참조 하세요.

- 확장 프로그램이 새 형식의 SharePoint 프로젝트 항목을 정의 하는 경우 항목 템플릿이나 프로젝트 템플릿을 만드는 항목 템플릿 또는 프로젝트 템플릿 프로젝트입니다. 이 시나리오를 보여 주는 연습은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)를 참조 하세요.

- 확장에 템플릿이 포함 된 경우 항목 템플릿이나 프로젝트 템플릿에 대 한 사용자 지정 마법사를 구현 하는 클래스 라이브러리 프로젝트입니다. 이 시나리오를 보여 주는 연습은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)를 참조 하세요.

모든 프로젝트를 동일한 Visual Studio 솔루션에 포함 하는 경우 VSIX 프로젝트의 source.extension.vsixmanifest 파일을 수정 하 여 클래스 라이브러리 프로젝트의 빌드 출력을 포함할 수 있습니다.

### <a name="edit-the-vsix-manifest"></a>VSIX 매니페스트 편집

확장에 포함할 모든 항목에 대 한 항목을 포함 하려면 VSIX 프로젝트의 source.extension.vsixmanifest 파일을 편집 해야 합니다. 바로 가기 메뉴에서 source.extension.vsixmanifest 파일을 열면 파일의 XML 편집을 위한 UI를 제공 하는 디자이너에 파일이 표시 됩니다. 자세한 내용은 [VSIX 매니페스트 디자이너](../extensibility/vsix-manifest-designer.md)를 참조 하세요.

다음 항목에 대 한 source.extension.vsixmanifest 파일에 항목을 추가 해야 합니다.

- 확장 어셈블리입니다.

- 확장 프로그램에서 사용 하는 SharePoint 명령을 구현 하는 어셈블리입니다.

- 확장과 연결 된 모든 프로젝트 템플릿 또는 항목 템플릿

- 확장과 연결 된 템플릿에 대 한 사용자 지정 마법사입니다.

다음 절차에서는 이러한 각 항목에 대 한 source.extension.vsixmanifest 파일에 항목을 추가 하는 방법에 대해 설명 합니다.

#### <a name="to-include-the-extension-assembly"></a>확장 어셈블리를 포함 하려면

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     파일이 디자이너에서 열립니다.

2. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

3. **유형** 목록에서 **VisualStudio**을 선택 합니다.

4. **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트에서 확장 어셈블리를 빌드하는 경우 **에는 현재 솔루션에서 프로젝트**를 선택 합니다. **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 확장 어셈블리가 프로젝트에 파일로 포함 된 경우 **파일 시스템에서 파일**을 선택 합니다. **경로** 목록에서 확장 어셈블리 파일의 전체 경로를 입력 하거나 **찾아보기** 단추를 사용 하 여 어셈블리 파일을 찾아 선택 합니다.

5. **확인** 단추를 선택합니다.

#### <a name="to-include-a-sharepoint-command-assembly"></a>SharePoint 명령 어셈블리를 포함 하려면

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 연 다음 **열기** 단추를 선택 합니다.

     파일이 디자이너에서 열립니다.

2. 편집기의 **자산** 섹션에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

3. **유형** 상자에 **SharePoint. Commands**를 입력 합니다.

4. **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트에서 명령 어셈블리를 빌드하는 경우 **에는 현재 솔루션에서 프로젝트**를 선택 합니다. **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 명령 어셈블리가 프로젝트에 파일로 포함 된 경우 **파일 시스템에서 파일**을 선택 합니다. **경로** 목록에서 확장 어셈블리 파일의 전체 경로를 입력 하거나 **찾아보기** 단추를 사용 하 여 어셈블리 파일을 찾아 선택 합니다.

5. **확인** 단추를 선택합니다.

#### <a name="to-include-a-template-that-you-create"></a>만든 템플릿을 포함 하려면

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 연 다음 **열기** 단추를 선택 합니다.

     파일이 디자이너에서 열립니다.

2. 편집기의 **자산** 섹션에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

3. **유형** 목록에서 **VisualStudio** 또는 **VisualStudio**를 선택 합니다.

4. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

5. **프로젝트** 목록에서 프로젝트 이름을 선택한 다음 **확인** 단추를 선택 합니다.

6. **솔루션 탐색기**에서 프로젝트 템플릿 또는 항목 템플릿 프로젝트에 대 한 바로 가기 메뉴를 열고 **프로젝트 언로드**를 선택 합니다.

7. 프로젝트 노드에 대 한 바로 가기 메뉴를 다시 열고 원하는 템플릿_projectname_**.csproj** 를 **편집**하거나 원하는 템플릿_projectname_**를** **편집**합니다.

8. `VSTemplate`프로젝트 파일에서 다음 요소를 찾습니다.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. 이 요소를 다음 XML로 바꿉니다.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`요소는 프로젝트를 빌드할 때 프로젝트 템플릿이 만들어지는 경로에 추가 폴더를 지정 합니다. 여기에 지정 된 폴더는 고객이 **새 프로젝트 추가** 대화 상자를 열고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 하는 경우에만 항목 템플릿을 사용할 수 있도록 합니다.

10. 파일을 저장하고 닫습니다.

11. **솔루션 탐색기**에서 프로젝트 템플릿 또는 항목 템플릿 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **프로젝트 다시 로드**를 선택 합니다.

#### <a name="to-include-a-template-that-you-create-manually"></a>수동으로 만든 템플릿을 포함 하려면

1. VSIX 프로젝트에서 템플릿을 포함 하는 새 폴더를 프로젝트에 추가 합니다.

2. 이 새 폴더에서 다음 하위 폴더를 만든 다음 *로캘 ID* 폴더에 템플릿 (.zip) 파일을 추가 합니다.

     *해당 템플릿 폴더*

     **SharePoint**

     **SharePoint14**

     *로케일 ID*

     *YourTemplateName*

     예를 들어 영어 (미국) 로캘을 지 원하는 ContosoCustomAction.zip 라는 항목 템플릿이 있으면 전체 경로를 *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*수 있습니다.

3. **솔루션 탐색기**에서 템플릿 파일 (*YourTemplateName*)을 선택 합니다.

4. **속성** 창에서 **빌드 작업** 속성을 **콘텐츠**로 설정 합니다.

5. Source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     파일이 디자이너에서 열립니다.

6. 편집기의 **자산** 섹션에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

7. **유형** 목록에서 **VisualStudio** 또는 **VisualStudio**를 선택 합니다.

8. **원본** 목록에서 **파일 시스템의 파일**을 선택 합니다.

9. **경로** 필드에 어셈블리에 대 한 전체 경로를 입력 합니다 (예: *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*). 또는 **찾아보기** 단추를 사용 하 여 어셈블리를 찾아 선택한 다음 **확인** 단추를 선택 합니다.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>프로젝트 템플릿 또는 항목 템플릿에 대 한 마법사를 포함 하려면

1. VSIX 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 **열기**를 선택 합니다.

     파일이 디자이너에서 열립니다.

2. 편집기의 **자산** 섹션에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

3. **유형** 목록에서 **VisualStudio**를 선택 합니다.

4. **원본** 목록에서 다음 단계 중 하나를 수행 합니다.

    - VSIX 프로젝트와 동일한 솔루션에 있는 프로젝트에서 마법사 어셈블리를 빌드하는 경우 **에는 현재 솔루션에서 프로젝트**를 선택 합니다. **프로젝트** 목록에서 프로젝트의 이름을 선택 합니다.

    - 마법사 어셈블리가 프로젝트에 파일로 포함 된 경우 **파일 시스템에서 파일**을 선택 합니다. **경로** 필드에 어셈블리 파일의 전체 경로를 입력 하거나 **찾아보기** 단추를 사용 하 여 어셈블리를 찾아 선택 합니다.

5. **확인** 단추를 선택합니다.

### <a name="related-walkthroughs"></a>관련 연습

다음 표에서는 VSIX 프로젝트를 사용 하 여 다양 한 유형의 SharePoint 도구 확장을 배포 하는 방법을 보여 주는 연습을 보여 줍니다.

|확장 형식|관련 연습|
|--------------------|--------------------------|
|확장 어셈블리만 포함 하는 확장입니다.|[연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [연습: SharePoint 프로젝트 확장 만들기](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [연습: 서버 탐색기 확장에서 SharePoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|SharePoint 명령이 포함 된 확장입니다.|[연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Visual Studio 템플릿을 포함 하는 확장입니다.|[연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|템플릿 마법사를 포함 하는 확장|[연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>수동으로 VSIX 패키지 만들기

SharePoint 도구 확장에 대 한 VSIX 패키지를 수동으로 만들려면 다음 단계를 수행 합니다.

1. Source.extension.vsixmanifest 파일 및 [Content_Types] .xml 파일을 새 폴더에 만듭니다. 자세한 내용은 [VSIX 패키지의 분석](../extensibility/anatomy-of-a-vsix-package.md)을 참조 하세요.

2. Windows 탐색기에서 두 XML 파일이 포함 된 폴더를 마우스 오른쪽 단추로 클릭 하 고 보내기를 클릭 한 다음 압축 (zip) 폴더를 클릭 합니다. 결과 .zip 파일의 이름을 Filename.vsix로 바꿉니다. 여기서 Filename은 패키지를 설치하는 재배포 가능 파일의 이름입니다.

3. VSIX 패키지에 확장 어셈블리를 추가 합니다. 확장에 SharePoint 명령이 포함 된 경우 SharePoint 명령을 구현 하는 어셈블리도 VSIX 패키지에 추가 합니다.

4. Source.extension.vsixmanifest 파일을 수정 합니다.

    - 요소 아래에 요소를 추가한 `Microsoft.VisualStudio.MefComponent` `Assets` 다음 새 요소의 값을 VSIX 패키지에서 확장을 구현 하는 어셈블리의 상대 경로로 설정 합니다. 자세한 내용은 [Mefcomponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))를 참조 하세요.

    - 확장에 SharePoint 용 서버 개체 모델을 호출 하는 SharePoint 명령이 포함 된 경우 요소 아래에 `Microsoft.VisualStudio.Assembly` 요소를 추가 `Assets` 합니다. 새 요소의 값을 VSIX 패키지에서 SharePoint 명령을 구현 하는 어셈블리의 상대 경로로 설정 합니다. 자세한 내용은 [Asset 요소 (VSX 스키마)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)를 참조 하세요.

    - 확장에 프로젝트 템플릿 또는 항목 템플릿이 포함 된 경우 `ProjectTemplate` 요소 아래에 또는 `ItemTemplate` 요소를 추가 `Assets` 합니다. 새 요소의 값을 VSIX 패키지의 템플릿이 포함 된 폴더의 상대 경로로 설정 합니다. 자세한 내용은 [Projecttemplate 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) 및 [ITEMTEMPLATE 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\))를 참조 하세요.

    - 확장에 프로젝트 템플릿 또는 항목 템플릿에 대 한 사용자 지정 마법사가 포함 된 경우 요소 `Assembly` 아래에 요소를 추가 `Assets` 합니다. 새 요소의 값을 VSIX 패키지에 있는 어셈블리의 상대 경로로 설정 하 고 `AssemblyName` 특성을 전체 어셈블리 이름 (버전, culture 및 공개 키 토큰 포함)으로 설정 합니다. 자세한 내용은 [Dependency 요소 (VSX 스키마)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37)를 참조 하세요.

### <a name="example"></a>예

다음 예제에서는 SharePoint 도구 확장에 대 한 source.extension.vsixmanifest 파일의 내용을 보여 줍니다. 확장은 Contoso.ProjectExtension.dll 이라는 어셈블리에 구현 됩니다. 확장에는 Contoso.ExtensionCommands.dll 이름이 지정 된 SharePoint 명령 어셈블리와 VSIX 패키지의 **itemtemplates** 이라는 폴더 아래에 항목 템플릿이 포함 되어 있습니다. 이 예에서는 두 어셈블리가 VSIX 패키지의 source.extension.vsixmanifest 파일과 동일한 폴더에 있는 것으로 가정 합니다.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>추가 정보

- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Visual Studio의 SharePoint 도구에 대 한 디버그 확장](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
