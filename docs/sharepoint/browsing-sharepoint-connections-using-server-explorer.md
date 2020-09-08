---
title: 서버 탐색기를 사용하여 SharePoint 연결 찾아보기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016351"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>서버 탐색기를 사용하여 SharePoint 연결 찾아보기
  이제 **서버 탐색기**에서 로컬 SharePoint 연결을 찾아볼 수 있습니다. 이 방법을 사용하면 시스템에서 SharePoint 사이트의 구성 요소를 탐색할 수 있습니다. 목록 정의, 콘텐츠 형식 등의 SharePoint 사이트 구성 요소는 **서버 탐색기** 트리 뷰에서 **SharePoint 연결** 노드에 표시됩니다. **서버 탐색기**를 표시하려면 메뉴 모음에서 **보기** > **서버 탐색기**를 선택합니다. SharePoint 사이트 구성 요소를 표시하는 것 외에도 바로 가기 메뉴의 명령을 사용하여 항목을 제거하거나, 속성을 보거나, 트리 뷰를 새로 고칠 수 있습니다.

> [!IMPORTANT]
> SharePoint 사이트를 탐색하려면 SharePoint 사이트 컬렉션의 관리자여야 하고 로컬 컴퓨터의 관리자로서 Visual Studio를 실행해야 합니다. 그러지 않으면 사이트가 **서버 탐색기**에 나타나지만 해당 노드를 확장할 수 없습니다. 사이트 모음 관리자인지 여부를 확인하려면 웹 브라우저에서 사이트를 열고 **사이트 작업** 메뉴를 연 다음, **사이트 권한**을 선택하고 **사용 권한: 팀 사이트** 페이지에서 리본의 **관리** 그룹에 있는 **사이트 모음 관리자** 명령을 선택합니다. 사이트 모음 관리자인 경우 사용자 이름이 텍스트 상자에 표시됩니다. **사이트 모음 관리자** 명령이 리본의 관리 그룹에 표시되지 않으면 사이트 모음의 관리자가 아닌 것이므로 사이트 관리자로부터 적절한 사용 권한을 얻어야 합니다.

## <a name="server-explorer-nodes"></a>서버 탐색기 노드
 SharePoint 사이트의 각 구성 요소는 **서버 탐색기** 트리 뷰에서 **SharePoint 연결** 아래의 노드로 표시됩니다. 예를 들어 기본 SharePoint 사이트에는 SharePoint 사이트의 **토론** 페이지에 표시되는 토론 형식을 나타내는 토론 콘텐츠 형식이 포함됩니다. 토론 콘텐츠 형식에는 여러 필드가 포함되어 있습니다. **서버 탐색기**에서 해당 필드를 보려면 **ContentTypes** 노드, **토론** 노드를 차례로 확장합니다. 그 아래에는 본문, 토론 주제, 제목 등의 여러 필드 노드가 있습니다.

## <a name="node-shortcut-menu-commands"></a>노드 바로 가기 메뉴 명령
 각 노드에는 노드를 마우스 오른쪽 단추로 클릭하거나 노드를 선택한 다음 **Shift**+**F10** 키를 선택하여 액세스하는 바로 가기 메뉴가 있습니다. 노드 명령에는 다음이 포함될 수 있습니다.

|명령 이름|설명|
|------------------|-----------------|
|새로 고침|노드를 마지막으로 표시한 이후 발생했을 수 있는 변경 내용을 반영하도록 트리 뷰를 업데이트합니다.|
|삭제|트리 뷰에서 선택한 노드를 제거합니다. **참고:**  이 명령은 **SharePoint 연결** 노드 아래에 나열된 SharePoint 연결에 대해서만 사용할 수 있습니다.|
|속성|**속성** 창에서 선택한 노드에 사용할 수 있는 속성을 표시합니다. 속성은 모두 읽기 전용이며, 모든 노드에 속성이 연결되어 있는 것은 아닙니다.|
|연결 추가|찾아보려는 SharePoint 사이트를 지정할 수 있습니다. **SharePoint 연결** 노드 및 하위 사이트 노드에서 사용할 수 있습니다.|
|브라우저에서 보기|웹 브라우저에서 선택한 목록을 표시합니다. 이 명령은 **목록 및 라이브러리**에 포함된 **목록** 노드 아래의 일부 목록에 대해 사용할 수 있습니다.|

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 연결 추가 또는 제거](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|**서버 탐색기**의 **SharePoint 연결** 노드에 새 SharePoint 사이트를 추가하는 데 필요한 단계를 설명합니다.|

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
