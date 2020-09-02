---
title: VSCodeWindow 개체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690766"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 개체
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 창은 하나 이상의 텍스트 뷰 (일반적으로 개체)를 포함할 수 있는 특수 문서 창입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 아키텍처 측면에서 코드 창은 창 프레임 안에 있는 문서 창입니다. 기능적으로 코드 창은 추가 기능이 있는 문서 창입니다. MDI (다중 문서 인터페이스) 모드에서 코드 창은 MDI 자식 프레임입니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창 사용자 지정](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)을 참조 하세요.  
  
 다음 표에서는 개체의 인터페이스를 포함 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .  
  
|메서드|설명|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|GUID (globally unique identifier)가 식별 하는 서비스를 찾기 위한 일반 액세스 메커니즘을 제공 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|하나 이상의 코드 뷰를 포함 하는 MDI (다중 문서 인터페이스) 자식을 나타냅니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 프레임을 채웁니다.|  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [그림 편집](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
