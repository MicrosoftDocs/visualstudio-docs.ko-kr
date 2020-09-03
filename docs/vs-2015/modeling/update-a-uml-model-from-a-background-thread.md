---
title: 백그라운드 스레드에서 UML 모델 업데이트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659458"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>백그라운드 스레드에서 UML 모델 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

때로는 백그라운드 스레드에서 모델을 변경하는 것이 유용할 수 있습니다. 예를 들어 속도가 느린 외부 리소스에서 정보를 로드하는 경우 백그라운드 스레드를 사용하여 업데이트를 감독할 수 있습니다. 이렇게 하면 사용자가 발생하는 즉시 각 업데이트를 볼 수 있습니다.

 그러나 UML 저장소가 스레드로부터 안전하지 않은 것에 주의해야 합니다. 다음과 같은 예방 조치가 중요합니다.

- 모델이나 다이어그램에 대한 모든 업데이트는 UI(사용자 인터페이스) 스레드에서 수행해야 합니다. 백그라운드 스레드는 <xref:System.Windows.Forms.Control.Invoke%2A> 또는 `Dispatcher.`<xref:System.Windows.Threading.Dispatcher.Invoke%2A>을 사용하여 UI 스레드가 실제 업데이트를 수행하도록 해야 합니다.

- 일련의 변경 내용을 단일 트랜잭션으로 그룹화하는 경우 트랜잭션이 진행되는 동안 사용자가 모델을 편집할 수 없도록 하는 것이 좋습니다. 그렇지 않으면 사용자의 편집 내용이 모두 동일한 트랜잭션에 포함됩니다. 모달 대화 상자를 표시하여 사용자가 변경하지 못하도록 차단할 수 있습니다. 원하는 경우 대화 상자에 취소 단추를 제공할 수 있습니다. 변경 시 사용자가 변경 내용을 확인할 수 있습니다.

## <a name="example"></a>예
 이 예제에서는 백그라운드 스레드를 사용하여 모델에 대한 여러 가지 변경을 수행합니다. 대화 상자는 스레드가 실행되는 동안 사용자를 제외하는 데 사용됩니다. 이 간단한 예제에서는 대화 상자에 취소 단추가 제공되지 않습니다. 그러나 해당 기능을 쉽게 추가할 수 있습니다.

#### <a name="to-run-the-example"></a>예제를 실행하려면

1. [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)에 설명 된 대로 c # 프로젝트에서 명령 처리기를 만듭니다.

2. 프로젝트에 아래 어셈블리에 대한 참조가 포함되어 있는지 확인합니다.

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility

   - Microsoft.VisualStudio.Modeling.Sdk.[version]

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]

   - Microsoft.VisualStudio.Uml.Interfaces

   - System.ComponentModel.Composition

   - System.Windows.Forms

3. **ProgressForm**이라는 Windows form을 프로젝트에 추가 합니다. 업데이트가 진행 중이라는 메시지가 표시됩니다. 다른 컨트롤은 없어도 됩니다.

4. 7단계 후에 표시된 코드를 포함하는 C# 파일을 추가합니다.

5. 프로젝트를 빌드하고 실행합니다.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 새 인스턴스가 실험적 모드에서 시작됩니다.

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 실험적 인스턴스에서 UML 클래스 다이어그램을 만들거나 엽니다.

7. UML 클래스 다이어그램의 아무 곳 이나 마우스 오른쪽 단추로 클릭 한 다음 **여러 Uml 클래스 추가**를 클릭 합니다.

   여러 개의 새 클래스 상자가 0.5초 간격으로 다이어그램에 하나씩 나타납니다.

```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.Composition;
using System.Threading;
using System.Windows.Forms;

using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.Uml.Classes;

namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class UmlClassAdderCommand : ICommandExtension
  {

    [Import]
    IDiagramContext context { get; set; }

    [Import]
    ILinkedUndoContext linkedUndoContext { get; set; }

    // Called when the user runs the command.
    public void Execute(IMenuCommand command)
    {
      // The form that will exclude the user.
      ProgressForm form = new ProgressForm();

      // System.ComponentModel.BackgroundWorker is a
      // convenient way to run a background thread.
      BackgroundWorker worker = new BackgroundWorker();
      worker.WorkerSupportsCancellation = true;

      worker.DoWork += delegate(object sender, DoWorkEventArgs args)
      {
        // This block will be executed in a background thread.

        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;
        IModelStore store = diagram.ModelStore;
        const int CLASSES_TO_CREATE = 15;

        // Group all the changes together.
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))
        {
          for (int i = 1; i < CLASSES_TO_CREATE; i++)
          {
            if (worker.CancellationPending)
               return; // No commit - undo all.

            // Create model elements using the UI thread by using
            // the Invoke method on the progress form. Always
            // modify the model and diagrams from a UI thread.
            form.Invoke((MethodInvoker)(delegate
            {
              IClass newClass = store.Root.CreateClass();
              newClass.Name = string.Format("NewClass{0}", i);
              diagram.Display(newClass);
            }));

            // Sleep briefly so that we can watch the updates.
            Thread.Sleep(500);
          }

          // Commit the transaction or it will be rolled back.
          transaction.Commit();
        }
      };

      // Close the form when the thread completes.
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)
      {
        form.Close();
      };

      // Start the thread before showing the modal progress dialog.
      worker.RunWorkerAsync();

      // Show the form modally, parented on VS.
      // Prevents the user from making changes while in progress.
      form.ShowDialog();
    }

    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }

    public string Text
    {
      get { return "Add several classes"; }
    }
  }
}
```

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>예제에서 사용자가 스레드를 취소할 수 있게 하려면

1. 진행률 대화 상자에 취소 단추를 추가합니다.

2. 진행률 대화 상자에 다음 코드를 추가합니다.

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. Execute() 메서드에서 폼 생성 뒤에 다음 줄을 삽입합니다.

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>UI 스레드에 액세스하는 기타 방법
 대화 상자를 만들지 않으려면 다이어그램을 표시하는 컨트롤에 액세스할 수 있습니다.

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 `uiThreadHolder.Invoke()`를 사용하여 UI 스레드에서 작업을 수행할 수 있습니다.

## <a name="see-also"></a>관련 항목
 모델링 [다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [모델링 다이어그램의 제스처 처리기 정의](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
