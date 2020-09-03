---
title: 웹 성능 테스트에 데이터 소스 추가
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94ad53e4ac3d65bfe6cf08bf03f1f79c2075e03d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85289068"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>웹 성능 테스트에 데이터 소스 추가

데이터를 바인딩하여 다른 값을 같은 테스트에 제공합니다. 예를 들어, 다른 값을 폼 게시 매개 변수에 제공합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![웹 성능 테스트에 데이터 바인딩](../test/media/web_test_databinding_conceptual.png)

여기에서는 샘플 ASP.NET 응용 프로그램을 사용합니다. 세 개의 *.aspx* 페이지(기본 페이지, 빨강 페이지, 파랑 페이지)가 있습니다. 기본 페이지는 빨강 또는 파랑 및 전송 단추를 선택할 수 있는 라디오 컨트롤이 포함됩니다. 다른 두 *.aspx* 페이지는 매우 간단합니다. 한 페이지의 레이블이 빨강이면, 다른 한 페이지의 레이블은 파랑입니다. 기본 페이지에서 제출을 선택하면 다른 페이지 중 하나가 표시됩니다. [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) 샘플을 다운로드하거나, 사용자 고유의 웹앱과 함께 따를 수 있습니다.

![테스트할 웹 응용 프로그램 실행](../test/media/web_test_databinding_runwebapp.png)

또한 솔루션에는 웹 애플리케이션의 페이지를 탐색하는 웹 성능 테스트를 포함해야 합니다.

