---
title: '연습: 개요 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb338803d50b2ecc9af8c8db6a6b6dc2f3631161
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85906181"
---
# <a name="walkthrough-outlining"></a>연습: 개요
확장 하거나 축소할 텍스트 영역의 종류를 정의 하 여 개요와 같은 언어 기반 기능을 설정 합니다. 언어 서비스의 컨텍스트에서 영역을 정의 하거나 고유한 파일 이름 확장명 및 콘텐츠 형식을 정의 하 고 해당 형식에만 지역 정의를 적용 하거나 기존 콘텐츠 형식 (예: "텍스트")에 지역 정의를 적용할 수 있습니다. 이 연습에서는 개요 영역을 정의 하 고 표시 하는 방법을 보여 줍니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Managed Extensibility Framework (MEF) 프로젝트 만들기

### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. VSIX 프로젝트를 만듭니다. 솔루션의 이름을 `OutlineRegionTest`로 지정합니다.

2. 편집기 분류자 항목 템플릿을 프로젝트에 추가 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-an-outlining-tagger"></a>개요 태거 구현
 개요 영역은 일종의 태그 ()로 표시 됩니다 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> . 이 태그는 표준 개요 동작을 제공 합니다. 윤곽선이 있는 영역을 확장 하거나 축소할 수 있습니다. 윤곽선이 축소 된 경우에는 더하기 기호 ()로 표시 되 **+** **-** 고, 확장 된 영역은 수직선으로 경계선는 경우에는 더하기 기호 ()로 표시 됩니다.

 다음 단계에서는 대괄호 (**[**,**]**)로 구분 되는 모든 지역에 대 한 개요 영역을 만드는 태거를 정의 하는 방법을 보여 줍니다.

### <a name="to-implement-an-outlining-tagger"></a>개요 태거를 구현 하려면

1. 클래스 파일을 추가하고 이름을 `OutliningTagger`로 지정합니다.

2. 다음 네임 스페이스를 가져옵니다.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 이라는 클래스를 만들고 `OutliningTagger` 구현 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> .

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 텍스트 버퍼와 스냅숏을 추적 하는 필드를 추가 하 고 개요 영역으로 태그를 지정 해야 하는 줄 집합을 누적 합니다. 이 코드에는 개요 영역을 나타내는 지역 개체의 목록 (나중에 정의 됨)이 포함 됩니다.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 필드를 초기화 하 고, 버퍼를 구문 분석 하 고, 이벤트 처리기를 이벤트에 추가 하는 태거 생성자를 추가 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 태그 범위를 인스턴스화하는 메서드를 구현 합니다 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> . 이 예에서는 메서드에 전달 된의 범위가 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 연속적 이라고 가정 하지만 항상 그렇지는 않을 수 있습니다. 이 메서드는 각 개요 영역에 대 한 새 태그 범위를 인스턴스화합니다.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. `TagsChanged`이벤트 처리기를 선언 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. `BufferChanged`텍스트 버퍼를 구문 분석 하 여 이벤트에 응답 하는 이벤트 처리기를 추가 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 버퍼를 구문 분석 하는 메서드를 추가 합니다. 여기에 제공 된 예제는 설명을 위한 것입니다. 버퍼를 중첩 된 개요 영역으로 동기적으로 구문 분석 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 다음 도우미 메서드는 개요의 수준을 나타내는 정수를 가져옵니다. 예를 들어 1은 가장 왼쪽 중괄호 쌍입니다.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 다음 도우미 메서드는이 문서의 뒷부분에서 정의 되는 영역을 SnapshotSpan로 변환 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 다음 코드는 설명을 위한 것입니다. 개요 영역 시작의 줄 번호와 오프셋 및 부모 영역 (있는 경우)에 대 한 참조를 포함 하는 PartialRegion 클래스를 정의 합니다. 이 코드를 사용 하 여 파서는 중첩 된 개요 영역을 설정할 수 있습니다. 파생 영역 클래스는 개요 영역 끝의 줄 번호에 대 한 참조를 포함 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>태거 공급자 구현
 태거의 태거 공급자를 내보냅니다. 태거 공급자는 `OutliningTagger` "text" 콘텐츠 형식의 버퍼에 대 한를 만들거나 버퍼에 이미 있는 경우를 반환 합니다 `OutliningTagger` .

### <a name="to-implement-a-tagger-provider"></a>태거 공급자를 구현 하려면

1. `OutliningTaggerProvider`을 구현 하는 클래스를 만들고 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ContentType 및 TagType 특성을 사용 하 여 내보냅니다.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 을 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> `OutliningTagger` 버퍼의 속성에 추가 하 여 메서드를 구현 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트 하려면 OutlineRegionTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>OutlineRegionTest 솔루션을 빌드하고 테스트 하려면

1. 솔루션을 빌드합니다.

2. 디버거에서이 프로젝트를 실행 하면 Visual Studio의 두 번째 인스턴스가 시작 됩니다.

3. 텍스트 파일을 만듭니다. 여는 대괄호와 닫는 대괄호를 모두 포함 하는 텍스트를 입력 합니다.

    ```
    [
       Hello
    ]
    ```

4. 두 괄호를 모두 포함 하는 개요 영역이 있어야 합니다. 왼쪽 괄호 왼쪽에 있는 빼기 기호를 클릭 하 여 개요 영역을 축소할 수 있습니다. 영역이 축소 되 면 줄임표 기호 (*...*)가 축소 된 영역의 왼쪽에 표시 되 고 텍스트 **가리키기 텍스트가** 포함 된 팝업은 줄임표 위로 포인터를 이동할 때 표시 되어야 합니다.

## <a name="see-also"></a>추가 정보
- [연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
