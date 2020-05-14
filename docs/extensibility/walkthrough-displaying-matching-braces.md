---
title: '연습: 일치하는 중괄호 표시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697445"
---
# <a name="walkthrough-display-matching-braces"></a>연습: 일치하는 중괄호 표시
일치할 중괄호를 정의하고, 카속이 중괄호 중 괄호 중 하나에 있을 때 일치하는 중괄호에 텍스트 마커 태그를 추가하여 중괄호 일치와 같은 언어 기반 기능을 구현합니다. 언어의 컨텍스트에서 중괄호를 정의하고, 고유한 파일 이름 확장자 및 콘텐츠 유형을 정의하고, 태그를 해당 형식에만 적용하거나 기존 콘텐츠 유형(예: "텍스트")에 태그를 적용할 수 있습니다. 다음 연습에서는 "텍스트" 콘텐츠 유형에 중괄호 일치 태그를 적용하는 방법을 보여 주며 있습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>관리되는 확장성 프레임워크(MEF) 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. 편집기 분류자 프로젝트를 만듭니다. 솔루션의 이름을 `BraceMatchingTest`로 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-a-brace-matching-tagger"></a>중괄호 일치 태거 구현
 Visual Studio에서 사용되는 것과 유사한 중괄호 강조 표시 효과를 얻으려면 형식의 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>태거를 구현할 수 있습니다. 다음 코드는 모든 중첩 수준에서 중괄호 쌍의 태거를 정의하는 방법을 보여 주며 있습니다. 이 예제에서는 [] 중괄호 {} 쌍과 태거 생성자에서 정의되지만 전체 언어 구현에서는 관련 중괄호 쌍이 언어 사양에 정의됩니다.

### <a name="to-implement-a-brace-matching-tagger"></a>중괄호 일치 태거를 구현하려면

1. 클래스 파일을 추가하고 BraceMatching이름을 지정합니다.

2. 다음 네임스페이스를 가져옵니다.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. 형식에서 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> `BraceMatchingTagger` 상속 하는 클래스를 정의 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. 텍스트 뷰, 소스 버퍼, 현재 스냅숏 지점 및 중괄호 쌍 집합에 대한 속성을 추가합니다.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. 태거 생성자에서 속성을 설정하고 뷰 변경 이벤트 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> 및 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>을 구독합니다. 이 예제에서는 설명을 위해 일치 하는 쌍도 생성자에서 정의 됩니다.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> 구현의 일부로 TagsChanged 이벤트를 선언합니다.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. 이벤트 처리기는 `CurrentChar` 속성의 현재 카포트 위치를 업데이트하고 TagsChanged 이벤트를 발생시다.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. 현재 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 문자가 열린 중괄호이거나 Visual Studio에서와 같이 이전 문자가 가까운 중괄호인 경우 중괄호와 일치하는 메서드를 구현합니다. 일치하는 검색기가 발견되면 이 메서드는 열린 중괄호에 대한 태그와 가까운 중괄호에 대한 태그 두 개를 인스턴스화합니다.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. 다음 개인 메서드는 모든 중첩 수준에서 일치하는 중괄호를 찾습니다. 첫 번째 방법은 열린 문자와 일치하는 닫기 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. 다음 도우미 메서드는 가까운 문자와 일치하는 열린 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>중괄호 일치 태거 공급자 구현
 태거를 구현하는 것 외에도 태거 공급자를 구현하고 내보내야 합니다. 이 경우 공급자의 콘텐츠 형식은 "텍스트"입니다. 따라서 중괄호 일치는 모든 유형의 텍스트 파일에 나타나지만 풀러 구현에서는 특정 콘텐츠 유형에만 중괄호 일치가 적용됩니다.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>중괄호 일치 태거 공급자를 구현하려면

1. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>에서 상속 하는 태거 공급자를 선언 합니다. <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. 브레이스매칭태그거를 인스턴스화하는 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> 메서드를 구현합니다.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 BraceMatchingTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만들고 일치하는 중괄호가 포함된 텍스트를 입력합니다.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. 열린 중괄호 앞에 캐번을 배치할 때 해당 중괄호와 일치하는 가까운 중괄호가 모두 강조 표시됩니다. 닫기 중괄호 바로 바로 후에 커서를 배치할 때 해당 중괄호와 일치하는 열린 중괄호가 모두 강조 표시됩니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
