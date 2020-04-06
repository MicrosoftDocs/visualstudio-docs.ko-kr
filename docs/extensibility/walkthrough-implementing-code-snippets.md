---
title: '연습: 코드 조각 구현 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697096"
---
# <a name="walkthrough-implement-code-snippets"></a>연습: 코드 조각 구현
코드 조각을 만들고 편집기 확장에 포함시켜 확장 사용자가 자신의 코드에 추가할 수 있습니다.

 코드 코드 조각은 파일에 통합할 수 있는 코드 또는 기타 텍스트의 조각입니다. **도구** 메뉴에서 특정 프로그래밍 언어에 등록된 모든 스니펫을 보려면 **코드 스니펫 관리자를**클릭합니다. 파일에 스니펫을 삽입하려면 스니펫을 원하는 위치를 마우스 오른쪽 단추로 클릭하고 코드 조각 삽입 또는 **둘러싸기**를 클릭한 다음 원하는 코드 조각을 찾은 다음 두 번 클릭합니다. **탭** 또는 **시프트**+**탭을** 눌러 스니펫의 관련 부분을 수정한 다음 **Enter** 또는 **Esc를** 눌러 수락합니다. 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조하십시오.

 코드 스니펫은 .snippet* 파일 이름 확장명이 있는 XML 파일에 포함되어 있습니다. 스니펫에는 스니펫을 삽입한 후 강조 표시된 필드가 포함되어 사용자가 찾아서 변경할 수 있습니다. 또한 코드 조각 파일은 **코드 조각 관리자에** 대한 정보를 제공하여 올바른 범주에 코드 조각을 표시할 수 있습니다. 코드 조각 스키마에 대한 자세한 내용은 [코드 코드 조각 스키마 참조를](../ide/code-snippets-schema-reference.md)참조하십시오.

 이 연습에서는 이러한 작업을 수행하는 방법을 설명합니다.

1. 특정 언어에 대한 코드 조각을 만들고 등록합니다.

2. 바로 가기 메뉴에 코드 삽입 명령을 **추가합니다.**

3. 스니펫 확장을 구현합니다.

   이 연습은 [연습: 명령문 완료를](../extensibility/walkthrough-displaying-statement-completion.md)기반으로 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-and-register-code-snippets"></a>코드 조각 만들기 및 등록
 일반적으로 코드 조각은 등록된 언어 서비스와 연결됩니다. 그러나 코드 조각을 등록하기 <xref:Microsoft.VisualStudio.Package.LanguageService> 위해 을 구현할 필요는 없습니다. 대신 스니펫 인덱스 파일에 GUID를 지정한 다음 프로젝트에 추가하는 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 것과 동일한 GUID를 사용합니다.

 다음 단계에서는 코드 조각을 만들고 특정 GUID와 연결하는 방법을 보여 줍니다.

1. 다음 디렉터리 구조를 만듭니다.

    **%설치디르%\테스트스니펫\스니펫\1033\\**

    *여기서 %InstallDir%는* 비주얼 스튜디오 설치 폴더입니다. 이 경로는 일반적으로 코드 조각 을 설치하는 데 사용되지만 모든 경로를 지정할 수 있습니다.

2. \1033\ 폴더에서 *.xml* 파일을 만들고 **TestSnippets.xml.** 이 이름은 일반적으로 스니펫 인덱스 파일에 사용되지만 *.xml* 파일 이름 확장이 있는 한 이름을 지정할 수 있습니다. 다음 텍스트를 추가한 다음 자리 표시자 GUID를 삭제하고 직접 추가합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <SnippetCollection>
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">
           <SnippetDir>
               <OnOff>On</OnOff>
               <Installed>true</Installed>
               <Locale>1033</Locale>
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>
               <LocalizedName>Snippets</LocalizedName>
           </SnippetDir>
       </Language>
   </SnippetCollection>
   ```

3. 스니펫 폴더에 파일을 만들고 **테스트**`.snippet`이름을 지정한 다음 다음 텍스트를 추가합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
       <CodeSnippet Format="1.0.0">
           <Header>
               <Title>Test replacement fields</Title>
               <Shortcut>test</Shortcut>
               <Description>Code snippet for testing replacement fields</Description>
               <Author>MSIT</Author>
               <SnippetTypes>
                   <SnippetType>Expansion</SnippetType>
               </SnippetTypes>
           </Header>
           <Snippet>
               <Declarations>
                   <Literal>
                     <ID>param1</ID>
                       <ToolTip>First field</ToolTip>
                       <Default>first</Default>
                   </Literal>
                   <Literal>
                       <ID>param2</ID>
                       <ToolTip>Second field</ToolTip>
                       <Default>second</Default>
                   </Literal>
               </Declarations>
               <References>
                  <Reference>
                      <Assembly>System.Windows.Forms.dll</Assembly>
                  </Reference>
               </References>
               <Code Language="TestSnippets">
                   <![CDATA[MessageBox.Show("$param1$");
        MessageBox.Show("$param2$");]]>
               </Code>
           </Snippet>
       </CodeSnippet>
   </CodeSnippets>
   ```

   다음 단계에서는 코드 조각을 등록하는 방법을 보여 주며, 코드 조각을 등록하는 방법을 보여 준다.

