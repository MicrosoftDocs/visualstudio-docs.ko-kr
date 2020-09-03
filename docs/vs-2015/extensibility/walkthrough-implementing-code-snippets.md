---
title: '연습: 코드 조각 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201991"
---
# <a name="walkthrough-implementing-code-snippets"></a>연습: 코드 조각 구현
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 조각을 만들고 편집기 확장에 포함 하 여 확장 사용자가 자신의 코드에 코드 조각을 추가할 수 있습니다.  
  
 코드 조각은 파일에 통합 될 수 있는 코드 조각 또는 기타 텍스트입니다. 특정 프로그래밍 언어에 대해 등록 된 모든 코드 조각을 보려면 **도구** 메뉴에서 **코드 조각 관리자**를 클릭 합니다. 파일에 코드 조각을 삽입 하려면 코드 조각을 배치할 위치를 마우스 오른쪽 단추로 클릭 하 고 **코드 조각 삽입** 또는 코드 **감싸기**를 클릭 한 다음 원하는 코드 조각을 찾은 다음 두 번 클릭 합니다. TAB 또는 SHIFT + TAB을 눌러 코드 조각의 관련 부분을 수정한 다음 ENTER 또는 ESC 키를 눌러 수락 합니다. 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조하세요.  
  
 코드 조각은 코드 조각이 파일 이름 확장명을 가진 XML 파일에 포함 되어 있습니다. 코드 조각은 사용자가 찾아서 변경할 수 있도록 코드 조각이 삽입 된 후 강조 표시 되는 필드를 포함할 수 있습니다. 코드 조각 파일은 **코드 조각 관리자** 에 대 한 정보를 제공 하 여 코드 조각 이름이 올바른 범주에 표시 될 수 있도록 합니다. 코드 조각 스키마에 대 한 자세한 내용은 [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)를 참조 하세요.  
  
 이 연습에서는 다음 작업을 수행 하는 방법을 배웁니다.  
  
1. 특정 언어에 대 한 코드 조각을 만들고 등록 합니다.  
  
2. **코드 조각 삽입** 명령을 바로 가기 메뉴에 추가 합니다.  
  
3. 코드 조각 확장을 구현 합니다.  
  
   이 연습은 [연습: 문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)를 기반으로 합니다.  
  
## <a name="prerequisites"></a>사전 준비 사항  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-and-registering-code-snippets"></a>코드 조각 만들기 및 등록  
 일반적으로 코드 조각은 등록 된 언어 서비스와 연결 됩니다. 그러나 <xref:Microsoft.VisualStudio.Package.LanguageService> 코드 조각을 등록 하기 위해를 구현할 필요는 없습니다. 대신, 코드 조각 인덱스 파일에 GUID를 지정 하 고 프로젝트에 추가 하는에서 동일한 GUID를 사용 하면 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 됩니다.  
  
 다음 단계에서는 코드 조각을 만들고 특정 GUID와 연결 하는 방법을 보여 줍니다.  
  
1. 다음 디렉터리 구조를 만듭니다.  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    여기서 *% InstallDir%* 은 Visual Studio 설치 폴더입니다. 이 경로는 일반적으로 코드 조각을 설치 하는 데 사용 되지만 임의의 경로를 지정할 수 있습니다.  
  
2. \ 1033 \ 폴더에서 .xml 파일을 만들고 이름을 **TestSnippets.xml**로 합니다. 이 이름은 일반적으로 조각 인덱스 파일에 사용 되지만 .xml 파일 이름 확장명을 사용 하는 경우 임의의 이름을 지정할 수 있습니다. 다음 텍스트를 추가한 다음 자리 표시자 GUID를 삭제 하 고 사용자 고유의 GUID를 추가 합니다.  
  
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
  
3. 코드 조각 폴더에 파일을 만들고 이름을 **test** `.snippet` 로 지정한 후 다음 텍스트를 추가 합니다.  
  
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
  
   다음 단계에서는 코드 조각을 등록 하는 방법을 보여 줍니다.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>특정 GUID에 대 한 코드 조각을 등록 하려면  
  
