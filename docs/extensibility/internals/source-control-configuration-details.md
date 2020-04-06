---
title: 소스 제어 구성 세부 정보 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705289"
---
# <a name="source-control-configuration-details"></a>소스 제어 구성 세부 정보
소스 제어를 구현하려면 다음을 수행하도록 프로젝트 시스템 이나 편집기를 올바르게 구성해야 합니다.

- 변경된 상태로 전환할 수 있는 권한 요청

- 파일 저장 권한 요청

- 프로젝트에서 파일을 추가, 제거 또는 이름 바꾸기 위한 권한 요청

## <a name="request-permission-to-transition-to-changed-state"></a>변경된 상태로 전환할 수 있는 권한 요청
 프로젝트 또는 편집기는 을 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>변경된(더티) 상태로 전환할 수 있는 권한을 요청해야 합니다. 구현하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> 각 편집기는 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 반환하기 `True` 전에 환경에서 문서를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>변경하려면 호출하고 승인을 받아야 합니다. 프로젝트는 본질적으로 프로젝트 파일의 편집기이며, 결과적으로 텍스트 편집기에서와 마찬가지로 프로젝트 파일에 대한 변경 된 상태 추적을 구현하는 것과 동일한 책임이 있습니다. 환경은 솔루션의 변경된 상태를 처리하지만 솔루션이 참조하지만 프로젝트 파일이나 해당 항목과 같이 저장하지 않는 개체의 변경된 상태를 처리해야 합니다. 일반적으로 프로젝트 또는 편집기가 항목에 대한 지속성을 관리하는 경우 변경된 상태 추적을 구현해야 합니다.

 호출에 `IVsQueryEditQuerySave2::QueryEditFiles` 대한 응답으로 환경은 다음을 수행할 수 있습니다.

- 변경 요청을 거부하면 편집기 또는 프로젝트가 변경되지 않은(정리) 상태로 유지되어야 합니다.

- 문서 데이터를 다시 로드해야 함을 나타냅니다. 프로젝트의 경우 환경이 프로젝트의 데이터를 다시 로드합니다. 편집기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 구현을 통해 디스크에서 데이터를 다시 로드해야 합니다. 두 경우 모두 데이터를 다시 로드할 때 프로젝트 또는 편집기의 컨텍스트가 변경될 수 있습니다.

  기존 코드 베이스에 적절한 `IVsQueryEditQuerySave2::QueryEditFiles` 호출을 다시 맞게 하는 것은 복잡하고 어려운 작업입니다. 따라서 이러한 호출은 프로젝트 또는 편집기 작성 중에 통합되어야 합니다.

## <a name="request-permission-to-save-a-file"></a>파일 저장 권한 요청
 프로젝트 또는 편집기에서 파일을 저장하기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 전에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>호출하거나 . 프로젝트 파일의 경우 이러한 호출은 프로젝트 파일을 저장할 시기를 알고 있는 솔루션에 의해 자동으로 완료됩니다. 편집기는 편집자 구현이 도우미 함수를 `IVsPersistDocData2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>사용하지 않는 한 이러한 호출을 담당합니다. 편집기에서 `IVsPersistDocData2` 이러한 방식으로 구현하는 경우 `IVsQueryEditQuerySave2::QuerySaveFile` 호출하거나 `IVsQueryEditQuerySave2::QuerySaveFiles` 수행할 수 있습니다.

> [!NOTE]
> 항상 이러한 호출을 선제적으로, 즉 편집자가 취소를 받을 수 있는 시점에 호출합니다.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>프로젝트에서 파일 추가, 제거 또는 이름 바꾸기 권한 요청
 프로젝트가 파일이나 디렉터리를 추가, 이름 변경 또는 제거하기 전에 `IVsTrackProjectDocuments2::OnQuery*` 환경의 권한을 요청하는 적절한 메서드를 호출해야 합니다. 권한이 부여되면 프로젝트는 작업을 완료한 다음 적절한 `IVsTrackProjectDocuments2::OnAfter*` 메서드를 호출하여 작업이 완료되었음을 환경에 알립니다. 프로젝트는 부모 파일뿐만 아니라 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 모든 파일(예: 특수 파일)에 대한 인터페이스 메서드를 호출해야 합니다. 파일 호출은 필수이지만 디렉터리 호출은 선택 사항입니다. 프로젝트에 디렉터리 정보가 있는 경우 적절한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 메서드를 호출해야 하지만 이 정보가 없는 경우 환경은 디렉터리 정보를 유추합니다.

 프로젝트는 프로젝트 열기 또는 `IVsTrackProjectDocuments2` 닫기의 메서드를 호출해서는 안 됩니다. 시작 시 이 정보를 원하는 리스너는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> 이벤트를 기다렸다가 솔루션을 반복하여 필요한 정보를 찾을 수 있습니다. 종료 시 이 정보는 필요하지 않습니다. `IVsTrackProjectDocuments2`에서 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>제공됩니다.

 각 추가, 이름 바꾸기 및 제거 작업에 `OnQuery*` 대해 `OnAfter*` 메서드와 메서드가 있습니다. 메서드를 `OnQuery*` 호출하여 파일 또는 디렉터리를 추가, 이름 변경 또는 제거할 수 있는 권한을 요청합니다. 파일 `OnAfter*` 또는 디렉터리가 추가, 이름 변경 또는 제거된 후 메서드를 호출하고 프로젝트 상태가 새 상태를 반영합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
