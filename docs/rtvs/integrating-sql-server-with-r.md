---
title: SQL Server와 R 통합
description: Visual Studio는 R에서 SQL 쿼리를 만들고 실행하는 기능과 R을 통해 저장 프로시저를 사용하는 기능을 지원합니다.
ms.date: 06/25/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 10b5dfee629b5b6e67ab544ca0bdd905ed2a120a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72888450"
---
# <a name="work-with-sql-server-and-r"></a>SQL Server 및 R 사용

Visual Studio의 뛰어난 SQL Server 지원은 SQL 쿼리를 생성 및 실행하고 저장 프로시저를 사용하는 기능을 통해 데이터 과학자의 R 및 SQL 데이터베이스 작업에 도움을 줍니다.

> [!Note]
> SQL 및 R을 함께 사용하려면 SQL Server Data Tools가 설치되어 있어야 합니다.
> - Visual Studio 2017: Visual Studio 설치 관리자를 실행하고 데이터 스토리지와 처리 워크로드를 선택합니다(SQL Server Data Tools 포함).
> - Visual Studio 2015: [Download SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)(SQL Server Data Tools 다운로드)의 지침을 따릅니다.

|   |   |
|---|---|
| ![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 시청") | SQL Server 및 R의 개요에 대한 [동영상(youtube.com)을 시청](https://www.youtube.com/watch?v=n4AYr0QIwdQ)하세요(3분 03초). |

## <a name="create-and-run-sql-queries"></a>SQL 쿼리 만들기 및 실행

RTVS에서는 R 제품에 SQL 쿼리를 추가하는 기능을 지원하므로 찾고 있는 결과를 얻을 때까지 별도의 컨텍스트에서 SQL 쿼리를 반복해서 개발할 수 있습니다.

SQL 쿼리 파일을 추가하려면 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고, **추가** > **새 항목**을 선택하고, **SQL 쿼리** 파일 형식을 선택합니다.

![프로젝트에 SQL 쿼리 항목 추가](media/sql-add-item.png)

이 명령을 수행하면 전체 SQL용 IntelliSense 및 쿼리 실행 기능을 제공하는 Visual Studio의 Transact-SQL 편집기에서 파일이 열립니다. 이러한 기능이 작동하려면 편집기 도구 모음에서 연결 단추를 사용하거나 간단히 쿼리를 실행하여(**Ctrl**+**Shift**+**E**, 선택에서도 작동함) 데이터베이스에 연결해야 합니다. 어느 방법을 사용해도 연결 대화 상자가 표시됩니다.

![SQL 연결 대화 상자](media/sql-connection-dialog.png)

연결이 설정되면 쿼리를 실행하고 결과를 확인할 수 있습니다.

![SQL 창 쿼리 결과](media/sql-query-results.png)

Transact-SQL 편집기에서는 쿼리에 대한 실행 계획 보기, 쿼리 디버거와 같은 다양한 기타 기능을 지원합니다.
자세한 내용은 [Transact-SQL 편집기를 사용하여 스크립트 편집 및 실행](https://msdn.microsoft.com/library/hh272706.aspx)을 참조하세요.

## <a name="work-with-sql-server-stored-procedures"></a>SQL Server 저장 프로시저 작업

[SQL Server R Services](/sql/advanced-analytics/r/sql-server-r-services)(SQL Server 2016 이상)를 사용하여 T-SQL 저장 프로시저의 R 코드를 포함하고 실행할 수 있습니다. SQL Server 컴퓨터에서 R 코드를 실행하고, SQL 쿼리에서 반환된 데이터에 대해 작업을 수행하고, 추가 SQL에 의해 처리되거나 클라이언트로 반환될 수 있는 SQL 결과 집합을 생성할 수 있습니다.

RTVS는 다음 섹션의 설명대로 SQL 및 R 코드를 단일 SQL 문으로 결합하는 불편하고 오류가 발생할 수 있는 프로세스를 간소화합니다.

- [데이터베이스 연결 추가](#add-a-database-connection)
- [SQL 저장 프로시저 작성 및 테스트](#write-and-test-a-sql-stored-procedure)
- [SQL 저장 프로시저 게시](#publish-a-sql-stored-procedure)

|   |   |
|---|---|
| ![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 시청") | R 및 SQL 저장 프로시저의 개요에 대한 [동영상(youtube.com)을 시청](https://www.youtube.com/watch?v=dFKIT2OitWQ)하세요(6분 09초). |

### <a name="add-a-database-connection"></a>데이터베이스 연결 추가

1. **R 도구** > **데이터** > **데이터베이스** 연결 추가를 선택하여 **연결 속성** 대화 상자를 표시합니다. 여기서 데이터 원본(이 경우 SQL Server)의 이름, 서버 이름, 인증 모드 및 데이터베이스 이름을 지정합니다. 대화 상자를 닫기 전에 **연결 테스트**를 선택하여 입력을 확인합니다.

    ![SQL 연결 대화 상자](media/sql-connection-string-dialog.png)

1. 올바른 연결과 함께 **확인**을 선택하면 새 *settings.R* 파일에 `dbConnection`이라는 연결 문자열이 생성됩니다. RTVS에서 이 파일이 자동으로 제공(실행)되므로 R 스크립트에서 연결을 즉시 사용할 수 있습니다.

![SQL Settings.R 파일](media/sql-settings-dot-r.png)

### <a name="write-and-test-a-sql-stored-procedure"></a>SQL 저장 프로시저 작성 및 테스트

새 SQL 저장 프로시저를 추가하려면 **추가** > **새 항목**을 선택하고, 템플릿 목록에서 **SQL 저장 프로시저(R 사용)** 를 선택하고, 파일 이름을 입력하고, **확인**을 클릭합니다. 기본 파일 이름은 읽기 쉽도록 *SqlSProc.R*이며, 이 섹션의 나머지 부분에서는 파일 이름 *StoredProcedure.R*이 사용됩니다. 여러 저장 프로시저가 있는 경우 각 파일마다 고유한 파일 이름이 있어야 합니다.

RTVS는 R 코드용 *.R* 파일, SQL 코드용 *.Query.sql* 파일, 두 파일을 결합하는 *.Template.sql* 파일 등 저장 프로시저용 파일 3개를 만듭니다. 뒤의 두 파일은 솔루션 탐색기에 *.R* 파일의 자식으로 표시됩니다.

![SQL 저장 프로시저(R 사용)의 솔루션 탐색기 확장 보기](media/sql-solution-explorer-expanded.png)

*.R* 파일(*StoredProcedure.R* 이 예제)은 R 코드를 작성하는 곳입니다. 기본 콘텐츠는 다음과 같습니다.

```R
# @InputDataSet: input data frame, result of SQL query execution
# @OutputDataSet: data frame to pass back to SQL

# Test code
# library(RODBC)
# channel <- odbcDriverConnect(dbConnection)
# InputDataSet <- sqlQuery(channel, )
# odbcClose(channel)

OutputDataSet <- InputDataSet
```

간단히 말하면 코드는 `InputDataSet`라는 R 데이터 프레임을 수신하고 입력을 출력으로 복사하는 템플릿 코드와 함께 `OutputDataSet`에 결과를 반환합니다.

> [!Note]
> 이러한 데이터 프레임의 이름은 `sp_execute_external_script` 시스템 저장 프로시저 호출에서 `@input_data_1_name` 및 `@output_data_1_name` 매개 변수에 의해 제어됩니다. 이 호출 규칙의 디자인에 대한 자세한 내용과 일부 사용 예제는 [sp_execute_external_script(Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)를 참조하세요.

주석의 다른 생성된 코드는 [RODBC 패키지](https://cran.r-project.org/web/packages/RODBC/index.html)를 사용하여 SQL 문을 SQL Server로 전송하고, 문을 실행하고, 해당 결과 집합을 R 데이터 프레임으로 검색하는 작은 테스트 스크립트를 제공합니다. 이 테스트 코드의 주석 처리를 제거하면 SQL Server에서 얻는 결과 집합을 대상으로 R 코드를 대화형으로 작성할 수 있습니다.

*Query.sql* 파일(이 예제의 *StoredProcedure.Query.sql*)은 `InputDataSet`에 대한 데이터를 생성하는 SQL 쿼리를 작성하고 테스트하는 곳입니다. 이 *.sql* 파일을 사용하면 편집기에서 일반적인 Transact-SQL 기능을 모두 제공합니다.

SQL 코드에 만족할 경우 *.sql* 파일을 *.R* 파일에 대해 열린 편집기로 끌어서 사용자 R 코드와 통합합니다. 아래 이미지에서 *StoredProcedure.Query.sql*을 `sqlQuery(channel, )`의 쉼표 뒤에 *StoredProcedure.R*의 지점으로 끌어 왔습니다.

![SQL 파일을 R 문자열 값으로 읽기](media/sql-reference-sql-file-from-r.png)

여기에서 볼 수 있듯이 이 간단한 단계에서는 자동으로 R 코드를 생성하여 *.sql* 파일을 열고, 콘텐츠를 문자열로 읽고, 문자열을 RODBC 패키지에 전달하여 SQL Server로 보냅니다.

이제 필요에 따라 `InputDataSet` 데이터 프레임을 조작하는 R 코드를 대화형으로 작성할 수 있습니다. 편집기에서 R 코드를 선택하고 **Ctrl**+**Enter**를 눌러 [대화형 창](interactive-repl-for-r-in-visual-studio.md)으로 보낼 수도 있습니다.

*Template.sql* 파일(이 예제의 *StoredProcedure.Template.sql*)에는 마지막으로 SQL 저장 프로시저를 생성하기 위한 템플릿이 포함되어 있습니다.

```sql
CREATE PROCEDURE [StoredProcedure]
AS
BEGIN
EXEC sp_execute_external_script @language = N'R'
    , @script = N'_RCODE_'
    , @input_data_1 = N'_INPUT_QUERY_'
--- Edit this line to handle the output data frame.
    WITH RESULT SETS (([MYNEWCOLUMN] NVARCHAR(max)));
END;
```

- `_RCODE_` 자리 표시자는 *.R* 파일의 내용으로 바뀝니다(예: *StoredProcedure.R*).
- `_INPUT_QUERY_` 자리 표시자는 *Query.sql* 파일의 내용으로 바뀝니다(예: *StoredProcedure.Query.sql*).
- `WITH RESULT SETS` 절을 편집하여 저장 프로시저에서 반환된 결과 집합의 스키마를 설명합니다. 저장 프로시저의 호출자로 반환할 열을 `OutputDataSet` 데이터 프레임에서 구체적으로 식별합니다.

예를 들어 다음 쿼리를 살펴봅니다.

```sql
SELECT TOP 100 medallion, hack_license FROM nyctaxi_sample
```

다음 `WITH RESULT SETS` 절을 사용하여 반환 값의 데이터 형식을 지정합니다.

```sql
WITH RESULT SETS ((medallion NVARCHAR(max), hack_license NVARCHAR(max)));
```

### <a name="publish-a-sql-stored-procedure"></a>SQL 저장 프로시저 게시

1. **R 도구** > **데이터** > **옵션과 함께 게시** 메뉴 명령을 선택합니다.
1. 표시된 대화 상자에서 **게시 위치:** 를 **데이터베이스**로 변경하고, 대상을 지정하고, **게시**를 선택하면 RTVS가 저장 프로시저를 빌드하고 게시합니다.

    ![저장 프로시저 게시 대화 상자](media/sql-publish-with-options.png)

1. 프로젝트에 모든 저장 프로시저를 게시하는 데는 **R 도구** > **데이터** > **저장 프로시저 게시** 명령을 사용할 수 있습니다. 이 명령은 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭할 때도 제공됩니다.

> [!Tip]
> SQL Server 개체 탐색기가 Visual Studio에서 열린 경우 데이터베이스의 **프로그래밍 기능** > **저장 프로시저** 폴더에 게시한 저장 프로시저가 표시됩니다. **프로시저 실행**을 마우스 오른쪽 단추로 클릭하고 선택하거나 *.sql*쿼리 창에서 대화형으로 호출하여 개체 탐색기에서 실행할 수도 있습니다.
