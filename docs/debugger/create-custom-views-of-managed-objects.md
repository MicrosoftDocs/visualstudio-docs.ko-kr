---
title: 관리 개체의 사용자 지정 뷰 만들기 | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188642"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>관리 개체의 사용자 지정 뷰 만들기(C#, Visual Basic, F#, C++/CLI)
Visual Studio에서 디버거 변수 창에 데이터 형식이 표시되는 방식을 사용자 지정할 수 있습니다.

## <a name="attributes"></a>특성

C#, Visual Basic, F# 및 C++(C++/CLI 코드만 해당)에서 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> 및 <xref:System.Diagnostics.DebuggerBrowsableAttribute>를 사용하여 사용자 지정 데이터에 대한 확장을 추가할 수 있습니다.

.NET Framework 2.0 코드에서 Visual Basic은 DebuggerBrowsable 특성을 지원하지 않습니다. 최신 버전의 .NET에서는 이러한 제한 사항이 제거되었습니다.

## <a name="visualizers"></a>시각화 도우미

시각화 도우미를 작성하여 관리되는 데이터 형식을 표시할 수 있습니다. 자세한 내용은 [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)을 참조하세요.

> [!NOTE]
> C++ 코드의 경우 [디버거에서 C++ 개체의 사용자 지정 뷰 만들기](create-custom-views-of-native-objects.md)에 설명된 대로 Natvis 프레임워크를 사용하여 사용자 지정 데이터 형식 확장을 추가할 수 있습니다.

## <a name="see-also"></a>참조

- [DebuggerDisplay 특성을 사용하여 디버거에 표시할 내용 지시](../debugger/using-the-debuggerdisplay-attribute.md)
- [DebuggerTypeProxy 특성을 사용하여 디버거에 표시할 내용 지시](../debugger/using-debuggertypeproxy-attribute.md)
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [디버거 표시 특성을 사용하여 디버깅 향상](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
