---
title: '연습: QuickInfo 도구 설명 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841834"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>연습: QuickInfo 도구 설명 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo는 사용자가 포인터를 메서드 이름 위로 이동할 때 메서드 시그니처와 설명을 표시 하는 IntelliSense 기능입니다. QuickInfo 설명을 제공 하려는 식별자를 정의 하 고 콘텐츠를 표시할 도구 설명을 만들어 QuickInfo와 같은 언어 기반 기능을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 QuickInfo를 정의 하거나 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 해당 형식에 대해서만 QuickInfo를 표시 하거나 기존 콘텐츠 형식 (예: "텍스트")에 대 한 QuickInfo를 표시할 수 있습니다. 이 연습에서는 "text" 콘텐츠 형식에 대해 QuickInfo를 표시 하는 방법을 보여 줍니다.  
  
 이 연습의 QuickInfo 예제에서는 사용자가 포인터를 메서드 이름 위로 이동할 때 도구 설명을 표시 합니다. 이 디자인에서는 다음 네 가지 인터페이스를 구현 해야 합니다.  
  
- 원본 인터페이스  
  
- 원본 공급자 인터페이스  
  
- 컨트롤러 인터페이스  
  
- 컨트롤러 공급자 인터페이스  
  
  소스 및 컨트롤러 공급자는 MEF (Managed Extensibility Framework) 구성 요소 부분으로, 소스 및 컨트롤러 클래스를 내보내고 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , 도구 설명 텍스트 버퍼를 만드는, QuickInfo 세션을 트리거하는 등의 서비스와 broker를 가져옵니다 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> .  
  
  이 예제에서는 QuickInfo 소스가 하드 코드 된 메서드 이름 및 설명 목록을 사용 하지만, 전체 구현에서는 언어 서비스 및 언어 설명서에서 해당 콘텐츠를 제공 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="creating-a-mef-project"></a>MEF 프로젝트 만들기  
  
#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면  
  
1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `QuickInfoTest` 합니다.  
  
2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.  
  
3. 기존 클래스 파일을 삭제합니다.  
  
## <a name="implementing-the-quickinfo-source"></a>QuickInfo 원본 구현  
 QuickInfo 원본은 식별자의 집합을 수집 하 고 식별자 중 하나를 발견 하면 도구 설명 텍스트 버퍼에 콘텐츠를 추가 합니다. 이 예제에서는 식별자와 해당 설명이 소스 생성자에 추가 됩니다.  
  
#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo source를 구현 하려면  
  
1. 클래스 파일을 추가하고 이름을 `TestQuickInfoSource`로 지정합니다.  
  
2. VisualStudio에 대 한 참조를 추가 합니다.  
  
3. 다음 가져오기를 추가합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. 을 구현 하는 클래스를 선언 하 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> 고 이름을로 `TestQuickInfoSource` 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. QuickInfo 원본 공급자, 텍스트 버퍼 및 메서드 이름 및 메서드 시그니처의 집합에 대 한 필드를 추가 합니다. 이 예제에서 메서드 이름 및 시그니처는 생성자에서 초기화 됩니다 `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. QuickInfo 원본 공급자와 텍스트 버퍼를 설정 하는 생성자를 추가 하 고 메서드 이름 및 메서드 시그니처와 설명의 집합을 채웁니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 메서드를 구현합니다. 이 예제에서 메서드는 현재 단어를 찾거나 커서가 줄 또는 텍스트 버퍼의 끝에 있는 경우 이전 단어를 찾습니다. 단어가 메서드 이름 중 하나 이면 해당 메서드 이름에 대 한 설명이 QuickInfo 내용에 추가 됩니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. 또한를 구현 하므로 Dispose () 메서드를 구현 해야 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> 합니다 <xref:System.IDisposable> .  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>QuickInfo 원본 공급자 구현  
 QuickInfo 원본 공급자는 주로 MEF 구성 요소 파트로 내보내고 QuickInfo 원본을 인스턴스화하는 데 사용 됩니다. MEF 구성 요소 부분 이므로 다른 MEF 구성 요소 부분을 가져올 수 있습니다.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo 원본 공급자를 구현 하려면  
  
1. 을 구현 하는 라는 QuickInfo 소스 공급자를 선언 하 `TestQuickInfoSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> 고, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Source", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> Before = "default" 및 "text"의를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> .  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. 두 개의 편집기 서비스 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 와 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 를의 속성으로 가져옵니다 `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A>새를 반환 하려면를 구현 `TestQuickInfoSource` 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>QuickInfo 컨트롤러 구현  
 QuickInfo 컨트롤러는 QuickInfo를 표시 해야 하는 시기를 결정 합니다. 이 예제에서 메서드 이름 중 하나에 해당 하는 단어 위에 포인터를 놓으면 QuickInfo이 표시 됩니다. QuickInfo 컨트롤러는 QuickInfo 세션을 트리거하는 마우스 호버 이벤트 처리기를 구현 합니다.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo 컨트롤러를 구현 하려면  
  
1. 을 구현 하는 클래스를 선언 하 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> 고 이름을로 `TestQuickInfoController` 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. 텍스트 뷰의 전용 필드, 텍스트 보기에 표시 되는 텍스트 버퍼, QuickInfo 세션 및 QuickInfo controller 공급자를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. 필드를 설정 하 고 마우스 호버 이벤트 처리기를 추가 하는 생성자를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. QuickInfo 세션을 트리거하는 마우스 호버 이벤트 처리기를 추가 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A>컨트롤러가 텍스트 뷰에서 분리 될 때 마우스 호버 이벤트 처리기가 제거 되도록 메서드를 구현 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A>메서드 및 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> 메서드를이 예제에 대 한 빈 메서드로 구현 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러 공급자 구현  
 QuickInfo 컨트롤러의 공급자는 주로 MEF 구성 요소 파트로 내보내고 QuickInfo 컨트롤러를 인스턴스화하는 데 사용 됩니다. MEF 구성 요소 부분 이므로 다른 MEF 구성 요소 부분을 가져올 수 있습니다.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러 공급자를 구현 하려면  
  
1. `TestQuickInfoControllerProvider`을 구현 하는 클래스를 선언 하 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> 고, <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" 및 "text"의를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> .  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>를 속성으로 가져옵니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A>QuickInfo 컨트롤러를 인스턴스화하여 메서드를 구현 합니다.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
 이 코드를 테스트 하려면 QuickInfoTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest 솔루션을 빌드하고 테스트 하려면  
  
1. 솔루션을 빌드합니다.  
  
2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 인스턴스화됩니다.  
  
3. 텍스트 파일을 만들고 "add" 및 "뺄셈" 이라는 단어를 포함 하는 텍스트를 입력 합니다.  
  
4. "추가" 항목 중 하나 위로 포인터를 이동 합니다. 메서드의 시그니처와 설명이 `add` 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