![웹 성능 테스트가 포함된 솔루션](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>SQL 데이터베이스 만들기

::: moniker range="vs-2017"

1. Visual Studio Enterprise가 없는 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지에서 다운로드할 수 있습니다.

2. SQL 데이터베이스를 만듭니다.

     ![새 SQL 데이터베이스 추가](../test/media/web_test_databinding_sql_addnewdb.png)

3. 데이터베이스 프로젝트를 만듭니다.

     ![데이터베이스에서 새 프로젝트 만들기](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. 데이터베이스 프로젝트에 테이블을 추가합니다.

     ![데이터베이스 프로젝트에 새 테이블 추가](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. 테이블에 필드를 추가합니다.

     ![테이블에 필드 추가](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. 데이터베이스 프로젝트를 게시합니다.

     ![솔루션 탐색기에서 데이터베이스 프로젝트 게시](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. 필드에 데이터를 추가합니다.

     ![필드에 데이터 추가](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio Enterprise가 없는 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지에서 다운로드할 수 있습니다.

2. SQL 데이터베이스를 만듭니다.

     ![새 SQL 데이터베이스 추가](../test/media/web_test_databinding_sql_addnewdb.png)

3. 데이터베이스 프로젝트를 만듭니다.

     ![데이터베이스에서 새 프로젝트 만들기](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. 데이터베이스 프로젝트에 테이블을 추가합니다.

     ![데이터베이스 프로젝트에 새 테이블 추가](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. 테이블에 필드를 추가합니다.

     ![테이블에 필드 추가](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. 데이터베이스 프로젝트를 게시합니다.

     ![솔루션 탐색기에서 데이터베이스 프로젝트 게시](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. 필드에 데이터를 추가합니다.

     ![필드에 데이터 추가](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>데이터 소스를 추가합니다.

1. 데이터 원본을 추가합니다.

     ![웹 성능 테스트에 데이터 소스 추가](../test/media/web_test_databinding_sql_adddatasource.png)

2. 데이터 소스 형식을 선택하고 이름을 지정합니다.

     ![데이터베이스 소스의 이름 지정](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. 연결을 만듭니다.

     ![새 연결 선택](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     연결 정보를 입력합니다.

     ![SQL 데이터베이스 연결 속성 입력](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. 테스트에 사용할 테이블을 선택합니다.

     ![데이터 소스로 Color 테이블 추가](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     표가 테스트에 바인딩됩니다.

     ![웹 성능 테스트에 추가한 Data Sources 노드](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. 테스트를 저장합니다.

## <a name="bind-the-data"></a>데이터 바인딩

1. **ColorName** 필드에 바인딩합니다.

     ![RadioButtonList1 값에 ColorName 필드 바인딩](../test/media/web_test_databinding_sql_binddatasource.png)

2. **솔루션 탐색기**에서 *Local.testsettings* 파일을 열고, **데이터 소스 행마다 한 번씩 실행** 옵션을 선택합니다.

     ![테스트 설정 파일 편집](../test/media/web_test_databinding_sql_testsettings.png)

3. 웹 성능 테스트를 저장합니다.

## <a name="run-the-test-with-the-data"></a>데이터를 사용하여 테스트 실행

1. 테스트를 실행합니다.

     ![웹 성능 테스트를 실행하여 바인딩 확인](../test/media/web_test_databinding_sql_runtest.png)

     각 데이터 행에 대해 두 가지 실행이 표시됩니다. 실행 1은 페이지 *Red.aspx*에 대한 요청을 보내고 실행 2는 페이지 *Blue.aspx*에 대한 요청을 보냅니다.

     ![테스트 실행 결과](../test/media/web_test_databinding_sql_runresults.png)

     데이터 소스에 바인딩할 때는 기본 응답 URL 규칙을 위반할 수 있습니다. 이 경우 2 실행의 오류는 원래 테스트 기록의 *Red.aspx* 페이지에서 발생할 것으로 예상되지만 데이터 바인딩이 *Blue.aspx* 페이지로 이동하는 규칙으로 인한 것입니다.

2. **응답 URL** 유효성 검사 규칙을 삭제하고 테스트를 다시 실행하여 유효성 검사 오류를 수정합니다.

     ![응답 URL 유효성 검사 규칙 삭제](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     데이터 바인딩을 사용하여 웹 성능 테스트를 통과합니다.

     ![데이터 바인딩을 사용하여 테스트 통과](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>질문과 대답

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>Q: 데이터 소스로 사용할 수 있는 데이터베이스는 무엇입니까?

**A:** 다음을 사용할 수 있습니다.

- Microsoft SQL Azure

- Microsoft SQL Server 2005 이상 버전

- Microsoft SQL Server 데이터베이스 파일(SQL Express 포함)

- Microsoft ODBC

- OLE DB의 .NET Framework 공급자를 사용한 Microsoft Access 파일

- Oracle 7.3, 8i, 9i 또는 10g

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>Q: 쉼표로 구분된 값(CSV) 텍스트 파일을 데이터 원본으로 사용하려면 어떻게 할까요?

**A:** 방법은 다음과 같습니다.

1. 프로젝트 데이터베이스 아티팩트를 구성하고 항목을 추가하려면 폴더를 만듭니다.

     ![Data 폴더에 새 항목 추가](../test/media/web_test_databinding_foldernewitem.png)

2. 텍스트 파일을 만듭니다.

     ![새 텍스트 파일 이름을 ColorData.csv로 지정](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. 텍스트 파일을 편집하여 다음을 추가합니다.

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. [데이터 소스 추가](#add-the-data-source)의 단계를 사용하되 사용자의 데이터 소스에 맞게 CSV 파일을 선택합니다.

     ![이름을 입력하고 CSV 파일을 선택](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>Q: 기존 CSV 파일에 열 머리글이 없으면 어떻게 됩니까?

**A:** 열 머리글을 추가할 수 없는 경우 스키마 설명 파일을 사용하여 CSV 파일을 데이터베이스로 취급할 수 있습니다.

1. *schema.ini*라는 새 텍스트 파일을 추가합니다.

     ![schema.ini 파일 추가](../test/media/web_test_databinding_schemafile.png)

2. *schema.ini* 파일을 편집하여 데이터 구조를 설명하는 정보를 추가합니다. 예를 들어, CSV 파일을 설명하는 스키마 파일은 다음과 같습니다.

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. 테스트에 데이터 소스를 추가합니다.

     ![웹 성능 테스트에 데이터 소스 추가](../test/media/web_test_databinding_sql_adddatasource.png)

4. *schema.ini* 파일을 사용하는 경우 **데이터베이스**(CSV 파일이 아님)를 데이터 소스로 선택하고 이름을 지정합니다.

     ![데이터베이스 데이터 소스 추가](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. 새 연결을 만듭니다.

     ![새 연결 선택](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. .NET Framework Data Provider for OLE DB를 선택합니다.

     ![.NET Framework OLE DB 데이터 공급자 선택](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. **고급**을 선택합니다.

     ![고급 선택](../test/media/web_test_databinding_advanced.png)

8. 공급자 속성의 경우 Microsoft.Jet.OLEDB.4.0을 선택한 다음, **확장 속성**을 Text;HDR=NO로 설정합니다.

     ![고급 속성 적용](../test/media/web_test_databinding_advancedproperties.png)

9. 스키마 파일이 포함된 폴더 이름을 입력하고 연결을 테스트합니다.

     ![데이터 폴더의 경로 입력](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. 사용할 CSV 파일을 선택합니다.

     ![텍스트 파일 선택](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     마친 후, CSV 파일이 테이블로 나타납니다.

     ![테스트에 추가된 데이터 소스](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>Q: XML 파일을 데이터 소스로 사용하려면 어떻게 할까요?

**A:** 예.

1. 프로젝트 데이터베이스 아티팩트를 구성하고 항목을 추가하려면 폴더를 만듭니다.

     ![Data 폴더에 새 항목 추가](../test/media/web_test_databinding_foldernewitem.png)

2. XML 파일을 만듭니다.

     ![Add ColorData.xml 파일 추가](../test/media/web_test_databinding_additemxmlfile.png)

3. XML 파일을 편집하고 데이터를 추가합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. [데이터 소스 추가](#add-the-data-source)의 단계를 사용하되 사용자의 데이터 소스에 맞게 XML 파일을 선택합니다.

     ![이름을 입력하고 XML 파일을 선택](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>Q: SOAP을 사용한 웹 서비스 요청에 데이터 바인딩을 추가할 수 있습니까?

**A:** 예, SOAP XML을 수동으로 변경해야 합니다.

1. 요청 트리 및 속성 창에서 웹 서비스 요청을 선택하고 문자열 본문 속성에서 줄임표(…)를 선택합니다.

     ![웹 서비스 문자열 본문 편집](../test/media/web_test_databinding_webservicerequest.png)

2. 다음 구문을 사용하여 SOAP 본문의 값을 데이터 바인딩된 값으로 바꿉니다.

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    예를 들어 다음과 같은 코드를 가정해 봅니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    다음과 같이 변경할 수 있습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. 테스트를 저장합니다.
