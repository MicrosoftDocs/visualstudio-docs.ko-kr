---
title: 예제 데이터베이스 SQL Server 설치 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299632"
---
# <a name="install-sql-server-sample-databases"></a>SQL Server 샘플 데이터베이스 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예제 데이터베이스는 SQL 및 LINQ 쿼리, 데이터 바인딩, Entity Framework 모델링 등을 시험 하는 데 유용 합니다.  각 데이터베이스 제품에는 자체 예제 데이터베이스가 있습니다. Northwind 및 AdventureWorks는 널리 사용 되는 두 SQL Server 예제 데이터베이스입니다.

 **AdventureWorks** 는 SQL Server 제품에 대해 제공 되는 현재 예제 데이터베이스입니다. [Codeplex의 AdventureWorks 페이지](https://archive.codeplex.com/?p=msftdbprodsamples)에서 .mdf 파일로 다운로드할 수 있습니다. 여기에서 사용할 수 있는 일반 및 경량 (LT) 버전의 데이터베이스가 있습니다. 대부분의 시나리오에서는 더 복잡 하지 않기 때문에 LT 버전을 선호 합니다.

 **Northwind** 는 여러 해 동안 사용 된 비교적 간단한 SQL Server 데이터베이스입니다. [CodePlex의 Northwind 데이터베이스 페이지](https://northwinddatabase.codeplex.com/)에서 .bak 파일로 다운로드할 수 있습니다. 권한 문제를 방지 하려면 파일의 압축을 사용자 폴더 아래에 없는 새 폴더로 압축을 풉니다.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Visual Studio에서 .bak 파일의 데이터베이스를 복원 하려면

1. Microsoft SQL Server 데이터베이스를 백업 하면 .bak 파일이 생성 됩니다. .Bak 파일을 데이터베이스 파일로 다시 사용할 수 있도록 하려면이 파일을 *복원*해야 합니다. 주 메뉴에서 **보기**  >  **SQL Server 개체 탐색기**를 선택 합니다. 표시 되지 않으면 설치 해야 할 수 있습니다. **제어판**  >  **프로그램 및 기능**으로 이동 하 Microsoft Visual Studio 2015를 찾고 **변경** 단추를 클릭 합니다. 설치 된 구성 요소 목록이 설치 관리자 창에 표시 되 면 **SQL Server 개체 탐색기** 확인란을 선택 하 고 설치를 계속 합니다.

2. SQL Server 개체 탐색기에서 SQL Server 데이터베이스 엔진 (예: localdb)을 마우스 오른쪽 단추로 클릭 하 고**새 쿼리**를 선택 합니다.

     ![새 쿼리 SQL Server 개체 탐색기](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server 개체 탐색기 새 쿼리")

3. 먼저 .bak 파일 내에 데이터베이스 및 로그 파일의 논리적 이름이 필요 합니다. 이를 가져오려면 SQL 쿼리 편집기에이 쿼리를 입력 한 다음 창의 맨 위에 있는 녹색 **실행** 단추를 선택 합니다. 필요한 경우 .bak 파일을 가리키도록 파일 경로를 수정 합니다.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     결과 창에 나타나는 논리적 이름을 적어 씁니다.  Northwind 데이터베이스의 경우 두 개의 논리적 이름이 Northwind이 고 Northwind_log입니다.

4. 이제이 쿼리를 실행 하 여 데이터베이스를 만듭니다. 자신의 원본 및 대상 경로, 논리적 데이터베이스 이름 및 Northwind의 물리적 파일 이름을 적절 하 게 대체 합니다. .Mdf 및 .ldf 파일 확장명을 유지 합니다.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. SQL Server 개체 탐색기에서 **데이터베이스** 노드를 마우스 오른쪽 단추로 클릭 하면 Northwind 데이터베이스 노드가 표시 됩니다. 그렇지 않은 경우 데이터베이스를 마우스 오른쪽 단추로 클릭 하 고 **새 데이터베이스 추가**를 선택 합니다. 방금 만든 .mdf 파일의 이름과 위치를 입력 합니다.

6. 이제 Visual Studio에서 데이터베이스를 데이터 원본으로 사용할 수 있습니다.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>SQL Server Management Studio .bak 파일에서 데이터베이스를 복원 하려면

1. 다운로드 사이트에서 SQL Server Management Studio을 다운로드 합니다.

2. SSMS **개체 탐색기** 창에서 **데이터베이스** 노드를 마우스 오른쪽 단추로 클릭 하 고**데이터베이스 복원**을 선택 하 고 .bak 파일의 위치를 제공 합니다.

     ![SSMS 복원 데이터베이스](../data-tools/media/raddata-ssms-restore-database.png "raddata SSMS 복원 데이터베이스")
