---
title: '방법: 실행 취소 관리 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842215"
---
# <a name="how-to-implement-undo-management"></a>방법: 실행 취소 관리 구현
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

실행 취소 관리에 사용 되는 기본 인터페이스는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 환경에서 구현 되는입니다. 실행 취소 관리를 지원 하려면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> 개별 단계를 여러 개 포함할 수 있는 별도의 실행 취소 단위를 구현 합니다.  
  
 실행 취소 관리를 구현 하는 방법은 편집기에서 여러 뷰를 지원 하는지 여부에 따라 달라 집니다. 각 구현에 대 한 절차는 다음 섹션에 자세히 설명 되어 있습니다.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>편집기에서 단일 뷰를 지 원하는 경우  
 이 시나리오에서 편집기는 여러 뷰를 지원 하지 않습니다. 편집기와 문서는 하나 뿐 이며 실행 취소를 지원 합니다. 다음 절차를 사용 하 여 실행 취소 관리를 구현할 수 있습니다.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>단일 뷰 편집기에 대 한 실행 취소 관리를 지원 하려면  
  
1. `QueryInterface` `IServiceProvider` 문서 뷰 개체에서의 창 프레임에 있는 인터페이스를 호출 `IOleUndoManager` 하 여 실행 취소 관리자 ()에 액세스 `IID_IOLEUndoManager` 합니다.  
  
2. 뷰가 창 프레임에 배치 되는 경우를 호출 하는 데 사용할 수 있는 사이트 포인터를 가져옵니다 `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>편집기에서 여러 뷰를 지 원하는 경우  
 문서와 뷰 분리가 있는 경우 일반적으로 문서 자체와 연결 된 실행 취소 관리자가 하나씩 있습니다. 모든 실행 취소 단위는 문서 데이터 개체와 연결 된 하나의 실행 취소 관리자에 배치 됩니다.  
  
 각 뷰에 대해 하나씩 실행 취소 관리자를 쿼리 하는 대신 문서 데이터 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> CLSID_OLEUndoManager의 클래스 식별자를 지정 하 여 실행 취소 관리자를 인스턴스화하기 위해를 호출 합니다. 클래스 식별자는 OCIDID.H 파일에 정의 되어 있습니다.  
  
 를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 사용자 고유의 실행 취소 관리자 인스턴스를 만들 때 다음 절차를 사용 하 여 실행 취소 관리자를 환경에 연결할 수 있습니다.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>실행 취소 관리자를 환경에 연결 하려면  
  
1. `QueryInterface`에 대해에서 반환 된 개체를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> `IID_IOleUndoManager` 합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 합니다.  
  
2. `QueryInterface` `IOleUndoManager` 에 대해를 호출 `IID_IOleCommandTarget` 합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 합니다.  
  
3. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 다음 StandardCommandSet97 명령에 대해 및 호출을 저장 된 인터페이스에 릴레이 `IOleCommandTarget` 합니다.  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. `QueryInterface` `IOleUndoManager` 에 대해를 호출 `IID_IVsChangeTrackingUndoManager` 합니다. 에 대 한 포인터를 저장 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> 합니다.  
  
    에 대 한 포인터를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> 및 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. `QueryInterface` `IOleUndoManager` 에 대해를 호출 `IID_IVsLinkCapableUndoManager` 합니다.  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>인터페이스를 구현 해야 하는 문서를 사용 하 여를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> . 문서가 닫히면를 호출 `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` 합니다.  
  
7. 문서가 닫히면 `QueryInterface` 의 실행 취소 관리자에서를 호출 `IID_IVsLifetimeControlledObject` 합니다.  
  
8. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>을 호출합니다.  
  
9. 문서가 변경 되 면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 클래스를 사용 하 여 관리자에 대해를 호출 `OleUndoUnit` 합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>메서드는 개체에 대 한 참조를 유지 하므로 일반적으로 바로 다음에 해당 개체를 해제 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> 합니다.  
  
   `OleUndoManager`클래스는 단일 실행 취소 스택 인스턴스를 나타냅니다. 따라서 실행 취소 또는 다시 실행에 대해 추적 되는 데이터 엔터티 마다 하나의 실행 취소 관리자 개체가 있습니다.  
  
> [!NOTE]
> 실행 취소 관리자 개체는 텍스트 편집기에서 광범위 하 게 사용 되지만 텍스트 편집기를 특정 하 게 지원 하지 않는 일반 구성 요소입니다. 다중 수준 실행 취소 또는 다시 실행을 지원 하려는 경우이 개체를 사용 하 여 작업을 수행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [방법: 실행 취소 스택 정리](../extensibility/how-to-clear-the-undo-stack.md)
