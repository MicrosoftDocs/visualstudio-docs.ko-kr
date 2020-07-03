---
title: '연습: 텍스트 뷰 사용자 지정 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7a62ee2b55bf2b56ae1d8e28fc1910ed444c29
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904939"
---
# <a name="walkthrough-customize-the-text-view"></a>연습: 텍스트 뷰 사용자 지정
편집기 형식 맵에서 다음 속성을 수정 하 여 텍스트 뷰를 사용자 지정할 수 있습니다.

- 표시기 여백

- 삽입 캐럿

- 캐럿 덮어쓰기

- 선택한 텍스트

- 선택한 비활성 텍스트 (즉, 포커스를 잃은 선택 된 텍스트)

- 표시 공백

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `ViewPropertyTest` 합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-the-content-type"></a>콘텐츠 형식 정의

1. 클래스 파일을 추가하고 이름을 `ViewPropertyModifier`로 지정합니다.

2. 다음 `using` 지시문을 추가합니다.

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. `TestViewCreationListener`에서 상속 되는 이라는 클래스를 선언 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 합니다. 다음 특성을 사용 하 여이 클래스를 내보냅니다.

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>이 수신기가 적용 되는 콘텐츠 형식을 지정 합니다.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>이 수신기의 역할을 지정 하는입니다.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. 이 클래스에서을 가져옵니다 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>보기 속성 변경

1. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>뷰를 열 때 뷰 속성이 변경 되도록 메서드를 설정 합니다. 변경 하려면 먼저 <xref:System.Windows.ResourceDictionary> 찾으려는 뷰의 측면에 해당 하는을 찾습니다. 그런 다음 리소스 사전에서 적절 한 속성을 변경 하 고 속성을 설정 합니다. <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> 속성을 설정 하기 전에 메서드를 호출 하 고 속성을 설정한 후에 메서드를 호출 하 여 메서드에 대 한 호출을 일괄 처리 합니다 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> .

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트

1. 솔루션을 빌드합니다.

     디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

2. 텍스트 파일을 만들고 일부 텍스트를 입력합니다.

    - 삽입 캐럿은 자홍 이어야 하며 overwrite 캐럿은 옥색 이어야 합니다.

    - 텍스트 보기의 왼쪽에 있는 표시기 여백은 연한 녹색 이어야 합니다.

3. 입력한 텍스트를 선택합니다. 선택한 텍스트의 색은 연한 분홍 이어야 합니다.

4. 텍스트를 선택 하는 동안 텍스트 창 외부의 아무 곳 이나 클릭 합니다. 선택한 텍스트의 색은 짙은 분홍색 이어야 합니다.

5. 표시 되는 공백을 설정 합니다. **편집** 메뉴에서 **고급** 을 가리킨 다음 **공백 보기**를 클릭 합니다. 텍스트에 일부 탭을 입력 합니다. 탭을 나타내는 빨간색 화살표가 표시 됩니다.

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
