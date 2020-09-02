---
title: 레거시 API를 사용 하 여 코드 창 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556145"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>레거시 API를 사용하여 코드 Windows 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 창은 하나 이상의 텍스트 뷰를 지 원하는 문서 창 개체입니다. 코드 창의 정확한 기능은 연결 된 언어 서비스에 따라 달라 집니다. MDI (다중 문서 인터페이스) 모드에서는 코드 창이 MDI 자식 프레임입니다.  
  
 코드 창은 언어 서비스에 의해 제어 되며, 각 언어 서비스는 자체 코드 창 관리자를 제공할 수 있습니다. 이렇게 하면 언어 서비스에서 물결선, 색 지정 등의 자체 장식을 코드 창에 추가할 수 있습니다. 핵심 창을 만드는 방법에 대 한 자세한 내용은 [레거시 API를 사용 하 여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)를 참조 하세요.  
  
 코드 창은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 텍스트 뷰 및 개체에 배치 된 모든 장식을 포함 하는 개체입니다. 핵심 편집기를 인스턴스화하는 동안 코드 창을 만들 때 언어 서비스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 다음 그림과 같이를 코드 창에 연결할 수 있습니다.  
  
 ![CodeWindow 그래픽](../extensibility/media/vscodewindow.gif "vscodewindow")  
코드 창  
  
 언어 서비스는 코드 창 관리자를 구현 하며 드롭다운 표시줄과 같은 장식 관리를 담당 합니다. 코드 창에서는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 코드 창을 초기화 하는 동안 메서드를 호출 합니다. 이 호출을 수행할 때 언어 서비스는 드롭다운 모음이 나 단추 모음 ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> )을 코드 창에 추가할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 `Customizing Code Windows by Using the Legacy API`  
 레거시 API를 사용 하 여 코드 창을 사용자 지정 하는 방법을 설명 합니다.  
  
 [방법: 다른 편집기에서 편집기 호스트](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 편집기 창 내에서 두 번째 편집기를 호스트 하는 방법에 대해 설명 합니다.  
  
 [방법: 편집기에서 포커스를 잃을 때 이벤트 발생](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 문서 데이터 개체에 문서 뷰를 연결 하는 방법에 대해 설명 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [레거시 API를 사용 하 여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
