---
title: C++용 데이터 도구
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- CPP
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: 063efeebff92698b8e5db66880360713c73fe150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281099"
---
# <a name="visual-studio-data-tools-for-c"></a>C++용 Visual Studio 데이터 도구

네이티브 C++는 데이터 원본에 액세스할 때 가장 빠른 성능을 제공하는 경우가 많습니다. 하지만 Visual Studio의 C++ 애플리케이션에 대한 데이터 도구는 .NET 애플리케이션에 대한 데이터 도구만큼 다양하지 않습니다. 예를 들어, **데이터 원본** 창을 사용하여 데이터 원본을 C++ 디자인 화면으로 끌어서 놓을 수 없습니다. 개체 관계형 레이어가 필요한 경우 직접 작성하거나 타사 제품을 사용해야 합니다. 이는 데이터 바인딩 기능도 마찬가지입니다. 단, MFC 라이브러리를 사용하는 애플리케이션은 문서 및 보기와 함께 일부 데이터베이스 클래스를 사용하여 메모리에 데이터를 저장하고 사용자에게 표시할 수 있습니다. 자세한 내용은 [Visual C++의 데이터 액세스](/cpp/data/data-access-in-cpp)를 참조하세요.

SQL 데이터베이스에 연결하기 위해 네이티브 C++ 애플리케이션은 Windows에 포함된 ODBC 및 OLE DB 드라이버와 ADO 공급자를 사용할 수 있습니다. 해당 인터페이스를 지원하는 모든 데이터베이스에 연결할 수 있습니다. ODBC 드라이버는 표준입니다. OLE DB는 이전 버전과의 호환성을 위해 제공됩니다. 데이터 기술에 대한 자세한 내용은 [Windows Data Access Components](/previous-versions/windows/desktop/ms692897(v=vs.85))를 참조하세요.

SQL Server 2005 이상의 사용자 지정 기능을 활용하려면 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)를 사용합니다. Native Client에는 하나의 네이티브 DLL(동적 연결 라이브러리)에 SQL Server ODBC 드라이버와 SQL Server OLE DB 공급자도 포함됩니다. Microsoft SQL Server에 대한 애플리케이션의 네이티브 코드 API(ODBC, OLE DB 및 ADO) 사용을 지원합니다. SQL Server Native Client는 SQL Server Data Tools와 함께 설치됩니다. 프로그래밍 가이드는 여기에 있습니다. [SQL Server Native Client 프로그래밍](/sql/relational-databases/native-client/sql-server-native-client-programming).

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>C++ 애플리케이션에서 ODBC 및 SQL Native Client를 통해 localDB에 연결

1. SQL Server 데이터 도구를 설치합니다.

2. 연결할 샘플 SQL 데이터베이스가 필요한 경우 Northwind 데이터베이스를 다운로드하고 새 위치에 압축을 풉니다.

3. SQL Server Management Studio를 사용하여 압축을 푼 *Northwind.mdf* 파일을 localDB에 연결합니다. SQL Server Management Studio가 시작되면 (localdb)\MSSQLLocalDB에 연결합니다.

   ![SSMS 연결 대화 상자](../data-tools/media/raddata-ssms-connect-dialog.png)

   그런 다음 왼쪽 창에서 localdb 노드를 마우스 오른쪽 단추로 클릭하고 **연결**을 선택합니다.

   ![SSMS 데이터베이스 연결](../data-tools/media/raddata-ssms-attach-database.png)

4. ODBC Windows SDK 샘플을 다운로드하고 새 위치에 압축을 풉니다. 이 샘플에서는 데이터베이스에 연결하고 쿼리 및 명령을 실행하는 데 사용되는 기본 ODBC 명령을 보여 줍니다. [Microsoft ODBC(Open Database Connectivity)](/sql/odbc/microsoft-open-database-connectivity-odbc)에서 해당 기능을 자세히 알아볼 수 있습니다. 솔루션을 처음 로드할 때(C++ 폴더에 있는 경우) Visual Studio에서 현재 버전으로의 업그레이드를 제공합니다. **예**를 클릭합니다.

5. Native Client를 사용하려면 ‘헤더’ 파일 및 ‘라이브러리’ 파일이 필요합니다.  파일에는 sql.h에 정의된 ODBC 함수 외에도 SQL Server 관련 함수와 정의가 포함되어 있습니다. **프로젝트** > **속성** > **VC++ 디렉터리**에서 다음 디렉터리를 추가합니다.

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

   또한 이 라이브러리 디렉터리를 추가합니다.

   **%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6. *odbcsql.cpp*에 줄을 추가합니다. #define으로 관련 없는 OLE DB 정의가 컴파일되는 것을 방지합니다.

   ```cpp
   #define _SQLNCLI_ODBC_
   #include <sqlncli.h>
   ```

    샘플은 실제로 Native Client 기능을 사용하지 않으므로 컴파일 및 실행을 위해 앞의 단계를 수행하지 않아도 됩니다. 하지만 이제 이 기능을 사용할 수 있도록 프로젝트가 구성됩니다. 자세한 내용은 [SQL Server Native Client 프로그래밍](/sql/relational-databases/native-client/sql-server-native-client)을 참조하세요.

7. ODBC 하위 시스템에서 사용할 드라이버를 지정합니다. 샘플은 DRIVER 연결 문자열 특성을 명령줄 인수로 전달합니다. **프로젝트** > **속성** > **디버깅**에서 이 명령 인수를 추가합니다.

   ```cpp
   DRIVER="SQL Server Native Client 11.0"
   ```

8. **F5** 키를 눌러 애플리케이션을 빌드하고 실행합니다. 드라이버에서 데이터베이스를 입력하라는 대화 상자가 표시됩니다. `(localdb)\MSSQLLocalDB`를 입력하고 **트러스트된 연결 사용**을 선택합니다. **확인**을 누릅니다. 연결에 성공했음을 나타내는 메시지가 콘솔에 표시되어야 합니다. 또한 SQL 문을 입력할 수 있는 명령 프롬프트가 표시되어야 합니다. 다음 화면에는 예제 쿼리와 결과가 표시됩니다.

   ![ODBC 샘플 쿼리 출력](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