1. 이상 **테스트** 프로젝트를 엽니다. 이 프로젝트를 만드는 방법에 대 한 자세한 내용은 [연습: 문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)를 참조 하세요.  
  
2. 프로젝트에서 다음 어셈블리에 대 한 참조를 추가 합니다.  
  
    - VisualStudio입니다.  
  
    - VisualStudio (영문)  
  
    - microsoft. msxml  
  
3. 프로젝트에서 source.extension.vsixmanifest 파일을 엽니다.  
  
4. **자산** 탭에 **VsPackage** 콘텐츠 형식이 포함 되어 **있고 프로젝트가 프로젝트** 이름으로 설정 되어 있는지 확인 합니다.  
  
5. .Pkgdef 테스트 프로젝트를 선택 속성 창 하 고, **파일 생성** 을 **true**로 설정 합니다. 프로젝트를 저장합니다.  
  
6. `SnippetUtilities`프로젝트에 정적 클래스를 추가 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. SnippetUtilities 클래스에서 GUID를 정의 하 고 SnippetsIndex.xml 파일에 사용한 값을 지정 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. 를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 클래스에 추가 합니다 `TestCompletionHandler` . 이 특성은 프로젝트의 public 또는 internal (비정적) 클래스에 추가할 수 있습니다. `using`VisualStudio 네임 스페이스에 대 한 문을 추가 해야 할 수도 있습니다.  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. 프로젝트를 빌드하고 실행합니다. 프로젝트를 실행할 때 시작 되는 Visual Studio의 실험적 인스턴스에서 방금 등록 한 코드 조각이 **testsnippets** 언어의 **코드 조각 관리자** 에 표시 되어야 합니다.  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>바로 가기 메뉴에 조각 삽입 명령 추가  
 **조각 삽입** 명령은 텍스트 파일에 대 한 바로 가기 메뉴에 포함 되지 않습니다. 따라서 명령을 사용 하도록 설정 해야 합니다.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>바로 가기 메뉴에 조각 삽입 명령을 추가 하려면  
  
1. `TestCompletionCommandHandler`클래스 파일을 엽니다.  
  
     이 클래스는를 구현 하므로 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 메서드에서 **코드 조각 삽입** 명령을 활성화할 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . 명령을 사용 하기 전에이 메서드가 자동화 함수 내에서 호출 되지 않았는지 확인 합니다. **코드 조각 삽입** 명령이 클릭 되 면 코드 조각 선택 UI (사용자 인터페이스)가 표시 되기 때문입니다.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. 프로젝트를 빌드하고 실행합니다. 실험적 인스턴스에서 zzz 파일 이름 확장명을 가진 파일을 열고 아무 곳 이나 마우스 오른쪽 단추로 클릭 합니다. **조각 삽입** 명령이 바로 가기 메뉴에 표시 됩니다.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>코드 조각 선택 UI에서 코드 조각 확장 구현  
 이 섹션에서는 바로 가기 메뉴에서 코드 조각 **삽입** 을 클릭할 때 코드 조각 선택 UI가 표시 되도록 코드 조각 확장을 구현 하는 방법을 보여 줍니다. 또한 사용자가 코드 조각 바로 가기를 입력 한 다음 TAB 키를 누르면 코드 조각이 확장 됩니다.  
  
 코드 조각 선택 UI를 표시 하 고 탐색 및 삽입 후 조각 허용을 사용 하도록 설정 하려면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드를 사용 합니다. 삽입 자체는 메서드에 의해 처리 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> .  
  
 코드 조각 확장의 구현은 레거시 인터페이스를 사용 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop> . 현재 편집기 클래스에서 레거시 코드로 변환 하는 경우 레거시 인터페이스는 줄 번호와 열 번호의 조합을 사용 하 여 텍스트 버퍼의 위치를 지정 하지만 현재 클래스는 하나의 인덱스를 사용 합니다. 따라서 버퍼에 각각 10 자 (+ 1 자로 계산 되는 줄 바꿈 문자)가 있는 3 개의 줄이 있는 경우 세 번째 줄의 네 번째 문자는 현재 구현에서 27 번째 문자 이지만 이전 구현의 경우 2 번째 줄에 위치 합니다.  
  
