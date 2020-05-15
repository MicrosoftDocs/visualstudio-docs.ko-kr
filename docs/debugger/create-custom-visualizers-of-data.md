---
title: 사용자 지정 데이터 시각화 도우미 만들기 | Microsoft Docs
ms.date: 11/07/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564736"
---
# <a name="create-custom-data-visualizers"></a>사용자 지정 데이터 시각화 도우미 만들기
 ‘시각화 도우미’는 해당 데이터 형식에 적합한 방식으로 변수나 개체를 표시하는 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 디버거 사용자 인터페이스의 일부입니다.  예를 들어 HTML 시각화 도우미는 HTML 문자열을 해석하고 브라우저 창에 나타날 결과를 표시합니다. 비트맵 시각화 도우미는 비트맵 구조를 해석하고 해당 구조를 나타내는 그래픽을 표시합니다. 일부 시각화 도우미에서는 데이터를 볼 수 있을 뿐 아니라 수정할 수도 있습니다.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 디버거에는 6가지 표준 시각화 도우미가 포함되어 있습니다. 텍스트, HTML, XML 및 JSON 시각화 도우미는 문자열 개체에 사용됩니다. WPF 트리 시각화 도우미는 WPF 개체 시각적 트리의 속성을 표시합니다. 데이터 세트 시각화 도우미는 DataSet, DataView 및 DataTable 개체에 적용됩니다.

Microsoft, 타사 및 커뮤니티에서 더 많은 시각화 도우미를 다운로드할 수 있습니다. 또한 자신만의 시각화 도우미를 직접 작성하여 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 디버거에 설치할 수도 있습니다.

디버거에서 시각화 도우미는 돋보기 아이콘 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘")으로 표시됩니다. **DataTip**, 디버거 **조사식** 창 또는 **간략한 조사식** 대화 상자에서 아이콘을 선택하고 해당 개체에 적합한 시각화 도우미를 선택할 수 있습니다.

## <a name="write-custom-visualizers"></a>사용자 지정 시각화 도우미 작성

 > [!NOTE]
 > 네이티브 코드를 위한 사용자 지정 시각화 도우미를 만들려면 [SQLite 네이티브 디버거 시각화 도우미](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) 샘플을 참조하세요. UWP 및 Windows 8.x 앱에서는 사용자 지정 시각화 도우미가 지원되지 않습니다.

<xref:System.Object> 및 <xref:System.Array>를 제외한 모든 관리 클래스의 개체에 대해 사용자 지정 시각화 도우미를 작성할 수 있습니다.

디버거 시각화 도우미의 아키텍처는 두 부분으로 구성되어 있습니다.

- ‘디버거 쪽’은 Visual Studio 디버거 내에서 실행되며 시각화 도우미 사용자 인터페이스를 만들고 표시합니다. 

- *디버기(debuggee) 쪽* 코드는 Visual Studio가 디버깅하는 프로세스(*디버기*) 내에서 실행됩니다. 시각화할 데이터 개체(예: String 개체)는 디버기 프로세스에 있습니다. 디버기 쪽은 개체를 디버거 쪽으로 전송하여, 만들어지는 사용자 인터페이스에 표시합니다.

디버거 쪽에서는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 인터페이스를 구현하는 ‘개체 공급자’로부터 데이터 개체를 전달받습니다.  디버기 쪽에서는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>에서 파생된 ‘개체 소스’를 통해 데이터 개체를 전달합니다. 

개체 공급자는 데이터를 다시 개체 소스로 전달할 수도 있습니다. 이를 통해 데이터를 편집할 수 있는 시각화 도우미를 작성할 수 있습니다. 식 계산기 및 개체 소스와 통신하도록 개체 공급자를 재정의합니다.

디버기 쪽 및 디버거 쪽은 데이터 개체를 <xref:System.IO.Stream>으로 직렬화하고 <xref:System.IO.Stream>을 다시 데이터 개체로 역직렬화하는 <xref:System.IO.Stream> 메서드를 통해 서로 통신합니다.

형식이 개방형 형식인 경우에만 제네릭 형식의 시각화 도우미를 작성할 수 있습니다. `DebuggerTypeProxy` 특성을 사용하는 경우에도 이 제한은 동일하게 적용됩니다. 자세한 내용은 [DebuggerTypeProxy 특성 사용](../debugger/using-debuggertypeproxy-attribute.md)을 참조하세요.

사용자 지정 시각화 도우미를 작성할 때는 보안 문제를 고려해야 합니다. [시각화 도우미 보안 고려 사항](../debugger/visualizer-security-considerations.md)을 참조하세요.

다음 단계에서는 시각화 도우미 만들기를 개괄적으로 살펴봅니다. 자세한 지침은 [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) 또는 [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)을 참조하세요.

### <a name="to-create-the-debugger-side"></a>디버거 쪽 코드를 만들려면

디버거 쪽에 시각화 도우미 사용자 인터페이스를 만들려면 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>에서 상속되는 클래스를 만들고 인터페이스를 표시하도록 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 메서드를 재정의합니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>를 사용하여 시각화 도우미의 Windows Forms, 대화 상자 및 컨트롤을 표시할 수 있습니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 메서드를 사용하여 디버거 쪽에서 시각화되는 개체를 가져옵니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>에서 상속된 클래스를 만듭니다.

1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 메서드를 재정의하여 인터페이스를 표시합니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 메서드를 사용하여 인터페이스의 Windows Forms, 대화 상자 및 컨트롤을 표시합니다.

4. <xref:System.Diagnostics.DebuggerVisualizerAttribute>를 적용하여 시각화 도우미에 표시합니다(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>디버기 쪽 코드를 만들려면

<xref:System.Diagnostics.DebuggerVisualizerAttribute>를 사용하여 디버기 쪽 코드를 지정합니다.

1. 시각화 도우미(<xref:System.Diagnostics.DebuggerVisualizerAttribute>)와 개체 소스(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)를 제공하여 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>를 적용합니다. 개체 소스를 생략하면 시각화 도우미에서 기본 개체 소스를 사용합니다.

1. 시각화 도우미에서 데이터 개체를 표시할 뿐 아니라 편집할 수 있도록 하려면 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>에서 `TransferData` 또는 `CreateReplacementObject` 메서드를 재정의합니다.

## <a name="see-also"></a>참조

- [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)
- [방법: 시각화 도우미 테스트 및 디버그](../debugger/how-to-test-and-debug-a-visualizer.md)
- [시각화 도우미 API 참조](../debugger/visualizer-api-reference.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)