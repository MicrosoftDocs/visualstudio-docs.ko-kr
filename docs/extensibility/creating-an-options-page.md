---
title: 옵션 페이지 만들기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739521"
---
# <a name="create-an-options-page"></a>옵션 페이지 만들기

이 연습에서는 속성 표를 사용하여 속성을 검사하고 설정하는 간단한 도구/옵션 페이지를 만듭니다.

 이러한 속성을 설정 파일에 저장하고 복원하려면 다음 단계를 수행한 다음 [설정 범주 만들기를](../extensibility/creating-a-settings-category.md)참조하십시오.

 MPF는 도구 옵션 페이지, 클래스 및 <xref:Microsoft.VisualStudio.Shell.Package> 클래스를 <xref:Microsoft.VisualStudio.Shell.DialogPage> 만드는 데 도움이 되는 두 가지 클래스를 제공합니다. 클래스를 하위 분류하여 이러한 페이지에 대한 컨테이너를 `Package` 제공하는 VSPackage를 만듭니다. `DialogPage` 클래스에서 파생하여 각 도구 옵션 페이지를 만듭니다.

## <a name="prerequisites"></a>사전 요구 사항

 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-tools-options-grid-page"></a>도구 옵션 그리드 만들기 페이지 만들기

 이 섹션에서는 간단한 도구 옵션 속성 표를 작성합니다. 이 그리드를 사용하여 속성 값을 표시하고 변경합니다.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX 프로젝트를 만들고 VSPackage를 추가하려면

1. 모든 Visual Studio 확장은 확장 에셋을 포함하는 VSIX 배포 프로젝트로 시작합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트를 `MyToolsOptionsExtension`만듭니다. 새 프로젝트 대화 상자에서 "vsix"를 검색하여 VSIX **프로젝트** 템플릿을 찾을 수 있습니다.

2. 라는 Visual Studio 패키지 항목 템플릿을 `MyToolsOptionsPackage`추가 하 여 VSPackage 를 추가 합니다. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 새 **항목 추가 대화 상자에서** **Visual C# 항목** > **확장성으로** 이동하여 Visual Studio **패키지를**선택합니다. 대화 상자 아래쪽에 있는 **이름** 필드에서 파일 이름을 `MyToolsOptionsPackage.cs`로 변경합니다. VSPackage를 만드는 방법에 대한 자세한 내용은 [VSPackage를 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-vspackage.md)참조하십시오.

### <a name="to-create-the-tools-options-property-grid"></a>도구 옵션 속성 그리드를 작성하려면

1. 코드 편집기에서 *MyToolsOptions패키지* 파일을 엽니다.

2. 문을 사용하여 다음을 추가합니다.

   ```csharp
   using System.ComponentModel;
   ```

3. 클래스를 `OptionPageGrid` 선언하고 <xref:Microsoft.VisualStudio.Shell.DialogPage>에서 파생합니다.

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 클래스에 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `VSPackage` a를 적용하여 OptionPageGrid에 대한 옵션 범주 및 옵션 페이지 이름을 클래스에 할당합니다. 결과는 다음과 같아야 합니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. 클래스에 `OptionInteger` 속성을 `OptionPageGrid` 추가합니다.

    - 속성에 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> 속성 그리드 범주를 할당할 을 적용합니다.

    - 속성에 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 이름을 할당할 을 적용합니다.

    - 속성에 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> 설명을 할당할 을 적용합니다.

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
    > 적절한 변환기가 <xref:Microsoft.VisualStudio.Shell.DialogPage> 있거나 적절한 변환기가 있는 속성으로 확장할 수 있는 구조 또는 배열인 속성의 기본 구현입니다. 변환기 목록은 네임스페이스를 <xref:System.ComponentModel> 참조하십시오.

6. 프로젝트를 빌드하고 디버깅을 시작합니다.

7. Visual Studio의 실험 인스턴스에서 **도구** 메뉴에서 **옵션을**클릭합니다.

     왼쪽 창에 **내 범주가**표시됩니다. 옵션 범주는 사전순으로 나열되므로 목록의 절반 정도 아래에 표시되어야 합니다. **내 범주를** 연 다음 **내 그리드 페이지를 클릭합니다.** 옵션 표가 오른쪽 창에 나타납니다. 속성 범주는 **내 옵션이고**속성 이름은 **내 정수 옵션입니다.** 속성 설명인 **내 정수 옵션이**창 아래쪽에 나타납니다. 값을 초기 값 256에서 다른 값으로 변경합니다. **확인을**클릭한 다음 내 그리드 페이지를 다시 **엽니다.** 새 값이 지속되는 것을 볼 수 있습니다.

     옵션 페이지는 Visual Studio의 검색 상자를 통해서도 사용할 수 있습니다. IDE 상단의 검색 상자에 **내 범주를** 입력하면 내 **범주 -> 내 그리드 페이지가** 결과에 나열됩니다.

