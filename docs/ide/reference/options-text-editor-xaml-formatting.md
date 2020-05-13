---
title: 옵션, 텍스트 편집기, XAML, 서식
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d340a3b9468ea23c4cab23aabe19a7c1390955a3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568245"
---
# <a name="options-text-editor-xaml-formatting"></a>옵션, 텍스트 편집기, XAML, 서식

**서식** 속성 페이지를 사용하여 XAML 문서에서 요소와 특성의 형식 지정 방법을 지정할 수 있습니다. **옵션** 대화 상자를 열려면 **도구** 메뉴를 클릭한 후 **옵션**을 클릭합니다. **서식 지정** 속성 페이지에 액세스하려면 **텍스트 편집기** > **XAML** > **서식 지정** 노드를 확장합니다.

## <a name="auto-formatting-events"></a>자동 서식 지정 이벤트

다음 이벤트가 검색되면 자동 서식 지정이 실행될 수 있습니다.

- 끝 태그 또는 단순 태그의 완료.

- 시작 태그의 완료.

- 클립보드에서 붙여넣기.

- 서식 키보드 명령.

자동 서식 지정을 일으키는 이벤트를 지정할 수 있습니다.

**끝 태그 또는 간단한 태그 완료 시**

끝 태그 또는 단순 태그의 입력을 완료하면 자동 서식 지정이 실행됩니다. 단순 태그에는 특성이 없습니다(예: `<Button />`).

**시작 태그 완료 시**

시작 태그 입력을 완료하면 자동 서식 지정이 실행됩니다.

**클립보드에서 붙여 넣을 때**

클립보드에서 XAML 보기로 XAML을 붙여넣으면 자동 서식 지정이 실행됩니다.

## <a name="quotation-mark-style"></a>따옴표 스타일

이 설정은 특성 값을 작은따옴표 또는 큰따옴표로 묶을지 여부를 나타냅니다. 자동 포맷터 및 IntelliSense 자동 완성에서는 이 설정을 사용합니다.

이 옵션을 설정하면 디자이너를 사용하거나 XAML 뷰에서 수동으로 이후에 추가된 특성만 영향을 받습니다.

**큰따옴표(")**

특성 값을 큰따옴표로 묶습니다.
`<Button Name="button1">Hello</Button>`

**작은따옴표(')**

특성 값을 작은따옴표로 묶습니다.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>태그 줄 바꿈

태그 줄 바꿈을 위해 줄 길이를 지정할 수 있습니다. 태그 줄 바꿈을 사용하도록 설정하면 디자이너를 사용하여 이후에 추가된 XAML이 이에 따라 래핑됩니다.

**지정한 길이를 초과할 때 태그 줄 바꿈**

**길이**에 의해 지정된 줄 길이에서 줄 바꿈할지 지정합니다.

**길이**

줄에 포함할 수 있는 문자 수입니다. 필요한 경우 일부 XAML 줄이 지정된 줄 길이를 초과할 수 있습니다.

## <a name="attribute-spacing"></a>특성 간격

이 설정을 사용하여 XAML 문서에서 특성 정렬 방식을 제어합니다.

**특성 간에 줄 바꿈과 공간 유지**

자동 서식 지정은 특성 간의 새 줄 및 공백에 영향을 미치지 않습니다.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**특성 간에 단일 공백 삽입**

특성에 한 줄이 사용되고 인접 특성은 하나의 공백으로 구분됩니다. 태그 줄 바꿈 설정이 적용됩니다.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**한 줄에 하나의 특성 배치**

각 특성은 각각의 줄에 해당하며 여러 특성이 있을 때 유용합니다.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**첫 번째 특성을 시작 태그와 같은 줄에 배치**

이 설정을 선택하면 첫 번째 특성이 요소의 시작 태그와 같은 줄에 표시됩니다.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>요소 간격

이 설정을 사용하여 XAML 문서에서 요소 정렬 방식을 제어합니다.

**콘텐츠의 줄 바꿈 유지**

요소 콘텐츠의 빈 줄이 제거되지 않습니다.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**콘텐츠의 여러 빈 줄을 한 줄로 축소**

요소 콘텐츠의 빈 줄이 한 줄로 축소됩니다.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**콘텐츠에서 빈 줄 제거**

요소 콘텐츠의 모든 빈 줄이 제거됩니다.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>참고 항목

- [WPF의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
