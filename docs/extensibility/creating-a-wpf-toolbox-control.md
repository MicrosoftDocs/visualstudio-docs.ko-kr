---
title: WPF 도구 상자 컨트롤 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: c1400efb0095760bf1cee302dd33dcf6ebb90152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739572"
---
# <a name="create-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤 만들기

WPF(Windows 프레젠테이션 프레임워크) 도구 상자 컨트롤 템플릿을 사용하면 확장이 설치될 때 **도구 상자에** 자동으로 추가되는 WPF 컨트롤을 만들 수 있습니다. 이 연습에서는 템플릿을 사용하여 다른 사용자에게 배포할 수 있는 **도구 상자** 컨트롤을 만드는 방법을 보여 주며 이 연습에서는 템플릿을 사용할 수 있습니다.

Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-the-toolbox-control"></a>도구 상자 컨트롤 만들기

### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>WPF 도구 상자 컨트롤을 사용하여 확장 만들기

1. 라는 VSIX 프로젝트를 `MyToolboxControl`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 프로젝트가 열리면 **WPF 도구 상자 컨트롤** 항목 `MyToolboxControl`템플릿을 추가합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **WPF 도구 상자 컨트롤을**선택합니다. 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *MyToolboxControl.cs.*

    이제 솔루션에는 사용자 컨트롤, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> **도구 상자에**컨트롤을 추가하는 컨트롤 및 배포를 위한 VSIX 매니페스트의 **Microsoft.VisualStudio.ToolboxControl** 자산 항목이 포함되어 있습니다.

#### <a name="to-create-the-control-ui"></a>컨트롤 UI를 만들려면

1. 디자이너에서 *MyToolboxControl.xaml을* 엽니다.

    디자이너에 <xref:System.Windows.Controls.Button> 컨트롤이 포함된 <xref:System.Windows.Controls.Grid> 컨트롤이 표시됩니다.

2. 그리드 레이아웃을 정렬합니다. 컨트롤을 <xref:System.Windows.Controls.Grid> 선택하면 파란색 컨트롤 막대가 그리드의 위쪽 및 왼쪽 가장자리에 나타납니다. 막대를 클릭하여 행과 열을 그리드에 추가할 수 있습니다.

3. 표에 자식 컨트롤을 추가합니다. **도구 상자에서** 그리드의 섹션으로 드래그하거나 XAML에서 해당 `Grid.Row` 컨트롤 및 `Grid.Column` 속성을 설정하여 자식 컨트롤을 배치할 수 있습니다. 다음 예제는 그리드의 맨 위 행에 두 개의 레이블과 두 번째 행의 단추를 추가합니다.

    ```xaml
    <Grid>
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />
    </Grid>
    ```

## <a name="renaming-the-control"></a>컨트롤 이름 바꾸기

 기본적으로 컨트롤은 **MyToolboxControl.MyToolboxControl**이라는 그룹의 **MyToolboxControl으로** **도구** 상자에 나타납니다. *MyToolboxControl.xaml.cs* 파일에서 이러한 이름을 변경할 수 있습니다.

1. 코드 보기에서 *MyToolboxControl.xaml.cs* 엽니다.

2. 클래스를 `MyToolboxControl` 찾아 TestControl로 이름을 바꿉니다. 이 작업을 수행하는 가장 빠른 방법은 클래스의 이름을 변경한 다음 컨텍스트 메뉴에서 **이름 바꾸기를** 선택하고 단계를 완료하는 것입니다. (이름 **바꾸기** 명령에 대한 자세한 내용은 [이름 바꾸기(C#)를](../ide/reference/rename.md)참조하십시오.)

3. 특성으로 `ProvideToolboxControl` 이동하여 첫 번째 매개 변수의 값을 **Test로**변경합니다. 도구 **상자에**컨트롤을 포함 할 그룹의 이름입니다.

    결과 코드는 다음과 같아야 합니다.

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

 프로젝트를 디버깅할 때 Visual Studio의 실험 인스턴스 도구 **상자에** 설치된 컨트롤을 찾아야 합니다.

### <a name="to-build-and-test-the-control"></a>컨트롤을 빌드하고 테스트하려면

1. 프로젝트를 다시 빌드하고 디버깅을 시작합니다.

2. Visual Studio의 새 인스턴스에서 WPF 애플리케이션 프로젝트를 만듭니다. XAML 디자이너가 열려 있는지 확인합니다.

3. **도구 상자** 에서 컨트롤을 찾아 디자인 화면으로 끕니다.

4. WPF 응용 프로그램 디버깅을 시작합니다.

5. 컨트롤이 표시되는지 확인합니다.

### <a name="to-deploy-the-control"></a>컨트롤을 배포하려면

1. 테스트된 프로젝트를 빌드한 후 프로젝트의 *\bin\debug\* 폴더에서 *.vsix* 파일을 찾을 수 있습니다.

2. *.vsix* 파일을 두 번 클릭하고 설치 절차에 따라 로컬 컴퓨터에 설치할 수 있습니다. 컨트롤을 제거하려면 **도구** > **확장 및 업데이트로** 이동하여 컨트롤 확장을 찾은 다음 **제거를**클릭합니다.

3. *.vsix* 파일을 네트워크 또는 웹 사이트에 업로드합니다.

    [파일을 Visual Studio 마켓플레이스](https://marketplace.visualstudio.com/) 웹 사이트에 업로드하는 경우 다른 사용자는 Visual Studio에서 **도구** > 확장 및 업데이트를 사용하여 온라인으로**컨트롤을** 찾아 설치할 수 있습니다.
