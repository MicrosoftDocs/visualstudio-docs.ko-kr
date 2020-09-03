---
title: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3b84d901a1fd94d72ff14ec5c481e04676c5cbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016398"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부
  사용자 지정 형식의 SharePoint 프로젝트 항목을 정의 하 고 Visual Studio에서 프로젝트 템플릿에 연결한 후에는 템플릿에 대 한 마법사를 제공할 수도 있습니다. 사용자가 템플릿을 사용 하 여 프로젝트 항목을 포함 하는 새 프로젝트를 만들 때이 마법사를 사용 하 여 사용자 로부터 정보를 수집할 수 있습니다. 수집 하는 정보를 사용 하 여 프로젝트 항목을 초기화할 수 있습니다.

 이 연습에서는 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)에서 보여 주는 사이트 열 프로젝트 템플릿에 마법사를 추가 합니다. 사용자가 사이트 열 프로젝트를 만드는 경우 마법사는 사이트 열 (예: 기본 형식 및 그룹)에 대 한 정보를 수집 하 고이 정보를 새 프로젝트의 *Elements.xml* 파일에 추가 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 프로젝트 템플릿과 연결 된 사용자 지정 SharePoint 프로젝트 항목 형식에 대 한 마법사 만들기

- Visual Studio에서 SharePoint 프로젝트에 대 한 기본 제공 마법사와 비슷한 사용자 지정 마법사 UI를 정의 합니다.

- 마법사를 실행 하는 동안 로컬 SharePoint 사이트를 호출 하는 데 사용 되는 두 개의 *sharepoint 명령* 만들기 SharePoint 명령은 Visual Studio 확장에서 SharePoint 서버 개체 모델의 Api를 호출 하는 데 사용할 수 있는 메서드입니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

- 대체 가능 매개 변수를 사용 하 여 마법사에서 수집한 데이터로 SharePoint 프로젝트 파일 초기화

- 새 각 사이트 열 프로젝트 인스턴스에 새 .snk 파일을 만듭니다. 이 파일은 SharePoint 솔루션 어셈블리를 전역 어셈블리 캐시에 배포할 수 있도록 프로젝트 출력에 서명 하는 데 사용 됩니다.

- 마법사 디버깅 및 테스트

> [!NOTE]
> 일련의 샘플 워크플로는 [SharePoint workflow samples](/sharepoint/dev/general-development/sharepoint-workflow-samples)를 참조 하십시오.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 수행 하려면 먼저 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)완료 하 여 SiteColumnProjectItem 솔루션을 만들어야 합니다.

 또한이 연습을 완료 하려면 개발 컴퓨터에 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Windows, SharePoint 및 Visual Studio

- Visual Studio SDK입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- Visual Studio의 프로젝트 및 항목 템플릿에 대 한 마법사입니다. 자세한 내용은 [방법: 프로젝트 템플릿과 인터페이스에서 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md) 을 참조 하세요 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

- SharePoint의 사이트 열입니다. 자세한 내용은 [열](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))을 참조 하세요.

## <a name="understand-the-wizard-components"></a>마법사 구성 요소 이해
 이 연습에서 설명 하는 마법사에는 몇 가지 구성 요소가 포함 되어 있습니다. 다음 표에서는 이러한 구성 요소에 대해 설명 합니다.

