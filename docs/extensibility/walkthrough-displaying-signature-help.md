---
title: '연습: 서명 도움말 표시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697426"
---
# <a name="walkthrough-display-signature-help"></a>연습: 서명 도움말 표시
서명 도움말(매개 *변수 정보라고도*함)은 사용자가 매개 변수 목록 시작 문자(일반적으로 여는 괄호)를 입력할 때 도구 설명에 메서드의 서명을 표시합니다. 매개 변수 및 매개 변수 구분 기호(일반적으로 쉼표)가 입력되면 도구 설명이 업데이트되어 다음 매개 변수를 굵게 표시합니다. 언어 서비스의 컨텍스트에서 사용자 고유의 파일 이름 확장자 및 콘텐츠 유형을 정의하고 해당 유형에 대한 서명 도움말을 표시하거나 기존 콘텐츠 유형에 대한 서명 도움말(예: "텍스트")을 표시할 수 있습니다. 이 연습에서는 "텍스트" 콘텐츠 유형에 대한 서명 도움말을 표시하는 방법을 보여 줍니다.

 서명 도움말은 일반적으로 특정 문자(예: "(괄호 열기)를 입력하고 다른 문자(예: ")"(괄호 닫기)를 입력하여 해제됩니다. 문자를 입력하여 트리거되는 IntelliSense 기능은 키 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 입력(인터페이스)에 대한 명령 처리기와 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 인터페이스를 구현하는 처리기 공급자를 사용하여 구현할 수 있습니다. 서명 도움말에 참여하는 서명 목록인 서명 도움말 소스를 만들려면 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 인터페이스와 인터페이스를 실행하는 원본 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 공급자를 구현합니다. 공급자는 MEF(관리되는 확장성 프레임워크) 구성 요소 부품이며 소스 및 컨트롤러 클래스를 내보내고 서비스 및 브로커를 가져오는 작업(예: 텍스트 버퍼에서 탐색할 수 있는 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.) 및 서명 도움말 세션을 트리거하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>.를 담당합니다.

 이 연습에서는 하드 코딩된 식별자 집합에 대해 서명 도움말을 설정하는 방법을 보여 줍니다. 전체 구현에서 언어는 해당 콘텐츠를 제공할 책임이 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `SignatureHelpTest`이름을 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가하고 **CopyLocal이** 다음과 같은지 `false`확인합니다.

     마이크로소프트.비주얼스튜디오.에디터

     Microsoft.VisualStudio.Language.Intellisense

     마이크로소프트.비주얼스튜디오.올레.인터롭

     마이크로소프트.비주얼 스튜디오.쉘.14.0

     마이크로소프트.비주얼 스튜디오.텍스트 관리자.인터롭

## <a name="implement-signature-help-signatures-and-parameters"></a>서명 도움말 서명 및 매개 변수 구현
 서명 도움말 소스는 구현하는 서명을 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>기반으로 하며, 각 서명에는 을 구현하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>매개 변수가 포함되어 있습니다. 전체 구현에서는 이 정보는 언어 설명서에서 가져오지만 이 예제에서는 서명이 하드 코딩됩니다.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>서명 도움말 서명 및 매개 변수를 구현하려면

1. 클래스 파일을 추가하고 이름을 `SignatureHelpSource`로 지정합니다.

2. 다음 가져오기를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. 을 구현하는 `TestParameter` 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. 모든 속성을 설정하는 생성자 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. 의 속성을 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. 을 구현하는 `TestSignature` 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. 일부 개인 필드를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. 필드를 설정하고 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트를 구독하는 생성기를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. 이벤트를 `CurrentParameterChanged` 선언합니다. 이 이벤트는 사용자가 서명의 매개 변수 중 하나를 채울 때 발생합니다.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> 속성 값이 변경 될 `CurrentParameterChanged` 때 이벤트를 발생 되도록 속성을 구현 합니다.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. 이벤트를 발생 시키는 `CurrentParameterChanged` 메서드를 추가 합니다.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. 의 쉼표 수를 서명의 쉼표 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 수와 비교하여 현재 매개 변수를 계산하는 메서드를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. 메서드를 호출 하는 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트에 대 `ComputeCurrentParameter()` 한 이벤트 처리기를 추가 합니다.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 속성을 구현합니다. 이 속성은 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 서명이 적용되는 버퍼의 텍스트 범위에 해당하는 을 보유합니다.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. 다른 매개 변수를 구현합니다.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>서명 도움말 소스 구현
 서명 도움말 소스는 정보를 제공하는 서명 집합입니다.

