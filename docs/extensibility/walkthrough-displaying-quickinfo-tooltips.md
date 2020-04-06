---
title: '연습: 퀵정보 도구 설명 표시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697431"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>연습: 빠른 정보 표시 도구 설명
QuickInfo는 사용자가 메서드 이름 위에 포인터를 이동할 때 메서드 서명 및 설명을 표시하는 IntelliSense 기능입니다. QuickInfo 설명을 제공할 식별자를 정의한 다음 콘텐츠를 표시할 도구 설명을 만들어 QuickInfo와 같은 언어 기반 기능을 구현할 수 있습니다. 언어 서비스의 컨텍스트에서 QuickInfo를 정의하거나 사용자 고유의 파일 이름 확장자 및 콘텐츠 유형을 정의하고 해당 유형에 대해 QuickInfo를 표시하거나 기존 콘텐츠 유형(예: "텍스트")에 대해 QuickInfo를 표시할 수 있습니다. 이 연습에서는 "텍스트" 콘텐츠 유형에 대해 QuickInfo를 표시하는 방법을 보여 주었습니다.

 이 연습의 QuickInfo 예제에서는 사용자가 메서드 이름 위로 포인터를 이동할 때 도구 설명이 표시됩니다. 이 디자인은 다음 네 가지 인터페이스를 구현해야 합니다.

- 소스 인터페이스

- 소스 공급자 인터페이스

- 컨트롤러 인터페이스

- 컨트롤러 공급자 인터페이스

  원본 및 컨트롤러 공급자는 MEF(관리되는 확장성 프레임워크) 구성 요소 부품이며 소스 및 컨트롤러 클래스를 내보내고 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>도구 설명 텍스트 버퍼를 만드는 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>및 QuickInfo 세션을 트리거하는 .와 같은 서비스 및 브로커를 가져옵니다.

  이 예제에서 QuickInfo 소스는 메서드 이름 및 설명의 하드 코딩된 목록을 사용하지만 전체 구현에서는 언어 서비스 및 언어 설명서가 해당 콘텐츠를 제공합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치할 필요가 없습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `QuickInfoTest`이름을 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-the-quickinfo-source"></a>퀵정보 소스 구현
 QuickInfo 소스는 식별자 집합및 해당 설명 집합을 수집하고 식별자 중 하나가 발생할 때 도구 설명 텍스트 버퍼에 콘텐츠를 추가하는 것을 담당합니다. 이 예제에서는 식별자와 해당 설명이 소스 생성자에 추가됩니다.

#### <a name="to-implement-the-quickinfo-source"></a>QuickInfo 소스를 구현하려면

1. 클래스 파일을 추가하고 이름을 `TestQuickInfoSource`로 지정합니다.

2. *Microsoft.VisualStudio.Language.IntelliSense에*대한 참조를 추가합니다.

3. 다음 가져오기를 추가합니다.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. 을 구현하는 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>선언하고 `TestQuickInfoSource`이름을 지정합니다.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. QuickInfo 소스 공급자, 텍스트 버퍼 및 메서드 이름 및 메서드 시그니처 집합에 대한 필드를 추가합니다. 이 예제에서는 메서드 이름 및 서명생성자에서 `TestQuickInfoSource` 초기화 됩니다.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. QuickInfo 소스 공급자 및 텍스트 버퍼를 설정 하 고 메서드 이름 및 메서드 서명 및 설명 집합을 채우는 생성자 추가 합니다.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> 메서드를 구현합니다. 이 예제에서 메서드는 현재 단어 또는 커서가 줄 또는 텍스트 버퍼의 끝에 있는 경우 이전 단어를 찾습니다. 단어가 메서드 이름 중 하나인 경우 해당 메서드 이름에 대한 설명이 QuickInfo 콘텐츠에 추가됩니다.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. 또한 Dispose() 메서드를 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> 구현해야 합니다. <xref:System.IDisposable>

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>QuickInfo 소스 공급자 구현
 QuickInfo 소스의 공급자는 주로 MEF 구성 요소 부분으로 자신을 내보내고 QuickInfo 소스를 인스턴스화하는 역할을 합니다. MEF 구성 요소 부품이기 때문에 다른 MEF 구성 요소 부품을 가져올 수 있습니다.

#### <a name="to-implement-a-quickinfo-source-provider"></a>QuickInfo 소스 공급자를 구현하려면

1. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>구현하는 이름의 `TestQuickInfoSourceProvider` QuickInfo 소스 공급자를 선언하고 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo 원본", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "기본값"의 및 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "텍스트"를 사용하여 내보냅니다.

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. 두 편집기 <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> 서비스를 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>가져오고 `TestQuickInfoSourceProvider`의 속성으로 .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. 구현하여 <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> 새 `TestQuickInfoSource`을 반환합니다.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>퀵정보 컨트롤러 구현
 QuickInfo 컨트롤러는 QuickInfo가 표시되는 시기를 결정합니다. 이 예제에서 QuickInfo는 포인터가 메서드 이름 중 하나에 해당하는 단어 위에 있을 때 나타납니다. QuickInfo 컨트롤러는 QuickInfo 세션을 트리거하는 마우스 호버 이벤트 처리기를 구현합니다.

### <a name="to-implement-a-quickinfo-controller"></a>QuickInfo 컨트롤러를 구현하려면

1. 을 구현하는 클래스를 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>선언하고 `TestQuickInfoController`이름을 지정합니다.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. 텍스트 보기에 대 한 개인 필드, 텍스트 보기에 표시 된 텍스트 버퍼, QuickInfo 세션 및 QuickInfo 컨트롤러 공급자를 추가 합니다.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. 필드를 설정하고 마우스 호버 이벤트 처리기를 추가하는 생성기를 추가합니다.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. QuickInfo 세션을 트리거하는 마우스 호버 이벤트 처리기를 추가합니다.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. 컨트롤러가 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> 텍스트 보기에서 분리될 때 마우스 호버 이벤트 처리기를 제거되도록 메서드를 구현합니다.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. 이 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> 예제의 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> 빈 메서드로 메서드와 메서드를 구현합니다.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러 공급자 구현
 QuickInfo 컨트롤러의 공급자는 주로 MEF 구성 요소 부분으로 자신을 내보내고 QuickInfo 컨트롤러를 인스턴스화하는 역할을 합니다. MEF 구성 요소 부품이기 때문에 다른 MEF 구성 요소 부품을 가져올 수 있습니다.

### <a name="to-implement-the-quickinfo-controller-provider"></a>QuickInfo 컨트롤러 공급자를 구현하려면

1. 을 `TestQuickInfoControllerProvider` 구현하는 <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>클래스를 선언하고 "ToolTip <xref:Microsoft.VisualStudio.Utilities.NameAttribute> QuickInfo 컨트롤러"와 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "텍스트"를 사용하여 내보냅니다.

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>를 속성으로 가져옵니다.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. QuickInfo <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> 컨트롤러를 인스턴스화하여 메서드를 구현합니다.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 QuickInfoTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>QuickInfoTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 "추가" 및 "빼기"라는 단어가 포함된 텍스트를 입력합니다.

4. 포인터를 "추가" 발생 중 하나로 이동합니다. 메서드의 서명과 설명이 `add` 표시되어야 합니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
