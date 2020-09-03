---
title: '연습: 문 완성 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 472ff8c10e1346f25e7bc72ed5fd4ee9f31bbafa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904788"
---
# <a name="walkthrough-display-statement-completion"></a>연습: 명령문 완성 표시
완료를 제공 하 고 완료 세션을 트리거하는 데 사용할 식별자를 정의 하 여 언어 기반 문 완성을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 문 완성을 정의 하 고 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의한 다음 해당 형식에 대 한 완료만 표시할 수 있습니다. 또는 기존 콘텐츠 형식 (예: "일반 텍스트")에 대해 완료를 트리거할 수 있습니다. 이 연습에서는 텍스트 파일의 콘텐츠 형식인 "plaintext" 콘텐츠 형식에 대해 문 완성을 트리거하는 방법을 보여 줍니다. "텍스트" 콘텐츠 형식은 코드 및 XML 파일을 비롯 한 다른 모든 콘텐츠 형식의 상위 항목입니다.

 문 완성은 일반적으로 특정 문자를 입력 하 여 트리거됩니다. 예를 들어 "using"과 같은 식별자의 시작 부분을 입력 합니다. 일반적으로 **스페이스바**, **Tab**또는 **enter** 키를 눌러 선택 항목을 커밋하는 방식으로 해제 됩니다. 키 입력에 대 한 명령 처리기 ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스)와 인터페이스를 구현 하는 처리기 공급자를 사용 하 여 문자를 입력할 때 트리거하는 IntelliSense 기능을 구현할 수 있습니다 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . 완료에 참여 하는 식별자의 목록 인 완성 원본을 만들려면 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 인터페이스와 완성 원본 공급자 (인터페이스)를 구현 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . 공급자는 MEF (Managed Extensibility Framework) 구성 요소 부분입니다. 소스 및 컨트롤러 클래스를 내보내고 서비스와 broker를 가져오는 일을 담당 합니다. 예를 들어 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , 텍스트 버퍼에서 탐색을 사용 하도록 설정 하는와 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 완료 세션을 트리거하는가 있습니다.

 이 연습에서는 하드 코드 된 식별자 집합에 대해 문 완성을 구현 하는 방법을 보여 줍니다. 모든 구현에서 언어 서비스 및 언어 설명서는 해당 콘텐츠를 제공 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `CompletionTest` 합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가 하 고 **CopyLocal** 이로 설정 되었는지 확인 합니다 `false` .

     VisualStudio

     Microsoft.VisualStudio.Language.Intellisense

     VisualStudio.

     VisualStudio. 15.0

     VisualStudio를 변경할 수 없습니다.

     VisualStudio입니다.

## <a name="implement-the-completion-source"></a>완성 소스 구현
 완료 원본은 사용자가 식별자의 첫 번째 문자와 같은 완성 트리거를 입력할 때 식별자 집합을 수집 하 고 완료 창에 콘텐츠를 추가 하는 일을 담당 합니다. 이 예제에서는 식별자와 해당 설명이 메서드에 하드 코딩 됩니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> . 대부분의 실제 사용에서는 언어의 파서를 사용 하 여 완성 목록을 채울 토큰을 가져옵니다.

### <a name="to-implement-the-completion-source"></a>완료 원본을 구현 하려면

1. 클래스 파일을 추가하고 이름을 `TestCompletionSource`로 지정합니다.

2. 다음 가져오기를 추가 합니다.

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. 을 구현 하도록 클래스 선언을 수정 합니다 `TestCompletionSource` <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> .

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. 원본 공급자, 텍스트 버퍼 및 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 개체 목록 (완료 세션에 참여할 식별자에 해당)에 대 한 전용 필드를 추가 합니다.

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. 소스 공급자 및 버퍼를 설정 하는 생성자를 추가 합니다. `TestCompletionSourceProvider`클래스는 이후 단계에서 정의 됩니다.

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>컨텍스트에 제공 하려는 완료를 포함 하는 완성 집합을 추가 하 여 메서드를 구현 합니다. 각 완성 집합에는 완성의 집합이 포함 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 되며 완성 창의 탭에 해당 합니다. Visual Basic 프로젝트에서 완료 창 탭의 이름은 **공통** 및 **모든**입니다. `FindTokenSpanAtPosition` 메서드는 다음 단계에서 정의 됩니다.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. 다음 메서드는 커서의 위치에서 현재 단어를 찾는 데 사용 됩니다.

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. 메서드를 구현 합니다 `Dispose()` .

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>완성 원본 공급자 구현
 완성 원본 공급자는 완성 소스를 인스턴스화하는 MEF 구성 요소 부분입니다.

