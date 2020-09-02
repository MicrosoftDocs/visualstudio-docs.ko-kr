---
title: '방법: 편집기에서 포커스를 잃을 때 이벤트 발생 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204201"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>방법: 편집기에서 포커스를 잃을 때 이벤트 발생
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기가 창 프레임에서 포커스를 잃을 때를 알아야 하는 경우가 있습니다. 예를 들어 편집기가 더 이상 집중 하지 않는 경우 코드 창에서 코드를 추출 해야 할 수 있습니다. 다음 절차에서는 편집기의 포커스를 잃는 알림을 받기 위해 수행 하는 단계를 설명 합니다.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>편집기에 대 한 응답으로 이벤트를 발생 시킵니다.  
  
1. 에서 개체를 가져와 선택 이벤트를 모니터링 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A>를 호출 하 고 개체를 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> 합니다.  
  
3. 호출에서를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 찾습니다 `elementid==SEID_WindowFrame` .  
  
4. `varValueNew`다음 두 가지 작업에 대 한 매개 변수를 테스트 합니다.  
  
    1. 찾고 있는 창 프레임입니다.  
  
    2. 프로그램에서 해당 창 프레임에 대 한 선택을 잃게 되는 지점입니다.
