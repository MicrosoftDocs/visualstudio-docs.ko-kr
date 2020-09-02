---
title: Visual Studio의 작업 영역 파일 컨텍스트 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952817"
---
# <a name="workspace-file-contexts"></a>작업 영역 파일 컨텍스트

[Open Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 작업 영역에 대 한 모든 정보는 인터페이스를 구현 하는 "파일 컨텍스트 공급자"에 의해 생성 됩니다 <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> . 이러한 확장은 파일 컨텍스트를 정의 하는 데 필요한 정보를 축적 하기 위해 폴더 또는 파일의 패턴, MSBuild 파일 및 메이크파일 읽기, 패키지 종속성 검색 등을 찾을 수 있습니다. 자체적으로 파일 컨텍스트는 어떤 동작도 수행 하지 않고 다른 확장이 작업할 수 있는 데이터를 제공 합니다.

각에 <xref:Microsoft.VisualStudio.Workspace.FileContext> 는 `Guid` 전달 되는 데이터 형식을 식별 하는와 연결 된가 있습니다. 작업 영역에서는이를 나중에 사용 하 여 `Guid` 속성을 통해 데이터를 사용 하는 확장과 일치 시킵니다 <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> . 파일 컨텍스트 공급자는 데이터를 생성할 수 있는 파일 컨텍스트를 식별 하는 메타 데이터를 사용 하 여 내보내집니다 `Guid` .

정의 되 면 파일 컨텍스트를 작업 영역에 있는 원하는 수의 파일 또는 폴더와 연결할 수 있습니다. 지정 된 파일 또는 폴더는 개수에 관계 없이 파일 컨텍스트에 연결 될 수 있습니다. 다대다 관계입니다.

파일 컨텍스트의 가장 일반적인 시나리오는 빌드, 디버그 및 언어 서비스와 관련 되어 있습니다. 자세한 내용은 이러한 시나리오와 관련 된 다른 항목을 참조 하세요.

## <a name="file-context-lifecycle"></a>파일 컨텍스트 수명 주기

의 생명주 기 `FileContext` 는 명확 하지 않습니다. 언제 든 지 구성 요소가 일부 컨텍스트 형식 집합에 대해 비동기적으로 요청할 수 있습니다. 요청 컨텍스트 형식의 일부 하위 집합을 지 원하는 공급자를 쿼리할 수 있습니다. `IWorkspace`인스턴스는 메서드를 통해 소비자와 공급자 간의 중간 남자 역할을 합니다 <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> . 소비자는 컨텍스트를 요청 하 고 컨텍스트를 기반으로 하는 단기 작업을 수행할 수 있으며, 다른 사용자는 컨텍스트를 요청 하 고 수명이 긴 참조를 유지 관리할 수 있습니다.

파일 컨텍스트가 오래 되기 위해 파일에 변경 내용이 발생할 수 있습니다. 공급자는에서 이벤트를 발생 하 여 `FileContext` 소비자에 게 업데이트를 알릴 수 있습니다. 예를 들어, 일부 파일에 대해 빌드 컨텍스트가 제공 되었지만 디스크 상의 변경으로 해당 컨텍스트가 무효화 되 면 원래 생산자는 이벤트를 호출할 수 있습니다. 계속 해 서 참조 하는 모든 소비자는 `FileContext` 새에 대해 다시 쿼리할 수 있습니다 `FileContext` .

>[!NOTE]
>소비자에 게 푸시 모델이 없습니다. 요청 후에는 공급자의 새에 대 한 알림이 소비자에 게 표시 되지 않습니다 `FileContext` .

## <a name="expensive-file-context-computations"></a>비용이 많이 드는 파일 컨텍스트 계산

특히 공급자가 파일 간의 관계를 확인 해야 하는 경우 디스크에서 파일 콘텐츠를 읽으면 비용이 많이 들 수 있습니다. 예를 들어 공급자가 일부 소스 파일의 파일 컨텍스트에 대해 쿼리 될 수 있지만 파일 컨텍스트는 프로젝트 파일의 메타 데이터에 종속 됩니다. 프로젝트 파일을 구문 분석 하거나 MSBuild를 사용 하 여 평가 하는 것은 비용이 많이 듭니다. 대신 확장은를 내보내 `IFileScanner` `FileDataValue` 작업 영역 인덱싱 중에 데이터를 만들 수 있습니다. 이제 파일 컨텍스트를 묻는 메시지가 표시 되 면에서 해당 `IFileContextProvider` 인덱싱된 데이터를 빠르게 쿼리할 수 있습니다. 인덱싱에 대 한 자세한 내용은 [작업 영역 인덱싱](workspace-indexing.md) 항목을 참조 하세요.

>[!WARNING]
>계산 하는 데 비용이 많이 들 수 있는 다른 방법에 주의 해야 `FileContext` 합니다. 일부 UI 상호 작용은 동기식 이며 많은 양의 요청을 사용 `FileContext` 합니다. 예를 들어 편집기 탭을 열고 **솔루션 탐색기** 상황에 맞는 메뉴를 엽니다. 이러한 작업은 많은 빌드 컨텍스트 형식 요청을 수행 합니다.

## <a name="file-context-related-apis"></a>파일 컨텍스트 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> 데이터 및 메타 데이터를 저장 합니다.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider><xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1>파일 컨텍스트를 만듭니다.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> 파일 컨텍스트 공급자를 내보냅니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 는 소비자가 파일 컨텍스트를 가져오는 데 사용 됩니다.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 열려 있는 폴더에서 사용 하는 빌드 컨텍스트 형식을 정의 합니다.

## <a name="file-context-actions"></a>파일 컨텍스트 작업

자체는 `FileContext` 일부 파일에 대 한 데이터 일 뿐 이지만는 <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 해당 데이터를 표현 하 고 작업 하는 방법입니다. `IFileContextAction` 은 (는) 사용이 유연 합니다. 가장 일반적인 두 가지 사례는 빌드 및 디버깅입니다.

## <a name="reporting-progress"></a>진행 상황 보고

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>메서드가 전달 `IProgress<IFileContextActionProgressUpdate>` 되었지만 인수를 해당 형식으로 사용할 수 없습니다. `IFileContextActionProgressUpdate` 가 빈 인터페이스 이며를 호출 하면이 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` throw 될 수 있습니다 `NotImplementedException` . 대신는 `IFileContextAction` 시나리오에 필요한 대로 인수를 다른 형식으로 캐스팅 해야 합니다.

Visual Studio에서 제공 하는 형식에 대 한 자세한 내용은 해당 시나리오의 설명서를 참조 하세요.

## <a name="file-context-action-related-apis"></a>파일 컨텍스트 작업 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 에 따라 몇 가지 동작을 실행 `FileContext` 합니다.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> 의 인스턴스를 만듭니다 `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 형식을 내보냅니다 `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>파일 감시

작업 영역은 파일 변경 알림을 수신 하 고 via를 제공 합니다 <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . "ExcludedItems" 설정과 일치 하는 파일은 파일 알림 이벤트를 생성 하지 않습니다. 이벤트 간의 임계값은 알림 단순화 및 중복 감소에 사용 됩니다. 파일 변경에 반응 해야 하는 경우이 서비스를 구독 해야 합니다.

>[!TIP]
>작업 영역의 [인덱싱 서비스](workspace-indexing.md) 는 기본적으로 파일 이벤트를 구독 합니다. 파일을 추가 하 고 수정 하면 `IFileScanner` 해당 파일의 새 데이터에 대해 관련 된 이벤트가 호출 됩니다. 파일을 삭제 하면 인덱싱된 데이터가 제거 됩니다. 를 `IFileScanner` 파일 감시자 서비스에 구독할 필요가 없습니다.

## <a name="next-steps"></a>다음 단계

* [인덱싱](workspace-indexing.md) -작업 영역 인덱싱은 작업 영역에 대 한 정보를 수집 하 고 유지 합니다.
* [작업 영역](workspaces.md) -작업 영역 개념 및 설정 저장소를 검토 합니다.
