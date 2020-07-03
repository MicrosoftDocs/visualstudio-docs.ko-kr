---
title: 옵션 페이지 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be826b73e28a73216ea88ceba8e23eb1e9ea457b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903820"
---
# <a name="create-an-options-page"></a>옵션 페이지 만들기

이 연습에서는 속성 표를 사용 하 여 속성을 검사 하 고 설정 하는 간단한 도구/옵션 페이지를 만듭니다.

 이러한 속성을에 저장 하 고 설정 파일에서 복원 하려면 다음 단계를 수행 하 고 [설정 범주 만들기](../extensibility/creating-a-settings-category.md)를 참조 하세요.

 MPF는 도구 옵션 페이지, 클래스 및 클래스를 만드는 데 도움이 되는 두 가지 클래스를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.DialogPage> . 클래스를 서브클래싱 하 여 이러한 페이지에 대 한 컨테이너를 제공 하는 VSPackage를 만듭니다 `Package` . 클래스에서 파생 하 여 각 도구 옵션 페이지를 만듭니다 `DialogPage` .

## <a name="prerequisites"></a>사전 요구 사항

 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-tools-options-grid-page"></a>도구 옵션 그리드 페이지 만들기

 이 섹션에서는 간단한 도구 옵션 속성 표를 만듭니다. 이 표를 사용 하 여 속성의 값을 표시 하 고 변경할 수 있습니다.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX 프로젝트를 만들고 VSPackage를 추가 하려면

1. 모든 Visual Studio 확장은 확장 자산을 포함 하는 VSIX 배포 프로젝트로 시작 합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]이라는 VSIX 프로젝트를 만듭니다 `MyToolsOptionsExtension` . **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 vsix 프로젝트 템플릿을 찾을 수 있습니다.

2. 이라는 Visual Studio 패키지 항목 템플릿을 추가 하 여 VSPackage를 추가 `MyToolsOptionsPackage` 합니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. **새 항목 추가 대화 상자**에서 **visual c # 항목**  >  **확장성** 으로 이동 하 고 **visual Studio 패키지**를 선택 합니다. 대화 상자의 맨 아래에 있는 **이름** 필드에서 파일 이름을으로 변경 합니다 `MyToolsOptionsPackage.cs` . VSPackage를 만드는 방법에 대 한 자세한 내용은 VSPackage를 [사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)를 참조 하세요.

### <a name="to-create-the-tools-options-property-grid"></a>도구 옵션 속성 표를 만들려면

1. 코드 편집기에서 *MyToolsOptionsPackage* 파일을 엽니다.

2. 다음 using 문을 추가 합니다.

   ```csharp
   using System.ComponentModel;
   ```

3. 클래스를 선언 `OptionPageGrid` 하 고에서 파생 <xref:Microsoft.VisualStudio.Shell.DialogPage> 합니다.

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 클래스에를 적용 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `VSPackage` 하 여 옵션 범주에 대 한 옵션 범주 및 옵션 페이지 이름을 지정 합니다. 결과는 다음과 같습니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. `OptionInteger`클래스에 속성을 추가 `OptionPageGrid` 합니다.

    - 속성 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> 표 범주를 속성에 할당 하려면를 적용 합니다.

    - 를 적용 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 하 여 속성에 이름을 지정 합니다.

    - <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName>속성에 설명을 할당 하려면를 적용 합니다.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > 의 기본 구현은 적절 한 <xref:Microsoft.VisualStudio.Shell.DialogPage> 변환기가 있거나 적절 한 변환기가 있는 속성으로 확장 될 수 있는 구조체 또는 배열인 속성을 지원 합니다. 변환기 목록은 네임 스페이스를 참조 하세요 <xref:System.ComponentModel> .

6. 프로젝트를 빌드하고 디버깅을 시작합니다.

7. Visual Studio의 실험적 인스턴스에서 **도구** 메뉴의 **옵션**을 클릭 합니다.

     왼쪽 창에 **내 범주가**표시 됩니다. 옵션 범주는 사전순으로 나열 되므로 목록의 중간에 표시 되어야 합니다. **내 범주** 를 열고 **내 그리드 페이지**를 클릭 합니다. 오른쪽 창에 옵션 표가 표시 됩니다. 속성 범주는 **내 옵션**이며 속성 이름은 **내 정수 옵션**입니다. 속성 설명, **내 정수 옵션**은 창 아래쪽에 표시 됩니다. 값을 초기 값 256에서 다른 값으로 변경 합니다. **확인**을 클릭 한 다음 **내 그리드 페이지**를 다시 엽니다. 새 값이 유지 되는 것을 볼 수 있습니다.

     옵션 페이지는 Visual Studio의 검색 상자를 통해서도 사용할 수 있습니다. IDE 위쪽의 검색 상자에 **내 범주** 를 입력 하면 결과에 나열 된 내 **그리드 > 내 범주가** 표시 됩니다.

