---
title: '방법: 프로젝트 템플릿에 마법사 사용'
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9d36ae9b3a4a4fbbb3c54cc3f3320e9878b6745
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905519"
---
# <a name="how-to-use-wizards-with-project-templates"></a>방법: 프로젝트 템플릿에 마법사 사용

Visual Studio에서는 사용자가 템플릿을 사용하여 프로젝트를 만들 때 사용자 지정 코드를 실행할 수 있도록 설정하여 구현 시 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스를 제공합니다.

프로젝트 템플릿 사용자 지정을 사용 하 여 사용자 입력을 수집 하는 사용자 지정 UI를 표시 하 여 템플릿을 사용자 지정 하거나 템플릿에 추가 파일을 추가 하거나 프로젝트에 허용 되는 기타 작업을 수행할 수 있습니다.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>인터페이스 메서드는 프로젝트가 생성 되는 동안 사용자가 **새 프로젝트** 대화 상자에서 **확인** 을 클릭 하는 즉시 시작 하 여 다양 한 시간에 호출 됩니다. 인터페이스의 각 메서드에는이 메서드가 호출 된 지점을 설명 하기 위해 이름이 지정 됩니다. 예를 들어 Visual Studio는 프로젝트를 만들기 시작 하는 즉시를 호출 하 여 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 사용자 입력을 수집 하는 사용자 지정 코드를 작성 하는 것이 좋은 위치입니다.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>VSIX 프로젝트를 사용 하 여 프로젝트 템플릿 프로젝트 만들기

Visual Studio SDK의 일부인 프로젝트 템플릿 프로젝트를 사용 하 여 사용자 지정 템플릿 만들기를 시작 합니다. 이 절차에서는 c # 프로젝트 템플릿 프로젝트를 사용 하지만 Visual Basic 프로젝트 템플릿 프로젝트도 있습니다. 그런 다음 프로젝트 템플릿 프로젝트를 포함 하는 솔루션에 VSIX 프로젝트를 추가 합니다.

1. C # 프로젝트 템플릿 프로젝트를 만듭니다 (Visual Studio에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 고 "프로젝트 템플릿" 검색). 이름을 **Myprojecttemplate**으로 합니다.

   > [!NOTE]
   > Visual Studio SDK를 설치 하 라는 메시지가 표시 될 수 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

2. 프로젝트 템플릿 프로젝트와 동일한 솔루션에 새 VSIX 프로젝트를 추가 합니다. **솔루션 탐색기**에서 솔루션 노드를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **Add**  >  **새 프로젝트** 추가를 선택 하 고 "VSIX"를 검색 합니다. 이름을 **Myprojectwizard로 만듭니다.**

3. VSIX 프로젝트를 시작 프로젝트로 설정 합니다. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **시작 프로젝트로 설정**을 선택 합니다.

4. VSIX 프로젝트의 자산으로 템플릿 프로젝트를 추가 합니다. **솔루션 탐색기**의 VSIX 프로젝트 노드 아래에서 *source.extension.vsixmanifest* 파일을 찾습니다. 매니페스트 편집기에서 열려면 두 번 클릭 합니다.

5. 매니페스트 편집기에서 창의 왼쪽에 있는 **자산** 탭을 선택 합니다.

6. **자산** 탭에서 **새로 만들기**를 선택 합니다. **새 자산 추가** 창의 형식 필드에서 **VisualStudio**를 선택 합니다. **원본** 필드에서 **현재 솔루션의 프로젝트**를 선택 합니다. **프로젝트** 필드에서 **myprojecttemplate**을 선택 합니다. 그런 후 **OK**를 클릭합니다.

7. 솔루션을 빌드하고 디버깅을 시작합니다. 두 번째 Visual Studio 인스턴스가 표시됩니다. (몇 분이 걸릴 수 있습니다.)

8. Visual Studio의 두 번째 인스턴스에서 새 템플릿을 사용 하 여 새 프로젝트를 만듭니다 (**파일**  >  **새로**만들기  >  **프로젝트**, "myproject" 검색). 새 프로젝트가 **Class1**이라는 클래스와 함께 표시 되어야 합니다. 이제 사용자 지정 프로젝트 템플릿을 만들었습니다. 지금 디버깅을 중지 합니다.

## <a name="create-a-custom-template-wizard"></a>사용자 지정 템플릿 만들기 마법사

이 절차에서는 프로젝트가 만들어지기 전에 Windows Form을 여는 사용자 지정 마법사를 만드는 방법을 보여 줍니다. 사용자는 폼을 사용 하 여 프로젝트를 만드는 동안 소스 코드에 추가 되는 사용자 지정 매개 변수 값을 추가할 수 있습니다.

1. VSIX 프로젝트를 설정 하 여 어셈블리를 만들 수 있도록 합니다.

2. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 선택 합니다. **솔루션 탐색기**아래에 **속성** 창이 표시 됩니다. 그렇지 않으면 **View**  >  **속성 창**보기를 선택 하거나 **F4**키를 누릅니다. **속성** 창에서 다음 필드를 선택 합니다 `true` .

   - **VSIX 컨테이너에 어셈블리 포함**

   - **VSIX 컨테이너에 디버그 기호 포함**

   - **로컬 VSIX 배포에 디버그 기호 포함**

3. VSIX 프로젝트에 어셈블리를 에셋으로 추가 합니다. *Source.extension.vsixmanifest* 파일을 열고 **자산** 탭을 선택 합니다. **새 자산 추가** 창에서 **VisualStudio**를 선택 하 고, **원본** 에 대해 **현재 솔루션에서 프로젝트**를 선택 하 고, **프로젝트** 에 대해 **myprojectwizard** **를 선택 합니다** .

4. VSIX 프로젝트에 다음 참조를 추가 합니다. **솔루션 탐색기**의 VSIX 프로젝트 노드에서 **참조**를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **참조 추가**를 선택 합니다. **참조 추가** 대화 상자의 **프레임 워크** 탭에서 **Windows Forms** 어셈블리를 찾아 선택 합니다. 또한 **시스템** 및 **시스템 그리기** 어셈블리를 찾아 선택 합니다. 이제 **확장** 탭을 선택 합니다. **EnvDTE** 어셈블리를 찾아 선택 합니다. **VisualStudio Wizardwizardinterface** 어셈블리도 찾아 선택 합니다. **확인**을 클릭합니다.

5. 마법사 구현에 대 한 클래스를 VSIX 프로젝트에 추가 합니다. **솔루션 탐색기**에서 VSIX 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **새 항목**, **클래스**를 차례로 선택 합니다. 클래스 이름을 **WizardImplementation**로 합니다.

6. *WizardImplementationClass.cs* 파일의 코드를 다음 코드로 바꿉니다.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    이 코드에서 참조 된 **Userinputform** 은 나중에 구현 됩니다.

    클래스에는 `WizardImplementation` 의 모든 멤버에 대 한 메서드 구현이 포함 되어 있습니다 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . 이 예제에서는 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 메서드만 작업을 수행 합니다. 다른 모든 메서드는 아무 작업도 수행 하지 않거나 `true` 를 반환 합니다.

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>메서드는 네 개의 매개 변수를 허용 합니다.

   - <xref:System.Object>프로젝트를 사용자 지정할 수 있도록 루트 개체로 캐스팅할 수 있는 매개 변수입니다 <xref:EnvDTE._DTE> .

   - <xref:System.Collections.Generic.Dictionary%602>템플릿에 있는 모든 미리 정의 된 매개 변수의 컬렉션을 포함 하는 매개 변수입니다. 템플릿 매개 변수에 대 한 자세한 내용은 [템플릿 매개 변수](../ide/template-parameters.md)를 참조 하세요.

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>사용 되는 템플릿 종류에 대 한 정보를 포함 하는 매개 변수입니다.

   - <xref:System.Object>Visual Studio에서 마법사에 전달 된 매개 변수 집합을 포함 하는 배열입니다.

     이 예에서는 사용자 입력 폼의 매개 변수 값을 <xref:System.Collections.Generic.Dictionary%602> 매개 변수에 추가 합니다. `$custommessage$`프로젝트의 모든 매개 변수 인스턴스는 사용자가 입력 한 텍스트로 바뀝니다.

7. 이제 **Userinputform**을 만듭니다. *WizardImplementation.cs* 파일에서 클래스의 끝 뒤에 다음 코드를 추가 `WizardImplementation` 합니다.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    사용자 입력 폼은 사용자 지정 매개 변수를 입력 하기 위한 간단한 양식을 제공 합니다. 양식에는 이라는 텍스트 상자 `textBox1` 와 이라는 단추가 포함 `button1` 됩니다. 단추를 클릭 하면 텍스트 상자의 텍스트가 `customMessage` 매개 변수에 저장 됩니다.

## <a name="connect-the-wizard-to-the-custom-template"></a>마법사를 사용자 지정 템플릿에 연결

사용자 지정 프로젝트 템플릿이 사용자 지정 마법사를 사용 하도록 하려면 마법사 어셈블리에 서명 하 고 새 프로젝트를 만들 때 마법사 구현을 찾을 위치를 알 수 있도록 사용자 지정 프로젝트 템플릿에 일부 줄을 추가 해야 합니다.

1. 어셈블리에 서명 합니다. **솔루션 탐색기**에서 VSIX 프로젝트를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **프로젝트 속성**을 선택 합니다.

2. **프로젝트 속성** 창에서 **서명** 탭을 선택 합니다. **서명** 탭에서 **어셈블리 서명**을 선택 합니다. **강력한 이름 키 파일 선택** 필드에서을 선택 **\<New>** 합니다. **강력한 이름 키 만들기** 창에서 **키 파일 이름** 필드에 **key.snk**를 입력 합니다. 암호 필드를 **사용 하 여 내 키 파일 보호** 를 선택 취소 합니다.

