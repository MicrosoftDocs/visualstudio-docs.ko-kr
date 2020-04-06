---
title: '연습: 여백 문어 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697696"
---
# <a name="walkthrough-create-a-margin-glyph"></a>연습: 여백 문말 만들기
사용자 지정 편집기 확장을 사용하여 편집기 여백의 모양을 사용자 지정할 수 있습니다. 이 연습에서는 코드 주석에 "todo"라는 단어가 나타날 때마다 표시기 여백에 사용자 지정 글리프를 넣습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `TodoGlyphTest`이름을 지정합니다.

2. 편집기 분류자 프로젝트 항목을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="define-the-glyph"></a>글리프 정의
 인터페이스를 실행하여 글리프를 정의합니다. <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>

### <a name="to-define-the-glyph"></a>글리프를 정의하려면

1. 클래스 파일을 추가하고 이름을 `TodoGlyphFactory`로 지정합니다.

2. 선언을 사용하여 다음 코드를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. 을 구현하는 `TodoGlyphFactory` 클래스를 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. 글리프의 크기를 정의하는 전용 필드를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. 글리프 사용자 인터페이스(UI) 요소를 정의하여 구현합니다. `GenerateGlyph` `TodoTag`이 연습의 나중에 정의됩니다.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. 을 구현하는 `TodoGlyphFactoryProvider` 클래스를 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>추가합니다. "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.NameAttribute> After <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> vsTextMarker, "코드"및 TodoTag의 "TodoGlyph"로 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> 이 클래스를 내보냅니다.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. `TodoGlyphFactory`을 인스턴스화하여 <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> 메서드를 구현합니다.

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>할 일 태그 및 태거 정의
 이전 단계에서 정의한 UI 요소와 표시기 여백 간의 관계를 정의합니다. 태그 유형 및 태거를 만들고 태거 공급자를 사용하여 내보냅니다.

### <a name="to-define-a-todo-tag-and-tagger"></a>할 일 태그와 태거를 정의하려면

1. 프로젝트에 새 클래스 파일을 추가하고 이름을 `TodoTagger`지정합니다.

2. 다음 가져오기를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. `TodoTag`(이)라는 클래스를 추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. 형식의 `TodoTagger` `TodoTag`구현이라는 클래스를 수정합니다. <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. 클래스에 `TodoTagger` a <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 및 텍스트에 대한 개인 필드를 추가하여 분류 범위에서 찾을 수 있습니다.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. 분류를 설정하는 생성자추가합니다.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. "comment"라는 단어가 포함되어 있고 텍스트에 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 검색 텍스트가 포함된 모든 분류 범위를 찾아 메서드를 구현합니다. 검색 텍스트가 발견될 때마다 새 <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> 형식을 `TodoTag`다시 생성합니다.

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. 이벤트를 `TagsChanged` 선언합니다.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. 구현하는 `TodoTaggerProvider` <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>클래스를 추가하고 "코드"와 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag를 사용하여 내보냅니다.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>을 가져옵니다.

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. `TodoTagger`을 인스턴스화하여 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 메서드를 구현합니다.

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 TodoGlyphTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>TodoGlyphTest 솔루션을 빌드하고 테스트하려면

1. 솔루션을 빌드합니다.

2. **F5를**눌러 프로젝트를 실행합니다. 비주얼 스튜디오의 두 번째 인스턴스가 시작됩니다.

3. 표시기 여백이 표시되는지 확인합니다. (도구 **Tools** 메뉴에서 **옵션을**클릭합니다. 텍스트 **편집기** 페이지에서 **표시기 여백이** 선택되어 있는지 확인합니다.

4. 주석이 있는 코드 파일을 엽니다. 주석 섹션 중 하나에 "todo"라는 단어를 추가합니다.

5. 코드 창 왼쪽의 표시기 여백에 진한 파란색 윤곽선이 있는 연한 파란색 원이 나타납니다.