|구성 요소|설명|
|---------------|-----------------|
|마법사 구현|인터페이스를 구현 하는 라는 클래스입니다 `SiteColumnProjectWizard` <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . 이 인터페이스는 마법사가 시작 되 고 완료 될 때 그리고 마법사가 실행 되는 동안 특정 시간에 Visual Studio에서 호출 하는 메서드를 정의 합니다.|
|마법사 UI|이는 이라는 WPF 기반 창입니다 `WizardWindow` . 이 창에는 및 라는 두 개의 사용자 컨트롤이 포함 됩니다 `Page1` `Page2` . 이러한 사용자 정의 컨트롤은 마법사의 두 페이지를 나타냅니다.<br /><br /> 이 연습에서 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 마법사 구현의 메서드는 마법사 UI를 표시 합니다.|
|마법사 데이터 모델|이 클래스는 `SiteColumnWizardModel` 마법사 UI와 마법사 구현 간의 계층을 제공 하는 라는 중간 클래스입니다. 이 샘플에서는이 클래스를 사용 하 여 마법사 구현과 마법사 UI를 서로 추상화 합니다. 이 클래스는 모든 마법사의 필수 구성 요소가 아닙니다.<br /><br /> 이 연습에서 마법사 구현은 마법사 `SiteColumnWizardModel` UI가 표시 될 때 개체를 마법사 창에 전달 합니다. 마법사 UI는이 개체의 메서드를 사용 하 여 UI에 컨트롤의 값을 저장 하 고 입력 사이트 URL이 유효한 지 확인 하는 등의 작업을 수행 합니다. 사용자가 마법사를 완료 한 후 마법사 구현은 개체를 사용 하 여 `SiteColumnWizardModel` UI의 최종 상태를 확인 합니다.|
|프로젝트 서명 관리자|이 클래스는 `ProjectSigningManager` 마법사 구현에서 새 각 프로젝트 인스턴스에 새 key.snk 파일을 만드는 데 사용 하는 라는 도우미 클래스입니다.|
|SharePoint 명령|마법사를 실행 하는 동안 마법사 데이터 모델에서 로컬 SharePoint 사이트를 호출 하는 데 사용 하는 메서드입니다. SharePoint 명령은 .NET Framework 3.5를 대상으로 해야 하므로 이러한 명령은 나머지 마법사 코드와는 다른 어셈블리에 구현 됩니다.|

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):에서 만든 SiteColumnProjectItem 솔루션에 여러 프로젝트를 추가 해야 합니다.

- WPF 프로젝트입니다. 인터페이스를 구현 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 하 고이 프로젝트에서 마법사 UI를 정의 합니다.

- SharePoint 명령을 정의 하는 클래스 라이브러리 프로젝트입니다. 이 프로젝트는 the.NET Framework 3.5를 대상으로 해야 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-wpf-project"></a>WPF 프로젝트를 만들려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem 솔루션을 엽니다.

2. **솔루션 탐색기**에서 **SiteColumnProjectItem** 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

3. **새 프로젝트 추가** 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 4.5** 이 선택 되어 있는지 확인 합니다.

4. **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 하 고 **Windows** 노드를 선택 합니다.

5. 프로젝트 템플릿 목록에서 **WPF 사용자 정의 컨트롤 라이브러리**를 선택 하 고 프로젝트 이름을 **projecttemplate 마법사**로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Projecttemplatewizard** 프로젝트를 솔루션에 추가 하 고 기본 UserControl1 .xaml 파일을 엽니다.

6. 프로젝트에서 UserControl1 .xaml 파일을 삭제 합니다.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint 명령 프로젝트를 만들려면

1. **솔루션 탐색기**에서 SiteColumnProjectItem 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

2. **새 프로젝트 추가** 대화 상자의 맨 위에 있는 .NET Framework 버전 목록에서 **.NET Framework 3.5** 를 선택 합니다.

3. **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

4. **클래스 라이브러리** 프로젝트 템플릿을 선택 하 고 프로젝트 이름을 **SharePointCommands**로 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SharePointCommands** 프로젝트를 솔루션에 추가 하 고 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-projects"></a>프로젝트 구성
 마법사를 만들기 전에 일부 코드 파일 및 어셈블리 참조를 프로젝트에 추가 해야 합니다.

#### <a name="to-configure-the-wizard-project"></a>마법사 프로젝트를 구성 하려면

1. **솔루션 탐색기**에서 **projecttemplatewizard** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **프로젝트 디자이너**에서 Visual c # 프로젝트의 경우 **응용 프로그램** 탭을 선택 하 고 Visual Basic 프로젝트의 경우 **컴파일** 탭을 선택 합니다.

3. 대상 프레임 워크가 .NET Framework 4.5 클라이언트 프로필이 아닌 .NET Framework 4.5으로 설정 되어 있는지 확인 합니다.

     자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/visual-studio-multi-targeting-overview.md)을 참조 하세요.

4. **Project템플릿 마법사** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

5. **창 (WPF)** 항목을 선택 하 고 항목 이름을 **wizardwindow**로 지정한 다음 **추가** 단추를 선택 합니다.

6. 프로젝트에 두 개의 **사용자 정의 컨트롤 (WPF)** 항목을 추가 하 고 이름을 **1에서 2로, 2** -2로 이름을 **로 합니다.**