3. **솔루션 탐색기**에서 VSIX 프로젝트를 선택 하 고 **속성** 창을 찾습니다.

4. **빌드 출력을 출력 디렉터리로 복사** 필드를 **true**로 설정 합니다. 이렇게 하면 솔루션을 다시 빌드할 때 출력 디렉터리에 어셈블리를 복사할 수 있습니다. 이 파일은 여전히 파일에 포함 되어 `.vsix` 있습니다. 서명 키를 찾으려면 어셈블리를 확인 해야 합니다.

5. 솔루션을 다시 빌드합니다.

6. 이제 MyProjectWizard 프로젝트 디렉터리 (* \<your disk location> \MyProjectTemplate\MyProjectWizard\key.snk*)에서 키 .snk 파일을 찾을 수 있습니다. *키 .snk* 파일을 복사 합니다.

7. 출력 디렉터리로 이동 하 여 어셈블리를 찾습니다 (* \<your disk location> \ myprojecttemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). *키 .snk* 파일을 여기에 붙여 넣습니다. 이는 반드시 필요한 것은 아니지만 다음 단계를 더 쉽게 수행할 수 있습니다.

8. 명령 창을 열고 어셈블리가 생성 된 디렉터리로 변경 합니다.

9. *sn.exe* 서명 도구를 찾습니다. 예를 들어 Windows 10 64 비트 운영 체제에서 일반적인 경로는 다음과 같습니다.

     *C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     도구를 찾을 수 없는 경우 명령 창에서 **sn.exe** 에서 실행을 시도 합니다. 경로를 적어 둡니다.

10. *키 .snk* 파일에서 공개 키를 추출 합니다. 명령 창에서 다음을 입력 합니다.

     **\<location of sn.exe>\sn.exe-p 키입니다.**

     디렉터리 이름에 공백이 있는 경우 *sn.exe* 경로를 따옴표로 묶어야 합니다.

11. 출력 키에서 공개 키 토큰을 가져옵니다.

     **\<location of sn.exe>\sn.exe-t 출력 키입니다.**

     다시 한 번 따옴표를 잊지 마세요. 출력에 다음과 같은 줄이 표시 됩니다.

     **공개 키 토큰\<token>**

     이 값을 적어 두세요.

12. 사용자 지정 마법사에 대 한 참조를 프로젝트 템플릿의 *.vstemplate* 파일에 추가 합니다. **솔루션 탐색기**에서 이름이 *myprojecttemplate. .vstemplate*인 파일을 찾아 엽니다. 섹션의 끝에 \<TemplateContent> 다음 섹션을 추가 합니다.

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     여기서 **Myprojectwizard** 는 어셈블리의 이름이 고, **token** 은 이전 단계에서 복사한 토큰입니다.

13. 프로젝트에 모든 파일을 저장 하 고 다시 빌드합니다.

## <a name="add-the-custom-parameter-to-the-template"></a>템플릿에 사용자 지정 매개 변수 추가

이 예제에서 템플릿으로 사용 되는 프로젝트는 사용자 지정 마법사의 사용자 입력 형식에 지정 된 메시지를 표시 합니다.

1. **솔루션 탐색기**에서 **myprojecttemplate** 프로젝트로 이동 하 여 *Class1.cs*를 엽니다.

2. `Main`응용 프로그램의 메서드에서 다음 코드 줄을 추가 합니다.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    `$custommessage$`템플릿에서 프로젝트를 만들 때 매개 변수가 사용자 입력 폼에 입력 된 텍스트로 바뀝니다.

다음은 템플릿으로 내보내기 전의 전체 코드 파일입니다.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>사용자 지정 마법사 사용

이제 템플릿에서 프로젝트를 만들고 사용자 지정 마법사를 사용할 수 있습니다.

1. 솔루션을 다시 빌드하고 디버깅을 시작 합니다. Visual Studio의 두 번째 인스턴스가 나타납니다.

2. 새 MyProjectTemplate 프로젝트를 만듭니다. (**파일**  >  **새**  >  **프로젝트**).

3. **새 프로젝트** 대화 상자에서 "myproject"를 검색 하 여 템플릿을 찾고 이름을 입력 한 다음 **확인**을 클릭 합니다.

     마법사 사용자 입력 양식이 열립니다.

4. 사용자 지정 매개 변수의 값을 입력 하 고 단추를 클릭 합니다.

     마법사 사용자 입력 폼이 닫히고 템플릿에서 프로젝트가 생성 됩니다.

5. **솔루션 탐색기**에서 소스 코드 파일을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 클릭 합니다.

     는 `$custommessage$` 마법사 사용자 입력 폼에 입력 한 텍스트로 대체 되었습니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)
- [WizardExtension 요소 (Visual Studio 템플릿)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Visual Studio 템플릿의 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)
