---
title: '방법: 프로젝트 템플릿에 마법사 사용'
ms.date: 3/16/2019
ms.topic: conceptual
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
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710540"
---
# <a name="how-to-use-wizards-with-project-templates"></a>방법: 프로젝트 템플릿을 사용하여 마법사 사용

Visual Studio에서는 사용자가 템플릿을 사용하여 프로젝트를 만들 때 사용자 지정 코드를 실행할 수 있도록 설정하여 구현 시 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스를 제공합니다.

프로젝트 템플릿 사용자 지정을 사용하여 사용자 입력을 수집하는 사용자 UI를 표시하여 템플릿을 사용자 지정하거나, 템플릿에 파일을 추가하거나, 프로젝트에서 허용되는 다른 작업을 표시할 수 있습니다.

사용자가 **새 프로젝트** 대화 상자에서 **확인을** 클릭하는 즉시 시작하여 프로젝트를 만들 때 인터페이스 메서드가 여러 번 호출됩니다. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 인터페이스의 각 메서드는 호출되는 지점을 설명하기 위해 명명됩니다. 예를 들어 Visual <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> Studio는 프로젝트를 만들기 시작할 때 즉시 호출되므로 사용자 입력을 수집하는 사용자 지정 코드를 작성하는 것이 좋습니다.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>VSIX 프로젝트를 사용하여 프로젝트 템플릿 프로젝트 만들기

Visual Studio SDK의 일부인 프로젝트 템플릿 프로젝트를 통해 사용자 지정 템플릿을 만들기 시작합니다. 이 절차에서는 C# 프로젝트 템플릿 프로젝트를 사용하지만 Visual Basic 프로젝트 템플릿 프로젝트도 있습니다. 그런 다음 프로젝트 템플릿 프로젝트를 포함하는 솔루션에 VSIX 프로젝트를 추가합니다.

1. C# 프로젝트 템플릿 프로젝트를 만듭니다(Visual Studio에서**새** > **프로젝트** **파일** > 선택 및 "프로젝트 템플릿"을 검색). 이름을 **내 프로젝트 템플릿**.

   > [!NOTE]
   > Visual Studio SDK를 설치하라는 메시지가 나타날 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

2. 프로젝트 템플릿 프로젝트와 동일한 솔루션에 새 VSIX 프로젝트를 추가합니다(솔루션 **탐색기에서**솔루션 노드를 선택하고 마우스 오른쪽 단추로 클릭하고**새 프로젝트** **추가를** > 선택하고 "vsix"를 검색). 이름을 **내 프로젝트 마법사로 지정합니다.**

3. VSIX 프로젝트를 시작 프로젝트로 설정합니다. **솔루션 탐색기에서**VSIX 프로젝트 노드를 선택하고 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정을**선택합니다.

4. 템플릿 프로젝트를 VSIX 프로젝트의 자산으로 추가합니다. **솔루션 탐색기에서**VSIX 프로젝트 노드 아래에서 *source.extension.vsixmanifest* 파일을 찾습니다. 매니페스트 편집기에서 열려면 두 번 클릭합니다.

5. 매니페스트 편집기에서 창 왼쪽에 있는 **자산** 탭을 선택합니다.

6. **자산** 탭에서 **새**을 선택합니다. 새 **자산 추가** 창에서 입력 필드에 대해 **Microsoft.VisualStudio.ProjectTemplate**를 선택합니다. **소스** 필드에서 현재 **솔루션의 A 프로젝트를 선택합니다.** **프로젝트** 필드에서 **MyProjectTemplate를**선택합니다. 그런 다음 **확인**을 클릭합니다.

7. 솔루션을 빌드하고 디버깅을 시작합니다. 두 번째 Visual Studio 인스턴스가 표시됩니다. (몇 분이 걸릴 수 있습니다.)

8. Visual Studio의 두 번째 인스턴스에서는 새 > **템플릿(파일** > 새**File****프로젝트**, "myproject"를 검색)으로 새 프로젝트를 만들어 보십시오. 새 프로젝트는 **Class1이라는**클래스와 함께 표시되어야 합니다. 이제 사용자 지정 프로젝트 템플릿을 만들었습니다! 지금 디버깅을 중지합니다.

## <a name="create-a-custom-template-wizard"></a>사용자 지정 템플릿 마법사 만들기

이 절차에서는 프로젝트를 만들기 전에 Windows Form을 여는 사용자 지정 마법사를 만드는 방법을 보여 줍니다. 이 양식을 사용하면 프로젝트를 만드는 동안 소스 코드에 추가되는 사용자 지정 매개 변수 값을 추가할 수 있습니다.

1. 어셈블리를 만들 수 있도록 VSIX 프로젝트를 설정합니다.

