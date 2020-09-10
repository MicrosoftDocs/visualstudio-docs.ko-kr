---
title: 중첩 프로젝트 언로드 및 다시 로드
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86f8f2f02258bc55f3221635fddab8ecdaaa3cf7
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743242"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>중첩 프로젝트 언로드 및 다시 로드에 대 한 고려 사항

중첩 된 프로젝트 형식을 구현 하는 경우 프로젝트를 언로드하고 다시 로드할 때 추가 단계를 수행 해야 합니다. 수신기를 솔루션 이벤트에 올바르게 알리려면 및 이벤트를 올바르게 발생 시켜야 `OnBeforeUnloadProject` 합니다 `OnAfterLoadProject` .

이러한 이벤트를 발생 시키는 한 가지 이유는 SCC (소스 코드 제어)에 대 한 것입니다. Scc에서 작업을 수행 하는 경우 SCC가 서버에서 항목을 삭제 한 다음 *새* 항목으로 다시 추가 하지 않도록 합니다 `Get` . 이 경우 새 파일은 SCC에서 로드 됩니다. 다른 경우에는 모든 파일을 언로드하고 다시 로드 해야 합니다.

소스 코드 제어는 `ReloadItem` 를 호출 합니다. 을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 호출 하 `OnBeforeUnloadProject` 고 프로젝트를 `OnAfterLoadProject` 삭제 한 다음 다시 만들기 위해 인터페이스를 구현 합니다. 이러한 방식으로 인터페이스를 구현 하는 경우 SCC에는 프로젝트가 일시적으로 삭제 되 고 다시 추가 되었다는 알림이 표시 됩니다. 따라서 SCC는 프로젝트가 *실제로* 삭제 되 고 다시 추가 된 것 처럼 프로젝트에서 작동 하지 않습니다.

## <a name="reload-projects"></a>프로젝트 다시 로드

중첩 된 프로젝트를 다시 로드 하도록 지원 하려면 메서드를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 합니다. 구현에서 `ReloadItem` 중첩 된 프로젝트를 닫은 후 다시 만듭니다.

일반적으로 프로젝트가 다시 로드 될 때 IDE는 및 이벤트를 발생 시킵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> . 그러나 삭제 되 고 다시 로드 된 중첩 프로젝트의 경우에는 부모 프로젝트가 IDE가 아닌 프로세스를 시작 합니다. 부모 프로젝트가 솔루션 이벤트를 발생 시 키 지 않고 IDE에 프로세스의 초기화에 대 한 정보가 없으므로 이벤트는 발생 하지 않습니다.

이 프로세스를 처리 하기 위해 부모 프로젝트는 `QueryInterface` 인터페이스에서를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> . `IVsFireSolutionEvents` 에는 IDE에서 `OnBeforeUnloadProject` 중첩 된 프로젝트를 언로드하기 위해 이벤트를 발생 시키고 이벤트를 발생 시켜 동일한 프로젝트를 다시 로드 하도록 지시 하는 함수가 있습니다 `OnAfterLoadProject` .

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
