---
title: '방법: 기본 제공 색 항목 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841474"
---
# <a name="how-to-use-built-in-colorable-items"></a>방법: 기본 제공 색 항목 사용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기본 제공 색 항목을 사용 하기 전에 먼저 사용자 지정 색 항목을 제공 하지 않는 IDE (통합 개발 환경)에 신호를 보내야 합니다 .이 경우에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 개체입니다. 언어 서비스의 레지스트리 항목을 설정 하 여이 작업을 수행 합니다.  
  
### <a name="to-use-built-in-colorable-items"></a>기본 제공 색 항목을 사용 하려면  
  
1. HKEY_LOCAL_MACHINE \VisualStudio \\ *X-y*\Languages\Language Services \\ *언어 이름*에서 *x. y* 는의 버전 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 이며 *언어 이름* 은 언어의 이름입니다. 라는 DWORD 레지스트리 항목 값을 만듭니다 `RequestStockColors` .  
  
2. `RequestStockColors`레지스트리 항목 값을 1로 설정 합니다.  
  
     레지스트리 항목을 만든 후 svc의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드는 열거형의 멤버를 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 하 여 편집기에서 사용할 색 특성의 배열을 채울 수 있습니다.  
  
    > [!NOTE]
    > 사용자 지정 색 항목을 제공 하는 경우에는이 레지스트리 항목을 설정 하지 마십시오. 자세한 내용은 [Custom 색 Items 항목](../../extensibility/internals/custom-colorable-items.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)   
 [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)   
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)