### <a name="to-register-code-snippets-for-a-specific-guid"></a>특정 GUID에 대한 코드 스니펫을 등록하려면

1. 완료 테스트 프로젝트를 **엽니다.** 이 프로젝트를 만드는 방법에 대한 자세한 내용은 [연습: 명령문 완료를](../extensibility/walkthrough-displaying-statement-completion.md)참조하십시오.

2. 프로젝트에서 다음 어셈블리에 참조를 추가합니다.

    - 마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭

    - 마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭.8.0

    - 마이크로 소프트.msxml

3. 프로젝트에서 **source.extension.vsixmanifest** 파일을 엽니다.

4. **자산** 탭에 **VsPackage** 콘텐츠 유형이 포함되어 있고 **프로젝트가** 프로젝트 이름으로 설정되어 있는지 확인합니다.

5. 완료 테스트 프로젝트를 선택하고 속성 창 세트에서 **Pkgdef 파일 생성을** **true로**선택합니다. 프로젝트를 저장합니다.

6. 프로젝트에 정적 `SnippetUtilities` 클래스를 추가합니다.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. SnippetUtilities 클래스에서 GUID를 정의하고 *SnippetsIndex.xml* 파일에 사용한 값을 지정합니다.

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. 클래스에 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 를 `TestCompletionHandler` 추가합니다. 이 특성은 프로젝트의 모든 공용 또는 내부(비정적) 클래스에 추가할 수 있습니다. Microsoft.VisualStudio.Shell `using` 네임스페이스에 대한 지시문을 추가해야 할 수 있습니다.

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. 프로젝트를 빌드하고 실행합니다. 프로젝트를 실행할 때 시작되는 Visual Studio의 실험적인 인스턴스에서는 방금 등록한 코드 조각이 **TestSnippets** 언어 아래의 **코드 조각 관리자에** 표시되어야 합니다.

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>바로 가기 메뉴에 스니펫 삽입 명령 추가
 코드 **조각 삽입** 명령은 텍스트 파일의 바로 가기 메뉴에 포함되지 않습니다. 따라서 명령을 사용 설정 해야 합니다.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>바로 가기 메뉴에 스니펫 삽입 명령을 추가하려면

1. `TestCompletionCommandHandler` 클래스 파일을 엽니다.

     이 클래스는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>구현하기 때문에 메서드에서 **코드 삽입** <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 명령을 활성화할 수 있습니다. 명령을 활성화하기 전에 **삽입 코드 조각을** 클릭하면 스니펫 선택사용자 인터페이스(UI)가 표시되므로 이 메서드가 자동화 함수 내에서 호출되지 않는지 확인합니다.

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. 프로젝트를 빌드하고 실행합니다. 실험사례에서는 *.zzz* 파일 이름 확장명이 있는 파일을 연 다음 마우스 오른쪽 단추로 클릭합니다. **코드 조각 삽입** 명령이 바로 가기 메뉴에 나타납니다.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>스니펫 피커 UI에서 스니펫 확장 구현
 이 섹션에서는 바로 가기 메뉴에서 코드 조각 **삽입을** 클릭할 때 코드 조각 선택기 UI가 표시되도록 코드 조각 확장을 구현하는 방법을 보여 줍니다. 사용자가 코드 조각 바로 가기를 입력한 다음 **Tab을**누르면 코드 스니펫도 확장됩니다.

 코드 조각 선택기 UI를 표시하고 탐색 및 삽입 후 스니펫 허용을 사용하려면 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 사용합니다. 삽입 자체는 메서드에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 의해 처리됩니다.

 코드 코드 조각 확장의 구현은 레거시 <xref:Microsoft.VisualStudio.TextManager.Interop> 인터페이스를 사용합니다. 현재 편집기 클래스에서 레거시 코드로 변환할 때 레거시 인터페이스는 줄 번호와 열 번호를 조합하여 텍스트 버퍼의 위치를 지정하지만 현재 클래스는 하나의 인덱스를 사용한다는 점을 기억하십시오. 따라서 버퍼에 각각 10자(한 문자로 계산되는 줄 바임)가 있는 세 줄이 있는 경우 세 번째 줄의 네 번째 문자는 현재 구현에서 위치 27에 있지만 이전 구현에서는 2, 3번째 줄에 있습니다.

