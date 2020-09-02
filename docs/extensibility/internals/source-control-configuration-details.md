---
title: 소스 제어 구성 세부 정보 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705289"
---
# <a name="source-control-configuration-details"></a>소스 제어 구성 세부 정보
소스 제어를 구현 하려면 다음 작업을 수행 하도록 프로젝트 시스템 또는 편집기를 적절히 구성 해야 합니다.

- 변경 된 상태로 전환할 수 있는 권한 요청

- 파일 저장 권한 요청

- 프로젝트에서 파일을 추가, 제거 또는 이름을 바꿀 수 있는 권한 요청

## <a name="request-permission-to-transition-to-changed-state"></a>변경 된 상태로 전환할 수 있는 권한 요청
 프로젝트 또는 편집기는를 호출 하 여 변경 된 (더티) 상태로 전환 하는 권한을 요청 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . 을 반환 하기 전에를 구현 하는 각 편집기는를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 고 승인을 받아서 환경에서 문서를 변경 해야 합니다 `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . 프로젝트는 기본적으로 프로젝트 파일에 대 한 편집기 이므로 프로젝트 파일에 대 한 변경 된 상태 추적을 텍스트 편집기에서 구현 하는 것과 동일한 책임이 있습니다. 환경에서는 솔루션의 변경 된 상태를 처리 하지만 솔루션에서 참조 하는 개체의 변경 된 상태를 처리 해야 하지만 프로젝트 파일이 나 해당 항목과 같이 저장 되지 않습니다. 일반적으로 프로젝트 또는 편집기에서 항목에 대 한 지 속성을 관리 해야 하는 경우 변경 된 상태 추적을 구현 해야 합니다.

 환경에서 호출에 대 한 응답으로 `IVsQueryEditQuerySave2::QueryEditFiles` 다음을 수행할 수 있습니다.

- 변경에 대 한 호출을 거부 합니다 .이 경우 편집기나 프로젝트가 변경 되지 않은 상태로 유지 되어야 합니다 (clean).

- 문서 데이터를 다시 로드 해야 함을 표시 합니다. 프로젝트의 경우 환경에서 프로젝트에 대 한 데이터를 다시 로드 합니다. 편집기는 구현을 통해 디스크에서 데이터를 다시 로드 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> . 두 경우 모두 데이터가 다시 로드 될 때 프로젝트나 편집기의 컨텍스트가 변경 될 수 있습니다.

  기존 코드 베이스에 대 한 적절 한 호출을 갱신 하는 복잡 하 고 어려운 작업입니다 `IVsQueryEditQuerySave2::QueryEditFiles` . 따라서 프로젝트 또는 편집기를 만드는 동안 이러한 호출을 통합 해야 합니다.

## <a name="request-permission-to-save-a-file"></a>파일 저장 권한 요청
 프로젝트나 편집기에서 파일을 저장 하기 전에는 또는를 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . 프로젝트 파일의 경우 이러한 호출은 솔루션에서 자동으로 완료 되므로 프로젝트 파일을 저장할 시기를 알 수 있습니다. 편집기는의 편집기 구현에서 도우미 함수를 사용 하지 않는 한 이러한 호출을 수행 해야 `IVsPersistDocData2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 합니다. 편집기에서 이러한 방식으로를 구현 하는 경우 `IVsPersistDocData2` 또는에 `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` 대 한 호출이 생성 됩니다.

> [!NOTE]
> 이러한 호출은 항상 미리 (편집기에서 취소를 받을 수 있는 경우)로 설정 합니다.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>프로젝트에서 파일을 추가, 제거 또는 이름을 바꿀 수 있는 권한 요청
 프로젝트에서 파일 또는 디렉터리를 추가 하거나, 이름을 바꾸거나, 제거 하려면 먼저 해당 메서드를 호출 `IVsTrackProjectDocuments2::OnQuery*` 하 여 환경에서 사용 권한을 요청 해야 합니다. 사용 권한이 부여 된 경우 프로젝트에서 작업을 완료 한 다음 적절 한 메서드를 호출 `IVsTrackProjectDocuments2::OnAfter*` 하 여 작업이 완료 되었음을 환경에 알려야 합니다. 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 부모 파일만이 아닌 모든 파일 (예: 특수 파일)에 대해 인터페이스의 메서드를 호출 해야 합니다. 파일 호출은 필수 이지만 디렉터리 호출은 선택 사항입니다. 프로젝트에 디렉터리 정보가 있는 경우 적절 한 메서드를 호출 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 하지만,이 정보가 없는 경우 환경에서 디렉터리 정보를 유추 합니다.

 프로젝트를 열거나 닫을 때 프로젝트에서 메서드를 호출 하면 안 `IVsTrackProjectDocuments2` 됩니다. 시작 시이 정보를 필요로 하는 수신기는 이벤트를 대기 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 고 솔루션을 반복 하 여 필요한 정보를 찾을 수 있습니다. 종료 시에는이 정보가 필요 하지 않습니다. `IVsTrackProjectDocuments2` 는에서 제공 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 각 추가, 이름 바꾸기 및 제거 작업에는 `OnQuery*` 메서드와 `OnAfter*` 메서드가 있습니다. 메서드를 호출 `OnQuery*` 하 여 파일이 나 디렉터리를 추가 하거나, 이름을 바꾸거나, 제거할 수 있는 권한을 요청 합니다. `OnAfter*`파일이 나 디렉터리를 추가, 이름 변경 또는 제거 하 고 프로젝트 상태가 새 상태를 반영 하는 경우 메서드를 호출 합니다.

## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