2. **솔루션 탐색기에서**VSIX 프로젝트 노드를 선택합니다. **솔루션 탐색기**아래에 **속성** 창이 표시됩니다. 그렇지 않으면 속성 **보기** > **창을**선택하거나 **F4**를 누릅니다. **속성** 창에서 다음 필드를 다음으로 `true`선택합니다.

   - **VSIX 컨테이너에 어셈블리 포함**

   - **VSIX 컨테이너에 디버그 기호 포함**

   - **로컬 VSIX 배포에 디버그 기호 포함**

3. 어셈블리를 VSIX 프로젝트에 자산으로 추가합니다. *source.extension.vsixmanifest* 파일을 열고 **자산** 탭을 선택합니다. 새 **자산 추가** 창에서 **유형에** 대해 **Microsoft.VisualStudio.Assembly를**선택하고 **소스에** 대해 **현재 솔루션에서 A 프로젝트를**선택하고 **프로젝트** 에 대해 **MyProjectWizard를**선택합니다.

4. VSIX 프로젝트에 다음 참조를 추가합니다. (솔루션 **탐색기에서**VSIX 프로젝트 노드에서 **참조,** 오른쪽 단추 클릭을 선택하고 **참조 추가를**선택합니다.) 참조 **추가** 대화 상자에서 **프레임워크** 탭에서 **System.Windows 양식** 어셈블리를 찾아 선택합니다. 또한 **시스템** 및 **System.Drawing** 어셈블리를 찾아 선택합니다. 이제 **확장 탭을 선택합니다.** **EnvDTE** 또한 **Microsoft.VisualStudio.TemplateWizardInterface** 어셈블리를 찾아 서 선택 합니다. **확인**을 클릭합니다.

5. VSIX 프로젝트에 마법사 구현에 대한 클래스를 추가합니다. (솔루션 **탐색기에서**VSIX 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가를**선택한 다음 **새 항목**, **클래스**를 선택합니다.) 클래스 의 이름을 **마법사 구현**.

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

    이 코드에서 참조되는 **UserInputForm은** 나중에 구현됩니다.

    클래스에는 `WizardImplementation` 의 모든 멤버에 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>대한 메서드 구현이 포함되어 있습니다. 이 예제에서는 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 메서드만 작업을 수행합니다. 다른 모든 메서드는 아무 `true`것도 수행하지 않거나 반환합니다.

    메서드는 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 다음 네 가지 매개 변수를 허용합니다.

   - 프로젝트를 <xref:System.Object> 사용자 지정할 수 <xref:EnvDTE._DTE> 있도록 루트 개체에 캐스팅할 수 있는 매개 변수입니다.

   - <xref:System.Collections.Generic.Dictionary%602> 템플릿에 미리 정의된 모든 매개 변수의 컬렉션을 포함하는 매개 변수입니다. 템플릿 매개 변수에 대한 자세한 내용은 [템플릿 매개 변수 를](../ide/template-parameters.md)참조하십시오.

   - 사용 <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> 중인 템플릿의 종류에 대한 정보가 포함된 매개 변수입니다.

   - Visual <xref:System.Object> Studio에서 마법사에 전달된 매개 변수 집합을 포함하는 배열입니다.

     이 예제는 사용자 입력 양식의 매개 <xref:System.Collections.Generic.Dictionary%602> 변수 값을 매개 변수에 추가합니다. 프로젝트의 `$custommessage$` 모든 매개 변수 인스턴스는 사용자가 입력한 텍스트로 바뀝습니다.

7. 이제 **사용자 입력 양식을**만듭니다. *WizardImplementation.cs* 파일에서 클래스가 끝난 후 다음 `WizardImplementation` 코드를 추가합니다.

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

    사용자 입력 양식은 사용자 지정 매개 변수를 입력하기 위한 간단한 양식을 제공합니다. 양식에는 라는 `textBox1` 텍스트 상자와 .라는 `button1`단추가 포함되어 있습니다. 단추를 클릭하면 텍스트 상자의 텍스트가 매개 변수에 `customMessage` 저장됩니다.

## <a name="connect-the-wizard-to-the-custom-template"></a>마법사를 사용자 지정 템플릿에 연결

사용자 지정 프로젝트 템플릿에서 사용자 지정 마법사를 사용하려면 마법사 어셈블리에 서명하고 사용자 지정 프로젝트 템플릿에 일부 줄을 추가하여 새 프로젝트를 만들 때 마법사 구현을 찾을 위치를 알려야 합니다.

1. 어셈블리에 서명 합니다. 솔루션 **탐색기에서**VSIX 프로젝트를 선택하고 마우스 오른쪽 단추로 클릭하고 **프로젝트 속성을**선택합니다.

2. 프로젝트 **속성** 창에서 **서명** **탭을** 선택합니다. **Sign the assembly** 강력한 **이름 키 파일** 선택 파일 필드에서 ** \<새>** 선택합니다. 강력한 **이름 만들기 키 만들기** 창에서 **키 파일 이름** 필드에 **key.snk를 입력합니다.** 암호 필드를 **통해 키 파일 보호** 의 선택을 취소합니다.

