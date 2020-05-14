---
title: '연습: 명령문 표시 완료 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697407"
---
# <a name="walkthrough-display-statement-completion"></a>연습: 명령문 완성 표시
완료를 제공할 식별자를 정의한 다음 완료 세션을 트리거하여 언어 기반 문 완성을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 문 완성을 정의하고, 사용자 고유의 파일 이름 확장자 및 콘텐츠 유형을 정의한 다음 해당 형식에 대한 완료를 표시할 수 있습니다. 또는 기존 콘텐츠 유형(예: "일반 텍스트")에 대한 완료를 트리거할 수 있습니다. 이 연습에서는 텍스트 파일의 콘텐츠 유형인 "일반 텍스트" 콘텐츠 형식에 대해 문 완성을 트리거하는 방법을 보여 주며, 이 연습에서는 "일반 텍스트" 콘텐츠 형식에 대해 문 완성을 트리거하는 방법을 보여 주며, 이 연습에서는 텍스트 파일의 콘텐츠 형식입니다. "텍스트" 콘텐츠 형식은 코드 및 XML 파일을 포함한 다른 모든 콘텐츠 형식의 상위 항목입니다.

 문 완성은 일반적으로 특정 문자(예: "using")와 같은 식별자의 시작 부분을 입력하여 트리거됩니다. 일반적으로 **스페이스바**, **탭**또는 **입력** 키를 눌러 선택을 커밋하면 해제됩니다. 키 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 입력(인터페이스)에 대한 명령 처리기와 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 인터페이스를 구현하는 처리기 공급자를 사용하여 문자를 입력할 때 트리거되는 IntelliSense 기능을 구현할 수 있습니다. 완료에 참여하는 식별자 목록인 완료 소스를 만들려면 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 인터페이스와 완료 소스 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> 공급자(인터페이스)를 구현합니다. 공급자는 MEF(관리되는 확장성 프레임워크) 구성 요소 부분입니다. 소스 및 컨트롤러 클래스를 내보내고 서비스 및 브로커를 가져오는 등의 업무를 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>담당합니다(예: 텍스트 버퍼에서 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>탐색을 활성화하는 는 ) 및 완료 세션을 트리거하는 .를 담당합니다.

 이 연습에서는 하드 코딩된 식별자 집합에 대해 문 완성을 구현하는 방법을 보여 주며 이 연습에서는 전체 구현에서 언어 서비스 및 언어 문서는 해당 콘텐츠를 제공할 책임이 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `CompletionTest`이름을 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가하고 **CopyLocal이** 다음과 같은 `false`지 확인합니다.

     마이크로소프트.비주얼스튜디오.에디터

     Microsoft.VisualStudio.Language.Intellisense

     마이크로소프트.비주얼스튜디오.올레.인터롭

     마이크로소프트.비주얼 스튜디오.쉘.15.0

     마이크로소프트.비주얼스튜디오.쉘.불변.10.0

     마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭

## <a name="implement-the-completion-source"></a>완료 소스 구현
 완료 소스는 식별자의 첫 번째 문자와 같이 사용자가 완료 트리거를 입력할 때 식별자 집합을 수집하고 완료 창에 콘텐츠를 추가합니다. 이 예제에서는 식별자와 해당 설명이 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 메서드에서 하드 코딩됩니다. 대부분의 실제 사용에서 언어의 파서를 사용하여 토큰을 사용하여 완료 목록을 채웁니다.

### <a name="to-implement-the-completion-source"></a>완료 소스를 구현하려면

1. 클래스 파일을 추가하고 이름을 `TestCompletionSource`로 지정합니다.

2. 이러한 가져오기를 추가합니다.

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. 다음을 `TestCompletionSource` 구현할 수 있도록 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>클래스 선언을 수정합니다.

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. 원본 공급자, 텍스트 버퍼 및 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 개체 목록(완료 세션에 참여할 식별자에 해당)에 대한 개인 필드를 추가합니다.

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. 소스 공급자 및 버퍼를 설정하는 생성자 추가합니다. 클래스는 `TestCompletionSourceProvider` 이후 단계에서 정의됩니다.

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. 컨텍스트에서 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> 제공할 완료를 포함하는 완료 집합을 추가하여 메서드를 구현합니다. 각 완료 집합에는 <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> 완료 집합이 포함되어 있으며 완료 창의 탭에 해당합니다. (시각적 기본 프로젝트에서 완료 창 탭은 **공통** 및 **모두입니다.)** 메서드는 `FindTokenSpanAtPosition` 다음 단계에서 정의됩니다.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. 다음 메서드는 커서의 위치에서 현재 단어를 찾는 데 사용됩니다.

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. 메서드를 `Dispose()` 구현합니다.

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>완료 소스 공급자 구현
 완료 소스 공급자는 완료 소스를 인스턴스화하는 MEF 구성 요소 부분입니다.

