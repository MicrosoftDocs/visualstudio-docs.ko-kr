---
title: RDT_ReadLock 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705925"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock 사용법

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 는 현재 Visual STUDIO IDE에 열려 있는 모든 문서 목록 인 RDT (실행 중인 문서 테이블)에서 문서를 잠그기 위한 논리를 제공 하는 플래그입니다. 이 플래그는 문서가 열리는 시기 및 문서가 사용자 인터페이스에 표시 되는지 아니면 메모리에 표시 되지 않는지를 결정 합니다.

일반적으로 _VSRDTFLAGS를 사용 [합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 다음 중 하나가 true 인 경우 RDT_ReadLock 합니다.

- 문서를 보이지 않고 읽기 전용으로 열 수 있지만 아직 소유자가 설정 되지 않았습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .

- 사용자가 UI에 표시 하기 전에 표시 되지 않는 문서를 저장 하 라는 메시지가 표시 되 면 사용자가 해당 문서를 닫으려고 시도 합니다.

## <a name="how-to-manage-visible-and-invisible-documents"></a>표시 및 보이지 않는 문서를 관리 하는 방법

사용자가 UI에서 문서를 열 때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 문서의 소유자를 설정 하 고 _VSRDTFLAGS 해야 합니다 [. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) 플래그를 설정 해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>소유자를 설정할 수 없는 경우 사용자가 **모두 저장** 을 클릭 하거나 IDE를 닫으면 문서가 저장 되지 않습니다. 즉, 문서가 메모리에서 수정 된 위치에 표시 되지 않는 것을 의미 하 고, **모두 저장** 이 선택 된 경우 사용자에 게 문서를 저장 하거나 저장 하 라는 메시지가 표시 되 면를 `RDT_ReadLock` 사용할 수 없습니다. 대신를 사용 하 `RDT_EditLock` 고 __VSREGDOCLOCKHOLDER 때를 등록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> [. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) 플래그입니다.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock 및 문서 수정

앞에서 언급 한 플래그는 문서를 `RDT_EditLock` 사용자가 볼 수 있는 문서 **창**으로 열 때 문서를 볼 수 없는 문서를 열 때이를 생성 함을 나타냅니다. 이 경우 표시 되는 **문서 창이** 닫히면 사용자에 게 **저장** 프롬프트가 표시 됩니다. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` 서비스를 사용 하는 구현은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> 처음에만 수행 될 때 `RDT_ReadLock` (즉, 문서를 열 때 정보를 구문 분석 하는 것이 보이지 않는 경우)에 작동 합니다. 나중에 문서를 수정 해야 하는 경우 잠금이 weak **RDT_EditLock**로 업그레이드 됩니다. 그러면 사용자가 표시 된 문서 **창**에서 문서를 열면 `CodeModel` weak `RDT_EditLock` 가 해제 됩니다.

그런 다음 사용자가 **Documentwindow** 를 닫고 열려 있는 문서를 저장 하 라는 메시지가 표시 되 면 **아니요** 를 선택 하면, 문서에 `CodeModel` 있는 모든 정보를 삭제 하 고 다음에 문서에 대 한 추가 정보가 필요할 때 디스크에서 문서를 다시 엽니다. 이 동작의 미묘한 사용자가 보이지 않는 열려 있는 문서의 **Documentwindow** 를 열고 수정 하 고 닫은 다음 문서를 저장할지 묻는 메시지가 표시 되 면 **아니요** 를 선택 하는 인스턴스입니다. 이 경우 문서에이 있으면 문서를 `RDT_ReadLock` 실제로 닫지 않으며, 사용자가 문서를 저장 하지 않은 경우에도 수정 된 문서는 메모리에 보이지 않는 상태로 유지 됩니다.

보이지 않는 문서를 열 때 weak를 사용 하면 `RDT_EditLock` 사용자가 문서를 표시 하 고 다른 잠금은 보유 하지 않는 경우 잠금이 생성 됩니다. 사용자가 **Documentwindow** 를 닫고 문서를 저장 하 라는 메시지가 표시 되 면 **아니요** 를 선택 하면 메모리에서 문서를 닫아야 합니다. 즉, 보이지 않는 클라이언트는이 발생을 추적 하기 위해 RDT 이벤트를 수신 대기 해야 합니다. 다음에 문서가 필요할 때 문서를 다시 열어야 합니다.
