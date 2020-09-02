---
title: '방법: 실행 취소 스택 지우기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db77f93fd7f6af16b5358b75b6ffcd5927430653
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549171"
---
# <a name="how-to-clear-the-undo-stack"></a>방법: 실행 취소 스택 정리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 절차에서는 실행 취소 스택을 지우는 방법을 설명 합니다.  
  
### <a name="to-clear-the-undo-stack"></a>실행 취소 스택을 지우려면  
  
1. 실행 취소 스택을 지우려면 [IOleUndoManager::D iscardfrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) 메서드를 사용 합니다. 이에 대 한 예는 다음과 같습니다.  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)