7. 4 개의 코드 파일을 프로젝트에 추가 하 고 다음 이름을 지정 합니다.

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - CommandIds

8. **Projecttemplatewizard** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

9. **어셈블리** 노드를 확장 하 고 **확장** 노드를 선택 하 고 다음 어셈블리 옆의 확인란을 선택 합니다.

    - EnvDTE

    - VisualStudio.

    - VisualStudio

    - VisualStudio.

    - VisualStudio입니다.

    - VisualStudio입니다.

    - Microsoft.VisualStudio.TemplateWizardInterface

10. 프로젝트에 어셈블리를 추가 하려면 **확인** 단추를 선택 합니다.

11. **솔루션 탐색기**의 **project템플릿 마법사** 프로젝트에 대 한 **참조** 폴더 아래에서 **EnvDTE**를 선택 합니다.

12. **속성** 창에서 **Interop 형식 포함** 속성의 값을 **False**로 변경 합니다.

13. Visual Basic 프로젝트를 개발 하는 경우 **프로젝트 디자이너**를 사용 하 여 Project템플릿 마법사 네임 스페이스를 프로젝트로 가져옵니다.

     자세한 내용은 [방법: 가져온 네임 스페이스 추가 또는 제거 &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)를 참조 하세요.

#### <a name="to-configure-the-sharepointcommands-project"></a>SharePointcommands 프로젝트를 구성 하려면

1. **솔루션 탐색기**에서 **SharePointCommands** 프로젝트 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**,  **기존 항목 추가**를 선택 합니다.

3. **기존 항목 추가** 대화 상자에서 ProjectTemplateWizard 프로젝트의 코드 파일이 포함 된 폴더를 찾은 다음 **CommandIds** 코드 파일을 선택 합니다.

4. **추가** 단추 옆의 화살표를 선택 하 고 표시 되는 메뉴에서 **링크로 추가** 옵션을 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**SharePointCommands** 프로젝트에 코드 파일을 링크로 추가 합니다. 코드 파일은 **Projecttemplatewizard** 프로젝트에 있지만 파일의 코드도 **SharePointCommands** 프로젝트에서 컴파일됩니다.

5. **SharePointCommands** 프로젝트에서 명령 이라는 다른 코드 파일을 추가 합니다.

6. SharePointCommands 프로젝트를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **참조 추가**를 선택 합니다.

7. **어셈블리** 노드를 확장 하 고 **확장** 노드를 선택 하 고 다음 어셈블리 옆의 확인란을 선택 합니다.

    - Microsoft SharePoint

    - VisualStudio.

8. 프로젝트에 어셈블리를 추가 하려면 **확인** 단추를 선택 합니다.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>마법사 모델, 서명 관리자 및 SharePoint 명령 Id 만들기
 ProjectTemplateWizard 프로젝트에 코드를 추가 하 여 샘플에서 다음 구성 요소를 구현 합니다.

- SharePoint 명령 Id입니다. 이러한 문자열은 마법사에서 사용 하는 SharePoint 명령을 식별 합니다. 이 연습 뒷부분에서는 SharePointCommands 프로젝트에 코드를 추가 하 여 명령을 구현 합니다.

- 마법사 데이터 모델입니다.

