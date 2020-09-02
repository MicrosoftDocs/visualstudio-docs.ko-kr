---
title: 레거시 API를 사용 하 여 실행 취소 및 다시 실행 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194365"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>레거시 API를 사용하여 실행 취소 및 다시 실행 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기는 사용자가 코드를 수정할 때 최근 변경 내용을 되돌릴 수 있도록 하는 실행 취소 작업을 지원 해야 합니다. 및에서 구현 된 대부분의 편집기 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] IDE (통합 개발 환경)에서 자동으로 제공 되는 실행 취소 지원이 있을 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)  
 단일 또는 여러 뷰가 포함 된 편집기에 실행 취소 기능을 제공 합니다.  
  
 [방법: 실행 취소 스택 정리](../extensibility/how-to-clear-the-undo-stack.md)  
 실행 취소 스택을 지우는 방법에 대해 설명 합니다.  
  
 [방법: 연결된 실행 취소 관리 사용](../extensibility/how-to-use-linked-undo-management.md)  
 편집기에 연결 된 실행 취소 관리를 통합 합니다.  
  
## <a name="reference"></a>참고  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 여러 뷰를 지 원하는 편집기에 대 한 실행 취소 관리 기능을 제공 합니다.  
  
## <a name="related-sections"></a>관련 섹션
