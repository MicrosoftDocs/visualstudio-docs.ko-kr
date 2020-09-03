---
title: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부
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
ms.openlocfilehash: c96546f85b21ee0ca8a559059a16158b743cb915
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016106"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부
  사용자 지정 형식의 SharePoint 프로젝트 항목을 정의 하 고 Visual Studio에서 항목 템플릿과 연결한 후에는 템플릿에 대 한 마법사를 제공할 수도 있습니다. 사용자가 템플릿을 사용 하 여 프로젝트 항목의 새 인스턴스를 프로젝트에 추가 하는 경우 마법사를 사용 하 여 사용자 로부터 정보를 수집할 수 있습니다. 수집 하는 정보를 사용 하 여 프로젝트 항목을 초기화할 수 있습니다.

 이 연습에서는 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)에서 보여 주는 사용자 지정 작업 프로젝트 항목에 마법사를 추가 합니다. 사용자가 SharePoint 프로젝트에 사용자 지정 작업 프로젝트 항목을 추가 하면 마법사에서 사용자 지정 작업 (예: 최종 사용자가 선택할 때 탐색할 URL)에 대 한 정보를 수집 하 고이 정보를 새 프로젝트 항목의 *Elements.xml* 파일에 추가 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 항목 템플릿과 연결 된 사용자 지정 SharePoint 프로젝트 항목 형식에 대 한 마법사를 만듭니다.

- Visual Studio에서 SharePoint 프로젝트 항목에 대 한 기본 제공 마법사와 비슷한 사용자 지정 마법사 UI를 정의 합니다.

- 대체 가능 매개 변수를 사용 하 여 마법사에서 수집한 데이터로 SharePoint 프로젝트 파일 초기화

- 마법사 디버깅 및 테스트

> [!NOTE]
> 워크플로에 대 한 사용자 지정 활동을 만드는 방법을 보여 주는 [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) 에서 샘플을 다운로드할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 수행 하려면 먼저 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부를](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)완료 하 여 CustomActionProjectItem 솔루션을 만들어야 합니다.

 또한이 연습을 완료 하려면 개발 컴퓨터에 다음 구성 요소가 필요 합니다.

- 지원 되는 버전의 Windows, SharePoint 및 Visual Studio

- Visual Studio SDK입니다. 이 연습에서는 SDK의 **Vsix 프로젝트** 템플릿을 사용 하 여 프로젝트 항목을 배포할 vsix 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

  다음 개념에 대 한 정보는 연습을 완료 하는 데 도움이 되지만 반드시 필요한 것은 아닙니다.

- Visual Studio의 프로젝트 및 항목 템플릿에 대 한 마법사입니다. 자세한 내용은 [방법: 프로젝트 템플릿과 인터페이스에서 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md) 을 참조 하세요 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

- SharePoint의 사용자 지정 작업. 자세한 내용은 [사용자 지정 작업](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14))을 참조 하세요.

## <a name="create-the-wizard-project"></a>마법사 프로젝트 만들기
 이 연습을 완료 하려면 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)에서 만든 CustomActionProjectItem 솔루션에 프로젝트를 추가 해야 합니다. 인터페이스를 구현 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 하 고이 프로젝트에서 마법사 UI를 정의 합니다.

#### <a name="to-create-the-wizard-project"></a>마법사 프로젝트를 만들려면

1. Visual Studio에서 CustomActionProjectItem 솔루션을 엽니다.

2. **솔루션 탐색기**에서 솔루션 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 프로젝트**를 선택 합니다.

3. **새 프로젝트** 대화 상자에서 **Visual c #** 또는 **Visual Basic** 노드를 확장 한 다음 **Windows** 노드를 선택 합니다.

4. **새 프로젝트** 대화 상자의 맨 위에서 .NET Framework 버전 목록에 **.NET Framework 4.5** 이 선택 되어 있는지 확인 합니다.

5. **WPF 사용자 정의 컨트롤 라이브러리** 프로젝트 템플릿을 선택 하 고 프로젝트 **itemtemplate 마법사**의 이름을 지정한 다음 **확인** 단추를 선택 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Item템플릿 마법사** 프로젝트를 솔루션에 추가 합니다.

6. 프로젝트에서 UserControl1 항목을 삭제 합니다.