- 프로젝트 서명 관리자입니다.

  이러한 구성 요소에 대 한 자세한 내용은 [마법사 구성 요소 이해](#understand-the-wizard-components)를 참조 하세요.

#### <a name="to-define-the-sharepoint-command-ids"></a>SharePoint 명령 Id를 정의 하려면

1. ProjectTemplateWizard 프로젝트에서 CommandIds 코드 파일을 열고이 파일의 전체 내용을 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>마법사 모델을 만들려면

1. SiteColumnWizardModel 코드 파일을 열고이 파일의 전체 내용을 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>프로젝트 서명 관리자를 만들려면

1. ProjectSigningManager 코드 파일을 열고이 파일의 전체 내용을 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>마법사 UI 만들기
 마법사 창의 UI를 정의 하 고 마법사 페이지의 UI를 제공 하는 두 개의 사용자 컨트롤을 정의 하는 XAML을 추가 하 고 창 및 사용자 정의 컨트롤의 동작을 정의 하는 코드를 추가 합니다. 만든 마법사는 Visual Studio의 SharePoint 프로젝트에 대 한 기본 제공 마법사와 유사 합니다.

> [!NOTE]
> 다음 단계에서는 프로젝트에 XAML 또는 코드를 추가한 후 프로젝트에 컴파일 오류가 발생 합니다. 이러한 오류는 이후 단계에서 코드를 추가할 때 사라집니다.

#### <a name="to-create-the-wizard-window-ui"></a>마법사 창 UI를 만들려면

1. ProjectTemplateWizard 프로젝트에서 WizardWindow .xaml 파일에 대 한 바로 가기 메뉴를 열고 **열기** 를 선택 하 여 디자이너에서 창을 엽니다.

2. 디자이너의 XAML 뷰에서 현재 XAML을 다음 XAML로 바꿉니다. XAML은 머리글, <xref:System.Windows.Controls.Grid> 마법사 페이지를 포함 하는, 창 맨 아래에 있는 탐색 단추를 포함 하는 UI를 정의 합니다.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > 이 XAML에서 만든 창은 기본 클래스에서 파생 됩니다 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> . Visual Studio에 사용자 지정 WPF 대화 상자를 추가 하는 경우이 클래스에서 대화 상자를 파생 시켜 다른 Visual Studio 대화 상자와 일관 된 스타일을 유지 하 고 그렇지 않을 수 있는 모달 대화 상자 문제를 방지 하는 것이 좋습니다. 자세한 내용은 [모달 대화 상자 만들기 및 관리](../extensibility/creating-and-managing-modal-dialog-boxes.md)를 참조 하세요.

3. Visual Basic 프로젝트를 개발 하는 경우 `ProjectTemplateWizard` `WizardWindow` 요소의 특성에 있는 클래스 이름에서 네임 스페이스를 제거 `x:Class` `Window` 합니다. 이 요소는 XAML의 첫 번째 줄에 있습니다. 완료 되 면 첫 번째 줄은 다음 예제와 같습니다.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow .xaml 파일에 대 한 코드 숨겨진 파일을 엽니다.

5. 파일 맨 위에 있는 선언을 제외 하 고 다음 코드를 사용 하 여이 파일의 내용을 바꿉니다 `using` .

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>첫 번째 마법사 페이지 UI를 만들려면

1. ProjectTemplateWizard 프로젝트에서 파일의 바로 가기 메뉴를 연 다음 **열기** 를 선택 하 여 디자이너에서 사용자 정의 컨트롤을 엽니다.

2. 디자이너의 XAML 뷰에서 현재 XAML을 다음 XAML로 바꿉니다. XAML은 사용자가 디버깅에 사용할 로컬 사이트의 URL을 입력할 수 있는 텍스트 상자를 포함 하는 UI를 정의 합니다. 또한 UI에는 사용자가 프로젝트를 샌드 박싱 할지 여부를 지정할 수 있는 옵션 단추도 포함 되어 있습니다.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Visual Basic 프로젝트를 개발 하는 경우 `ProjectTemplateWizard` `Page1` 요소의 특성에 있는 클래스 이름에서 네임 스페이스를 제거 `x:Class` `UserControl` 합니다. 이는 XAML의 첫 번째 줄에 있습니다. 완료 되 면 첫 번째 줄은 다음과 같이 표시 됩니다.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. 파일 맨 위에 있는 선언을 제외 하 고 다음 코드를 사용 하 여 파일의 내용을 바꿉니다. `using`

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>두 번째 마법사 페이지 UI를 만들려면

1. ProjectTemplateWizard 프로젝트에서 파일 (.xaml) 파일에 대 한 바로 가기 메뉴를 연 다음 **열기**를 선택 합니다.

     사용자 정의 컨트롤이 디자이너에서 열립니다.

2. XAML 뷰에서 현재 XAML을 다음 XAML로 바꿉니다. XAML은 사이트 열의 기본 유형을 선택할 수 있는 드롭다운 목록을 포함 하는 UI를 정의 하 고, 갤러리에 사이트 열을 표시할 기본 제공 또는 사용자 지정 그룹을 지정 하는 콤보 상자와 사이트 열의 이름을 지정 하기 위한 텍스트 상자를 정의 합니다.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Visual Basic 프로젝트를 개발 하는 경우 `ProjectTemplateWizard` `Page2` 요소의 특성에 있는 클래스 이름에서 네임 스페이스를 제거 `x:Class` `UserControl` 합니다. 이는 XAML의 첫 번째 줄에 있습니다. 완료 되 면 첫 번째 줄은 다음과 같이 표시 됩니다.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. `using`파일의 맨 위에 있는 선언을 제외 하 고 다음 코드를 사용 하 여 파일의 코드에 포함 된 파일의 내용을 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>마법사 구현
 인터페이스를 구현 하 여 마법사의 주요 기능을 정의 합니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . 이 인터페이스는 마법사가 시작 되 고 완료 될 때 그리고 마법사가 실행 되는 동안 특정 시간에 Visual Studio에서 호출 하는 메서드를 정의 합니다.

#### <a name="to-implement-the-wizard"></a>마법사를 구현 하려면

1. ProjectTemplateWizard 프로젝트에서 SiteColumnProjectWizard 코드 파일을 엽니다.

2. 이 파일의 전체 내용을 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>SharePoint 명령 만들기
 SharePoint 서버 개체 모델을 호출 하는 두 개의 사용자 지정 명령을 만듭니다. 한 명령은 마법사에서 사용자가 입력 하는 사이트 URL이 유효한 지 여부를 확인 합니다. 다른 명령은 사용자가 새 사이트 열의 기반으로 사용할 항목을 선택할 수 있도록 지정 된 SharePoint 사이트에서 모든 필드 형식을 가져옵니다.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint 명령을 정의 하려면

1. **SharePointCommands** 프로젝트에서 명령 코드 파일을 엽니다.

2. 이 파일의 전체 내용을 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 마법사의 모든 코드가 이제 프로젝트에 있습니다. 프로젝트를 빌드하여 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-your-project"></a>프로젝트를 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>프로젝트 템플릿에서 키 .snk 파일을 제거 하는 중
 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), 만든 프로젝트 템플릿에는 각 사이트 열 프로젝트 인스턴스에 서명 하는 데 사용 되는 key.snk 파일이 포함 되어 있습니다. 이제 마법사에서 각 프로젝트에 대 한 새 key.snk 파일을 생성 하므로이 key.snk 파일은 더 이상 필요 하지 않습니다. 프로젝트 템플릿에서 키 .snk 파일을 제거 하 고이 파일에 대 한 참조를 제거 합니다.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>프로젝트 템플릿에서 키 .snk 파일을 제거 하려면

