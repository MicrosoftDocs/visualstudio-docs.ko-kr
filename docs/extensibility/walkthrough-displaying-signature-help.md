---
title: '연습: 서명 도움말 표시 | Microsoft Docs'
description: 이 연습을 사용 하 여 텍스트 콘텐츠 형식에 대 한 시그니처 도움말을 표시 하는 방법을 알아봅니다. 서명 도움말 도구 설명에 메서드의 시그니처를 표시 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6ffa2a0e646c11cb56d08ef91e3d7a4b9af7572
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217504"
---
# <a name="walkthrough-display-signature-help"></a>연습: 서명 도움말 표시
서명 도움말 ( *매개 변수 정보* 라고도 함)은 사용자가 매개 변수 목록 시작 문자 (일반적으로 여는 괄호)를 입력 하는 경우 도구 설명에 메서드의 시그니처를 표시 합니다. 매개 변수 및 매개 변수 구분 기호 (일반적으로 쉼표)가 입력 되 면 도구 설명이 업데이트 되어 다음 매개 변수가 굵게 표시 됩니다. 다음과 같은 방법으로 시그니처 도움말을 정의할 수 있습니다. 언어 서비스 컨텍스트에서 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 해당 형식에 대 한 서명 도움말을 표시 하거나 기존 콘텐츠 형식 (예: "텍스트")에 대 한 서명 도움말을 표시 합니다. 이 연습에서는 "text" 콘텐츠 형식에 대 한 시그니처 도움말을 표시 하는 방법을 보여 줍니다.

 서명 도움말은 일반적으로 특정 문자 (예: "(") (여는 괄호)를 입력 하 여 트리거되고 다른 문자 (예: ")" (닫는 괄호)를 입력 하 여 해제 됩니다. 문자를 입력 하 여 트리거되는 IntelliSense 기능은 키 입력 ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스) 및 인터페이스를 구현 하는 처리기 공급자에 대해 명령 처리기를 사용 하 여 구현할 수 있습니다 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . 서명 도움말에 참여 하는 서명 목록에 해당 하는 서명 도움말 원본을 만들려면 인터페이스 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 와 인터페이스를 실행 하는 소스 공급자를 구현 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> . 공급자는 MEF (Managed Extensibility Framework) 구성 요소 부분으로, 소스 및 컨트롤러 클래스를 내보내고 서비스와 broker를 가져옵니다. 예를 들어, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 텍스트 버퍼에서 탐색할 수 있는 및 서명 도움말 세션을 트리거하는를 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> .

 이 연습에서는 하드 코드 된 식별자 집합에 대 한 시그니처 도움말을 설정 하는 방법을 보여 줍니다. 모든 구현에서이 언어는 해당 콘텐츠를 제공 합니다.

## <a name="prerequisites"></a>필수 조건
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트** 를 차례로 선택 합니다.) 솔루션 이름을로 `SignatureHelpTest` 합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

4. 프로젝트에 다음 참조를 추가 하 고 **CopyLocal** 이로 설정 되었는지 확인 합니다 `false` .

     VisualStudio

     Microsoft.VisualStudio.Language.Intellisense

     VisualStudio.

     VisualStudio. 14.0

     VisualStudio입니다.

## <a name="implement-signature-help-signatures-and-parameters"></a>서명 도움말 서명 및 매개 변수 구현
 서명 도움말 소스는을 구현 하는 서명을 기반으로 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> 하며, 각각은를 구현 하는 매개 변수를 포함 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 합니다. 전체 구현에서이 정보는 언어 설명서에서 확인할 수 있지만이 예제에서는 서명이 하드 코드 되어 있습니다.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>서명 도움말 서명 및 매개 변수를 구현 하려면

1. 클래스 파일을 추가하고 이름을 `SignatureHelpSource`로 지정합니다.

2. 다음 가져오기를 추가합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. 을 구현 하는 라는 클래스를 추가 `TestParameter` <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. 모든 속성을 설정 하는 생성자를 추가 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. 의 속성을 추가 <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. 을 구현 하는 라는 클래스를 추가 `TestSignature` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. 일부 전용 필드를 추가 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. 필드를 설정 하 고 이벤트를 구독 하는 생성자를 추가 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. 이벤트를 선언 `CurrentParameterChanged` 합니다. 이 이벤트는 사용자가 시그니처의 매개 변수 중 하나를 채울 때 발생 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. 속성 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> `CurrentParameterChanged` 값이 변경 될 때 이벤트가 발생 하도록 속성을 구현 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. 이벤트를 발생 시키는 메서드를 추가 `CurrentParameterChanged` 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. 의 쉼표 수를 시그니처의 쉼표 수와 비교 하 여 현재 매개 변수를 계산 하는 메서드를 추가 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>메서드를 호출 하는 이벤트에 대 한 이벤트 처리기를 추가 `ComputeCurrentParameter()` 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> 속성을 구현합니다. 이 속성에는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 서명이 적용 되는 버퍼의 텍스트 범위에 해당 하는이 포함 됩니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. 다른 매개 변수를 구현 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>서명 도움말 소스 구현
 서명 도움말 원본은 정보를 제공 하는 서명 집합입니다.

