---
title: Visual Studio의 작업 영역 인덱싱 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952712"
---
# <a name="workspace-indexing"></a>작업 영역 인덱싱

솔루션에서 프로젝트 시스템은 **빌드, 디버그, 기호** 검색 등을 위한 기능을 제공 합니다. 프로젝트 시스템은 프로젝트 내에서 파일의 관계와 기능을 이해 하기 때문에이 작업을 수행할 수 있습니다. [열려 있는 폴더](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 작업 영역에도 풍부한 IDE 기능을 제공 하는 것과 같은 정보가 필요 합니다. 이 데이터의 컬렉션 및 영구 저장소는 작업 영역 인덱싱 이라는 프로세스입니다. 이 인덱싱된 데이터는 비동기 Api 집합을 통해 쿼리할 수 있습니다. Extender <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> 는 특정 형식의 파일을 처리 하는 방법을 알고 있는를 제공 하 여 인덱싱 프로세스에 참여할 수 있습니다.

## <a name="types-of-indexed-data"></a>인덱싱된 데이터의 형식

인덱싱된 데이터에는 세 가지 종류가 있습니다. 참고 파일 검색 프로그램에서 예상 되는 형식은 인덱스에서 deserialize 된 형식과 다릅니다.

|데이터|파일 스캐너 유형|인덱스 쿼리 결과 형식|관련 형식|
|--|--|--|--|
|참조|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|기호|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService>쿼리에 대신 사용 해야 합니다. `IIndexWorkspaceService`|
|데이터 값|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>인덱싱된 데이터 쿼리

지속형 데이터에 액세스 하는 데 사용할 수 있는 두 가지 비동기 형식이 있습니다. 첫 번째는를 통하는 것입니다 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . 단일 파일 및 데이터에 대 한 기본 액세스를 제공 하 `FileReferenceResult` `FileDataResult` 고 결과를 캐시 합니다. 두 번째는 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> 캐싱을 사용 하지 않지만 더 많은 쿼리 기능을 허용 하는입니다.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>인덱싱 참여

작업 영역 인덱싱은 대략 다음 시퀀스를 따릅니다.

1. 작업 영역에서 파일 시스템 엔터티의 검색 및 지 속성 (초기 열기 검색 시에만 해당)
1. 파일에 따라 우선 순위가 가장 높은 일치 하는 공급자에는를 검색 하 라는 메시지가 표시 됩니다 `FileReferenceInfo` .
1. 파일에 따라 우선 순위가 가장 높은 일치 하는 공급자에는를 검색 하 라는 메시지가 표시 됩니다 `SymbolDefinition` .
1. 파일당 모든 공급자에 게를 요청 `FileDataValue` 합니다.

확장은를 사용 하 여 형식을 구현 하 고 내보내 스캐너를 내보낼 수 있습니다 `IWorkspaceProviderFactory<IFileScanner>` <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . `SupportedTypes`특성 인수는에서 하나 이상의 값 이어야 합니다 <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . 예제 스캐너는 VS SDK [샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)을 참조 하세요.

> [!WARNING]
> 유형을 지 원하는 파일 스캐너를 내보내지 않습니다 `FileScannerTypeConstants.FileScannerContentType` . Microsoft 내부용 으로만 사용 됩니다.

고급 상황에서 확장은 임의 파일 형식 집합을 동적으로 지원할 수 있습니다. MEF를 내보내는 대신 `IWorkspaceProviderFactory<IFileScanner>` 확장을 내보낼 수 있습니다 `IWorkspaceProviderFactory<IFileScannerProvider>` . 인덱싱이 시작 되 면이 팩터리 형식을 가져오고 인스턴스화한 다음 해당 <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> 메서드를 호출 합니다. `IFileScanner` 의 모든 값을 지 원하는 인스턴스 `FileScannerTpeConstants` 는 기호 뿐만 아니라 그대로 적용 됩니다.

## <a name="next-steps"></a>다음 단계

* [작업 영역 및 언어 서비스](workspace-language-services.md) -공개 폴더 작업 영역에 언어 서비스를 통합 하는 방법에 대해 알아봅니다.
* [작업 영역 빌드](workspace-build.md) -열기 폴더는 MSBuild 및 메이크파일과 같은 빌드 시스템을 지원 합니다.