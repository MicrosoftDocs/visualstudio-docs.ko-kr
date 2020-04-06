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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710322"
---
# <a name="inside-the-editor"></a>편집기 내부

편집기는 텍스트 보기 및 사용자 인터페이스와 별도로 편집기 텍스트 모델을 유지하도록 설계된 여러 하위 시스템으로 구성됩니다.

이 섹션에서는 편집기의 다양한 측면을 설명합니다.

- [하위 시스템의 개요](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [텍스트 모델](../extensibility/inside-the-editor.md#the-text-model)

- [텍스트 보기](../extensibility/inside-the-editor.md#the-text-view)

이 섹션에서는 편집기의 기능을 설명합니다.

- [태그 및 분류기](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [장식](../extensibility/inside-the-editor.md#adornments)

- [프로젝션](../extensibility/inside-the-editor.md#projection)

- [개요](../extensibility/inside-the-editor.md#outlining)

- [마우스 바인딩](../extensibility/inside-the-editor.md#mouse-bindings)

- [편집기 작업](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>하위 시스템의 개요

### <a name="text-model-subsystem"></a>텍스트 모델 하위 시스템

텍스트 모델 하위 시스템은 텍스트를 표현하고 텍스트를 조작할 책임이 있습니다. 텍스트 모델 하위 시스템에는 편집기에서 표시할 문자 의 시퀀스를 설명하는 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 인터페이스가 포함되어 있습니다. 이 텍스트는 여러 가지 방법으로 수정, 추적 및 조작할 수 있습니다. 텍스트 모델은 다음 측면에 대한 형식도 제공합니다.

- 텍스트를 파일과 연결하여 파일 시스템에서 읽고 쓰는 서비스를 관리합니다.

- 두 개체 시퀀스 간의 최소 차이점을 찾는 서로 다른 서비스입니다.

- 다른 버퍼의 텍스트 하위 집합측면에서 버퍼의 텍스트를 설명하는 시스템입니다.

텍스트 모델 하위 시스템은 UI(사용자 인터페이스) 개념이 없습니다. 예를 들어 텍스트 서식이나 텍스트 레이아웃에 대한 책임은 없으며 텍스트와 연관될 수 있는 시각적 장식에 대한 지식이 없습니다.

텍스트 모델 하위 시스템의 공용 형식은 .NET Framework 기본 클래스 라이브러리 및 관리되는 확장성 프레임워크(MEF)에만 의존하는 *Microsoft.VisualStudio.Text.Data.dll* 및 *Microsoft.VisualStudio.CoreUtility.dll에*포함되어 있습니다.

### <a name="text-view-subsystem"></a>텍스트 보기 하위 시스템

텍스트 보기 하위 시스템은 텍스트의 서식 을 지정하고 표시합니다. 이 하위 시스템의 형식은 형식이 WPF(Windows 프레젠테이션 기반)에 의존하는지 여부에 따라 두 계층으로 나뉩니다. 가장 중요한 유형은 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>표시할 텍스트 줄 집합과 WPF UI 요소를 사용하여 텍스트를 장식하는 캐리트, 선택 및 텍스트를 표시하기 위한 시설도 제어하는 형식입니다. <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 이 하위 시스템은 텍스트 표시 영역 주위에 여백을 제공합니다. 이러한 여백은 확장할 수 있으며 다양한 종류의 콘텐츠 및 시각 효과를 포함할 수 있습니다. 여백의 예로는 줄 번호 표시 및 스크롤 막대가 있습니다.

텍스트 보기 하위 시스템의 공용 형식은 *Microsoft.VisualStudio.Text.UI.dll* 및 *Microsoft.VisualStudio.Text.UI.Wpf.dll*에 포함되어 있습니다. 첫 번째 어셈블리에는 플랫폼 독립적 요소가 포함되고 두 번째 어셈블리에는 WPF 관련 요소가 포함됩니다.

### <a name="classification-subsystem"></a>분류 하위 시스템

분류 하위 시스템은 텍스트에 대한 글꼴 속성을 결정합니다. 분류자는 텍스트를 "키워드" 또는 "주석"과 같은 다른 클래스로 나눕니다. 분류 형식 맵은 이러한 클래스를 실제 글꼴 속성(예: "Blue Consolas 10 pt")과 관련이 있습니다. 이 정보는 텍스트의 서식을 지정하고 렌더링할 때 텍스트 뷰에서 사용됩니다. 이 항목의 후반부에서 자세히 설명하는 태그 지정을 사용하면 데이터를 텍스트 범위와 연결할 수 있습니다.

분류 하위 시스템의 공용 유형은 Microsoft.VisualStudio.Text.Logic.dll에 포함되어 있으며 Microsoft.VisualStudio.Text.UI.Wpf.dll에 포함된 분류의 시각적 측면과 상호 작용합니다.

### <a name="operations-subsystem"></a>운영 하위 시스템

작업 하위 시스템은 편집기 동작을 정의합니다. Visual Studio 편집기 명령 및 실행 취소 시스템에 대한 구현을 제공합니다.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>텍스트 모델과 텍스트 보기를 자세히 살펴봅니다.

### <a name="the-text-model"></a>텍스트 모델

텍스트 모델 하위 시스템은 텍스트 유형의 여러 그룹으로 구성됩니다. 여기에는 텍스트 버퍼, 텍스트 스냅숏 및 텍스트 범위가 포함됩니다.

#### <a name="text-buffers-and-text-snapshots"></a>텍스트 버퍼 및 텍스트 스냅샷

인터페이스는 <xref:Microsoft.VisualStudio.Text.ITextBuffer> .NET Framework의 `String` 형식에서 사용되는 인코딩인 UTF-16을 사용하여 인코딩되는 유니코드 문자 시퀀스를 나타냅니다. 텍스트 버퍼는 파일 시스템 문서로 유지될 수 있지만 필수는 아닙니다.

는 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> 빈 텍스트 버퍼 또는 문자열또는 에서 <xref:System.IO.TextReader>초기화 된 텍스트 버퍼를 만드는 데 사용됩니다. 텍스트 버퍼를 파일 시스템에 <xref:Microsoft.VisualStudio.Text.ITextDocument>로 유지될 수 있습니다.

모든 스레드는 스레드가 를 호출하여 텍스트 버퍼의 소유권을 취할 때까지 텍스트 버퍼를 편집할 수 있습니다. <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> 그런 다음 해당 스레드만 편집을 수행할 수 있습니다.

텍스트 버퍼는 수명 동안 여러 버전을 통과할 수 있습니다. 버퍼를 편집할 때마다 새 버전이 생성되고 변경할 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 수 없는 버퍼의 해당 버전의 내용을 나타냅니다. 텍스트 스냅숏은 변경할 수 없으므로 텍스트 스냅숏이 나타내는 텍스트 버퍼가 계속 변경되더라도 제한 없이 모든 스레드에서 텍스트 스냅숏에 액세스할 수 있습니다.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>텍스트 스냅샷 및 텍스트 스냅샷 선

텍스트 스냅숏의 내용을 문자 시퀀스 또는 선 시퀀스로 볼 수 있습니다. 문자와 줄은 모두 0부터 인덱싱됩니다. 빈 텍스트 스냅샷에는 문자가 0이고 빈 줄이 하나 있습니다. 줄은 유효한 유니코드 줄 바그 문자 시퀀스 또는 버퍼의 시작 또는 끝에 의해 구분됩니다. 줄 바꿈 문자는 텍스트 스냅숏에 명시적으로 표현되며 텍스트 스냅숏의 줄 바꿈이 모두 같을 필요는 없습니다.

> [!NOTE]
> Visual Studio 편집기의 줄 바꿈 문자에 대한 자세한 내용은 [인코딩 및 줄 바꿈을](../ide/encodings-and-line-breaks.md)참조하십시오.

텍스트 줄은 특정 줄 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 번호 또는 특정 문자 위치에 대한 텍스트 스냅샷에서 가져올 수 있는 개체로 표시됩니다.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>스냅샷 포인트, 스냅숏스팬 및 정규화된 스냅샷스팬컬렉션

A는 <xref:Microsoft.VisualStudio.Text.SnapshotPoint> 스냅샷의 문자 위치를 나타냅니다. 위치는 스냅샷의 길이0과 길이 사이에 위치가 보장됩니다. A는 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 스냅샷의 텍스트 범위를 나타냅니다. 끝 위치는 스냅숏의 길이와 0 사이에 위치하도록 보장됩니다. 는 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 동일한 스냅샷의 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 개체 집합으로 구성됩니다.

#### <a name="spans-and-normalizedspancollections"></a>범위 및 정규화된 범위컬렉션

A는 <xref:Microsoft.VisualStudio.Text.Span> 텍스트 스냅샷의 텍스트 범위에 적용할 수 있는 간격을 나타냅니다. 스냅샷 위치는 0기반이므로 스팬은 0을 포함한 모든 위치에서 시작할 수 있습니다. 범위의 `End` 속성은 해당 `Start` 속성과 해당 `Length` 속성의 합계와 같습니다. A는 `Span` `End` 속성에 의해 인덱싱되는 문자를 포함하지 않습니다. 예를 들어 시작=5 및 Length=3이 있는 범위에는 End=8이 있으며 위치 5, 6 및 7의 문자를 포함합니다. 이 범위에 대한 표기는 [5..8)입니다.

끝 위치를 포함하여 공통된 위치가 있는 경우 두 범위가 교차합니다. 따라서[3, 5) 및 [2, 7)의 교차점은 [3, 5) 및 [3, 5)]와 [5, 7)의 교차점이 [5, 5)이다. ([5, 5)는 빈 범위입니다.)

끝 위치를 제외한 공통 위치가 있는 경우 두 범위가 겹칩니다. 빈 범위는 다른 범위와 겹치지 않으며 두 범위의 겹치는 것은 비어 없습니다.

A는 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> 범위의 시작 속성 순서대로 범위 목록입니다. 목록에서 겹치거나 인부팅범위가 병합됩니다. 예를 들어 범위 집합 [5..9), [0..1), [3..6), [9..10)을 감안할 때 정규화된 범위 목록은 [0..1), [3..10)입니다.

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, 텍스트 버전 및 텍스트 변경 알림

텍스트 버퍼의 내용은 개체를 <xref:Microsoft.VisualStudio.Text.ITextEdit> 사용하여 변경할 수 있습니다. 이러한 개체를 `CreateEdit()` 만들면(메서드 중 <xref:Microsoft.VisualStudio.Text.ITextBuffer>하나를 사용하여) 텍스트 편집으로 구성된 텍스트 트랜잭션이 시작됩니다. 모든 편집은 버퍼의 일부 텍스트 범위를 문자열로 대체합니다. 모든 편집의 좌표와 내용은 트랜잭션이 시작될 때 버퍼의 스냅숏을 기준으로 표현됩니다. 개체는 <xref:Microsoft.VisualStudio.Text.ITextEdit> 동일한 트랜잭션의 다른 편집의 영향을 받는 편집 의 좌표를 조정합니다.

예를 들어 이 문자열이 포함된 텍스트 버퍼를 생각해 보십시오.

```
abcdefghij
```

문자를 사용하여 [2..4)에서 범위를 대체하는 두 개의 편집내용과 [6..9]에서 `X` 범위를 대체하는 두 번째 편집을 포함하는 트랜잭션을 `Y`적용합니다. 결과는 이 버퍼입니다.

```
abXefYj
```

두 번째 편집에 대한 좌표는 첫 번째 편집이 적용되기 전에 트랜잭션 시작 시 버퍼의 내용에 대해 계산되었습니다.

버퍼에 대한 변경 사항은 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체가 해당 `Apply()` 메서드를 호출하여 커밋될 때 적용됩니다. 비어 없는 편집이 하나 이상 있는 경우 <xref:Microsoft.VisualStudio.Text.ITextVersion> 새 편집이 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 만들어지고 새 `Changed` 이벤트가 만들어지며 하나의 이벤트가 발생합니다. 모든 텍스트 버전에는 다른 텍스트 스냅샷이 있습니다. 텍스트 스냅숏은 편집 트랜잭션 후 텍스트 버퍼의 전체 상태를 나타내지만 텍스트 버전은 한 스냅숏에서 다음 스냅숏으로의 변경 내용만 설명합니다. 일반적으로 텍스트 스냅숏은 한 번 사용한 다음 삭제하는 반면 텍스트 버전은 한동안 살아 있어야 합니다.

텍스트 버전에는 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>을 포함합니다. 이 컬렉션은 스냅숏에 적용될 때 후속 스냅숏을 생성하는 변경 내용을 설명합니다. 컬렉션의 모든 <xref:Microsoft.VisualStudio.Text.ITextChange> 변경 내용의 문자 위치, 대체 된 문자열 및 대체 문자열이 포함 됩니다. 대체된 문자열은 기본 삽입을 위해 비어 있고 기본 삭제를 위해 대체 문자열이 비어 있습니다. 정규화된 컬렉션은 `null` 항상 텍스트 버퍼의 최신 버전에 대한 것입니다.

언제든지 <xref:Microsoft.VisualStudio.Text.ITextEdit> 텍스트 버퍼에 대해 하나의 개체만 인스턴스화할 수 있으며 소유권이 요구된 경우 텍스트 버퍼를 소유한 스레드에서 모든 텍스트 편집을 수행해야 합니다. 텍스트 편집은 메서드 또는 메서드를 `Cancel` `Dispose` 호출하여 중단될 수 있습니다.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>또한 `Insert()`인터페이스에서 `Replace()` 찾은 것과 유사한 <xref:Microsoft.VisualStudio.Text.ITextEdit> 및 `Delete()`메서드를 제공합니다. 이러한 호출은 <xref:Microsoft.VisualStudio.Text.ITextEdit> 개체를 만들고, 유사한 호출을 한 다음 편집을 적용하는 것과 동일한 효과가 있습니다.

#### <a name="tracking-points-and-tracking-spans"></a>추적 지점 및 추적 범위

A는 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> 텍스트 버퍼의 문자 위치를 나타냅니다. 캐릭터의 위치를 이동시키는 방식으로 버퍼를 편집하면 추적 점이 함께 이동합니다. 예를 들어 추적 점이 버퍼의 위치 10을 참조하고 버퍼의 시작 부분에 5개의 문자가 삽입된 경우 추적 점은 위치 15를 참조합니다. 삽입이 추적 점에 의해 표시된 위치에서 정확하게 발생하는 경우 해당 동작은 <xref:Microsoft.VisualStudio.Text.PointTrackingMode>중 하나 `Positive` 또는 `Negative`에 의해 결정됩니다. 추적 모드가 양수이면 추적 점은 삽입끝에 있는 동일한 문자를 나타냅니다. 추적 모드가 음수이면 추적 점은 원래 위치에 처음 삽입된 문자를 나타냅니다. 추적 점으로 표시되는 위치에 있는 문자가 삭제되면 추적 점이 삭제된 범위를 따르는 첫 번째 문자로 이동합니다. 예를 들어 추적 지점이 위치 5의 문자를 참조하고 위치 3부터 6까지의 문자가 삭제되는 경우 추적 점은 위치 3의 문자를 참조합니다.

A는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 한 위치가 아닌 다양한 문자를 나타냅니다. 해당 동작은 에 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>의해 결정됩니다. 범위 추적 모드가 [SpanTrackingMode.Edge포함인](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)경우 추적 범위는 해당 가장자리에 삽입된 텍스트를 통합하도록 증가합니다. 범위 추적 모드가 [SpanTrackingMode.EdgeExclusive인](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)경우 추적 범위는 가장자리에 삽입된 텍스트를 포함하지 않습니다. 그러나 범위 추적 모드가 [SpanTrackingMode.EdgePositive인](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)경우 삽입은 현재 위치를 시작 쪽으로 밀어 내고 범위 추적 모드가 [SpanTrackingMode.EdgeNegative인](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)경우 삽입은 현재 위치를 끝까지 밀어 넣습니다.

추적 지점의 위치 또는 추적 범위의 범위를 사용하여 해당 지점이 속한 텍스트 버퍼의 스냅숏을 얻을 수 있습니다. 추적 지점 및 추적 범위는 모든 스레드에서 안전하게 참조할 수 있습니다.

#### <a name="content-types"></a>내용 유형

콘텐츠 형식은 다양한 종류의 콘텐츠를 정의하는 메커니즘입니다. 콘텐츠 형식은 "텍스트", "코드" 또는 "이진"과 같은 파일 형식이거나 "xml", "vb" 또는 "c#"과 같은 기술 유형일 수 있습니다. 예를 들어 "using"라는 단어는 C# 및 Visual Basic의 키워드이지만 다른 프로그래밍 언어에서는 사용할 수 없습니다. 따라서 이 키워드의 정의는 "c#" 및 "vb" 콘텐츠 유형으로 제한됩니다.

콘텐츠 형식은 장식 및 편집기의 다른 요소에 대한 필터로 사용됩니다. 많은 편집기 기능 및 확장 지점은 콘텐츠 유형에 따라 정의됩니다. 예를 들어 일반 텍스트 파일, XML 파일 및 Visual Basic 소스 코드 파일의 경우 텍스트 색칠이 다릅니다. 텍스트 버퍼는 일반적으로 만들 때 콘텐츠 형식이 할당되며 텍스트 버퍼의 콘텐츠 형식을 변경할 수 있습니다.

콘텐츠 형식은 다른 콘텐츠 형식에서 여러 상속할 수 있습니다. 여러 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> 기본 형식을 지정된 콘텐츠 형식의 부모로 지정할 수 있습니다.

개발자는 자신의 콘텐츠 형식을 정의하고 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>을 사용하여 등록할 수 있습니다. 많은 편집기 기능을 사용하여 특정 콘텐츠 유형에 대해 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>정의할 수 있습니다. 예를 들어 편집기 여백, 장식 및 마우스 처리기를 정의하여 특정 콘텐츠 형식을 표시하는 편집기에만 적용할 수 있습니다.

### <a name="the-text-view"></a>텍스트 보기

모델 뷰 컨트롤러(MVC) 패턴의 뷰 부분은 텍스트 뷰, 뷰의 서식, 스크롤 막대와 같은 그래픽 요소 및 caret를 정의합니다. 비주얼 스튜디오 편집기의 모든 프레젠테이션 요소는 WPF를 기반으로 합니다.

#### <a name="text-views"></a>텍스트 보기

인터페이스는 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 텍스트 뷰의 플랫폼 독립적 표현입니다. 주로 창에 텍스트 문서를 표시하는 데 사용되지만 도구 설명과 같은 다른 용도로도 사용할 수 있습니다.

텍스트 보기는 다양한 종류의 텍스트 버퍼를 참조합니다. 속성은 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> 이러한 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 세 가지 다른 텍스트 버퍼를 가리키는 개체를 참조합니다: 최상위 데이터 수준 버퍼인 데이터 버퍼, 편집이 발생하는 편집 버퍼 및 텍스트 보기에 표시되는 버퍼인 시각적 버퍼입니다.

텍스트는 기본 텍스트 버퍼에 연결된 분류자를 기반으로 서식이 지정되며 텍스트 뷰 자체에 연결된 장식 공급자를 사용하여 장식됩니다.

#### <a name="the-text-view-coordinate-system"></a>텍스트 뷰 좌표계

텍스트 뷰 좌표 계는 텍스트 뷰의 위치를 지정합니다. 이 좌표계에서 x 값 0.0은 표시되는 텍스트의 왼쪽 가장자리에 해당하며 y 값 0.0은 표시되는 텍스트의 위쪽 가장자리에 해당합니다. x 좌표는 왼쪽에서 오른쪽으로 증가하고 y 좌표는 위에서 아래로 증가합니다.

뷰포트(텍스트 창에 표시되는 텍스트 부분)는 세로로 스크롤될 때와 동일한 방식으로 가로로 스크롤할 수 없습니다. 뷰포트는 왼쪽 좌표를 변경하여 드로잉 서피스를 따라 이동하도록 가로로 스크롤됩니다. 그러나 뷰포트는 렌더링된 텍스트를 변경하여서만 세로로 스크롤할 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 수 있으며, 이로 인해 이벤트가 발생합니다.

좌표계의 거리는 논리 픽셀에 해당합니다. 텍스트 렌더링 표면이 배율 변환 없이 표시되는 경우 텍스트 렌더링 좌표계의 한 단위는 디스플레이의 한 픽셀에 해당합니다.

#### <a name="margins"></a>여백

인터페이스는 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> 여백을 나타내며 여백과 그 크기에 대한 가시성을 제어할 수 있습니다. 미리 정의된 여백은 "위쪽", "왼쪽", "오른쪽" 및 "아래쪽"으로 명명되며 뷰의 위쪽, 아래쪽, 왼쪽 또는 오른쪽 가장자리에 연결됩니다. 이러한 여백은 다른 여백을 배치할 수 있는 컨테이너입니다. 인터페이스는 여백의 크기와 여백의 가시성을 반환하는 메서드를 정의합니다. 여백은 첨부된 텍스트 보기에 대한 추가 정보를 제공하는 시각적 요소입니다. 예를 들어 줄 번호 여백에는 텍스트 보기에 대한 선 번호가 표시됩니다. 글리프 여백에는 UI 요소가 표시됩니다.

인터페이스는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> 여백생성 및 배치를 처리합니다. 여백은 다른 여백과 관련하여 정렬할 수 있습니다. 우선 순위가 높은 여백은 텍스트 보기에 더 가깝게 배치됩니다. 예를 들어 왼쪽 여백 A와 여백 B가 두 개 있고 여백 B가 여백 A보다 우선 순위가 낮은 경우 여백 B가 여백 A의 왼쪽에 나타납니다.

#### <a name="the-text-view-host"></a>텍스트 보기 호스트

인터페이스에는 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 텍스트 보기와 스크롤 막대와 같은 뷰와 함께 제공되는 인접 장식이 포함되어 있습니다. 텍스트 뷰 호스트에는 뷰 테두리에 연결된 여백도 포함되어 있습니다.

#### <a name="formatted-text"></a>서식 있는 텍스트

텍스트 보기에 표시되는 텍스트는 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 개체로 구성됩니다. 모든 텍스트 보기 줄은 텍스트 뷰의 한 줄의 텍스트에 해당합니다. 기본 텍스트 버퍼의 긴 줄은 부분적으로 가려지거나(단어 줄 바꿈이 활성화되지 않은 경우) 여러 텍스트 뷰 줄로 나눌 수 있습니다. 인터페이스에는 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 좌표와 문자 간의 매핑과 선과 연관될 수 있는 장식에 대한 메서드와 속성이 포함되어 있습니다.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>개체는 인터페이스를 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 사용하여 만들어집니다. 현재 보기에 표시되는 텍스트에 대해 염려하는 경우 서식 원본을 무시할 수 있습니다. 뷰에 표시되지 않는 텍스트 형식(예: 리치 텍스트 잘라내기 및 붙여넣기 지원)에 관심이 있는 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 경우 텍스트 버퍼에서 텍스트 의 서식을 지정하는 데 사용할 수 있습니다.

텍스트 보기는 한 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 번에 하나씩 서식을 지정합니다.

## <a name="editor-features"></a>편집기 기능

편집기의 기능은 기능의 정의가 구현과 분리되도록 설계되었습니다. 편집기에는 다음 기능이 포함되어 있습니다.

- 태그 및 분류기

- 장식

- 프로젝션

- 개요

- 마우스 및 키 바인딩

- 운영 및 원시

- IntelliSense

### <a name="tags-and-classifiers"></a>태그 및 분류기

태그는 텍스트 범위와 연결된 마커입니다. 예를 들어 텍스트 색칠, 밑줄, 그래픽 또는 팝업을 사용하여 다양한 방식으로 표시할 수 있습니다. 분류기는 하나의 종류의 태그입니다.

다른 종류의 태그는 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 텍스트 강조 표시, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 개요 및 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 컴파일 오류용입니다.

#### <a name="classification-types"></a>분류 유형

인터페이스는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> 텍스트의 추상 범주인 등가 클래스를 나타냅니다. 분류 유형은 다른 분류 유형에서 다중 상속할 수 있습니다. 예를 들어 프로그래밍 언어 분류에는 "코드", "주석"및 "식별자"가 포함될 수 있으며, 모두 "코드"에서 상속됩니다. 자연어 분류 유형에는 "명사", "동사" 및 "형용사"가 포함될 수 있으며, 모든 "자연어"에서 상속됩니다.

#### <a name="classifications"></a>분류

분류는 일반적으로 텍스트 범위에 걸쳐 특정 분류 유형의 인스턴스입니다. A는 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> 분류를 나타내는 데 사용됩니다. 분류 범위는 특정 텍스트 범위를 포함하는 레이블로 생각할 수 있으며 이 텍스트 범위가 특정 분류 유형임을 시스템에 알려줍니다.

#### <a name="classifiers"></a>분류자

A는 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 텍스트를 분류 집합으로 나누는 메커니즘입니다. 분류자는 특정 콘텐츠 유형에 대해 정의되고 특정 텍스트 버퍼에 대해 인스턴스화되어야 합니다. 클라이언트는 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 텍스트 분류에 참여하려면 구현해야 합니다.

#### <a name="classifier-aggregators"></a>분류자 집계기

분류자 집계는 하나의 텍스트 버퍼에 대한 모든 분류자를 하나의 분류 집합으로 결합하는 메커니즘입니다. 예를 들어 C# 분류자와 영어 분류자 모두 C# 파일의 주석에 대한 분류를 만들 수 있습니다. 이 주석을 고려하십시오.

```
// This method produces a classifier
```

C# 분류기는 전체 범위를 주석으로 레이블을 지정할 수 있으며 영어 분류기는 "생성"을 "동사"와 "메소드"를 "명사"로 분류할 수 있습니다. 집계는 겹치지 않는 분류 집합을 생성하며 집합의 형식은 모든 기여를 기반으로 합니다.

분류자 집계는 텍스트를 분류 집합으로 나누기 때문에 분류자이기도 합니다. 분류기 집계는 겹치는 분류가 없고 분류가 정렬되도록 합니다. 개별 분류자는 모든 분류 집합을 순서에 관계없이 반환할 수 있으며 어떤 방식으로든 겹칩니다.

#### <a name="classification-formatting-and-text-coloring"></a>분류 서식 및 텍스트 색칠

텍스트 서식지정은 텍스트 분류를 기반으로 하는 피쳐의 예입니다. 응용 프로그램에서 텍스트의 표시를 결정 하기 위해 텍스트 보기 레이어에 의해 사용 됩니다. 텍스트 서식 영역은 WPF에 따라 다르지만 분류의 논리적 정의는 그렇지 않습니다.

분류 형식은 특정 분류 유형에 대한 서식 속성 집합입니다. 이러한 형식은 분류 형식의 상위 형식에서 상속됩니다.

A는 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> 분류 유형에서 텍스트 서식 속성 집합에 이르는 맵입니다. 편집기에서 형식 맵의 구현은 분류 형식의 모든 내보내기를 처리합니다.

### <a name="adornments"></a>장식

장식은 텍스트 보기의 문자 글꼴 및 색상과 직접 관련이 없는 그래픽 효과입니다. 예를 들어 많은 프로그래밍 언어에서 컴파일되지 않은 코드를 표시하는 데 사용되는 빨간색 물결선 밑줄은 포함된 장식이며 도구 설명은 팝업 장식입니다. 장식에서 파생 <xref:System.Windows.UIElement> 되 고 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>구현 합니다. 두 가지 특수한 유형의 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>장식 태그는 뷰의 텍스트와 동일한 공간을 차지하는 장식에 대한 및 물결선 밑줄의 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>에 대한 입니다.

포함된 장식은 서식이 지정된 텍스트 보기의 일부를 구성하는 그래픽입니다. 그들은 다른 Z 순서 레이어로 구성되어 있습니다. 텍스트, 캐리트 및 선택 영역의 세 가지 기본 제공 레이어가 있습니다. 그러나 개발자는 더 많은 레이어를 정의하고 서로에 대해 순서대로 배치할 수 있습니다. 포함된 장식의 세 가지 종류는 텍스트 상대 장식(텍스트가 이동할 때 이동하고 텍스트가 삭제될 때 삭제됨), 뷰 상대 장식(뷰의 텍스트가 아닌 부분과 관련이 있음) 및 소유자가 제어하는 장식(개발자는 배치를 관리해야 함)입니다.

팝업 장식은 도구 설명과 같이 텍스트 보기 위의 작은 창에 나타나는 그래픽입니다.

### <a name="projection"></a><a name="projection"></a>프로젝션

프로젝션은 텍스트를 실제로 저장하지 않고 다른 텍스트 버퍼의 텍스트를 결합하는 다른 종류의 텍스트 버퍼를 생성하는 기술입니다. 예를 들어 프로젝션 버퍼를 사용하여 다른 두 버퍼에서 텍스트를 연결하여 하나의 버퍼에 있는 것처럼 결과를 표시하거나 텍스트의 일부를 하나의 버퍼에 숨길 수 있습니다. 프로젝션 버퍼는 다른 프로젝션 버퍼에 대한 소스 버퍼역할을 할 수 있습니다. 프로젝션과 관련된 버퍼 집합을 구성하여 다양한 방법으로 텍스트를 다시 정렬할 수 있습니다. (이러한 집합은 *버퍼 그래프라고도*합니다.) Visual Studio 텍스트 개요 기능은 프로젝션 버퍼를 사용하여 축소된 텍스트를 숨기고 ASP.NET 페이지의 Visual Studio 편집기는 프로젝션을 사용하여 Visual Basic 및 C#과 같은 임베디드 언어를 지원합니다.

A를 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> 사용하여 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>만들어집니다. 프로젝션 버퍼는 소스 범위라고 하는 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 정렬된 개체 시퀀스로 표시됩니다. *source spans* 이러한 범위의 내용은 문자 시퀀스로 표시됩니다. 소스 범위가 그려지는 텍스트 버퍼는 소스 *버퍼로*명명됩니다. 프로젝션 버퍼의 클라이언트는 일반 텍스트 버퍼와 다르다는 것을 알 필요가 없습니다.

프로젝션 버퍼는 소스 버퍼의 텍스트 변경 이벤트를 수신합니다. 소스 범위의 텍스트가 변경되면 프로젝션 버퍼는 변경된 텍스트 좌표를 자체 좌표에 매핑하고 적절한 텍스트 변경 이벤트를 발생시게 됩니다. 예를 들어 이러한 내용이 있는 소스 버퍼 A와 B를 고려합니다.

```
A: ABCDE
B: vwxyz
```

프로젝션 버퍼 P가 버퍼 A를 모두 포함하는 두 텍스트 범위와 버퍼 B를 모두 포함하는 텍스트 범위에서 형성되는 경우 P에는 다음 내용이 있습니다.

```
P: ABCDEvwxyz
```

버퍼 B에서 `xy` 하위 문자열이 삭제된 경우 버퍼 P는 위치 7과 8의 문자가 삭제되었음을 나타내는 이벤트를 발생시게 됩니다.

프로젝션 버퍼를 직접 편집할 수도 있습니다. 적절한 소스 버퍼에 편집을 전파합니다. 예를 들어, 문자열이 위치 6(문자 "v"의 원래 위치)에서 버퍼 P에 삽입된 경우 삽입은 위치 1에서 버퍼 B로 전파됩니다.

프로젝션 버퍼에 기여하는 소스 범위에 제한이 있습니다. 소스 범위가 겹치지 않을 수 있습니다. 프로젝션 버퍼의 위치는 소스 버퍼의 두 개 이상의 위치에 매핑할 수 없으며 소스 버퍼의 위치는 프로젝션 버퍼의 두 개 이상의 위치에 매핑할 수 없습니다. 원본 버퍼 관계에서는 순환이 허용되지 않습니다.

프로젝션 버퍼에 대한 소스 버퍼 집합이 변경되고 소스 집합이 변경될 때 이벤트가 발생합니다.
elision 버퍼는 특별한 종류의 프로젝션 버퍼입니다. 주로 텍스트 블록을 확장하고 축소하는 작업의 개요및 작업에 사용됩니다. elision 버퍼는 하나의 소스 버퍼를 기반으로 하며 elision 버퍼의 범위는 소스 버퍼에서 정렬된 것과 동일하게 정렬되어야 합니다.

#### <a name="the-buffer-graph"></a>버퍼 그래프

인터페이스를 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> 사용하면 프로젝션 버퍼 그래프에 매핑할 수 있습니다. 모든 텍스트 버퍼 및 프로젝션 버퍼는 언어 컴파일러에서 생성되는 추상 구문 트리와 마찬가지로 지시된 비순환 그래프로 수집됩니다. 그래프는 모든 텍스트 버퍼일 수 있는 맨 위 버퍼에 의해 정의됩니다. 버퍼 그래프는 최상위 버퍼의 한 지점에서 소스 버퍼의 한 지점으로 매핑하거나 맨 위 버퍼의 범위에서 소스 버퍼의 범위 집합으로 매핑할 수 있습니다. 마찬가지로 소스 버퍼에서 위쪽 버퍼의 점에 대한 점 또는 스팬을 매핑할 수 있습니다. 버퍼 그래프는 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>을 사용하여 만들어집니다.

#### <a name="events-and-projection-buffers"></a>이벤트 및 프로젝션 버퍼

프로젝션 버퍼가 수정되면 프로젝션 버퍼에서 종속된 버퍼로 수정사항이 전송됩니다. 모든 버퍼가 수정되면 가장 깊은 버퍼부터 시작하여 버퍼 변경 이벤트가 발생합니다.

### <a name="outlining"></a>개요

개요는 텍스트 보기에서 다른 텍스트 블록을 확장하거나 축소하는 기능입니다. 개요는 장식이 정의된 <xref:Microsoft.VisualStudio.Text.Tagging.ITag>것과 같은 방식으로 의 일종으로 정의됩니다. A는 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 확장하거나 축소할 수 있는 텍스트 영역을 정의하는 태그입니다. 개요를 사용하려면 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>을 가져오려면 을 가져와야 합니다. 개요 관리자는 개체로 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 표시되는 다른 블록을 확장, 축소 및 확장하고 그에 따라 이벤트를 발생시합니다.

### <a name="mouse-bindings"></a>마우스 바인딩

마우스 바인딩은 마우스 움직임을 다른 명령에 연결합니다. 마우스 바인딩은 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>을 사용하여 정의되며 키 바인딩은 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>을 사용하여 정의됩니다. 이 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> 바인딩은 자동으로 모든 바인딩을 인스턴스화하고 뷰의 마우스 이벤트에 연결합니다.

인터페이스에는 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> 서로 다른 마우스 이벤트에 대한 사전 프로세스 및 사후 프로세스 이벤트 처리기가 포함되어 있습니다. 이벤트 중 하나를 처리하려면 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>에서 일부 메서드를 재정의할 수 있습니다.

### <a name="editor-operations"></a>편집기 작업

편집기 작업은 스크립팅 또는 기타 목적으로 편집기와의 상호 작용을 자동화하는 데 사용할 수 있습니다. 을 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>가져올 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 수 있습니다. 그런 다음 이러한 객체를 사용하여 선택 영역을 수정하거나 뷰를 스크롤하거나 캐번을 뷰의 다른 부분으로 이동할 수 있습니다.

### <a name="intellisense"></a>IntelliSense

IntelliSense는 명령문 완료, 서명 도움말(매개 변수 정보라고도 함), 빠른 정보 및 전구를 지원합니다.

명령문 완성은 메서드 이름, XML 요소 및 기타 코딩 또는 태그 요소에 대한 잠재적 완료의 팝업 목록을 제공합니다. 일반적으로 사용자 제스처는 완료 세션을 호출합니다. 세션에는 잠재적완료 목록이 표시되며 사용자는 목록을 선택하거나 해제할 수 있습니다. 을 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> 만들고 트리거하는 것은 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>담당합니다. 세션의 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 완료 항목을 계산합니다.

## <a name="see-also"></a>참조

- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
- [편집기 가져오기](../extensibility/editor-imports.md)