## <a name="configure-the-wizard-project"></a>마법사 프로젝트 구성
 마법사를 만들기 전에 Windows Presentation Foundation (WPF) 창, 코드 파일 및 어셈블리 참조를 프로젝트에 추가 해야 합니다.

#### <a name="to-configure-the-wizard-project"></a>마법사 프로젝트를 구성 하려면

1. **솔루션 탐색기**의 **item템플릿 마법사** 프로젝트 노드에서 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **프로젝트 디자이너**에서 대상 프레임 워크가 .NET Framework 4.5로 설정 되어 있는지 확인 합니다.

     Visual c # 프로젝트의 경우 **응용 프로그램** 탭에서이 값을 설정할 수 있습니다. Visual Basic 프로젝트의 경우 **컴파일** 탭에서이 값을 설정할 수 있습니다. 자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/visual-studio-multi-targeting-overview.md)을 참조 하세요.

3. **Item템플릿 마법사** 프로젝트에서 **창 (WPF)** 항목을 프로젝트에 추가 하 고 항목의 이름을 **wizardwindow**로 지정한 다음

4. CustomActionWizard 및 Strings 라는 두 개의 코드 파일을 추가 합니다.

5. **Item템플릿 마법사** 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

6. **참조 관리자-Item템플릿 마법사** 대화 상자의 **어셈블리** 노드에서 **확장** 노드를 선택 합니다.

7. 다음 어셈블리 옆의 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

    - EnvDTE

    - VisualStudio.

    - Microsoft.VisualStudio.TemplateWizardInterface

8. **솔루션 탐색기**의 Item템플릿 마법사 프로젝트에 대 한 **참조** 폴더에서 **EnvDTE** 참조를 선택 합니다.

9. **속성** 창에서 **Interop 형식 포함** 속성의 값을 **False**로 변경 합니다.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>사용자 지정 작업의 기본 위치 및 ID 문자열을 정의 합니다.
 모든 사용자 지정 작업에는 `GroupID` `Location` `CustomAction` *Elements.xml* 파일에 있는 요소의 및 특성에 지정 된 위치와 ID가 있습니다. 이 단계에서는 Item템플릿 마법사 프로젝트에서 이러한 특성에 대 한 유효한 문자열 중 일부를 정의 합니다. 이 연습을 완료 하면 사용자가 마법사에서 위치 및 ID를 지정할 때 이러한 문자열이 사용자 지정 작업 프로젝트 항목의 *Elements.xml* 파일에 기록 됩니다.

 편의상이 샘플은 사용 가능한 기본 위치 및 Id의 하위 집합만 지원 합니다. 전체 목록은 [기본 사용자 지정 작업 위치 및 id](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))를 참조 하세요.

#### <a name="to-define-the-default-location-and-id-strings"></a>기본 위치 및 ID 문자열을 정의 하려면

1. 열린.

2. **Item템플릿 마법사** 프로젝트에서 문자열 코드 파일의 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>마법사 UI 만들기
 마법사의 UI를 정의 하는 XAML을 추가 하 고 마법사의 일부 컨트롤을 ID 문자열에 바인딩하는 코드를 추가 합니다. 만든 마법사는 Visual Studio의 SharePoint 프로젝트에 대 한 기본 제공 마법사와 유사 합니다.

#### <a name="to-create-the-wizard-ui"></a>마법사 UI를 만들려면

1. **Item템플릿 마법사** 프로젝트에서 **wizardwindow .xaml** 파일에 대 한 바로 가기 메뉴를 열고 **열기** 를 선택 하 여 디자이너에서 창을 엽니다.

2. XAML 뷰에서 현재 XAML을 다음 XAML로 바꿉니다. XAML은 머리글, 사용자 지정 작업의 동작을 지정 하는 컨트롤 및 창의 아래쪽에 있는 탐색 단추를 포함 하는 UI를 정의 합니다.

    > [!NOTE]
    > 이 코드를 추가한 후 프로젝트에 컴파일 오류가 발생 합니다. 이러한 오류는 이후 단계에서 코드를 추가할 때 사라집니다.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > 이 XAML에서 만든 창은 기본 클래스에서 파생 됩니다 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> . Visual Studio에 사용자 지정 WPF 대화 상자를 추가 하는 경우이 클래스에서 대화 상자를 파생 하 여 Visual Studio의 다른 대화 상자와 일관 된 스타일을 유지 하 고, 모달 대화 상자에서 발생할 수 있는 문제를 방지 하는 것이 좋습니다. 자세한 내용은 [모달 대화 상자 만들기 및 관리](../extensibility/creating-and-managing-modal-dialog-boxes.md)를 참조 하세요.

