---
title: 중첩 프로젝트 언로드 및 재로드고려사항 | 마이크로 소프트 문서
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
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709298"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>중첩된 프로젝트 언로드 및 다시 로드에 대한 고려 사항

중첩된 프로젝트 형식을 구현할 때 프로젝트를 언로드하고 다시 로드할 때 추가 단계를 수행해야 합니다. 솔루션 이벤트에 대해 리스너에게 올바르게 `OnBeforeUnloadProject` 알리려면 `OnAfterLoadProject` 및 이벤트를 올바르게 발생시켜야 합니다.

이러한 이벤트를 발생 하는 한 가지 이유는 소스 코드 제어 (SCC)에 대 한 것입니다. SCC에서 항목을 삭제한 다음 SCC에서 작업이 있는 경우 *새* 항목으로 `Get` 다시 추가하는 것을 원하지 않습니다. 이 경우 새 파일이 SCC에서 로드됩니다. 다른 경우를 대비하여 모든 파일을 언로드하고 다시 로드해야 합니다.

소스 코드 `ReloadItem`제어 호출합니다. 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> `OnBeforeUnloadProject` 프로젝트를 삭제하고 `OnAfterLoadProject` 다시 만들 인터페이스를 구현합니다. 이러한 방식으로 인터페이스를 구현하면 SCC는 프로젝트가 일시적으로 삭제되고 다시 추가되었다는 알림을 보습니다. 따라서 SCC는 프로젝트가 *실제로* 삭제되고 다시 추가된 것처럼 프로젝트에서 작동하지 않습니다.

## <a name="reload-projects"></a>프로젝트 재로드

중첩된 프로젝트의 재로드를 지원하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> 메서드를 구현합니다. `ReloadItem`을 구현할 때 중첩된 프로젝트를 닫은 다음 다시 만듭니다.

일반적으로 프로젝트가 다시 로드되면 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> 이벤트를 발생시게 됩니다. 그러나 삭제되고 다시 로드되는 중첩 된 프로젝트의 경우 상위 프로젝트는 IDE가 아닌 프로세스를 시작합니다. 상위 프로젝트는 솔루션 이벤트를 발생하지 않으며 IDE에는 프로세스의 초기화에 대한 정보가 없으므로 이벤트가 발생하지 않습니다.

이 프로세스를 처리 하려면 `QueryInterface` 부모 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> 프로젝트는 인터페이스를 호출 합니다. `IVsFireSolutionEvents`는 중첩 된 프로젝트를 언로드 `OnBeforeUnloadProject` 하는 이벤트를 발생 하 고 동일한 `OnAfterLoadProject` 프로젝트를 다시 로드 하는 이벤트를 발생 하도록 IDE를 알리는 함수를 가지고 있습니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [네스트 프로젝트](../../extensibility/internals/nesting-projects.md)