#### <a name="to-implement-the-signature-help-source"></a>서명 도움말 소스를 구현하려면

1. 을 구현하는 `TestSignatureHelpSource` 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. 텍스트 버퍼에 참조를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. 텍스트 버퍼와 서명 도움말 원본 공급자를 설정하는 생성자추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 메서드를 구현합니다. 이 예제에서는 서명이 하드 코딩되지만 전체 구현에서는 언어 설명서에서 이 정보를 얻을 수 있습니다.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. 도우미 메서드는 `CreateSignature()` 그림에 만 제공 됩니다.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 메서드를 구현합니다. 이 예제에서는 각각 두 개의 매개 변수가 있는 두 개의 서명만 있습니다. 따라서이 메서드는 필요 하지 않습니다. 두 개 이상의 서명 도움말 원본을 사용할 수 있는 전체 구현에서 이 메서드는 우선 순위가 가장 높은 서명 도움말 원본이 일치하는 서명을 제공할 수 있는지 여부를 결정하는 데 사용됩니다. 그렇지 않으면 메서드가 null을 반환하고 우선 순위가 가장 높은 소스가 일치 를 제공하라는 메시지가 표시됩니다.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. 메서드를 `Dispose()` 구현합니다.

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>서명 도움말 원본 공급자 구현
 서명 도움말 원본 공급자는 관리되는 확장성 프레임워크(MEF) 구성 요소 부품을 내보내고 서명 도움말 원본을 인스턴스화하는 역할을 합니다.

#### <a name="to-implement-the-signature-help-source-provider"></a>서명 도움말 원본 공급자를 구현하려면

1. 을 `TestSignatureHelpSourceProvider` 구현하는 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>클래스를 추가하고 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "텍스트"의 및 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "기본값"을 로 내보냅니다.

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. 을 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> 인스턴스화하여 구현합니다. `TestSignatureHelpSource`

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>명령 처리기 구현
 서명 도움말은 일반적으로 여는 괄호 "(" 문자)에 의해 트리거되고 닫는 괄호 ")" 문자에 의해 해제됩니다. 알려진 메서드 이름 앞에 오는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 여건 괄호 문자를 수신하고 닫는 괄호 문자를 받을 때 세션을 해제할 때 서명 도움말 세션을 트리거할 수 있도록 이러한 키 입력을 실행하여 이러한 키 입력을 처리할 수 있습니다.

#### <a name="to-implement-the-command-handler"></a>명령 처리기를 구현하려면

1. 을 구현하는 `TestSignatureHelpCommand` 클래스를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. 어댑터에 대한 개인 필드(명령 처리기 체인에 명령 처리기를 추가할 수 있음), 텍스트 보기, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>서명 도움말 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>브로커 및 세션, a 및 다음 에 대한 개인 필드를 추가합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. 생성자 추가를 추가하여 이러한 필드를 초기화하고 명령 필터 체인에 명령 필터를 추가합니다.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. 명령 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 필터가 알려진 메서드 이름 중 하나 후에 열린 괄호 "(" 문자)를 수신하고 세션이 여전히 활성 상태인 동안 닫는 괄호 ")" 문자를 수신할 때 세션을 해제하는 메서드를 구현합니다. 모든 경우에 명령이 전달됩니다.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. 항상 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 명령을 전달되도록 메서드를 구현합니다.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>서명 도움말 명령 공급자 구현
 텍스트 뷰를 만들 때 명령 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 처리기를 인스턴스화하는 을 구현하여 서명 도움말 명령을 제공할 수 있습니다.

### <a name="to-implement-the-signature-help-command-provider"></a>서명 도움말 명령 공급자를 구현하려면

1. `TestSignatureHelpController` 을 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 구현하고 로 내보내는 <xref:Microsoft.VisualStudio.Utilities.NameAttribute>클래스를 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>추가합니다. <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (개체를 가져오는 데 사용), (현재 단어를 찾는 데 사용) <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> 및 (서명 도움말 세션을 트리거하려면) 가져옵니다. <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. `TestSignatureCommandHandler`을 인스턴스화하여 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> 메서드를 구현합니다.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 SignatureHelpTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>SignatureHelpTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 "add" 와 여는 괄호가 포함된 텍스트를 입력합니다.

4. 여는 괄호를 입력한 후에는 메서드에 대한 두 서명 목록을 표시하는 도구 `add()` 설명이 표시됩니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
