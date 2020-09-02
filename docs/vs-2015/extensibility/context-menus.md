---
title: 상황에 맞는 메뉴 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184270"
---
# <a name="context-menus"></a>상황에 맞는 메뉴
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

상황에 맞는 메뉴는 사용자가 클라이언트 영역의 활성 영역을 마우스 오른쪽 단추로 클릭 하면 표시 되 고 마우스 오른쪽 단추를 놓으면 선택이 취소 됩니다.  
  
## <a name="editor-context-menus"></a>편집기 상황에 맞는 메뉴  
 가로채기 `ECMD_SHOWCONTEXTMENU` 를 통해 언어 서비스는 편집기에 표시 되는 상황에 맞는 메뉴를 제어할 수 있습니다. 사용자의 상황에 맞는 메뉴를 표시 하려면를 호출 하 여에 전달 될 때이 명령을 처리 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 합니다. 이 명령을 처리 하지 않으면 IDE는 편집기에 대해 제공 되는 표준 상황에 맞는 메뉴를 표시 합니다. 마커 별로 상황에 맞는 메뉴의 내용을 제어할 수도 있습니다. 이에 대 한 자세한 내용은 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md) 및 [레거시 언어 서비스 가로채기 명령을](../extensibility/internals/intercepting-legacy-language-service-commands.md)참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)   
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
