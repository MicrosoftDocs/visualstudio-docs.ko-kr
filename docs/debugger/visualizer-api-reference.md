---
title: 시각화 도우미 API 참조 | Microsoft Docs
description: 시각화 도우미는 특정 형식의 데이터 요소를 표시하며 편집도 허용할 수 있습니다. 만들려면 이 섹션에 설명된 시각화 도우미 API를 사용합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- APIs, visualizers
- reference, visualizer APIs
- visualizers, API reference
ms.assetid: b9ff4ed0-9e80-49df-9016-a81189319afd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b790bcdc11e80b8f01877efe4a8d9497038b260b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884262"
---
# <a name="visualizer-api-reference"></a>시각화 도우미 API 참조

시각화 도우미 API는 Visual Studio 디버거용 시각화 도우미를 작성하려는 사용자를 위해 제공됩니다. 시각화 도우미는 Visual Studio 디버거 사용자 인터페이스의 기능을 확장하는 작은 애플리케이션입니다. 시각화 도우미에서는 설계 대상으로 선택된 특정 형식의 데이터 개체를 표시하고 선택에 따라서는 이 개체를 편집할 수도 있습니다.

## <a name="in-this-section"></a>섹션 내용

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource?displayProperty=fullName>

## <a name="see-also"></a>참조

- [연습: C#에서 시각화 도우미 작성](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)