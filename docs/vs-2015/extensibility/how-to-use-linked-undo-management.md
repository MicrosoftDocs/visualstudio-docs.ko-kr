---
title: '방법: 연결 된 실행 취소 관리 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841587"
---
# <a name="how-to-use-linked-undo-management"></a>방법: 연결된 실행 취소 관리 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

연결 된 실행 취소를 사용 하면 사용자가 여러 파일에서 동일한 편집 내용을 동시에 취소할 수 있습니다. 예를 들어 헤더 파일 및 Visual C++ 파일과 같은 여러 프로그램 파일에서 동시 텍스트 변경 내용은 연결 된 실행 취소 트랜잭션입니다. 연결 된 실행 취소 기능은 환경에서 실행 취소 관리자의 구현에 기본 제공 되며 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> 이 기능을 조작할 수 있습니다. 연결 된 실행 취소는 개별 실행 취소 스택을 함께 실행 하 여 단일 실행 취소 단위로 처리할 수 있는 부모 실행 취소 단위에 의해 구현 됩니다. 연결 된 실행 취소를 사용 하는 절차는 다음 섹션에 자세히 설명 되어 있습니다.  
  
### <a name="to-use-linked-undo"></a>연결 된 실행 취소를 사용 하려면  
  
1. 에 `QueryService` 대 한 포인터를 가져오려면를 호출 `SVsLinkedUndoManager` `IVsLinkedUndoTransactionManager` 합니다.  
  
2. 을 호출 하 여 초기 부모 연결 된 실행 취소 단위를 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . 이는 연결 된 실행 취소 스택으로 그룹화 될 실행 취소 스택 집합의 시작 지점을 설정 합니다. 메서드에서는 `OpenLinkedUndo` 연결 된 실행 취소를 strict로 설정할지 아니면 strict로 설정할지 여부도 지정 해야 합니다. 비 strict 연결 된 실행 취소 동작은 연결 된 실행 취소 형제를 포함 하는 일부 문서를 닫을 수 있으며 해당 스택에서 연결 된 실행 취소 형제를 그대로 유지할 수 있음을 의미 합니다. 엄격한 연결 된 실행 취소 동작은 연결 된 모든 실행 취소 형제 스택을 함께 실행 취소 하거나 전혀 실행 하지 않도록 지정 합니다. [IOleUndoManager:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) 메서드를 호출 하 여 후속 연결 된 실행 취소 스택을 추가 합니다.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A>을 호출 하 여 연결 된 모든 실행 취소 단위를 하나로 롤백합니다.  
  
    > [!NOTE]
    > 편집기에서 연결 된 실행 취소 관리를 구현 하려면 실행 취소 관리를 추가 합니다. 연결 된 실행 취소 관리를 구현 하는 방법에 대 한 자세한 내용은 [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)을 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [방법: 실행 취소 관리 구현](../extensibility/how-to-implement-undo-management.md)
