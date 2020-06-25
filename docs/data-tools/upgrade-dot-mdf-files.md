---
title: .mdf 파일 업그레이드
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d35611dcc7b6067cf6d6166aff521ef291b8dfcd
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281125"
---
# <a name="upgrade-mdf-files"></a>.mdf 파일 업그레이드

이 항목에서는 새 버전의 Visual Studio를 설치한 후 데이터베이스 파일 (*.mdf*)을 업그레이드 하기 위한 옵션에 대해 설명 합니다. 여기에는 다음 태스크에 대 한 지침이 포함 됩니다.

- 최신 버전의 SQL Server Express LocalDB를 사용 하도록 데이터베이스 파일 업그레이드

- 최신 버전의 SQL Server Express을 사용 하도록 데이터베이스 파일 업그레이드

- Visual Studio에서 데이터베이스 파일에 대 한 작업을 수행 하지만 이전 버전의 SQL Server Express 또는 LocalDB와의 호환성을 유지 합니다.

- 기본 데이터베이스 엔진 SQL Server Express 설정

Visual Studio를 사용 하 여 이전 버전의 SQL Server Express 또는 LocalDB를 사용 하 여 만든 데이터베이스 파일 (*.mdf*)을 포함 하는 프로젝트를 열 수 있습니다. 그러나 Visual Studio에서 프로젝트를 계속 개발 하려면 해당 버전의 SQL Server Express 또는 LocalDB가 Visual Studio와 같은 컴퓨터에 설치 되어 있거나 데이터베이스 파일을 업그레이드 해야 합니다. 데이터베이스 파일을 업그레이드 하는 경우 이전 버전의 SQL Server Express 또는 LocalDB를 사용 하 여 액세스할 수 없습니다.

이전 버전의 SQL Server Express 또는 LocalDB를 통해 만든 데이터베이스 파일의 버전이 현재 설치 되어 있는 SQL Server Express 또는 LocalDB의 인스턴스와 호환 되지 않는 경우 해당 데이터베이스 파일을 업그레이드 하 라는 메시지가 표시 될 수도 있습니다. 이 문제를 해결 하기 위해 Visual Studio에서 파일을 업그레이드할지 묻는 메시지를 표시 합니다.

> [!IMPORTANT]
> 데이터베이스 파일을 업그레이드 하기 전에 백업 하는 것이 좋습니다.

> [!WARNING]
> LocalDB 2014 (V12) 32 비트에서 LocalDB 2016 (V13) 이상으로 만든 *.mdf* 파일을 업그레이드 하는 경우에는 버전의 localdb 32에서 다시 파일을 열 수 없습니다.

데이터베이스를 업그레이드 하기 전에 다음 조건을 고려 합니다.

- 이전 버전 및 최신 버전의 Visual Studio에서 프로젝트를 사용 하려면 업그레이드 하지 마세요.

- 응용 프로그램이 LocalDB 대신 SQL Server Express를 사용 하는 환경에서 사용 되는 경우 업그레이드 하지 마세요.

- 응용 프로그램에서 원격 연결을 사용 하는 경우에는 LocalDB에서 해당 연결을 허용 하지 않으므로 업그레이드 하지 마십시오.

- 응용 프로그램이 인터넷 정보 서비스 (IIS)를 사용 하는 경우 업그레이드 하지 않습니다.

- 샌드박스 환경에서 데이터베이스 응용 프로그램을 테스트 하지만 데이터베이스를 관리 하지 않으려는 경우 업그레이드 하는 것이 좋습니다.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>LocalDB 버전을 사용 하도록 데이터베이스 파일을 업그레이드 하려면

1. **서버 탐색기**에서 **데이터베이스에 연결** 단추를 선택 합니다.

2. **연결 추가** 대화 상자에서 다음 정보를 지정 합니다.

    - **데이터 원본**:`Microsoft SQL Server (SqlClient)`

    - **서버 이름**:

        - 기본 버전을 사용 하려면를 사용 `(localdb)\MSSQLLocalDB` 합니다.  설치 된 Visual Studio 버전 및 첫 번째 LocalDB 인스턴스를 만든 시간에 따라 ProjectV12 또는 ProjectV13를 지정 합니다. **SQL Server 개체 탐색기** 의 **MSSQLLocalDB** 노드에는 가리키는 버전이 표시 됩니다.

        - 특정 버전을 사용 하려면 또는를 사용 합니다. `(localdb)\ProjectsV12` `(localdb)\ProjectsV13` 여기서 V12은 localdb 2014이 고 V13는 localdb 2016입니다.

    - **데이터베이스 파일 연결**: 기본 *.mdf* 파일의 실제 경로입니다.

    - **논리적 이름**: 파일을 사용 하려는 이름입니다.

3. **확인** 단추를 선택합니다.

4. 메시지가 표시 되 면 **예** 단추를 선택 하 여 파일을 업그레이드 합니다.

    데이터베이스가 업그레이드 되 고 LocalDB 데이터베이스 엔진에 연결 되며 이전 버전의 LocalDB와 더 이상 호환 되지 않습니다.

연결에 대 한 바로 가기 메뉴를 열고 **연결 수정**을 선택 하 여 LocalDB를 사용 하도록 SQL Server Express 연결을 수정할 수도 있습니다. **연결 수정** 대화 상자에서 서버 이름을로 변경 `(LocalDB)\MSSQLLocalDB` 합니다. **고급 속성** 대화 상자에서 **사용자 인스턴스가** **False**로 설정 되어 있는지 확인 합니다.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>SQL Server Express 버전을 사용 하도록 데이터베이스 파일을 업그레이드 하려면

1. 데이터베이스에 대 한 연결에 대 한 바로 가기 메뉴에서 **연결 수정**을 선택 합니다.

2. **연결 수정** 대화 상자에서 **고급** 단추를 선택 합니다.

3. **고급 속성** 대화 상자에서 서버 이름을 변경 하지 않고 **확인** 단추를 선택 합니다.

    데이터베이스 파일은 SQL Server Express 현재 버전과 일치 하도록 업그레이드 됩니다.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio에서 데이터베이스를 사용 하지만 SQL Server Express와의 호환성을 유지 하려면

- Visual Studio에서 프로젝트를 업그레이드 하지 않고 엽니다.

  - 프로젝트를 실행 하려면 **F5** 키를 선택 합니다.

  - 데이터베이스를 편집 하려면 **솔루션 탐색기**에서 *.mdf* 파일을 열고 **서버 탐색기** 에서 노드를 확장 하 여 데이터베이스 작업을 수행 합니다.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>기본 데이터베이스 엔진 SQL Server Express 만들려면

1. 메뉴 모음에서 **도구**  >  **옵션**을 선택 합니다.

2. **옵션** 대화 상자에서 **데이터베이스 도구** 옵션을 확장 한 다음 **데이터 연결**을 선택 합니다.

3. **SQL Server 인스턴스 이름** 입력란에 사용 하려는 SQL Server Express 또는 LocalDB 인스턴스의 이름을 지정 합니다. 인스턴스에 이름이 지정 되지 않은 경우를 지정 `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` 합니다.

4. **확인** 단추를 선택합니다.

    SQL Server Express는 응용 프로그램에 대 한 기본 데이터베이스 엔진입니다.

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터 액세스](accessing-data-in-visual-studio.md)
