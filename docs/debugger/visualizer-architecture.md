---
title: 시각화 도우미 아키텍처 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6dfbc8c57ff2e78bf0c6ebbd4e9899c372d7084
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187163"
---
# <a name="visualizer-architecture"></a>시각화 도우미 아키텍처
디버거 시각화 도우미의 아키텍처는 두 부분으로 구성되어 있습니다.

- *디버거(debugger) 쪽* 코드는 Visual Studio 디버거 내에서 실행됩니다. 디버거 쪽 코드에서는 시각화 도우미의 사용자 인터페이스를 만들고 표시합니다.

- *디버기(debuggee) 쪽* 코드는 Visual Studio가 디버깅하는 프로세스(*디버기*) 내에서 실행됩니다.

  시각화 도우미는 디버거에서 데이터 개체의 내용을 의미 있고 이해할 수 있는 형식으로 표시(*시각화*)하는 데 사용되는 디버거 구성 요소입니다. 일부 시각화 도우미에서는 데이터 개체를 편집할 수도 있습니다. 사용자 지정 시각화 도우미를 작성하면 고유한 사용자 지정 데이터 형식을 처리하도록 디버거를 확장할 수 있습니다.

  시각화할 데이터 개체는 디버깅할 프로세스(*디버기* 프로세스) 내에 있습니다. 데이터를 표시하는 사용자 인터페이스는 Visual Studio 디버거 프로세스 내에서 만들어집니다.

|디버거 프로세스|디버기 프로세스|
|----------------------|----------------------|
|디버거 사용자 인터페이스(DataTip, 조사식 창, 간략한 조사식)|시각화할 데이터 개체|

 디버거 인터페이스 내에서 데이터 개체를 시각화하려면 두 프로세스 사이에서 통신하는 코드가 필요합니다. 따라서 시각화 도우미 아키텍처는 *디버거 쪽* 코드와 *디버기 쪽* 코드라는 두 부분으로 구성됩니다.

 디버거 쪽 코드에서는 DataTip, 조사식 창, 간략한 조사식 등의 디버거 인터페이스에서 호출할 수 있는 자체 사용자 인터페이스를 만듭니다. 시각화 도우미 인터페이스는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> 클래스와 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> 인터페이스를 사용하여 만들어집니다. 모든 시각화 도우미 API와 마찬가지로 DialogDebuggerVisualizer 및 IDialogVisualizerService는 <xref:Microsoft.VisualStudio.DebuggerVisualizers> 네임스페이스에 있습니다.

|디버거 쪽|디버기 쪽|
|-------------------|-------------------|
|DialogDebuggerVisualizer 클래스<br /><br /> IDialogVisualizerService 인터페이스|데이터 개체|

 사용자 인터페이스를 통해 디버거 쪽에 있는 개체 공급자에서 시각화할 데이터를 가져옵니다.

|디버거 쪽|디버기 쪽|
|-------------------|-------------------|
|DialogDebuggerVisualizer 클래스<br /><br /> IDialogVisualizerService 인터페이스|데이터 개체|
|개체 공급자(<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 구현)||

 디버기 쪽에는 개체 소스라는 해당 개체가 있습니다.

|디버거 쪽|디버기 쪽|
|-------------------|-------------------|
|DialogDebuggerVisualizer 클래스<br /><br /> IDialogVisualizerService 인터페이스|데이터 개체|
|개체 공급자(<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> 구현)|개체 소스(<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>에서 파생)|

 개체 공급자는 시각화 도우미 UI에 시각화할 개체 데이터를 제공합니다. 개체 공급자는 개체 소스에서 개체 데이터를 가져옵니다. 개체 공급자와 개체 소스는 디버거 쪽과 디버기 쪽 사이에 개체 데이터를 주고받는 API를 제공합니다.

 모든 시각화 도우미는 시각화할 데이터 개체를 가져와야 합니다. 다음 표에서는 이러한 용도로 개체 공급자와 개체 소스에서 사용되는 해당 API를 보여 줍니다.

|개체 공급자|개체 소스|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> 또는<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|

 개체 공급자는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 또는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>를 사용할 수 있습니다. 두 가지 API 모두 개체 소스를 대상으로 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>를 호출하게 됩니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName>를 호출하면 시각화 대상 개체의 serialize된 형식을 나타내는 <xref:System.IO.Stream?displayProperty=fullName>이 채워집니다.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName>는 데이터를 다시 개체 양식으로 역직렬화합니다. 그런 다음, <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>를 사용하여 만든 UI에 이 개체 양식을 표시할 수 있습니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>는 사용자가 직접 역직렬화해야 하는 원시 `Stream`으로 데이터를 채웁니다. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName>는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>를 호출하여 직렬화된 `Stream`을 가져온 다음, 데이터를 역직렬화하는 방식으로 작동합니다. .NET을 통해 개체를 serialize할 수 없고 사용자가 직접 serialize해야 하는 경우에는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>를 사용합니다. 이러한 경우 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> 메서드도 재정의해야 합니다.

 읽기 전용 시각화 도우미를 만드는 경우에는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> 또는 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>를 사용한 단방향 통신으로도 충분합니다. 데이터 개체 편집을 지원하는 시각화 도우미를 만드는 경우에는 더 많은 단계를 거쳐야 합니다. 이러한 경우 개체 공급자에서 개체 소스로 데이터 개체를 다시 전달할 수도 있어야 합니다. 다음 표에서는 이러한 용도로 사용되는 개체 공급자 및 개체 소스 API를 보여 줍니다.

|개체 공급자|개체 소스|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> 또는<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|

 이 경우에도 개체 공급자에서 두 가지 API를 사용할 수 있습니다. 데이터는 항상 개체 공급자에서 개체 소스로 `Stream`으로 전달되지만 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A>를 사용하는 경우 사용자가 개체를 `Stream`으로 serialize해야 합니다.

 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>는 사용자가 제공한 개체를 받아 `Stream`으로 serialize한 다음 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A>를 호출하여 `Stream`을 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>에 전달합니다.

 Replace 메서드 중 하나를 사용하면 디버기에서 시각화 대상 개체를 대체하는 새 데이터 개체가 만들어집니다. 원래 개체를 바꾸지 않고 내용을 변경하려는 경우에는 다음 표에 나와 있는 Transfer 메서드 중 하나를 사용합니다. 이들 API는 시각화 대상 개체를 바꾸지 않고 데이터를 양방향으로 동시에 전송합니다.

|개체 공급자|개체 소스|
|---------------------|-------------------|
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> 또는<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|

## <a name="see-also"></a>참조
- [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)
- [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [연습: Visual Basic에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [시각화 도우미 보안 고려 사항](../debugger/visualizer-security-considerations.md)