### <a name="to-implement-the-completion-source-provider"></a>완료 소스 공급자를 구현하려면

1. 을 구현하는 `TestCompletionSourceProvider` 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>추가합니다. 이 클래스를 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "일반 텍스트"와 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "테스트 완료"로 내보냅니다.

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>을 가져오면 완료 소스에서 현재 단어를 찾습니다.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. 완료 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> 소스를 인스턴스화하는 메서드를 구현합니다.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자 구현
 완료 명령 처리기 공급자는 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>텍스트 보기 만들기 이벤트를 수신하는 및 Visual Studio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>셸의 명령 체인에 명령을 추가할 수 있는 뷰를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>에서 로 변환하는 에서 파생됩니다. 이 클래스는 MEF 내보내기이므로 명령 처리기 자체에 필요한 서비스를 가져오는 데도 사용할 수 있습니다.

#### <a name="to-implement-the-completion-command-handler-provider"></a>완료 명령 처리기 공급자를 구현하려면

1. 라는 파일을 `TestCompletionCommandHandler`추가합니다.

2. 지시문을 사용하여 다음을 추가합니다.

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. 을 구현하는 `TestCompletionHandlerProvider` 클래스를 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>추가합니다. "토큰 완료 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 처리기", "일반 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 텍스트"및 의 를 <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> 사용 <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>하 으로이 클래스를 내보냅니다.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>을 가져오면 에서 에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 로 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 변환할 수 있습니다.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. 메서드를 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 구현하여 명령 처리기를 인스턴스화합니다.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>완료 명령 처리기 구현
 명령문 완성은 키 입력에 의해 트리거되므로 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 완료 세션을 트리거, 커밋 및 해제하는 키 입력을 수신하고 처리하는 인터페이스를 구현해야 합니다.

#### <a name="to-implement-the-completion-command-handler"></a>완료 명령 처리기를 구현하려면

1. 다음을 구현하는 `TestCompletionCommandHandler` 클래스를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>추가합니다.

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. 다음 명령 처리기(명령을 전달하는 경우), 텍스트 보기, 명령 처리기 공급자(다양한 서비스에 액세스할 수 있음) 및 완료 세션에 대한 개인 필드를 추가합니다.

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. 텍스트 보기 및 공급자 필드를 설정 하는 생성자 추가 하 고 명령 체인에 명령을 추가 합니다.

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. 명령을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 따라 전달하여 메서드를 구현합니다.

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드를 구현합니다. 이 메서드가 키 입력을 수신하는 경우 다음 중 하나를 수행해야 합니다.

   - 문자를 버퍼에 쓸 수 있도록 허용한 다음 완료를 트리거하거나 필터링합니다. (인쇄 문자는이 작업을 수행합니다.)

   - 완료를 커밋하지만 버퍼에 문자를 쓸 수 없습니다. (완료 세션이 표시될 때 공백, **탭**및 **Enter이** 작업을 수행합니다.)

   - 명령을 다음 처리기에 전달할 수 있도록 허용합니다. (다른 모든 명령))

     이 메서드는 UI를 <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> 표시할 수 있으므로 자동화 컨텍스트에서 호출되지 않도록 호출합니다.

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. 이 코드는 완료 세션을 트리거하는 전용 메서드입니다.

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. 다음 예제는 이벤트에서 구독을 취소하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> 개인 메서드입니다.

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 CompleteTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

#### <a name="to-build-and-test-the-completiontest-solution"></a>CompleteTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 "add"라는 단어가 포함된 텍스트를 입력합니다.

4. 먼저 "a"를 입력한 다음 "d"를 입력하면 "추가" 및 "적응"이 포함된 목록이 나타납니다. 추가가 선택됩니다. 다른 "d"를 입력하면 목록에 "추가"만 포함되어야 하며 이제 선택됩니다. **스페이스바**, **탭**또는 **입력** 키를 눌러 "추가"를 커밋하거나 Esc 또는 기타 키를 입력하여 목록을 해제할 수 있습니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
