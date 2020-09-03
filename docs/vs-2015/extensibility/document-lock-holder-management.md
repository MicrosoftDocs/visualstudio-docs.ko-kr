---
title: 문서 잠금 보유자 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204626"
---
# <a name="document-lock-holder-management"></a>문서 잠금 소유자 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RT (실행 중인 문서 테이블)는 열려 있는 문서 및 편집 잠금 수를 유지 관리 합니다. 사용자가 문서 창에서 열린 문서를 보지 않고도 백그라운드에서 프로그래밍 방식으로 편집 된 문서에 대 한 편집 잠금을 추가할 수 있습니다. 이 기능은 그래픽 사용자 인터페이스를 통해 여러 파일을 수정 하는 디자이너에서 주로 사용 됩니다.  
  
## <a name="document-lock-holder-scenarios"></a>문서 잠금 표시자 시나리오  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>"A" 파일은 "b" 파일에 종속 되어 있습니다.  
 "A" 파일 형식에 대 한 표준 편집기 "A"를 구현 하 고 "a" 형식의 각 파일에 "b" 형식의 파일에 대 한 참조 (또는 종속성)가 있는 경우를 고려해 보세요. "B" 형식의 파일에 대 한 표준 편집기 "B"가 있습니다. "A" 편집기가 "a" 파일을 열면 해당 파일 "b"에 대 한 참조를 검색 합니다. "B" 파일이 표시 되지 않지만 "A" 편집기에서 수정할 수 있습니다. "A" 편집기는 메서드에서 파일 "b"의 문서 데이터에 대 한 참조를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> "b" 파일에 대 한 편집 잠금도 유지 합니다. "A" 편집기가 "b" 파일 수정을 완료 한 후에는 메서드를 호출 하 여 파일 "b"의 편집 잠금 수를 줄일 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>매개 변수를로 설정 하 여 메서드를 호출한 경우이 단계를 생략할 수 있습니다 `dwRDTLockType` <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> .  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>다른 편집기에서 파일 "b"를 열었습니다.  
 "B" 편집기가 파일을 열려고 할 때 "b" 편집기에서 파일 "b"를 이미 연 경우에는 다음 두 가지 개별 시나리오를 처리 해야 합니다.  
  
- "B" 파일이 호환 편집기에서 열려 있는 경우 메서드를 사용 하 여 "b" 파일에 문서 편집 잠금 등록 편집기가 있어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> . "A" 편집기가 "b" 파일을 수정 하는 작업을 수행한 후 메서드를 사용 하 여 문서 편집 잠금을 등록 취소 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> .  
  
- "B" 파일이 호환 되지 않는 방식으로 열려 있는 경우 "A" 편집기에서 "b" 파일을 열려고 하면 실패 하거나 "A" 편집기와 연결 된 뷰가 부분적으로 열리고 적절 한 오류 메시지가 표시 되도록 할 수 있습니다. 오류 메시지는 호환 되지 않는 편집기에서 파일 "b"를 닫도록 사용자에 게 지시 하 고 "a" 편집기를 사용 하 여 "a" 파일을 다시 엽니다. 메서드를 구현 하 여 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 호환 되지 않는 편집기에 열려 있는 파일 "b"를 닫도록 사용자에 게 표시할 수도 있습니다. 사용자가 "b" 파일을 닫으면 "A" 편집기에서 "a" 파일을 여는 작업이 정상적으로 계속 됩니다.  
  
## <a name="additional-document-edit-lock-considerations"></a>추가 문서 편집 잠금 고려 사항  
 "A" 편집기가 "b" 파일에 대 한 문서 편집 잠금을 포함 하는 유일한 편집기 인 경우 편집기 "b"가 파일 "b"에 대 한 문서 편집 잠금을 보유 하는 경우와는 다른 동작이 발생 합니다. 에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **클래스 디자이너** 은 연결 된 코드 파일에 대 한 편집 잠금을 보유 하지 않는 비주얼 디자이너의 예입니다. 즉, 사용자가 디자인 뷰에서 열린 클래스 다이어그램을 사용 하 고 연결 된 코드 파일을 동시에 열고 사용자가 코드 파일을 수정 하지만 변경 내용을 저장 하지 않는 경우에도 클래스 다이어그램 (.cd) 파일에 대 한 변경 내용이 손실 됩니다. **클래스 디자이너** 코드 파일에 대 한 문서 편집 잠금이 있는 경우 코드 파일을 닫을 때 사용자에 게 변경 내용을 저장할지 묻는 메시지가 표시 되지 않습니다. 사용자가 **클래스 디자이너**를 닫은 후에만 사용자에 게 변경 내용을 저장 하 라는 메시지가 표시 됩니다. 저장 된 변경 내용은 두 파일에 모두 반영 됩니다. **클래스 디자이너** 및 코드 파일 편집기 모두에서 코드 파일에 대 한 문서 편집 잠금을 보유 하 고 있는 경우 코드 파일이 나 폼을 닫을 때 사용자에 게 저장할지를 묻는 메시지가 표시 됩니다. 이때 저장 된 변경 내용은 양식과 코드 파일에 모두 반영 됩니다. 클래스 다이어그램에 대 한 자세한 내용은 [클래스 다이어그램 작업 (클래스 디자이너)](../ide/working-with-class-diagrams-class-designer.md)을 참조 하세요.  
  
 비 편집기의 문서에 편집 잠금을 설정 해야 하는 경우에는 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> .  
  
 프로그래밍 방식으로 코드 파일을 수정 하는 UI 디자이너에서 두 개 이상의 파일을 변경 하는 경우가 많습니다. 이러한 경우, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> 메서드는 **다음 항목에 대 한 변경 내용을 저장 하 시겠습니까?** 대화 상자를 사용 하 여 하나 이상의 문서를 저장 하는 작업을 처리 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [문서 테이블 실행](../extensibility/internals/running-document-table.md)   
 [지속성 및 실행 중인 문서 테이블](../extensibility/internals/persistence-and-the-running-document-table.md)
