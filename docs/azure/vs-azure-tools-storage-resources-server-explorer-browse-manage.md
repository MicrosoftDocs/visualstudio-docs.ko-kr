---
title: 서버 탐색기로 스토리지 리소스 찾아보기 및 관리 | Microsoft Docs
description: 서버 탐색기로 스토리지 리소스 찾아보기 및 관리
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 8702b9814214a902a644cc5854250b600c301caa
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508446"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>서버 탐색기를 사용하여 스토리지 리소스 찾아보기 및 관리

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>개요

Microsoft Visual Studio용 Azure 도구를 설치한 경우 Azure 스토리지 계정에서 Blob, 큐 및 테이블 데이터를 볼 수 있습니다. 서버 탐색기의 Azure **storage** 노드는 로컬 저장소 에뮬레이터 계정 및 다른 azure storage 계정에 있는 데이터를 표시 합니다.

Visual Studio에서 서버 탐색기 보려면 메뉴 모음에서 **보기**  >  **서버 탐색기**를 선택 합니다. **스토리지** 노드는 연결된 각 Azure 구독 또는 인증서 아래에 존재하는 모든 스토리지 계정을 보여줍니다. 스토리지 계정이 나타나지 않으면 [이 문서 뒷부분](#add-storage-accounts-by-using-server-explorer)의 지침을 따라 추가할 수 있습니다.

Azure SDK 2.7부터 클라우드 탐색기를 사용해 Azure 리소스를 확인 및 관리할 수 있습니다. 자세한 내용은 [클라우드 탐색기를 사용 하 여 Azure 리소스 관리](vs-azure-tools-resources-managing-with-cloud-explorer.md)를 참조 하세요.

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio에서 스토리지 리소스를 확인 및 관리합니다.

서버 탐색기는 스토리지 에뮬레이터 계정에 있는 Blob, 큐, 테이블 목록을 자동으로 보여줍니다. 저장소 에뮬레이터 계정은 **저장소** 노드 아래 서버 탐색기에 **개발** 노드로 나열 됩니다.

스토리지 에뮬레이터 계정의 리소스를 보려면 **개발** 노드를 확장하세요. **개발** 노드를 확장했을 때 스토리지 에뮬레이터가 시작하지 않으면 자동으로 시작될 것입니다. 이 프로세스는 몇 초 정도 걸릴 수 있습니다. 스토리지 에뮬레이터가 시작하는 동안 Visual Studio의 다른 영역에서 작업을 계속할 수 있습니다.

스토리지 계정의 리소스를 보려면 서버 탐색기에서 스토리지 계정의 노드를 확장하세요. 그러면 **Blob**, **큐** 및 **테이블** 노드가 표시됩니다.

## <a name="work-with-blob-resources"></a>Blob 리소스로 작업

**Blob** 노드에는 선택한 저장소 계정에 대한 컨테이너 목록이 표시됩니다. Blob 컨테이너는 Blob 파일을 포함하고 있으며 이러한 Blob을 폴더와 하위 폴더로 구성할 수 있습니다. 자세한 내용은 [.NET에서 Blob Storage를 사용하는 방법](/azure/storage/blobs/storage-dotnet-how-to-use-blobs)(영문)을 참조하세요.

### <a name="to-create-a-blob-container"></a>Blob 컨테이너를 생성하려면

1. **Blob** 노드에 대한 바로 가기 메뉴를 열고 **Blob 컨테이너 만들기**를 선택합니다.
1. **Blob 컨테이너 만들기** 대화 상자에서 새 컨테이너 이름을 입력합니다.
1. 키보드에서 Enter 키를 누르거나 이름 필드 외부를 클릭하거나 탭하여 Blob 컨테이너를 저장합니다.

   > [!NOTE]
   > Blob 컨테이너 이름은 숫자 (0-9) 또는 소문자 (a-z)로 시작해야 합니다.

### <a name="to-delete-a-blob-container"></a>Blob 컨테이너를 삭제하려면

제거하려는 Blob 컨테이너에 대한 바로 가기 메뉴를 연 다음 **삭제**를 선택합니다.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Blob 컨테이너의 항목 목록을 표시하려면 다음을 수행합니다.

목록에서 Blob 컨테이너 이름에 대한 바로 가기 메뉴를 연 다음 **열기**를 선택합니다.

Blob 컨테이너의 콘텐츠를 보면 Blob 컨테이너 보기라는 탭이 표시됩니다.

![Blob 컨테이너 보기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob 컨테이너 보기의 오른쪽 위 모서리에 있는 단추를 사용하여 Blob에서 다음과 같은 작업을 수행할 수 있습니다.

* 필터 값을 입력하고 적용합니다.
* 컨테이너의 Blob 목록 새로 고칩니다.
* 파일을 업로드합니다.
* Blob을 삭제합니다. (Blob 컨테이너에서 파일을 삭제해도 기본 파일은 삭제되지 않습니다. 해당 Blob 컨테이너에서만 제거됩니다.)
* Blob을 엽니다.
* 로컬 컴퓨터에 Blob을 저장합니다.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Blob 컨테이너에 폴더 또는 하위 폴더를 만들려면

1. **클라우드 탐색기**에서 blob 컨테이너를 선택 합니다. 컨테이너 창에서 **Blob 업로드** 단추를 선택합니다.

1. **새 파일 업로드** 대화 상자에서 **찾아보기** 단추를 선택하여 업로드하려는 파일을 지정한 다음 **폴더(선택 사항)** 상자에 폴더 이름을 입력합니다.

   ![Blob 폴더에 파일 업로드하기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   동일한 절차를 수행하여 컨테이너 폴더에 하위 폴더를 추가할 수 있습니다. 폴더 이름을 지정하지 않으면 파일은 Blob 컨테이너의 최상위 수준으로 업로드됩니다. 파일은 컨테이너의 지정된 폴더에 나타납니다.

   ![Blob 컨테이너에 폴더 추가하기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. 폴더를 두 번 클릭하거나 Enter 키를 눌러 폴더의 콘텐츠를 확인합니다. 컨테이너의 폴더에 있는 경우 **부모 디렉터리 열기**(화살표) 단추를 선택하여 컨테이너의 루트로 다시 이동할 수 있습니다.

### <a name="to-delete-a-container-folder"></a>컨테이너 폴더를 삭제하려면

폴더에서 파일을 모두 삭제합니다.

Blob 컨테이너의 폴더는 가상 폴더이기 때문에 빈 폴더를 만들 수 없습니다. 또한 폴더를 삭제해도 해당 파일의 콘텐츠가 삭제되지 않지만, 폴더의 전체 콘텐츠를 삭제하면 폴더 자체가 삭제됩니다.

### <a name="to-filter-blobs-in-a-container"></a>컨테이너의 Blob를 필터링하려면

공통 접두사를 지정하여 표시되는 Blob를 필터링할 수 있습니다.

예를 들어 필터 텍스트 상자에 접두사 **hello**를 입력한 다음 **실행**(**!**) 단추를 선택하면 “hello”로 시작하는 Blob만 나타납니다.

![필터 텍스트 상자](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

필터 텍스트 상자는 대/소문자를 구분하며 와일드카드 문자 필터링을 지원하지 않습니다. Blob은 접두사로만 필터링될 수 있습니다. 구분 기호를 사용하여 가상 계층에 Blob을 구성하는 경우 접두사는 구분 기호를 포함할 수 있습니다. 예를 들어, “HelloFabric/” 접두사로 시작하는 필터링은 해당 문자열로 시작하는 모든 Blob을 반환합니다.

### <a name="to-download-blob-data"></a>Blob 데이터를 다운로드하려면

**클라우드 탐색기**에서 다음 방법 중 하나를 사용 합니다.

* 하나 이상의 Blob에 대한 바로 가기 메뉴를 연 다음 **열기**를 선택합니다.
* Blob 이름을 선택한 다음 **열기** 단추를 선택합니다.
* Blob 이름을 두 번 클릭합니다.

Blob 다운로드 진행률이 **Azure 활동 로그** 창에 표시됩니다.

Blob는 해당 파일 형식에 대한 기본 편집기에서 열립니다. 운영 체제가 파일 형식을 인식하는 경우 로컬에 설치된 애플리케이션에서 파일이 열립니다. 그렇지 않으면 Blob의 파일 형식에 적합한 애플리케이션을 선택하라는 메시지가 표시됩니다. Blob을 다운로드할 때 생성되는 로컬 파일은 읽기 전용으로 표시됩니다.

Blob 데이터는 로컬로 캐시되고 Azure Blob Storage에서 Blob의 마지막 수정된 시간에 대해 확인됩니다. Blob이 마지막으로 다운로드된 후 업데이트된 경우 다시 다운로드됩니다. 그렇지 않은 경우 Blob은 로컬 디스크에서 로드됩니다.

기본적으로 Blob은 임시 디렉터리에 다운로드됩니다. 특정 디렉터리에 Blob을 다운로드하려면 선택한 Blob 이름에 대한 바로 가기 메뉴를 열고 **다른 이름으로 저장**을 선택합니다. 이 방식으로 Blob을 저장하면 Blob 파일이 열리지 않으며, 로컬 파일이 읽기/쓰기 특성으로 생성됩니다.

### <a name="to-upload-blobs"></a>Blob을 업로드하려면

BLOB을 업로드하려면 BLOB 컨테이너 보기에서 볼 수 있도록 컨테이너가 열려 있는 동안 **BLOB 업로드** 단추를 선택합니다.

하나 이상의 파일을 선택해 업로드할 수 있으며 모든 형식의 파일을 업로드할 수 있습니다. **Azure 활동 로그** 창에 업로드 진행률이 표시됩니다. Blob 데이터 작업 방법에 대한 자세한 내용은 [.NET에서 Azure Blob Storage를 사용하는 방법](/azure/storage/blobs/storage-quickstart-blobs-dotnet)을 참조하세요.

### <a name="to-view-logs-transferred-to-blobs"></a>Blob에 전송된 로그를 보려면

Azure Diagnostics를 사용하여 Azure 애플리케이션에서 데이터를 기록하고 스토리지 계정에 로그를 전송하는 경우 이러한 로그에 대해 Azure에서 만들어진 컨테이너가 표시됩니다. 서버 탐색기에서 이러한 로그를 확인하는 것은 특히 Azure에 배포된 경우 애플리케이션에 대한 문제를 식별하는 쉬운 방법입니다.

Azure Diagnostics에 대한 자세한 내용은 [Azure Diagnostics를 사용하여 로깅 데이터 수집](/azure/cloud-services/cloud-services-dotnet-diagnostics)을 참조하세요.

### <a name="to-get-the-url-for-a-blob"></a>Blob에 대한 URL을 가져오려면

Blob의 바로 가기 메뉴를 열고 **URL 복사**를 선택합니다.

### <a name="to-edit-a-blob"></a>Blob을 편집하려면

Blob을 선택한 다음 **Blob 열기** 단추를 선택 합니다.

파일은 임시 위치로 다운로드되고 로컬 컴퓨터에서 열립니다. 변경한 후 BLOB을 다시 업로드합니다.

## <a name="work-with-queue-resources"></a>큐 리소스로 작업

스토리지 서비스 큐는 Azure Storage 계정에 호스트됩니다. 클라우드 서비스 역할이 메시지 전달 메커니즘에 의해 서로 및 다른 서비스와 통신할 수 있도록 사용할 수 있습니다. 클라우드 서비스 및 외부 클라이언트에 대한 웹 서비스를 통해 프로그래밍 방식으로 큐에 액세스할 수 있습니다. 또한 Visual Studio에서 서버 탐색기를 사용하여 직접 큐에 액세스할 수 있습니다.

큐를 사용하는 클라우드 서비스를 개발할 때 Visual Studio를 사용하여 큐를 생성하여 코드를 개발 및 테스트하는 동안 대화형으로 작업하는 것이 좋습니다.

서버 탐색기에서는 스토리지 계정의 큐 보기, 큐 생성 및 삭제, 큐를 열어 메시지 보기, 큐에 메시지 추가하기가 가능합니다. 큐를 확인하기 위해 열 때 개별 메시지를 볼 수 있으며 왼쪽 위 모서리의 단추를 사용하여 큐에서 다음의 작업을 수행할 수 있습니다.

* 큐 보기를 새로 고칩니다.
* 큐에 메시지 추가.
* 최상위 메시지를 큐에서 제거
* 전체 큐를 지웁니다.

다음 이미지에서는 두 개의 메시지를 포함하는 큐를 보여 줍니다.

![큐 보기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

스토리지 서비스 큐에 대한 자세한 내용은 [.NET을 사용하여 Azure Queue Storage 시작](/azure/storage/queues/storage-dotnet-how-to-use-queues)을 참조하세요. 스토리지 서비스 큐의 웹 서비스에 대한 자세한 내용은 [큐 서비스 개념](/rest/api/storageservices/Queue-Service-Concepts)을 참조하세요. Visual Studio를 사용하여 Storage 서비스 큐에 메시지를 보내는 방법에 대한 자세한 내용은 [Storage 서비스 큐에 메시지 보내기](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues)를 참조하세요.

> [!NOTE]
> 스토리지 서비스 큐는 Azure Service Bus 큐와 구별됩니다. Service Bus 큐에 대 한 자세한 내용은 [큐, 토픽 및 구독 Service Bus](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)을 참조 하세요.

## <a name="work-with-table-resources"></a>테이블 리소스로 작업

Azure Table Storage는 많은 양의 구조화된 데이터를 저장합니다. 이 서비스는 Azure 클라우드 내부 및 외부에서 인증된 호출을 수락하는 NoSQL 데이터 저장소입니다. Azure 테이블은 구조화된 비관계형 데이터를 저장하는 데 적합합니다.

### <a name="to-create-a-table"></a>테이블 형식 보고서를 만들려면

1. **클라우드 탐색기**에서 저장소 계정의 **테이블** 노드를 선택한 다음 **테이블 만들기**를 선택 합니다.
1. **테이블 만들기** 대화 상자에서 테이블의 이름을 입력합니다.

### <a name="to-view-table-data"></a>테이블 데이터를 보려면

1. **클라우드 탐색기**에서 **Azure** 노드를 연 다음 **저장소** 노드를 엽니다.
1. 관심 있는 스토리지 계정 노드를 연 다음 **테이블** 노드를 열어 스토리지 계정에 대한 테이블 목록을 확인합니다.
1. 테이블의 바로 가기 메뉴를 연 다음 **테이블 보기**를 선택합니다.

    ![솔루션 탐색기에 있는 Azure 테이블](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

테이블은 엔터티 (행에 표시) 및 속성 (열에 표시) 별로 구성됩니다. 예를 들어 다음 그림은 테이블 디자이너에 나열된 엔터티를 보여 줍니다.

### <a name="to-edit-table-data"></a>테이블 데이터를 편집하려면

**테이블 디자이너**에서 엔터티 (단일 행) 또는 속성 (단일 셀)에 대 한 바로 가기 메뉴를 연 다음 **편집**을 선택 합니다.

![테이블 엔터티 추가 또는 편집](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

단일 테이블의 엔터티는 속성 (열)과 동일한 집합을 가질 필요가 없습니다. 테이블 데이터 보기 및 편집에 대한 다음의 제한 사항에 유의하십시오.

* 이진 데이터(`type byte[]`)를 보거나 편집할 수 없지만 테이블에 저장할 수는 있습니다.
* Azure Table storage는 해당 작업을 지원 하지 않으므로 **PartitionKey** 또는 **rowkey** 값을 편집할 수 없습니다.
* **Timestamp**라는 속성을 만들 수 없습니다. Azure Storage 서비스는 해당 이름의 속성을 사용합니다.
* **DateTime** 값을 입력하는 경우 컴퓨터의 지역 및 언어 설정에 부합하는 형식을 따라야 합니다(예: 미국 영어의 경우 MM/DD/YYYY HH:MM:SS [AM|PM]).

### <a name="to-add-entities"></a>엔터티를 추가하려면

1. **테이블 디자이너**에서 **엔터티 추가** 단추를 선택 합니다.

    ![엔터티 추가 단추](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. **엔터티 추가** 대화 상자에서 **PartitionKey** 및 **RowKey** 속성 값을 입력합니다.

    ![엔터티 추가 대화 상자](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    신중하게 값을 입력합니다. 엔터티를 삭제하고 다시 추가하지 않는 한 대화 상자를 닫은 후에는 값을 변경할 수 없습니다.

### <a name="to-filter-entities"></a>엔터티를 필터링하려면

쿼리 작성기를 사용하는 경우 테이블에 표시되는 엔터티 집합을 사용자 지정할 수 있습니다.

1. 쿼리 작성기를 열려면 테이블을 열어 확인합니다.
1. 테이블 보기의 도구 모음에서 **쿼리 작성기** 단추를 선택합니다.

    그러면 **쿼리 작성기** 대화 상자가 나타납니다. 다음 그림에서는 쿼리 작성기에서 작성되고 있는 쿼리를 보여줍니다.

    ![쿼리 작성기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. 쿼리 작성을 마친 경우 대화 상자를 닫습니다. 쿼리의 결과 텍스트 형식이 WCF Data Services 필터로 텍스트 상자에 나타납니다.
1. 쿼리를 실행하려면 녹색 삼각형 아이콘을 선택합니다.

또한 필터 텍스트 상자에 WCF Data Services 필터 문자열을 직접 입력한 경우 테이블 디자이너에 표시되는 엔터티 데이터를 필터링할 수 있습니다. 이러한 종류의 문자열은 SQL WHERE 절과 유사하지만 HTTP 요청으로 서버에 전송됩니다. 필터 문자열을 생성 하는 방법에 대 한 자세한 내용은 [테이블 디자이너에 대 한 필터 문자열 생성](vs-azure-tools-table-designer-construct-filter-strings.md)을 참조 하세요.

다음 그림에서는 유효한 필터 문자열의 예를 보여줍니다.

![필터 문자열](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>스토리지 데이터 새로 고침

서버 탐색기에서 연결하거나 스토리지 계정에서 데이터를 가져올 때 작업을 완료하기까지 최대 1분이 소요될 수 있습니다. 서버 탐색기 연결할 수 없는 경우 작업 시간이 초과 될 수 있습니다. 데이터를 검색 하는 동안 Visual Studio의 다른 부분에서 작업을 계속할 수 있습니다. 시간이 너무 오래 걸려서 작업을 취소하려면 서버 탐색기 도구 모음에서 **새로 고침 중지** 단추를 선택합니다.

### <a name="to-refresh-blob-container-data"></a>Blob 컨테이너 데이터를 새로 고치려면

* **스토리지** 아래의 **Blob** 노드를 선택하고 서버 탐색기 도구 모음에서 **새로 고침** 단추를 선택합니다.
* 표시된 Blob 목록을 새로 고치려면 **실행** 단추를 선택합니다.

### <a name="to-refresh-table-data"></a>테이블 데이터를 새로 고치려면

* **스토리지** 아래의 **테이블** 노드를 선택하고 서버 탐색기 도구 모음에서 **새로 고침** 단추를 선택합니다.
* **테이블 디자이너**에 표시 된 엔터티 목록을 새로 고치려면 테이블 디자이너에서 **실행** 단추를 선택 합니다.

### <a name="to-refresh-queue-data"></a>큐 데이터를 새로 고치려면

**스토리지** 아래의 **큐** 노드를 선택하고 서버 탐색기 도구 모음에서 **새로 고침** 단추를 선택합니다.

### <a name="to-refresh-all-items-in-a-storage-account"></a>스토리지 계정의 모든 항목을 새로 고치려면

계정 이름을 선택하고 서버 탐색기 도구 모음에서 **새로 고침** 단추를 선택합니다.

## <a name="add-storage-accounts-by-using-server-explorer"></a>서버 탐색기를 사용하여 스토리지 계정 추가

서버 탐색기를 사용하여 스토리지 계정을 추가하는 방법은 두 가지가 있습니다. Azure 구독에서 스토리지 계정을 만들거나 기존 스토리지 계정을 연결할 수 있습니다.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>서버 탐색기를 사용하여 스토리지 계정을 만들려면 다음을 수행합니다.

1. 서버 탐색기에서 **스토리지** 노드에 대한 바로 가기 메뉴를 연 다음 **스토리지 계정 만들기**를 선택합니다.

1. **스토리지 계정 만들기** 대화 상자에서 다음 정보를 선택하거나 입력합니다.

   * 스토리지 계정을 추가할 Azure 구독입니다.
   * 새 스토리지 계정에 대해 사용하려는 이름입니다.
   * 지역 또는 선호도 그룹 (예: 미국 서부 또는 동아시아)입니다.
   * 스토리지 계정에 대해 사용하려는 복제의 유형입니다(예: 지역 중복).

   ![Azure Storage 계정 만들기](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **만들기**를 선택합니다.

솔루션 탐색기의 **스토리지** 목록에 새 Storage 계정이 나타납니다.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>서버 탐색기를 사용하여 기존 스토리지 계정을 연결하려면

1. 서버 탐색기에서 Azure **스토리지** 노드에 대한 바로 가기 메뉴를 연 다음 **외부 스토리지 연결**을 선택합니다.

    ![기존 스토리지 계정 추가](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. **스토리지 계정 만들기** 대화 상자에서 다음 정보를 선택하거나 입력합니다.

   * 연결하려는 기존 스토리지 계정의 이름입니다.
   * 선택한 스토리지 계정에 대한 키입니다. 스토리지 계정을 선택할 때 일반적으로 이 값이 제공됩니다. Visual Studio가 스토리지 계정 키를 기억하기를 원하는 경우 **계정 키 기억하기** 확인란을 선택합니다.
   * 스토리지 계정에 연결하기 위해 사용하는 프로토콜입니다 - 예: HTTP, HTTPS, 또는 사용자 지정 엔드포인트. 사용자 지정 엔드포인트에 대한 자세한 내용은 [연결 문자열을 구성하는 방법](/azure/storage/common/storage-configure-connection-string)을 참조하세요.

### <a name="to-view-the-secondary-endpoints"></a>보조 엔드포인트를 확인하려면

**읽기 액세스 지역 중복** 복제 옵션을 사용하여 스토리지 계정을 만든 경우 계정 이름의 바로 가기 메뉴를 열고 **속성**을 선택하면 보조 엔드포인트를 볼 수 있습니다.

![스토리지 보조 엔드포인트](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>서버 탐색기에서 스토리지 계정을 제거하려면

서버 탐색기에서 계정 이름에 대한 바로 가기 메뉴를 연 다음 **삭제**를 선택합니다.

스토리지 계정을 삭제하면 해당 계정에 저장된 키 정보도 제거됩니다.

서버 탐색기에서 스토리지 계정을 삭제하면 스토리지 계정이나 그 안에 포함된 데이터에는 영향을 주지 않습니다. 단순히 서버 탐색기의 참조를 제거합니다. 스토리지 계정을 영구적으로 삭제하려면 [Azure Portal](https://portal.azure.com/)을 사용하세요.

## <a name="next-steps"></a>다음 단계

Azure Storage 서비스를 사용하는 방법에 대해 자세히 알아보려면 [Azure Storage 서비스 액세스](/azure/storage/common/storage-introduction)를 참조하세요.
