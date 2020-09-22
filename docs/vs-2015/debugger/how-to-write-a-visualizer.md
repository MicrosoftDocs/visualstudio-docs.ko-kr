---
title: '방법: 시각화 도우미 작성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce50276e4e83a1a055294c8e2b6e09cd0f93d54d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843264"
---
# <a name="how-to-write-a-visualizer"></a>방법: 시각화 도우미 작성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Object> 또는 <xref:System.Array>를 제외한 모든 관리되는 클래스의 개체에 대해 사용자 지정 시각화 도우미를 작성할 수 있습니다.  
  
> [!NOTE]
> **스토어** 앱에서는 표준 텍스트, HTML, XML 및 JSON 시각화 도우미만 지원 됩니다. 사용자가 만든 사용자 지정 시각화 도우미는 지원되지 않습니다.  
  
 디버거 시각화 도우미의 아키텍처는 두 부분으로 구성되어 있습니다.  
  
- *디버거(debugger) 쪽* 코드는 Visual Studio 디버거 내에서 실행됩니다. 디버거 쪽 코드에서는 시각화 도우미의 사용자 인터페이스를 만들고 표시합니다.  
  
- *디버기(debuggee) 쪽* 코드는 Visual Studio가 디버깅하는 프로세스(*디버기*) 내에서 실행됩니다.  
  
  시각화하려는 데이터 개체(예: String 개체)는 디버기 프로세스에 있습니다. 따라서 디버기 쪽에서 디버거 쪽에 데이터 개체를 전달해야 디버거 쪽에서 작성된 사용자 인터페이스를 사용하여 이 개체를 표시할 수 있습니다.  
  
  디버거 쪽은 인터페이스를 구현 하는 *개체 공급자* 에서 시각화할이 데이터 개체를 받습니다 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> . 디버기 쪽에서는에서 파생 된 *개체 소스*를 통해 데이터 개체를 전송 합니다 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> . 개체 공급자는 데이터를 다시 개체 소스로 전달할 수도 있습니다. 이를 통해 데이터를 표시할 뿐만 아니라 편집도 하는 시각화 도우미를 작성할 수 있습니다. 식 계산기와 통신하고 궁극적으로는 개체 소스와 통신하도록 개체 공급자를 재정의할 수 있습니다.  
  
  디버기 쪽과 디버거 쪽에서는 <xref:System.IO.Stream>을 통해 서로 통신합니다. 데이터 개체를 <xref:System.IO.Stream>으로 직렬화하고 <xref:System.IO.Stream>을 데이터 개체로 다시 역직렬화하기 위한 메서드가 제공됩니다.  
  
  디버기 쪽 코드는 DebuggerVisualizer 특성(<xref:System.Diagnostics.DebuggerVisualizerAttribute>)을 사용하여 지정됩니다.  
  
  디버거 쪽에 시각화 도우미 사용자 인터페이스를 만들려면 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>에서 상속되는 클래스를 만들고 인터페이스를 표시하도록 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 메서드를 재정의해야 합니다.  
  
  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>를 사용하여 시각화 도우미의 Windows Forms, 대화 상자 및 컨트롤을 표시할 수 있습니다.  
  
  제네릭 형식에 대한 지원은 제한되어 있습니다. 제네릭 형식이 개방형 형식인 경우에만 제네릭 형식을 대상으로 하는 시각화 도우미를 작성할 수 있습니다. `DebuggerTypeProxy` 특성을 사용하는 경우에도 이 제한은 동일하게 적용됩니다. 자세한 내용은 [DebuggerTypeProxy 특성 사용](../debugger/using-debuggertypeproxy-attribute.md)을 참조 하세요.  
  
  사용자 지정 시각화 도우미를 작성할 때는 보안 문제를 고려해야 합니다. [시각화 도우미 보안 고려 사항](../debugger/visualizer-security-considerations.md)을 참조 하세요.  
  
  다음 절차에서는 시각화 도우미를 만들기 위해 수행해야 할 작업에 대한 간략한 개요를 제공합니다. 자세한 설명은 [연습: c #에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)을 참조 하세요.  
  
### <a name="to-create-the-debugger-side"></a>디버거 쪽 코드를 만들려면  
  
1. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 메서드를 사용하여 디버거 쪽에서 시각화되는 개체를 가져옵니다.  
  
2. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>에서 상속된 클래스를 만듭니다.  
  
3. <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> 메서드를 재정의하여 인터페이스를 표시합니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 메서드를 사용하여 Windows Forms, 대화 상자 및 컨트롤을 인터페이스의 일부로 표시합니다.  
  
4. 시각화 도우미(<xref:System.Diagnostics.DebuggerVisualizerAttribute>)를 제공하여 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>를 적용합니다.  
  
### <a name="to-create-the-debuggee-side"></a>디버기 쪽 코드를 만들려면  
  
1. 시각화 도우미(<xref:System.Diagnostics.DebuggerVisualizerAttribute>)와 개체 소스(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>)를 제공하여 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>를 적용합니다. 개체 소스를 제공하지 않으면 기본 개체 소스가 사용됩니다.  
  
2. 시각화 도우미에서 데이터 개체를 표시할 뿐만 아니라 편집할 수도 있도록 하려면 `TransferData`에서 `CreateReplacementObject` 또는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 메서드를 재정의해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)   
 [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)   
 [방법: 시각화 도우미 테스트 및 디버그](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [시각화 도우미 보안 고려 사항](../debugger/visualizer-security-considerations.md)
