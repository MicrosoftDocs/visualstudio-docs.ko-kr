---
title: '연습: 텍스트 보기 사용자 지정 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697464"
---
# <a name="walkthrough-customize-the-text-view"></a>연습: 텍스트 보기 사용자 지정
편집기 형식 맵에서 다음 속성 중 일부를 수정하여 텍스트 보기를 사용자 지정할 수 있습니다.

- 표시기 여백

- 삽입 카테

- 카를트 덮어쓰기

- 선택한 텍스트

- 비활성 선택 텍스트(즉, 포커스가 손실된 선택한 텍스트)

- 가시 공백

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `ViewPropertyTest`이름을 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-the-content-type"></a>콘텐츠 유형 정의

1. 클래스 파일을 추가하고 이름을 `ViewPropertyModifier`로 지정합니다.

2. 다음 `using` 지시문을 추가합니다.

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. 에서 상속하는 `TestViewCreationListener` 클래스를 선언합니다. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> 다음 특성을 사용 하 고이 클래스를 내보내기:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>을 사용하여 이 수신기가 적용되는 콘텐츠 유형을 지정합니다.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>을 사용하여 이 수신기의 역할을 지정합니다.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. 이 클래스에서 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>을 가져옵니다.

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>뷰 속성 변경

1. 뷰를 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 열 때 뷰 속성이 변경되도록 메서드를 설정합니다. 변경하려면 먼저 찾으려는 <xref:System.Windows.ResourceDictionary> 뷰의 측면에 해당하는 뷰를 찾습니다. 그런 다음 리소스 사전에서 해당 속성을 변경하고 속성을 설정합니다. 속성을 설정하기 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> 전에 메서드를 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> 호출한 다음 속성을 설정한 <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> 후 메서드에 대한 호출을 일괄 처리합니다.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트

1. 솔루션을 빌드합니다.

     디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

2. 텍스트 파일을 만들고 일부 텍스트를 입력합니다.

    - 삽입 카렛은 자홍색이어야하며 덮어 쓰기 는 청록색이어야합니다.

    - 표시기 여백(텍스트 보기 왼쪽)은 연한 녹색이어야 합니다.

3. 입력한 텍스트를 선택합니다. 선택한 텍스트의 색상은 연한 분홍색이어야 합니다.

4. 텍스트를 선택한 동안 텍스트 창 외부의 아무 곳이나 클릭합니다. 선택한 텍스트의 색상은 진한 분홍색이어야 합니다.

5. 보이는 공백을 켭니다. 편집 **메뉴에서** **고급을** 가리킨 다음 **공백 보기를**클릭합니다. 텍스트에 일부 탭을 입력합니다. 탭을 나타내는 빨간색 화살표가 표시되어야 합니다.

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