1. **솔루션 탐색기**의 **SiteColumnProjectTemplate** 노드에서 **key.snk** 파일의 바로 가기 메뉴를 열고 **삭제**를 선택 합니다.

2. 나타나는 확인 대화 상자에서 **확인** 단추를 선택합니다.

3. **SiteColumnProjectTemplate** 노드 아래에서 SiteColumnProjectTemplate 파일을 열고 다음 요소를 제거 합니다.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. 파일을 저장하고 닫습니다.

5. **SiteColumnProjectTemplate** 노드에서 projecttemplate .Csproj 또는 projecttemplate .vbproj 파일을 열고 다음 요소를 제거 `PropertyGroup` 합니다.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. 다음 요소를 제거 `None` 합니다.

    ```xml
    <None Include="key.snk" />
    ```

7. 파일을 저장하고 닫습니다.

## <a name="associating-the-wizard-with-the-project-template"></a>마법사를 프로젝트 템플릿과 연결
 마법사를 구현 했으므로 마법사를 **사이트 열** 프로젝트 템플릿과 연결 해야 합니다. 이 작업을 수행 하려면 다음 세 가지 절차를 완료 해야 합니다.

1. 강력한 이름을 사용 하 여 마법사 어셈블리에 서명 합니다.

2. 마법사 어셈블리에 대 한 공개 키 토큰을 가져옵니다.

3. **사이트 열** 프로젝트 템플릿에 대 한 .vstemplate 파일에서 마법사 어셈블리에 대 한 참조를 추가 합니다.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>강력한 이름을 사용 하 여 마법사 어셈블리에 서명 하려면

1. **솔루션 탐색기**에서 **project템플릿 마법사** 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **서명** 탭에서 **어셈블리 서명** 확인란을 선택합니다.

3. **강력한 이름 키 파일 선택** 목록에서을 선택 **\<New...>** 합니다.

4. **강력한 이름 키 만들기** 대화 상자에서 새 키 파일의 이름을 입력 하 고 **암호를 사용 하 여 키 파일 보호** 확인란의 선택을 취소 한 다음 **확인** 단추를 선택 합니다.

