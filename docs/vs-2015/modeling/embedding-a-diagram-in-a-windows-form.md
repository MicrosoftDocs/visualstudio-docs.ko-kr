---
title: Windows Form에 다이어그램 포함 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669698"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Windows Forms에 다이어그램 포함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

창에 표시 되는 Windows 컨트롤에 DSL 다이어그램을 포함할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="embedding-a-diagram"></a>다이어그램 포함

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Windows 컨트롤에 DSL 다이어그램을 포함 하려면

1. 새 **사용자 정의 컨트롤** 파일을 DslPackage 프로젝트에 추가 합니다.

2. 사용자 정의 컨트롤에 Panel 컨트롤을 추가 합니다. 이 패널에는 DSL 다이어그램이 포함 됩니다.

     필요한 다른 컨트롤을 추가 합니다.

     컨트롤의 앵커 속성을 설정 합니다.

3. 솔루션 탐색기에서 사용자 정의 컨트롤 파일을 마우스 오른쪽 단추로 클릭 하 고 **코드 보기**를 클릭 합니다. 이 생성자와 변수를 코드에 추가 합니다.

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDSLDocView docView;

    ```

4. 다음 콘텐츠를 사용 하 여 새 파일을 DslPackage 프로젝트에 추가 합니다.

    ```
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }

    ```

5. DSL을 테스트 하려면 F5 키를 누르고 샘플 모델 파일을 엽니다. 다이어그램은 컨트롤 내부에 표시 됩니다. 도구 상자 및 기타 기능은 정상적으로 작동 합니다.

#### <a name="updating-the-form-using-store-events"></a>Store 이벤트를 사용 하 여 폼 업데이트

1. 폼 디자이너에서 라는 **ListBox** 를 추가 `listBox1` 합니다. 그러면 모델의 요소 목록이 표시 됩니다. *저장소 이벤트*를 사용 하 여 모델과 함께 synchronism에 유지 됩니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

2. 사용자 지정 코드 파일에서 추가 메서드를 DocView 클래스로 재정의 합니다.

    ```

    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }

    ```

3. 사용자 컨트롤 뒤에 있는 코드에서 추가 및 제거 된 요소를 수신 하는 메서드를 삽입 합니다.

    ```

          public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }

    ```

4. DSL을 테스트 하려면 F5 키를 누르고의 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 샘플 모델 파일을 엽니다.

     목록 상자에는 모델의 요소 목록이 표시 되 고, 추가 또는 삭제 후, 실행 취소 및 다시 실행 후에도 올바른 것을 확인할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md) [하 여 도메인별 언어를 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