3. Visual Basic 프로젝트를 개발 하는 경우 `ItemTemplateWizard` `WizardWindow` 요소의 특성에 있는 클래스 이름에서 네임 스페이스를 제거 `x:Class` `Window` 합니다. 이 요소는 XAML의 첫 번째 줄에 있습니다. 완료 되 면 첫 번째 줄은 다음 코드와 유사 하 게 표시 됩니다.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. WizardWindow .xaml 파일의 코드 숨김이 파일에서 현재 코드를 다음 코드로 바꿉니다.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>마법사 구현
 인터페이스를 구현 하 여 마법사의 기능을 정의 합니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

#### <a name="to-implement-the-wizard"></a>마법사를 구현 하려면

1. **Item템플릿 마법사** 프로젝트에서 **CustomActionWizard** 코드 파일을 열고이 파일의 현재 코드를 다음 코드로 바꿉니다.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>검사점
 연습의이 시점에서 마법사의 모든 코드가 이제 프로젝트에 있습니다. 프로젝트를 빌드하여 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-your-project"></a>프로젝트를 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="associate-the-wizard-with-the-item-template"></a>마법사를 항목 템플릿과 연결
 마법사를 구현 했으므로 이제 세 가지 주요 단계를 완료 하 여 **사용자 지정 작업** 항목 템플릿과 연결 해야 합니다.

1. 강력한 이름을 사용 하 여 마법사 어셈블리에 서명 합니다.

2. 마법사 어셈블리에 대 한 공개 키 토큰을 가져옵니다.

3. **사용자 지정 작업** 항목 템플릿에 대 한 .vstemplate 파일에 마법사 어셈블리에 대 한 참조를 추가 합니다.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>강력한 이름을 사용 하 여 마법사 어셈블리에 서명 하려면

1. **솔루션 탐색기**의 **item템플릿 마법사** 프로젝트 노드에서 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **서명** 탭에서 **어셈블리 서명** 확인란을 선택합니다.

3. **강력한 이름 키 파일 선택** 목록에서을 선택 **\<New...>** 합니다.

4. **강력한 이름 키 만들기** 대화 상자에서 이름을 입력 하 고 **암호를 사용 하 여 키 파일 보호** 확인란의 선택을 취소 한 다음 **확인** 단추를 선택 합니다.

5. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>마법사 어셈블리에 대 한 공개 키 토큰을 가져오려면

1. Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 하 여 *PathToWizardAssembly* 를 개발 컴퓨터의 Item템플릿 마법사 프로젝트에 대 한 빌드된 ItemTemplateWizard.dll 어셈블리의 전체 경로로 바꿉니다.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     *ItemTemplateWizard.dll* 어셈블리의 공개 키 토큰은 Visual Studio 명령 프롬프트 창에 기록 됩니다.

2. Visual Studio 명령 프롬프트 창을 열어 둡니다. 다음 절차를 완료 하려면 공개 키 토큰이 필요 합니다.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>.Vstemplate 파일에서 마법사 어셈블리에 대 한 참조를 추가 하려면

1. **솔루션 탐색기**에서 **itemtemplate** 프로젝트 노드를 확장 한 다음 *itemtemplate .vstemplate* 파일을 엽니다.