3. 솔루션 **탐색기에서**VSIX 프로젝트를 선택하고 **속성** 창을 찾습니다.

4. **[복사 빌드 출력] [출력 디렉터리]** 필드를 **true로**설정합니다. 이렇게 하면 솔루션을 다시 빌드할 때 어셈블리를 출력 디렉터리로 복사할 수 있습니다. 여전히 파일에 포함되어 `.vsix` 있습니다. 서명 키를 찾으려면 어셈블리를 확인해야 합니다.

5. 솔루션을 다시 빌드합니다.

6. 이제 MyProjectWizard 프로젝트 디렉토리(디스크*\<위치>\MyProjectTemplate\MyProjectWizard\key.snk)에서*key.snk 파일을 찾을 수 있습니다. *key.snk* 파일을 복사합니다.

7. 출력 디렉토리로 이동하여 어셈블리를*\<찾습니다(디스크 위치>\MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll).* *여기에 key.snk* 파일을 붙여 넣습니다. (이것은 절대적으로 필요한 것은 아니지만 다음 단계를 더 쉽게 만듭니다.)

8. 명령 창을 열고 어셈블리가 만들어진 디렉터리로 변경합니다.

9. *sn.exe* 서명 도구를 찾습니다. 예를 들어 Windows 10 64비트 운영 체제에서 일반적인 경로는 다음과 같은 것입니다.

     *C:\프로그램 파일 (x86)\마이크로소프트 SDKs\윈도우\v10.0A\빈\NETFX 4.6.1 도구*

     도구를 찾을 수 없는 경우 명령 창에서 **/R. sn.exe를** 실행해 보십시오. 경로를 기록합니다.

10. *key.snk* 파일에서 공개 키를 추출합니다. 명령 창에서

     **\<sn.exe>\sn.exe -p key.snk outfile.key의 위치.**

     디렉토리 이름에 공백이있는 경우 인용 부호로 *sn.exe의* 경로를 둘러싸는 것을 잊지 마십시오!

11. 아웃 파일에서 공개 키 토큰을 가져옵니다.

     **\<sn.exe>\sn.exe -t outfile.key의 위치.**

     다시 말하지만, 인용 부호를 잊지 마세요. 다음과 같은 출력에 선이 표시됩니다.

     **공개 키 \<토큰은 토큰>**

     이 값을 기록해 둡을 작성합니다.

12. 사용자 지정 마법사에 대한 참조를 프로젝트 템플릿의 *.vstemplate* 파일에 추가합니다. 솔루션 **탐색기에서** *MyProjectTemplate.vstemplate라는*파일을 찾아 엽니다. 템플릿콘텐츠> \<섹션이 끝나면 다음 섹션을 추가합니다.

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     **MyProjectWizard가** 어셈블리의 이름이며 **토큰은** 이전 단계에서 복사한 토큰입니다.

13. 프로젝트의 모든 파일을 저장하고 다시 빌드합니다.

## <a name="add-the-custom-parameter-to-the-template"></a>템플릿에 사용자 지정 매개 변수 추가

이 예제에서는 템플릿으로 사용되는 프로젝트에 사용자 입력 양식에 지정된 메시지가 사용자 마법사의 표시됩니다.

1. 솔루션 **탐색기에서** **MyProjectTemplate** 프로젝트로 이동하여 *Class1.cs.*

2. 응용 `Main` 프로그램의 메서드에서 다음 코드 줄을 추가합니다.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    템플릿에서 `$custommessage$` 프로젝트를 만들 때 매개 변수가 사용자 입력 양식에 입력된 텍스트로 바뀝습니다.

템플릿으로 내보내기 전에 전체 코드 파일은 다음과 같습니다.

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

1. 솔루션을 다시 빌드하고 디버깅을 시작합니다. Visual Studio의 두 번째 인스턴스가 나타납니다.

2. 새 MyProjectTemplate 프로젝트를 만듭니다. **(파일** > **새** > **프로젝트).**

3. 새 **프로젝트** 대화 상자에서 "myproject"를 검색하여 템플릿을 찾고 이름을 입력하고 **확인을**클릭합니다.

     마법사 사용자 입력 양식이 열립니다.

4. 사용자 지정 매개 변수에 대한 값을 입력하고 단추를 클릭합니다.

     마법사 사용자 입력 양식이 닫히고 템플릿에서 프로젝트가 만들어집니다.

5. **솔루션 탐색기에서**소스 코드 파일을 마우스 오른쪽 단추로 클릭하고 **코드 보기를**클릭합니다.

     `$custommessage$` 마법사 사용자 입력 양식에 입력된 텍스트로 대체되었습니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)
- [마법사확장 요소(비주얼 스튜디오 템플릿)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [비주얼 스튜디오 템플릿에서 NuGet 패키지](/nuget/visual-studio-extensibility/visual-studio-templates)
