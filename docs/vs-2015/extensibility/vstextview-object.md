---
title: VSTextView 개체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690694"
---
# <a name="vstextview-object"></a>VSTextView 개체
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 뷰는 사용자가 텍스트 버퍼의 유니코드 텍스트를 보고 편집할 수 있도록 하는 창입니다. 기본적으로 뷰는 대부분의 사용자가 편집기로 참조 하는 것입니다. 뷰는 다양 한 텍스트 계층 (자동 줄 바꿈, 개요 텍스트 등)에 의해 버퍼에서 분리 되기 때문에 버퍼의 텍스트를 정확 하 게 표현 하는 것이 보장 되지 않습니다. 텍스트 보기에 대 한 자세한 내용은 [레거시 API를 사용 하 여 TheText View 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) 를 참조 하세요.  
  
 다음 표에서는 개체의 인터페이스를 보여 줍니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
|인터페이스|설명|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업 (즉, 단일 실행 취소/다시 실행 단위로 그룹화 된 작업)을 만들 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|뷰를 관리 하 고 액세스 하는 기본 메서드를 제공 합니다. `IVsTextView` 는 스레드로부터 안전 하지 않습니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 창을 만들고 관리 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|텍스트 레이어와 상호 작용 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|다른 스레드에서 뷰에서 작업을 수행 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [그림 편집](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 개체](../extensibility/vstextbuffer-object.md)   
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
