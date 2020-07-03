---
title: '연습: 여백 문자 모양 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b94ab61f56d74537758c189adc9c104516f67f92
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905045"
---
# <a name="walkthrough-create-a-margin-glyph"></a>연습: 여백 문자 모양 만들기
사용자 지정 편집기 확장을 사용 하 여 편집기 여백의 모양을 사용자 지정할 수 있습니다. 이 연습에서는 코드 주석에 "todo" 라는 단어가 나타날 때마다 표시기 여백에 사용자 지정 문자 모양을 삽입 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `TodoGlyphTest` 합니다.

2. 편집기 분류자 프로젝트 항목을 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-the-glyph"></a>문자 모양 정의
 인터페이스를 실행 하 여 문자 모양을 정의 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 합니다.

### <a name="to-define-the-glyph"></a>문자 모양을 정의 하려면

1. 클래스 파일을 추가하고 이름을 `TodoGlyphFactory`로 지정합니다.

2. 선언을 사용 하 여 다음 코드를 추가 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 을 구현 하는 라는 클래스를 추가 `TodoGlyphFactory` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 문자 모양의 크기를 정의 하는 전용 필드를 추가 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. `GenerateGlyph`GLYPH UI (사용자 인터페이스) 요소를 정의 하 여 구현 합니다. `TodoTag`는이 연습의 뒷부분에서 정의 됩니다.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 을 구현 하는 라는 클래스를 추가 `TodoGlyphFactoryProvider` <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> 합니다. 이 클래스 <xref:Microsoft.VisualStudio.Utilities.NameAttribute> 를 "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker After, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" 및 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag의로 내보냅니다.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A>를 인스턴스화하여 메서드를 구현 합니다 `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Todo 태그 및 태거 정의
 이전 단계에서 정의한 UI 요소와 표시기 여백 간의 관계를 정의 합니다. 태그 유형 및 태거를 만들고 태거 공급자를 사용 하 여 내보냅니다.

### <a name="to-define-a-todo-tag-and-tagger"></a>Todo 태그 및 태거를 정의 하려면

1. 프로젝트에 새 클래스 파일을 추가 하 고 이름을로 추가 `TodoTagger` 합니다.

2. 다음 가져오기를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. `TodoTag`(이)라는 클래스를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. `TodoTagger`형식을 구현 하는 라는 클래스를 수정 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. 클래스에 `TodoTagger` 대 한 전용 필드를 추가 하 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 고 분류 범위에서 찾을 텍스트에 대해를 추가 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 분류자를 설정 하는 생성자를 추가 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. 이름에 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> "comment" 라는 단어가 포함 되 고 해당 텍스트에 검색 텍스트가 포함 된 모든 분류 범위를 검색 하 여 메서드를 구현 합니다. 검색 텍스트가 발견 될 때마다는 형식의 새을 반환 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> `TodoTag` 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 이벤트를 선언 `TagsChanged` 합니다.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 을 구현 하는 라는 클래스를 추가 하 `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> 고을 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" 및 <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag의로 내보냅니다.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. 를 가져옵니다 <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A>를 인스턴스화하여 메서드를 구현 합니다 `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 TodoGlyphTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest 솔루션을 빌드하고 테스트 하려면

1. 솔루션을 빌드합니다.

2. **F5**키를 눌러 프로젝트를 실행 합니다. Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 표시기 여백이 표시 되는지 확인 합니다. **도구** 메뉴에서 **옵션**을 클릭 합니다. **텍스트 편집기** 페이지에서 **표시기 여백** 이 선택 되어 있는지 확인 합니다.

4. 주석이 포함 된 코드 파일을 엽니다. 설명 섹션 중 하나에 "todo" 라는 단어를 추가 합니다.

5. 어두운 파란색 윤곽선이 있는 연한 파란색 원이 코드 창의 왼쪽에 있는 표시기 여백에 나타납니다.