#### <a name="to-implement-snippet-expansion"></a>스니펫 확장을 구현하려면

1. `TestCompletionCommandHandler` 클래스가 포함된 파일에 다음 `using` 지시문을 추가합니다.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. 클래스가 `TestCompletionCommandHandler` 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 구현합니다.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. `TestCompletionCommandHandlerProvider` 클래스에서 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>을 가져옵니다.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. 코드 확장 인터페이스 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>에 대한 몇 가지 개인 필드를 추가합니다.

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. `TestCompletionCommandHandler` 클래스의 생성자에서 다음 필드를 설정합니다.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. 사용자가 코드 조각 삽입 명령을 클릭할 때 코드 **선택기를** 표시하려면 메서드에 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 다음 코드를 추가합니다. 이 설명을 더 읽기 쉽게 `Exec()`만들려면 문 완성에 사용되는 코드가 표시되지 않고 대신 코드 블록이 기존 메서드에 추가됩니다. 문자를 확인하는 코드 다음에 다음 코드 블록을 추가합니다.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. 스니펫에 탐색할 수 있는 필드가 있는 경우 확장이 명시적으로 수락될 때까지 확장 세션이 열려 있습니다. 스니펫에 필드가 없는 경우 세션이 닫히고 `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> 메서드에서 와 같이 반환됩니다. 이 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드에서 이전 단계에서 추가한 코드 선택기 UI 코드 다음에 다음 코드를 추가하여 스니펫 탐색을 처리합니다(사용자가 스니펫 삽입 후 **탭** 또는 **Shift**+**Tab을** 누를 때).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. 사용자가 해당 바로 가기를 입력한 다음 **Tab을**누르면 코드 조각을 삽입하려면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드에 코드를 추가합니다. 스니펫을 삽입하는 개인 메서드는 이후 단계에서 표시됩니다. 이전 단계에서 추가한 탐색 코드 다음에 다음 코드를 추가합니다.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. 인터페이스의 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 구현합니다. 이 구현에서 관심 있는 유일한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>방법은 및 . 다른 메서드는 반환해야 <xref:Microsoft.VisualStudio.VSConstants.S_OK>합니다.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 메서드를 구현합니다. 실제로 확장을 삽입하는 도우미 메서드는 이후 단계에서 다룹니다. 은 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>에서 얻을 수 있는 줄 및 열 정보를 제공합니다.

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. 다음 private 메서드는 바로 가키 또는 제목 및 경로에 따라 코드 조각을 삽입합니다. 그런 다음 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> 스니펫을 사용하여 메서드를 호출합니다.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>코드 스니펫 확장 빌드 및 테스트
 프로젝트에서 코드 조각 확장이 작동하는지 테스트할 수 있습니다.

1. 솔루션을 빌드합니다. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

2. 텍스트 파일을 열고 텍스트를 입력합니다.

3. 텍스트의 위치를 마우스 오른쪽 단추로 클릭한 다음 **코드 조각 삽입을**클릭합니다.

4. 코드 조각 선택기 UI **테스트 대체 필드를**표시 하는 팝업과 함께 표시 되어야 합니다. 팝업을 두 번 클릭합니다.

     다음 스니펫을 삽입해야 합니다.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     **Enter** 또는 **Esc를**누르지 마십시오.

5. **탭** 및 **이동**+**탭을** 눌러 "첫 번째"와 "두 번째" 사이를 전환합니다.

6. **Enter** 또는 **Esc를**눌러 삽입을 수락합니다.

7. 텍스트의 다른 부분에서 "테스트"를 입력한 다음 **탭**을 누릅니다. "test"는 코드 조각 바로 가기이므로 스니펫을 다시 삽입해야 합니다.

## <a name="next-steps"></a>다음 단계
