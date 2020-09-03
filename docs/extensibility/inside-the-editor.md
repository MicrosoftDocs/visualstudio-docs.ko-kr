---
title: 편집기 기본 사항
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710322"
---
# <a name="inside-the-editor"></a>편집기 내부

편집기는 편집기 텍스트 모델과 사용자 인터페이스를 별도로 유지 하도록 디자인 된 여러 하위 시스템으로 구성 됩니다.

다음 섹션에서는 편집기의 여러 측면을 설명 합니다.

- [하위 시스템 개요](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [텍스트 모델](../extensibility/inside-the-editor.md#the-text-model)

- [텍스트 뷰입니다.](../extensibility/inside-the-editor.md#the-text-view)

다음 섹션에서는 편집기의 기능을 설명 합니다.

- [태그 및 분류자](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [도구 영역](../extensibility/inside-the-editor.md#adornments)

- [프로젝션](../extensibility/inside-the-editor.md#projection)

- [개요](../extensibility/inside-the-editor.md#outlining)

- [마우스 바인딩](../extensibility/inside-the-editor.md#mouse-bindings)

- [편집기 작업](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>하위 시스템 개요

### <a name="text-model-subsystem"></a>텍스트 모델 하위 시스템

텍스트 모델 하위 시스템은 텍스트를 표시 하 고 조작을 가능 하 게 합니다. 텍스트 모델 하위 시스템은 편집기에 표시 되는 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 문자 시퀀스를 설명 하는 인터페이스를 포함 합니다. 이 텍스트는 여러 가지 방법으로 수정, 추적 및 조작할 수 있습니다. 텍스트 모델은 또한 다음과 같은 측면에 대 한 형식을 제공 합니다.

- 텍스트를 파일과 연결 하 고 파일 시스템에서 읽고 쓰는 것을 관리 하는 서비스입니다.

- 두 개체 시퀀스 간의 최소 차이를 찾는 차이점 보관용 서비스입니다.

- 다른 버퍼에 있는 텍스트의 하위 집합을 기준으로 버퍼의 텍스트를 설명 하는 시스템입니다.

텍스트 모델 하위 시스템은 UI (사용자 인터페이스) 개념을 사용 하지 않습니다. 예를 들어 텍스트 서식 또는 텍스트 레이아웃을 담당 하지 않으며 텍스트와 연결 될 수 있는 시각적 장식을 알지 못합니다.

텍스트 모델 하위 시스템의 공용 형식은 *Microsoft.VisualStudio.Text.Data.dll* 및 *Microsoft.VisualStudio.CoreUtility.dll*에 포함 되어 있으며, .NET Framework 기본 클래스 라이브러리와 MEF (Managed Extensibility Framework)에만 종속 됩니다.

### <a name="text-view-subsystem"></a>텍스트 뷰 하위 시스템

텍스트 뷰 하위 시스템은 텍스트의 서식을 지정 하 고 표시 하는 일을 담당 합니다. 이 하위 시스템의 형식은 형식이 Windows Presentation Foundation (WPF)를 사용 하는지 여부에 따라 두 개의 계층으로 나뉩니다. 가장 중요 한 형식은 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 및 이며 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , 표시 되는 텍스트 줄 집합과 캐럿, 선택 영역, WPF UI 요소를 사용 하 여 텍스트를 표시할 하는 기능을 제어 합니다. 또한이 하위 시스템은 텍스트 표시 영역 주위에 여백을 제공 합니다. 이러한 여백은 확장 될 수 있으며 다양 한 종류의 콘텐츠와 시각적 효과를 포함할 수 있습니다. 여백 예는 줄 번호 표시 및 스크롤 막대입니다.

텍스트 뷰 하위 시스템의 공용 형식은 *Microsoft.VisualStudio.Text.UI.dll* 및 *Microsoft.VisualStudio.Text.UI.Wpf.dll*에 포함 되어 있습니다. 첫 번째 어셈블리에는 플랫폼 독립적인 요소가 포함 되 고, 두 번째 어셈블리에는 WPF 관련 요소가 포함 됩니다.

### <a name="classification-subsystem"></a>분류 하위 시스템

분류 하위 시스템은 텍스트의 글꼴 속성을 결정 해야 합니다. 분류자는 텍스트를 다른 클래스 (예: "keyword" 또는 "comment")로 나눕니다. 분류 형식 맵은 이러한 클래스를 실제 글꼴 속성 (예: "Blue Consolas 10 pt")에 연결 합니다. 이 정보는 텍스트의 서식을 지정 하 고 렌더링할 때 텍스트 뷰에서 사용 됩니다. 태그 지정 (이 항목의 뒷부분에서 자세히 설명)을 사용 하면 데이터를 텍스트 범위에 연결할 수 있습니다.

분류 하위 시스템의 공용 형식은 Microsoft.VisualStudio.Text.Logic.dll 포함 되어 있으며 Microsoft.VisualStudio.Text.UI.Wpf.dll에 포함 된 분류의 시각적 측면과 상호 작용 합니다.

### <a name="operations-subsystem"></a>작업 하위 시스템

작업 하위 시스템은 편집기 동작을 정의 합니다. Visual Studio 편집기 명령 및 실행 취소 시스템에 대 한 구현을 제공 합니다.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>텍스트 모델과 텍스트 뷰를 자세히 살펴봅니다.

### <a name="the-text-model"></a>텍스트 모델

텍스트 모델 하위 시스템은 다양 한 텍스트 형식 그룹으로 구성 됩니다. 여기에는 텍스트 버퍼, 텍스트 스냅숏 및 텍스트 범위가 포함 됩니다.

#### <a name="text-buffers-and-text-snapshots"></a>텍스트 버퍼 및 텍스트 스냅숏

<xref:Microsoft.VisualStudio.Text.ITextBuffer>인터페이스는 `String` .NET Framework에서 형식에 사용 되는 인코딩입니다. u t f-16을 사용 하 여 인코딩된 유니코드 문자 시퀀스를 나타냅니다. 텍스트 버퍼는 파일 시스템 문서로 지속 될 수 있지만 반드시 필요한 것은 아닙니다.

는 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 빈 텍스트 버퍼 또는 문자열 또는에서 초기화 되는 텍스트 버퍼를 만드는 데 사용 됩니다 <xref:System.IO.TextReader> . 텍스트 버퍼를 파일 시스템에로 저장할 수 있습니다 <xref:Microsoft.VisualStudio.Text.ITextDocument> .

스레드는를 호출 하 여 텍스트 버퍼의 소유권을 가질 때까지 모든 스레드에서 텍스트 버퍼를 편집할 수 있습니다 <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . 그 후에는 해당 스레드만 편집을 수행할 수 있습니다.

텍스트 버퍼는 수명 중에 여러 버전을 사용할 수 있습니다. 새 버전은 버퍼를 편집할 때마다 생성 되 고 변경할 수 없는은 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 해당 버퍼 버전의 내용을 나타냅니다. 텍스트 스냅숏은 변경할 수 없기 때문에 표시 되는 텍스트 버퍼가 계속 변경 되더라도 제한 없이 모든 스레드에서 텍스트 스냅숏에 액세스할 수 있습니다.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>텍스트 스냅숏 및 텍스트 스냅숏 줄

문자 시퀀스 또는 일련의 줄로 텍스트 스냅숏의 내용을 볼 수 있습니다. 문자 및 줄은 모두 0부터 시작 하는 인덱스입니다. 빈 텍스트 스냅숏에는 0 자와 빈 줄이 하나씩 포함 됩니다. 줄은 유효한 유니코드 줄 바꿈 문자 시퀀스 또는 버퍼의 시작 또는 끝으로 구분 됩니다. 줄 바꿈 문자는 텍스트 스냅숏에 명시적으로 표시 되며 텍스트 스냅숏의 줄 바꿈이 모두 같을 필요는 없습니다.

> [!NOTE]
> Visual Studio 편집기의 줄 바꿈 문자에 대 한 자세한 내용은 [인코딩 및 줄 바꿈](../ide/encodings-and-line-breaks.md)을 참조 하세요.

텍스트 줄은 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 특정 줄 번호 또는 특정 문자 위치에 대 한 텍스트 스냅숏에서 가져올 수 있는 개체로 표현 됩니다.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Snapshotpoints가, SnapshotSpans 및 NormalizedSnapshotSpanCollections

는 <xref:Microsoft.VisualStudio.Text.SnapshotPoint> 스냅숏의 문자 위치를 나타냅니다. 위치는 0과 스냅숏의 길이 사이에 있어야 합니다. 는 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 스냅숏의 텍스트 범위를 나타냅니다. 끝 위치는 0과 스냅숏의 길이 사이에 있어야 합니다. 는 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 동일한 스냅숏의 개체 집합으로 구성 됩니다 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> .

#### <a name="spans-and-normalizedspancollections"></a>범위 및 NormalizedSpanCollections

는 <xref:Microsoft.VisualStudio.Text.Span> 텍스트 스냅숏의 텍스트 범위에 적용할 수 있는 간격을 나타냅니다. 스냅숏 위치는 0부터 시작 하므로 범위는 0을 포함 한 모든 위치에서 시작할 수 있습니다. `End`범위의 속성은 해당 `Start` 속성 및 해당 속성의 합계와 같습니다 `Length` . 에는 `Span` 속성으로 인덱싱된 문자가 포함 되지 않습니다 `End` . 예를 들어 Start = 5이 고 길이가 3 인 범위는 End = 8 이며 위치 5, 6, 7에 문자를 포함 합니다. 이 범위에 대 한 표기법은 [5 ... 8)입니다.

끝 위치를 포함 하 여 공통 된 위치가 있는 경우 두 범위가 교차 합니다. 따라서 [3, 5)와 [2, 7)의 교집합은 [3, 5)이 고 [3, 5)와 [5, 7)의 교집합은 [5, 5)입니다. ([5, 5)는 빈 범위입니다.)

끝 위치를 제외 하 고 공통 된 위치가 있는 경우 두 범위가 겹칩니다. 빈 범위는 다른 범위와 겹치면 안 되며 두 범위의 중복은 비어 있지 않습니다.

는 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 범위의 시작 속성 순서에 포함 된 범위 목록입니다. 목록에서 겹치는 또는 인접 범위가 병합 됩니다. 예를 들어 범위 [5.9), [0 ..1), [3 ... 6) 및 [9.10) 집합을 지정 하는 경우 정규화 된 범위 목록은 [0 ..1), [3.. 10)입니다.

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion 및 텍스트 변경 알림

텍스트 버퍼의 내용은 개체를 사용 하 여 변경할 수 있습니다 <xref:Microsoft.VisualStudio.Text.ITextEdit> . 의 메서드 중 하나를 사용 하 여 이러한 개체를 만들면 `CreateEdit()` <xref:Microsoft.VisualStudio.Text.ITextBuffer> 텍스트 편집으로 구성 된 텍스트 트랜잭션이 시작 됩니다. 모든 편집은 버퍼의 일부 텍스트를 문자열로 대체 하는 것입니다. 모든 편집의 좌표와 내용은 트랜잭션이 시작 될 때 버퍼의 스냅숏에 상대적으로 표시 됩니다. <xref:Microsoft.VisualStudio.Text.ITextEdit>개체는 동일한 트랜잭션에서 다른 편집의 영향을 받는 편집의 좌표를 조정 합니다.

예를 들어 다음 문자열을 포함 하는 텍스트 버퍼를 가정 합니다.

```
abcdefghij
```

문자를 사용 하 여 [ `X` 6.. 9)의 범위를 대체 하는 두 번째 편집, 문자를 사용 하 여 [2.4.4)의 범위를 대체 하는 한 개의 편집을 포함 하는 트랜잭션을 적용 합니다. `Y` 결과는 다음과 같습니다.

```
abXefYj
```

첫 번째 편집이 적용 되기 전에 트랜잭션 시작 부분에 있는 버퍼의 내용에 대해 두 번째 편집의 좌표가 계산 되었습니다.

버퍼에 대 한 변경 내용은 <xref:Microsoft.VisualStudio.Text.ITextEdit> 해당 메서드를 호출 하 여 개체를 커밋할 때 적용 됩니다 `Apply()` . 비어 있지 않은 편집이 하나 이상 있는 경우 새가 <xref:Microsoft.VisualStudio.Text.ITextVersion> 만들어지고 새 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 가 만들어지고 하나의 `Changed` 이벤트가 발생 합니다. 모든 텍스트 버전에는 다른 텍스트 스냅숏이 있습니다. 텍스트 스냅숏은 편집 트랜잭션 후 텍스트 버퍼의 전체 상태를 나타내지만 텍스트 버전은 한 스냅숏의 변경 내용만 다음 스냅숏으로 설명 합니다. 일반적으로 텍스트 스냅숏은 한 번 사용 되 고 삭제 된 다음 텍스트 버전이 일정 시간 동안 활성 상태를 유지 해야 하는 것을 의미 합니다.

텍스트 버전에는가 포함 되어 있습니다 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . 이 컬렉션은 스냅숏에 적용 될 때 후속 스냅숏을 생성 하는 변경 사항을 설명 합니다. 컬렉션의 모든에는 <xref:Microsoft.VisualStudio.Text.ITextChange> 변경의 문자 위치, 대체 된 문자열 및 대체 문자열이 포함 됩니다. 기본 삽입을 위해 대체 된 문자열이 비어 있고 기본 삭제를 위해 대체 문자열이 비어 있습니다. 정규화 된 컬렉션은 항상 `null` 최신 버전의 텍스트 버퍼에 대해입니다.

<xref:Microsoft.VisualStudio.Text.ITextEdit>언제 든 지 텍스트 버퍼에 대해 하나의 개체만 인스턴스화할 수 있으며, 소유권을 요청한 경우 텍스트 버퍼를 소유 하는 스레드에서 모든 텍스트 편집을 수행 해야 합니다. 텍스트 편집은 메서드나 해당 메서드를 호출 하 여 중단 될 수 있습니다 `Cancel` `Dispose` .

<xref:Microsoft.VisualStudio.Text.ITextBuffer> 또한는 `Insert()` `Delete()` 인터페이스에 있는 것과 유사한, 및 메서드를 제공 `Replace()` <xref:Microsoft.VisualStudio.Text.ITextEdit> 합니다. 이러한 작업은 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체를 만들고 비슷한 호출을 수행한 다음 편집을 적용 하는 것과 동일한 효과를 가집니다.

#### <a name="tracking-points-and-tracking-spans"></a>추적 요소 및 추적 범위

는 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> 텍스트 버퍼의 문자 위치를 나타냅니다. 문자 위치를 이동 하는 방식으로 버퍼를 편집 하면 추적 지점은 함께 이동 합니다. 예를 들어 추적 지점이 버퍼의 위치 10을 참조 하 고 버퍼의 시작 부분에 5 개의 문자가 삽입 되 면 추적 지점은 위치 15를 참조 합니다. 추적 지점으로 표시 되는 위치를 정확 하 게 삽입 하는 경우 해당 동작은 <xref:Microsoft.VisualStudio.Text.PointTrackingMode> 또는 일 수 있는에 의해 결정 됩니다 `Positive` `Negative` . 추적 모드가 양수인 경우 추적 지점은 같은 문자를 참조 하며이는 현재 삽입 끝에 있습니다. 추적 모드가 음수 이면 추적 지점은 원래 위치에서 첫 번째 삽입 된 문자를 참조 합니다. 추적 지점이 나타내는 위치의 문자가 삭제 되 면 추적 지점은 삭제 된 범위 다음의 첫 번째 문자로 이동 합니다. 예를 들어 추적 지점이 위치 5에서 문자를 참조 하 고, 3 ~ 6 위치의 문자를 삭제 하는 경우 추적 지점은 3 위치의 문자를 참조 합니다.

는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 한 위치 뿐만 아니라 문자 범위를 나타냅니다. 해당 동작은에 의해 결정 됩니다 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . 범위 추적 모드가 [EdgeInclusive SpanTrackingMode](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)경우 추적 범위는 해당 가장자리에 삽입 된 텍스트를 통합 하기 위해 증가 합니다. 범위 추적 모드가 [SpanTrackingMode](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)인 경우 추적 범위는 해당 가장자리에 삽입 된 텍스트를 포함 하지 않습니다. 그러나 범위 추적 모드가 [SpanTrackingMode](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)인 경우에는 삽입이 시작 부분을 향해 현재 위치를 푸시합니다. 범위 추적 모드가 [SpanTrackingMode](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)인 경우 삽입은 현재 위치를 끝 쪽으로 푸시합니다.

추적 지점이 속한 텍스트 버퍼의 스냅숏에 대 한 추적 지점의 위치 또는 추적 범위 범위를 가져올 수 있습니다. 모든 스레드에서 추적 지점과 추적 범위를 안전 하 게 참조할 수 있습니다.

#### <a name="content-types"></a>내용 유형

콘텐츠 형식은 다양 한 종류의 콘텐츠를 정의 하는 메커니즘입니다. 콘텐츠 형식은 "text", "code" 또는 "binary"와 같은 파일 형식 이거나 "xml", "vb", "c #" 등의 기술 형식일 수 있습니다. 예를 들어 "using" 이라는 단어는 c # 및 Visual Basic 모두의 키워드 이지만 다른 프로그래밍 언어에는 해당 하지 않습니다. 따라서이 키워드의 정의는 "c #" 및 "vb" 콘텐츠 형식으로 제한 됩니다.

콘텐츠 형식은 편집기의 장식 및 기타 요소에 대 한 필터로 사용 됩니다. 많은 편집기 기능 및 확장 지점은 콘텐츠 유형별으로 정의 됩니다. 예를 들어 텍스트 색 지정은 일반 텍스트 파일, XML 파일 및 Visual Basic 소스 코드 파일에 대해 다릅니다. 텍스트 버퍼는 생성 될 때 일반적으로 콘텐츠 형식이 할당 되며 텍스트 버퍼의 내용 유형을 변경할 수 있습니다.

콘텐츠 형식은 다른 콘텐츠 형식에서 여러 상속할 수 있습니다. 에서는 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 지정 된 콘텐츠 형식의 부모로 여러 기본 형식을 지정할 수 있습니다.

개발자는를 사용 하 여 고유한 콘텐츠 형식을 정의 하 고 등록할 수 있습니다 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . 를 사용 하 여 특정 콘텐츠 형식에 대해 많은 편집기 기능을 정의할 수 있습니다 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . 예를 들어 편집기 여백, 장식 및 마우스 처리기를 정의 하 여 특정 내용 유형을 표시 하는 편집기에만 적용할 수 있습니다.

### <a name="the-text-view"></a>텍스트 뷰입니다.

MVC (모델 뷰 컨트롤러) 패턴의 뷰 부분은 텍스트 뷰, 뷰의 서식, 스크롤 막대와 같은 그래픽 요소 및 캐럿을 정의 합니다. Visual Studio 편집기의 모든 프레젠테이션 요소는 WPF를 기반으로 합니다.

#### <a name="text-views"></a>텍스트 보기

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>인터페이스는 텍스트 뷰를 플랫폼에 독립적으로 표현한 것입니다. 주로 창에 텍스트 문서를 표시 하는 데 사용 되지만 도구 설명 등의 다른 용도로도 사용할 수 있습니다.

텍스트 뷰는 다른 종류의 텍스트 버퍼를 참조 합니다. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>속성은 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 세 가지 다른 텍스트 버퍼를 가리키는 개체를 참조 합니다. 데이터 버퍼는 상위 데이터 수준 버퍼, 편집 버퍼, 편집이 발생 하는 데이터 버퍼 및 텍스트 뷰에 표시 되는 버퍼에 해당 하는 시각적 버퍼를 가리킵니다.

텍스트는 기본 텍스트 버퍼에 연결 된 분류자에 따라 서식이 지정 되 고 텍스트 뷰 자체에 연결 된 장식 공급자를 사용 하 여 표시 됩니다.

#### <a name="the-text-view-coordinate-system"></a>텍스트 뷰 좌표계

텍스트 뷰 좌표계는 텍스트 보기에서 위치를 지정 합니다. 이 좌표계에서 x 값 0.0은 표시 되는 텍스트의 왼쪽 가장자리에 해당 하 고 y 값 0.0은 표시 되는 텍스트의 위쪽 가장자리에 해당 합니다. X 좌표가 왼쪽에서 오른쪽으로 늘어나고 y 좌표가 위쪽에서 아래쪽으로 늘어납니다.

뷰포트 (텍스트 창에 표시 되는 텍스트 부분)는 세로로 스크롤할 때와 동일한 방식으로 스크롤할 수 없습니다. 뷰포트는 그리기 화면을 기준으로 이동 하도록 왼쪽 좌표를 변경 하 여 가로로 스크롤됩니다. 그러나 뷰포트는 렌더링 된 텍스트를 변경 해야만 세로로 스크롤할 수 있으며이로 인해 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 이벤트가 발생 합니다.

좌표계의 거리는 논리적 픽셀에 해당 합니다. 배율 변형 없이 텍스트 렌더링 화면이 표시 되 면 텍스트 렌더링 좌표계의 한 단위는 디스플레이의 1 픽셀에 해당 합니다.

#### <a name="margins"></a>여백

인터페이스는 여백을 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> 나타내며 여백 및 크기의 표시 여부를 제어할 수 있습니다. 미리 정의 된 여백에는 "Top", "Left", "Right" 및 "Bottom" 이라는 4 개의 미리 정의 된 여백이 있으며 보기의 위쪽, 아래쪽, 왼쪽 또는 오른쪽 가장자리에 연결 되어 있습니다. 이러한 여백은 다른 여백을 배치할 수 있는 컨테이너입니다. 인터페이스는 여백의 크기와 여백 표시 유형을 반환 하는 메서드를 정의 합니다. 여백은 연결 된 텍스트 보기에 대 한 추가 정보를 제공 하는 시각적 요소입니다. 예를 들어 줄 번호 여백은 텍스트 보기의 줄 번호를 표시 합니다. 문자 모양 여백은 UI 요소를 표시 합니다.

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>인터페이스는 여백 만들기 및 배치를 처리 합니다. 여백은 다른 여백과 관련 하 여 정렬할 수 있습니다. 우선 순위가 높은 여백은 텍스트 보기에 더 가깝게 배치 됩니다. 예를 들어 두 개의 왼쪽 여백이 있고, 여백 A와 여백 B가 있고, 여백 B의 우선 순위가 여백 A 보다 낮으면 여백 B가 여백 A의 왼쪽에 나타납니다.

#### <a name="the-text-view-host"></a>텍스트 뷰 호스트

인터페이스에는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 보기와 함께 표시 되는 텍스트 뷰 및 인접 장식이 포함 됩니다 (예: 스크롤 막대). 텍스트 보기 호스트에는 뷰의 테두리에 연결 된 여백도 포함 됩니다.

#### <a name="formatted-text"></a>서식 있는 텍스트

텍스트 뷰에 표시 되는 텍스트는 개체로 구성 됩니다 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> . 모든 텍스트 보기 줄은 텍스트 뷰의 텍스트 한 줄에 해당 합니다. 기본 텍스트 버퍼의 긴 줄은 부분적으로 가려져 있거나 (단어 잘림을 사용 하지 않는 경우) 여러 텍스트 보기 줄로 나눌 수 있습니다. 인터페이스에는 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 좌표와 문자 간의 매핑과 선으로 연결 될 수 있는 장식을 위한 메서드와 속성이 포함 되어 있습니다.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 개체는 인터페이스를 사용 하 여 생성 됩니다 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> . 뷰에 현재 표시 되는 텍스트에 대 한 관심이 있는 경우 서식 지정 원본을 무시할 수 있습니다. 보기에 표시 되지 않는 텍스트 형식 (예: 서식 있는 텍스트 잘라내기 및 붙여넣기를 지원 하기 위해)에 관심이 있는 경우를 사용 하 여 텍스트 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 버퍼의 텍스트에 서식을 지정할 수 있습니다.

텍스트 뷰는 한 번에 하나씩 서식 지정 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 됩니다.

## <a name="editor-features"></a>편집기 기능

편집기의 기능을 구현 하는 것과 별개의 기능입니다. 편집기에는 다음 기능이 포함 되어 있습니다.

- 태그 및 분류자

- 도구 영역

- 프로젝션

- 개요

- 마우스 및 키 바인딩

- 작업 및 기본 형식

- IntelliSense

### <a name="tags-and-classifiers"></a>태그 및 분류자

태그는 텍스트 범위와 연결 된 표식입니다. 텍스트 색 지정, 밑줄, 그래픽 또는 팝업을 사용 하는 등의 다양 한 방법으로 표시할 수 있습니다. 분류자는 태그의 한 종류입니다.

다른 종류의 태그는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 텍스트 강조 표시, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 개요 및 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 컴파일 오류에 대 한 것입니다.

#### <a name="classification-types"></a>분류 유형

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>인터페이스는 텍스트의 추상 범주인 동치 클래스를 나타냅니다. 분류 유형은 다른 분류 유형에 서 여러 상속할 수 있습니다. 예를 들어 프로그래밍 언어 분류에는 "코드"에서 모두 상속 되는 "keyword", "comment" 및 "identifier"가 포함 될 수 있습니다. 자연어 분류 형식에는 "명사", "verb" 및 "형용사"가 포함 될 수 있으며이는 모두 "자연어"에서 상속 됩니다.

#### <a name="classifications"></a>분류

분류는 일반적으로 텍스트 범위에 대 한 특정 분류 형식의 인스턴스입니다. 는 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 분류를 나타내는 데 사용 됩니다. 분류 범위는 특정 텍스트 범위를 포함 하는 레이블로 간주할 수 있으며,이 텍스트 범위가 특정 분류 유형인 것을 시스템에 알려줍니다.

#### <a name="classifiers"></a>분류자

는 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 텍스트를 분류 집합으로 분할 하는 메커니즘입니다. 분류자는 특정 콘텐츠 형식에 대해 정의 되어야 하며 특정 텍스트 버퍼에 대해 인스턴스화됩니다. 클라이언트는 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 를 구현 하 여 텍스트 분류에 참여 해야 합니다.

#### <a name="classifier-aggregators"></a>분류자 집계

분류자 집계는 한 텍스트 버퍼의 모든 분류자를 하나의 분류 집합에만 결합 하는 메커니즘입니다. 예를 들어 c # 분류자와 영어 분류자는 모두 c # 파일에서 주석에 대 한 분류를 만들 수 있습니다. 다음 설명을 참조 하십시오.

```
// This method produces a classifier
```

C # 분류자는 전체 범위에 대 한 주석을 주석으로 처리 하 고, 영어 분류자는 "생성"을 "동사"로, "method"를 "명사"로 분류할 수 있습니다. 집계는 겹치지 않는 분류 집합을 생성 하 고 집합의 유형은 모든 기여를 기반으로 합니다.

또한 분류자 집계는 텍스트를 분류 집합으로 분할 하므로 분류자입니다. 또한 분류자 집계를 사용 하면 겹치는 분류가 없고 분류가 정렬 됩니다. 개별 분류자는 임의의 순서에 관계 없이 모든 분류 집합을 자유롭게 반환 하 고 어떤 방식으로든 겹칠 수 있습니다.

#### <a name="classification-formatting-and-text-coloring"></a>분류 서식 지정 및 텍스트 색 지정

텍스트 서식 지정은 텍스트 분류를 기반으로 하는 기능의 예입니다. 텍스트 뷰 계층에서 응용 프로그램의 텍스트 표시를 확인 하는 데 사용 됩니다. 텍스트 서식 영역은 WPF에 종속 되지만 분류의 논리적 정의는 그렇지 않습니다.

분류 형식은 특정 분류 유형에 대 한 서식 속성의 집합입니다. 이러한 형식은 분류 형식의 부모 형식에서 상속 됩니다.

는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 분류 형식에서 텍스트 서식 속성 집합으로의 매핑입니다. 편집기에서 형식 맵의 구현은 분류 형식의 모든 내보내기를 처리 합니다.

### <a name="adornments"></a>도구 영역

장식은 텍스트 뷰의 문자 글꼴 및 색과 직접적으로 관련 되지 않은 그래픽 효과입니다. 예를 들어, 대부분의 프로그래밍 언어에서 비 컴파일 코드를 표시 하는 데 사용 되는 빨간색 물결선 밑줄은 포함 된 장식 이며 도구 설명은 팝업 장식입니다. 장식은에서 파생 되며를 <xref:System.Windows.UIElement> 구현 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> 합니다. <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>뷰의 텍스트와 동일한 공간을 차지 하는 장식의 경우 두 가지 특수화 된 장식 태그 형식 및에 대 한는 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 물결선 밑줄의입니다.

포함 된 장식은 서식이 지정 된 텍스트 보기의 일부를 구성 하는 그래픽입니다. 서로 다른 Z 순서 계층으로 구성 됩니다. 다음과 같이 세 가지 기본 제공 계층이 있습니다. 텍스트, 캐럿 및 선택 항목입니다. 그러나 개발자는 더 많은 계층을 정의 하 고 서로 관련 하 여 순서 대로 배치할 수 있습니다. 세 가지 종류의 포함 된 장식을 텍스트를 기준으로 하는 장식 (텍스트를 이동할 때, 텍스트를 삭제할 때 삭제 됨), 보기 관련 장식 (뷰의 텍스트가 아닌 부분과 함께 사용 해야 함) 및 소유자가 제어 하는 장식 (개발자가 배치를 관리 해야 함)입니다.

팝업 도구는 텍스트 보기 위의 작은 창 (예: 도구 설명)에 표시 되는 그래픽입니다.

### <a name="projection"></a><a name="projection"></a> 투사

프로젝션은 실제로 텍스트를 저장 하지 않고 다른 텍스트 버퍼의 텍스트를 조합 하는 다른 종류의 텍스트 버퍼를 생성 하는 기술입니다. 예를 들어, 프로젝션 버퍼를 사용 하 여 두 개의 다른 버퍼에서 텍스트를 연결 하 고 결과를 하나의 버퍼에 있는 것 처럼 표시 하거나 한 버퍼에서 텍스트 부분을 숨길 수 있습니다. 프로젝션 버퍼는 다른 프로젝션 버퍼에 대 한 소스 버퍼 역할을 할 수 있습니다. 여러 가지 방법으로 텍스트를 다시 정렬 하기 위해 프로젝션과 관련 된 버퍼 집합을 생성할 수 있습니다. 이러한 집합을 *버퍼 그래프*라고도 합니다. Visual Studio 텍스트 개요 기능은 프로젝션 버퍼를 사용 하 여 축소 된 텍스트를 숨기고 구현 되며, Visual Studio editor for ASP.NET 페이지는 프로젝션을 사용 하 여 Visual Basic 및 c #과 같은 포함 된 언어를 지원 합니다.

는를 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 사용 하 여 만듭니다 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . 프로젝션 버퍼는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> *소스 범위*라고 하는 개체의 순서가 지정 된 시퀀스로 표시 됩니다. 이러한 범위의 내용은 일련의 문자로 표시 됩니다. 소스 범위를 그리는 텍스트 버퍼에는 *소스 버퍼*라는 이름이 지정 됩니다. 프로젝션 버퍼의 클라이언트는 일반 텍스트 버퍼와 다르다는 점을 인식 하지 않아도 됩니다.

프로젝션 버퍼는 소스 버퍼에서 텍스트 변경 이벤트를 수신 대기 합니다. 소스 범위의 텍스트가 변경 되 면 프로젝션 버퍼는 변경 된 텍스트 좌표를 고유한 좌표로 매핑하고 적절 한 텍스트 변경 이벤트를 발생 시킵니다. 예를 들어 다음 내용이 포함 된 원본 버퍼 A와 B를 살펴보겠습니다.

```
A: ABCDE
B: vwxyz
```

프로젝션 버퍼 P가 모든 버퍼 A를 포함 하 고 다른 하나는 버퍼 B를 모두 포함 하는 두 개의 텍스트 범위에서 형성 되는 경우 P에는 다음과 같은 내용이 있습니다.

```
P: ABCDEvwxyz
```

부분 문자열이 `xy` 버퍼 B에서 삭제 되는 경우 버퍼 P는 7과 8 위치의 문자가 삭제 되었음을 나타내는 이벤트를 발생 시킵니다.

프로젝션 버퍼를 직접 편집할 수도 있습니다. 적절 한 소스 버퍼에 대 한 편집 내용을 전파 합니다. 예를 들어 문자열을 6 번 (문자 "v"의 원래 위치)의 버퍼 P에 삽입 하는 경우 삽입은 위치 1의 버퍼 B로 전파 됩니다.

프로젝션 버퍼에 영향을 주는 소스 범위에는 제한이 있습니다. 소스 범위는 겹칠 수 없습니다. 프로젝션 버퍼의 위치는 모든 소스 버퍼의 둘 이상의 위치로 매핑될 수 없으며, 소스 버퍼의 위치는 프로젝션 버퍼의 둘 이상의 위치에 매핑할 수 없습니다. 원본 버퍼 관계에는 circularities이 허용 되지 않습니다.

프로젝션 버퍼에 대 한 원본 버퍼 집합이 변경 되 고 소스 범위 집합이 변경 되 면 이벤트가 발생 합니다.
생략 버퍼는 특별 한 종류의 프로젝션 버퍼입니다. 주로 개요 및 텍스트 블록을 확장 및 축소 하는 작업에 사용 됩니다. 생략 버퍼는 소스 버퍼를 하나만 기반으로 하며, 생략 버퍼의 범위는 소스 버퍼에서 정렬 되는 것과 동일 하 게 정렬 되어야 합니다.

#### <a name="the-buffer-graph"></a>버퍼 그래프

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>인터페이스를 사용 하면 프로젝션 버퍼 그래프에서 매핑을 사용할 수 있습니다. 모든 텍스트 버퍼 및 프로젝션 버퍼는 언어 컴파일러에 의해 생성 되는 추상 구문 트리와 매우 유사 하 게 방향이 지정 된 비순환 그래프에 수집 됩니다. 그래프는 텍스트 버퍼 일 수 있는 최상위 버퍼에 의해 정의 됩니다. 버퍼 그래프는 최상위 버퍼의 지점에서 원본 버퍼의 지점으로 또는 최상위 버퍼의 범위에서 원본 버퍼의 범위 집합으로 매핑할 수 있습니다. 마찬가지로 소스 버퍼의 점 또는 범위를 최상위 버퍼의 지점에 매핑할 수 있습니다. 버퍼 그래프는를 사용 하 여 만듭니다 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>이벤트 및 프로젝션 버퍼

프로젝션 버퍼를 수정 하면 프로젝션 버퍼에서이를 종속 하는 버퍼로 수정 내용이 전송 됩니다. 모든 버퍼를 수정한 후에는 가장 깊은 버퍼부터 시작 하 여 버퍼 변경 이벤트가 발생 합니다.

### <a name="outlining"></a>개요

개요는 텍스트 보기에서 다양 한 텍스트 블록을 확장 하거나 축소 하는 기능입니다. 개요는 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> 장식이 정의 된 것과 같은 방식으로 일종의으로 정의 됩니다. 는 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 확장 하거나 축소할 수 있는 텍스트 영역을 정의 하는 태그입니다. 개요를 사용 하려면을 가져와서을 가져와야 합니다 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . 개요 관리자는 개체로 표시 되는 다양 한 블록을 열거, 축소 및 확장 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 하 고 그에 따라 이벤트를 발생 시킵니다.

### <a name="mouse-bindings"></a>마우스 바인딩

마우스 바인딩은 마우스 움직임을 다른 명령에 연결 합니다. 마우스 바인딩은를 사용 하 여 정의 되며 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> 키 바인딩은를 사용 하 여 정의 됩니다 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . 는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 모든 바인딩을 자동으로 인스턴스화하고 뷰의 마우스 이벤트에 연결 합니다.

인터페이스에는 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> 다른 마우스 이벤트에 대 한 프로세스 전 및 처리 후 이벤트 처리기가 포함 되어 있습니다. 이벤트 중 하나를 처리 하려면의 메서드 중 일부를 재정의할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>편집기 작업

편집기 작업을 사용 하 여 스크립트 또는 다른 용도로 편집기와의 상호 작용을 자동화할 수 있습니다. 를 가져와서 지정 된에 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 대 한 작업에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . 이러한 개체를 사용 하 여 선택 영역을 수정 하거나, 뷰를 스크롤하거나, 캐럿을 뷰의 다른 부분으로 이동할 수 있습니다.

### <a name="intellisense"></a>IntelliSense

IntelliSense는 문 완성, 시그니처 도움말 (매개 변수 정보 라고도 함), 요약 정보 및 light 전구 지원 합니다.

문 완성은 메서드 이름, XML 요소 및 기타 코딩 또는 태그 요소에 대 한 잠재적 완성의 팝업 목록을 제공 합니다. 일반적으로 사용자 제스처는 완료 세션을 호출 합니다. 세션에는 잠재적 완성 목록이 표시 되며 사용자는이를 선택 하 여 목록을 해제할 수 있습니다. 는를 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 만들고 트리거하는 역할을 담당 합니다 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . 는 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 세션에 대 한 완료 항목의를 계산 합니다.

## <a name="see-also"></a>추가 정보

- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
- [편집기 가져오기](../extensibility/editor-imports.md)
