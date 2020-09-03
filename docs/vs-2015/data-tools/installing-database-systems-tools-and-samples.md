---
title: 데이터베이스 시스템, 도구 및 샘플 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299600"
---
# <a name="installing-database-systems-tools-and-samples"></a>데이터베이스 시스템, 도구 및 샘플 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 자체에는 내부적으로 사용 하는 데이터베이스가 아닌 다른 데이터베이스 시스템은 포함 되지 않습니다. Visual Studio에서 데이터 연결 응용 프로그램을 개발 하려면 일반적으로 로컬 개발 컴퓨터에 데이터베이스 시스템을 설치한 다음 준비가 되 면 프로덕션 환경에 응용 프로그램 및 데이터베이스를 배포 합니다. .NET 응용 프로그램에서 데이터베이스 시스템에 액세스할 수 있고 Visual Studio data tools 창에 표시 하려면 ADO.NET 데이터 공급자가 있어야 합니다. 공급자는 .NET 응용 프로그램에서 엔터티 데이터 모델을 사용 하려는 경우 Entity Framework를 구체적으로 지원 해야 합니다.     대부분의 공급자는 NuGet 패키지 관리자를 통해 또는 Visual Studio 갤러리를 통해 제공 됩니다.

 SQL 개발의 경우 Visual Studio에 SQL Server Data Tools 설치 되어 있는지 확인 합니다. **보기** 메뉴를 클릭 합니다. SQL Server 개체 탐색기 표시 되지 않으면 제어판으로 이동 하 여 Visual Studio를 변경 합니다. 설치 관리자에서 **Microsoft SQL Server Data Tools**를 선택 합니다.

 Azure Storage Api를 사용 하는 경우 프로덕션 환경에 배포할 준비가 될 때까지 요금을 방지 하기 위해 개발 중에 로컬 컴퓨터에 Azure Storage 에뮬레이터를 설치 합니다. 자세한 내용은 [개발 및 테스트에 Azure Storage 에뮬레이터 사용](https://azure.microsoft.com/documentation/articles/storage-use-emulator/)을 참조하세요.

 다음 목록에는 Visual Studio 프로젝트에서 사용할 수 있는 인기 있는 데이터베이스 시스템 중 일부가 포함 되어 있습니다. 목록은 완전 하지 않습니다. Visual Studio 도구와 긴밀 하 게 통합할 수 있는 ADO.NET 데이터 공급자를 제공 하는 타사 공급 업체 목록은 [ADO.NET Data providers](https://msdn.microsoft.com/library/dd363565.aspx)를 참조 하세요.

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server는 Microsoft 주력 데이터베이스 제품입니다. SQL Server 2016은 혁신적인 성능, 고급 보안 및 풍부한 통합 보고 및 분석을 제공 합니다. 단일 컴퓨터에서 사용할 수 있는 확장성이 뛰어난 고성능 비즈니스 분석에서 다양 한 용도로 설계 된 다양 한 버전으로 제공 됩니다. SQL Server Express은 재배포 및 포함에 맞게 조정 된 SQL Server의 완전 한 기능을 갖춘 버전입니다.  LocalDB는 구성이 필요 없고 응용 프로그램의 프로세스에서 실행 되는 SQL Server Express의 단순화 된 버전입니다. [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 두 제품 중 하나를 다운로드할 수 있습니다. 이 섹션의 많은 SQL 예제에서는 SQL Server LocalDB를 사용 합니다. SSMS (SQL Server Management Studio)는 Visual Studio SQL Server 개체 탐색기에서 제공 되는 것 보다 많은 기능을 제공 하는 독립 실행형 데이터베이스 관리 응용 프로그램입니다. 이전 링크에서 SSMS를 가져올 수 있습니다.

### <a name="oracle"></a>Oracle
 Oracle [기술 네트워크](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) 페이지에서 oracle 데이터베이스의 유료 또는 무료 버전을 다운로드할 수 있습니다. Entity Framework 및 Tableadapter에 대 한 디자인 타임 지원에는 [Visual Studio 용 Oracle 개발자 도구](https://www.oracle.com/database/technologies/developer-tools/visual-studio/)필요 합니다. Oracle 인스턴트 클라이언트를 비롯 한 다른 공식 Oracle 제품은 NuGet 패키지 관리자를 통해 사용할 수 있습니다.  Oracle [온라인 설명서](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)의 지침에 따라 oracle 샘플 스키마를 다운로드할 수 있습니다.

### <a name="mysql"></a>MySQL
 MySQL은 기업 및 websites에서 널리 사용 되는 인기 있는 오픈 소스 데이터베이스 시스템입니다. Mysql, Visual Studio 용 MySQL 및 관련 제품에 대 한 다운로드는 [Windows의 mysql](https://www.mysql.com/why-mysql/windows/)에 있습니다.  타사는 다양 한 Visual Studio 확장 및 MySQL 용 독립 실행형 관리 응용 프로그램을 제공 합니다. Nuget 패키지 관리자 (**도구**  >  **nuget 패키지 관리자**  >  **솔루션의 nuget 패키지 관리**)에서 제공 하는 기능을 찾아볼 수 있습니다.

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL는 무료 오픈 소스 개체 관계형 데이터베이스 시스템입니다. Windows에 설치 하려면 [PostgreSQL 다운로드 페이지](http://www.postgresql.org/download/windows/)에서 다운로드할 수 있습니다.  소스 코드에서 PostgreSQL를 빌드할 수도 있습니다.  PostgreSQL core 시스템은 C 언어 인터페이스를 포함 합니다. 많은 제 3 자가 .NET 응용 프로그램에서 PostgreSQL를 사용 하기 위한 NuGet 패키지를 제공 합니다.  Nuget 패키지 관리자 (**도구**  >  **nuget 패키지 관리자**  >  **솔루션의 nuget 패키지 관리**)에서 제공 하는 기능을 찾아볼 수 있습니다. 가장 인기 있는 패키지는 [npgsql.org](http://www.npgsql.org/)에서 제공 하는 것일 수 있습니다.

### <a name="sqlite"></a>SQLite
 SQLite는 응용 프로그램 자체 프로세스에서 실행 되는 임베디드 SQL database 엔진입니다. [SQLite 다운로드 페이지](http://www.sqlite.org/download.html)에서 다운로드할 수 있습니다. SQLite 용 타사 NuGet 패키지도 사용할 수 있습니다. Nuget 패키지 관리자 (**도구**  >  **nuget 패키지 관리자**  >  **솔루션의 nuget 패키지 관리**)에서 제공 하는 기능을 찾아볼 수 있습니다.

### <a name="firebird"></a>Firebird
 Firebird은 오픈 소스 SQL 데이터베이스 시스템입니다. [Firebird 다운로드 페이지](http://firebirdsql.org/en/downloads/)에서 다운로드할 수 있습니다. ADO.NET 데이터 공급자는 NuGet 패키지 관리자를 통해 사용할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [SQL Server 및 구성 요소의 버전 및 에디션 확인 방법](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