### <a name="to-implement-the-completion-source-provider"></a>완성 원본 공급자를 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 `TestCompletionSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 합니다. 이 클래스를 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "일반 텍스트" 및 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "테스트 완료"의로 내보냅니다.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>완성 원본에서 현재 단어를 찾는를 가져옵니다.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. 메서드를 구현 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 하 여 완성 소스를 인스턴스화합니다.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자 구현
 완료 명령 처리기 공급자는에서 파생 되며 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , 텍스트 뷰 생성 이벤트를 수신 하 고에서 뷰를 변환 합니다 .이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 를 통해 Visual Studio 셸의 명령 체인에 명령을 추가할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . 이 클래스는 MEF 내보내기 이므로이 클래스를 사용 하 여 명령 처리기 자체에 필요한 서비스를 가져올 수도 있습니다.

#### <a name="to-implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자를 구현 하려면

1. 이라는 파일을 추가 `TestCompletionCommandHandler` 합니다.

2. 다음 using 지시문을 추가 합니다.

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 을 구현 하는 라는 클래스를 추가 `TestCompletionHandlerProvider` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 합니다. 이 클래스 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 를 "토큰 완성 처리기", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "일반 텍스트"의 및의로 내보냅니다 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. 를 가져와서 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 표준 Visual Studio 서비스에 액세스할 수 있도록 하는,, 및로 변환할 수 있습니다.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. 메서드를 구현 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 하 여 명령 처리기를 인스턴스화합니다.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>완료 명령 처리기 구현
 문 완성은 키 입력에 의해 트리거되기 때문에 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 완료 세션을 트리거하고 커밋 및 해제 하는 키 입력을 수신 하 고 처리 하기 위해 인터페이스를 구현 해야 합니다.

#### <a name="to-implement-the-completion-command-handler"></a>완료 명령 처리기를 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 합니다 `TestCompletionCommandHandler` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. 명령을 전달 하는 다음 명령 처리기, 텍스트 뷰, 명령 처리기 공급자 (다양 한 서비스에 대 한 액세스 가능) 및 완료 세션의 전용 필드를 추가 합니다.

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. 텍스트 뷰 및 공급자 필드를 설정 하는 생성자를 추가 하 고 명령을 명령 체인에 추가 합니다.

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>명령을 함께 전달 하 여 메서드를 구현 합니다.

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드를 구현합니다. 이 메서드는 키 입력을 받을 때 다음 작업 중 하나를 수행 해야 합니다.

   - 문자를 버퍼에 쓴 다음 트리거 또는 필터 완료를 수행할 수 있습니다. (인쇄 문자는이 작업을 수행 합니다.)

   - 완료를 커밋하거나 버퍼에 문자를 쓸 수 없습니다. (공백, **탭**을 입력 하 고 완료 세션이 표시 될 때이 작업을 **입력** 합니다.)

   - 명령이 다음 처리기로 전달 되도록 허용 합니다. (다른 모든 명령)

     이 메서드는 UI를 표시할 수 있으므로를 호출 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> 하 여 자동화 컨텍스트에서 호출 되지 않는지 확인 합니다.

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. 이 코드는 완료 세션을 트리거하는 전용 메서드입니다.

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. 다음 예제는 이벤트에서 구독을 취소 하는 전용 메서드입니다 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> .

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 테스트 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

#### <a name="to-build-and-test-the-completiontest-solution"></a>이상 테스트 솔루션을 빌드 및 테스트 하려면

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만들고 "추가" 라는 단어를 포함 하는 텍스트를 입력 합니다.

4. "A"를 입력 하 고 "d"를 입력 하면 "더하기" 및 "적응"이 포함 된 목록이 표시 됩니다. 추가가 선택 되어 있는지 확인 합니다. 다른 "d"를 입력 하는 경우 목록에는 "더하기"만 포함 해야 합니다 .이는 현재 선택 되어 있습니다. **스페이스바**, **Tab**또는 **Enter** 키를 눌러 "추가"를 커밋하거나 Esc 키 또는 다른 키를 입력 하 여 목록을 해제할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