2. 파일의 끝 부분에서 `WizardExtension` 및 태그 사이에 다음 요소를 추가 `</TemplateContent>` 합니다 `</VSTemplate>` . 특성의 해당 *토큰* 값을 `PublicKeyToken` 이전 절차에서 가져온 공개 키 토큰으로 바꿉니다.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     요소에 대 한 자세한 내용은 `WizardExtension` [WizardExtension Element &#40;Visual Studio Templates&#41;](../extensibility/wizardextension-element-visual-studio-templates.md)를 참조 하세요.

3. 파일을 저장하고 닫습니다.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>항목 템플릿의 *Elements.xml* 파일에 대체 가능 매개 변수 추가
 ItemTemplate 프로젝트의 *Elements.xml* 파일에 여러 대체 가능 매개 변수를 추가 합니다. 이러한 매개 변수는 앞에서 `PopulateReplacementDictionary` 정의한 클래스의 메서드에서 초기화 됩니다 `CustomActionWizard` . 사용자가 프로젝트에 사용자 지정 작업 프로젝트 항목을 추가 하는 경우 Visual Studio는 새 프로젝트 항목의 *Elements.xml* 파일에서 이러한 매개 변수를 마법사에서 지정한 값으로 자동으로 바꿉니다.

 대체 가능 매개 변수는 달러 기호 ($) 문자로 시작 하 고 끝나는 토큰입니다. 대체 가능한 매개 변수를 정의 하는 것 외에도 SharePoint 프로젝트 시스템에서 정의 하 고 초기화 하는 기본 제공 매개 변수를 사용할 수 있습니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조 하세요.

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>*Elements.xml* 파일에 대체 가능 매개 변수를 추가 하려면

1. ItemTemplate 프로젝트에서 *Elements.xml* 파일의 내용을 다음 XML로 바꿉니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="$IdValue$"
                    GroupId="$GroupIdValue$"
                    Location="$LocationValue$"
                    Sequence="1000"
                    Title="$TitleValue$"
                    Description="$DescriptionValue$" >
        <UrlAction Url="$UrlValue$"/>
      </CustomAction>
    </Elements>
    ```

     새 XML은 `Id` ,, `GroupId` `Location` , 및 특성의 값을 `Description` 대체 가능한 `Url` 매개 변수로 변경 합니다.

2. 파일을 저장하고 닫습니다.

## <a name="add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에 마법사 추가
 VSIX 프로젝트의 source.extension.vsixmanifest 파일에서 프로젝트 항목을 포함 하는 VSIX 패키지를 사용 하 여 배포 되도록 마법사 프로젝트에 대 한 참조를 추가 합니다.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>VSIX 패키지에 마법사를 추가 하려면

1. **솔루션 탐색기**CustomActionProjectItem 프로젝트의 **source.extension.vsixmanifest** 파일에서 바로 가기 메뉴를 열고 **열기** 를 선택 하 여 매니페스트 편집기에서 파일을 엽니다.

2. 매니페스트 편집기에서 **자산** 탭을 선택한 다음 **새로 만들기** 단추를 선택 합니다.

     **새 자산 추가** 대화 상자가 나타납니다.

3. **유형** 목록에서 **VisualStudio**를 선택 합니다.

4. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

5. **프로젝트** 목록에서 **item템플릿 마법사**를 선택한 다음 **확인** 단추를 선택 합니다.

6. 메뉴 모음에서 빌드 **Build**  >  **솔루션**빌드를 선택한 다음 솔루션이 오류 없이 컴파일되는지 확인 합니다.

## <a name="test-the-wizard"></a>마법사 테스트
 이제 마법사를 테스트할 준비가 되었습니다. 먼저 Visual Studio의 실험적 인스턴스에서 CustomActionProjectItem 솔루션의 디버깅을 시작 합니다. 그런 다음 Visual Studio의 실험적 인스턴스에서 SharePoint 프로젝트의 사용자 지정 작업 프로젝트 항목에 대해 마법사를 테스트 합니다. 마지막으로 SharePoint 프로젝트를 빌드하고 실행 하 여 사용자 지정 작업이 예상 대로 작동 하는지 확인 합니다.

#### <a name="to-start-to-debug-the-solution"></a>솔루션 디버그를 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작한 다음 CustomActionProjectItem 솔루션을 엽니다.

2. Item템플릿 마법사 프로젝트에서 CustomActionWizard 코드 파일을 연 다음 메서드의 첫 번째 코드 줄에 중단점을 추가 합니다 `RunStarted` .

3. 메뉴 모음에서 **디버그**  >  **예외**를 선택 합니다.

4. **예외** 대화 상자에서 **공용 언어 런타임 예외** 에 대해 **throw** 됨 및 **사용자가 처리 하지 않은** 확인란이 선택 취소 되었는지 확인 하 고 **확인** 단추를 선택 합니다.

5. **F5** 키를 선택 하 여 디버깅을 시작 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Action 프로젝트 Item\1.0에 확장을 설치 하 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에서 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Visual Studio에서 마법사를 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서, 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

2. 항목 템플릿이 지 원하는 언어에 따라 **Visual c #** 또는 **Visual Basic** 노드를 확장 하 고 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **SharePoint 2010 프로젝트**를 선택 하 고 프로젝트 이름을 **CustomActionWizardTest**로 지정한 다음 **확인** 단추를 선택 합니다.

4. **SharePoint 사용자 지정 마법사**에서 디버깅에 사용할 사이트의 URL을 입력 한 후 **마침** 단추를 선택 합니다.

5. **솔루션 탐색기**에서 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 항목**을 선택 합니다.

6. **새 항목 추가-CustomItemWizardTest** 대화 상자에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 확장 합니다.

7. 프로젝트 항목 목록에서 **사용자 지정 작업** 항목을 선택한 다음 **추가** 단추를 선택 합니다.

8. 메서드의 이전에 설정한 중단점에서 Visual Studio의 다른 인스턴스의 코드가 중지 되는지 확인 `RunStarted` 합니다.

9. **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**계속을 선택 하 여 프로젝트를 계속 디버깅  >  **Continue**합니다.

     SharePoint 사용자 지정 마법사가 나타납니다.

10. **위치**에서 **목록 편집** 옵션 단추를 선택 합니다.

11. **그룹 ID** 목록에서 **통신**을 선택 합니다.

12. **제목** 상자에 **SharePoint 개발자 센터**를 입력 합니다.

13. **설명** 상자에 **SharePoint 개발자 센터 웹 사이트를 엽니다**.를 입력 합니다.

14. **URL** 상자에를 입력 한 **https://docs.microsoft.com/sharepoint/dev/** 후 **마침** 단추를 선택 합니다.

     Visual Studio에서 **CustomAction1** 라는 항목이 프로젝트에 추가 되 고 편집기에서 *Elements.xml* 파일이 열립니다. *Elements.xml* 에 마법사에서 지정한 값이 포함 되어 있는지 확인 합니다.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>SharePoint에서 사용자 지정 작업을 테스트 하려면

1. Visual Studio의 실험적 인스턴스에서 **F5** 키를 선택 하거나 메뉴 모음에서 **디버그**  >  **디버깅 시작**을 선택 합니다.

     사용자 지정 작업은 패키지 되 고 프로젝트의 **사이트 URL** 속성에서 지정한 SharePoint 사이트에 배포 되며 웹 브라우저가이 사이트의 기본 페이지로 열립니다.

    > [!NOTE]
    > **스크립트 디버깅 사용 안 함** 대화 상자가 나타나면 **예** 단추를 선택 합니다.

2. SharePoint 사이트의 목록 영역에서 **작업** 링크를 선택 합니다.

     **작업-모든 작업** 페이지가 나타납니다.

3. 리본 메뉴의 **목록 도구** 탭에서 **목록** 탭을 선택 하 고 **설정** 그룹에서 **목록 설정**을 선택 합니다.

     **목록 설정** 페이지가 나타납니다.

4. 페이지 맨 위 근처의 **통신** 제목 아래에서 **SharePoint 개발자 센터** 링크를 선택 하 고 브라우저가 웹 사이트 https://docs.microsoft.com/sharepoint/dev/ 를 열고 브라우저를 닫습니다.

## <a name="cleaning-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목 테스트를 마친 후 Visual Studio의 실험적 인스턴스에서 프로젝트 항목 템플릿을 제거 합니다.

#### <a name="to-clean-up-the-development-computer"></a>개발 컴퓨터를 정리 하려면

1. Visual Studio의 실험적 인스턴스에서 메뉴 모음에서 **도구**  >  **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 **사용자 지정 작업 프로젝트 항목** 확장을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것인지 확인 하 고 **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

4. Visual Studio의 두 인스턴스 (CustomActionProjectItem 솔루션이 열리는 실험적 인스턴스 및 Visual Studio의 인스턴스)를 닫습니다.

## <a name="see-also"></a>추가 정보
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [방법: 프로젝트 템플릿에 마법사 사용](../extensibility/how-to-use-wizards-with-project-templates.md)
- [기본 사용자 지정 작업 위치 및 Id](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