## <a name="create-a-tools-options-custom-page"></a>도구 옵션 만들기 사용자 지정 페이지

 이 섹션에서는 사용자 지정 UI를 사용 하 여 도구 옵션 페이지를 만듭니다. 이 페이지를 사용 하 여 속성의 값을 표시 하 고 변경할 수 있습니다.

1. 코드 편집기에서 *MyToolsOptionsPackage* 파일을 엽니다.

2. 다음 using 문을 추가 합니다.

    ```csharp
    using System.Windows.Forms;
    ```

3. 클래스 `OptionPageCustom` 바로 앞에 클래스를 추가 `OptionPageGrid` 합니다. 에서 새 클래스를 파생 시킵니다 `DialogPage` .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. GUID 특성을 추가 합니다. 추가 문자열 속성을 추가 합니다.

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. VSPackage 클래스에 두 번째를 적용 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 합니다. 이 특성은 클래스에 옵션 범주 및 옵션 페이지 이름을 할당 합니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. MyUserControl 라는 새 **사용자 정의 컨트롤** 을 프로젝트에 추가 합니다.

7. **TextBox** 컨트롤을 사용자 정의 컨트롤에 추가 합니다.

     **속성** 창의 도구 모음에서 **이벤트** 단추를 클릭 한 다음 **Leave** 이벤트를 두 번 클릭 합니다. 새 이벤트 처리기가 *MyUserControl.cs* 코드에 나타납니다.

8. `OptionsPage`컨트롤 클래스에 public 필드와 메서드를 추가 하 `Initialize` 고 이벤트 처리기를 업데이트 하 여 옵션 값을 텍스트 상자의 내용으로 설정 합니다.

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     필드에는 `optionsPage` 부모 인스턴스에 대 한 참조가 포함 `OptionPageCustom` 됩니다. `Initialize`메서드는 `OptionString` **텍스트 상자**에를 표시 합니다. 이벤트 처리기는 **TextBox** `OptionString` 포커스가 **Textbox**를 벗어날 때 텍스트 상자의 현재 값을에 씁니다.

9. 패키지 코드 파일에서 속성에 대 한 재정의를 클래스에 추가 하 여 `OptionPageCustom.Window` `OptionPageCustom` 의 인스턴스를 만들고 초기화 하 고 반환 `MyUserControl` 합니다. 이제 클래스는 다음과 같습니다.

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. 프로젝트를 빌드하고 실행합니다.

11. 실험적 인스턴스에서 **도구**  >  **옵션**을 클릭 합니다.

12. **내 범주** 를 찾은 다음 **사용자 지정 페이지**를 찾습니다.

13. 기본값 **문자열**의 값을 변경 합니다. **확인**을 클릭 한 다음 **내 사용자 지정 페이지**를 다시 엽니다. 새 값이 유지 된 것을 볼 수 있습니다.

## <a name="access-options"></a>액세스 옵션

 이 섹션에서는 연결 된 도구 옵션 페이지를 호스트 하는 VSPackage 옵션의 값을 가져옵니다. 동일한 기술을 사용 하 여 공용 속성의 값을 가져올 수 있습니다.

1. 패키지 코드 파일에서 **MyToolsOptionsPackage** 클래스 **에 라는 public 속성을 추가** 합니다.

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     이 코드 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 는를 호출 하 여 인스턴스를 만들거나 검색 `OptionPageGrid` 합니다. `OptionPageGrid`는 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 를 호출 하 여 해당 옵션을 로드 합니다 .이는 공용 속성입니다.

2. 이제 **MyToolsOptionsCommand** 이라는 사용자 지정 명령 항목 템플릿을 추가 하 여 값을 표시 합니다. **새 항목 추가** 대화 상자에서 **Visual c #**  >  **확장성** 으로 이동 하 고 **사용자 지정 명령**을 선택 합니다. 창 맨 아래에 있는 **이름** 필드에서 명령 파일 이름을 *MyToolsOptionsCommand.cs*로 변경 합니다.

3. *MyToolsOptionsCommand* 파일에서 명령의 메서드 본문을 `ShowMessageBox` 다음과 같이 바꿉니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다.

5. 실험적 인스턴스의 **도구** 메뉴에서 **MyToolsOptionsCommand 호출**을 클릭 합니다.

     메시지 상자에의 현재 값이 표시 됩니다 `OptionInteger` .

## <a name="see-also"></a>참조

- [옵션 및 옵션 페이지](../extensibility/internals/options-and-options-pages.md)
