---
title: RDT_ReadLock 사용 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705925"
---
# <a name="rdt_readlock-usage"></a>RDT_ReadLock 사용법

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 현재 Visual Studio IDE에서 열려 있는 모든 문서의 목록인 RDT(실행 중인 문서 테이블)에서 문서를 잠그는 논리를 제공하는 플래그입니다. 이 플래그는 문서가 열리는 시기와 문서가 사용자 인터페이스에 표시되는지 또는 메모리에 보이지 않게 유지되는지 여부를 결정합니다.

일반적으로 _VSRDTFLAGS [사용합니다. 다음](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) 중 하나가 true인 경우 RDT_ReadLock:

- 보이지 않게 읽기 전용으로 문서를 열려고 하지만 아직 문서를 소유해야 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 문서가 설정되지 않았습니다.

- 사용자가 UI에 표시하기 전에 보이지 않게 열린 문서를 저장하라는 메시지가 표시되고 닫으려고 합니다.

## <a name="how-to-manage-visible-and-invisible-documents"></a>가시적이고 보이지 않는 문서를 관리하는 방법

사용자가 UI에서 문서를 열때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 문서의 소유자가 설정되고 [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) 플래그를 설정해야 합니다. 소유자를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 설정할 수 없는 경우 사용자가 **모두 저장을** 클릭하거나 IDE를 닫을 때 문서가 저장되지 않습니다. 즉, 문서가 메모리에서 수정된 곳에서 보이지 않게 열려 있고 사용자가 종료 시 문서를 저장하라는 메시지가 표시되거나 `RDT_ReadLock` **모두 저장을** 선택한 경우 저장할 수 없는 경우 사용할 수 없습니다. 대신 __VSREGDOCLOCKHOLDER 를 `RDT_EditLock` 사용하고 등록해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> [합니다. 플래그를 RDLH_WeakLockHolder.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>)

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock 및 문서 수정

언급 된 이전 플래그는 문서가 표시되는 `RDT_EditLock` **DocumentWindow로**사용자가 열 때 문서의 보이지 않는 열면 해당 문서가 생성됨을 나타냅니다. 이 경우 표시되는 **DocumentWindow가** 닫히면 사용자에게 **저장** 프롬프트가 표시됩니다. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`<xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> 서비스를 사용하는 구현은 처음에 `RDT_ReadLock` 만 수행될 때 작동합니다(예: 문서를 보이지 않게 열어 정보를 구문 분석하는 경우). 나중에 문서를 수정해야 하는 경우 잠금이 약한 **RDT_EditLock**업그레이드됩니다. 그런 다음 사용자가 표시되는 **문서창에서** `CodeModel`문서를 열면 `RDT_EditLock` 약이 해제됩니다.

그런 다음 사용자가 **DocumentWindow를** 닫고 열려 있는 문서를 저장하라는 `CodeModel` 메시지가 표시될 때 **아니요를** 선택하면 구현에서 문서에 대한 자세한 정보가 필요할 때 문서에 대한 자세한 정보가 필요할 때 문서에서 문서를 보이지 않게 삭제하고 문서를 다시 엽니다. 이 동작의 미묘함은 사용자가 보이지 않는 열린 문서의 **DocumentWindow를** 열고 수정하고 닫은 다음 문서를 저장하라는 메시지가 표시될 때 **아니요를** 선택하는 인스턴스입니다. 이 경우 문서에 `RDT_ReadLock`의한 문서가 있는 경우 사용자가 문서를 저장하지 않기로 선택했음에도 불구하고 문서가 실제로 닫히지 않고 수정된 문서가 메모리에서 보이지 않게 열려 있는 상태를 유지합니다.

문서의 보이지 않는 열기가 약한 `RDT_EditLock`경우 사용자가 문서를 눈에 띄게 열고 다른 잠금이 유지되지 않으면 잠금이 생성됩니다. 사용자가 **DocumentWindow를** 닫고 문서를 저장하라는 메시지가 표시될 때 **아니요를** 선택하면 문서가 메모리에서 닫아야 합니다. 즉, 보이지 않는 클라이언트는 이 발생을 추적하기 위해 RDT 이벤트를 수신 수신해야 합니다. 다음에 문서가 필요할 때 문서를 다시 열어야 합니다.
