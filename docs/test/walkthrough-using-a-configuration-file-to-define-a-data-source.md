---
title: 구성 파일을 사용하여 원본 데이터 정의
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a4f5731a828eb04e57f56a46fe399125b5ded2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75776151"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>연습: 구성 파일을 통한 데이터 원본 정의

이 연습에서는 *app.config* 파일에 정의된 데이터 원본을 유닛 테스트에 사용하는 방법을 설명합니다. *클래스에 사용될 수 있는 데이터 원본을 정의하는*app.config<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 파일을 만드는 방법을 알아봅니다. 이 연습에서 수행할 작업은 다음과 같습니다.

- *app.config* 파일 만들기

- 사용자 지정 구성 섹션 정의

- 연결 문자열 정의

- 데이터 원본 정의

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 클래스를 사용하여 데이터 원본 액세스

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 완료하려면 다음 사항이 필요합니다.

- Visual Studio Enterprise

- 하나 이상의 테스트 메서드를 위한 데이터를 제공할 Microsoft Access 또는 Microsoft Excel

- 테스트 프로젝트가 포함된 Visual Studio 솔루션

## <a name="add-an-appconfig-file-to-the-project"></a>프로젝트에 app.config 파일 추가

1. 테스트 프로젝트에 이미 *app.config* 파일이 있는 경우 [사용자 지정 구성 섹션 정의](#define-a-custom-configuration-section)로 이동합니다.

2. **솔루션 탐색기**에서 테스트 프로젝트를 마우스 오른쪽 단추로 클릭한 다음, **추가** > **새 항목**을 선택합니다.

     **새 항목 추가** 창이 열립니다.

3. **애플리케이션 구성 파일** 템플릿을 선택하고 **추가**를 클릭합니다.

## <a name="define-a-custom-configuration-section"></a>사용자 지정 구성 섹션 정의

*app.config* 파일을 검토합니다. XML 선언과 루트 요소는 반드시 포함되어야 합니다.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>app.config 파일에 사용자 지정 구성 섹션을 추가하려면

1. *app.config*의 루트 요소는 **구성** 요소여야 합니다. **configuration** 요소 내에 **configSections** 요소를 만듭니다. **configSections**는 *app.config* 파일의 첫 번째 요소여야 합니다.

2. **configSections** 요소 내에 **section** 요소를 만듭니다.

3. **section** 요소에서 `name`이라는 특성을 추가하고 여기에 `microsoft.visualstudio.testtools` 값을 할당합니다. `type`이라는 다른 특성을 추가하고 여기에 `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions` 값을 할당합니다.

**section** 요소는 다음과 유사하게 표시됩니다.

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> 어셈블리 이름이 사용 중인 버전과 일치해야 합니다.

## <a name="define-connection-strings"></a>연결 문자열 정의

연결 문자열은 데이터 소스 액세스를 위한 공급자 특정 정보를 정의합니다. 구성 파일에 정의된 연결 문자열은 애플리케이션 전체에서 재사용 가능한 데이터 공급자 정보를 제공합니다. 이 섹션에서는 사용자 지정 구성 섹션에 정의된 데이터 원본에서 사용되는 두 개의 연결 문자열을 만듭니다.

### <a name="to-define-connection-strings"></a>연결 문자열을 정의하려면

1. **configSections** 요소 뒤에 **connectionStrings** 요소를 만듭니다.

2. **connectionStrings** 요소 내에 두 개의 **add** 요소를 만듭니다.

3. 첫 번째 **add** 요소에서 Microsoft Access 데이터베이스에 연결하기 위한 다음과 같은 특성 및 값을 만듭니다.

|attribute|값|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

두 번째 **add** 요소에서 Microsoft Excel 스프레드시트에 연결하기 위한 다음과 같은 특성 및 값을 만듭니다.

|attribute|값|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

**connectionStrings** 요소는 다음과 유사하게 표시됩니다.

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>데이터 원본 정의

데이터 원본 섹션에는 테스트 엔진이 데이터 원본에서 데이터를 검색할 때 사용하는 4개의 특성이 포함되어 있습니다.

- `name`은 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>가 사용할 데이터 원본을 지정하는 데 사용하는 ID를 정의합니다.

- `connectionString`은 이전 연결 문자열 정의 섹션에서 만든 연결 문자열을 식별합니다.

- `dataTableName`은 테스트에 사용할 데이터가 들어 있는 테이블 또는 시트를 정의합니다.

- `dataAccessMethod`는 데이터 원본에 있는 데이터 값에 액세스하는 기술을 정의합니다.

이 섹션에서는 단위 테스트에 사용할 두 개의 데이터 원본을 정의합니다.

### <a name="to-define-data-sources"></a>데이터 원본을 정의하려면

1. **connectionStrings** 요소 뒤에 **microsoft.visualstudio.testtools** 요소를 만듭니다. 이 섹션은 사용자 지정 구성 섹션 정의에서 만들어졌습니다.

2. **microsoft.visualstudio.testtools** 요소 내에서 **dataSources** 요소를 만듭니다.

3. **dataSources** 요소 내에 두 개의 **add** 요소를 만듭니다.

4. 첫 번째 **add** 요소에서 Microsoft Access 데이터 원본에 대해 다음과 같은 특성 및 값을 만듭니다.

|attribute|값|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

두 번째 **add** 요소에서 Microsoft Excel 데이터 원본에 대해 다음과 같은 특성 및 값을 만듭니다.

|attribute|값|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

**microsoft.visualstudio.testtools** 요소는 다음과 유사하게 표시됩니다.

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

최종 *app.config* 파일은 다음과 유사하게 표시됩니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>app.config에 정의된 데이터 원본을 사용하는 단위 테스트 만들기

이제 *app.config* 파일을 정의했으므로 *app.config* 파일에 정의된 데이터 원본에 있는 데이터를 사용하는 단위 테스트를 만듭니다. 이 섹션에서는 다음을 수행합니다.

- *app.config* 파일에 있는 데이터 원본을 만듭니다.

- 각 데이터 원본의 값을 비교하는 두 개의 테스트 메서드에서 데이터 원본을 사용합니다.

### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access 데이터 원본을 만들려면

1. *testdatasource.accdb*라는 Microsoft Access 데이터베이스를 만듭니다.

2. `MyDataTable`testdatasource.accdb*에 테이블을 만들고 이름을* 로 지정합니다.

3. `MyDataTable` 데이터 형식을 사용하여 이름이 `Arg1` 및 `Arg2`인 두 개의 필드를 `Number`에 만듭니다.

4. `MyDataTable`과 `Arg1`에 다음과 같은 값을 사용한 5개의 엔터티를 `Arg2`에 추가합니다. (10,50), (3,2), (6,0), (0,8), (12312,1000)

5. 데이터베이스를 저장한 후 닫습니다.

6. 데이터베이스의 위치를 가리키도록 연결 문자열을 변경합니다. 데이터베이스의 위치를 반영하여 `Data Source`의 값을 변경합니다.

### <a name="to-create-a-microsoft-excel-data-source"></a>Microsoft Excel 데이터 원본을 만들려면

1. *data.xlsx*라는 Microsoft Excel 스프레드시트를 만듭니다.

2. `Sheet1`data.xlsx*에 없는 경우* 이라는 시트를 만듭니다.

3. `Val1`에 두 개의 열 머리글을 만들고 `Val2` 및 `Sheet1`로 이름을 지정합니다.

4. `Sheet1`과 `Val1`에 다음과 같은 값을 사용한 5개의 엔터티를 `Val2`에 추가합니다. (1,1), (2,2), (3,3), (4,4), (5,0)

5. 스프레드시트를 저장한 후 닫습니다.

6. 스프레드시트의 위치를 가리키도록 연결 문자열을 변경합니다. 스프레드시트의 위치를 반영하여 `dbq`의 값을 변경합니다.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>app.config 데이터 원본을 사용하여 단위 테스트를 만들려면

1. 테스트 프로젝트에 단위 테스트를 추가합니다.

2. 자동 생성된 단위 테스트 콘텐츠를 다음 코드로 바꿉니다.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. DataSource 특성을 검토합니다. *app.config* 파일에서 설정 이름을 확인합니다.

4. 솔루션을 빌드하고 MyTestMethod 및 MyTestMethod2 테스트를 실행합니다.

> [!IMPORTANT]
> 테스트에서 배포 디렉터리를 통해 액세스할 수 있도록 데이터 원본과 같은 항목을 배포합니다.

## <a name="see-also"></a>참고 항목

- [코드 단위 테스트](../test/unit-test-your-code.md)
- [방법: 데이터 기반 단위 테스트 만들기](../test/how-to-create-a-data-driven-unit-test.md)
