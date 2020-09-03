---
title: 레거시 API를 사용 하 여 theText View에 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184939"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>레거시 API를 사용하여 텍스트 보기에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 뷰는 텍스트 버퍼에 저장 되는 텍스트의 표현입니다. 다음 섹션에 표시 된 것 처럼 레거시 API를 사용 하 여 텍스트 보기에 액세스할 수 있습니다.  
  
## <a name="text-view-object"></a>텍스트 뷰 개체  
 각 보기는 자체 텍스트 버퍼와 연결 되며, 뷰는 버퍼의 데이터에 대 한 창입니다. 다음 다이어그램에서는로 표현 되는 텍스트 뷰 개체의 핵심 인터페이스를 보여 줍니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Visual Studio 텍스트 뷰 개체](../extensibility/media/vstextview.gif "vstextview")  
텍스트 뷰 개체  
  
 뷰는 버퍼에 텍스트를 표시 하는 방법입니다. 여기에는 자동 줄 바꿈 및 개요와 같은 기능이 포함 되어 있으므로 뷰에 표시 되는 내용이 버퍼의 텍스트를 정확 하 게 표시 하지 않습니다.  
  
 뷰를 사용 하면 다른 서비스 또는 프로세스에서 들어오는 명령을 가로채서 해당 명령을 실행 하 여 뷰가 동작을 수행할 수 있습니다. 이 작업을 수행 하는 가장 일반적인 서비스는 언어 서비스입니다. 예를 들어 언어 서비스는 ENTER 키에 대 한 명령을 가로채서 사용자 지정 들여쓰기 동작이 나 도구 설명을 제공 해야 할 수 있습니다.  
  
## <a name="adding-functionality-to-the-text-view"></a>텍스트 뷰에 기능 추가  
 특정 키 입력을 처리 하 여 텍스트 보기 동작을 사용자 지정할 수 있습니다. 키 입력을 가로채는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 개체에 대해를 구현 하 고 명령을 모니터링 및 가로채는 명령 대상 ()을 제공 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
 텍스트 뷰는 명령 필터에 대 한 순차 아키텍처를 사용 합니다. 새 명령 필터 ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 개체)는 메서드를 호출 하 여 시퀀스에 추가 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 인터페이스를 사용 하 여 텍스트 뷰에 대 한 이벤트 알림을 제공 합니다 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` . 클라이언트 개체에서이 인터페이스를 구현 하 여 텍스트 보기의 변경에 대 한 알림을 받습니다. 텍스트 뷰의 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 뷰의 변경 내용에 대 한 알림을 수신 하 여이 인터페이스를 텍스트 뷰에 노출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [레거시 API를 사용 하 여 보기 설정 변경](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [텍스트 관리자를 사용하여 글로벌 설정 모니터링](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
