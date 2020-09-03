---
title: 관리 되는 개체의 사용자 지정 뷰 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72578028"
---
# <a name="create-custom-views-of-managed-objects"></a>관리 개체의 사용자 지정 뷰 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 디버거 변수 창에 데이터 형식이 표시되는 방식을 사용자 지정할 수 있습니다.  
  
## <a name="attributes"></a>특성  
 C# 및 Visual Basic에서는 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> 및 <xref:System.Diagnostics.DebuggerBrowsableAttribute>를 사용하여 사용자 지정 데이터에 대한 확장을 추가할 수 있습니다.  
  
 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 코드에서 Visual Basic은 DebuggerBrowsable 특성을 지원하지 않습니다. 최신 버전의 .NET Framework에서는 이러한 제한 사항이 제거되었습니다.  
  
## <a name="visualizers"></a>시각화 도우미  
 시각화 도우미를 작성하여 관리되는 데이터 형식을 표시할 수 있습니다. 자세한 내용은 [방법: 시각화 도우미 작성](../debugger/how-to-write-a-visualizer.md)을 참조하세요.  
  
## <a name="native-code"></a>네이티브 코드  
 네이티브 코드를 사용하는 경우 Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger 디렉터리에 있는 autoexp.dat 파일에 사용자 지정 데이터 형식 확장을 추가할 수 있습니다. `autoexp` 규칙의 작성 방법에 대한 지침은 해당 파일 내에 있습니다.  
  
> [!CAUTION]
> 이 파일의 구조와 autoexp 규칙의 구문은 Visual Studio 릴리스마다 다를 수 있습니다.  
  
 또한 식 계산기 추가 기능을 작성하여 네이티브 형식 뷰를 사용자 지정할 수도 있습니다. 자세한 내용은 [Eeaddin 샘플: 디버깅 식 계산기 추가 기능](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [DebuggerTypeProxy 특성 사용](../debugger/using-debuggertypeproxy-attribute.md)   
 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)   
 [조사식 및 간략 한 조사식 창](../debugger/watch-and-quickwatch-windows.md)   
 [디버거 표시 특성을 사용하여 디버깅 향상](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
