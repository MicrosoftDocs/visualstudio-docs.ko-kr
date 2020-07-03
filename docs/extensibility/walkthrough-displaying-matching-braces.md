---
title: '연습: 짝이 되는 중괄호 표시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65a0bc2c53d5d6e970b4aaa956170bc06c24e7c9
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904839"
---
# <a name="walkthrough-display-matching-braces"></a>연습: 일치 하는 중괄호 표시
일치 시키려는 중괄호를 정의 하 고 캐럿이 중괄호 중 하나에 있을 때 일치 하는 중괄호에 텍스트 표식 태그를 추가 하 여 중괄호 일치와 같은 언어 기반 기능을 구현 합니다. 언어의 컨텍스트에서 중괄호를 정의 하 고, 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고, 해당 형식에만 태그를 적용 하 여 기존 콘텐츠 형식 (예: "텍스트")에 태그를 적용할 수 있습니다. 다음 연습에서는 "text" 콘텐츠 형식에 중괄호 일치 태그를 적용 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) 프로젝트 만들기

#### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. 편집기 분류자 프로젝트를 만듭니다. 솔루션의 이름을 `BraceMatchingTest`로 지정합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-a-brace-matching-tagger"></a>중괄호 일치 태거 구현
 Visual Studio에서 사용 되는 것과 유사한 중괄호 강조 표시 효과를 얻으려면 형식의 태거를 구현할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . 다음 코드에서는 모든 중첩 수준에서 중괄호 쌍의 태거를 정의 하는 방법을 보여 줍니다. 이 예제에서는 [] 및의 중괄호 쌍이 {} 태거 생성자에 정의 되어 있지만 전체 언어 구현에서는 언어 사양에 관련 중괄호 쌍이 정의 됩니다.

### <a name="to-implement-a-brace-matching-tagger"></a>중괄호 일치 태거를 구현 하려면

1. 클래스 파일을 추가 하 고 이름을 BraceMatching로 추가 합니다.

2. 다음 네임 스페이스를 가져옵니다.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. `BraceMatchingTagger`형식의에서 상속 되는 클래스를 정의 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. 텍스트 뷰, 소스 버퍼, 현재 스냅숏 지점 및 중괄호 쌍 집합에 대 한 속성을 추가 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. 태거 생성자에서 속성을 설정 하 고 뷰 변경 이벤트 및를 구독 합니다 <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . 이 예제에서 설명 하기 위해 일치 하는 쌍도 생성자에 정의 됩니다.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>구현의 일부로 TagsChanged 이벤트를 선언 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. 이벤트 처리기는 속성의 현재 캐럿 위치를 업데이트 `CurrentChar` 하 고 TagsChanged 이벤트를 발생 시킵니다.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>현재 문자가 여는 중괄호 이거나 이전 문자가 Visual Studio와 같이 닫는 중괄호가 면 중괄호를 일치 시키는 메서드를 구현 합니다. 일치가 발견 되 면이 메서드는 여는 중괄호와 닫는 중괄호에 대해 하나씩 두 개의 태그를 인스턴스화합니다.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. 다음 private 메서드는 모든 중첩 수준에서 일치 하는 중괄호를 찾습니다. 첫 번째 메서드는 여는 문자와 일치 하는 닫기 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. 다음 도우미 메서드는 닫는 문자와 일치 하는 열린 문자를 찾습니다.

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>중괄호 일치 태거 공급자 구현
 태거를 구현 하는 것 외에도 태거 공급자를 구현 하 고 내보내야 합니다. 이 경우 공급자의 콘텐츠 형식은 "text"입니다. 따라서 중괄호 일치는 모든 형식의 텍스트 파일에 나타나지만 완전 하지 않은 구현은 특정 콘텐츠 형식에만 중괄호 일치를 적용 합니다.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>중괄호 일치 태거 공급자를 구현 하려면

1. 에서 상속 되는 태거 공급자를 선언 하 고 <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , BraceMatchingTaggerProvider로 이름을, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" 및의를 사용 하 여 내보냅니다 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>BraceMatchingTagger을 인스턴스화하는 메서드를 구현 합니다.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 BraceMatchingTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>BraceMatchingTest 솔루션을 빌드하고 테스트 하려면

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만들고 일치 하는 중괄호를 포함 하는 텍스트를 입력 합니다.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. 닫는 중괄호 앞에 캐럿을 배치 하면 중괄호와 일치 하는 닫는 중괄호가 모두 강조 표시 됩니다. 닫는 중괄호 바로 뒤에 커서를 놓으면 중괄호와 일치 하는 여는 중괄호를 모두 강조 표시 해야 합니다.

## <a name="see-also"></a>참조
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
