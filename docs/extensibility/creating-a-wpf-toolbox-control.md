---
title: WPF 도구 상자 컨트롤 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa6051648e495e21f7954a737f7b572ce6a6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903951"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤 만들기

WPF (Windows Presentation Framework) 도구 상자 컨트롤 템플릿을 사용 하면 확장이 설치 될 때 **도구 상자** 에 자동으로 추가 되는 wpf 컨트롤을 만들 수 있습니다. 이 연습에서는 템플릿을 사용 하 여 다른 사용자에 게 배포할 수 있는 **도구 상자** 컨트롤을 만드는 방법을 보여 줍니다.

Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-the-toolbox-control"></a>도구 상자 컨트롤 만들기

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤을 사용 하 여 확장 만들기

1. 이라는 VSIX 프로젝트를 만듭니다 `MyToolboxControl` . **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 이라는 **WPF 도구 상자 컨트롤** 항목 템플릿을 추가 합니다 `MyToolboxControl` . **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **WPF 도구 상자 컨트롤**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *MyToolboxControl.cs*로 변경 합니다.

    이제 솔루션에는 사용자 정의 컨트롤, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> **도구 상자**에 컨트롤을 추가 하는 VisualStudio 및 배포를 위한 VSIX 매니페스트에 **ToolboxControl** 자산 항목이 포함 되어 있습니다.

#### <a name="to-create-the-control-ui"></a>컨트롤 UI를 만들려면

1. 디자이너에서 *MyToolboxControl* 를 엽니다.

    디자이너에 <xref:System.Windows.Controls.Button> 컨트롤이 포함된 <xref:System.Windows.Controls.Grid> 컨트롤이 표시됩니다.

2. 모눈 레이아웃을 정렬 합니다. 컨트롤을 선택 하면 <xref:System.Windows.Controls.Grid> 표의 위쪽 및 왼쪽 가장자리에 파란색 컨트롤 막대가 표시 됩니다. 막대를 클릭 하 여 표에 행과 열을 추가할 수 있습니다.

3. 모눈에 자식 컨트롤을 추가 합니다. **도구 상자** 에서 모눈의 섹션으로 끌거나 `Grid.Row` XAML에서 및 특성을 설정 하 여 자식 컨트롤을 배치할 수 있습니다 `Grid.Column` . 다음 예에서는 표의 맨 위 행에 두 개의 레이블을 추가 하 고 두 번째 행에 단추를 추가 합니다.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>컨트롤 이름 바꾸기

 기본적으로 컨트롤은 **MyToolboxControl MyToolboxControl**이라는 그룹의 **MyToolboxControl** 로 **도구 상자** 에 표시 됩니다. 이러한 이름은 *MyToolboxControl.xaml.cs* 파일에서 변경할 수 있습니다.

1. 코드 보기에서 *MyToolboxControl.xaml.cs* 을 엽니다.

2. 클래스를 찾아 `MyToolboxControl` TestControl로 이름을 바꿉니다. 이 작업을 수행 하는 가장 빠른 방법은 클래스 이름을 바꾼 다음 상황에 맞는 메뉴에서 **이름 바꾸기** 를 선택 하 고 단계를 완료 하는 것입니다. **이름 바꾸기** 명령에 대 한 자세한 내용은 [이름 바꾸기 리팩터링 (c #)](../ide/reference/rename.md)을 참조 하세요.

3. 특성으로 이동 하 여 `ProvideToolboxControl` **테스트**를 위해 첫 번째 매개 변수의 값을 변경 합니다. **도구 상자**에 컨트롤을 포함 하는 그룹의 이름입니다.

    결과 코드는 다음과 같습니다.

    ```csharp
    [ProvideToolboxControl("Test", true)]
    public partial class TestControl : UserControl
    {
        public TestControl()
        {
            InitializeComponent();
        }
    }
    ```

## <a name="build-test-and-deployment"></a>빌드, 테스트 및 배포

 프로젝트를 디버그할 때 Visual Studio 실험적 인스턴스의 **도구 상자** 에 설치 된 컨트롤을 찾아야 합니다.

### <a name="to-build-and-test-the-control"></a>컨트롤을 빌드하고 테스트하려면

1. 프로젝트를 다시 빌드하고 디버깅을 시작 합니다.

2. Visual Studio의 새 인스턴스에서 WPF 애플리케이션 프로젝트를 만듭니다. XAML 디자이너 열려 있는지 확인 합니다.

3. **도구 상자** 에서 컨트롤을 찾아 디자인 화면으로 끕니다.

4. WPF 응용 프로그램 디버깅을 시작 합니다.

5. 컨트롤이 표시 되는지 확인 합니다.

### <a name="to-deploy-the-control"></a>컨트롤을 배포하려면

1. 테스트 된 프로젝트를 빌드한 후 프로젝트의 * \bin\debug 폴더에서 *.vsix* 파일을 찾을 수 있습니다. \*

2. *.Vsix* 파일을 두 번 클릭 하 고 설치 절차를 수행 하 여 로컬 컴퓨터에 설치할 수 있습니다. 컨트롤을 제거 하려면 **도구**  >  **확장 및 업데이트** 로 이동 하 여 컨트롤 확장을 찾은 다음 **제거**를 클릭 합니다.

3. 네트워크 또는 웹 사이트에 *.vsix* 파일을 업로드 합니다.

    [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트에 파일을 업로드 하는 경우 다른 사용자가 **Tools**  >  Visual Studio에서 도구**확장 및 업데이트** 를 사용 하 여 온라인으로 컨트롤을 찾아 설치할 수 있습니다.