5. **Project템플릿 마법사** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드** 를 선택 하 여 ProjectTemplateWizard.dll 파일을 만듭니다.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>마법사 어셈블리에 대 한 공개 키 토큰을 가져오려면

1. **시작 메뉴**에서 **모든 프로그램**을 선택 하 고 **Microsoft Visual Studio**를 선택한 다음 **Visual Studio Tools**를 선택 하 고 **개발자 명령 프롬프트**를 선택 합니다.

     Visual Studio 명령 프롬프트 창이 열립니다.

2. 다음 명령을 실행 하 여 *PathToWizardAssembly* 를 개발 컴퓨터의 ProjectTemplateWizard 프로젝트에 대 한 빌드된 ProjectTemplateWizard.dll 어셈블리의 전체 경로로 바꿉니다.

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     ProjectTemplateWizard.dll 어셈블리의 공개 키 토큰은 Visual Studio 명령 프롬프트 창에 기록 됩니다.

3. Visual Studio 명령 프롬프트 창을 열어 둡니다. 다음 절차를 수행 하는 동안 공개 키 토큰이 필요 합니다.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.Vstemplate 파일에서 마법사 어셈블리에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 **SiteColumnProjectTemplate** 프로젝트 노드를 확장 하 고 SiteColumnProjectTemplate 파일을 엽니다.

