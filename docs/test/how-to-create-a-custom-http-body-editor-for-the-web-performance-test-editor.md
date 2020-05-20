---
title: 웹 성능 테스트 편집기에 대한 사용자 지정 HTTP 본문 편집기 만들기
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efc9a959fa02b62583e7bf366e8c580b2876a4a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589203"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>방법: 웹 성능 테스트 편집기에 대한 사용자 지정 HTTP 본문 편집기 만들기

SOAP, REST, asmx, wcf, RIA 및 기타 웹 서비스 요청 형식과 같은 웹 서비스 요청의 문자열 본문 콘텐츠나 이진 본문 콘텐츠를 편집하는 데 사용할 수 있는 사용자 지정 콘텐츠 편집기를 만들 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

다음 종류의 편집기를 구현할 수 있습니다.

- **문자열 콘텐츠 편집기** 이 편집기는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 인터페이스를 사용하여 구현합니다.

- **이진 콘텐츠 편집기** 이 편집기는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 인터페이스를 사용하여 구현합니다.

이러한 인터페이스는 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 네임스페이스에 포함되어 있습니다.

## <a name="create-a-windows-control-library-project"></a>Windows 컨트롤 라이브러리 프로젝트 만들기

1. Visual Studio에서 새 **Windows Forms 컨트롤 라이브러리** 프로젝트를 만듭니다. 프로젝트 이름을 **MessageEditors**로 지정합니다.

   프로젝트가 새 솔루션에 추가되고 *UserControl1.cs*라는 <xref:System.Windows.Forms.UserControl>이 디자이너에 표시됩니다.

1. **도구 상자**의 **공용 컨트롤** 범주에서 <xref:System.Windows.Forms.RichTextBox>를 UserControl1로 끌어 옵니다.

1. <xref:System.Windows.Forms.RichTextBox> 컨트롤의 오른쪽 위에 있는 작업 태그 문자 모양(![스마트 태그 문자 모양](../test/media/vs_winformsmttagglyph.gif))을 선택한 다음, **부모 컨테이너에서 도킹**을 선택합니다.

1. **솔루션 탐색기**에서 Windows Forms 라이브러리 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. **속성**에서 **애플리케이션** 탭을 선택합니다.

1. **대상 프레임워크** 드롭다운 목록에서 .NET Framework 4(또는 이상)를 선택합니다.

1. **대상 프레임워크 변경** 대화 상자가 표시됩니다.

1. **예**를 선택합니다.

1. **솔루션 탐색기**에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

1. **참조 추가** 대화 상자가 표시됩니다.

1. **.NET** 탭을 선택하고 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework**를 선택한 다음, **확인**을 선택합니다.

1. **디자이너 보기**가 아직 열려 있지 않으면 **솔루션 탐색기**에서 **UserControl1.cs**를 마우스 오른쪽 단추로 클릭한 다음, **디자이너 보기**를 선택합니다.

1. 디자인 화면에서 마우스 오른쪽 단추를 클릭하고 **코드 보기**를 선택합니다.

1. (선택 사항) 클래스 및 생성자의 이름을 UserControl1에서 의미 있는 이름(예: MessageEditorControl)으로 바꿉니다.

    > [!NOTE]
    > 이 샘플에서는 MessageEditorControl을 사용합니다.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. 다음 속성을 추가하여 RichTextBox1의 텍스트를 가져오거나 설정할 수 있도록 합니다. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 인터페이스는 EditString을 사용하고 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>은 EditByteArray를 사용합니다.

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Windows 컨트롤 라이브러리 프로젝트에 클래스 추가

프로젝트에 클래스를 추가합니다. 이 클래스는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 인터페이스를 구현하는 데 사용됩니다.

**이 절차의 코드 개요**

이전 절차에서 만든 MessageEditorControl의 <xref:System.Windows.Forms.UserControl>은 messageEditorControl로 인스턴스화됩니다.

```csharp
private MessageEditorControl messageEditorControl
```

messageEditorControl 인스턴스는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> 메서드로 만든 플러그 인 대화 상자 내에서 호스팅됩니다. 또한 messageEditorControl의 <xref:System.Windows.Forms.RichTextBox>는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>의 콘텐츠로 채워집니다. 그러나 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*>에서 `true`를 반환하지 않는 경우에는 플러그 인을 만들 수 없습니다. 이 편집기의 경우 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*>의 `true`에 "xml"이 포함되어 있으면 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*>은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>를 반환합니다.

문자열 본문의 편집이 완료된 후 사용자가 플러그 인 대화 상자에서 **확인**을 클릭하면 편집된 텍스트를 문자열로 가져오고 웹 성능 테스트 편집기의 요청에 있는 **문자열 본문**을 업데이트하기 위해 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*>가 호출됩니다.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>클래스 만들기 및 IStringHttpBodyEditorPlugin 인터페이스 구현

