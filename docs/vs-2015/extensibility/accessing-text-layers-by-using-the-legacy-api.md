---
title: 레거시 API를 사용 하 여 텍스트 계층 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148019"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>레거시 API를 사용하여 텍스트 레이어에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 계층은 일반적으로 텍스트 레이아웃의 일부 측면을 캡슐화 합니다. 예를 들어 "일회성" 계층은 캐럿 (텍스트 삽입 지점)이 포함 된 함수 앞뒤의 텍스트를 숨깁니다.  
  
 텍스트 계층은 버퍼와 뷰 사이에 있으며 뷰에서 버퍼 내용이 표시 되는 방식을 수정 합니다.  
  
## <a name="text-layer-information"></a>텍스트 계층 정보  
 다음 목록에서는에서 텍스트 계층의 작동 방식을 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- 텍스트 계층의 텍스트는 구문 색 지정 및 표식으로 표시 될 수 있습니다.  
  
- 현재 사용자 고유의 레이어를 구현할 수 없습니다.  
  
- 계층은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 에서 파생 되는를 노출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 합니다. 텍스트 버퍼 자체도 계층으로 구현 됩니다 .이를 통해 뷰가 기본 계층으로 다형적으로을 처리할 수 있습니다.  
  
- 뷰와 버퍼 사이에는 여러 개의 레이어가 있을 수 있습니다. 각 계층은 하위 계층을 처리 하며, 뷰는 최상위 계층을 주로 처리 합니다. 이 뷰에는 버퍼에 대 한 일부 정보가 있습니다.  
  
- 계층은 그 아래에 있는 레이어에만 영향을 줄 수 있습니다. 원래 표준 이벤트 이상의 계층에는 영향을 주지 않습니다.  
  
- 편집기에서 숨겨진 텍스트, 합성 텍스트 및 자동 줄 바꿈이 계층으로 구현 됩니다. 레이어와 직접 상호 작용 하지 않고도 숨겨진 및 합성 텍스트를 구현할 수 있습니다. 자세한 내용은 [레거시 언어 서비스에서 개요](../extensibility/internals/outlining-in-a-legacy-language-service.md) 표시 및을 참조 하세요 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- 각 텍스트 계층에는 인터페이스를 통해 노출 되는 자체 로컬 좌표계가 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> . 예를 들어 줄 바꿈 계층은 두 줄을 포함할 수 있지만 기본 텍스트 버퍼에는 줄이 하나만 포함 될 수 있습니다.  
  
- 뷰는 인터페이스를 통해 레이어와 통신 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> . 이 인터페이스를 사용 하 여 버퍼 좌표로 뷰 좌표를 조정 합니다.  
  
- 텍스트를 시작 하는 합성 텍스트 계층과 같은 계층은의 로컬 구현을 제공 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- 뿐만 아니라 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 텍스트 계층은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 인터페이스에서 이벤트를 구현 하 고 실행 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> .  
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)   
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [레거시 API를 사용하여 편집기 컨트롤 및 메뉴 사용자 지정](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
