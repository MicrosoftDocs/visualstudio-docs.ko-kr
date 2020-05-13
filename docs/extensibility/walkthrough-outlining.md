---
title: '연습: 개요 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697221"
---
# <a name="walkthrough-outlining"></a>연습: 개요
확장하거나 축소하려는 텍스트 영역의 종류를 정의하여 개요와 같은 언어 기반 기능을 설정합니다. 언어 서비스의 컨텍스트에서 영역을 정의하거나 고유한 파일 이름 확장자 및 콘텐츠 유형을 정의하고 해당 형식에만 지역 정의를 적용하거나 기존 콘텐츠 유형(예: "텍스트")에 지역 정의를 적용할 수 있습니다. 이 연습에서는 개요 영역을 정의하고 표시하는 방법을 보여 주었습니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-managed-extensibility-framework-mef-project"></a>관리되는 확장성 프레임워크(MEF) 프로젝트 만들기

### <a name="to-create-a-mef-project"></a>MEF 프로젝트를 만들려면

1. VSIX 프로젝트를 만듭니다. 솔루션의 이름을 `OutlineRegionTest`로 지정합니다.

2. 프로젝트에 편집기 분류자 항목 템플릿을 추가합니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

3. 기존 클래스 파일을 삭제합니다.

## <a name="implement-an-outlining-tagger"></a>개요 태거 구현
 개요 영역은 일종의 태그()로<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>표시됩니다. 이 태그는 표준 개요 동작을 제공합니다. 윤곽이 있는 영역을 확장하거나 축소할 수 있습니다. 윤곽이 표시된 영역은 축소된**+** 경우 () 또는 확장된 경우**-** 빼기 기호()로 표시되고 확장된 영역은 세로선으로 구분됩니다.

 다음 단계는 괄호 **([ [****]**)로 구분된 모든 영역에 대한 개요 영역을 만드는 태거를 정의하는 방법을 보여 준다.

### <a name="to-implement-an-outlining-tagger"></a>개요 태거를 구현하려면

1. 클래스 파일을 추가하고 이름을 `OutliningTagger`로 지정합니다.

2. 다음 네임스페이스를 가져옵니다.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. 이라는 클래스를 `OutliningTagger`만들고 구현 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>합니다.

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. 일부 필드를 추가하여 텍스트 버퍼 및 스냅숏을 추적하고 윤곽 영역으로 태그지정해야 하는 줄 집합을 누적합니다. 이 코드에는 개요 영역을 나타내는 지역 개체 목록(나중에 정의)이 포함됩니다.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. 필드를 초기화하고 버퍼를 구문 분석하며 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 이벤트에 이벤트 처리기를 추가하는 태거 생성기를 추가합니다.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. 태그 <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> 범위를 인스턴스화하는 메서드를 구현합니다. 이 예제에서는 메서드에 전달된 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 범위가 연속적이라고 가정하지만 항상 그런 것은 아닐 수도 있습니다. 이 메서드는 개요 각 영역에 대 한 새 태그 범위를 인스턴스화 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. 이벤트 `TagsChanged` 처리기를 선언합니다.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. 텍스트 `BufferChanged` 버퍼를 구문 <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> 분석하여 이벤트에 응답하는 이벤트 처리기를 추가합니다.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. 버퍼를 구문 분석하는 메서드를 추가합니다. 여기에 제공된 예제는 그림전용입니다. 동시에 버퍼를 중첩된 개요 영역으로 구문 분석합니다.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. 다음 도우미 메서드는 1이 가장 왼쪽 중괄호 쌍이되도록 개요의 수준을 나타내는 정수를 가져옵니다.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. 다음 도우미 메서드는 지역(이 문서의 후반부에서 정의)을 SnapshotSpan으로 변환합니다.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. 다음 코드는 그림전용입니다. 개요 영역의 시작에 대한 선 번호 및 오프셋과 상위 영역(있는 경우)에 대한 참조를 포함하는 PartialRegion 클래스를 정의합니다. 이 코드를 사용하면 파서가 중첩된 개요 영역을 설정할 수 있습니다. 파생 된 Region 클래스는 개요 영역의 끝의 줄 번호에 대 한 참조를 포함 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>태거 공급자 구현
 태거에 대한 태거 공급자를 내보냅니다. 태거 공급자는 `OutliningTagger` "텍스트" 콘텐츠 형식의 버퍼에 대한 버퍼를 만들거나 버퍼에 이미 있는 경우 를 `OutliningTagger` 반환합니다.

### <a name="to-implement-a-tagger-provider"></a>태거 공급자를 구현하려면

1. 을 구현하는 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> `OutliningTaggerProvider` 클래스를 만들고 ContentType 및 TagType 특성을 사용하여 내보냅니다.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. 버퍼의 <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> 속성에 `OutliningTagger` 메서드를 추가 하여 메서드를 구현 합니다.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>코드 빌드 및 테스트
 이 코드를 테스트하려면 OutlineRegionTest 솔루션을 빌드하고 실험 인스턴스에서 실행합니다.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>개요를 구축하고 테스트하려면

1. 솔루션을 빌드합니다.

2. 디버거에서 이 프로젝트를 실행하면 Visual Studio의 두 번째 인스턴스가 시작됩니다.

3. 텍스트 파일을 만듭니다. 여는 대괄호와 닫는 대괄호가 모두 포함된 텍스트를 입력합니다.

    ```
    [
       Hello
    ]
    ```

4. 두 대괄호를 모두 포함하는 개요 영역이 있어야 합니다. 열린 대괄호의 왼쪽에 있는 마이너스 기호를 클릭하여 개요 영역을 축소할 수 있습니다. 영역이 축소되면 타원*기호(...*)가 축소된 영역의 왼쪽에 나타나고 타원 위로 포인터를 이동할 때 텍스트 **가리키기 텍스트가** 포함된 팝업이 나타납니다.

## <a name="see-also"></a>참조
- [연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
