---
title: 문서 잠금 홀더 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712131"
---
# <a name="document-lock-holder-management"></a>문서 잠금 홀더 관리

실행 중인 문서 테이블(RDT)은 열려 있는 문서 수와 해당 문서의 편집 잠금을 유지 관리합니다. 사용자가 문서 창에서 열린 문서를 볼 수 없는 경우 백그라운드에서 프로그래밍 방식으로 편집할 때 RDT의 문서에 편집 잠금을 배치할 수 있습니다. 이 기능은 그래픽 사용자 인터페이스를 통해 여러 파일을 수정하는 디자이너가 자주 사용합니다.

## <a name="document-lock-holder-scenarios"></a>문서 잠금 홀더 시나리오

### <a name="file-a-has-a-dependence-on-file-b"></a>파일 "a"는 파일 "b"에 대한 종속성을 가미합니다.

파일 형식 "a"에 대한 표준 편집기 "A"를 구현하고 "a"형식의 각 파일에 "b"형식의 파일에 대한 참조가 있는 상황을 고려하십시오. "b"형식의 파일에 대한 표준 편집기 "B"가 있습니다. 편집기 "A"가 파일 "a"를 열면 해당 파일 "b"에 대한 참조를 검색합니다. 파일 "b"는 표시되지 않지만 편집기 "A"는 수정할 수 있습니다. 편집기 "A"는 메서드에서 파일 "b"의 문서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 데이터에 대한 참조를 가져오고 파일 "b"에 대한 편집 잠금을 유지합니다. 편집기 "A"가 파일 "b"를 수정한 후 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> 메서드를 호출하여 파일 "b"에 대한 편집 잠금 수를 감소시킬 수 있습니다. 매개 변수가 `dwRDTLockType` _VSRDTFLAGS 설정된 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 호출한 경우 이 단계를 생략할 수 [있습니다. RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>파일 "b"는 다른 편집기에서 열립니다.

편집기 "A"가 파일을 열려고 할 때 파일 "b"가 이미 편집기 "B"에 의해 열려있는 경우 처리할 두 가지 별도의 시나리오가 있습니다.

- 호환되는 편집기에서 파일 "b"가 열려 있는 경우 편집기 "A"가 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> 사용하여 파일 "b"에 대한 문서 편집 잠금을 등록해야 합니다. 편집기 "A"가 파일 "b"를 수정한 후 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> 문서 편집 잠금을 등록 취소합니다.

- 파일 "b"가 호환되지 않는 방식으로 열려 있는 경우 편집기 "A"에 의해 파일 "b"의 열기 시도가 실패하도록 하거나 편집기 "A"와 연결된 뷰를 부분적으로 열고 적절한 오류 메시지를 표시하도록 할 수 있습니다. 오류 메시지는 호환되지 않는 편집기에서 파일 "b"를 닫은 다음 편집기 "A"를 사용하여 파일 "a"를 다시 열도록 사용자에게 지시해야 합니다. 호환되지 않는 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 편집기에서 열려 있는 파일 "b"를 닫도록 사용자에게 메시지를 표시하는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> 구현할 수도 있습니다. 사용자가 파일 "b"를 닫으면 편집기 "A"에서 파일 "a"의 열기가 정상적으로 계속됩니다.

## <a name="additional-document-edit-lock-considerations"></a>추가 문서 편집 잠금 고려 사항

편집기 "A"가 문서 편집 잠금이 파일 "b"에 있는 유일한 편집기인 경우 편집기 "B"가 파일 "b"에 대한 문서 편집 잠금을 보유하는 경우와 는 다른 동작이 있습니다. 에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **클래스 디자이너는** 연결된 코드 파일에 편집 잠금을 보유하지 않는 시각적 디자이너의 예입니다. 즉, 사용자가 디자인 뷰에서 클래스 다이어그램이 열리고 관련 코드 파일이 동시에 열리고 사용자가 코드 파일을 수정하지만 변경 내용을 저장하지 않으면 변경 내용도 클래스 다이어그램(.cd) 파일로 손실됩니다. 클래스 **디자이너가** 코드 파일에 대한 유일한 문서 편집 잠금을 가지고 있는 경우 사용자는 코드 파일을 닫을 때 변경 내용을 저장하라는 메시지가 지정되지 않습니다. IDE는 사용자가 **클래스 디자이너를**닫은 후에만 변경 내용을 저장하도록 사용자에게 요청합니다. 저장된 변경 내용은 두 파일에 모두 반영됩니다. **클래스 디자이너와** 코드 파일 편집기 모두 코드 파일에 대한 문서 편집 잠금을 유지한 경우 코드 파일 또는 양식을 닫을 때 저장하라는 메시지가 표시됩니다. 이 때 저장된 변경 내용은 양식과 코드 파일 모두에 반영됩니다. 클래스 다이어그램에 대한 자세한 내용은 [클래스 다이어그램(클래스 디자이너)을 사용할 수 있는 작업을](../ide/class-designer/designing-and-viewing-classes-and-types.md)참조하십시오.

편집기 이외의 문서에 편집 잠금을 배치해야 하는 경우 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> 구현해야 합니다.

코드 파일을 프로그래밍 방식으로 수정하는 UI 디자이너가 두 개 이상의 파일을 변경하는 경우가 많습니다. 이러한 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> 메서드는 **다음 항목에 변경 내용을 저장하시겠습니까?** 대화 상자를 통해 하나 이상의 문서를 저장처리합니다.

## <a name="see-also"></a>참조

- [문서 테이블 실행](../extensibility/internals/running-document-table.md)
- [지속성 및 실행 중인 문서 테이블](../extensibility/internals/persistence-and-the-running-document-table.md)