#### <a name="to-implement-snippet-expansion"></a>코드 조각 확장을 구현 하려면  
  
1. 클래스가 포함 된 파일에 `TestCompletionCommandHandler` 다음 문을 추가 합니다 `using` .  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. `TestCompletionCommandHandler`클래스가 인터페이스를 구현 하도록 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> .  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. 클래스에서을 `TestCompletionCommandHandlerProvider` 가져옵니다 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. 코드 확장 인터페이스와에 대 한 전용 필드를 추가 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. 클래스의 생성자에서 `TestCompletionCommandHandler` 다음 필드를 설정 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. 사용자가 코드 **조각 삽입** 명령을 클릭할 때 조각 선택을 표시 하려면 다음 코드를 메서드에 추가 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . 이 설명을 더 쉽게 읽을 수 있도록 문 완성에 사용 되는 Exec () 코드가 표시 되지 않습니다. 대신 코드 블록을 기존 메서드에 추가 합니다. 문자를 확인 하는 코드 뒤에 다음 코드 블록을 추가 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. 탐색할 수 있는 필드가 코드 조각에 있으면 확장 세션이 명시적으로 허용 될 때까지 열린 상태로 유지 됩니다. 코드 조각에 필드가 없으면 세션이 닫히고 메서드에서로 반환 됩니다 `null` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> . <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>메서드에서 이전 단계에서 추가한 코드 조각 선택 UI 코드 뒤에 다음 코드를 추가 하 여 코드 조각 삽입 후 사용자가 TAB 키 또는 SHIFT + tab을 누르면 코드 조각 탐색을 처리 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. 사용자가 해당 바로 가기를 입력 하 고 TAB 키를 누를 때 코드 조각을 삽입 하려면 메서드에 코드를 추가 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . 코드 조각을 삽입 하는 private 메서드는 이후 단계에서 표시 됩니다. 이전 단계에서 추가한 탐색 코드 뒤에 다음 코드를 추가 합니다.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. 인터페이스의 메서드를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> 합니다. 이 구현에서 관심 있는 유일한 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 입니다. 다른 메서드는만 반환 해야 합니다 <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 메서드를 구현합니다. 실제로 확장을 삽입 하는 도우미 메서드는 이후 단계에서 설명 됩니다. 는 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 에서 가져올 수 있는 줄 및 열 정보를 제공 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. 다음 private 메서드는 바로 가기 또는 제목과 경로를 기반으로 코드 조각을 삽입 합니다. 그런 다음 코드 조각을 사용 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> .  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>코드 조각 확장 빌드 및 테스트  
 프로젝트에서 코드 조각 확장이 작동 하는지 여부를 테스트할 수 있습니다.  
  
1. 솔루션을 빌드합니다. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
2. 텍스트 파일을 열고 텍스트를 입력 합니다.  
  
3. 텍스트의 아무 곳 이나 마우스 오른쪽 단추로 클릭 한 다음 **조각 삽입**을 클릭 합니다.  
  
4. 코드 조각 선택 UI에는 **테스트 대체 필드**라는 팝업이 표시 됩니다. 팝업을 두 번 클릭 합니다.  
  
     다음 코드 조각을 삽입 해야 합니다.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     ENTER 또는 ESC 키를 누르지 마십시오.  
  
5. TAB 키와 SHIFT + TAB을 눌러 "first"와 "second" 사이를 전환 합니다.  
  
6. ENTER 또는 ESC 키를 눌러 삽입을 허용 합니다.  
  
7. 텍스트의 다른 부분에 "test"를 입력 한 다음 TAB 키를 누릅니다. "Test"는 코드 조각 바로 가기입니다. 조각이 다시 삽입 되어야 합니다.  
  
## <a name="next-steps"></a>다음 단계