1. **솔루션 탐색기**에서 Windows Forms 컨트롤 라이브러리 프로젝트를 마우스 오른쪽 단추로 클릭하고 **새 항목 추가**를 선택합니다.

   **새 항목 추가** 대화 상자가 표시됩니다.

2. **클래스**를 선택합니다.

3. **이름** 텍스트 상자에 클래스의 의미 있는 이름(예: `MessageEditorPlugins`)을 입력합니다.

4. **추가**를 선택합니다.

   Class1이 프로젝트에 추가되고 코드 편집기에 표시됩니다.

5. 코드 편집기에서 다음 `using` 문을 추가합니다.

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. 다음 코드에 붙여넣어 인터페이스를 구현합니다.

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>클래스에 IBinaryHttpBodyEditorPlugin 추가

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 인터페이스를 구현합니다.

**이 절차의 코드 개요**

<xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 인터페이스에 대한 코드 구현은 이전 절차에서 설명한 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>과 비슷합니다. 그러나 이진 버전에서는 바이트 배열을 사용하여 문자열 대신 이진 데이터를 처리합니다.

첫 번째 절차에서 만든 MessageEditorControl의 <xref:System.Windows.Forms.UserControl>은 messageEditorControl로 인스턴스화됩니다.

```csharp
private MessageEditorControl messageEditorControl
```

messageEditorControl 인스턴스는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> 메서드로 만든 플러그 인 대화 상자 내에서 호스팅됩니다. 또한 messageEditorControl의 <xref:System.Windows.Forms.RichTextBox>는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>의 콘텐츠로 채워집니다. 그러나 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*>에서 `true`를 반환하지 않는 경우에는 플러그 인을 만들 수 없습니다. 이 편집기의 경우 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*>의 `true`에 "msbin1"이 포함되어 있으면 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*>은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>를 반환합니다.

문자열 본문의 편집이 완료된 후 사용자가 플러그 인 대화 상자에서 **확인**을 클릭하면 편집된 텍스트를 문자열로 가져오고 웹 성능 테스트 편집기의 요청에 있는 **BinaryHttpBody.Data**를 업데이트하기 위해 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*>가 호출됩니다.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>클래스에 IBinaryHttpBodyEditorPlugin을 추가하려면

- 이전 절차에서 추가한 XmlMessageEditor 클래스 아래에 다음 코드를 작성하거나 복사하여 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> 인터페이스의 Msbin1MessageEditor 클래스를 인스턴스화하고 필요한 메서드를 구현합니다.

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>플러그 인 빌드 및 배포

1. **빌드** 메뉴에서 **\<Windows Form 컨트롤 라이브러리 프로젝트 이름> 빌드**를 선택합니다.

2. Visual Studio의 모든 인스턴스를 닫습니다.

   > [!NOTE]
   > Visual Studio를 닫으면 복사하기 전에 *.dll* 파일이 잠기지 않습니다.

3. 프로젝트의 *bin\debug* 폴더에서 결과 *.dll* 파일(예: *MessageEditors.dll*)을 *%ProgramFiles%\Microsoft Visual Studio\2017\\\<edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*에 복사합니다.

4. Visual Studio를 엽니다.

   *.dll*이 이제 Visual Studio에 등록됩니다.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>웹 성능 테스트를 사용하여 플러그 인 확인

1. 테스트 프로젝트를 만듭니다.

2. 웹 성능 테스트를 만들고 브라우저에서 웹 서비스에 대한 URL을 입력합니다.

3. 기록을 마치면 웹 성능 테스트 편집기에서 웹 서비스의 요청을 확장하고 **문자열 본문** 또는 **이진 본문**을 선택합니다.

4. **속성** 창에서 문자열 본문이나 이진 본문을 선택하고 줄임표 **(…)** 를 선택합니다.

   **HTTP 본문 데이터 편집** 대화 상자가 표시됩니다.

5. 이제 데이터를 편집하고 **확인**을 선택합니다. 그러면 적절한 GetNewValue 메서드가 호출되어 <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>의 콘텐츠가 업데이트됩니다.

## <a name="compile-the-code"></a>코드 컴파일

Windows 컨트롤 라이브러리 프로젝트의 대상 프레임워크가 .NET Framework 4.5인지 확인합니다. 기본적으로 Windows 컨트롤 라이브러리 프로젝트는 Microsoft.VisualStudio.QualityTools.WebTestFramework 참조를 포함할 수 없는 .NET Framework 4.5 Client 프레임워크를 대상으로 합니다.

자세한 내용은 [애플리케이션 페이지, 프로젝트 디자이너(C#)](../ide/reference/application-page-project-designer-csharp.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [방법: 요청 수준 플러그 인 만들기](../test/how-to-create-a-request-level-plug-in.md)
- [웹 성능 테스트에 대한 사용자 지정 추출 규칙 코딩](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)
- [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)
- [방법: 웹 성능 테스트 결과 뷰어에 대한 Visual Studio 추가 기능 만들기](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
