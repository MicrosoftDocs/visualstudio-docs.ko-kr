---
title: Visual Studio에서 데이터 작업
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c7aa1544f998a88424c0087fadceab63757d23b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272080"
---
# <a name="work-with-data-in-visual-studio"></a>Visual Studio에서 데이터 작업

Visual Studio에서는 거의 모든 데이터베이스 제품 또는 서비스의 데이터에 연결 하는 응용 프로그램을 로컬 컴퓨터, 로컬 영역 네트워크 또는 공용, 사설 또는 하이브리드 클라우드에서 모든 형식으로 만들 수 있습니다.

JavaScript, Python, PHP, Ruby 또는 c + +의 응용 프로그램의 경우 라이브러리를 가져오고 코드를 작성 하 여 다른 작업을 수행 하는 것 처럼 데이터에 연결 합니다. .NET 응용 프로그램의 경우 Visual Studio는 데이터 원본을 탐색 하 고, 개체 모델을 만들어 메모리에 데이터를 저장 및 조작 하 고, 데이터를 사용자 인터페이스에 바인딩하는 데 사용할 수 있는 도구를 제공 합니다. Microsoft Azure는 .NET, Java, Node.js, PHP, Python, Ruby 및 모바일 앱에 대 한 Sdk 및 Visual Studio에서 Azure Storage에 연결 하는 데 사용할 수 있는 도구를 제공 합니다.