## <a name="create-a-tools-options-custom-page"></a>도구 옵션 사용자 지정 페이지 만들기

 이 섹션에서는 사용자 지정 UI가 있는 도구 옵션 페이지를 만듭니다. 이 페이지를 사용하여 속성 값을 표시하고 변경합니다.

1. 코드 편집기에서 *MyToolsOptions패키지* 파일을 엽니다.

2. 문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Windows.Forms;
    ```

3. `OptionPageCustom` 클래스 바로 앞에 클래스를 추가합니다. `OptionPageGrid` 에서 `DialogPage`새 클래스를 파생합니다.

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

4. GUID 특성을 추가합니다. OptionString 속성 추가:

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

5. VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 클래스에 두 번째를 적용합니다. 이 특성은 클래스에 옵션 범주 및 옵션 페이지 이름을 할당합니다.

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

6. MyUserControl이라는 새 **사용자 컨트롤을** 프로젝트에 추가합니다.

7. 사용자 컨트롤에 TextBox 컨트롤을 **추가합니다.**

     **속성** 창에서 도구 모음에서 **이벤트** 단추를 클릭한 다음 **Leave** 이벤트를 두 번 클릭합니다. 새 이벤트 처리기가 *MyUserControl.cs* 코드에 나타납니다.

8. 공용 `OptionsPage` 필드, 메서드를 `Initialize` 컨트롤 클래스에 추가하고 이벤트 처리기를 업데이트하여 옵션 값을 텍스트 상자의 내용으로 설정합니다.

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

     `optionsPage` 필드에는 상위 `OptionPageCustom` 인스턴스에 대한 참조가 있습니다. 메서드는 `Initialize` `OptionString` **TextBox**에 표시됩니다. 이벤트 처리기는 **TextBox의** 현재 값을 `OptionString` 포커스가 **TextBox를**떠날 때에 씁니다.

9. 패키지 코드 파일에서 `OptionPageCustom.Window` 속성에 대한 재정의를 `OptionPageCustom` 클래스에 추가하여 `MyUserControl`의 인스턴스를 만들고 초기화하고 반환합니다. 이제 클래스는 다음과 같아야 합니다.

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

11. 실험 인스턴스에서 **도구** > **옵션을 클릭합니다.**

12. **내 범주를** 찾은 다음 **내 사용자 지정 페이지를**찾습니다.

13. 옵션 문자열의 값을 **변경합니다.** **확인을**클릭한 다음 내 사용자 지정 페이지를 다시 **엽니다.** 새 값이 유지되었음을 확인할 수 있습니다.

## <a name="access-options"></a>액세스 옵션

 이 섹션에서는 연결된 도구 옵션 페이지를 호스팅하는 VSPackage에서 옵션 값을 가져옵니다. 동일한 기술을 사용하여 모든 공용 속성의 값을 얻을 수 있습니다.

1. 패키지 코드 파일에서 **OptionInteger라는** 공용 속성을 **MyToolsOptionsPackage** 클래스에 추가합니다.

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

     이 코드는 인스턴스를 `OptionPageGrid` 만들거나 검색하기 위해 호출됩니다. <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> `OptionPageGrid`을 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 호출하여 공용 속성인 옵션을 로드합니다.

2. 이제 **MyToolsOptionsCommand라는** 사용자 지정 명령 항목 템플릿을 추가하여 값을 표시합니다. 새 **항목 추가** 대화 상자에서 **시각적 C#** > **확장성으로** 이동하여 **사용자 지정 명령을 선택합니다.** 창 아래쪽의 **이름** 필드에서 명령 파일 이름을 *MyToolsOptionsCommand.cs.*

3. *MyToolsOptionsCommand* 파일에서 명령 `ShowMessageBox` 메서드의 본문을 다음과 같은 값으로 바꿉꿉입니다.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다.

5. 실험인스턴스에서 **도구** 메뉴에서 **MyToolsOptionsCommand 호출을**클릭합니다.

     메시지 상자에의 현재 값이 `OptionInteger`표시됩니다.

## <a name="see-also"></a>참조

- [옵션 및 옵션 페이지](../extensibility/internals/options-and-options-pages.md)