#### <a name="to-implement-the-signature-help-source"></a>서명 도움말 원본을 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 `TestSignatureHelpSource` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. 텍스트 버퍼에 대 한 참조를 추가 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. 텍스트 버퍼 및 서명 도움말 소스 공급자를 설정 하는 생성자를 추가 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> 메서드를 구현합니다. 이 예제에서는 서명이 하드 코드 되지만 전체 구현에서는 언어 설명서에서이 정보를 얻을 수 있습니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. 도우미 메서드는 설명 `CreateSignature()` 목적 으로만 제공 됩니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> 메서드를 구현합니다. 이 예제에는 두 개의 매개 변수가 있는 시그니처가 있습니다. 따라서이 메서드는 필요 하지 않습니다. 둘 이상의 시그니처 도움말 소스를 사용할 수 있는 완전 한 구현에서는이 메서드를 사용 하 여 우선 순위가 가장 높은 서명 도움말 소스가 일치 하는 시그니처를 제공할 수 있는지 여부를 결정 합니다. 사용할 수 없는 경우이 메서드는 null을 반환 하 고, 다음으로 높은 우선 순위 소스가 일치 하는 항목을 제공 하도록 요청 됩니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. 메서드를 구현 합니다 `Dispose()` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>서명 도움말 소스 공급자 구현
 서명 도움말 소스 공급자는 MEF (Managed Extensibility Framework) 구성 요소 파트를 내보내고 서명 도움말 원본을 인스턴스화하는 역할을 담당 합니다.

#### <a name="to-implement-the-signature-help-source-provider"></a>서명 도움말 소스 공급자를 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 하 `TestSignatureHelpSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> 고 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text"의 및 <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default"를 사용 하 여 내보냅니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A>를 인스턴스화하여 구현 `TestSignatureHelpSource` 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>명령 처리기 구현
 서명 도움말은 일반적으로 여는 괄호 "(" 문자, 닫는 괄호 ")" 문자로 인해 트리거됩니다. 을 실행 하 여 이러한 키 입력을 처리 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 고, 알려진 메서드 이름 앞에 여는 괄호 문자를 받을 때 서명 도움말 세션을 트리거하고 닫는 괄호 문자를 받을 때 세션을 닫을 수 있습니다.

#### <a name="to-implement-the-command-handler"></a>명령 처리기를 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 `TestSignatureHelpCommand` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. 명령 처리기를 명령 처리기 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 체인에 추가할 수 있는 어댑터에 대 한 전용 필드, 텍스트 뷰, 서명 도움말 브로커 및 세션, a 및 다음을 추가 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. 생성자를 추가 하 여 이러한 필드를 초기화 하 고 명령 필터 체인에 명령 필터를 추가 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. 메서드를 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 하 여 명령 필터에서 알려진 메서드 이름 중 하나 뒤에 여는 괄호 "(" 문자를 받고, 세션이 아직 활성 상태인 동안 닫는 괄호 ")" 문자를 받을 때 세션을 해제할 때 서명 도움말 세션을 트리거합니다. 모든 경우에 명령이 전달 됩니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>항상 명령을 전달 하도록 메서드를 구현 합니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>서명 도움말 명령 공급자 구현
 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>텍스트 뷰를 만들 때 명령 처리기를 인스턴스화하기 위해를 구현 하 여 서명 도움말 명령을 제공할 수 있습니다.

### <a name="to-implement-the-signature-help-command-provider"></a>서명 도움말 명령 공급자를 구현 하려면

1. 을 구현 하는 라는 클래스를 추가 하 `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 고, 및를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. ( <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 개체를 가져오는 데 사용 됨 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (현재 단어를 찾는 데 사용 됨) 및 <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (서명 도움말 세션을 트리거하기 위해)을 가져옵니다.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A>를 인스턴스화하여 메서드를 구현 합니다 `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 서명 Helptest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>서명 도움말 테스트 솔루션을 빌드 및 테스트 하려면

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만들고 단어 "추가"와 여는 괄호를 포함 하는 텍스트를 입력 합니다.

4. 여는 괄호를 입력 한 후에는 메서드에 대 한 두 서명 목록을 표시 하는 도구 설명이 표시 됩니다 `add()` .

## <a name="see-also"></a>참고 항목
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
