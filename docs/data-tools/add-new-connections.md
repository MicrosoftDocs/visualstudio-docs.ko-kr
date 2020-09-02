---
title: 새 연결 추가
ms.date: 11/04/2016
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f6f34c28a6bbba236a4d90e2f936fad0b2a3f60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283062"
---
# <a name="add-new-connections"></a>새 연결 추가

데이터베이스 또는 서비스에 대 한 연결을 테스트 하 고 **서버 탐색기**, **클라우드 탐색기**또는 **SQL Server 개체 탐색기**를 사용 하 여 데이터베이스 내용과 스키마를 탐색할 수 있습니다. 이러한 창의 기능은 일부 범위에 겹칩니다. 기본 차이점은 다음과 같습니다.

- 서버 탐색기

   기본적으로 Visual Studio에 설치 됩니다. 를 사용 하 여 연결을 테스트 하 고 SQL Server 데이터베이스, ADO.NET 공급자가 설치 된 다른 데이터베이스 및 일부 Azure 서비스를 볼 수 있습니다. 시스템 성능 카운터, 이벤트 로그 및 메시지 큐와 같은 하위 수준 개체도 보여 줍니다. 데이터 원본에 ADO.NET 공급자가 없으면 여기에 표시 되지 않지만 프로그래밍 방식으로 연결 하 여 Visual Studio에서 사용할 수 있습니다.

- 클라우드 탐색기

   [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.CloudExplorerForVS)에서 Visual Studio 확장으로이 창을 수동으로 설치 합니다. 는 Azure 서비스를 탐색 하 고 연결 하기 위한 특수 기능을 제공 합니다.

- SQL Server 개체 탐색기

   SQL Server Data Tools와 함께 설치 되 고 **보기** 메뉴 아래에 표시 됩니다. 표시 되지 않으면 제어판의 **프로그램 및 기능** 으로 이동 하 여 Visual Studio를 찾은 다음 **변경** 을 선택 하 여 SQL Server Data Tools에 대 한 확인란을 선택한 후 설치 관리자를 다시 실행 합니다. **SQL Server 개체 탐색기** 를 사용 하 여 SQL 데이터베이스 (ADO.NET 공급자가 있는 경우)를 보고, 새 데이터베이스를 만들고, 스키마를 수정 하 고, 저장 프로시저를 만들고, 연결 문자열을 검색 하 고, 데이터를 볼 수 있습니다. ADO.NET 공급자가 설치 되지 않은 SQL 데이터베이스는 여기에 표시 되지 않지만 프로그래밍 방식으로 연결할 수 있습니다.

## <a name="add-a-connection-in-server-explorer"></a>서버 탐색기에서 연결 추가

데이터베이스에 대 한 연결을 만들려면 **서버 탐색기**에서 **연결 추가** 아이콘을 클릭 하거나 **데이터 연결** 노드에서 **서버 탐색기** 을 마우스 오른쪽 단추로 클릭 하 고 **연결 추가**를 선택 합니다. 여기에서 다른 서버, SharePoint 서비스 또는 Azure 서비스의 데이터베이스에 연결할 수도 있습니다.

![서버 탐색기 새 연결 아이콘](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

그러면 **연결 추가** 대화 상자가 나타납니다. 여기에서 SQL Server LocalDB 인스턴스의 이름을 입력 했습니다.

![새 연결 추가](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>공급자 변경

데이터 원본이 원하는 항목이 아닌 경우 **변경** 단추를 클릭 하 여 새 데이터 원본 및/또는 새 ADO.NET 데이터 공급자를 선택 합니다. 새 공급자는 구성 된 방법에 따라 자격 증명을 요청할 수 있습니다.

![AD0.NET Data Provider 변경](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>연결 테스트

데이터 원본을 선택한 후 **연결 테스트**를 클릭 합니다. 성공 하지 못하면 공급 업체의 설명서에 따라 문제를 해결 해야 합니다.

![연결을 테스트](../data-tools/media/raddata-test-connection.png)

테스트에 성공 하면 기본 데이터베이스 또는 서비스를 기반으로 하는 *데이터 모델* 을 의미 하는 Visual Studio 용어 인 *데이터 소스*를 만들 준비가 된 것입니다.

## <a name="see-also"></a>추가 정보

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
