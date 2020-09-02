---
title: '방법: 레거시 API를 사용 하 여 텍스트 버퍼 이벤트 등록 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204091"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>방법: 레거시 API를 사용하여 텍스트 버퍼 이벤트에 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

레거시 API를 사용 하 여 텍스트 버퍼에 액세스 하는 경우 다음 절차에 나와 있는 것 처럼 텍스트 버퍼 이벤트를 등록 해야 합니다.  
  
### <a name="to-advise-text-buffer-events"></a>텍스트 버퍼 이벤트를 알리기 위해  
  
1. 에 있는 인터페이스 중 하나에 대 한 포인터에서에 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> `QueryInterface` 대 한 포인터에 대해를 호출 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 합니다.  
  
2. <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>메서드를 호출 하 고 등록 하려는 이벤트의 인터페이스 ID를 전달 합니다.  
  
     예를 들어에 등록 하려는 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> IID_IVsTextLinesEvents 인터페이스 ID를 전달 합니다.  
  
     텍스트 버퍼는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 적절 한 연결 지점 개체의 인터페이스에 대 한 포인터를 반환 합니다.  
  
3. 이 포인터를 사용 하 여 메서드를 호출 하 고, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 등록 하려는 이벤트 인터페이스 (예: 인터페이스)의 구현에 대 한 포인터를 전달 `IVsTextLinesEvents` 합니다.  
  
     환경에서는 메서드를 호출 하 여 이벤트 수신을 중지 하는 데 사용할 수 있는 쿠키를 반환 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> .  
  
## <a name="see-also"></a>관련 항목  
 [레거시 API의 텍스트 버퍼 이벤트](../extensibility/text-buffer-events-in-the-legacy-api.md)