::: moniker range="vs-2017"
다음 목록에서는 Visual Studio에서 사용할 수 있는 몇 가지 데이터베이스 및 저장소 시스템을 보여 줍니다. [Microsoft Azure](https://azure.microsoft.com/) 제품은 기본 데이터 저장소의 모든 프로 비전 및 관리를 포함 하는 데이터 서비스입니다. [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 의 **azure 개발** 워크 로드를 통해 Visual studio에서 직접 azure 데이터 저장소를 사용할 수 있습니다.
::: moniker-end
::: moniker range=">=vs-2019"
다음 목록에서는 Visual Studio에서 사용할 수 있는 몇 가지 데이터베이스 및 저장소 시스템을 보여 줍니다. [Microsoft Azure](https://azure.microsoft.com/) 제품은 기본 데이터 저장소의 모든 프로 비전 및 관리를 포함 하는 데이터 서비스입니다. [Visual studio 2019](https://visualstudio.microsoft.com/downloads) 의 **azure 개발** 워크 로드를 통해 Visual studio에서 직접 azure 데이터 저장소를 사용할 수 있습니다.
::: moniker-end

![Azure 개발 워크로드](media/azure-development-workload.png)

여기에 나열 된 다른 SQL 및 NoSQL 데이터베이스 제품은 대부분 로컬 컴퓨터, 로컬 네트워크 또는 가상 컴퓨터의 Microsoft Azure에서 호스팅될 수 있습니다. Microsoft Azure 가상 머신에서 데이터베이스를 호스트 하는 경우 데이터베이스 자체를 관리 하는 일을 담당 합니다.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- 저장소 (blob, 테이블, 큐, 파일)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- 등...

**SQL**

- SQL Server 2005-2016 (Express 및 LocalDB 포함)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- 등...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- 등...

::: moniker range="vs-2017"

많은 데이터베이스 공급 업체와 제 3 자가 NuGet 패키지를 통해 Visual Studio 통합을 지원 합니다. Visual Studio의 nuget 패키지 관리자를 통해 nuget.org 또는 Visual Studio의 nuget 패키지 관리자를 통해 제품을 탐색할 수 있습니다 (**도구**  >  **nuget 패키지 관리자**  >  **솔루션용 nuget 패키지 관리**). 다른 데이터베이스 제품은 Visual Studio와 확장으로 통합 됩니다. 이러한 제품은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 에서 찾아보거나, **도구**  >  **확장 및 업데이트** 로 이동한 다음 대화 상자의 왼쪽 창에서 **온라인** 을 선택 하 여 찾을 수 있습니다. 자세한 내용은 [Visual Studio에 대 한 호환 데이터베이스 시스템](../data-tools/installing-database-systems-tools-and-samples.md)을 참조 하세요.

::: moniker-end

::: moniker range=">=vs-2019"

많은 데이터베이스 공급 업체와 제 3 자가 NuGet 패키지를 통해 Visual Studio 통합을 지원 합니다. Visual Studio의 nuget 패키지 관리자를 통해 nuget.org 또는 Visual Studio의 nuget 패키지 관리자를 통해 제품을 탐색할 수 있습니다 (**도구**  >  **nuget 패키지 관리자**  >  **솔루션용 nuget 패키지 관리**). 다른 데이터베이스 제품은 Visual Studio와 확장으로 통합 됩니다. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 에서 이러한 제품을 찾아보거나 **확장**  >  **관리** 로 이동한 다음 대화 상자의 왼쪽 창에서 **온라인** 을 선택 하 여 이러한 제품을 찾아볼 수 있습니다. 자세한 내용은 [Visual Studio에 대 한 호환 데이터베이스 시스템](../data-tools/installing-database-systems-tools-and-samples.md)을 참조 하세요.

::: moniker-end

> [!NOTE]
> SQL Server 2005에 대해 연장된 지원은 2016년 4월 12일에 종료되었습니다. Visual Studio 2015 이상에서 데이터 도구가 SQL Server 2005에서 계속 작동할 수 있는 것은 아닙니다. 자세한 내용은 [SQL Server 2005에 대 한 지원 종료 알림](https://www.microsoft.com/sql-server/sql-server-2005)을 참조 하세요.

## <a name="net-languages"></a>.NET 언어

.NET Core에 포함 된 모든 .NET 데이터 액세스는 모든 종류의 데이터 원본에 액세스 하기 위한 인터페이스를 정의 하는 클래스 집합인 ADO.NET을 기반으로 합니다. Visual Studio에는 데이터베이스에 연결 하 고, 데이터를 조작 하 고, 사용자에 게 데이터를 표시 하는 데 도움이 되는 ADO.NET와 함께 작동 하는 몇 가지 도구와 디자이너가 있습니다. 이 섹션의 설명서에서는 이러한 도구를 사용 하는 방법을 설명 합니다. ADO.NET 명령 개체에 대해 직접 프로그래밍할 수도 있습니다. ADO.NET Api를 직접 호출 하는 방법에 대 한 자세한 내용은 [ADO.NET](/dotnet/framework/data/adonet/index)를 참조 하세요.

ASP.NET 관련 된 데이터 액세스 설명서는 ASP.NET 사이트에서 [데이터 작업](https://www.asp.net/web-forms/overview/presenting-and-managing-data) 을 참조 하세요. ASP.NET MVC와 함께 Entity Framework를 사용 하는 방법에 대 한 자습서는 [mvc 5를 사용 하 여 Entity Framework 6 Code First 시작](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)을 참조 하세요.

C # 또는 Visual Basic의 UWP (유니버설 Windows 플랫폼) 앱은 .NET 용 Microsoft Azure SDK를 사용 하 여 Azure Storage 및 기타 Azure 서비스에 액세스할 수 있습니다. Windows. HttpClient 클래스를 사용 하면 모든 RESTful 서비스와 통신할 수 있습니다. 자세한 내용은 [Windows를 사용 하 여 http 서버에 연결 하는 방법](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)을 참조 하세요.

로컬 컴퓨터에 데이터를 저장 하는 경우 권장 되는 방법은 앱과 동일한 프로세스에서 실행 되는 SQLite를 사용 하는 것입니다. ORM (개체-관계형 매핑) 계층이 필요한 경우 Entity Framework를 사용할 수 있습니다. 자세한 내용은 Windows 개발자 센터에서 [데이터 액세스](/windows/uwp/data-access/index) 를 참조 하세요.

Azure 서비스에 연결 하는 경우 최신 [AZURE SDK 도구](https://azure.microsoft.com/downloads/)를 다운로드 해야 합니다.

### <a name="data-providers"></a>데이터 공급자

ADO.NET에서 데이터베이스를 사용할 수 있도록 하려면 사용자 지정 *ADO.NET 데이터 공급자* 가 있어야 합니다. 그렇지 않으면 ODBC 또는 OLE DB 인터페이스를 노출 해야 합니다. Microsoft는 SQL Server 제품 뿐만 아니라 ODBC 및 OLE DB 공급자에 대 한 [ADO.NET 데이터 공급자의 목록을](/dotnet/framework/data/adonet/ado-net-overview) 제공 합니다.

### <a name="data-modeling"></a>데이터 모델링

.NET에서는 데이터 원본에서 데이터를 검색 한 후 메모리에서 데이터를 모델링 하 고 조작할 수 있는 세 가지 옵션이 있습니다.

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) 기본 설정 된 Microsoft ORM 기술입니다. 이를 사용 하 여 관계형 데이터를 최고 수준의 .NET 개체로 프로그래밍할 수 있습니다. 새 응용 프로그램의 경우 모델이 필요할 때 첫 번째로 선택 해야 합니다. 기본 ADO.NET 공급자의 사용자 지정 지원이 필요 합니다.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 이전 세대 개체-관계형 매퍼입니다. 더 복잡 한 시나리오에 적합 하지만 더 이상 개발에 더 이상 필요 하지 않습니다.

[데이터 집합](../data-tools/dataset-tools-in-visual-studio.md) 세 가지 모델링 기술 중 가장 오래 된 기술입니다. 대량의 데이터를 처리 하거나 복잡 한 쿼리 또는 변환을 수행 하지 않는 "데이터 폼" 응용 프로그램을 신속 하 게 개발 하는 데 주로 설계 되었습니다. DataSet 개체는 SQL 데이터베이스 개체와 논리적으로 동일한 SQL 데이터베이스 개체와 유사한 DataTable 및 DataRow 개체로 구성 됩니다. SQL 데이터 원본을 기반으로 하는 비교적 간단한 응용 프로그램의 경우에도 데이터 집합을 선택 하는 것이 좋습니다.

이러한 기술을 사용할 필요는 없습니다. 특히 성능이 중요 한 일부 시나리오에서는 DataReader 개체를 사용 하 여 데이터베이스에서 읽고 필요한 값을 List와 같은 컬렉션 개체에 복사할 수 있습니다 \<T> .

## <a name="native-c"></a>네이티브 C++

SQL Server에 연결 하는 c + + 응용 프로그램은 대부분의 경우 [SQL Server 용 Microsoft® ODBC 드라이버 13.1](https://www.microsoft.com/download/details.aspx?id=53339) 를 사용 해야 합니다. 서버가 연결 된 경우 OLE DB 필요 하며 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)를 사용 합니다. [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) 또는 OLE DB 드라이버를 직접 사용 하 여 다른 데이터베이스에 액세스할 수 있습니다. ODBC는 현재 표준 데이터베이스 인터페이스 이지만 대부분의 데이터베이스 시스템은 ODBC 인터페이스를 통해 액세스할 수 없는 사용자 지정 기능을 제공 합니다. OLE DB은 계속 지원 되지만 새 응용 프로그램에는 권장 되지 않는 레거시 COM 데이터 액세스 기술입니다. 자세한 내용은 [Visual C++에서 데이터 액세스](/cpp/data/data-access-in-cpp)를 참조 하세요.

REST 서비스를 사용 하는 c + + 프로그램은 [c + + REST SDK](https://github.com/Microsoft/cpprestsdk)를 사용할 수 있습니다.

Microsoft Azure Storage와 함께 작동 하는 c + + 프로그램은 [Microsoft Azure Storage 클라이언트](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)를 사용할 수 있습니다.

데이터 모델링 &mdash; Visual Studio는 c + + 용 ORM 계층을 제공 하지 않습니다. [ODB](https://www.codesynthesis.com/products/odb/) 는 c + + 용의 인기 있는 오픈 소스 ORM입니다.

C + + 응용 프로그램에서 데이터베이스에 연결 하는 방법에 대 한 자세한 내용은 [c + + 용 Visual Studio data tools](../data-tools/visual-studio-data-tools-for-cpp.md)를 참조 하세요. 레거시 Visual C++ 데이터 액세스 기술에 대 한 자세한 내용은 [데이터 액세스](/cpp/data/data-access-in-cpp)를 참조 하세요.

## <a name="javascript"></a>JavaScript

[Visual Studio의 JavaScript](/scripting/javascript/javascript-language-reference) 는 플랫폼 간 앱, UWP 앱, 클라우드 서비스, 웹 사이트 및 웹 앱을 빌드하기 위한 최고 수준의 언어입니다. Visual Studio 내에서 Bower, Grunt, Gulp, npm 및 NuGet을 사용 하 여 즐겨 사용 하는 JavaScript 라이브러리 및 데이터베이스 제품을 설치할 수 있습니다. [Azure 웹 사이트](https://azure.microsoft.com/)에서 sdk를 다운로드 하 여 azure storage 및 서비스에 연결 합니다. Edge.js는 서버 쪽 JavaScript (Node.js)를 ADO.NET 데이터 원본에 연결 하는 라이브러리입니다.

## <a name="python"></a>Python

Python 응용 프로그램을 만들기 위해 [Visual Studio에서 python 지원을](../python/overview-of-python-tools-for-visual-studio.md) 설치 합니다. Azure 설명서에는 다음을 포함 하 여 데이터에 연결 하는 몇 가지 자습서가 있습니다.

- [Azure의 Django 및 SQL Database](/azure/app-service/app-service-web-get-started-python)
- [Azure의 Django 및 MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- [Blob](/azure/storage/blobs/storage-quickstart-blobs-python), [파일](/azure/storage/files/storage-python-how-to-use-file-storage), [큐](/azure/storage/queues/storage-python-how-to-use-queue-storage)및 [테이블 (cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)작업

## <a name="related-topics"></a>관련 항목

[MICROSOFT AI 플랫폼](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Cortana Analytics Suite 및 사물 인터넷에 대 한 지원을 포함 하 여 Microsoft intelligent cloud에 대 한 소개를 제공 합니다.

[Microsoft Azure Storage](/azure/storage/) &mdash; Azure Storage 및 Azure blob, 테이블, 큐 및 파일을 사용 하 여 응용 프로그램을 만드는 방법을 설명 합니다.

[Azure SQL Database](/azure/sql-database/) &mdash; 관계형 Database as a Service Azure SQL Database에 연결 하는 방법을 설명 합니다.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; 데이터 연결 응용 프로그램 및 데이터베이스의 디자인, 탐색, 테스트 및 배포를 간소화 하는 도구에 대해 설명 합니다.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; ADO.NET 아키텍처와 ADO.NET 클래스를 사용 하 여 응용 프로그램 데이터를 관리 하 고 데이터 원본 및 XML과 상호 작용 하는 방법을 설명 합니다.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; 개발자가 관계형 데이터베이스에 대해 직접 프로그래밍 하는 대신 개념적 모델을 기반으로 프로그래밍할 수 있도록 하는 데이터 응용 프로그램을 만드는 방법을 설명 합니다.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index) &mdash; 를 사용 하 여 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] [OData (Open Data Protocol)](https://www.odata.org/)를 구현 하는 웹 또는 인트라넷에 데이터 서비스를 배포 하는 방법을 설명 합니다.

[Office 솔루션](../vsto/data-in-office-solutions.md) &mdash; 의 데이터 Office 솔루션에서 데이터가 작동 하는 방식을 설명 하는 항목의 링크를 포함 합니다. 여기에는 스키마 지향 프로그래밍, 데이터 캐싱 및 서버 쪽 데이터 액세스에 대 한 정보가 포함 됩니다.

[LINQ (통합 언어 쿼리)](/dotnet/csharp/linq/) &mdash; C # 및 Visual Basic에 기본 제공 되는 쿼리 기능과 관계형 데이터베이스, XML 문서, 데이터 집합 및 메모리 내 컬렉션을 쿼리 하기 위한 일반 모델에 대해 설명 합니다.

[Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; 의 XML 도구 XML 데이터 작업, XSLT 디버깅, .NET XML 기능 및 XML 쿼리 아키텍처에 대해 설명 합니다.

[XML 문서 및 데이터](/dotnet/standard/data/xml/index) &mdash; .NET에서 XML 문서 및 데이터를 사용 하는 포괄적이 고 통합 된 클래스 집합에 대 한 개요를 제공 합니다.