2. 파일의 끝 부분에서 `WizardExtension` 및 태그 사이에 다음 요소를 추가 `</TemplateContent>` 합니다 `</VSTemplate>` . 특성의 *토큰* 값을 `PublicKeyToken` 이전 절차에서 가져온 공개 키 토큰으로 바꿉니다.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     요소에 대 한 자세한 내용은 `WizardExtension` [WizardExtension Element &#40;Visual Studio Templates&#41;](../extensibility/wizardextension-element-visual-studio-templates.md)를 참조 하세요.

3. 파일을 저장하고 닫습니다.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>프로젝트 템플릿에서 Elements.xml 파일에 대체 가능 매개 변수 추가
 SiteColumnProjectTemplate 프로젝트의 *Elements.xml* 파일에 여러 대체 가능 매개 변수를 추가 합니다. 이러한 매개 변수는 앞에서 `RunStarted` 정의한 클래스의 메서드에서 초기화 됩니다 `SiteColumnProjectWizard` . 사용자가 사이트 열 프로젝트를 만들 때 Visual Studio는 새 프로젝트의 *Elements.xml* 파일에서 이러한 매개 변수를 마법사에서 지정한 값으로 자동으로 바꿉니다.

 대체 가능 매개 변수는 달러 기호 ($) 문자로 시작 하 고 끝나는 토큰입니다. 사용자 고유의 대체 가능 매개 변수를 정의 하는 것 외에도 SharePoint 프로젝트 시스템에서 정의 하 고 초기화 하는 기본 제공 매개 변수를 사용할 수 있습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조 하세요.

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Elements.xml 파일에 대체 가능 매개 변수를 추가 하려면

1. SiteColumnProjectTemplate 프로젝트에서 *Elements.xml* 파일의 내용을 다음 XML로 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     새 XML은,, 및 특성의 값을 `Name` `DisplayName` `Type` `Group` 사용자 지정 대체 가능 매개 변수로 변경 합니다.

2. 파일을 저장하고 닫습니다.

## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에 마법사 추가
 사이트 열 프로젝트 템플릿이 포함 된 VSIX 패키지를 사용 하 여 마법사를 배포 하려면 VSIX 프로젝트의 source.extension.vsixmanifest 파일에 마법사 프로젝트 및 SharePoint commands 프로젝트에 대 한 참조를 추가 합니다.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에 마법사를 추가 하려면

1. **솔루션 탐색기**의 **SiteColumnProjectItem** 프로젝트에서 **source.extension.vsixmanifest** 파일에 대 한 바로 가기 메뉴를 연 다음 **열기**를 선택 합니다.

     Visual Studio가 매니페스트 편집기에서 파일을 엽니다.

2. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

3. **유형** 목록에서 **VisualStudio**를 선택 합니다.

4. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

5. **프로젝트** 목록에서 **projecttemplatewizard**를 선택 하 고 **확인** 단추를 선택 합니다.

6. 편집기의 **자산** 탭에서 **새로 만들기** 단추를 다시 선택 합니다.

     **새 자산 추가** 대화 상자가 열립니다.

7. **유형** 목록에서 **SharePoint. Commands**를 입력 합니다.

8. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

9. **프로젝트** 목록에서 **SharePointCommands** 프로젝트를 선택한 다음 **확인** 단추를 선택 합니다.

10. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 다음 솔루션이 오류 없이 빌드되는지 확인 합니다.

## <a name="test-the-wizard"></a>마법사 테스트
 이제 마법사를 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 SiteColumnProjectItem 솔루션의 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 사이트 열 프로젝트에 대 한 마법사를 테스트 합니다. 마지막으로 프로젝트를 빌드하고 실행 하 여 사이트 열이 예상 대로 작동 하는지 확인 합니다.

#### <a name="to-start-debugging-the-solution"></a>솔루션 디버깅을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 SiteColumnProjectItem 솔루션을 엽니다.

2. ProjectTemplateWizard 프로젝트에서 SiteColumnProjectWizard 코드 파일을 연 다음 메서드의 첫 번째 코드 줄에 중단점을 추가 합니다 `RunStarted` .

3. 메뉴 모음에서 **디버그**  >  **예외**를 선택 합니다.

4. **예외** 대화 상자에서 **공용 언어 런타임 예외** 에 대해 **throw** 됨 및 **사용자가 처리 하지 않은** 확인란이 선택 취소 되었는지 확인 하 고 **확인** 단추를 선택 합니다.

5. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio에서 마법사를 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서, 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. 프로젝트 템플릿에서 지 원하는 언어에 따라 **Visual c #** 노드 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **사이트 열**을 선택 하 고 프로젝트 이름을 **SiteColumnWizardTest**로 지정한 다음 **확인** 단추를 선택 합니다.

4. 메서드의 이전에 설정한 중단점에서 Visual Studio의 다른 인스턴스의 코드가 중지 되는지 확인 `RunStarted` 합니다.

5. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**계속을 선택 하 여 프로젝트를 계속 디버깅  >  **Continue**합니다.

6. **SharePoint 사용자 지정 마법사**에서 디버깅에 사용할 사이트의 URL을 입력 하 고 **다음** 단추를 선택 합니다.

7. **SharePoint 사용자 지정 마법사**의 두 번째 페이지에서 다음과 같이 선택 합니다.

   - **유형** 목록에서 **부울**을 선택 합니다.

   - **그룹** 목록에서 **사용자 지정 예/아니요 열**을 선택 합니다.

   - **이름** 상자에 **내 예/아니요 열**을 입력 한 후 **마침** 단추를 선택 합니다.

     **솔루션 탐색기**새 프로젝트가 표시 되 고 **Field1**이라는 프로젝트 항목이 포함 되며, Visual Studio에서 프로젝트의 *Elements.xml* 파일을 편집기에서 엽니다.

8. *Elements.xml* 에 마법사에서 지정한 값이 포함 되어 있는지 확인 합니다.

#### <a name="to-test-the-site-column-in-sharepoint"></a>SharePoint에서 사이트 열을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 **F5** 키를 선택 합니다.

     사이트 열이 패키지 되 고 프로젝트의 **사이트 URL** 속성이 지정 하는 SharePoint 사이트에 배포 됩니다. 웹 브라우저가이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > **스크립트 디버깅 사용 안 함** 대화 상자가 나타나면 **예** 단추를 선택 하 여 프로젝트를 계속 디버깅 합니다.

2. **사이트 작업** 메뉴에서 **사이트 설정**을 선택 합니다.

3. 사이트 설정 페이지의 **갤러리**에서 **사이트 열** 링크를 선택 합니다.

4. 사이트 열 목록에서 **사용자 지정 예/아니요 열** 그룹에 **예/아니요 열**이라는 열이 포함 되어 있는지 확인 한 다음 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목 테스트를 마친 후 Visual Studio의 실험적 인스턴스에서 프로젝트 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **사이트 열**을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것인지 확인 하 고 **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

4. Visual Studio의 실험적 인스턴스와 CustomActionProjectItem 솔루션이 열려 있는 인스턴스를 모두 닫습니다.

     확장을 배포 하는 방법에 대 한 자세한 내용은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [Visual Studio 확장](../extensibility/shipping-visual-studio-extensions.md)제공을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)
